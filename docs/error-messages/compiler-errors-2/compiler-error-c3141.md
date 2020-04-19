---
title: コンパイラ エラー C3141
ms.date: 11/04/2016
f1_keywords:
- C3141
helpviewer_keywords:
- C3141
ms.assetid: b4fd65c3-50cc-46cd-8de0-6a6d24cb9cda
ms.openlocfilehash: 71f5a69bf96098b41bc2eb3945e1360955870657
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746189"
---
# <a name="compiler-error-c3141"></a>コンパイラ エラー C3141

' interface_name ': インターフェイスはパブリック継承のみをサポートしています

[インターフェイス (または __interface)](../../cpp/interface.md)キーワードで定義されたインターフェイスは、パブリック継承のみをサポートします。

次の例では、C3141 が生成されます。

```cpp
// C3141.cpp
__interface IBase {};
__interface IDerived1 : protected IBase {};  // C3141
__interface IDerived2 : private IBase {};    // C3141
```
