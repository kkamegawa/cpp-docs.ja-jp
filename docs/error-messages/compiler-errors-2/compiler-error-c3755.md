---
title: コンパイラ エラー C3755
ms.date: 11/04/2016
f1_keywords:
- C3755
helpviewer_keywords:
- C3755
ms.assetid: 9317b55e-a52e-4b87-b915-5a208d6eda38
ms.openlocfilehash: 0150693ae84b45dc62c11cfdc59369eb25a819cd
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757281"
---
# <a name="compiler-error-c3755"></a>コンパイラ エラー C3755

' delegate ': デリゲートを定義することはできません

[デリゲート (C++コンポーネント拡張)](../../extensions/delegate-cpp-component-extensions.md)は宣言できますが、定義することはできません。

## <a name="example"></a>使用例

次の例では、C3755 が生成されます。

```cpp
// C3755.cpp
// compile with: /clr /c
delegate void MyDel() {};   // C3755
```

## <a name="example"></a>使用例

C3755 は、デリゲートテンプレートを作成しようとした場合にも発生する可能性があります。 次の例では、C3755 が生成されます。

```cpp
// C3755_b.cpp
// compile with: /clr /c
ref struct R {
   template<class T>
   delegate void D(int) {}   // C3755
};
```
