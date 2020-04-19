---
title: ドキュメント テンプレートとドキュメント/ビューの作成手順
ms.date: 11/19/2018
helpviewer_keywords:
- icons, for multiple document templates
- document templates [MFC], and views
- document/view architecture [MFC], creating document/view
- single document template
- MFC, document templates
- multiple document template
- CDocTemplate class [MFC]
- templates [MFC], document templates
ms.assetid: 311ce4cd-fbdf-4ea1-a51b-5bb043abbcee
ms.openlocfilehash: 79d24ef4b6687bce61295a92cdb90f4ce4a0d619
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389612"
---
# <a name="document-templates-and-the-documentview-creation-process"></a>ドキュメント テンプレートとドキュメント/ビューの作成手順

フレームワークは、2 つのドキュメント テンプレート クラスを使用して、関連付けられているビューやフレーム ウィンドウとドキュメントを作成する複雑なプロセスを管理するには、するには[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md) SDI アプリケーションと[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md) MDI アプリケーション用。 A`CSingleDocTemplate`を作成し、一度に 1 つの種類の 1 つのドキュメントを格納します。 A `CMultiDocTemplate` 1 つの型の多くの開いているドキュメントのリストを保持します。

一部のアプリケーションでは、複数のドキュメント タイプをサポートします。 たとえば、アプリケーションでは、ドキュメントのテキストとグラフィックスのドキュメントをサポート可能性があります。 このようなアプリケーションは、ユーザーが [ファイル] メニューで [New]、ダイアログ ボックスはの新しいドキュメント型を開くの一覧を示します。 サポートされているドキュメントの種類ごとに、アプリケーションは、個別のドキュメント テンプレート オブジェクトを使用します。 次の図は、2 つのドキュメントの種類をサポートし、いくつかの開いているドキュメントを表示する MDI アプリケーションの構成を示しています。

![2 つのドキュメント型を持つ MDI アプリケーション](../mfc/media/vc387h1.gif "を 2 つのドキュメントの種類を持つ MDI アプリケーション") <br/>
2 つのドキュメント タイプをサポートする MDI アプリケーション

ドキュメント テンプレートを作成して、アプリケーション オブジェクトによって保持されます。 アプリケーションの中に、重要なタスクの 1 つ実行`InitInstance`機能の適切な種類の 1 つまたは複数のドキュメント テンプレートを作成することです。 この機能については、「[ドキュメント テンプレートの作成](../mfc/document-template-creation.md)です。 アプリケーション オブジェクトでは、テンプレートのリストにそれぞれのドキュメント テンプレートへのポインターを格納し、ドキュメント テンプレートを追加するためのインターフェイスを提供します。

2 つ以上のドキュメントの種類をサポートする必要がある場合への余分な呼び出しを追加する必要があります[AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate)の各ドキュメントの種類。

アイコンは、ドキュメント テンプレートのアプリケーションの一覧における位置に基づいてそれぞれのドキュメント テンプレートに登録されます。 ドキュメント テンプレートの順序はへの呼び出しに追加された順序によって決まります`AddDocTemplate`します。 MFC では、アプリケーションの最初のアイコン リソースは、アプリケーションのアイコン、次へ のアイコン リソースは、最初のドキュメント アイコンと、前提としています。

たとえば、ドキュメント テンプレートは、3 番目のアプリケーション用に 3 つです。 インデックス 3 のアプリケーションで、アイコン リソースがある場合、そのアイコンは、ドキュメント テンプレートの使用されます。 有効でない場合は、インデックス 0 位置にあるアイコンは、既定値として使用されます。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)<br/>
[ドキュメント テンプレートの作成](../mfc/document-template-creation.md)<br/>
[ドキュメント/ビューの作成](../mfc/document-view-creation.md)<br/>
[各種 MFC オブジェクト間の関係](../mfc/relationships-among-mfc-objects.md)<br/>
[新しいドキュメント、ウィンドウ、ビューの作成](../mfc/creating-new-documents-windows-and-views.md)
