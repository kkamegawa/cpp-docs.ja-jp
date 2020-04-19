---
title: メッセージの処理とマップ
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, messages
- message handling [MFC]
- message maps [MFC]
ms.assetid: 62fe2a1b-944c-449d-a0f0-63c11ee0a3cb
ms.openlocfilehash: 0321d98d8b92af0b80259bc49e84e69b987577a4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508241"
---
# <a name="message-handling-and-mapping"></a>メッセージの処理とマップ

この記事ファミリでは、メッセージとコマンドが MFC フレームワークによってどのように処理されるか、およびそれらをハンドラー関数に接続する方法について説明します。

Windows 用の従来のプログラムでは、Windows メッセージはウィンドウプロシージャ内の大きな switch ステートメントで処理されます。 代わりに MFC では、[メッセージマップ](../mfc/message-categories.md)を使用して、個別のクラスメンバー関数に直接メッセージをマップします。 メッセージマップは、この目的のための仮想関数よりも効率的であり、アプリケーション、ドキュメント、ビューなどC++の最も適切なオブジェクトによってメッセージを処理できます。 1つのメッセージ、またはメッセージの範囲、コマンド Id、またはコントロール Id をマップできます。

WM_COMMAND メッセージ (通常はメニュー、ツールバーボタン、またはアクセラレータによって生成される) では、メッセージマップ機構も使用されます。 MFC では、プログラム内のアプリケーション、フレームウィンドウ、ビュー、およびアクティブドキュメント間でのコマンドメッセージの標準的な[ルーティング](../mfc/command-routing.md)を定義します。 必要に応じて、このルーティングをオーバーライドできます。

また、メッセージマップは、ユーザーインターフェイスオブジェクト (メニューやツールバーボタンなど) を更新し、現在のコンテキストに合わせてそれらを有効または無効にする方法も提供します。

Windows のメッセージとメッセージキューに関する一般的な情報については、「Windows SDK のメッセージ[とメッセージキュー](/windows/win32/winmsg/messages-and-message-queues) 」を参照してください。

## <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)

- [フレームワークがメッセージハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)

- [フレームワークのメッセージ マップ検索方法](../mfc/how-the-framework-searches-message-maps.md)

- [メッセージ ハンドラー関数の宣言](../mfc/declaring-message-handler-functions.md)

- [マップ (関数にメッセージを)](../mfc/reference/mapping-messages-to-functions.md)

- [ステータスバーにコマンド情報を表示する方法](../mfc/how-to-display-command-information-in-the-status-bar.md)

- [ユーザーインターフェイスオブジェクトの動的な更新](../mfc/how-to-update-user-interface-objects.md)

- [方法: テンプレート クラスのメッセージ マップを作成する](../mfc/how-to-create-a-message-map-for-a-template-class.md)

## <a name="see-also"></a>関連項目

[概念](../mfc/mfc-concepts.md)<br/>
[MFC の一般的なトピック](../mfc/general-mfc-topics.md)<br/>
[CWnd クラス](../mfc/reference/cwnd-class.md)<br/>
[CCmdTarget クラス](../mfc/reference/ccmdtarget-class.md)
