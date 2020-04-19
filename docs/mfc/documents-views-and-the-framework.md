---
title: ドキュメント、ビュー、フレームワーク
ms.date: 11/19/2018
helpviewer_keywords:
- document templates [MFC], template objects
- applications [MFC]
- MFC, application framework
- application objects [MFC], relation to other MFC objects
- documents [MFC]
- MFC, documents
- document objects [MFC], in relation to other MFC objects
- view objects [MFC], relation to other MFC objects
- MFC, views
- document/view architecture [MFC], about document/view architecture
- objects [MFC], MFC applications
- MFC object relationships
- thread objects [MFC]
ms.assetid: 409ddd9b-66ad-4625-84f7-bf55a41d697b
ms.openlocfilehash: 799035976ea55988a635f7dc9b667e87c48d8f7e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406177"
---
# <a name="documents-views-and-the-framework"></a>ドキュメント、ビュー、フレームワーク

MFC フレームワークの中核には、ドキュメントとビューの概念が。 ドキュメントでは、ユーザーが編集セッションで対話するデータ オブジェクトです。 によって作成される、**新規**または**オープン**コマンドを**ファイル**メニューと、通常、ファイルに保存します。 (クラスから派生した、MFC の標準ドキュメント`CDocument`、アクティブなドキュメントと OLE 複合ドキュメントとは異なります)。ビューは、使用される、ユーザーがドキュメントを操作ウィンドウ オブジェクトです。

実行中のアプリケーションで主要なオブジェクトは次のとおりです。

- ドキュメントまたはドキュメント。

   ドキュメント クラス (から派生した[CDocument](../mfc/reference/cdocument-class.md))、アプリケーションのデータを指定します。

   OLE の機能をアプリケーションで使用すると場合からドキュメント クラスを派生[COleDocument](../mfc/reference/coledocument-class.md)またはその派生クラスで必要とする機能の種類に応じてのいずれか。

- ビューまたは表示します。

   ビュー クラス (から派生した[CView](../mfc/reference/cview-class.md))、ユーザーの「ウィンドウ データを」。 ビュー クラスでは、ユーザーのドキュメントのデータを表示および対話を制御します。 場合によっては、データのビューを複数のドキュメントをする可能性があります。

   スクロールが必要な場合から派生[CScrollView](../mfc/reference/cscrollview-class.md)します。 派生して、ビューにダイアログ テンプレート リソースに配置されるユーザー インターフェイスがある場合は、 [CFormView](../mfc/reference/cformview-class.md)します。 単純なテキスト データを使用して、またはそれから派生した[CEditView](../mfc/reference/ceditview-class.md)します。 データ入力プログラムなどのフォーム ベースのデータ アクセス アプリケーションから派生[CRecordView](../mfc/reference/crecordview-class.md) (for ODBC)。 使用可能なクラス[CTreeView](../mfc/reference/ctreeview-class.md)、 [CListView](../mfc/reference/clistview-class.md)、および[CRichEditView](../mfc/reference/cricheditview-class.md)します。

- フレーム ウィンドウ

   「ドキュメント フレーム ウィンドウ」内のビューに表示されます。 SDI アプリケーションで使用するドキュメント フレーム ウィンドウとは、またアプリケーションの「メイン フレーム ウィンドウ」です。 MDI アプリケーションでは、ドキュメント ウィンドウは、メイン フレーム ウィンドウ内に表示される子ウィンドウです。 派生のメイン フレーム ウィンドウ クラスには、ビューを含むフレーム ウィンドウの他の特性とスタイルを指定します。 フレーム ウィンドウをカスタマイズする必要がある場合から派生[CFrameWnd](../mfc/reference/cframewnd-class.md) SDI アプリケーションは、ドキュメント フレーム ウィンドウをカスタマイズします。 派生[CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md) MDI アプリケーションのメイン フレーム ウィンドウをカスタマイズします。 クラスを派生させることも[CMDIChildWnd](../mfc/reference/cmdichildwnd-class.md)をそれぞれ個別の種類のアプリケーションをサポートする MDI ドキュメント フレーム ウィンドウをカスタマイズします。

- ドキュメント テンプレートまたはテンプレート

   ドキュメント テンプレートでは、ドキュメント、ビュー、フレーム ウィンドウの作成を調整します。 クラスから派生した、特定のドキュメント テンプレート クラス[CDocTemplate](../mfc/reference/cdoctemplate-class.md)を作成し、1 つの種類のすべての開いているドキュメントを管理します。 ドキュメントの 1 つ以上の型をサポートするアプリケーションでは、複数のドキュメント テンプレートがあります。 クラスを使用して[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) SDI アプリケーション、またはクラスを使用して[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) MDI アプリケーション用。

- アプリケーション オブジェクト

   アプリケーション クラス (から派生した[CWinApp](../mfc/reference/cwinapp-class.md)) 上のオブジェクトのすべてを制御し、初期化やクリーンアップなどのアプリケーションの動作を指定します。 アプリケーションの 1 つ、唯一のアプリケーション オブジェクトを作成し、アプリケーションがサポートするドキュメント型のドキュメント テンプレートを管理します。

- スレッド オブジェクト

   アプリケーションが実行の個別のスレッドを作成する場合: たとえば、バック グラウンドで計算を実行する — から派生したクラスを使用します[CWinThread](../mfc/reference/cwinthread-class.md)。 [CWinApp](../mfc/reference/cwinapp-class.md)自体に由来`CWinThread`アプリケーションで、プライマリ スレッドの実行 (または、メイン プロセス) を表します。 セカンダリ スレッドで MFC を使用することもできます。

実行中のアプリケーションでこれらのオブジェクトは、協調的コマンドおよびその他のメッセージによって結合されて、ユーザーの操作に応答します。 1 つのアプリケーション オブジェクトは、1 つまたは複数のドキュメント テンプレートを管理します。 それぞれのドキュメント テンプレートを作成および (アプリケーションが SDI または MDI のどちらか) に応じて、1 つまたは複数のドキュメントを管理します。 ユーザーは、表示して、フレーム ウィンドウ内に含まれるビューを使用して、ドキュメントを操作できます。 次の図は、SDI アプリケーションのこれらのオブジェクト間の関係を示します。

![実行中の SDI アプリケーション内のオブジェクト](../mfc/media/vc386v1.gif "中の実行中の SDI アプリケーション オブジェクト") <br/>
動作中の SDI アプリケーションのオブジェクト

この一連のトピックの残りの部分では、framework のツール、MFC アプリケーション ウィザード、および、リソース エディターがこれらのオブジェクトを作成する方法、どのように連動する、および、プログラミングでの使用方法について説明します。 ドキュメント、ビュー、およびフレーム ウィンドウがで詳しく説明されている[ウィンドウ オブジェクト](../mfc/window-objects.md)と[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)します。

## <a name="see-also"></a>関連項目

[クラスを使用した Windows アプリケーションの作成](../mfc/using-the-classes-to-write-applications-for-windows.md)
