---
title: NMAKE の警告 U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 3b73e92c929b3dd5924584ab732f731d565d0430
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359775"
---
# <a name="nmake-warning-u4011"></a>NMAKE の警告 U4011

'target': 依存ファイルの一部が使用できます。ターゲットはビルドされません。

指定されたターゲットの依存が存在していなかったか、最新でし、の依存を更新するためのコマンドには 0 以外の終了コードが返されます。 /K オプションでは、NMAKE (nmake の) セッションが終了すると、終了コード 1 を発行して、ビルドの関連付けられていない部分の処理を続行するように指示します。

この警告は、前に警告[U4010](../../error-messages/tool-errors/nmake-warning-u4010.md)に作成または更新に失敗した依存します。