---
title: コンパイラの警告 (レベル 2 および 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 99b78e1426cf1618e68ae74ae7e16dd0f08606ba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359970"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>コンパイラの警告 (レベル 2 および 3) C4008

'identifier': 'attribute' 属性は無視されました

コンパイラは、関数 (レベル 3 警告) またはデータ (レベル 2 警告) の `__fastcall`、 **静的**、または **インライン** 属性を無視しました。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. データを伴う`__fastcall` 属性。

1. **メイン** 関数の **静的** または **インライン** 属性。