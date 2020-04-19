---
title: ドキュメント/ビュー アーキテクチャ
ms.date: 11/19/2018
helpviewer_keywords:
- CView class [MFC], view architecture
- CDocument class [MFC]
- MFC, views
- views [MFC], MFC document/view model
- document objects [MFC]
- document objects [MFC], MFC document/view model
- MFC, documents
- documents [MFC], MFC document/view model
- document objects [MFC], document/view architecture
ms.assetid: 6127768a-553f-462a-b01b-a5ee6068c81e
ms.openlocfilehash: d1b1f80f44fdc66a3174ea75c15e139f98a4520b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389690"
---
# <a name="documentview-architecture"></a>ドキュメント/ビュー アーキテクチャ

既定では、MFC アプリケーション ウィザードは、ドキュメント クラスとビュー クラスで、アプリケーションのスケルトンを作成します。 MFC では、これら 2 つのクラスのデータ管理を分離します。 ドキュメントは、データを格納およびデータ印刷の管理し、データの複数のビューの更新を調整します。 ビューは、データを表示し、選択や編集など、ユーザー操作を管理します。

このモデルでは、MFC のドキュメント オブジェクトは読み取りし、永続的ストレージにデータを書き込みます。 ドキュメントは、(データベースなど) が存在する限り、データにインターフェイスを提供も可能性があります。 個別のビュー オブジェクトは、ユーザー選択ウィンドウにデータを表示して、データの編集からのデータの表示を管理します。 ビューでは、ドキュメントからデータの表示を取得し、データが変更を文書に通信します。

簡単にオーバーライドするか、ドキュメント/ビューの分離を無視する、ほとんどの場合は、このモデルに従うにいられない理由があります。 最高の 1 つは、スプレッドシートとグラフ ビューの両方など、同じドキュメントの複数のビューを作成する必要がある場合です。 ドキュメント/ビュー モデルは、コードの一般的なドキュメントにすべてのビュー (など、計算エンジン) を配置するときに、データの各ビューを表す個別のビュー オブジェクトを使用できます。 ドキュメントは、データが変更されるたびに、すべてのビューを更新するタスクもかかります。

MFC のドキュメント/ビュー アーキテクチャでは、複数のビュー、複数のドキュメント タイプ、分割ウィンドウ、およびその他の貴重なユーザー インターフェイス機能のサポートが容易にします。

プログラマ、およびユーザーに表示されている MFC フレームワークの部分では、ドキュメントとビューを示します。 フレームワークとアプリケーションの開発に、作業の大部分は、ドキュメントとビューのクラスを作成に移動します。 この記事のファミリについて説明します。

- ドキュメント、ビュー、およびフレームワークでやり取りする方法の目的。

- 必要がありますに何を実装します。

ドキュメント/ビューの中心にある 4 つのキー クラスには。

[CDocument](../mfc/reference/cdocument-class.md) (または[COleDocument](../mfc/reference/coledocument-class.md)) クラスを格納またはプログラムのデータの制御に使用されるオブジェクトをサポートします ドキュメントのプログラマが定義したクラスの基本的な機能を提供します。 ドキュメントでは、ユーザーは通常ファイル メニューの 開く コマンドを表示して、ファイル メニュー、保存 コマンドを保存しますデータの単位を表します。

[CView](../mfc/reference/cview-class.md) (またはその派生クラスのいずれかの) ビューのプログラマが定義したクラスの基本的な機能を提供します。 ビューがドキュメントにアタッチされているし、ドキュメントとユーザーの間の仲介役として機能します。 ビューは、画面上のドキュメントのイメージを表示しますし、ユーザー入力をドキュメントに操作として解釈します。 ビューには、印刷と印刷プレビュー画像も表示します。

[CFrameWnd](../mfc/reference/cframewnd-class.md) (またはそのバリエーションの 1 つ) は、ドキュメントの 1 つまたは複数のビューを囲むフレームを提供するオブジェクトをサポートします。

[CDocTemplate](../mfc/reference/cdoctemplate-class.md) (または[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)または[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)) を指定された型の 1 つまたは複数の既存のドキュメントを調整し、適切な作成を管理するオブジェクトをサポートしていますドキュメント、ビュー、およびその型のフレーム ウィンドウ オブジェクト。

次の図は、ドキュメントとビュー間の関係を示します。

![ビューが表示されているドキュメントの一部](../mfc/media/vc379n1.gif "ビューが表示されているドキュメントの一部") <br/>
ドキュメントとビュー

クラス ライブラリのドキュメント/ビューの実装は、データ自体の表示と、データ上でユーザー操作からを区切ります。 データに対するすべての変更は、ドキュメントのクラスによって管理されます。 ビューにアクセスしてデータを更新するには、このインターフェイスを呼び出します。

ドキュメント、関連付けられたビュー、およびフレーム ウィンドウ ビューには、ドキュメント テンプレートによって作成されます。 ドキュメント テンプレートは、作成して、1 つのドキュメントの種類のすべてのドキュメントを管理する責任を負います。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ドキュメント/ビュー アーキテクチャの全体像](../mfc/a-portrait-of-the-document-view-architecture.md)

- [ドキュメント/ビュー アーキテクチャの利点](../mfc/advantages-of-the-document-view-architecture.md)

- [アプリケーション ウィザードによって作成されたドキュメントとビュー クラス](../mfc/document-and-view-classes-created-by-the-mfc-application-wizard.md)

- [ドキュメント/ビュー アーキテクチャの代替手段](../mfc/alternatives-to-the-document-view-architecture.md)

- [シングル ドキュメントへのマルチ ビューの追加](../mfc/adding-multiple-views-to-a-single-document.md)

- [ドキュメントの使い方](../mfc/using-documents.md)

- [ビューの使い方](../mfc/using-views.md)

- [複数のドキュメント タイプ、ビュー、フレーム ウィンドウ](../mfc/multiple-document-types-views-and-frame-windows.md)

- [ドキュメントとビューの初期化と後処理](../mfc/initializing-and-cleaning-up-documents-and-views.md)

- [ドキュメントとビュー クラスに、独自の追加を初期化します。](../mfc/creating-new-documents-windows-and-views.md)

- [ドキュメントとビューを用いたデータベース クラス](../data/mfc-using-database-classes-with-documents-and-views.md)

- [ドキュメントとビューを用いないデータベース クラスの使用](../data/mfc-using-database-classes-without-documents-and-views.md)

- [サンプル](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス要素](../mfc/user-interface-elements-mfc.md)<br/>
[Windows](../mfc/windows.md)<br/>
[フレーム ウィンドウ](../mfc/frame-windows.md)<br/>
[ドキュメント テンプレートとドキュメント/ビューの作成手順](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[ドキュメント/ビューの作成](../mfc/document-view-creation.md)<br/>
[新しいドキュメント、ウィンドウ、ビューの作成](../mfc/creating-new-documents-windows-and-views.md)
