---
title: コンパイラの警告 (レベル 1) C4086
ms.date: 11/04/2016
f1_keywords:
- C4086
helpviewer_keywords:
- C4086
ms.assetid: 9248831b-22bf-47af-8684-bfadb17e94fc
ms.openlocfilehash: dc841016218efa365f7cd9c098efbfe6748cca5d
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626846"
---
# <a name="compiler-warning-level-1-c4086"></a>コンパイラの警告 (レベル 1) C4086

プラグマに '1'、'2'、'4'、'8'、'16' のいずれかのパラメーターが必要です。

プラグマのパラメーターに必要な値 (1、2、4、8、または 16) がありません。

## <a name="example"></a>例

```cpp
// C4086.cpp
// compile with: /W1 /LD
#pragma pack( 3 ) // C4086
```