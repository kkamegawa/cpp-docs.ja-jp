---
title: クリップボード:Windows クリップボードの使用方法
ms.date: 11/04/2016
helpviewer_keywords:
- Clipboard commands
- Cut/Copy and Paste command handler functions [MFC]
- handler functions, Cut/Copy and Paste commands
- Clipboard [MFC], commands
- commands [MFC], implementing Edit
- Clipboard commands [MFC], implementing
- Windows Clipboard [MFC]
- Clipboard [MFC], Windows Clipboard API
ms.assetid: 24415b42-9301-4a70-b69a-44c97918319f
ms.openlocfilehash: 49111e4efd2a12264d61030fe038d80b974514c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62326990"
---
# <a name="clipboard-using-the-windows-clipboard"></a>クリップボード:Windows クリップボードの使用方法

このトピックでは、MFC アプリケーション内では、標準の Windows クリップボード API を使用する方法について説明します。

Windows のほとんどのアプリケーションでは、切り取りまたはデータを Windows クリップボードにコピーして、クリップボードからのデータの貼り付けをサポートします。 クリップボードのデータ形式は、アプリケーションによって異なります。 フレームワークでは、クラスの数が制限のクリップボード形式の数に制限のみをサポートしています。 通常、クリップボードに関連するコマンドを実装: 切り取り、コピー、および貼り付け、[ビューの編集] メニュー。 クラス ライブラリでは、これらのコマンドのコマンド Id を定義します。**ID_EDIT_CUT**、 **ID_EDIT_COPY**、および**ID_EDIT_PASTE**します。 そのメッセージ行プロンプトも定義されます。

[フレームワークのメッセージとコマンド](../mfc/messages-and-commands-in-the-framework.md)メニュー コマンドをハンドラー関数にマップすることによって、アプリケーションでメニュー コマンドを処理する方法について説明します。 アプリケーションが [編集] メニュー クリップボード コマンドのハンドラー関数を定義しない限り、無効のままです。 コピーと切り取りのコマンドのハンドラー関数を作成するには、アプリケーションでの選択を実装します。 貼り付けコマンドのハンドラー関数を記述するには、アプリケーションが受け入れる形式のデータが含まれているかどうかをクリップボードをクエリします。 たとえば、コピー コマンドを有効にするは、次のようなハンドラーをする記述。

[!code-cpp[NVC_MFCListView#2](../atl/reference/codesnippet/cpp/clipboard-using-the-windows-clipboard_1.cpp)]

切り取り、コピー、および貼り付けのコマンドでは、特定のコンテキストで意味のあるのみです。 何かが選択されているときのみ貼り付けコマンドが、クリップボードで場合にのみ、切り取り、コピー コマンドを有効にする必要があります。 更新ハンドラー関数を有効または無効、コンテキストに応じてこれらのコマンドを定義することで、この動作を行うことができます。 詳細については、次を参照してください。[ユーザー インターフェイス オブジェクトを更新する方法](../mfc/how-to-update-user-interface-objects.md)します。

Microsoft Foundation Class ライブラリは、テキストの編集でクリップボードのサポートを提供して、`CEdit`と`CEditView`クラス。 OLE クラスには、OLE アイテムに関連する実装のクリップボード操作も簡略化します。 OLE クラスの詳細については、次を参照してください。[クリップボード。OLE クリップボード機構を使用して](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)します。

元に戻すなどのメニュー コマンドを編集するその他の実装 (**ID_EDIT_UNDO**) とやり直し (**ID_EDIT_REDO**) は残してもします。 アプリケーションがこれらのコマンドをサポートしていない場合簡単にして、Visual C リソース エディターを使用して、リソース ファイルから削除することができます。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [コピーと貼り付けデータ](../mfc/clipboard-copying-and-pasting-data.md)

- [OLE クリップボード機構の使用](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)

## <a name="see-also"></a>関連項目

[クリップボード](../mfc/clipboard.md)
