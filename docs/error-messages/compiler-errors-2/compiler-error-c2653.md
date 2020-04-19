---
title: コンパイラ エラー C2653
ms.date: 11/30/2017
f1_keywords:
- C2653
helpviewer_keywords:
- C2653
ms.assetid: 3f49e731-affd-43a0-a8d0-181db7650bc3
ms.openlocfilehash: 2882764e1c0a84634c500d920f327fbebc4b19a9
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447945"
---
# <a name="compiler-error-c2653"></a>コンパイラ エラー C2653

> '*識別子*': クラスまたは名前空間名ではありません

言語の構文では、クラス、構造体、共用体、またはここに名前空間名が必要です。

このエラーは、クラス、構造体、共用体、またはスコープ演算子の前に名前空間として宣言されていない名前を使用するときに発生することができます。 この問題を解決するには、名前を宣言またはされる前に、名前を宣言するヘッダーが含まれます。

C2653 を定義しようとする場合も、*複合名前空間*、1 つまたは複数のスコープの入れ子になった名前空間名を含む名前空間。 C++17 の前に定義が C++ では許可されません。 名前空間を合成します。 複合の名前空間を指定すると、Visual Studio 2015 Update 3 以降はサポートされて、 [/std:c++latest](../../build/reference/std-specify-language-standard-version.md)コンパイラ オプション。 Visual Studio 2017 バージョン 15.5 以降では、コンパイラは複合名前空間の定義をサポートときに、 [/std:c++17](../../build/reference/std-specify-language-standard-version.md)オプションを指定します。

## <a name="examples"></a>使用例

このサンプルでは、スコープ名の使用が宣言されていないために、C2653 が生成されます。 コンパイラでは、クラス、構造体、共用体、またはスコープ演算子 (::) の前に名前空間の名前が必要です。

```cpp
// C2653.cpp
// compile with: /c
class yy {
   void func1(int i);
};

void xx::func1(int m) {}   // C2653, xx is not declared
void yy::func1(int m) {}   // OK
```

C++ 17 または以降の標準コンパイルされていないコードで入れ子になった名前空間は、入れ子の各レベルで、明示的な名前空間宣言を使用する必要があります。

```cpp
// C2653b.cpp
namespace a::b {int i;}   // C2653 prior to Visual Studio 2015 Update 3,
                          // C2429 thereafter. Use /std:c++17 or /std:c++latest to fix.

namespace a {             // Use this form for compliant code under /std:c++14 (the default)
   namespace b {          // or when using compilers before Visual Studio 2015 update 3.
      int i;
   }
}

int main() {
   a::b::i = 2;
}
```
