---
title: CDocument クラス
ms.date: 11/04/2016
f1_keywords:
- CDocument
- AFXWIN/CDocument
- AFXWIN/CDocument::CDocument
- AFXWIN/CDocument::AddView
- AFXWIN/CDocument::BeginReadChunks
- AFXWIN/CDocument::CanCloseFrame
- AFXWIN/CDocument::ClearChunkList
- AFXWIN/CDocument::ClearPathName
- AFXWIN/CDocument::DeleteContents
- AFXWIN/CDocument::FindChunk
- AFXWIN/CDocument::GetAdapter
- AFXWIN/CDocument::GetDocTemplate
- AFXWIN/CDocument::GetFile
- AFXWIN/CDocument::GetFirstViewPosition
- AFXWIN/CDocument::GetNextView
- AFXWIN/CDocument::GetPathName
- AFXWIN/CDocument::GetThumbnail
- AFXWIN/CDocument::GetTitle
- AFXWIN/CDocument::InitializeSearchContent
- AFXWIN/CDocument::IsModified
- AFXWIN/CDocument::IsSearchAndOrganizeHandler
- AFXWIN/CDocument::LoadDocumentFromStream
- AFXWIN/CDocument::OnBeforeRichPreviewFontChanged
- AFXWIN/CDocument::OnChangedViewList
- AFXWIN/CDocument::OnCloseDocument
- AFXWIN/CDocument::OnCreatePreviewFrame
- AFXWIN/CDocument::OnDocumentEvent
- AFXWIN/CDocument::OnDrawThumbnail
- AFXWIN/CDocument::OnLoadDocumentFromStream
- AFXWIN/CDocument::OnNewDocument
- AFXWIN/CDocument::OnOpenDocument
- AFXWIN/CDocument::OnPreviewHandlerQueryFocus
- AFXWIN/CDocument::OnPreviewHandlerTranslateAccelerator
- AFXWIN/CDocument::OnRichPreviewBackColorChanged
- AFXWIN/CDocument::OnRichPreviewFontChanged
- AFXWIN/CDocument::OnRichPreviewSiteChanged
- AFXWIN/CDocument::OnRichPreviewTextColorChanged
- AFXWIN/CDocument::OnSaveDocument
- AFXWIN/CDocument::OnUnloadHandler
- AFXWIN/CDocument::PreCloseFrame
- AFXWIN/CDocument::ReadNextChunkValue
- AFXWIN/CDocument::ReleaseFile
- AFXWIN/CDocument::RemoveChunk
- AFXWIN/CDocument::RemoveView
- AFXWIN/CDocument::ReportSaveLoadException
- AFXWIN/CDocument::SaveModified
- AFXWIN/CDocument::SetChunkValue
- AFXWIN/CDocument::SetModifiedFlag
- AFXWIN/CDocument::SetPathName
- AFXWIN/CDocument::SetTitle
- AFXWIN/CDocument::UpdateAllViews
- AFXWIN/CDocument::OnFileSendMail
- AFXWIN/CDocument::OnUpdateFileSendMail
- AFXWIN/CDocument::m_bGetThumbnailMode
- AFXWIN/CDocument::m_bPreviewHandlerMode
- AFXWIN/CDocument::m_bSearchMode
- AFXWIN/CDocument::m_clrRichPreviewBackColor
- AFXWIN/CDocument::m_clrRichPreviewTextColor
- AFXWIN/CDocument::m_lfRichPreviewFont
helpviewer_keywords:
- CDocument [MFC], CDocument
- CDocument [MFC], AddView
- CDocument [MFC], BeginReadChunks
- CDocument [MFC], CanCloseFrame
- CDocument [MFC], ClearChunkList
- CDocument [MFC], ClearPathName
- CDocument [MFC], DeleteContents
- CDocument [MFC], FindChunk
- CDocument [MFC], GetAdapter
- CDocument [MFC], GetDocTemplate
- CDocument [MFC], GetFile
- CDocument [MFC], GetFirstViewPosition
- CDocument [MFC], GetNextView
- CDocument [MFC], GetPathName
- CDocument [MFC], GetThumbnail
- CDocument [MFC], GetTitle
- CDocument [MFC], InitializeSearchContent
- CDocument [MFC], IsModified
- CDocument [MFC], IsSearchAndOrganizeHandler
- CDocument [MFC], LoadDocumentFromStream
- CDocument [MFC], OnBeforeRichPreviewFontChanged
- CDocument [MFC], OnChangedViewList
- CDocument [MFC], OnCloseDocument
- CDocument [MFC], OnCreatePreviewFrame
- CDocument [MFC], OnDocumentEvent
- CDocument [MFC], OnDrawThumbnail
- CDocument [MFC], OnLoadDocumentFromStream
- CDocument [MFC], OnNewDocument
- CDocument [MFC], OnOpenDocument
- CDocument [MFC], OnPreviewHandlerQueryFocus
- CDocument [MFC], OnPreviewHandlerTranslateAccelerator
- CDocument [MFC], OnRichPreviewBackColorChanged
- CDocument [MFC], OnRichPreviewFontChanged
- CDocument [MFC], OnRichPreviewSiteChanged
- CDocument [MFC], OnRichPreviewTextColorChanged
- CDocument [MFC], OnSaveDocument
- CDocument [MFC], OnUnloadHandler
- CDocument [MFC], PreCloseFrame
- CDocument [MFC], ReadNextChunkValue
- CDocument [MFC], ReleaseFile
- CDocument [MFC], RemoveChunk
- CDocument [MFC], RemoveView
- CDocument [MFC], ReportSaveLoadException
- CDocument [MFC], SaveModified
- CDocument [MFC], SetChunkValue
- CDocument [MFC], SetModifiedFlag
- CDocument [MFC], SetPathName
- CDocument [MFC], SetTitle
- CDocument [MFC], UpdateAllViews
- CDocument [MFC], OnFileSendMail
- CDocument [MFC], OnUpdateFileSendMail
- CDocument [MFC], m_bGetThumbnailMode
- CDocument [MFC], m_bPreviewHandlerMode
- CDocument [MFC], m_bSearchMode
- CDocument [MFC], m_clrRichPreviewBackColor
- CDocument [MFC], m_clrRichPreviewTextColor
- CDocument [MFC], m_lfRichPreviewFont
ms.assetid: e5a2891d-e1e1-4599-8c7e-afa9b4945446
ms.openlocfilehash: 2d87ff67000fb5b70c0a5c965638875e6f50b22c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164119"
---
# <a name="cdocument-class"></a>CDocument クラス

ユーザーが定義するドキュメント クラスの基本機能が用意されています。

## <a name="syntax"></a>構文

```
class CDocument : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDocument::CDocument](#cdocument)|`CDocument` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDocument::AddView](#addview)|ビューをドキュメントにアタッチします。|
|[CDocument::BeginReadChunks](#beginreadchunks)|チャンクの読み取りを初期化します。|
|[CDocument::CanCloseFrame](#cancloseframe)|オーバーライド可能な; 高度なこのドキュメントを表示するフレーム ウィンドウを閉じる前に呼び出されます。|
|[CDocument::ClearChunkList](#clearchunklist)|チャンクの一覧をクリアします。|
|[CDocument::ClearPathName](#clearpathname)|ドキュメント オブジェクトのパスをクリアします。|
|[CDocument::DeleteContents](#deletecontents)|ドキュメントのクリーンアップを実行すると呼ばれます。|
|[CDocument::FindChunk](#findchunk)|指定した GUID のチャンクを検索します。|
|[CDocument::GetAdapter](#getadapter)|実装するオブジェクトへのポインターを返します`IDocument`インターフェイス。|
|[CDocument::GetDocTemplate](#getdoctemplate)|ドキュメントの種類を説明するドキュメント テンプレートへのポインターを返します。|
|[CDocument::GetFile](#getfile)|必要なポインターを返します`CFile`オブジェクト。|
|[CDocument::GetFirstViewPosition](#getfirstviewposition)|最初の位置を返しますビューの一覧で、。イテレーションを開始するために使用します。|
|[CDocument::GetNextView](#getnextview)|ドキュメントに関連付けられているビューの一覧を反復処理します。|
|[CDocument::GetPathName](#getpathname)|ドキュメントのデータ ファイルのパスを返します。|
|[CDocument::GetThumbnail](#getthumbnail)|サムネイルを表示するサムネイル プロバイダーによって使用されるビットマップを作成するには、呼び出されます。|
|[CDocument::GetTitle](#gettitle)|ドキュメントのタイトルを返します。|
|[CDocument::InitializeSearchContent](#initializesearchcontent)|検索ハンドラーの検索コンテンツを初期化するために呼び出されます。|
|[CDocument::IsModified](#ismodified)|最後に保存してから、ドキュメントが変更されたかどうかを示します。|
|[CDocument::IsSearchAndOrganizeHandler](#issearchandorganizehandler)|通知するかどうかのこのインスタンス`CDocument`ハンドラーの検索と整理のオブジェクトが作成されました。|
|[CDocument::LoadDocumentFromStream](#loaddocumentfromstream)|ストリームからドキュメントのデータを読み込むと呼ばれます。|
|[CDocument::OnBeforeRichPreviewFontChanged](#onbeforerichpreviewfontchanged)|リッチ プレビューのフォントが変更される前に呼び出されます。|
|[CDocument::OnChangedViewList](#onchangedviewlist)|ビューが追加またはドキュメントから削除された後に呼び出されます。|
|[CDocument::OnCloseDocument](#onclosedocument)|文書を閉じると呼ばれます。|
|[CDocument::OnCreatePreviewFrame](#oncreatepreviewframe)|リッチ プレビュー用プレビュー フレームを作成する必要があるときに、フレームワークによって呼び出されます。|
|[CDocument::OnDocumentEvent](#ondocumentevent)|ドキュメントのイベントに応答フレームワークによって呼び出されます。|
|[CDocument::OnDrawThumbnail](#ondrawthumbnail)|サムネイルのコンテンツを描画するために派生クラスでこのメソッドをオーバーライドします。|
|[CDocument::OnLoadDocumentFromStream](#onloaddocumentfromstream)|ストリームからドキュメント データを読み込む必要があるときに、フレームワークによって呼び出されます。|
|[CDocument::OnNewDocument](#onnewdocument)|新しいドキュメントを作成するには、呼び出されます。|
|[CDocument::OnOpenDocument](#onopendocument)|既存のドキュメントを開くと呼ばれます。|
|[CDocument::OnPreviewHandlerQueryFocus](#onpreviewhandlerqueryfocus)|プレビュー ハンドラーを呼び出し元の GetFocus 関数から HWND を返すよう指示します。|
|[CDocument::OnPreviewHandlerTranslateAccelerator](#onpreviewhandlertranslateaccelerator)|プレビュー ハンドラーが実行されているプロセスのメッセージ ポンプから渡されたキーストロークを処理するために、プレビュー ハンドラーに指示します。|
|[CDocument::OnRichPreviewBackColorChanged](#onrichpreviewbackcolorchanged)|豊富なプレビューの背景色が変更されたときに呼び出されます。|
|[CDocument::OnRichPreviewFontChanged](#onrichpreviewfontchanged)|リッチ プレビューのフォントが変更されたときに呼び出されます。|
|[CDocument::OnRichPreviewSiteChanged](#onrichpreviewsitechanged)|リッチ プレビュー サイトが変更されたときに呼び出されます。|
|[CDocument::OnRichPreviewTextColorChanged](#onrichpreviewtextcolorchanged)|リッチ プレビュー テキストの色が変更されたときに呼び出されます。|
|[CDocument::OnSaveDocument](#onsavedocument)|ドキュメントをディスクに保存すると呼ばれます。|
|[CDocument::OnUnloadHandler](#onunloadhandler)|プレビュー ハンドラーがアンロードされるときに、フレームワークによって呼び出されます。|
|[CDocument::PreCloseFrame](#precloseframe)|フレーム ウィンドウを閉じる前に呼び出されます。|
|[CDocument::ReadNextChunkValue](#readnextchunkvalue)|次のチャンク値を読み取ります。|
|[CDocument::ReleaseFile](#releasefile)|他のアプリケーションで使用できるようにするファイルを解放します。|
|[CDocument::RemoveChunk](#removechunk)|指定した GUID のチャンクを削除します。|
|[CDocument::RemoveView](#removeview)|ドキュメントからビューをデタッチします。|
|[CDocument::ReportSaveLoadException](#reportsaveloadexception)|オーバーライド可能な; 高度な開いているときに呼び出されますまたは保存操作は、例外のため完了できません。|
|[に対して、順番](#savemodified)|オーバーライド可能な; 高度なドキュメントを保存するかどうかをユーザーに要求と呼ばれます。|
|[CDocument::SetChunkValue](#setchunkvalue)|チャンクの値を設定します。|
|[CDocument::SetModifiedFlag](#setmodifiedflag)|最後に保存してから、ドキュメントを変更したことを示すフラグを設定します。|
|[CDocument::SetPathName](#setpathname)|ドキュメントで使用されるデータ ファイルのパスを設定します。|
|[CDocument::SetTitle](#settitle)|ドキュメントのタイトルを設定します。|
|[CDocument::UpdateAllViews](#updateallviews)|ドキュメントのすべてのビューが変更されたかを通知します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CDocument::OnFileSendMail](#onfilesendmail)|ドキュメントを添付して、メール メッセージを送信します。|
|[CDocument::OnUpdateFileSendMail](#onupdatefilesendmail)|メールのサポートが存在する場合は、メール送信コマンドを有効にします。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDocument::m_bGetThumbnailMode](#m_bgetthumbnailmode)|指定します`CDocument`サムネイルの dllhost でオブジェクトが作成されます。 チェックインする必要があります`CView::OnDraw`します。|
|[CDocument::m_bPreviewHandlerMode](#m_bpreviewhandlermode)|指定します`CDocument`の prevhost によってオブジェクトが作成された`Rich Preview`します。 チェックインする必要があります`CView::OnDraw`します。|
|[CDocument::m_bSearchMode](#m_bsearchmode)|指定します`CDocument`インデクサーまたはその他の検索アプリケーションでオブジェクトが作成されます。|
|[CDocument::m_clrRichPreviewBackColor](#m_clrrichpreviewbackcolor)|リッチ プレビュー ウィンドウの背景色を指定します。 この色は、ホストによって設定されます。|
|[CDocument::m_clrRichPreviewTextColor](#m_clrrichpreviewtextcolor)|リッチ プレビュー ウィンドウの前景色を指定します。 この色は、ホストによって設定されます。|
|[CDocument::m_lfRichPreviewFont](#m_lfrichpreviewfont)|リッチ プレビュー ウィンドウのテキストのフォントを指定します。 このフォント情報は、ホストによって設定されます。|

## <a name="remarks"></a>Remarks

ドキュメントでは、ユーザーが通常ファイルを開くコマンドを使用して表示してファイルの保存のコマンドを使用して保存データの単位を表します。

`CDocument` ドキュメントを作成し、それを読み込み、保存などの標準的な操作をサポートしています。 フレームワークによって定義されたインターフェイスを使用して、ドキュメントを操作する`CDocument`します。

アプリケーションのドキュメントの 1 つ以上の型をサポートできます。たとえば、アプリケーションでは、スプレッドシートやテキスト ドキュメントの両方をサポート可能性があります。 ドキュメントの種類ごとに、関連付けられたドキュメント テンプレートドキュメント テンプレートでは、そのドキュメントの種類を使用するリソース (たとえば、メニューのアイコン、またはアクセラレータ テーブル) を指定します。 各ドキュメントには、それに関連付けられたへのポインターが含まれています。`CDocTemplate`オブジェクト。

ユーザーを使用するドキュメントと対話する、 [CView](../../mfc/reference/cview-class.md)関連付けられているオブジェクト。 ビューは、フレーム ウィンドウにドキュメントのイメージをレンダリングし、ドキュメントに対する操作としてユーザー入力を解釈します。 ドキュメントには、関連付けられている複数のビューを持つことができます。 ユーザーは、ドキュメント上のウィンドウが開いたら、フレームワークはビューを作成し、ドキュメントにアタッチします。 ドキュメント テンプレートでは、どのような種類のビューとフレームのウィンドウはドキュメントの種類を表示するために使用を指定します。

ドキュメント、framework の標準の一部では、ルーティング コマンドし、その結果 (ファイルの保存のメニュー項目) などの標準的なユーザー インターフェイス コンポーネントからのコマンドを受信します。 ドキュメントでは、アクティブなビューが転送されたコマンドを受信します。 ドキュメントでは、特定のコマンドを処理しない場合は、コマンドによって管理されるドキュメント テンプレートを転送します。

ドキュメントのデータが変更されたときにそのビューの各変更を反映させる必要があります。 `CDocument` 提供、 [UpdateAllViews](#updateallviews)ビューを必要に応じて再描画自体は、ビューに、このような変更を通知するためのメンバー関数。 フレームワークには、それを閉じる前に、変更されたファイルを保存するユーザーも求められます。

一般的なアプリケーションでドキュメントを実装するには、次の操作を行う必要があります。

- クラスを派生`CDocument`ドキュメントの種類ごとにします。

- 各ドキュメントのデータを格納するメンバー変数を追加します。

- 読み取りおよびドキュメントのデータを変更するためのメンバー関数を実装します。 ドキュメントのビューは、これらのメンバー関数の最も重要なユーザーです。

- 上書き、 [cobject::serialize](../../mfc/reference/cobject-class.md#serialize)やディスクから、ドキュメントのデータを読み書きするドキュメント クラスのメンバー関数。

`CDocument` サポート メール サポート (MAPI) が存在する場合にメールを使ってドキュメントを送信します。 記事を参照して[MAPI](../../mfc/mapi.md)と[MFC での MAPI サポート](../../mfc/mapi-support-in-mfc.md)します。

詳細については`CDocument`を参照してください[シリアル化](../../mfc/serialization-in-mfc.md)、[ドキュメント/ビュー アーキテクチャに関するトピック](../../mfc/document-view-architecture.md)、および[ドキュメント/ビューの作成](../../mfc/document-view-creation.md)です。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocument`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="addview"></a>  CDocument::AddView

ビューをドキュメントにアタッチするには、この関数を呼び出します。

```
void AddView(CView* pView);
```

### <a name="parameters"></a>パラメーター

*pView*<br/>
追加するビューを指します。

### <a name="remarks"></a>Remarks

この関数は、ドキュメントに関連付けられたビューの一覧に、指定されたビューを追加します。また、関数は、このドキュメントに、ビューのドキュメントのポインターを設定します。 ドキュメントを新しく作成されたビュー オブジェクトをアタッチするときに、フレームワークはこの関数を呼び出しますこれは、応答ファイルの新しいファイルを開く、または新しいウィンドウのコマンドまたはスプリッター ウィンドウを分割すると発生します。

手動で作成して、ビューをアタッチする場合にのみ、この関数を呼び出します。 ドキュメントとビューを定義することによって接続フレームワークをできるように、通常、 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)クラスのドキュメント、ビューのクラスとフレーム ウィンドウ クラスに関連付けるオブジェクト。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocViewSDI#12](../../mfc/codesnippet/cpp/cdocument-class_1.cpp)]

##  <a name="beginreadchunks"></a>  CDocument::BeginReadChunks

チャンクの読み取りを初期化します。

```
virtual void BeginReadChunks ();
```

### <a name="remarks"></a>Remarks

##  <a name="cancloseframe"></a>  CDocument::CanCloseFrame

ドキュメントを表示するフレーム ウィンドウを閉じる前に、フレームワークによって呼び出されます。

```
virtual BOOL CanCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>パラメーター

*pFrame*<br/>
ドキュメントにアタッチされているビューのフレーム ウィンドウへのポインター。

### <a name="return-value"></a>戻り値

フレーム ウィンドウを閉じるには安全である場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

ドキュメントを表示するその他のフレーム ウィンドウがあるかどうか、既定の実装を確認します。 指定したフレーム ウィンドウがドキュメントを表示する最後の 1 つである場合は、関数が変更された場合に、ドキュメントを保存するように求めるプロンプトを表示します。 フレーム ウィンドウが閉じられたときに、特別な処理を実行する場合は、この関数をオーバーライドします。 これは、高度なオーバーライド可能な。

##  <a name="cdocument"></a>  CDocument::CDocument

`CDocument` オブジェクトを構築します。

```
CDocument();
```

### <a name="remarks"></a>Remarks

フレームワークは、ドキュメントの作成を処理します。 上書き、[でも実質的](#onnewdocument)ドキュメント単位; での初期化を実行するメンバー関数はこれには、シングル ドキュメント インターフェイス (SDI) アプリケーションで特に重要です。

##  <a name="clearchunklist"></a>  CDocument::ClearChunkList

チャンクの一覧をクリアします。

```
virtual void ClearChunkList ();
```

### <a name="remarks"></a>Remarks

##  <a name="clearpathname"></a>  CDocument::ClearPathName

ドキュメント オブジェクトのパスをクリアします。

```
virtual void ClearPathName();
```

### <a name="remarks"></a>Remarks

パスをオフにすると、`CDocument`オブジェクトにより、アプリケーションは、ドキュメントが次に保存するときにユーザーに確認します。 これにより、**保存**コマンドと同様に動作を**名前を付けて保存**コマンド。

##  <a name="deletecontents"></a>  CDocument::DeleteContents

破棄せずに、ドキュメントのデータを削除するためにフレームワークによって呼び出される、`CDocument`オブジェクト自体です。

```
virtual void DeleteContents();
```

### <a name="remarks"></a>Remarks

ドキュメントが破棄される直前に呼び出されます。 再利用される前に、ドキュメントが空であることを確認することも呼び出されます。 これは、ドキュメントを 1 つのみを使用して、SDI アプリケーションにとって特に重要です。ドキュメントは、ユーザーを作成または別のドキュメントを開くたびに再利用されます。 "クリアを編集する All"またはドキュメントのデータをすべて削除する同様のコマンドを実装するには、この関数を呼び出します。 この関数の既定の実装は、何も行いません。 ドキュメント内のデータを削除するには、この関数をオーバーライドします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#57](../../mfc/codesnippet/cpp/cdocument-class_2.cpp)]

##  <a name="findchunk"></a>  CDocument::FindChunk

指定した GUID のチャンクを検索します。

```
virtual POSITION FindChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>パラメーター

*guid*<br/>
検索するチャンクの GUID を指定します。

*pid*<br/>
検索するには、チャンクの PID を指定します。

### <a name="return-value"></a>戻り値

成功した場合は、内部のチャンク リスト内の位置。 それ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="getadapter"></a>  CDocument::GetAdapter

実装するオブジェクトへのポインターを返します、`IDocument`インターフェイス。

```
virtual ATL::IDocument* GetAdapter();
```

### <a name="return-value"></a>戻り値

実装するオブジェクトへのポインター、`IDocument`インターフェイス。

### <a name="remarks"></a>Remarks

##  <a name="getdoctemplate"></a>  CDocument::GetDocTemplate

このドキュメントの種類のドキュメント テンプレートをポインターを取得するには、この関数を呼び出します。

```
CDocTemplate* GetDocTemplate() const;
```

### <a name="return-value"></a>戻り値

このドキュメントの種類、またはドキュメントがドキュメント テンプレートで管理されていない場合は NULL のドキュメント テンプレートへのポインター。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#58](../../mfc/codesnippet/cpp/cdocument-class_3.cpp)]

##  <a name="getfile"></a>  CDocument::GetFile

ポインターを取得するには、このメンバー関数を呼び出す、`CFile`オブジェクト。

```
virtual CFile* GetFile(
    LPCTSTR lpszFileName,
    UINT nOpenFlags,
    CFileException* pError);
```

### <a name="parameters"></a>パラメーター

*lpszFileName*<br/>
目的のファイルのパスを表す文字列。 相対パスまたは絶対パスがあります。

*pError*<br/>
操作の完了ステータスを示す既存のファイルの例外オブジェクトへのポインター。

*nOpenFlags*<br/>
共有とアクセス モード。 ファイルを開くときに実行するアクションを指定します。 CFile コンス トラクターに示すオプションを組み合わせることができます[ほか](../../mfc/reference/cfile-class.md#cfile)ビットごとの OR を使用して (&#124;) 演算子。 1 つのアクセス許可と 1 つの共有オプションが必要です。`modeCreate`と`modeNoInherit`モードは省略可能です。

### <a name="return-value"></a>戻り値

`CFile` オブジェクトへのポインター。

##  <a name="getfirstviewposition"></a>  CDocument::GetFirstViewPosition

ドキュメントに関連付けられたビューの一覧で最初のビューの位置を取得するには、この関数を呼び出します。

```
virtual POSITION GetFirstViewPosition() const;
```

### <a name="return-value"></a>戻り値

位置の値を使用したイテレーションを使用できる、 [GetNextView](#getnextview)メンバー関数。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getnextview"></a>  CDocument::GetNextView

すべてのドキュメントのビューを反復処理するには、この関数を呼び出します。

```
virtual CView* GetNextView(POSITION& rPosition) const;
```

### <a name="parameters"></a>パラメーター

*rPosition*<br/>
以前の呼び出しによって返される位置の値への参照、`GetNextView`または[GetFirstViewPosition](#getfirstviewposition)メンバー関数。 この値は、NULL は指定できません。

### <a name="return-value"></a>戻り値

識別されるビューへのポインター *rPosition*します。

### <a name="remarks"></a>Remarks

識別されるビューを返します*rPosition*し、設定*rPosition*の一覧で、[次へ] ビューの位置の値にします。 リスト内の最後は、取得したビュー *rPosition* NULL に設定されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#59](../../mfc/codesnippet/cpp/cdocument-class_4.cpp)]

##  <a name="getpathname"></a>  CDocument::GetPathName

ドキュメントのディスク ファイルの完全修飾パスを取得するには、この関数を呼び出します。

```
const CString& GetPathName() const;
```

### <a name="return-value"></a>戻り値

ドキュメントの完全修飾パス。 文書が保存されていないかに関連付けられているディスク ファイルがない場合、この文字列が空です。

##  <a name="getthumbnail"></a>  CDocument::GetThumbnail

サムネイルを表示するサムネイルのプロバイダーによって使用されるビットマップを作成します。

```
virtual BOOL GetThumbnail(
    UINT cx,
    HBITMAP* phbmp,
    DWORD* pdwAlpha);
```

### <a name="parameters"></a>パラメーター

*cx*<br/>
ビットマップの高さと幅を指定します。

*phbmp*<br/>
関数が正常に返されるときに、ビットマップを識別するハンドルが含まれています。

*pdwAlpha*<br/>
関数が正常に返されるときに、アルファ チャネルの値を指定する DWORD が含まれています。

### <a name="return-value"></a>戻り値

サムネイルのビットマップの場合は TRUE を返しますが正常に作成されました。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="gettitle"></a>  CDocument::GetTitle

通常、ドキュメントのファイル名から派生するドキュメントのタイトルを取得するには、この関数を呼び出します。

```
const CString& GetTitle() const;
```

### <a name="return-value"></a>戻り値

ドキュメントのタイトル。

##  <a name="initializesearchcontent"></a>  CDocument::InitializeSearchContent

検索ハンドラーの検索コンテンツを初期化するために呼び出されます。

```
virtual void InitializeSearchContent ();
```

### <a name="remarks"></a>Remarks

コンテンツの検索を初期化するために派生クラスでこのメソッドをオーバーライドします。 コンテンツで区切られた文字列である必要があります「;」します。 たとえば、"ポイントです。四角形。ole 項目"。

##  <a name="ismodified"></a>  CDocument::IsModified

最後に保存してから、ドキュメントが変更されたかどうかを判断するには、この関数を呼び出します。

```
virtual BOOL IsModified();
```

### <a name="return-value"></a>戻り値

最後の保存のため、ドキュメントが変更された場合、0 以外の場合それ以外の場合 0 を返します。

##  <a name="issearchandorganizehandler"></a>  CDocument::IsSearchAndOrganizeHandler

通知するかどうかのこのインスタンス`CDocument`検索と整理のハンドラー用に作成されました。

```
BOOL IsSearchAndOrganizeHandler() const;
```

### <a name="return-value"></a>戻り値

TRUE の場合は、このインスタンスを返します`CDocument`検索と整理のハンドラー用に作成されました。

### <a name="remarks"></a>Remarks

現在この関数は、アウト プロセス サーバーで実装された豊富なプレビュー ハンドラーに対してのみ TRUE を返します。 この機能は TRUE を返すようにする、アプリケーション レベルでは、(m_bPreviewHandlerMode、m_bSearchMode、m_bGetThumbnailMode) は、適切なフラグを設定できます。

##  <a name="loaddocumentfromstream"></a>  CDocument::LoadDocumentFromStream

ストリームからドキュメントのデータを読み込むと呼ばれます。

```
virtual HRESULT LoadDocumentFromStream(
    IStream* pStream,
    DWORD dwGrfMode);
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
ストリームへのポインター。 このストリームは、シェルによって提供されます。

*dwGrfMode*<br/>
ストリームへのアクセス モード。

### <a name="return-value"></a>戻り値

読み込み操作が成功すると、それ以外の場合の HRESULT エラー コードの場合は s_ok を返します。

### <a name="remarks"></a>Remarks

ストリームからデータを読み込む方法をカスタマイズする派生クラスでこのメソッドをオーバーライドすることができます。

##  <a name="m_bgetthumbnailmode"></a>  CDocument::m_bGetThumbnailMode

指定します、`CDocument`サムネイルの dllhost でオブジェクトが作成されます。 チェックインする必要があります`CView::OnDraw`します。

```
BOOL m_bGetThumbnailMode;
```

### <a name="remarks"></a>Remarks

`TRUE` サムネイルの dllhost でドキュメントが作成されたことを示します。

##  <a name="m_bpreviewhandlermode"></a>  CDocument::m_bPreviewHandlerMode

指定します、`CDocument`リッチ プレビュー用 prevhost によってオブジェクトが作成されます。 チェックインする必要があります`CView::OnDraw`します。

```
BOOL m_bPreviewHandlerMode;
```

### <a name="remarks"></a>Remarks

TRUE は、リッチ プレビュー用 prevhost によってドキュメントが作成されたことを示します。

##  <a name="m_bsearchmode"></a>  CDocument::m_bSearchMode

指定します、`CDocument`インデクサーによって、または他の検索アプリケーションでオブジェクトが作成されました。

```
BOOL m_bSearchMode;
```

### <a name="remarks"></a>Remarks

`TRUE` インデクサーで、または他の検索アプリケーションでドキュメントが作成されたことを示します。

##  <a name="m_clrrichpreviewbackcolor"></a>  CDocument::m_clrRichPreviewBackColor

リッチ プレビュー ウィンドウの背景色を指定します。 この色は、ホストによって設定されます。

```
COLORREF m_clrRichPreviewBackColor;
```

### <a name="remarks"></a>Remarks

##  <a name="m_clrrichpreviewtextcolor"></a>  CDocument::m_clrRichPreviewTextColor

リッチ プレビュー ウィンドウの前景色を指定します。 この色は、ホストによって設定されます。

```
COLORREF m_clrRichPreviewTextColor;
```

### <a name="remarks"></a>Remarks

##  <a name="m_lfrichpreviewfont"></a>  CDocument::m_lfRichPreviewFont

リッチ プレビュー ウィンドウのテキストのフォントを指定します。 このフォント情報は、ホストによって設定されます。

```
CFont m_lfRichPreviewFont;
```

### <a name="remarks"></a>Remarks

##  <a name="onbeforerichpreviewfontchanged"></a>  CDocument::OnBeforeRichPreviewFontChanged

リッチ プレビューのフォントが変更される前に呼び出されます。

```
virtual void OnBeforeRichPreviewFontChanged();
```

### <a name="remarks"></a>Remarks

##  <a name="onchangedviewlist"></a>  CDocument::OnChangedViewList

ビューが追加またはドキュメントから削除した後に、フレームワークによって呼び出されます。

```
virtual void OnChangedViewList();
```

### <a name="remarks"></a>Remarks

かどうか、最後のビューが削除されると、そうである場合は、ドキュメントを削除します。 この関数の既定の実装を確認します。 フレームワークを追加またはビューを削除する場合は、特別な処理を実行する場合は、この関数をオーバーライドします。 たとえば、ビューを関連付けることがない場合でも、開いたままにドキュメントを作成する場合は、この関数をオーバーライドします。

##  <a name="onclosedocument"></a>  CDocument::OnCloseDocument

ドキュメントが閉じられたとき、通常、ファイルを閉じるコマンドの一部として、フレームワークによって呼び出されます。

```
virtual void OnCloseDocument();
```

### <a name="remarks"></a>Remarks

この関数の既定の実装のドキュメントを表示するためのフレームのすべてを破棄し、ビューを閉じ、ドキュメントの内容を消去およびを呼び出して、 [DeleteContents](#deletecontents)メンバー関数は、ドキュメントの削除データ。

フレームワークは、ドキュメントを閉じるときに特別な後処理を実行する場合は、この関数をオーバーライドします。 などのドキュメントでは、データベース内のレコードを表している場合、データベースを終了するには、この関数をオーバーライドします。 この関数の基底クラスのバージョンは、オーバーライドから呼び出す必要があります。

##  <a name="oncreatepreviewframe"></a>  CDocument::OnCreatePreviewFrame

リッチ プレビュー用プレビュー フレームを作成する必要があるときに、フレームワークによって呼び出されます。

```
virtual BOOL OnCreatePreviewFrame();
```

### <a name="return-value"></a>戻り値

フレームが正常に作成されたかどうかは TRUE を返しますそれ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="ondocumentevent"></a>  CDocument::OnDocumentEvent

ドキュメントのイベントに応答フレームワークによって呼び出されます。

```
virtual void OnDocumentEvent(DocumentEvent deEvent);
```

### <a name="parameters"></a>パラメーター

*deEvent*<br/>
[in]イベントの種類を示す列挙型。

### <a name="remarks"></a>Remarks

複数のクラスがドキュメント イベントの影響を与える可能性があります。 以外のクラスに影響を与えるドキュメント イベントを処理するため、このメソッドは、 [CDocument クラス](../../mfc/reference/cdocument-class.md)します。 現在、ドキュメントのイベントに応答する必要がありますを唯一のクラスは、 [CDataRecoveryHandler クラス](../../mfc/reference/cdatarecoveryhandler-class.md)します。 `CDocument`クラスが他の上書き可能な方法で効果を処理する、`CDocument`します。

次の表に、可能な値*deEvent*および対応するイベントです。

|[値]|対応するイベント|
|-----------|-------------------------|
|`onAfterNewDocument`|新しいドキュメントが作成されました。|
|`onAfterOpenDocument`|新しいドキュメントが開かれました。|
|`onAfterSaveDocument`|ドキュメントが保存されました。|
|`onAfterCloseDocument`|ドキュメントが閉じられました。|

##  <a name="ondrawthumbnail"></a>  CDocument::OnDrawThumbnail

縮小表示を描画するために派生クラスでこのメソッドをオーバーライドします。

```
virtual void OnDrawThumbnail(
    CDC& dc,
    LPRECT lprcBounds);
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
デバイス コンテキストへの参照。

*lprcBounds*<br/>
縮小表示を描画する領域の外接する四角形を指定します。

### <a name="remarks"></a>Remarks

##  <a name="onfilesendmail"></a>  CDocument::OnFileSendMail

メッセージを送信常駐メール ホスト経由で (ある場合)、ドキュメント、添付ファイルとして。

```
void OnFileSendMail();
```

### <a name="remarks"></a>Remarks

`OnFileSendMail` 呼び出し[呼び出す必要はありません](#onsavedocument)(保存) 無題と変更されたドキュメントは、電子メールで送信し、一時ファイルをシリアル化します。 ドキュメントが変更されていない場合、一時ファイルは必要ありません。元に送信されます。 `OnFileSendMail` MAPI32 を読み込みます。既に読み込まれていない場合は、DLL です。

特殊な実装`OnFileSendMail`の[COleDocument](../../mfc/reference/coledocument-class.md)複合ファイルを正しく処理します。

`CDocument` サポート メール サポート (MAPI) が存在する場合にメールを使ってドキュメントを送信します。 記事を参照して[MAPI トピック](../../mfc/mapi.md)と[MFC での MAPI サポート](../../mfc/mapi-support-in-mfc.md)します。

##  <a name="onloaddocumentfromstream"></a>  CDocument::OnLoadDocumentFromStream

ストリームからドキュメント データを読み込む必要があるときに、フレームワークによって呼び出されます。

```
virtual HRESULT OnLoadDocumentFromStream(
    IStream* pStream,
    DWORD grfMode);
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
受信のストリームへのポインター。

*grfMode*<br/>
ストリームへのアクセス モード。

### <a name="return-value"></a>戻り値

負荷が成功した場合は s_ok を返します。それ以外の場合、エラー コード。

### <a name="remarks"></a>Remarks

##  <a name="onnewdocument"></a>  CDocument::OnNewDocument

ファイルの新しいコマンドの一部として、フレームワークによって呼び出されます。

```
virtual BOOL OnNewDocument();
```

### <a name="return-value"></a>戻り値

以外の場合は、ドキュメントが正常に初期化します。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

この関数の既定の実装、 [DeleteContents](#deletecontents)メンバー関数は、ドキュメントが空で、新しいドキュメントにマークを確認します。 新しいドキュメントのデータ構造を初期化するためには、この関数をオーバーライドします。 この関数の基底クラスのバージョンは、オーバーライドから呼び出す必要があります。

SDI アプリケーションで新しいファイル を選択すると、フレームワークは、新しいものを作成するのではなく、既存のドキュメントを再初期化するのにこの関数を使用します。 場合は、ユーザーは、マルチ ドキュメント インターフェイス (MDI) アプリケーションで新しいファイルが選択した、フレームワークは毎回新しい文書を作成、初期化するには、この関数を呼び出します。 SDI アプリケーションで有効にするファイルの新しいコマンドのコンス トラクターではなく、この関数には、初期化コードを配置する必要があります。

あるをケースがあることに注意してください`OnNewDocument`が 2 回呼び出されます。 これは、ActiveX ドキュメント サーバーとして、ドキュメントが埋め込まれている場合に発生します。 関数が初めて呼び出された、`CreateInstance`メソッド (によって公開されている、 `COleObjectFactory`-派生クラス) と、2 つ目の時刻、`InitNew`メソッド (によって公開されている、 `COleServerDoc`-派生クラス)。

### <a name="example"></a>例

次の例では、別のドキュメント オブジェクトの初期化方法を示します。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

##  <a name="onopendocument"></a>  CDocument::OnOpenDocument

ファイルを開く コマンドの一部として、フレームワークによって呼び出されます。

```
virtual BOOL OnOpenDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
開かれているドキュメントのパスを指します。

### <a name="return-value"></a>戻り値

以外の場合は、ドキュメントが正常に読み込まれました。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

この関数の既定の実装は、指定したファイルを開き、 [DeleteContents](#deletecontents)ドキュメントが空であることを確認するメンバー関数を呼び出す[cobject::serialize](../../mfc/reference/cobject-class.md#serialize)ファイルの読み取り内容、およびクリーンとしてマークします。 アーカイブ機構やファイル メカニズム以外の何かを使用する場合は、この関数をオーバーライドします。 たとえば、ドキュメントが別々 のファイルではなく、データベース内のレコードを表すアプリケーションを作成する場合があります。

フレームワークでこの関数を使用して、既存の再初期化する SDI アプリケーションでファイルを開く を選択すると場合、`CDocument`新規に作成するのではなく、オブジェクト。 フレームワークの作成、新しいユーザーは、MDI アプリケーションでファイルを開くが場合、`CDocument`オブジェクト毎回し初期化するには、この関数を呼び出します。 SDI アプリケーションで有効にするファイルを開くコマンドのコンス トラクターではなく、この関数には、初期化コードを配置する必要があります。

### <a name="example"></a>例

次の例では、別のドキュメント オブジェクトの初期化方法を示します。

[!code-cpp[NVC_MFCDocView#60](../../mfc/codesnippet/cpp/cdocument-class_5.cpp)]

[!code-cpp[NVC_MFCDocView#61](../../mfc/codesnippet/cpp/cdocument-class_6.cpp)]

[!code-cpp[NVC_MFCDocView#62](../../mfc/codesnippet/cpp/cdocument-class_7.cpp)]

[!code-cpp[NVC_MFCDocView#63](../../mfc/codesnippet/cpp/cdocument-class_8.cpp)]

##  <a name="onpreviewhandlerqueryfocus"></a>  CDocument::OnPreviewHandlerQueryFocus

プレビュー ハンドラーを呼び出し元から取得した HWND を返すように指示、`GetFocus`関数。

```
virtual HRESULT OnPreviewHandlerQueryFocus(HWND* phwnd);
```

### <a name="parameters"></a>パラメーター

*phwnd*<br/>
[out]このメソッドから制御が戻るときに、呼び出しから返される HWND へのポインターが含まれています、`GetFocus`プレビュー ハンドラーのフォア グラウンド スレッドからの関数。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返します。または、それ以外の場合、エラー値。

### <a name="remarks"></a>Remarks

##  <a name="onpreviewhandlertranslateaccelerator"></a>  CDocument::OnPreviewHandlerTranslateAccelerator

プレビュー ハンドラーが実行されているプロセスのメッセージ ポンプから渡されたキーストロークを処理するために、プレビュー ハンドラーに指示します。

```
virtual HRESULT OnPreviewHandlerTranslateAccelerator(MSG* pmsg);
```

### <a name="parameters"></a>パラメーター

*pmsg*<br/>
[in]ウィンドウ メッセージへのポインター。

### <a name="return-value"></a>戻り値

キーストロークのメッセージは、プレビュー ハンドラーによって処理されることができる場合、ハンドラーはそれを処理し、S_OK を返します。 使用してホストには、プレビュー ハンドラーでは、キー入力メッセージを処理できない場合`IPreviewHandlerFrame::TranslateAccelerator`します。 ホストは、メッセージを処理する場合、このメソッドは、S_OK を返します。 ホストにメッセージが処理されない場合、このメソッドは S_FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="onrichpreviewbackcolorchanged"></a>  CDocument::OnRichPreviewBackColorChanged

豊富なプレビューの背景色が変更されたときに呼び出されます。

```
virtual void OnRichPreviewBackColorChanged();
```

### <a name="remarks"></a>Remarks

##  <a name="onrichpreviewfontchanged"></a>  CDocument::OnRichPreviewFontChanged

リッチ プレビューのフォントが変更されたときに呼び出されます。

```
virtual void OnRichPreviewFontChanged();
```

### <a name="remarks"></a>Remarks

##  <a name="onrichpreviewsitechanged"></a>  CDocument::OnRichPreviewSiteChanged

リッチ プレビュー サイトが変更されたときに呼び出されます。

```
virtual void OnRichPreviewSiteChanged();
```

### <a name="remarks"></a>Remarks

##  <a name="onrichpreviewtextcolorchanged"></a>  CDocument::OnRichPreviewTextColorChanged

リッチ プレビュー テキストの色が変更されたときに呼び出されます。

```
virtual void OnRichPreviewTextColorChanged();
```

### <a name="remarks"></a>Remarks

##  <a name="onsavedocument"></a>  CDocument::OnSaveDocument

ファイルの保存またはファイル名を付けてコマンドの一部として、フレームワークによって呼び出されます。

```
virtual BOOL OnSaveDocument(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
ファイルの保存先の完全修飾パスを指します。

### <a name="return-value"></a>戻り値

以外の場合は、ドキュメントが正常に保存されました。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

この関数の既定の実装は、指定したファイルを開き[cobject::serialize](../../mfc/reference/cobject-class.md#serialize)ドキュメントのデータを書き込むファイル、および、マークとしてドキュメントをクリーンアップします。 フレームワークは、ドキュメントを保存するときに、特別な処理を実行する場合は、この関数をオーバーライドします。 たとえば、ドキュメントが別々 のファイルではなく、データベース内のレコードを表すアプリケーションを作成する場合があります。

##  <a name="onunloadhandler"></a>  CDocument::OnUnloadHandler

プレビュー ハンドラーが読み込まれるときに、フレームワークによって呼び出されます。

```
virtual void OnUnloadHandler();
```

### <a name="remarks"></a>Remarks

##  <a name="onupdatefilesendmail"></a>  CDocument::OnUpdateFileSendMail

メール サポート (MAPI) が存在する場合は、判定コマンドを有効にします。

```
void OnUpdateFileSendMail(CCmdUI* pCmdUI);
```

### <a name="parameters"></a>パラメーター

*pCmdUI*<br/>
ポインター、 [CCmdUI](../../mfc/reference/ccmdui-class.md)判定コマンドに関連付けられているオブジェクト。

### <a name="remarks"></a>Remarks

それ以外の場合、関数では、適切なメニュー項目の上または区切り記号を含む、メニューから判定コマンドを削除します。 場合に、MAPI が有効になっている MAPI32 します。DLL は、パスと、WIN の [メール] セクションに存在します。INI ファイル、MAPI = 1。 ほとんどのアプリケーションは、[ファイル] メニューのこのコマンドを配置します。

`CDocument` サポート メール サポート (MAPI) が存在する場合にメールを使ってドキュメントを送信します。 記事を参照して[MAPI トピック](../../mfc/mapi.md)と[MFC での MAPI サポート](../../mfc/mapi-support-in-mfc.md)します。

##  <a name="precloseframe"></a>  CDocument::PreCloseFrame

このメンバー関数は、フレーム ウィンドウが破棄される前に、フレームワークによって呼び出されます。

```
virtual void PreCloseFrame(CFrameWnd* pFrame);
```

### <a name="parameters"></a>パラメーター

*pFrame*<br/>
ポインター、 [CFrameWnd](../../mfc/reference/cframewnd-class.md) 、関連付けられているを保持している`CDocument`オブジェクト。

### <a name="remarks"></a>Remarks

カスタムのクリーンアップが、基本クラスも必ずオーバーライドできます。

既定値は`PreCloseFrame`何も`CDocument`します。 `CDocument`-クラスを派生[COleDocument](../../mfc/reference/coledocument-class.md)と[CRichEditDoc](../../mfc/reference/cricheditdoc-class.md)このメンバー関数を使用します。

##  <a name="readnextchunkvalue"></a>  CDocument::ReadNextChunkValue

次のチャンク値を読み取ります。

```
virtual BOOL ReadNextChunkValue(IFilterChunkValue** ppValue);
```

### <a name="parameters"></a>パラメーター

*ppValue*<br/>
[out]関数から制御が戻るときに*ppValue*読み取られた値が含まれています。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

##  <a name="releasefile"></a>  CDocument::ReleaseFile

このメンバー関数は、他のアプリケーションで使用するために使用できるように、ファイルをリリースするためにフレームワークによって呼び出されます。

```
virtual void ReleaseFile(
    CFile* pFile,
    BOOL bAbort);
```

### <a name="parameters"></a>パラメーター

*pFile*<br/>
リリースされる CFile オブジェクトへのポインター。

*bAbort*<br/>
ファイルがいずれかを使用して解放するかどうかを指定`CFile::Close`または`CFile::Abort`します。 ファイルを使用して解放する場合は FALSE[データ](../../mfc/reference/cfile-class.md#close);ファイルを使用して解放する場合は TRUE。[解放](../../mfc/reference/cfile-class.md#abort)します。

### <a name="remarks"></a>Remarks

場合*bAbort*が true の場合、`ReleaseFile`呼び出し`CFile::Abort`、され、ファイルが解放されます。 `CFile::Abort` 例外はスローされません。

場合*bAbort* false で、`ReleaseFile`呼び出し`CFile::Close`され、ファイルが解放されます。

ファイルが解放される前に、ユーザーが操作を要求するには、このメンバー関数をオーバーライドします。

##  <a name="removechunk"></a>  CDocument::RemoveChunk

指定した GUID のチャンクを削除します。

```
virtual void RemoveChunk(
    REFCLSID guid,
    DWORD pid);
```

### <a name="parameters"></a>パラメーター

*Guid*<br/>
削除するチャンクの GUID を指定します。

*pid*<br/>
削除するチャンクの PID を指定します。

### <a name="remarks"></a>Remarks

##  <a name="removeview"></a>  CDocument::RemoveView

ドキュメントからビューをデタッチするには、この関数を呼び出します。

```
void RemoveView(CView* pView);
```

### <a name="parameters"></a>パラメーター

*pView*<br/>
削除されるビューへのポインター。

### <a name="remarks"></a>Remarks

この関数は、ドキュメントに関連付けられたビューの一覧から、指定されたビューを削除します。また、ビューのドキュメントのポインターを NULL に設定します。 フレーム ウィンドウが閉じているか、スプリッター ウィンドウのペインが閉じられたときに、この関数は、フレームワークによって呼び出されます。

ビューを手動でデタッチされている場合にのみ、この関数を呼び出します。 ドキュメントとビューを定義することでデタッチ フレームワークをできるように、通常、 [CDocTemplate](../../mfc/reference/cdoctemplate-class.md)クラスのドキュメント、ビューのクラスとフレーム ウィンドウ クラスに関連付けるオブジェクト。

例を参照してください[AddView](#addview)のサンプルを実装します。

##  <a name="reportsaveloadexception"></a>  CDocument::ReportSaveLoadException

例外がスローされた場合に呼び出されます (通常、 [CFileException](../../mfc/reference/cfileexception-class.md)または[CArchiveException](../../mfc/reference/carchiveexception-class.md)) の保存や、ドキュメントの読み込み中にします。

```
virtual void ReportSaveLoadException(
    LPCTSTR lpszPathName,
    CException* e,
    BOOL bSaving,
    UINT nIDPDefault);
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
ポイントされていたドキュメントの名前を保存または読み込み。

*e*<br/>
スローされた例外を指します。 NULL にすることがあります。

*bSaving*<br/>
どのような操作が進行中を示すフラグします。ドキュメントが保存されている場合、0、ドキュメントが読み込まれたされている場合は 0 以外の値。

*nIDPDefault*<br/>
関数が複数の特定の 1 つを指定しない場合に表示されるエラー メッセージの識別子。

### <a name="remarks"></a>Remarks

既定の実装では、例外オブジェクトを検査し、具体的には、原因を説明するエラー メッセージを探します。 特定のメッセージが見つからない場合、または場合*e*が null の場合、一般的なメッセージで指定された、 *nIDPDefault*パラメーターを使用します。 関数は、エラー メッセージを含むメッセージ ボックスを表示します。 追加のカスタマイズされたエラー メッセージを提供したい場合は、この関数をオーバーライドします。 これは、高度なオーバーライド可能な。

##  <a name="savemodified"></a>  CDocument::SaveModified

変更されたドキュメントが終了する前に、フレームワークによって呼び出されます。

```
virtual BOOL SaveModified();
```

### <a name="return-value"></a>戻り値

続行して、ドキュメントを閉じても安全である場合、0 以外の場合ドキュメントが閉じていない場合は 0 を返します。

### <a name="remarks"></a>Remarks

この関数の既定の実装では、行われている場合、ユーザーをドキュメントに変更を保存するかどうか確認するメッセージ ボックスが表示されます。 プログラムには、別のプロンプトを表示する手順が必要な場合は、この関数をオーバーライドします。 これは、高度なオーバーライド可能な。

##  <a name="setchunkvalue"></a>  CDocument::SetChunkValue

チャンクの値を設定します。

```
virtual BOOL SetChunkValue (IFilterChunkValue* pValue);
```

### <a name="parameters"></a>パラメーター

*pValue*<br/>
設定するチャンクの値を指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

##  <a name="setmodifiedflag"></a>  CDocument::SetModifiedFlag

ドキュメントの変更を行った後は、この関数を呼び出します。

```
virtual void SetModifiedFlag(BOOL bModified = TRUE);
```

### <a name="parameters"></a>パラメーター

*bModified*<br/>
ドキュメントが変更されたかどうかを示すフラグします。

### <a name="remarks"></a>Remarks

この関数を一貫して呼び出すことによってフレームワークがドキュメントを閉じる前に変更を保存するユーザーを要求することを確認します。 通常、既定の値が TRUE を使用する必要があります、 *bModified*パラメーター。 マークはクリーンにドキュメント (変更なし)、FALSE の値は、この関数を呼び出します。

##  <a name="setpathname"></a>  CDocument::SetPathName

ドキュメントのディスク ファイルの完全修飾パスを指定するには、この関数を呼び出します。

```
virtual void SetPathName(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
ドキュメントのパスとして使用する文字列を指します。

*baddtomru です。*<br/>
ファイル名に追加するかどうか、最近使用した (MRU) ファイルの一覧を決定します。 TRUE の場合、ファイル名を追加します。FALSE の場合は追加されません。

### <a name="remarks"></a>Remarks

値に応じて*bAddToMRU*パスを追加、または、アプリケーションによって管理される MRU 一覧に追加されません。 いくつかのドキュメントがディスク ファイルに関連付けられていないことに注意してください。 オープンと保存、フレームワークによって使用されるファイルの既定の実装をオーバーライドしている場合にのみ、この関数を呼び出します。

##  <a name="settitle"></a>  CDocument::SetTitle

ドキュメントのタイトル (フレーム ウィンドウのタイトル バーに表示される文字列) を指定するには、この関数を呼び出します。

```
virtual void SetTitle(LPCTSTR lpszTitle);
```

### <a name="parameters"></a>パラメーター

*lpszTitle*<br/>
ドキュメントのタイトルとして使用する文字列を指します。

### <a name="remarks"></a>Remarks

この関数を呼び出すと、ドキュメントを表示するすべてのフレーム ウィンドウのタイトルが更新されます。

##  <a name="updateallviews"></a>  CDocument::UpdateAllViews

ドキュメントが変更された後は、この関数を呼び出します。

```
void UpdateAllViews(
    CView* pSender,
    LPARAM lHint = 0L,
    CObject* pHint = NULL);
```

### <a name="parameters"></a>パラメーター

*pSender*<br/>
ドキュメントを変更するビューを指すすべてのビューを更新するか場合は null です。

*lHint*<br/>
変更に関する情報が含まれています。

*pHint*<br/>
変更に関する情報を格納するオブジェクトを指します。

### <a name="remarks"></a>Remarks

呼び出した後は、この関数を呼び出す必要があります、 [SetModifiedFlag](#setmodifiedflag)メンバー関数。 この関数で指定されたビューを除く、ドキュメントにアタッチされているそれぞれのビューに通知*pSender*ドキュメントが変更されました。 通常この関数を呼び出すビュー クラスから、ユーザーには、ビューを使用して、ドキュメントが変更された後です。

この関数を呼び出して、 [CView::OnUpdate](../../mfc/reference/cview-class.md#onupdate)を除き、送信ドキュメントのビューの各メンバー関数を表示、渡す*pHint*と*lHint*。 ドキュメントに加えられた変更についてのビューに情報を渡すには、これらのパラメーターを使用します。 使用して情報をエンコードする*lHint*定義することや、 [CObject](../../mfc/reference/cobject-class.md)-派生クラスを変更についての情報を格納しを使用してそのクラスのオブジェクトを渡す*pHint*. 上書き、`CView::OnUpdate`でメンバー関数、 [CView](../../mfc/reference/cview-class.md)-渡された情報に基づいて、ビューの表示の更新を最適化するためにクラスを派生します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#64](../../mfc/codesnippet/cpp/cdocument-class_9.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプルは](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル SNAPVW](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル NPP](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[CDocTemplate クラス](../../mfc/reference/cdoctemplate-class.md)
