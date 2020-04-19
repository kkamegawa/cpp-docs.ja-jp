---
title: random_device クラス
ms.date: 11/04/2016
f1_keywords:
- random/std::random_device
- random/std::random_device::min
- random/std::random_device::max
- random/std::random_device::entropy
- random/std::random_device::operator()
helpviewer_keywords:
- std::random_device [C++]
- std::random_device [C++], min
- std::random_device [C++], max
- std::random_device [C++], entropy
- std::random_device [C++], entropy
ms.assetid: 4393d515-0cb6-4e0d-a2ba-c780f05dc1bf
ms.openlocfilehash: 184513bc63975bd8eaaf0e53300e5a6be7986389
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448532"
---
# <a name="randomdevice-class"></a>random_device クラス

外部デバイスからランダム シーケンスを生成します。

## <a name="syntax"></a>構文

```cpp
class random_device {
public:
   typedef unsigned int result_type;

   // constructor
   explicit random_device(const std::string& token = "");

   // properties
   static result_type min();
   static result_type max();
   double entropy() const;

   // generate
   result_type operator()();

   // no-copy functions
   random_device(const random_device&) = delete;
   void operator=(const random_device&) = delete;
   };
```

## <a name="members"></a>メンバー

|||
|-|-|
|[random_device](#random_device)|[entropy](#entropy)|
|[random_device::operator()](#op_call)||

## <a name="remarks"></a>Remarks

このクラスは乱数のソースを表します。ISO C++ 標準では、非確定的または暗号的に安全であることが認められていますが、要求されていはいません。 Visual Studio の実装では、生成される値は非確定的で暗号的に安全ですが、エンジンやエンジン アダプター ([mersenne_twister_engine](../standard-library/mersenne-twister-engine-class.md) など、大部分のアプリケーションで選択される高品質で高速のエンジン) から作成されるジェネレーターよりも実行は遅いです。

`random_device` の結果は、閉じた範囲 [ `0, 2`<sup>32</sup>) で一様に分布します。

`random_device` が非ブロッキング呼び出しになることは保証されていません。

一般に、`random_device` は、エンジンまたはエンジン アダプターで作成された他のジェネレーターにシードを設定するために使用されます。 詳細については、「[\<random>](../standard-library/random.md)」を参照してください。

## <a name="example"></a>例

次のコードは、このクラスの基本的な機能と結果の例を示しています。 `random_device` の持つ非確定的な特性のため、**出力**セクションに表示される乱数値は各人の結果と一致しません。 これは想定されている正常な動作です。

```cpp
// random_device_engine.cpp
// cl.exe /W4 /nologo /EHsc /MTd
#include <random>
#include <iostream>
using namespace std;

int main()
{
    random_device gen;

    cout << "entropy == " << gen.entropy() << endl;
    cout << "min == " << gen.min() << endl;
    cout << "max == " << gen.max() << endl;

    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
    cout << "a random value == " << gen() << endl;
}
```

```Output
entropy == 32
min == 0
max == 4294967295
a random value == 2378414971
a random value == 3633694716
a random value == 213725214
```

これは単純な例であり、このジェネレーターの一般的な使用例を表しているわけではありません。 代表的なコード サンプルについては、「[\<random>](../standard-library/random.md)」を参照してください。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<random>

**名前空間:** std

## <a name="random_device"></a>  random_device::random_device

ジェネレーターを構築します。

```cpp
random_device(const std::string& = "");
```

### <a name="remarks"></a>Remarks

このコンストラクターは、文字列パラメーターを無視して必要に応じてジェネレーターを初期化します。 `random_device` を初期化できなかった場合は、[exception](../standard-library/exception-class.md) から派生された実装定義型の値をスローします。

## <a name="entropy"></a>  random_device::entropy

乱数発生源の無作為性を推定します。

```cpp
double entropy() const noexcept;
```

### <a name="remarks"></a>Remarks

このメンバー関数は、乱数発生源がどの程度の無作為性を持っているかの推定値を返します。評価の単位には、ビットが使用されます。

## <a name="op_call"></a>  random_device::operator()

乱数値を返します。

```cpp
result_type operator()();
```

### <a name="remarks"></a>Remarks

閉区間 [ `min, max`] で、メンバー関数 `min()` および `max()` で定義されたように、一様に分布した値を返します。 乱数が取得できない場合は、[exception](../standard-library/exception-class.md) から導出される実装定義型の値をスローします。

## <a name="see-also"></a>関連項目

[\<random>](../standard-library/random.md)
