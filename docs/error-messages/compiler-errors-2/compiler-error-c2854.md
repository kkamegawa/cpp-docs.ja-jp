---
title: コンパイラ エラー C2854
ms.date: 11/04/2016
f1_keywords:
- C2854
helpviewer_keywords:
- C2854
ms.assetid: 917fec9c-790a-4149-8dfc-00d17a09199c
ms.openlocfilehash: 70b763afa4d511823a62d4d3770fc030ab9fb2ec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74745890"
---
# <a name="compiler-error-c2854"></a>コンパイラ エラー C2854

#pragma hdrstop に構文エラーがあります

`#pragma hdrstop` に無効なファイル名が与えられています。 プラグマの後に、省略可能なファイル名をかっこと引用符で囲んで指定できます。

次の例では、C2854 が生成されます。

```cpp
// C2854.cpp
// compile with: /c
#pragma hdrstop( "\\source\\pchfiles\\myheader.pch" ]   // C2854
// try the following line instead
// #pragma hdrstop( "\\source\\pchfiles\\myheader.pch" )
```
