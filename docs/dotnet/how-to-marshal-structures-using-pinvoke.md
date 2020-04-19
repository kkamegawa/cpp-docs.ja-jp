---
title: '方法: 構造体のマーシャ リングを使用して PInvoke'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- data marshaling [C++], structures
- platform invoke [C++], structures
- interop [C++], structures
- marshaling [C++], structures
ms.assetid: 35997e6f-9251-4af3-8c6e-0712d64d6a5d
ms.openlocfilehash: d5c64a3e93cd85d7e38bac7c0ea3fa3c3301abc9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387241"
---
# <a name="how-to-marshal-structures-using-pinvoke"></a>方法: 構造体のマーシャ リングを使用して PInvoke

このドキュメントでは、C スタイルの構造体から呼び出せるマネージ関数を P/invoke を使用してそのまま使用するネイティブ関数について説明します。 代わりに、C++ Interop 機能を使用することをお勧めします。 P/invoke P/invoke は、ほとんどのコンパイル時エラーを報告するため、タイプ セーフでないし、実装、アンマネージ API が DLL としてパッケージ化され、ソース コードがない場合に時間がかかることができます。P/invoke は、使用可能な唯一のオプションです。 それ以外の場合、次のドキュメントを参照してください。

- [C++ Interop (暗黙の PInvoke) の使用](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [方法: PInvoke を使用して文字列をマーシャリングする](../dotnet/how-to-marshal-strings-using-pinvoke.md)

既定では、ネイティブおよびマネージ構造体レイアウトが異なる、メモリ内構造体のマネージ/アンマネージの境界を越えて受け渡しには、データの整合性を保持するために余分な手順が必要です。 正常されます。

このドキュメントでは、ネイティブの構造と結果の構造をアンマネージ関数に渡す方法に相当するマネージドを定義するために必要な手順について説明します。 このドキュメントで単純な構造体-文字列またはポインターを含まないもの — 使用されます。 Blittable でない相互運用性については、次を参照してください。[を使用して C++ Interop (暗黙の PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md)します。 P/invoke は、戻り値として非 blittable 型を含めることはできません。 Blittable 型のマネージ コードとアンマネージ コードで同じ表現であります。 詳細については、次を参照してください。 [blittable 型と非 Blittable 型](/dotnet/framework/interop/blittable-and-non-blittable-types)します。

単純なをマーシャ リングするマネージ/アンマネージの境界を越えて blittable 構造最初が必要です各ネイティブ構造体のマネージ バージョンが定義されています。 これらの構造は、任意の有効な名前を持つことができます。2 つの構造、データ レイアウト以外のネイティブおよびマネージ バージョン間の関係はありません。 したがって、管理対象のバージョンには、サイズとネイティブ バージョンと同じ順序で同じフィールドが含まれている重要なは。 (非互換性が明確にならない実行時まで、構造体のマネージ コードとネイティブ バージョン、それと同等であることを確認するためのメカニズムはありません。 2 つの構造は、同じデータのレイアウトでいることを確認するはプログラマの役目です。)

パフォーマンス向上のためのマネージ構造体のメンバーを並べ替え場合があります、ために、使用する必要が、<xref:System.Runtime.InteropServices.StructLayoutAttribute>構造が順番にレイアウトされることを指定する属性。 構造体のパッキング ネイティブ構造体で使用すると同じにする設定を明示的に設定することをお勧めします。 (既定では Visual C では、8 バイト構造体のマネージ コードの両方のパッキングします。)

1. 次に、<xref:System.Runtime.InteropServices.DllImportAttribute>宣言、構造をそのまま使用するアンマネージ関数に対応するエントリ ポイントが有言を同じ名前の両方のバージョンを使用する場合は、関数のシグネチャで構造体のマネージ バージョンを使用して、構造体。

1. これで実際にマネージ関数のように、マネージ コードは、構造体のマネージ バージョンをアンマネージ関数に渡すことができます。 これらの構造体渡すことができます、値、または参照渡しの次の例に示す。

## <a name="example"></a>例

次のコードは、アンマネージとマネージ モジュールで構成されます。 非管理対象のモジュールは、場所と場所の構造体の 2 つのインスタンスが受け取る GetDistance という名前の関数と呼ばれる構造を定義する DLL です。 2 番目のモジュールは、GetDistance 関数をインポートしますが、相当するマネージ MLocation 場所の構造体の観点からそれを定義する管理対象のコマンド ライン アプリケーションです。 実際にはこれらの同じ名前はおそらく、構造体の両方のバージョンを使用します。ただし、別の名前は、管理対象のバージョンの観点から DllImport のプロトタイプが定義されていることを示すためにここで使用されます。

従来を使用してマネージ コードに、DLL の部分は公開されていませんことに注意してください。 #include ディレクティブ。 実際には、DllImport でインポートされた関数に関する問題はコンパイル時に検出されないために、DLL は実行時にのみ、アクセスします。

```
// TraditionalDll3.cpp
// compile with: /LD /EHsc
#include <iostream>
#include <stdio.h>
#include <math.h>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
   #define TRADITIONALDLL_API __declspec(dllexport)
#else
   #define TRADITIONALDLL_API __declspec(dllimport)
#endif

#pragma pack(push, 8)
struct Location {
   int x;
   int y;
};
#pragma pack(pop)

extern "C" {
   TRADITIONALDLL_API double GetDistance(Location, Location);
   TRADITIONALDLL_API void InitLocation(Location*);
}

double GetDistance(Location loc1, Location loc2) {
   printf_s("[unmanaged] loc1(%d,%d)", loc1.x, loc1.y);
   printf_s(" loc2(%d,%d)\n", loc2.x, loc2.y);

   double h = loc1.x - loc2.x;
   double v = loc1.y = loc2.y;
   double dist = sqrt( pow(h,2) + pow(v,2) );

   return dist;
}

void InitLocation(Location* lp) {
   printf_s("[unmanaged] Initializing location...\n");
   lp->x = 50;
   lp->y = 50;
}
```

## <a name="example"></a>例

```
// MarshalStruct_pi.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

[StructLayout(LayoutKind::Sequential, Pack=8)]
value struct MLocation {
   int x;
   int y;
};

value struct TraditionalDLL {
   [DllImport("TraditionalDLL3.dll")]
   static public double GetDistance(MLocation, MLocation);
   [DllImport("TraditionalDLL3.dll")]
   static public double InitLocation(MLocation*);
};

int main() {
   MLocation loc1;
   loc1.x = 0;
   loc1.y = 0;

   MLocation loc2;
   loc2.x = 100;
   loc2.y = 100;

   double dist = TraditionalDLL::GetDistance(loc1, loc2);
   Console::WriteLine("[managed] distance = {0}", dist);

   MLocation loc3;
   TraditionalDLL::InitLocation(&loc3);
   Console::WriteLine("[managed] x={0} y={1}", loc3.x, loc3.y);
}
```

```Output
[unmanaged] loc1(0,0) loc2(100,100)
[managed] distance = 141.42135623731
[unmanaged] Initializing location...
[managed] x=50 y=50
```

## <a name="see-also"></a>関連項目

[C++ での明示的な PInvoke (DllImport 属性) の使用方法](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
