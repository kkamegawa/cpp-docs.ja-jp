---
title: コンパイラの警告 (レベル 4) C4057
ms.date: 11/04/2016
f1_keywords:
- C4057
helpviewer_keywords:
- C4057
ms.assetid: e75d0645-84c9-4bef-a812-942ed9879aa3
ms.openlocfilehash: 234223ee7b6a031dd9e2c0fc88ccbbdba05beb3c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401437"
---
# <a name="compiler-warning-level-4-c4057"></a>コンパイラの警告 (レベル 4) C4057

'operator' : 'identifier1' と 'identifier2' で間接参照している基本型が微妙に異なっています

2 つのポインター式が参照する基本型が異なります。 式は変換されずに使用されます。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. signed 型と unsigned 型が混在しています。

1. **short** 型と **long** 型が混在しています。