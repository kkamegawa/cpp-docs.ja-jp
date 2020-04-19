---
title: Active ドキュメント
ms.date: 11/04/2016
helpviewer_keywords:
- active documents [MFC]
- active documents [MFC], requirements
- view objects [MFC], requirements
- OLE [MFC], active documents
- views [MFC], active documents
- active documents [MFC], views
ms.assetid: 1378f18e-aaa6-420b-8501-4b974905baa0
ms.openlocfilehash: 519dd51ab9b46adf862999104e97c6e478ccd86b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394950"
---
# <a name="active-documents"></a>Active ドキュメント

アクティブなドキュメントは、OLE の複合ドキュメント テクノロジを拡張します。 これらの拡張機能は、オブジェクトをコンテナー内で機能し、表示および印刷機能の制御をまだ保持するために、ビューを管理する追加のインターフェイスの形式で提供されます。 このプロセスを行う (Microsoft Internet Explorer や Microsoft Office バインダー) などの外部のフレームと (ポート製品の表示) などのネイティブ フレームの両方にドキュメントを表示します。

このセクションでは、機能について説明します[のアクティブなドキュメント要件](#requirements_for_active_documents)します。 アクティブなドキュメントを一連のデータを所有してアクセスするのには、ストレージ、データを保存および取得できます。 作成し、データの 1 つまたは複数のビューを管理できます。 アクティブなドキュメントのビューを作成するには、その機能の通信だけでなく、通常の埋め込みと OLE ドキュメントのインプレース アクティブ化のインターフェイスをサポートしている、`IOleDocument`します。 このインターフェイスからは、コンテナーは、アクティブなドキュメントを表示できるビューの作成 (および場合によっては列挙) を要求できます。 このインターフェイスを使用では、アクティブなドキュメントは、自身に関する複数のビューまたは複雑な四角形をサポートするかどうかなどの他の情報も提供します。

次に、`IOleDocument`インターフェイス。 なお、`IEnumOleDocumentViews`インターフェイスは標準の OLE 列挙子の`IOleDocumentView*`型。

```
interface IOleDocument : IUnknown
    {
    HRESULT CreateView(
        [in] IOleInPlaceSite *pIPSite,
        [in] IStream *pstm,
        [in] DWORD dwReserved,
        [out] IOleDocumentView **ppView);

    HRESULT GetDocMiscStatus([out] DWORD *pdwStatus);

    HRESULT EnumViews(
        [out] IEnumOleDocumentViews **ppEnum,
        [out] IOleDocumentView **ppView);
    }
```

すべてのアクティブなドキュメントには、このインターフェイスであるビューのフレーム プロバイダーをいる必要があります。 コンテナー内で、ドキュメントが埋め込まれていない場合、active ドキュメント サーバー自体はビュー フレームを提供する必要があります。 ただし、active ドキュメント コンテナーでは、アクティブなドキュメントが埋め込まれているときに、コンテナーは、ビューのフレームを提供します。

アクティブ ドキュメントの 1 つまたは複数の種類を作成できます[ビュー](#requirements_for_view_objects)のデータ (例では、通常、アウトライン、ページのレイアウト、およびなど)。 ビューは、フィルター、データを表示するように動作します。 まだ新しいウィンドウの機能をサポートするための手段として、複数のビューをサポートするためにする場合でも、ドキュメントは、ビューの種類を 1 つだけがある、可能性があります (たとえば、**新しいウィンドウ**項目、**ウィンドウ**Office のメニューアプリケーションの場合)。

##  <a name="requirements_for_active_documents"></a> アクティブなドキュメントの要件

Active ドキュメント コンテナーに表示できる作業中のドキュメントにする必要があります。

- そのストレージ メカニズムとして OLE 複合ファイルを使用して実装することによって`IPersistStorage`します。

- などの OLE ドキュメントの基本的な埋め込み機能をサポート**ファイルの作成から**します。 インターフェイスが必要になりますこの`IPersistFile`、 `IOleObject`、および`IDataObject`します。

- インプレース アクティブ化できるは、1 つまたは複数のビューをサポートします。 つまり、ビューがインターフェイスをサポートする必要があります`IOleDocumentView`インターフェイスと`IOleInPlaceObject`と`IOleInPlaceActiveObject`(コンテナーの使用`IOleInPlaceSite`と`IOleInPlaceFrame`インターフェイス)。

- アクティブなドキュメントの標準的なインターフェイスをサポートして`IOleDocument`、 `IOleCommandTarget`、および`IPrint`します。

場合の知識とコンテナー側のインターフェイスを使用する方法をこれらの要件で暗黙的に指定するとします。

##  <a name="requirements_for_view_objects"></a> オブジェクトを表示するための要件

アクティブ ドキュメントでは、そのデータの 1 つまたは複数のビューを作成できます。 機能的には、これらのビューは、データを表示するための特定のメソッドへのポートは。 アクティブ ドキュメントは、1 つのビューのみをサポートする場合、アクティブなドキュメントとビュー実装できます 1 つのクラスを使用します。 `IOleDocument::CreateView` 同じオブジェクトを返します`IOleDocumentView`インターフェイス ポインター。

Active ドキュメント コンテナー内で表される、ビュー コンポーネントをサポートする必要があります`IOleInPlaceObject`と`IOleInPlaceActiveObject`に加えて`IOleDocumentView`:

```
interface IOleDocumentView : IUnknown
    {
    HRESULT SetInPlaceSite([in] IOleInPlaceSite *pIPSite);
    HRESULT GetInPlaceSite([out] IOleInPlaceSite **ppIPSite);
    HRESULT GetDocument([out] IUnknown **ppunk);
    [input_sync] HRESULT SetRect([in] LPRECT prcView);
    HRESULT GetRect([in] LPRECT prcView);
    [input_sync] HRESULT SetRectComplex(
        [in] LPRECT prcView,
        [in] LPRECT prcHScroll,
        [in] LPRECT prcVScroll,
        [in] LPRECT prcSizeBox);
    HRESULT Show([in] BOOL fShow);
    HRESULT UIActivate([in] BOOL fUIActivate);
    HRESULT Open(void);
    HRESULT CloseView([in] DWORD dwReserved);
    HRESULT SaveViewState([in] IStream *pstm);
    HRESULT ApplyViewState([in] IStream *pstm);
    HRESULT Clone(
        [in] IOleInPlaceSite *pIPSiteNew,
        [out] IOleDocumentView **ppViewNew);
    }
```

すべてのビューには、ビューのフレームと、ビュー ポート (HWND とそのウィンドウ内の四角形の領域) をカプセル化する、関連付けられたビュー サイトがあります。 サイトを公開しますこの機能は、標準`IOleInPlaceSite`インターフェイス。 1 つの HWND には、複数のビュー ポートを含めることは可能であるに注意してください。

通常、ビューの各種類では、さまざまな印刷表現があります。 そのためのビューと対応するサイトの表示する必要があります、印刷インターフェイス実装`IPrint`と`IContinueCallback`、それぞれします。 ビューのフレームが使用して、ビュー プロバイダーでネゴシエートする必要があります`IPrint`印刷が開始すると、ヘッダー、フッター、余白、および関連する要素が正しく印刷されるようにします。 ビュー プロバイダー経由の印刷関連イベントのフレームに通知`IContinueCallback`します。 これらのインターフェイスの使用に関する詳細については、次を参照してください。[プログラムによる印刷](../mfc/programmatic-printing.md)します。

アクティブ ドキュメントは、1 つのビューのみをサポートする場合、アクティブなドキュメントとビュー実装できることを 1 つの具象クラスを使用してに注意してください。 `IOleDocument::CreateView` 単に、同じオブジェクトを返します`IOleDocumentView`インターフェイス ポインター。 簡単に言えば、1 つのビューが必要な場合が 2 つの個別のオブジェクト インスタンスをするを必要はありません。

ビュー オブジェクトには、コマンド ターゲットことができます。 実装することによって`IOleCommandTarget`ビューは、コンテナーのユーザー インターフェイスで発生するコマンドを受信できます (など**新規**、**オープン**、**名前を付けて保存**、 **印刷**で、**ファイル**メニューと**コピー**、**貼り付け**、**を元に戻す**上、 **を編集**メニュー)。 詳細については、次を参照してください。[メッセージの処理とコマンド ターゲット](../mfc/message-handling-and-command-targets.md)します。

## <a name="see-also"></a>関連項目

[Active ドキュメント コンテインメント](../mfc/active-document-containment.md)
