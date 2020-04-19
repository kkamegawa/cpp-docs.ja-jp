---
title: COleServerDoc クラス
ms.date: 11/04/2016
f1_keywords:
- COleServerDoc
- AFXOLE/COleServerDoc
- AFXOLE/COleServerDoc::COleServerDoc
- AFXOLE/COleServerDoc::ActivateDocObject
- AFXOLE/COleServerDoc::ActivateInPlace
- AFXOLE/COleServerDoc::DeactivateAndUndo
- AFXOLE/COleServerDoc::DiscardUndoState
- AFXOLE/COleServerDoc::GetClientSite
- AFXOLE/COleServerDoc::GetEmbeddedItem
- AFXOLE/COleServerDoc::GetItemClipRect
- AFXOLE/COleServerDoc::GetItemPosition
- AFXOLE/COleServerDoc::GetZoomFactor
- AFXOLE/COleServerDoc::IsDocObject
- AFXOLE/COleServerDoc::IsEmbedded
- AFXOLE/COleServerDoc::IsInPlaceActive
- AFXOLE/COleServerDoc::NotifyChanged
- AFXOLE/COleServerDoc::NotifyClosed
- AFXOLE/COleServerDoc::NotifyRename
- AFXOLE/COleServerDoc::NotifySaved
- AFXOLE/COleServerDoc::OnDeactivate
- AFXOLE/COleServerDoc::OnDeactivateUI
- AFXOLE/COleServerDoc::OnDocWindowActivate
- AFXOLE/COleServerDoc::OnResizeBorder
- AFXOLE/COleServerDoc::OnShowControlBars
- AFXOLE/COleServerDoc::OnUpdateDocument
- AFXOLE/COleServerDoc::RequestPositionChange
- AFXOLE/COleServerDoc::SaveEmbedding
- AFXOLE/COleServerDoc::ScrollContainerBy
- AFXOLE/COleServerDoc::UpdateAllItems
- AFXOLE/COleServerDoc::CreateInPlaceFrame
- AFXOLE/COleServerDoc::DestroyInPlaceFrame
- AFXOLE/COleServerDoc::GetDocObjectServer
- AFXOLE/COleServerDoc::OnClose
- AFXOLE/COleServerDoc::OnExecOleCmd
- AFXOLE/COleServerDoc::OnFrameWindowActivate
- AFXOLE/COleServerDoc::OnGetEmbeddedItem
- AFXOLE/COleServerDoc::OnReactivateAndUndo
- AFXOLE/COleServerDoc::OnSetHostNames
- AFXOLE/COleServerDoc::OnSetItemRects
- AFXOLE/COleServerDoc::OnShowDocument
helpviewer_keywords:
- COleServerDoc [MFC], COleServerDoc
- COleServerDoc [MFC], ActivateDocObject
- COleServerDoc [MFC], ActivateInPlace
- COleServerDoc [MFC], DeactivateAndUndo
- COleServerDoc [MFC], DiscardUndoState
- COleServerDoc [MFC], GetClientSite
- COleServerDoc [MFC], GetEmbeddedItem
- COleServerDoc [MFC], GetItemClipRect
- COleServerDoc [MFC], GetItemPosition
- COleServerDoc [MFC], GetZoomFactor
- COleServerDoc [MFC], IsDocObject
- COleServerDoc [MFC], IsEmbedded
- COleServerDoc [MFC], IsInPlaceActive
- COleServerDoc [MFC], NotifyChanged
- COleServerDoc [MFC], NotifyClosed
- COleServerDoc [MFC], NotifyRename
- COleServerDoc [MFC], NotifySaved
- COleServerDoc [MFC], OnDeactivate
- COleServerDoc [MFC], OnDeactivateUI
- COleServerDoc [MFC], OnDocWindowActivate
- COleServerDoc [MFC], OnResizeBorder
- COleServerDoc [MFC], OnShowControlBars
- COleServerDoc [MFC], OnUpdateDocument
- COleServerDoc [MFC], RequestPositionChange
- COleServerDoc [MFC], SaveEmbedding
- COleServerDoc [MFC], ScrollContainerBy
- COleServerDoc [MFC], UpdateAllItems
- COleServerDoc [MFC], CreateInPlaceFrame
- COleServerDoc [MFC], DestroyInPlaceFrame
- COleServerDoc [MFC], GetDocObjectServer
- COleServerDoc [MFC], OnClose
- COleServerDoc [MFC], OnExecOleCmd
- COleServerDoc [MFC], OnFrameWindowActivate
- COleServerDoc [MFC], OnGetEmbeddedItem
- COleServerDoc [MFC], OnReactivateAndUndo
- COleServerDoc [MFC], OnSetHostNames
- COleServerDoc [MFC], OnSetItemRects
- COleServerDoc [MFC], OnShowDocument
ms.assetid: a9cdd96a-e0ac-43bb-9203-2c29237e965c
ms.openlocfilehash: eec94a32fa0963d4cf2eccae0fb9e2423e75ffdc
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69503820"
---
# <a name="coleserverdoc-class"></a>COleServerDoc クラス

OLE サーバー ドキュメントの基底クラスです。

## <a name="syntax"></a>構文

```
class AFX_NOVTABLE COleServerDoc : public COleLinkingDoc
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleServerDoc::COleServerDoc](#coleserverdoc)|`COleServerDoc` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleServerDoc::ActivateDocObject](#activatedocobject)|関連付けられている DocObject ドキュメントをアクティブにします。|
|[COleServerDoc:: アクティブ](#activateinplace)|埋め込み先編集のドキュメントをアクティブにします。|
|[COleServerDoc::D e Andundo](#deactivateandundo)|サーバーのユーザーインターフェイスを非アクティブにします。|
|[COleServerDoc::D iscardUndoState](#discardundostate)|元に戻す状態の情報を破棄します。|
|[COleServerDoc:: GetClientSite](#getclientsite)|基になる`IOleClientSite`インターフェイスへのポインターを取得します。|
|[COleServerDoc::GetEmbeddedItem](#getembeddeditem)|ドキュメント全体を表す項目へのポインターを返します。|
|[COleServerDoc::GetItemClipRect](#getitemcliprect)|埋め込み先編集のための現在のクリッピング四角形を返します。|
|[COleServerDoc::GetItemPosition](#getitemposition)|埋め込み先編集のために、コンテナーアプリケーションのクライアント領域を基準とした、現在の位置の四角形を返します。|
|[COleServerDoc::GetZoomFactor](#getzoomfactor)|ズーム率をピクセル単位で返します。|
|[COleServerDoc::IsDocObject](#isdocobject)|ドキュメントが DocObject であるかどうかを判断します。|
|[COleServerDoc::IsEmbedded](#isembedded)|ドキュメントがコンテナードキュメントに埋め込まれているか、スタンドアロンで実行されているかを示します。|
|[COleServerDoc::IsInPlaceActive](#isinplaceactive)|項目が現在アクティブになっている場合は TRUE を返します。|
|[COleServerDoc:: NotifyChanged](#notifychanged)|ユーザーがドキュメントを変更したことをコンテナーに通知します。|
|[COleServerDoc:: NotifyClosed](#notifyclosed)|ユーザーがドキュメントを閉じたことをコンテナーに通知します。|
|[COleServerDoc:: NotifyRename](#notifyrename)|ユーザーがドキュメントの名前を変更したことをコンテナーに通知します。|
|[COleServerDoc:: NotifySaved](#notifysaved)|ユーザーがドキュメントを保存したことをコンテナーに通知します。|
|[COleServerDoc:: OnDeactivate](#ondeactivate)|インプレースでアクティブ化された項目をユーザーが非アクティブにしたときに、フレームワークによって呼び出されます。|
|[COleServerDoc:: Ondeアクティブ化 Ui](#ondeactivateui)|組み込みのアクティベーション用に作成されたコントロールおよびその他のユーザーインターフェイス要素を破棄するために、フレームワークによって呼び出されます。|
|[COleServerDoc::OnDocWindowActivate](#ondocwindowactivate)|コンテナーのドキュメントフレームウィンドウがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。|
|[COleServerDoc::OnResizeBorder](#onresizeborder)|コンテナーアプリケーションのフレームウィンドウまたはドキュメントウィンドウのサイズが変更されたときにフレームワークによって呼び出されます。|
|[COleServerDoc:: OnShowControlBars](#onshowcontrolbars)|埋め込み先編集のコントロールバーを表示または非表示にするために、フレームワークによって呼び出されます。|
|[COleServerDoc:: OnUpdateDocument](#onupdatedocument)|埋め込み項目であるサーバードキュメントが保存されるときにフレームワークによって呼び出され、コンテナーの項目のコピーを更新します。|
|[COleServerDoc::RequestPositionChange](#requestpositionchange)|埋め込み先編集フレームの位置を変更します。|
|[COleServerDoc:: SaveEmbedding 込み](#saveembedding)|ドキュメントを保存するようにコンテナーアプリケーションに指示します。|
|[COleServerDoc::ScrollContainerBy](#scrollcontainerby)|コンテナードキュメントをスクロールします。|
|[COleServerDoc::UpdateAllItems](#updateallitems)|ユーザーがドキュメントを変更したことをコンテナーに通知します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[COleServerDoc:: Createinplace フレーム](#createinplaceframe)|埋め込み先編集のためのフレームウィンドウを作成するために、フレームワークによって呼び出されます。|
|[COleServerDoc::D estroyInPlaceFrame](#destroyinplaceframe)|埋め込み先編集のフレームウィンドウを破棄するために、フレームワークによって呼び出されます。|
|[COleServerDoc::GetDocObjectServer](#getdocobjectserver)|この関数をオーバーライドして新しい`CDocObjectServer`オブジェクトを作成し、このドキュメントが DocObject コンテナーであることを示します。|
|[COleServerDoc:: OnClose](#onclose)|コンテナーがドキュメントを閉じるように要求したときに、フレームワークによって呼び出されます。|
|[COleServerDoc::OnExecOleCmd](#onexecolecmd)|指定されたコマンドを実行するか、コマンドのヘルプを表示します。|
|[COleServerDoc:: OnFrameWindowActivate](#onframewindowactivate)|コンテナーのフレームウィンドウがアクティブ化または非アクティブ化されたときにフレームワークによって呼び出されます。|
|[COleServerDoc::OnGetEmbeddedItem](#ongetembeddeditem)|文書全体を表す`COleServerItem`を取得するために呼び出されます。埋め込み項目を取得するために使用されます。 実装が必要です。|
|[COleServerDoc:: Onre Andundo](#onreactivateandundo)|インプレース編集中に行われた変更を元に戻すために、フレームワークによって呼び出されます。|
|[COleServerDoc:: OnSetHostNames](#onsethostnames)|コンテナーが埋め込みオブジェクトのウィンドウタイトルを設定するときに、フレームワークによって呼び出されます。|
|[COleServerDoc::OnSetItemRects](#onsetitemrects)|コンテナーアプリケーションのウィンドウ内に埋め込み先編集フレームウィンドウを配置するために、フレームワークによって呼び出されます。|
|[COleServerDoc:: OnShowDocument](#onshowdocument)|ドキュメントを表示または非表示にするためにフレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

サーバードキュメントには、埋め込みまたはリンクされたアイテムへのサーバーインターフェイスを表す、 [COleServerItem](../../mfc/reference/coleserveritem-class.md)オブジェクトを含めることができます。 埋め込みアイテムを編集するためにコンテナーによってサーバーアプリケーションが起動されると、そのアイテムは専用のサーバードキュメントとして読み込まれます。オブジェクト`COleServerDoc`には、ドキュメント`COleServerItem`全体で構成されるオブジェクトが1つだけ含まれています。 サーバーアプリケーションが、リンクされた項目を編集するためにコンテナーによって起動されると、既存のドキュメントがディスクから読み込まれます。ドキュメントの内容の一部が強調表示され、リンクされた項目が示されます。

`COleServerDoc`オブジェクトには、 [COleClientItem](../../mfc/reference/coleclientitem-class.md)クラスの項目を含めることもできます。 これにより、コンテナーサーバーアプリケーションを作成できます。 フレームワークには、オブジェクトの`COleClientItem` `COleServerItem`処理中に項目を適切に格納する関数が用意されています。

サーバーアプリケーションでリンクがサポートされていない場合、サーバードキュメントには、埋め込みオブジェクト全体をドキュメントとして表すサーバー項目が常に1つだけ含まれます。 サーバーアプリケーションがリンクをサポートしている場合は、選択項目がクリップボードにコピーされるたびに、サーバー項目を作成する必要があります。

を使用`COleServerDoc`するには、このクラスからクラスを派生させ、 [OnGetEmbeddedItem](#ongetembeddeditem)メンバー関数を実装します。これにより、埋め込みアイテムをサーバーでサポートできるようになります。 から`COleServerItem`クラスを派生させて、ドキュメント内に項目を実装し、そのクラスの`OnGetEmbeddedItem`オブジェクトをから返します。

リンクされた項目`COleServerDoc`をサポートするために、には[OnGetLinkedItem](../../mfc/reference/colelinkingdoc-class.md#ongetlinkeditem)メンバー関数が用意されています。 ドキュメントアイテムを管理する独自の方法がある場合は、既定の実装を使用するか、上書きすることができます。

アプリケーションでサポート`COleServerDoc`されているサーバードキュメントの種類ごとに、1つの派生クラスが必要です。 たとえば、サーバーアプリケーションでワークシートとグラフがサポートされている`COleServerDoc`場合は、2つの派生クラスが必要です。

サーバーの詳細については、「 [サーバー:サーバー](../../mfc/servers-implementing-a-server.md)の実装。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocument](../../mfc/reference/cdocument-class.md)

[COleDocument](../../mfc/reference/coledocument-class.md)

[COleLinkingDoc](../../mfc/reference/colelinkingdoc-class.md)

`COleServerDoc`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole

##  <a name="activatedocobject"></a>COleServerDoc::ActivateDocObject

関連付けられている DocObject ドキュメントをアクティブにします。

```
void ActivateDocObject();
```

### <a name="remarks"></a>Remarks

既定では`COleServerDoc` 、はアクティブなドキュメント (DocObjects とも呼ばれます) をサポートしていません。 このサポートを有効にするには、「 [GetDocObjectServer](#getdocobjectserver) And class [CDocObjectServer](../../mfc/reference/cdocobjectserver-class.md)」を参照してください。

##  <a name="activateinplace"></a>COleServerDoc:: アクティブ

埋め込み先編集の項目をアクティブにします。

```
BOOL ActivateInPlace();
```

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。項目が完全に開いていることを示します。

### <a name="remarks"></a>Remarks

この関数は、インプレースアクティベーションに必要なすべての操作を実行します。 埋め込み先フレームウィンドウを作成し、アクティブ化して項目にサイズを設定し、共有メニューやその他のコントロールを設定し、項目をスクロールして表示し、フォーカスを埋め込み先フレームウィンドウに設定します。

この関数は、 [COleServerItem:: OnShow](../../mfc/reference/coleserveritem-class.md#onshow)の既定の実装によって呼び出されます。 アプリケーションがインプレースアクティベーション (Play など) のために別の動詞をサポートする場合は、この関数を呼び出します。

##  <a name="coleserverdoc"></a>COleServerDoc::COleServerDoc

OLE システム`COleServerDoc` dll と接続せずにオブジェクトを構築します。

```
COleServerDoc();
```

### <a name="remarks"></a>Remarks

OLE との通信を開くには、 [COleLinkingDoc:: Register](../../mfc/reference/colelinkingdoc-class.md#register)を呼び出す必要があります。 アプリケーション`OnOpenDocument` `OnSaveDocument` `COleLinkingDoc` `OnNewDocument` `COleLinkingDoc::Register`で[COleTemplateServer](../../mfc/reference/coletemplateserver-class.md)を使用している場合は、、、およびの実装によってが呼び出されます。

##  <a name="createinplaceframe"></a>COleServerDoc:: Createinplace フレーム

フレームワークは、この関数を呼び出して、埋め込み先編集用のフレームウィンドウを作成します。

```
virtual COleIPFrameWnd* CreateInPlaceFrame(CWnd* pParentWnd);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
コンテナーアプリケーションの親ウィンドウへのポインター。

### <a name="return-value"></a>戻り値

埋め込み先フレームウィンドウへのポインター。失敗した場合は NULL。

### <a name="remarks"></a>Remarks

既定の実装では、ドキュメントテンプレートに指定された情報を使用してフレームを作成します。 使用されるビューは、ドキュメントに対して作成された最初のビューです。 このビューは、元のフレームから一時的にデタッチされ、新しく作成されたフレームにアタッチされます。

これは高度なオーバーライド可能です。

##  <a name="deactivateandundo"></a>COleServerDoc::D e Andundo

アプリケーションが元に戻す操作をサポートし、ユーザーが項目をアクティブ化した後、編集する前に [元に戻す] を選択した場合は、この関数を呼び出します。

```
BOOL DeactivateAndUndo();
```

### <a name="return-value"></a>戻り値

正常に完了した場合はゼロ以外、それ以外の場合は 0 です。

### <a name="remarks"></a>Remarks

Microsoft Foundation Class ライブラリを使用してコンテナーアプリケーションが記述されている場合、この関数を呼び出すと、 [COleClientItem:: Onde Andundo](../../mfc/reference/coleclientitem-class.md#ondeactivateandundo)が呼び出され、サーバーのユーザーインターフェイスが非アクティブになります。

##  <a name="destroyinplaceframe"></a>COleServerDoc::D estroyInPlaceFrame

フレームワークは、この関数を呼び出して、埋め込み先フレームウィンドウを破棄し、サーバーアプリケーションのドキュメントウィンドウをその状態に戻します。

```
virtual void DestroyInPlaceFrame(COleIPFrameWnd* pFrameWnd);
```

### <a name="parameters"></a>パラメーター

*pFrameWnd*<br/>
破棄する埋め込み先フレームウィンドウへのポインター。

### <a name="remarks"></a>Remarks

これは高度なオーバーライド可能です。

##  <a name="discardundostate"></a>COleServerDoc::D iscardUndoState

元に戻すことができない編集操作をユーザーが実行する場合は、この関数を呼び出して、コンテナーアプリケーションが元に戻す状態の情報を破棄するように強制します。

```
BOOL DiscardUndoState();
```

### <a name="return-value"></a>戻り値

正常に完了した場合はゼロ以外、それ以外の場合は 0 です。

### <a name="remarks"></a>Remarks

この関数は、Undo をサポートするサーバーが、使用できない元に戻す状態の情報によって使用されるリソースを解放できるようにするために用意されています。

##  <a name="getclientsite"></a>COleServerDoc:: GetClientSite

基になる`IOleClientSite`インターフェイスへのポインターを取得します。

```
LPOLECLIENTSITE GetClientSite() const;
```

### <a name="return-value"></a>戻り値

基になる[IOleClientSite](/windows/win32/api/oleidl/nn-oleidl-ioleclientsite)インターフェイスへのポインターを取得します。

##  <a name="getdocobjectserver"></a>COleServerDoc::GetDocObjectServer

新しい`CDocObjectServer`項目を作成し、その項目へのポインターを返すには、この関数をオーバーライドします。

```
virtual CDocObjectServer* GetDocObjectServer(LPOLEDOCUMENTSITE pDocSite);
```

### <a name="parameters"></a>パラメーター

*pDocSite*<br/>
このドキュメントを`IOleDocumentSite`サーバーに接続するインターフェイスへのポインター。

### <a name="return-value"></a>戻り値

へのポインター `CDocObjectServer`。操作が失敗した場合は NULL。

### <a name="remarks"></a>Remarks

DocObject サーバーがアクティブになると、NULL 以外のポインターが返され、クライアントが DocObjects をサポートできることが示されます。 既定の実装では、NULL が返されます。

DocObjects をサポートするドキュメントの一般的な実装では、新しい`CDocObjectServer`オブジェクトを割り当てて呼び出し元に返すだけです。 例えば:

[!code-cpp[NVC_MFCOleServer#3](../../mfc/codesnippet/cpp/coleserverdoc-class_1.cpp)]

##  <a name="getembeddeditem"></a>  COleServerDoc::GetEmbeddedItem

ドキュメント全体を表す項目へのポインターを取得するには、この関数を呼び出します。

```
COleServerItem* GetEmbeddedItem();
```

### <a name="return-value"></a>戻り値

ドキュメント全体を表す項目へのポインター。操作が失敗した場合は NULL。

### <a name="remarks"></a>Remarks

既定の実装のない仮想関数[COleServerDoc:: OnGetEmbeddedItem](#ongetembeddeditem)を呼び出します。

##  <a name="getitemcliprect"></a>COleServerDoc::GetItemClipRect

`GetItemClipRect`メンバー関数を呼び出して、埋め込み先で編集されている項目のクリッピング四角形の座標を取得します。

```
void GetItemClipRect(LPRECT lpClipRect) const;
```

### <a name="parameters"></a>パラメーター

*lpClipRect*<br/>
項目のクリッピング`RECT`四角形の座標`CRect`を受け取る構造体またはオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

座標は、コンテナーアプリケーションウィンドウのクライアント領域に対して相対的にピクセル単位で表されます。

クリッピング四角形の外側に描画を行うことはできません。 通常、描画は自動的に制限されます。 この関数を使用すると、ユーザーがドキュメントの表示部分の外にスクロールしたかどうかを確認できます。その場合は、 [ScrollContainerBy](#scrollcontainerby)を呼び出すことによって、必要に応じてコンテナードキュメントをスクロールします。

##  <a name="getitemposition"></a>COleServerDoc::GetItemPosition

`GetItemPosition`メンバー関数を呼び出して、編集中の項目の座標を取得します。

```
void GetItemPosition(LPRECT lpPosRect) const;
```

### <a name="parameters"></a>パラメーター

*lpPosRect*<br/>
項目の座標`RECT`を受け取る構造`CRect`体またはオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

座標は、コンテナーアプリケーションウィンドウのクライアント領域に対して相対的にピクセル単位で表されます。

項目の位置と現在のクリッピング四角形を比較して、画面上で項目が表示される (または表示されない) 範囲を決定できます。

##  <a name="getzoomfactor"></a>COleServerDoc::GetZoomFactor

この`GetZoomFactor`メンバー関数は、埋め込み先編集のためにアクティブ化された項目の "ズームファクター" を決定します。

```
BOOL GetZoomFactor(
    LPSIZE lpSizeNum = NULL,
    LPSIZE lpSizeDenom = NULL,
    LPCRECT lpPosRect = NULL) const;
```

### <a name="parameters"></a>パラメーター

*lpSizeNum 型*<br/>
ズームファクターの分子を保持`CSize`するクラスのオブジェクトへのポインター。 NULL を指定できます。

*lpSizeDenom*<br/>
ズームファクターの分母を保持`CSize`するクラスのオブジェクトへのポインター。 NULL を指定できます。

*lpPosRect*<br/>
項目の新しい位置を記述`CRect`するクラスのオブジェクトへのポインター。 この引数が NULL の場合、関数は項目の現在位置を使用します。

### <a name="return-value"></a>戻り値

項目が埋め込み先編集のためにアクティブになっており、その拡大率が 100% (1:1) 以外の場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

ズーム率は、現在の範囲に対する項目のサイズの比率で、ピクセル単位で表示されます。 コンテナーアプリケーションで項目の範囲が設定されていない場合は、( [COleServerItem:: OnGetExtent](../../mfc/reference/coleserveritem-class.md#ongetextent)によって決定されるように) 自然なエクステントが使用されます。

関数は、最初の2つの引数を項目の "ズーム係数" の分子と分母に設定します。 項目がインプレースで編集されていない場合、関数はこれらの引数を既定値の 100% (または 1:1) に設定し、0を返します。 詳細については、「テクニカルノート40、 [MFC/OLE の埋め込み先のサイズ変更とズーム](../../mfc/tn040-mfc-ole-in-place-resizing-and-zooming.md)」を参照してください。

##  <a name="isdocobject"></a>  COleServerDoc::IsDocObject

ドキュメントが DocObject であるかどうかを判断します。

```
BOOL IsDocObject() const;
```

### <a name="return-value"></a>戻り値

ドキュメントが DocObject の場合は TRUE。それ以外の場合は FALSE。

##  <a name="isembedded"></a>  COleServerDoc::IsEmbedded

メンバー関数`IsEmbedded`を呼び出して、ドキュメントがコンテナーに埋め込まれたオブジェクトを表しているかどうかを確認します。

```
BOOL IsEmbedded() const;
```

### <a name="return-value"></a>戻り値

`COleServerDoc`オブジェクトがコンテナーに埋め込まれたオブジェクトを表すドキュメントである場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

ファイルから読み込まれたドキュメントは埋め込まれませんが、コンテナーアプリケーションによってリンクとして操作される可能性があります。 コンテナードキュメントに埋め込まれているドキュメントは、埋め込まれていると見なされます。

##  <a name="isinplaceactive"></a>COleServerDoc::IsInPlaceActive

`IsInPlaceActive`メンバー関数を呼び出して、項目が現在インプレースアクティブ状態であるかどうかを確認します。

```
BOOL IsInPlaceActive() const;
```

### <a name="return-value"></a>戻り値

オブジェクトが配置`COleServerDoc`されている場合は0以外。それ以外の場合は0。

##  <a name="notifychanged"></a>  COleServerDoc::NotifyChanged

ドキュメントが変更されたことをドキュメントに接続しているすべてのリンク項目を通知するには、この関数を呼び出します。

```
void NotifyChanged();
```

### <a name="remarks"></a>Remarks

通常、この関数は、ユーザーがサーバードキュメントのディメンションなどの一部のグローバル属性を変更した後に呼び出されます。 OLE 項目が自動リンクを使用してドキュメントにリンクされている場合、その項目は変更内容を反映して更新されます。 Microsoft Foundation Class ライブラリで記述されたコンテナーアプリケーションでは、の`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) メンバー関数が呼び出されます。

> [!NOTE]
>  この関数は、OLE 1 との互換性のために用意されています。 新しいアプリケーションでは[UpdateAllItems](#updateallitems)を使用する必要があります。

##  <a name="notifyclosed"></a>  COleServerDoc::NotifyClosed

ドキュメントが閉じられたことをコンテナーに通知するには、この関数を呼び出します。

```
void NotifyClosed();
```

### <a name="remarks"></a>Remarks

ユーザーが [ファイル] メニューから [閉じる] を選択`NotifyClosed`すると、 `COleServerDoc`は、 [onclosedocument](../../mfc/reference/cdocument-class.md#onclosedocument)メンバー関数の実装によって呼び出されます。 Microsoft Foundation Class ライブラリで記述されたコンテナーアプリケーションでは、の`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) メンバー関数が呼び出されます。

##  <a name="notifyrename"></a>  COleServerDoc::NotifyRename

ユーザーがサーバードキュメントの名前を変更した後に、この関数を呼び出します。

```
void NotifyRename(LPCTSTR lpszNewName);
```

### <a name="parameters"></a>パラメーター

*lpszNewName*<br/>
サーバードキュメントの新しい名前を指定する文字列へのポインターです。これは通常、完全修飾パスです。

### <a name="remarks"></a>Remarks

ユーザーが [ファイル] メニューから [名前を付けて保存`NotifyRename` ] コマンドを`COleServerDoc`選択すると、は、 [onsavedocument](../../mfc/reference/cdocument-class.md#onsavedocument)メンバー関数の実装によって呼び出されます。 この関数は、OLE システム Dll に通知し、次にコンテナーに通知します。 Microsoft Foundation Class ライブラリで記述されたコンテナーアプリケーションでは、の`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) メンバー関数が呼び出されます。

##  <a name="notifysaved"></a>COleServerDoc:: NotifySaved

ユーザーがサーバードキュメントを保存した後に、この関数を呼び出します。

```
void NotifySaved();
```

### <a name="remarks"></a>Remarks

ユーザーが [ファイル] メニューから [保存] コマンドを`NotifySaved`選択すると、 [onsavedocument](../../mfc/reference/cdocument-class.md#onsavedocument)の実装によって`COleServerDoc`が呼び出されます。 この関数は、OLE システム Dll に通知し、次にコンテナーに通知します。 Microsoft Foundation Class ライブラリで記述されたコンテナーアプリケーションでは、の`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) メンバー関数が呼び出されます。

##  <a name="onclose"></a>  COleServerDoc::OnClose

コンテナーがサーバードキュメントを閉じるように要求したときに、フレームワークによって呼び出されます。

```
virtual void OnClose(OLECLOSE dwCloseOption);
```

### <a name="parameters"></a>パラメーター

*dwCloseOption*<br/>
列挙 OLECLOSE の値。 このパラメーターには、次のいずれかの値を指定できます。

- OLECLOSE_SAVEIFDIRTY ファイルが変更されている場合は保存されます。

- OLECLOSE_NOSAVE ファイルは保存されずに閉じられます。

- OLECLOSE_PROMPTSAVE ファイルが変更されている場合、ユーザーは保存を求めるメッセージが表示されます。

### <a name="remarks"></a>Remarks

既定の実装で`CDocument::OnCloseDocument`は、が呼び出されます。

詳細およびその他の値については、Windows SDK の「 [OLECLOSE](/windows/win32/api/oleidl/ne-oleidl-oleclose) 」を参照してください。

##  <a name="ondeactivate"></a>COleServerDoc:: OnDeactivate

現在アクティブになっている埋め込み項目またはリンクされた項目をユーザーが非アクティブ化するときに、フレームワークによって呼び出されます。

```
virtual void OnDeactivate();
```

### <a name="remarks"></a>Remarks

この関数は、コンテナーアプリケーションのユーザーインターフェイスを元の状態に復元し、インプレースアクティブ化のために作成されたメニューやその他のコントロールを破棄します。

この時点で、元に戻す状態の情報を無条件に解放する必要があります。

詳細については、記事を参照してください[アクティベーション](../../mfc/activation-cpp.md)..

##  <a name="ondeactivateui"></a>COleServerDoc:: Ondeアクティブ化 Ui

インプレースでアクティブ化された項目をユーザーが非アクティブにしたときに呼び出されます。

```
virtual void OnDeactivateUI(BOOL bUndoable);
```

### <a name="parameters"></a>パラメーター

*bUndoable*<br/>
編集の変更を元に戻すことができるかどうかを指定します。

### <a name="remarks"></a>Remarks

この関数は、コンテナーアプリケーションのユーザーインターフェイスを元の状態に復元し、埋め込み先アクティベーション用に作成されたメニューやその他のコントロールを非表示にします。

フレームワークは常に*bUndoable*を FALSE に設定します。 サーバーが元に戻す操作をサポートしていて、元に戻すことができる操作がある場合は、 *bUndoable*を TRUE に設定して基本クラスの実装を呼び出します。

##  <a name="ondocwindowactivate"></a>  COleServerDoc::OnDocWindowActivate

フレームワークは、この関数を呼び出して、埋め込み先編集のためにドキュメントウィンドウをアクティブ化または非アクティブ化します。

```
virtual void OnDocWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>パラメーター

*bActivate*<br/>
ドキュメントウィンドウをアクティブにするか非アクティブにするかを指定します。

### <a name="remarks"></a>Remarks

既定の実装では、必要に応じて、フレームレベルのユーザーインターフェイス要素が削除または追加されます。 項目が含まれているドキュメントがアクティブ化または非アクティブ化されたときに追加のアクションを実行する場合は、この関数をオーバーライドします。

詳細については、記事を参照してください[アクティベーション](../../mfc/activation-cpp.md)..

##  <a name="onexecolecmd"></a>COleServerDoc::OnExecOleCmd

フレームワークは、この関数を呼び出して、指定されたコマンドを実行したり、コマンドのヘルプを表示したりします。

```
virtual HRESULT OnExecOleCmd(
    const GUID* pguidCmdGroup,
    DWORD nCmdID,
    DWORD nCmdExecOpt,
    VARIANTARG* pvarargIn,
    VARIANTARG* pvarargOut);
```

### <a name="parameters"></a>パラメーター

*pguidCmdGroup*<br/>
コマンドのセットを識別する GUID へのポインター。 NULL を指定すると、既定のコマンドグループを示すことができます。

*nCmdID*<br/>
実行するコマンド。 *Pguidcmdgroup*によって識別されるグループに存在する必要があります。

*nCmdExecOut*<br/>
オブジェクトがコマンドを実行する方法。 OLECMDEXECOPT 列挙から、次の1つ以上の値を指定します。

OLECMDEXECOPT_DODEFAULT

OLECMDEXECOPT_PROMPTUSER

OLECMDEXECOPT_DONTPROMPTUSER

OLECMDEXECOPT_SHOWHELP

*pvarargIn*<br/>
コマンドの入力引数を格納している VARIANTARG へのポインター。 NULL を指定できます。

*pvarargOut*<br/>
コマンドから出力戻り値を受け取る VARIANTARG へのポインター。 NULL を指定できます。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返します。それ以外の場合は、次のエラーコードのいずれかになります。

|値|説明|
|-----------|-----------------|
|E_UNEXPECTED|予期しないエラーが発生しました|
|E_FAIL|エラーが発生しました|
|E_NOTIMPL|MFC 自体がコマンドの変換とディスパッチを試みる必要があることを示します。|
|OLECMDERR_E_UNKNOWNGROUP|*Pguidcmdgroup*は NULL 以外ですが、認識されたコマンドグループを指定していません|
|OLECMDERR_E_NOTSUPPORTED|*Ncmdid*はグループ*pguidcmdgroup*の有効なコマンドとして認識されません|
|OLECMDERR_DISABLED|*Ncmdid*で識別されたコマンドは無効になっているため、実行できません|
|OLECMDERR_NOHELP|呼び出し元は*Ncmdid*で識別されたコマンドに関するヘルプを要求しましたが、ヘルプはありません|
|OLECMDERR_CANCELED|ユーザーが実行を取り消しました|

### <a name="remarks"></a>Remarks

`COleCmdUI`DocObject user interface コマンドの他のプロパティを有効にしたり、更新したり、設定したりするために使用できます。 コマンドが初期化されたら、を使用して`OnExecOleCmd`コマンドを実行できます。

フレームワークは、OLE ドキュメントコマンドの変換とディスパッチを試行する前に関数を呼び出します。 標準の OLE ドキュメントコマンドを処理するためにこの関数をオーバーライドする必要はありませんが、独自のカスタムコマンドを処理する場合や、パラメーターを受け取ったり結果を返したりするコマンドを処理する場合は、この関数のオーバーライドを指定する必要があります。

ほとんどのコマンドは、引数または戻り値を受け取りません。 ほとんどのコマンドでは、呼び出し元は*pvarargIn*と*pvarargOut*に null を渡すことができます。 入力値を必要とするコマンドの場合、呼び出し元は VARIANTARG 変数を宣言して初期化し、 *pvarargIn*内の変数へのポインターを渡すことができます。 1つの値を必要とするコマンドの場合、引数を VARIANTARG に直接格納し、関数に渡すことができます。 サポートされている型 ( `IDispatch`や SAFEARRAY など) のいずれかを使用して、VARIANTARG 内に複数の引数をパッケージ化する必要があります。

同様に、コマンドから引数が返された場合、呼び出し元は VARIANTARG を宣言し、それを VT_EMPTY に初期化し、そのアドレスを*pvarargOut*に渡す必要があります。 コマンドが単一の値を返す場合、オブジェクトはその値を*pvarargOut*に直接格納できます。 複数の出力値は、VARIANTARG に適した方法でパッケージ化する必要があります。

この関数の基本クラスの実装では、コマンドターゲットに関連付けられている OLE_COMMAND_MAP 構造体をウォークし、適切なハンドラーにコマンドをディスパッチします。 基底クラスの実装は、引数または戻り値を受け取らないコマンドでのみ動作します。 引数または戻り値を受け入れるコマンドを処理する必要がある場合は、この関数をオーバーライドし、 *pvarargIn*パラメーターと*pvarargOut*パラメーターを自分で操作する必要があります。

##  <a name="onframewindowactivate"></a>COleServerDoc:: OnFrameWindowActivate

フレームワークは、コンテナーアプリケーションのフレームウィンドウがアクティブ化または非アクティブ化されたときに、この関数を呼び出します。

```
virtual void OnFrameWindowActivate(BOOL bActivate);
```

### <a name="parameters"></a>パラメーター

*bActivate*<br/>
フレームウィンドウをアクティブにするか非アクティブにするかを指定します。

### <a name="remarks"></a>Remarks

既定の実装では、フレームウィンドウのすべてのヘルプモードがキャンセルされます。 フレームウィンドウがアクティブ化または非アクティブ化されたときに特殊な処理を実行する場合は、この関数をオーバーライドします。

詳細については、記事を参照してください[アクティベーション](../../mfc/activation-cpp.md)..

##  <a name="ongetembeddeditem"></a>  COleServerDoc::OnGetEmbeddedItem

コンテナーアプリケーションが、埋め込み項目を作成または編集するためにサーバーアプリケーションを呼び出すときに、フレームワークによって呼び出されます。

```
virtual COleServerItem* OnGetEmbeddedItem() = 0;
```

### <a name="return-value"></a>戻り値

ドキュメント全体を表す項目へのポインター。操作が失敗した場合は NULL。

### <a name="remarks"></a>Remarks

既定の実装はありません。 ドキュメント全体を表す項目を返すには、この関数をオーバーライドする必要があります。 この戻り値は、 `COleServerItem`から派生したクラスのオブジェクトである必要があります。

##  <a name="onreactivateandundo"></a>COleServerDoc:: Onre Andundo

この関数は、ユーザーが、インプレースでアクティブ化され、変更され、その後、非アクティブになった項目に対して行われた変更を元に戻すことを選択した場合に、この関数を呼び出します。

```
virtual BOOL OnReactivateAndUndo();
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

既定の実装では、失敗を示すために FALSE を返す以外は何も行いません。

アプリケーションが元に戻す操作をサポートしている場合は、この関数をオーバーライドします。 通常は、元に戻す操作を実行してから、を`ActivateInPlace`呼び出して項目をアクティブにします。 コンテナーアプリケーションが Microsoft Foundation Class ライブラリで記述されている場合`COleClientItem::ReactivateAndUndo` 、を呼び出すと、この関数が呼び出されます。

##  <a name="onresizeborder"></a>  COleServerDoc::OnResizeBorder

フレームワークは、コンテナーアプリケーションのフレームウィンドウのサイズが変更されたときに、この関数を呼び出します。

```
virtual void OnResizeBorder(
    LPCRECT lpRectBorder,
    LPOLEINPLACEUIWINDOW lpUIWindow,
    BOOL bFrame);
```

### <a name="parameters"></a>パラメーター

*lpRectBorder*<br/>
境界線の`RECT`座標を指定`CRect`する構造体またはオブジェクトへのポインター。

*lpUIWindow*<br/>
現在の埋め込み先編集`IOleInPlaceUIWindow`セッションを所有するクラスのオブジェクトへのポインター。

*bFrame*<br/>
*Lpuiwindow*がコンテナーアプリケーションの最上位のフレームウィンドウを指している場合は TRUE、 *lpuiwindow*がコンテナーアプリケーションのドキュメントレベルのフレームウィンドウを指している場合は FALSE。

### <a name="remarks"></a>Remarks

この関数は、新しいウィンドウサイズに従って、ツールバーとその他のユーザーインターフェイス要素のサイズを変更し、調整します。

詳細については、Windows SDK の「 [IOleInPlaceUIWindow](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceuiwindow) 」を参照してください。

これは高度なオーバーライド可能です。

##  <a name="onsethostnames"></a>  COleServerDoc::OnSetHostNames

コンテナーがこのドキュメントのホスト名を設定または変更するときに、フレームワークによって呼び出されます。

```
virtual void OnSetHostNames(
    LPCTSTR lpszHost,
    LPCTSTR lpszHostObj);
```

### <a name="parameters"></a>パラメーター

*lpszHost*<br/>
コンテナーアプリケーションの名前を指定する文字列へのポインター。

*lpszHostObj*<br/>
ドキュメントのコンテナー名を指定する文字列へのポインター。

### <a name="remarks"></a>Remarks

既定の実装では、このドキュメントを参照するすべてのビューのドキュメントタイトルが変更されます。

アプリケーションが別のメカニズムを使用してタイトルを設定する場合は、この関数をオーバーライドします。

##  <a name="onsetitemrects"></a>COleServerDoc::OnSetItemRects

フレームワークは、この関数を呼び出して、コンテナーアプリケーションのフレームウィンドウ内に埋め込み先編集フレームウィンドウを配置します。

```
virtual void OnSetItemRects(
    LPCRECT lpPosRect,
    LPCRECT lpClipRect);
```

### <a name="parameters"></a>パラメーター

*lpPosRect*<br/>
コンテナーアプリケーションの`RECT`クライアント領域を`CRect`基準とした、埋め込み先フレームウィンドウの位置を指定する構造体またはオブジェクトへのポインター。

*lpClipRect*<br/>
コンテナーアプリケーションの`RECT`クライアント領域を`CRect`基準とした、埋め込み先フレームウィンドウのクリッピング四角形を指定する構造体またはオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

必要に応じて、この関数をオーバーライドして、ビューのズームファクターを更新します。

通常、この関数は`RequestPositionChange`呼び出しへの応答として呼び出されますが、埋め込み先項目の位置の変更を要求するためにコンテナーによっていつでも呼び出すことができます。

##  <a name="onshowcontrolbars"></a>  COleServerDoc::OnShowControlBars

フレームワークは、 *pFrameWnd*で識別されるフレームウィンドウに関連付けられているサーバーアプリケーションのコントロールバーを表示または非表示にするために、この関数を呼び出します。

```
virtual void OnShowControlBars(
    CFrameWnd* pFrameWnd,
    BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*pFrameWnd*<br/>
コントロールバーを非表示または表示するフレームウィンドウへのポインター。

*bShow*<br/>
コントロールバーを表示するか非表示にするかを決定します。

### <a name="remarks"></a>Remarks

既定の実装は、そのフレームウィンドウによって所有されるすべてのコントロールバーを列挙し、それらを非表示にしたり表示したりします。

##  <a name="onshowdocument"></a>  COleServerDoc::OnShowDocument

サーバードキュメントを非`OnShowDocument`表示にしたり表示したりする必要がある場合、フレームワークは関数を呼び出します。

```
virtual void OnShowDocument(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
ドキュメントへのユーザーインターフェイスを表示するか非表示にするかを指定します。

### <a name="remarks"></a>Remarks

*BShow*が TRUE の場合、必要に応じて既定の実装によってサーバーアプリケーションがアクティブ化され、項目が表示されるように、コンテナーアプリケーションによってウィンドウがスクロールされます。 *BShow*が FALSE の場合、既定の実装では、の呼び出し`OnDeactivate`によって項目が非アクティブ化された後、最初のフレームを除く、ドキュメント用に作成されたすべてのフレームウィンドウを破棄または非表示にします。 表示されているドキュメントが残っていない場合、既定の実装ではサーバーアプリケーションが非表示になります。

##  <a name="onupdatedocument"></a>COleServerDoc:: OnUpdateDocument

複合ドキュメントに埋め込まれた項目であるドキュメントを保存するときに、フレームワークによって呼び出されます。

```
virtual BOOL OnUpdateDocument();
```

### <a name="return-value"></a>戻り値

ドキュメントが正常に更新された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

既定の実装は、 [COleServerDoc:: NotifySaved](#notifysaved)および[COleServerDoc:: saveembedding 込み](#saveembedding)メンバー関数を呼び出し、ドキュメントをクリーンとしてマークします。 埋め込み項目を更新するときに特別な処理を実行する場合は、この関数をオーバーライドします。

##  <a name="requestpositionchange"></a>  COleServerDoc::RequestPositionChange

このメンバー関数を呼び出して、コンテナーアプリケーションで項目の位置を変更します。

```
void RequestPositionChange(LPCRECT lpPosRect);
```

### <a name="parameters"></a>パラメーター

*lpPosRect*<br/>
項目の新しい`RECT`位置を格納`CRect`している構造体またはオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

この関数は、通常、埋め込み先`UpdateAllItems`のアクティブな項目のデータが変更された場合に、と共に呼び出されます。 この呼び出しの後、コンテナーはを呼び出す`OnSetItemRects`ことによって変更を実行できない場合があります。 結果として得られる位置は、要求されたものと異なる場合があります。

##  <a name="saveembedding"></a>COleServerDoc:: SaveEmbedding 込み

埋め込みオブジェクトを保存するようにコンテナーアプリケーションに指示するには、この関数を呼び出します。

```
void SaveEmbedding();
```

### <a name="remarks"></a>Remarks

この関数は、から`OnUpdateDocument`自動的に呼び出されます。 この関数によってディスク上の項目が更新されるため、通常は特定のユーザー操作の結果としてのみ呼び出されることに注意してください。

##  <a name="scrollcontainerby"></a>COleServerDoc::ScrollContainerBy

メンバー関数を呼び出して、で`sizeScroll`示されている量 (ピクセル単位) でコンテナードキュメントをスクロールします。 `ScrollContainerBy`

```
BOOL ScrollContainerBy(CSize sizeScroll);
```

### <a name="parameters"></a>パラメーター

*sizeScroll*<br/>
コンテナードキュメントをスクロールする距離を示します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

正の値は、スクロールダウンと右側の値を示します。負の値は、左右にスクロールすることを示します。

##  <a name="updateallitems"></a>  COleServerDoc::UpdateAllItems

ドキュメントが変更されたことをドキュメントに接続しているすべてのリンク項目を通知するには、この関数を呼び出します。

```
void UpdateAllItems(
    COleServerItem* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL,
    DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>パラメーター

*pSender*<br/>
ドキュメントを変更した項目へのポインター。すべての項目が更新される場合は NULL。

*lHint*<br/>
変更に関する情報を格納します。

*pHint*<br/>
変更に関する情報を格納しているオブジェクトへのポインター。

*nDrawAspect*<br/>
項目の描画方法を決定します。 これは DVASPECT 列挙子の値です。 このパラメーターには、次のいずれかの値を指定できます。

- DVASPECT_CONTENT Item は、コンテナー内に埋め込みオブジェクトとして表示できるように表現されます。

- なりますが項目は、参照ツールで表示できるように "サムネイル" 表現で表示されます。

- DVASPECT_ICON Item はアイコンで表されます。

- DVASPECT_DOCPRINT Item は、[ファイル] メニューの [印刷] コマンドを使用して印刷されたかのように表されます。

### <a name="remarks"></a>Remarks

通常は、ユーザーがサーバードキュメントを変更した後に、この関数を呼び出します。 OLE 項目が自動リンクを使用してドキュメントにリンクされている場合、その項目は変更内容を反映して更新されます。 Microsoft Foundation Class ライブラリで記述されたコンテナーアプリケーションでは、の`COleClientItem` [OnChange](../../mfc/reference/coleclientitem-class.md#onchange) メンバー関数が呼び出されます。

この関数`OnUpdate`は、送信側の項目、 *phint*、 *lhint*、および*ndrawaspect 各側面*を除き、ドキュメントの各項目のメンバー関数を呼び出します。 ドキュメントに対して行われた変更に関する情報を項目に渡すには、これらのパラメーターを使用します。 *Lhint*を使用して情報をエンコードしたり、 `CObject`派生クラスを定義して変更に関する情報を格納したり、 *phint*を使用してそのクラスのオブジェクトを渡したりすることができます。 派生クラスの`COleServerItem`メンバー関数をオーバーライドして、そのプレゼンテーションが変更されたかどうかに応じて各項目の更新を最適化します。 `OnUpdate`

## <a name="see-also"></a>関連項目

[MFC サンプル HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[COleLinkingDoc クラス](../../mfc/reference/colelinkingdoc-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDocument クラス](../../mfc/reference/coledocument-class.md)<br/>
[COleLinkingDoc クラス](../../mfc/reference/colelinkingdoc-class.md)<br/>
[COleTemplateServer クラス](../../mfc/reference/coletemplateserver-class.md)
