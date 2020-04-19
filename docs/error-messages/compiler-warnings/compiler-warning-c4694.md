---
title: コンパイラの警告 C4694
ms.date: 10/25/2017
f1_keywords:
- C4694
helpviewer_keywords:
- C4694
ms.assetid: 5ca122bb-34f3-43ee-a21f-95802cd515f7
ms.openlocfilehash: 6164fd2e19e35233ba67feb84d117f1e4e01f20d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311053"
---
# <a name="compiler-warning-c4694"></a>コンパイラの警告 C4694

> '*クラス*': シールドされた抽象クラスは基底クラス' を含めることはできません*base_class*'

シールされた抽象クラスは参照型を継承できません。シールされた抽象クラスは、基底クラスの関数を実装することも、それ自体を基底クラスとして使用しすることもできません。

詳細については、次を参照してください。[抽象](../../extensions/abstract-cpp-component-extensions.md)、[シール](../../extensions/sealed-cpp-component-extensions.md)、および[クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)します。

この警告は、自動的にエラーになります。 この動作を変更する場合を使用して、 [#pragma warning](../../preprocessor/warning.md)します。

## <a name="example"></a>例

次の例では C4694 が生成されます。

```cpp
// C4694.cpp
// compile with: /c /clr
ref struct A {};
ref struct B sealed abstract : A {};   // C4694
```