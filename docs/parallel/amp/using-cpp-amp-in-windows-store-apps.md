---
title: UWP アプリで C++ AMP の使用
ms.date: 11/04/2016
ms.assetid: 85577298-2c28-4209-9470-eb21048615db
ms.openlocfilehash: 31fede0a2419e56d53cb16521b08067dac5facc6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405353"
---
# <a name="using-c-amp-in-uwp-apps"></a>UWP アプリで C++ AMP の使用

ユニバーサル Windows プラットフォーム (UWP) アプリで C++ AMP (C++ Accelerated Massive Parallelism) を使用すると、GPU (グラフィックス処理装置) またはその他の計算アクセラレータで計算を実行します。 ただし C++ AMP では、Windows ランタイムの型を直接操作するための API が提供されておらず、Windows ランタイムでは C++ AMP のラッパーが提供されません。 Windows ランタイムの型を (独自に作成したコードも含めて) コード内で使用するときは、C++ AMP と互換性のある型に変換する必要があります。

## <a name="performance-considerations"></a>パフォーマンスに関する考慮事項

Visual C コンポーネント拡張 C + を使用しているかどうか/cli CX、ユニバーサル Windows プラットフォーム (UWP) アプリを作成すると共に連続した記憶域プレーン old data (POD) 型を使用することをお勧めします — たとえば、`std::vector`または C スタイル配列 — となるデータの。C++ AMP で使用します。 マーシャリングの必要がないため、非 POD 型または Windows RT コンテナーを使用する場合より高いパフォーマンスの実現に役立ちます.

C++ AMP カーネルで、この方法で格納されているデータにアクセスするには、`std::vector` または配列記憶域を `concurrency::array_view` でラップし、この配列ビューを `concurrency::parallel_for_each` ループで使用します。

```cpp
// simple vector addition example
std::vector<int> data0(1024, 1);
std::vector<int> data1(1024, 2);
std::vector<int> data_out(data0.size(), 0);

concurrency::array_view<int, 1> av0(data0.size(), data0);
concurrency::array_view<int, 1> av1(data1.size(), data1);
concurrency::array_view<int, 1> av2(data_out.size(), data2);

av2.discard_data();

concurrency::parallel_for_each(av0.extent, [=](concurrency::index<1> idx) restrict(amp)
    {
        av2[idx] = av0[idx] + av1[idx];
    });
```

## <a name="marshaling-windows-runtime-types"></a>Windows ランタイム型をマーシャリングする

Windows ランタイム Api を使用する場合など、Windows ランタイム コンテナーに格納されているデータに対して C++ AMP を使用する場合、`Platform::Array<T>^`クラスまたは構造体を使用して宣言されているなどの複雑なデータ型、 **ref**キーワードまたは**値**キーワード。 この場合、C++ AMP でデータを使用できるように特別な作業を行う必要があります。

### <a name="platformarrayt-where-t-is-a-pod-type"></a>Platform::array\<T > ^、T は POD 型

`Platform::Array<T>^` を検出した場合に T が POD 型であれば、基となる記憶域に `get` メンバー関数を使用してアクセスすることができます。

```cpp
Platform::Array<float>^ arr; // Assume that this was returned by a Windows Runtime API
concurrency::array_view<float, 1> av(arr->Length, &arr->get(0));
```

T が POD 型でない場合に C++ AMP でデータを使用するには、次のセクションで説明する手法を使用します。

### <a name="windows-runtime-types-ref-classes-and-value-classes"></a>Windows ランタイム型: ref クラスと value クラス

C++ AMP では、複合データ型がサポートされません。 非 POD 型とを使用して宣言されている任意の種類が含まれます、 **ref**キーワードまたは**値**キーワード。 サポートされていない型が `restrict(amp)` のコンテキストで使用されている場合、コンパイル時エラーが生成されます。

サポートされない型を検出した場合は、そのデータの必要な部分を `concurrency::array` オブジェクトにコピーできます。 データを C++ AMP で使用できるようにする作業に加え、この手動コピーを行うことも、データの局所性を最大限に高め、使用しないデータがアクセラレータにコピーされないようにする点で、パフォーマンスの向上に役立ちます。 使用してさらにパフォーマンスを向上させることができます、*ステージング配列*、これは特殊な形式の`concurrency::array`で他の配列との間の頻繁に転送するため、配列を最適化する AMP ランタイムへのヒントを提供する、指定されたアクセス キー。

```cpp
// pixel_color.h
ref class pixel_color sealed
{
public:
    pixel_color(Platform::String^ color_name, int red, int green, int blue)
    {
        name = color_name;
        r = red;
        g = green;
        b = blue;
    }

    property Platform::String^ name;
    property int r;
    property int g;
    property int b;
};

// Some other file

std::vector<pixel_color^> pixels (256);

for (pixel_color ^pixel : pixels)
{
    pixels.push_back(ref new pixel_color("blue", 0, 0, 255));
}

// Create the accelerators
auto cpuAccelerator = concurrency::accelerator(concurrency::accelerator::cpu_accelerator);
auto devAccelerator = concurrency::accelerator(concurrency::accelerator::default_accelerator);

// Create the staging arrays
concurrency::array<float, 1> red_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);
concurrency::array<float, 1>  blue_vec(256, cpuAccelerator.default_view, devAccelerator.default_view);

// Extract data from the complex array of structs into staging arrays.
concurrency::parallel_for(0, 256, [&](int i)
    {
        red_vec[i] = pixels[i]->r;
        blue_vec[i] = pixels[i]->b;
    });

// Array views are still used to copy data to the accelerator
concurrency::array_view<float, 1> av_red(red_vec);
concurrency::array_view<float, 1> av_blue(blue_vec);

// Change all pixels from blue to red.
concurrency::parallel_for_each(av_red.extent, [=](index<1> idx) restrict(amp)
    {
        av_red[idx] = 255;
        av_blue[idx] = 0;
    });
```

## <a name="see-also"></a>関連項目

[C++ を使った初めての UWP アプリを作成します。](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)<br/>
[C++ で Windows ランタイム コンポーネントを作成する](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp)
