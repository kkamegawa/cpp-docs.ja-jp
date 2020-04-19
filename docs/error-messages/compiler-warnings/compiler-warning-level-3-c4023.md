---
title: コンパイラの警告 (レベル 3) C4023
ms.date: 11/04/2016
f1_keywords:
- C4023
helpviewer_keywords:
- C4023
ms.assetid: 615d5374-d7c1-42eb-acfd-917c053270c8
ms.openlocfilehash: 4d433ff7d6b323fcb8508872d4e755f893a50f5c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62402360"
---
# <a name="compiler-warning-level-3-c4023"></a>コンパイラの警告 (レベル 3) C4023

'symbol' : _based ポインターがプロトタイプ宣言されていない関数へ渡されます : パラメーター番号

プロトタイプ宣言されていない関数に _based ポインターを渡すと、ポインターが正規化され、予期しない結果になります。

_based ポインターを渡されるプロトタイプ関数を使用すると、この警告が解決することがあります。