---
title: コンパイラの警告 (レベル 2) C4412
ms.date: 11/04/2016
f1_keywords:
- C4412
helpviewer_keywords:
- C4412
ms.assetid: f28dc531-1a98-497b-a366-0a13e1bc81c7
ms.openlocfilehash: 2c9d50fc3433321c0ca92366a512892212545754
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402438"
---
# <a name="compiler-warning-level-2-c4412"></a>コンパイラの警告 (レベル 2) C4412

> '*関数*': 関数のシグネチャには、型が含まれています'*型*';。C++ オブジェクトは、純粋なコードの間で渡すため安全でないと混合またはネイティブです。

## <a name="remarks"></a>Remarks

**/Clr: 純粋な**コンパイラ オプションは Visual Studio 2015 で非推奨とされ、Visual Studio 2017 でサポートされていません。 ように移植することをお勧めは純粋にする必要があるコードがあれば、C#します。

実行時エラーの原因となる可能性のある安全でない状況が検出されました: から呼び出しが作成されている、 **/clr: 純粋な**dllimport と関数のシグネチャを使用してインポートされた関数をコンパイル単位には、安全でない型が含まれています. メンバー関数が含まれるか、安全でない型または間接参照を安全でない型であるデータ メンバーがある場合、型は安全ではありません。

これは、既定の呼び出し規約は純粋とネイティブ コード間の違いにより、安全な (またはネイティブおよびマネージの混合)。 インポートするときに (を使用して`dllimport`) に関数を **/clr: 純粋な**コンパイル単位、署名の各型の宣言が関数 (されるについて特に注意をエクスポートするコンパイル単位内に同じであることを確認相違暗黙の呼び出し規約)。

仮想メンバー関数は、傾向が予期しない結果が得られます。  ただし、正しい結果を取得するために、非仮想関数も含めてをテストする必要があります。 正しい結果が発生している場合は、この警告を無視できます。

C4412 は既定で無効にします。 参照してください[コンパイラの警告 That Are Off by 既定](../../preprocessor/compiler-warnings-that-are-off-by-default.md)と[dllexport、dllimport](../../cpp/dllexport-dllimport.md)詳細についてはします。

この警告を解決するには、型からのすべての機能を削除します。

## <a name="example"></a>例

次の例では、C4412 が生成されます。

```cpp
// C4412.cpp
// compile with: /c /W2 /clr:pure
#pragma warning (default : 4412)

struct Unsafe {
   virtual void __cdecl Test();
};

struct Safe {
   int i;
};

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   Unsafe *pUnsafe = func();   // C4412
   // pUnsafe->Test();

   Safe *pSafe = func2();   // OK
}
```

## <a name="example"></a>例

次のサンプルは、2 つの型を宣言するヘッダー ファイルです。 `Unsafe`型のメンバー関数があるため、安全ではありません。

```cpp
// C4412.h
struct Unsafe {
   // will be __clrcall if #included in pure compilation
   // defaults to __cdecl in native or mixed mode compilation
   virtual void Test(int * pi);

   // try the following line instead
   // virtual void __cdecl Test(int * pi);
};

struct Safe {
   int i;
};
```

## <a name="example"></a>例

このサンプルでは、ヘッダー ファイルで定義された型と関数をエクスポートします。

```cpp
// C4412_2.cpp
// compile with: /LD
#include "C4412.h"

void Unsafe::Test(int * pi) {
   *pi++;
}

__declspec(dllexport) Unsafe * __cdecl func() { return new Unsafe; }
__declspec(dllexport) Safe * __cdecl func2() { return new Safe; }
```

## <a name="example"></a>例

既定の呼び出し規約、 **/clr: 純粋な**コンパイルはネイティブ コンパイルと異なる。  C4412.h が含まれている`Test`の既定値は`__clrcall`します。 コンパイルして、このプログラムを実行する場合 (使用しない **/c**)、プログラムは例外をスローします。

次の例では、C4412 が生成されます。

```cpp
// C4412_3.cpp
// compile with: /W2 /clr:pure /c /link C4412_2.lib
#pragma warning (default : 4412)
#include "C4412.h"

__declspec(dllimport) Unsafe * __cdecl func();
__declspec(dllimport) Safe * __cdecl func2();

int main() {
   int n = 7;
   Unsafe *pUnsafe = func();   // C4412
   pUnsafe->Test(&n);

   Safe *pSafe = func2();   // OK
}
```