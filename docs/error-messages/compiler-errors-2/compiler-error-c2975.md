---
title: コンパイラ エラー C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 66b7c0d61cbc8141b9ed3e5f6eb329b68eb00477
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344701"
---
# <a name="compiler-error-c2975"></a>コンパイラ エラー C2975

> '*引数*': 無効なテンプレート引数'*型*'、コンパイル時定数式が必要です

テンプレート引数は、テンプレート宣言; と一致しません定数式は、山かっこ内に表示する必要があります。 変数は、実際のテンプレート引数としては許可されません。 テンプレートの定義を調べて正しい型が指定されていることをご確認ください。

## <a name="example"></a>例

次の例では、C2975 を生成し、また正しい使用法を示します。

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

C2975 は、使用する場合にも発生します。 &#95;&#95;行&#95;&#95;コンパイル時定数として[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)します。 1 つのソリューションを使用してコンパイルすること[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)の代わりに **/ZI**します。

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```