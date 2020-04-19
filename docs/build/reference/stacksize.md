---
title: STACKSIZE
ms.date: 11/04/2016
f1_keywords:
- STACKSIZE
helpviewer_keywords:
- STACKSIZE .def file statement
ms.assetid: 4d8c79bd-1cb4-4e4d-90f2-b5a7a4d20e7a
ms.openlocfilehash: 2d27b4fd596098f4abc5bb0d804d87bd08f70a60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318357"
---
# <a name="stacksize"></a>STACKSIZE

スタック サイズをバイト単位で設定します。

```
STACKSIZE reserve[,commit]
```

## <a name="remarks"></a>Remarks

スタックを設定することは、[スタック割り当て](stack-stack-allocations.md)(/stack) オプション。 に関する詳細については、そのオプションについては、ドキュメントを参照してください、*予約*と`commit`引数。

このオプションは、Dll への影響を与えません。

## <a name="see-also"></a>関連項目

[モジュール定義ステートメントに関する規則](rules-for-module-definition-statements.md)
