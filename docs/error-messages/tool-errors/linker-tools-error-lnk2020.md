---
title: リンカ ツール エラー LNK2020
ms.date: 11/04/2016
f1_keywords:
- LNK2020
helpviewer_keywords:
- LNK2020
ms.assetid: 4dd017d0-5e83-471b-ac8a-538ac1ed6870
ms.openlocfilehash: 9c6be2548e277af08f1069a70b26cd761db835bc
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988767"
---
# <a name="linker-tools-error-lnk2020"></a>リンカ ツール エラー LNK2020

未解決のトークン ' token '

未定義の外部エラーに似ていますが、メタデータを介して参照が使用されている点が異なります。 メタデータでは、すべての関数とデータを定義する必要があります。

解決するには、以下を行います。

- 不足している関数またはデータを定義します。

- 不足している関数またはデータが既に定義されているオブジェクトファイルまたはライブラリを含めます。

## <a name="example"></a>使用例

次の例では、LNK2020 が生成されます。

```cpp
// LNK2020.cpp
// compile with: /clr /LD
ref struct A {
   A(int x);   // LNK2020
   static int f();   // LNK2020
};

// OK
ref struct B {
   B(int x) {}
   static int f() { return 0; }
};
```

## <a name="example"></a>使用例

マネージテンプレート型の変数を作成しても、型をインスタンス化しない場合も、LNK2020 が発生します。

次の例では、LNK2020 が生成されます。

```cpp
// LNK2020_b.cpp
// compile with: /clr

template <typename T>
ref struct Base {
   virtual void f1() {};
};

template <typename T>
ref struct Base2 {
   virtual void f1() {};
};

int main() {
   Base<int>^ p;   // LNK2020
   Base2<int>^ p2 = gcnew Base2<int>();   // OK
};
```
