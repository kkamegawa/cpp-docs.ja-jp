---
title: コンパイラエラー C2790
ms.date: 11/04/2016
f1_keywords:
- C2790
helpviewer_keywords:
- C2790
ms.assetid: 38d4fce1-ba00-413d-8bc1-e8aa43d7bc1f
ms.openlocfilehash: c63fe7bb3686692818337e890de7fe4c80a18158
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739559"
---
# <a name="compiler-error-c2790"></a>コンパイラエラー C2790

' super ': このキーワードはクラスメンバー関数の本体内でのみ使用できます

このエラーメッセージは、ユーザーがメンバー関数のコンテキストの外部でキーワード[super](../../cpp/super.md)を使用しようとした場合に表示されます。

次の例では、C2790 が生成されます。

```cpp
// C2790.cpp
void f() {
   __super::g();   // C2790
}
```
