---
title: フレームワークと記述したコードとの関係
ms.date: 11/04/2016
helpviewer_keywords:
- control flow [MFC], MFC framework and your code
- events [MFC], command routing in MFC
- command routing [MFC], framework
- command handling [MFC], calling handlers and code in MFC
- events [MFC], event-driven programming
- MFC, calling code from
- MFC, calling code
- application-specific events [MFC]
- command routing [MFC], MFC
ms.assetid: 39e68189-a580-40d0-9e35-bf5cd24a8ecf
ms.openlocfilehash: 81b0749167391a841badff5494023a2ca5d3147e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407953"
---
# <a name="how-the-framework-calls-your-code"></a>フレームワークと記述したコードとの関係

ソース コードおよび MFC フレームワークのコード間の関係を理解するために重要になります。 アプリケーションを実行すると、制御フローのほとんどはフレームワークのコードに存在します。 フレームワークは、Windows からメッセージのように、ユーザーがコマンドを選択し、編集ビューでのデータを取得するメッセージ ループを管理します。 フレームワークを単独で処理できるイベント依存しないコードにします。 たとえば、フレームワークは、ウィンドウを閉じる方法と、ユーザーのコマンドを応答でアプリケーションを終了する方法を認識します。 これらのタスク処理時に、フレームワークはこれらのイベントに応答するのに機会を提供するのにメッセージ ハンドラーと C++ の仮想関数を使用します。 ただし; は、コントロールではなく、コードです。フレームワークは次のとおりです。

フレームワークは、アプリケーション固有のイベントのコードを呼び出します。 たとえば、ユーザーが メニュー コマンド、フレームワークは C++ オブジェクトのシーケンスに沿ったコマンドを送ります: 現在のビューとフレームのウィンドウで、ビュー、ドキュメントのドキュメント テンプレート、およびアプリケーションのオブジェクトに関連付けられたドキュメントです。 コマンドは、これらのオブジェクトが処理される場合は、適切なメッセージ ハンドラー関数を呼び出します。 、任意のコマンドの自分と呼ばれるコードがあります。 またはフレームワークの場合があります。

この配置では、Windows の従来のプログラミングまたはイベント ドリブン プログラミングで発生したプログラマについてある程度理解します。

関連のトピックでは、どのようなフレームワークは、として初期化しアプリケーションを実行しクリーンアップ、アプリケーションが終了するとを読み取ります。 作成したコードが内に収まるも理解できます。

詳細については、次を参照してください[クラス CWinApp:。アプリケーション クラス](../mfc/cwinapp-the-application-class.md)と[ドキュメント テンプレートとドキュメント/ビューの作成プロセス](../mfc/document-templates-and-the-document-view-creation-process.md)します。

## <a name="see-also"></a>関連項目

[フレームワークを使ったアプリケーションの作成](../mfc/building-on-the-framework.md)
