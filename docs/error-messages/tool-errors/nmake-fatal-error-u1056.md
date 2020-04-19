---
title: NMAKE の致命的なエラー U1056
ms.date: 11/04/2016
f1_keywords:
- U1056
helpviewer_keywords:
- U1056
ms.assetid: da855728-b69e-413c-83ed-df912126215e
ms.openlocfilehash: b15b14c04dd91ae648ea4311612c122f04f90477
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62367266"
---
# <a name="nmake-fatal-error-u1056"></a>NMAKE の致命的なエラー U1056

コマンド プロセッサを見つけることができません。

指定されたパスでコマンド プロセッサはなかった、 **COMSPEC**または**パス**環境変数。

NMAKE は COMMAND.COM または cmd.コマンドを実行するときに、コマンド プロセッサとして実行します。 検索コマンド プロセッサを最初設定されているパス**COMSPEC**します。 場合**COMSPEC** (nmake の) の検索で指定されたディレクトリが存在しない**パス**します。