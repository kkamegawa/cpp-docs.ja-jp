---
title: NMAKE の警告 U4010
ms.date: 11/04/2016
f1_keywords:
- U4010
helpviewer_keywords:
- U4010
ms.assetid: 99d8eb9a-ae31-40d1-b8c5-8c66732127d3
ms.openlocfilehash: aa4d2355b18a3c6cc6fc3151c7662fbbbaa665d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298114"
---
# <a name="nmake-warning-u4010"></a>NMAKE の警告 U4010

'target': ビルドに失敗しました。/K 指定すると、続行しています.

指定したターゲットのコマンド ブロックのコマンドでは、0 以外の終了コードが返されます。 /K オプションでは、NMAKE (nmake の) セッションが終了すると、終了コード 1 を発行して、ビルドの関連付けられていない部分の処理を続行するように指示します。

NMAKE が警告を発行する場合は、指定されたターゲットは、自体の別のターゲットの依存[U4011](../../error-messages/tool-errors/nmake-warning-u4011.md)この警告の後にします。