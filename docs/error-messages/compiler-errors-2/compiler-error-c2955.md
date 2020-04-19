---
title: コンパイラ エラー C2955
ms.date: 03/28/2017
f1_keywords:
- C2955
helpviewer_keywords:
- C2955
ms.assetid: 77709fb6-d69b-46fd-a62f-e8564563d01b
ms.openlocfilehash: 8afdeaf43c0c9789753b9165f1e8a8287aaac76d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742874"
---
# <a name="compiler-error-c2955"></a>コンパイラ エラー C2955

'identifier' : クラス テンプレートまたは別名ジェネリックを使用するには、テンプレートまたは汎用引数リストが必要です。

クラス テンプレートまたはクラス ジェネリックは、テンプレートまたは汎用引数リストを付けずに識別子として使用することはできません。

詳細については、「[クラステンプレート](../../cpp/class-templates.md)」を参照してください。

次の例では C2955 が生成され、その修正方法が示されています。

```cpp
// C2955.cpp
// compile with: /c
template<class T>
class X {};

X x1;   // C2955
X<int> x2;   // OK - this is how to fix it.
```

C2955 は、クラス テンプレートで宣言される関数を行外で定義しようとした場合にも発生することがあります。

```cpp
// C2955_b.cpp
// compile with: /c
template <class T>
class CT {
public:
   void CTFunc();
   void CTFunc2();
};

void CT::CTFunc() {}   // C2955

// OK - this is how to fix it
template <class T>
void CT<T>::CTFunc2() {}
```

C2955 は、ジェネリックを使用しているときも発生します。

```cpp
// C2955_c.cpp
// compile with: /clr
generic <class T>
ref struct GC {
   T t;
};

int main() {
   GC^ g;   // C2955
   GC <int>^ g;
}
```

## <a name="example"></a>使用例

**Visual Studio 2017 以降:** テンプレートがテンプレートパラメーターリストに存在する場合、コンパイラはテンプレート引数リストがないことを正しく診断します (たとえば、既定のテンプレート引数または非型テンプレートパラメーターの一部として)。 次のコードは、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではエラーが発生します。

```
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```
