---
title: コンパイラ エラー C2059
ms.date: 03/26/2019
f1_keywords:
- C2059
helpviewer_keywords:
- C2059
ms.assetid: 2be4eb39-3f37-4b32-8e8d-75835e07c78a
ms.openlocfilehash: f91eb428fcb49c81187788730128545916955790
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127661"
---
# <a name="compiler-error-c2059"></a>コンパイラ エラー C2059

構文エラー: ' token '

トークンにより、構文エラーが発生しました。

次の例では、`j`を宣言する行に対してエラーメッセージを生成します。

```cpp
// C2059e.cpp
// compile with: /c
// C2143 expected
// Error caused by the incorrect use of '*'.
   int j*; // C2059
```

エラーの原因を特定するには、エラーメッセージに示されている行だけでなく、その上の行も確認します。 行を調べると問題についての手掛かりが得られない場合は、エラーメッセージに示されている行と、その上の数行をコメントアウトしてください。

`typedef` 変数の直後にあるシンボルでエラーメッセージが発生した場合は、変数がソースコードで定義されていることを確認します。

プリプロセッサシンボル名が識別子として再使用されると、C2059 が発生します。 次の例では、コンパイラによって `DIGITS.ONE` が number 1 として認識されますが、これは列挙型の要素名としては無効です。

```cpp
#define ONE 1

enum class DIGITS {
    ZERO,
    ONE // error C2059
};
```

シンボルが何も評価されない場合は、 **/d**_シンボル_**=** を使用してコンパイルすると発生する可能性があるため、C2059 が返されることがあります。

```cpp
// C2059a.cpp
// compile with: /DTEST=
#include <stdio.h>

int main() {
   #ifdef TEST
      printf_s("\nTEST defined %d", TEST);   // C2059
   #else
      printf_s("\nTEST not defined");
   #endif
}
```

C2059 が発生するもう1つのケースとして、関数の既定の引数に構造体を指定するアプリケーションをコンパイルする場合があります。 引数の既定値は式である必要があります。 たとえば、構造体の初期化に使用された初期化子リストは、式ではありません。  この問題を解決するには、必要な初期化を実行するコンストラクターを定義します。

次の例では、C2059 が生成されます。

```cpp
// C2059b.cpp
// compile with: /c
struct ag_type {
   int a;
   float b;
   // Uncomment the following line to resolve.
   // ag_type(int aa, float bb) : a(aa), b(bb) {}
};

void func(ag_type arg = {5, 7.0});   // C2059
void func(ag_type arg = ag_type(5, 7.0));   // OK
```

不適切な形式のキャストに対して C2059 が発生する可能性があります。

次の例では、C2059 が生成されます。

```cpp
// C2059c.cpp
// compile with: /clr
using namespace System;
ref class From {};
ref class To : public From {};

int main() {
   From^ refbase = gcnew To();
   To^ refTo = safe_cast<To^>(From^);   // C2059
   To^ refTo2 = safe_cast<To^>(refbase);   // OK
}
```

また、期間を含む名前空間の名前を作成しようとすると、C2059 も発生する可能性があります。

次の例では、C2059 が生成されます。

```cpp
// C2059d.cpp
// compile with: /c
namespace A.B {}   // C2059

// OK
namespace A  {
   namespace B {}
}
```

次の例に示すように、名前を修飾できる演算子 (`::`、`->`、および `.`) の後にキーワード `template`を指定する必要がある場合に、C2059 が発生する可能性があります。

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::Rebind<X>::Other AX; // error C2059
};
```

既定ではC++ 、は `AY::Rebind` がテンプレートではないことを前提としています。したがって、次の `<` は不等号として解釈されます。  山かっこを正しく解析できるように、`Rebind` がテンプレートであることをコンパイラに明示する必要があります。 このエラーを修正するには、次に示すように、依存する型の名前に対して `template` キーワードを使用します。

```cpp
template <typename T> struct Allocator {
    template <typename U> struct Rebind {
        typedef Allocator<U> Other;
    };
};

template <typename X, typename AY> struct Container {
    typedef typename AY::template Rebind<X>::Other AX; // correct
};
```
