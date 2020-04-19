---
title: アイドリング ループ処理
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
ms.openlocfilehash: 72491c057f3bf7c531bb5515b07f1e9d0acf35d5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508407"
---
# <a name="idle-loop-processing"></a>アイドリング ループ処理

多くのアプリケーションは、時間のかかる処理をバックグラウンドで実行します。 パフォーマンスに関する考慮事項は、このような作業にマルチスレッドを使用することがあります。 スレッドには追加の開発オーバーヘッドが伴います。そのため、MFC が[OnIdle](../mfc/reference/cwinthread-class.md#onidle)関数で実行するアイドル時間の作業のような単純なタスクには推奨されません。 この記事では、アイドル処理に焦点を当てています。 マルチスレッドの詳細については、[マルチスレッドのトピック](../parallel/multithreading-support-for-older-code-visual-cpp.md)を参照してください。

バックグラウンド処理の中には、ユーザーがアプリケーションと対話できない間隔で適切に実行されるものもあります。 Microsoft Windows オペレーティングシステム用に開発されたアプリケーションでは、長いプロセスを多数の小さなフラグメントに分割することによって、アプリケーションでアイドル時の処理を実行できます。 各フラグメントの処理後、アプリケーションは[PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew)ループを使用して Windows に実行制御を戻します。

この記事では、アプリケーションでアイドル処理を実行する2つの方法について説明します。

- MFC のメインメッセージループで**PeekMessage**を使用します。

- アプリケーションの他の場所に別の**PeekMessage**ループを埋め込みます。

##  <a name="_core_peekmessage_in_the_mfc_message_loop"></a>MFC メッセージループの PeekMessage

MFC を使用して開発されたアプリケーションでは、 `CWinThread`クラスのメインメッセージループに、 [PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) Win32 API を呼び出すメッセージループが含まれています。 このループでは、 `OnIdle`メッセージ間の`CWinThread`メンバー関数も呼び出されます。 アプリケーションでは、関数をオーバーライドすることによって`OnIdle` 、このアイドル時間でメッセージを処理できます。

> [!NOTE]
>  `Run`、 `OnIdle`、およびその他の特定のメンバー関数は、 `CWinThread`クラス`CWinApp`ではなくクラスのメンバーになりました。 `CWinApp` は、`CWinThread` から派生しています。

アイドル処理の実行の詳細については、 *MFC リファレンス*の「 [OnIdle](../mfc/reference/cwinthread-class.md#onidle) 」を参照してください。

##  <a name="_core_peekmessage_elsewhere_in_your_application"></a>アプリケーション内の他の場所に PeekMessage

アプリケーションでアイドル処理を実行するもう1つの方法として、関数のいずれかにメッセージループを埋め込む方法があります。 このメッセージループは、 [CWinThread:: Run](../mfc/reference/cwinthread-class.md#run)で検出された MFC のメインメッセージループとよく似ています。 つまり、MFC を使用して開発されたアプリケーションのこのようなループは、メインメッセージループと同じ機能の多くを実行する必要があります。 次のコードフラグメントは、MFC と互換性のあるメッセージループを記述する方法を示しています。

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

関数に埋め込まれたこのコードは、実行するアイドル処理がある限りループします。 このループ内では、入れ子になっ`PeekMessage`たループはを繰り返し呼び出します。 この呼び出しが0以外の値を返す限り、ループは`CWinThread::PumpMessage`を呼び出して通常のメッセージの変換とディスパッチを実行します。 はドキュメントに記載されていませんが、Visual C++インストールの \ atl/srcディレクトリにある thrdcore .cpp ファイルのソースコードを確認できます。 `PumpMessage`

内側のループが終了すると、外側のループはの1回以上の呼び出し`OnIdle`を使用してアイドル処理を実行します。 最初の呼び出しは、MFC の目的で使用されます。 の追加の呼び出し`OnIdle`を行って、独自のバックグラウンド処理を行うことができます。

アイドル処理の実行の詳細については、「MFC ライブラリリファレンス」の「 [OnIdle](../mfc/reference/cwinthread-class.md#onidle) 」を参照してください。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
