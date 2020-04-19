---
title: MFC アプリケーション アーキテクチャ クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.mfc
helpviewer_keywords:
- MFC, classes
- MFC, application development
- classes [MFC], MFC
- application architecture classes [MFC]
ms.assetid: 71b2de54-b44d-407e-9c71-9baf954e18d9
ms.openlocfilehash: 47feeb056d02b81bb88ccf3c5fd49bc983583ee7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239306"
---
# <a name="mfc-application-architecture-classes"></a>MFC アプリケーション アーキテクチャ クラス

このカテゴリのクラスは、framework アプリケーションのアーキテクチャに貢献します。 これらは、ほとんどのアプリケーションに共通の機能を指定します。 アプリケーション固有の機能を追加するためにフレームワークを入力します。 通常、そのアーキテクチャのクラスから新しいクラスを派生して、新しいメンバーの追加または既存のメンバー関数をオーバーライドして行います。

[アプリケーション ウィザード](../mfc/reference/mfc-application-wizard.md)いくつかの種類の異なる方法で、アプリケーション フレームワークを使用して、すべてのアプリケーションを生成します。 SDI (シングル ドキュメント インターフェイス) と MDI (マルチ ドキュメント インターフェイス) アプリケーション有効にドキュメント/ビュー アーキテクチャと呼ばれるフレームワークの一部を利用します。 ダイアログ ベースのアプリケーション、フォーム ベースのアプリケーション、Dll などのアプリケーションの他の種類は、ドキュメント/ビュー アーキテクチャの機能の一部のみを使用します。

ドキュメント/ビュー アプリケーションには、ドキュメント、ビュー、およびフレーム ウィンドウの 1 つまたは複数のセットが含まれます。 ドキュメント テンプレート オブジェクトには、各ドキュメント/ビュー/フレーム セットについては、クラスが関連付けられます。

MFC アプリケーションでのドキュメント/ビュー アーキテクチャを使用する必要はありませんは、さまざまな利点があります。 印刷と印刷プレビューのサポートの現状、MFC OLE コンテナーとサーバーのサポートはドキュメント/ビュー アーキテクチャに基づきます。

すべての MFC アプリケーションで少なくとも 2 つのオブジェクトがある: アプリケーション オブジェクトから派生した[CWinApp](../mfc/reference/cwinapp-class.md)、やある種のメイン ウィンドウのオブジェクトから (多くの場合、間接的に) 派生[CWnd](../mfc/reference/cwnd-class.md)します。 (メイン ウィンドウがから派生するほとんどの場合、 [CFrameWnd](../mfc/reference/cframewnd-class.md)、 [CMDIFrameWnd](../mfc/reference/cmdiframewnd-class.md)、または[CDialog](../mfc/reference/cdialog-class.md)から派生する`CWnd`)。

ドキュメント/ビュー アーキテクチャを使用するアプリケーションには、追加のオブジェクトが含まれます。 プリンシパル オブジェクトは次のとおりです。

- クラスから派生したアプリケーション オブジェクト[CWinApp](../mfc/reference/cwinapp-class.md)、前述のとおりです。

- クラスから派生した 1 つまたは複数のドキュメント クラス オブジェクト[CDocument](../mfc/reference/cdocument-class.md)します。 ドキュメント クラスのオブジェクトは、ビューで操作されるデータの内部表現を担当します。 データ ファイルに関連付けられている必要があります。

- クラスから派生した 1 つまたは複数のビュー オブジェクト[CView](../mfc/reference/cview-class.md)します。 それぞれのビューは、ドキュメントにアタッチされ、フレーム ウィンドウに関連付けられているされるウィンドウです。 ビューは、表示し、ドキュメント クラスのオブジェクトに含まれるデータを操作します。

ドキュメント/ビュー アプリケーションには、フレーム ウィンドウも含まれています (から派生した[CFrameWnd](../mfc/reference/cframewnd-class.md)) とドキュメント テンプレート (から派生した[CDocTemplate](../mfc/reference/cdoctemplate-class.md))。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
