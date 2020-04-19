---
title: コンパイラ エラー C2957
ms.date: 11/04/2016
f1_keywords:
- C2957
helpviewer_keywords:
- C2957
ms.assetid: 9cb4526f-4af8-47e9-b786-56192627ca72
ms.openlocfilehash: 122d6919271a165ceb0dad31a344e59cb3457a25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742770"
---
# <a name="compiler-error-c2957"></a>コンパイラ エラー C2957

'delim': 無効な左側の区切り文字です: '<' が必要です

ジェネリック クラスの形式が正しくありません。

次の例では C2957 が生成されます。

```cpp
// C2957.cpp
// compile with: /clr /LD
generic << class T>   // C2957
// try the following line instead
// generic < class T>
gc class C {};
```
