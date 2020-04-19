---
title: アサーションの表示
ms.date: 05/05/2019
helpviewer_keywords:
- debugging [ATL], displaying assertions
- assertions, displaying
- debugging assertions
- assertions, debugging
ms.assetid: fa353fe8-4656-4384-a5d2-8866bc977f06
ms.openlocfilehash: 962a33a7d5d922f7f1655e22b2c9d0acdcf8925c
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65221265"
---
# <a name="displaying-assertions"></a>アサーションの表示

サービスに接続されているクライアントが応答を停止する場合は、サービスがアサートすることを確認する必要がないメッセージ ボックスが表示されますがある可能性があります。 これはコードをデバッグする Visual Studio デバッガーを使用して確認できます (を参照してください[タスク マネージャーを使用して](../atl/using-task-manager.md)このセクションで前述した)。

設定することがあります、サービスで表示できない、メッセージ ボックスが表示されていると判断した場合、**デスクトップとの対話を許可するサービス**もう一度サービスを使用する前にオプション。 このオプションは、デスクトップに表示されるサービスによって表示されるメッセージ ボックスを許可する起動時のパラメーターです。 このオプションを設定するコントロール パネルの [サービス アプリケーションを開き、サービスを選択して、] をクリックして**スタートアップ**を選び、**デスクトップとの対話を許可するサービス**オプション。

## <a name="see-also"></a>関連項目

[デバッグのヒント](../atl/debugging-tips.md)
