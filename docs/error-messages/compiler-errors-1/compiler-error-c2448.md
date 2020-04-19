---
title: コンパイラ エラー C2448
ms.date: 11/04/2016
f1_keywords:
- C2448
helpviewer_keywords:
- C2448
ms.assetid: e255df3c-f861-4b4d-a193-8768cef061a5
ms.openlocfilehash: 8a71fe05e2a046a65b659840f94d104a3c526778
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744161"
---
# <a name="compiler-error-c2448"></a>コンパイラ エラー C2448

' identifier ': 関数スタイル初期化子が関数定義である可能性があります

関数の定義が正しくありません。

このエラーは、旧形式の C 言語の正式リストが原因で発生する場合があります。

次の例では、C2448 が生成されます。

```cpp
// C2448.cpp
void func(c)
   int c;
{}   // C2448
```
