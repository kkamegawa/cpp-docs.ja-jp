---
title: ドキュメントとビューの初期化と後処理
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- views [MFC], cleaning up
- documents [MFC], initializing
- documents [MFC], cleaning up
- views [MFC], initializing
- initializing objects [MFC], document objects
- document objects [MFC], life cycle of
- initializing views [MFC]
ms.assetid: 95d6f09b-a047-4079-856a-ae7d0548e9d2
ms.openlocfilehash: 59e86f4000e2da588749ca48887d34c3effdfc3a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297191"
---
# <a name="initializing-and-cleaning-up-documents-and-views"></a>ドキュメントとビューの初期化と後処理

初期化と、ドキュメントとビューの後にクリーンアップするには、次のガイドラインを使用します。

- MFC フレームワークは、ドキュメントとビューを初期化します。追加するすべてのデータを初期化します。

- ドキュメントとしてフレームワークをクリーンアップして、ビューを閉じます。これらのドキュメントとビューのメンバー関数の中からヒープに割り当てられたメモリを解放する必要があります。

> [!NOTE]
>  アプリケーション全体は、オーバーライドで最適に処理されるは、その初期化を思い出してください、 [InitInstance](../mfc/reference/cwinapp-class.md#initinstance)クラスのメンバー関数`CWinApp`、し、のオーバーライドではアプリケーション全体のクリーンアップを行う最も`CWinApp`メンバー関数は[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)します。

ドキュメントとそのフレーム ウィンドウとビュー (ビュー) mdi のライフ サイクル アプリケーションのとおりです。

1. 動的作成時にドキュメントのコンス トラクターが呼び出されます。

1. 各新しいドキュメントに対し、ドキュメントの[でも実質的](../mfc/reference/cdocument-class.md#onnewdocument)または[かまいません](../mfc/reference/cdocument-class.md#onopendocument)が呼び出されます。

1. ユーザーは、その有効期間中のドキュメントと対話します。 通常は、ユーザーを選択して、データの編集、表示を使用してデータをドキュメントに発生します。 ビューには、変更をストレージおよびその他のビューを更新するためのドキュメントが渡されます。 この期間中に、ドキュメントとビューの両方がコマンドを処理できます。

1. Framework 呼び出し[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)をドキュメントに固有のデータを削除します。

1. ドキュメントのデストラクターが呼び出されます。

SDI アプリケーションでは、手順 1 は、ドキュメントが最初に作成されたときに 1 回実行されます。 手順 2 ~ 4 が繰り返し実行新しいドキュメントが開かれるたびにします。 新しいドキュメントには、既存のドキュメント オブジェクトが再利用されます。 最後に、手順 5 は、アプリケーションの終了時に実行されます。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ドキュメントとビューの初期化](../mfc/initializing-documents-and-views.md)

- [ドキュメントとビューの後処理](../mfc/cleaning-up-documents-and-views.md)

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)
