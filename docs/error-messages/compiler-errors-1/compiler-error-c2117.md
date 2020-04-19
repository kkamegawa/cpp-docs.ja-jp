---
title: コンパイラ エラー C2117
ms.date: 11/04/2016
f1_keywords:
- C2117
helpviewer_keywords:
- C2117
ms.assetid: b947379d-5861-42fc-ac26-170318579cbd
ms.openlocfilehash: 7166ba4e5f3a0fb66360d388fb18367bf553492e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750456"
---
# <a name="compiler-error-c2117"></a>コンパイラ エラー C2117

' identifier ': 配列の範囲がオーバーフローしています

配列の初期化子が多すぎます。

- 配列要素および初期化子のサイズと数が一致しません。

- 文字列内の null 終端文字を格納するスペースがありません。

次の例では、C2117 が生成されます。

```cpp
// C2117.cpp
int main() {
   char abc[4] = "abcd";   // C2117
   char def[4] = "abd";   // OK
}
```
