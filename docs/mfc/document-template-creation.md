---
title: ドキュメント テンプレートの作成
ms.date: 11/04/2016
helpviewer_keywords:
- document templates [MFC]
- constructors [MFC], document template
- document templates [MFC], creating
- MFC, document templates
- templates [MFC], document templates
ms.assetid: c87f1821-7cbf-442e-9690-f126ae7fb783
ms.openlocfilehash: 85ff6ad47b37d85c812608dbee918f0543730eae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62219809"
---
# <a name="document-template-creation"></a>ドキュメント テンプレートの作成

応答で新しいドキュメントを作成するときに、**新規**または**オープン**コマンドから、**ファイル**] メニューの [ドキュメント テンプレートも新しいフレーム ウィンドウを表示、作成、ドキュメントです。

ドキュメント テンプレート コンス トラクターでは、ドキュメント、windows、およびテンプレートが作成できるビューの種類を指定します。 これは、ドキュメント テンプレート コンス トラクターに渡す引数によって決定されます。 次のコードの作成を示しています、 [CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)サンプル アプリケーションについて。

[!code-cpp[NVC_MFCDocView#7](../mfc/codesnippet/cpp/document-template-creation_1.cpp)]

新しいポインター`CMultiDocTemplate`オブジェクトへの引数として使用されます[AddDocTemplate](../mfc/reference/cwinapp-class.md#adddoctemplate)します。 引数、`CMultiDocTemplate`コンス トラクターは、ドキュメントの種類のメニューとアクセラレータに関連付けられているリソース ID を含めるしの 3 つを使用して、 [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)マクロ。 `RUNTIME_CLASS` 返します、 [CRuntimeClass](../mfc/reference/cruntimeclass-structure.md)引数としてという名前の C++ クラスのオブジェクト。 3 つ`CRuntimeClass`ドキュメント テンプレート コンス トラクターに渡されたオブジェクトは、ドキュメントの作成プロセス中に、指定したクラスの新しいオブジェクトを作成するために必要な情報を指定します。 作成するドキュメント テンプレートの作成の例を示します`CScribDoc`オブジェクト`CScribView`アタッチされたオブジェクト。 ビューは、標準の MDI 子フレーム ウィンドウで囲まれます。

## <a name="see-also"></a>関連項目

[ドキュメント テンプレートとドキュメント/ビューの作成手順](../mfc/document-templates-and-the-document-view-creation-process.md)<br/>
[ドキュメント/ビューの作成](../mfc/document-view-creation.md)<br/>
[各種 MFC オブジェクト間の関係](../mfc/relationships-among-mfc-objects.md)<br/>
[新しいドキュメント、ウィンドウ、ビューの作成](../mfc/creating-new-documents-windows-and-views.md)
