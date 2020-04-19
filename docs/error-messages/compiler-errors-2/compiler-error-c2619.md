---
title: コンパイラエラー C2619
ms.date: 11/04/2016
f1_keywords:
- C2619
helpviewer_keywords:
- C2619
ms.assetid: c826f8ab-d66a-4b79-a0b2-93b0af8c41ac
ms.openlocfilehash: 3ca5ea4612091f1e3eee8fead2b1eaebb264b696
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754772"
---
# <a name="compiler-error-c2619"></a>コンパイラエラー C2619

'identifier' : 静的データ メンバー宣言は匿名の構造体または共用体では使用できません

匿名の構造体または共用体のメンバーは、`static` として宣言されます。

次の例では C2619 を生成し、static キーワードの削除による修正方法を示しています。

```cpp
// C2619.cpp
int main() {
   union { static int j; };  // C2619
   union { int j; };  // OK
}
```
