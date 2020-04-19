---
title: MFC のアプリケーション ウィザードで作成されるドキュメント クラスとビュー クラス
ms.date: 11/04/2016
helpviewer_keywords:
- document classes [MFC]
- document classes [MFC], created by application wizards
- application wizards [MFC], document/view classes created
- view classes [MFC], created by application wizards
ms.assetid: 70c34a60-2701-4981-acea-c08a5787d8e6
ms.openlocfilehash: 95b50e34d612c3b8f5dea2f8b469bd6c65182d41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408027"
---
# <a name="document-and-view-classes-created-by-the-mfc-application-wizard"></a>MFC のアプリケーション ウィザードで作成されるドキュメント クラスとビュー クラス

MFC アプリケーション ウィザードできますスタートが切れますので、プログラム開発のスケルトンのドキュメントとビュー クラスを作成しています。 できます[コマンドとメッセージをこれらのクラスにマップ](../mfc/reference/mapping-messages-to-functions.md)Visual C ソース コード エディターを使用して、そのメンバー関数を記述するとします。

クラスから派生した MFC アプリケーション ウィザードによって作成されたドキュメント クラスは[CDocument](../mfc/reference/cdocument-class.md)します。 ビュー クラスから派生[CView](../mfc/reference/cview-class.md)します。 アプリケーション ウィザード ダイアログ ボックスに指定した名前のアプリケーション ウィザードにはこれらのクラスをこれらを含むファイルがプロジェクト名に基づきます。 アプリケーション ウィザードでは、既定の名前を変更するのに [クラスの生成] ページを使用できます。

一部のアプリケーションには、1 つ以上のドキュメント クラス、ビュー クラス、またはフレーム ウィンドウ クラスを必要があります。 詳細については、次を参照してください。[複数のドキュメント タイプ、ビュー、およびフレーム Windows](../mfc/multiple-document-types-views-and-frame-windows.md)します。

## <a name="see-also"></a>関連項目

[ドキュメント/ビュー アーキテクチャ](../mfc/document-view-architecture.md)
