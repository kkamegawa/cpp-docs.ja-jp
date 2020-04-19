---
title: コンパイラの警告 (レベル 1) C4083
ms.date: 11/04/2016
f1_keywords:
- C4083
helpviewer_keywords:
- C4083
ms.assetid: e7d3344e-5645-4d56-8460-d1acc9145ada
ms.openlocfilehash: c267d466b70242ebef837fbe01c91f2cf0f69c02
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626877"
---
# <a name="compiler-warning-level-1-c4083"></a>コンパイラの警告 (レベル 1) C4083

' token ' が必要です。識別子 ' identifier ' が見つかりました

**#Pragma**ステートメント内の間違った場所で識別子が発生しています。

## <a name="example"></a>例

```cpp
// C4083.cpp
// compile with: /W1 /LD
#pragma warning disable:4083    // C4083
#pragma warning(disable:4083)   //correct
```

[#Pragma](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)ディレクティブの構文を確認します。