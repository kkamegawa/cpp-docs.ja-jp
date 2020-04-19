---
title: サーバー:埋め込み先フレームウィンドウの実装
ms.date: 09/09/2019
helpviewer_keywords:
- frame windows [MFC], implementing
- OLE server applications [MFC], frame windows
- servers, in-place frame windows
- frame windows [MFC], in-place
- in-place frame windows
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
ms.openlocfilehash: bc5439003b7c891ac3f4000c9b7820746aec4c8d
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907536"
---
# <a name="servers-implementing-in-place-frame-windows"></a>サーバー:埋め込み先フレームウィンドウの実装

この記事では、アプリケーションウィザードを使用してサーバーアプリケーションを作成しない場合に、ビジュアル編集サーバーアプリケーションに埋め込み先フレームウィンドウを実装するために必要な作業について説明します。 この記事で説明されている手順に従って、アプリケーションウィザードで生成されたアプリケーションまたはビジュアルC++で提供されているサンプルの既存のインプレースフレームウィンドウクラスを使用できます。

#### <a name="to-declare-an-in-place-frame-window-class"></a>埋め込み先フレームウィンドウクラスを宣言するには

1. の埋め込み先フレームウィンドウクラス`COleIPFrameWnd`を派生させます。

   - クラスのヘッダーファイルで DECLARE_DYNCREATE マクロを使用します。

   - クラス実装 (.cpp) ファイルで IMPLEMENT_DYNCREATE マクロを使用します。 これにより、このクラスのオブジェクトがフレームワークによって作成されます。

1. フレームウィンドウ`COleResizeBar`クラスでメンバーを宣言します。 これは、サーバーアプリケーションでのインプレースサイズ変更をサポートする場合に必要です。

   (クラス[ウィザード](reference/mfc-class-wizard.md)を使用して) `Create` `COleResizeBar` `OnCreate`メッセージハンドラーを宣言し、メンバーを定義している場合はを呼び出します。

1. ツールバーがある場合は、フレーム`CToolBar`ウィンドウクラスでメンバーを宣言します。

   サーバーが`OnCreateControlBars`適切に配置されている場合は、メンバー関数をオーバーライドしてツールバーを作成します。 例えば:

   [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/cpp/servers-implementing-in-place-frame-windows_1.cpp)]

   手順5の次のコードについて説明します。

1. メインの .cpp ファイルに、このインプレースフレームウィンドウクラスのヘッダーファイルを含めます。

1. アプリケーションクラス`SetServerInfo`の場合は、ドキュメントテンプレートオブジェクトの関数を呼び出して、オープンおよびインプレース編集で使用するリソースと埋め込み先フレームウィンドウを指定します。 `InitInstance`

**If**ステートメント内の一連の関数呼び出しによって、サーバーが提供するリソースからツールバーが作成されます。 この時点で、ツールバーはコンテナーのウィンドウ階層の一部です。 このツールバーはから`CToolBar`派生しているので、所有者を変更しない限り、メッセージはコンテナーアプリケーションのフレームウィンドウである所有者に渡されます。 そのため、を`SetOwner`呼び出す必要があります。 この呼び出しによって、コマンドがサーバーの埋め込み先フレームウィンドウとして送信されるウィンドウが変更され、メッセージがサーバーに渡されます。 これにより、サーバーは、提供されているツールバーに対する操作に対応できます。

ツールバーのビットマップの ID は、サーバーアプリケーションで定義されている他のインプレースリソースと同じである必要があります。 「 [メニューとリソース:詳細に](../mfc/menus-and-resources-server-additions.md)ついては、サーバーの追加情報をご確認ください。

詳細については、*クラスライブラリリファレンス*の「 [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md)、 [Coleresizebar](../mfc/reference/coleresizebar-class.md)、および[CDocTemplate:: setserverinfo](../mfc/reference/cdoctemplate-class.md#setserverinfo) 」を参照してください。

## <a name="see-also"></a>関連項目

[サーバー](../mfc/servers.md)<br/>
[サーバー: サーバーの実装](../mfc/servers-implementing-a-server.md)<br/>
[サーバー: サーバー ドキュメントの実装](../mfc/servers-implementing-server-documents.md)<br/>
[サーバー: サーバー アイテム](../mfc/servers-server-items.md)
