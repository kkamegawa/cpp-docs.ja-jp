---
title: NMAKE の致命的なエラー U1099
ms.date: 11/04/2016
f1_keywords:
- U1099
helpviewer_keywords:
- U1099
ms.assetid: 6688a805-43e6-4247-a2d0-14be082f0b13
ms.openlocfilehash: 395f25d8d27bc5e9b6132c87390c8c3bc19b6cc4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298244"
---
# <a name="nmake-fatal-error-u1099"></a>NMAKE の致命的なエラー U1099

スタック オーバーフロー

処理中のメイクファイルが複雑すぎるため、現在のスタック割り当て (nmake の)。 NMAKE は、0x3000 (12 K) の割り当てが。

NMAKE のスタック割り当てを増やすには、実行、 [editbin/stack](../../build/reference/stack.md)ユーティリティをより大きなスタック オプション。

**editbin/STACK:reserve (nmake の)。実行可能ファイル**

場所*予約*数値を (nmake の) 現在のスタック割り当てを超えています。