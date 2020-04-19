---
title: コンパイラの警告 C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 83f5c535f9cf252783110838c181c88c8b0096ee
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631602"
---
# <a name="compiler-warning-c4687"></a>コンパイラの警告 C4687

> '*class*': シールドされた抽象クラスはインターフェイス '*interface*' を実装できません

## <a name="remarks"></a>Remarks

シールドされた抽象型は、通常、静的メンバー関数を保持する場合にのみ役立ちます。

詳細については、「 [abstract](../../extensions/abstract-cpp-component-extensions.md) and [sealed](../../extensions/sealed-cpp-component-extensions.md)」を参照してください。

C4687 は、既定ではエラーとして発行されます。 C4687 は、 [warning](../../preprocessor/warning.md)プラグマを使用して抑制できます。 シールされた抽象型にインターフェイスを実装することがわかっている場合は、C4687 を抑制することができます。

## <a name="example"></a>例

次の例では、C4687 が生成されます。

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
