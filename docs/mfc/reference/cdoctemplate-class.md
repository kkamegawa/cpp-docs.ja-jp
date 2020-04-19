---
title: CDocTemplate クラス
ms.date: 11/04/2016
f1_keywords:
- CDocTemplate
- AFXWIN/CDocTemplate
- AFXWIN/CDocTemplate::CDocTemplate
- AFXWIN/CDocTemplate::AddDocument
- AFXWIN/CDocTemplate::CloseAllDocuments
- AFXWIN/CDocTemplate::CreateNewDocument
- AFXWIN/CDocTemplate::CreateNewFrame
- AFXWIN/CDocTemplate::CreateOleFrame
- AFXWIN/CDocTemplate::CreatePreviewFrame
- AFXWIN/CDocTemplate::GetDocString
- AFXWIN/CDocTemplate::GetFirstDocPosition
- AFXWIN/CDocTemplate::GetNextDoc
- AFXWIN/CDocTemplate::InitialUpdateFrame
- AFXWIN/CDocTemplate::LoadTemplate
- AFXWIN/CDocTemplate::MatchDocType
- AFXWIN/CDocTemplate::OpenDocumentFile
- AFXWIN/CDocTemplate::RemoveDocument
- AFXWIN/CDocTemplate::SaveAllModified
- AFXWIN/CDocTemplate::SetContainerInfo
- AFXWIN/CDocTemplate::SetDefaultTitle
- AFXWIN/CDocTemplate::SetPreviewInfo
- AFXWIN/CDocTemplate::SetServerInfo
helpviewer_keywords:
- CDocTemplate [MFC], CDocTemplate
- CDocTemplate [MFC], AddDocument
- CDocTemplate [MFC], CloseAllDocuments
- CDocTemplate [MFC], CreateNewDocument
- CDocTemplate [MFC], CreateNewFrame
- CDocTemplate [MFC], CreateOleFrame
- CDocTemplate [MFC], CreatePreviewFrame
- CDocTemplate [MFC], GetDocString
- CDocTemplate [MFC], GetFirstDocPosition
- CDocTemplate [MFC], GetNextDoc
- CDocTemplate [MFC], InitialUpdateFrame
- CDocTemplate [MFC], LoadTemplate
- CDocTemplate [MFC], MatchDocType
- CDocTemplate [MFC], OpenDocumentFile
- CDocTemplate [MFC], RemoveDocument
- CDocTemplate [MFC], SaveAllModified
- CDocTemplate [MFC], SetContainerInfo
- CDocTemplate [MFC], SetDefaultTitle
- CDocTemplate [MFC], SetPreviewInfo
- CDocTemplate [MFC], SetServerInfo
ms.assetid: 14b41a1f-bf9d-4eac-b6a8-4c54ffcc77f6
ms.openlocfilehash: 3b2d84af9be8e5c606cde8794b51e12207dcdec9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62163988"
---
# <a name="cdoctemplate-class"></a>CDocTemplate クラス

ドキュメント テンプレートの基本的な機能を定義する抽象基底クラスです。

## <a name="syntax"></a>構文

```
class CDocTemplate : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CDocTemplate::CDocTemplate](#cdoctemplate)|`CDocTemplate` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDocTemplate::AddDocument](#adddocument)|テンプレートにドキュメントを追加します。|
|[CDocTemplate::CloseAllDocuments](#closealldocuments)|このテンプレートに関連付けられているすべてのドキュメントを閉じます。|
|[CDocTemplate::CreateNewDocument](#createnewdocument)|新しいドキュメントを作成します。|
|[CDocTemplate::CreateNewFrame](#createnewframe)|ドキュメントとビューを含む新しいフレーム ウィンドウを作成します。|
|[CDocTemplate::CreateOleFrame](#createoleframe)|OLE が有効なフレーム ウィンドウを作成します。|
|[CDocTemplate::CreatePreviewFrame](#createpreviewframe)|豊富なプレビューに使用される子フレームを作成します。|
|[CDocTemplate::GetDocString](#getdocstring)|ドキュメントの種類に関連付けられている文字列を取得します。|
|[CDocTemplate::GetFirstDocPosition](#getfirstdocposition)|このテンプレートに関連付けられた最初のドキュメントの位置を取得します。|
|[CDocTemplate::GetNextDoc](#getnextdoc)|ドキュメントおよび次の位置を取得します。|
|[CDocTemplate::InitialUpdateFrame](#initialupdateframe)|フレーム ウィンドウを初期化し、必要に応じて、可視化します。|
|[CDocTemplate::LoadTemplate](#loadtemplate)|リソースを読み込み、指定された`CDocTemplate`または派生クラス。|
|[CDocTemplate::MatchDocType](#matchdoctype)|ドキュメントの種類とテンプレート間の一致で信頼度を決定します。|
|[CDocTemplate::OpenDocumentFile](#opendocumentfile)|パス名で指定されたファイルを開きます。|
|[CDocTemplate::RemoveDocument](#removedocument)|テンプレートからドキュメントを削除します。|
|[CDocTemplate::SaveAllModified](#saveallmodified)|変更されたこのテンプレートに関連付けられているすべてのドキュメントを保存します。|
|[CDocTemplate::SetContainerInfo](#setcontainerinfo)|インプレース OLE 項目を編集するときに、OLE コンテナーのリソースを決定します。|
|[CDocTemplate::SetDefaultTitle](#setdefaulttitle)|ドキュメント ウィンドウのタイトル バーで、既定のタイトルを表示します。|
|[CDocTemplate::SetPreviewInfo](#setpreviewinfo)|プロセス外の設定はプレビュー ハンドラーです。|
|[CDocTemplate::SetServerInfo](#setserverinfo)|サーバーのドキュメントが埋め込まれているまたはインプレースを編集するときは、リソースやクラスを決定します。|

## <a name="remarks"></a>Remarks

通常、アプリケーションの実装では 1 つまたは複数のドキュメント テンプレートを作成する`InitInstance`関数。 ドキュメント テンプレートでは、3 種類のクラス間のリレーションシップを定義します。

- ドキュメント クラスから派生した`CDocument`します。

- ビュー クラスの上に表示されるドキュメント クラスからのデータが表示されます。 このクラスから派生できます`CView`、 `CScrollView`、 `CFormView`、または`CEditView`します。 (使用することも`CEditView`直接)。

- ビューを含むフレーム ウィンドウ クラス。 シングル ドキュメント インターフェイス (SDI) アプリケーションからには、このクラスを派生する`CFrameWnd`します。 このクラスを派生するマルチ ドキュメント インターフェイス (MDI) アプリケーションでは、`CMDIChildWnd`します。 使用することができる場合、フレーム ウィンドウの動作をカスタマイズする必要はありません、`CFrameWnd`または`CMDIChildWnd`独自のクラスを派生させることがなく直接します。

アプリケーションでは、サポートされているドキュメントの種類ごとに 1 つのドキュメント テンプレートを持ちます。 たとえば、アプリケーションでは、スプレッドシートやテキスト ドキュメントの両方をサポートする場合、アプリケーションには、2 つのドキュメント テンプレート オブジェクトがあります。 それぞれのドキュメント テンプレートが作成して、その型のすべてのドキュメントを管理する責任を負います。

ドキュメント テンプレートへのポインターを格納する、`CRuntimeClass`ドキュメント、ビュー、およびフレーム ウィンドウ クラスのオブジェクト。 これら`CRuntimeClass`ドキュメント テンプレートを作成するときに、オブジェクトが指定されています。

ドキュメント テンプレートには、(メニューのアイコン、またはアクセラレータ テーブル リソース) などのドキュメントの種類で使用するリソースの ID が含まれています。 ドキュメント テンプレートでは、そのドキュメントの種類に関する追加情報を含む文字列もあります。 ドキュメントの種類 (たとえば、「ワークシート」) とファイル拡張子 (たとえば、".xls"など) の名前が含まれます。 必要に応じて、アプリケーションのユーザー インターフェイス、Windows ファイル マネージャーでは、およびオブジェクトのリンクと埋め込み (OLE) のサポートで使用されるその他の文字列を含めることができます。

アプリケーションが、OLE コンテナーやサーバーの場合は、ドキュメント テンプレートには、インプレース アクティブ化時に使用するメニューの ID も定義します。 アプリケーションが OLE サーバーである場合は、ドキュメント テンプレートは、インプレース アクティブ化時に使用するメニューのツールバーの ID を定義します。 呼び出すことによってこれらの追加 OLE リソースを指定する`SetContainerInfo`と`SetServerInfo`します。

`CDocTemplate`抽象クラスでは、クラスを直接使用することはできません。 一般的なアプリケーションを使用して、2 つのいずれかの`CDocTemplate`-Microsoft Foundation Class ライブラリで提供されるクラスを派生: `CSingleDocTemplate`、SDI を実装して`CMultiDocTemplate`MDI を実装します。 ドキュメント テンプレートの使用に関する詳細については、これらのクラスを参照してください。

アプリケーションでは、ユーザー インターフェイスのパラダイムは SDI または MDI 根本的に異なる必要がある場合から、独自のクラスを派生できます`CDocTemplate`します。

詳細については`CDocTemplate`を参照してください[ドキュメント テンプレートとドキュメント/ビューの作成手順](../../mfc/document-templates-and-the-document-view-creation-process.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`CDocTemplate`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="adddocument"></a>  CDocTemplate::AddDocument

テンプレートにドキュメントを追加するのにには、この関数を使用します。

```
virtual void AddDocument(CDocument* pDoc);
```

### <a name="parameters"></a>パラメーター

*pDoc*<br/>
追加するドキュメントへのポインター。

### <a name="remarks"></a>Remarks

派生クラス[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)と[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)この関数をオーバーライドします。 独自のドキュメント テンプレート クラスを派生させるかどうか`CDocTemplate`、派生クラスは、この関数をオーバーライドする必要があります。

##  <a name="cdoctemplate"></a>  CDocTemplate::CDocTemplate

`CDocTemplate` オブジェクトを構築します。

```
CDocTemplate (
    UINT nIDResource,
    CRuntimeClass* pDocClass,
    CRuntimeClass* pFrameClass,
    CRuntimeClass* pViewClass);
```

### <a name="parameters"></a>パラメーター

*可能*<br/>
ドキュメントの種類で使用するリソースの ID を指定します。 これには、メニューのアイコン、アクセラレータ テーブル、および文字列リソースを含めることができます。

文字列リソースは、'\n' 文字で区切られた最大 7 つの部分文字列で構成されます (部分文字列が含まれない場合 '\n' 文字はプレース ホルダーとして必要です。 ただし、末尾の '\n' 文字は必要ありません)。これらの部分文字列には、ドキュメントの種類について説明します。 これらの部分文字列については、次を参照してください。 [GetDocString](#getdocstring)します。 この文字列リソースには、アプリケーションのリソース ファイルが記載されています。 例:

```RC
// MYCALC.RC
STRINGTABLE PRELOAD DISCARDABLE
BEGIN
  IDR_SHEETTYPE "\nSheet\nWorksheet\nWorksheets (*.myc)\n.myc\n MyCalcSheet\nMyCalc Worksheet"
END
```

文字列が、'\n' 文字で始まることに注意してください。これは、最初の部分文字列が MDI アプリケーションは使用されません、これが含まれていないためです。 ストリング エディターを使用してこの文字列を編集できます。文字列全体は、7 つの個別のエントリとしてではなく文字列エディターで、1 つのエントリとして表示されます。

*pDocClass*<br/>
指す、`CRuntimeClass`ドキュメント クラスのオブジェクト。 このクラスは、 `CDocument`-ドキュメントを表すために定義するクラスを派生します。

*pFrameClass*<br/>
指す、`CRuntimeClass`フレーム ウィンドウ クラスのオブジェクト。 このクラスにすることができます、 `CFrameWnd`-クラスを派生することもできます`CFrameWnd`自体、メイン フレーム ウィンドウの既定の動作をする場合。

*pViewClass*<br/>
指す、`CRuntimeClass`ビュー クラスのオブジェクト。 このクラスは、 `CView`-ドキュメントの表示を定義するクラスを派生します。

### <a name="remarks"></a>Remarks

このメンバー関数を使用して、構築、`CDocTemplate`オブジェクト。 動的に割り当てる、`CDocTemplate`オブジェクトに渡すと[とき](../../mfc/reference/cwinapp-class.md#adddoctemplate)から、`InitInstance`アプリケーション クラスのメンバー関数。

##  <a name="closealldocuments"></a>  CDocTemplate::CloseAllDocuments

すべての開いている文書を閉じるには、このメンバー関数を呼び出します。

```
virtual void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>パラメーター

*bEndSession*<br/>
使用しません。

### <a name="remarks"></a>Remarks

このメンバー関数は、通常のファイルの終了コマンドの一部として使用されます。 この関数の既定の実装、[のに](../../mfc/reference/cdocument-class.md#deletecontents)メンバー関数は、ドキュメントのデータと削除し、ドキュメントにアタッチされているすべてのビューのフレーム ウィンドウを閉じます。

文書を閉じる前に特別なクリーンアップの処理を実行するユーザーを要求する場合は、この関数をオーバーライドします。 などのドキュメントでは、データベース内のレコードを表している場合、データベースを終了するには、この関数をオーバーライドします。

##  <a name="createnewdocument"></a>  CDocTemplate::CreateNewDocument

このドキュメント テンプレートに関連付けられた型の新しいドキュメントを作成するには、このメンバー関数を呼び出します。

```
virtual CDocument* CreateNewDocument();
```

### <a name="return-value"></a>戻り値

新しく作成されたドキュメント、またはエラーが発生した場合は NULL へのポインター。

##  <a name="createnewframe"></a>  CDocTemplate::CreateNewFrame

ドキュメントとビューを含む新しいフレーム ウィンドウを作成します。

```
virtual CFrameWnd* CreateNewFrame(
    CDocument* pDoc,
    CFrameWnd* pOther);
```

### <a name="parameters"></a>パラメーター

*pDoc*<br/>
ドキュメントは、新しいフレーム ウィンドウが参照してください。 NULL にすることができます。

*pOther*<br/>
フレーム ウィンドウを新しいフレーム ウィンドウは、基にします。 NULL にすることができます。

### <a name="return-value"></a>戻り値

新しく作成されたフレーム ウィンドウ、またはエラーが発生した場合は NULL へのポインター。

### <a name="remarks"></a>Remarks

`CreateNewFrame` 使用して、`CRuntimeClass`オブジェクトがドキュメントを添付し、新しいフレーム ウィンドウを作成するコンス トラクターに渡されます。 場合、 *pDoc*パラメーターが NULL で、フレームワークは、トレース メッセージを出力します。

*POther*パラメーターは、新しいウィンドウのコマンドを実装するために使用します。 フレーム ウィンドウは、新しいフレーム ウィンドウのモデルを提供します。 新しいフレーム ウィンドウを非表示には、通常は作成されます。 新しいファイルとファイルを開くの標準的なフレームワークの実装の外部のフレーム ウィンドウを作成するには、この関数を呼び出します。

##  <a name="createoleframe"></a>  CDocTemplate::CreateOleFrame

OLE のフレーム ウィンドウを作成します。

```
CFrameWnd* CreateOleFrame(
    CWnd* pParentWnd,
    CDocument* pDoc,
    BOOL bCreateView);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
フレームの親ウィンドウへのポインター。

*pDoc*<br/>
新しい OLE フレーム ウィンドウを参照するドキュメントへのポインター。

*bCreateView*<br/>
フレームとビューを作成するかどうかを判断します。

### <a name="return-value"></a>戻り値

成功した場合は、フレーム ウィンドウへのポインターそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

場合*bCreateView* 0 の場合は、空のフレームが作成されます。

##  <a name="getdocstring"></a>  CDocTemplate::GetDocString

ドキュメントの種類に関連付けられている文字列を取得します。

```
virtual BOOL GetDocString(
    CString& rString,
    enum DocStringIndex index) const;
```

### <a name="parameters"></a>パラメーター

*rString*<br/>
参照を`CString`関数が戻るときに、文字列を格納するオブジェクト。

*index*<br/>
ドキュメントの種類を表す文字列から取得する部分文字列のインデックス。 このパラメーターには、次のいずれかの値を指定できます。

- `CDocTemplate::windowTitle` アプリケーション ウィンドウのタイトル バーの (たとえば、"Excel") に表示される名前です。 SDI アプリケーションのドキュメント テンプレートにのみ存在します。

- `CDocTemplate::docName` 既定のドキュメント名 (たとえば、「シート」) のルートします。 このルートでは、数字を付加は、ユーザーが (たとえば、「シート 1」または「シート 2」) は、[ファイル] メニューから新しいコマンドを選択するたびにこの型の新しいドキュメントの既定の名前に使用されます。 指定しない場合は既定値として「無題」が使用されます。

- `CDocTemplate::fileNewName` このドキュメントの種類の名前です。 アプリケーションでは、ドキュメントの 1 つ以上の型をサポートする場合は、新しいファイル ダイアログ ボックス (たとえば、「ワークシート」) にこの文字列が表示されます。 指定しない場合、ドキュメントの種類がファイルの新しいコマンドを使用してアクセスできません。

- `CDocTemplate::filterName` ドキュメントの種類と一致するドキュメントのこの型のワイルドカード フィルターの説明です。 この文字列は、ファイルを開く ダイアログ ボックス (「ワークシート (*.xls)」など) でファイルの種類のドロップダウン リストに表示されます。 指定しない場合、ドキュメントの種類がファイルを開くコマンドを使用してアクセスできません。

- `CDocTemplate::filterExt` この型 (たとえば、".xls"など) のドキュメントの拡張機能。 指定しない場合、ドキュメントの種類がファイルを開くコマンドを使用してアクセスできません。

- `CDocTemplate::regFileTypeId` Windows によって管理される登録データベースに格納されるドキュメントの種類の識別子。 この文字列は内部の使用のみ (たとえば、「したりできます」) されます。 指定しない場合、ドキュメントの種類が、Windows ファイル マネージャーを登録することはできません。

- `CDocTemplate::regFileTypeName` 登録情報データベースに格納されるドキュメントの種類の名前です。 この文字列は、登録情報データベース (たとえば、「Microsoft Excel ワークシート」) にアクセスするアプリケーションのダイアログ ボックスに表示されます。

### <a name="return-value"></a>戻り値

指定された部分文字列が見つかった場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

ドキュメント型を記述する特定の部分文字列を取得するには、この関数を呼び出します。 これらの部分文字列を含む文字列では、ドキュメント テンプレートに格納され、アプリケーションのリソース ファイル内の文字列から派生します。 フレームワークは、アプリケーションのユーザー インターフェイスに必要な文字列を取得するには、この関数を呼び出します。 アプリケーションのドキュメントのファイル名拡張子を指定した場合、またフレームワーク Windows 登録データベースにエントリを追加するときにこれにより、ドキュメントを Windows ファイル マネージャーから開くことができます。

独自のクラスを派生する場合にのみ、この関数を呼び出す`CDocTemplate`します。

##  <a name="getfirstdocposition"></a>  CDocTemplate::GetFirstDocPosition

このテンプレートに関連付けられた最初のドキュメントの位置を取得します。

```
virtual POSITION GetFirstDocPosition() const = 0;
```

### <a name="return-value"></a>戻り値

ドキュメント テンプレートに関連付けられたドキュメントの一覧を反復処理するために使用する位置の値または、リストが空の場合は NULL です。

### <a name="remarks"></a>Remarks

このテンプレートに関連付けられているドキュメントの一覧で最初のドキュメントの位置を取得するのにには、この関数を使用します。 位置の値を使用して、引数として[CDocTemplate::GetNextDoc](#getnextdoc)テンプレートに関連付けられているドキュメントの一覧を反復処理します。

[CSingleDocTemplate](../../mfc/reference/csingledoctemplate-class.md)と[CMultiDocTemplate](../../mfc/reference/cmultidoctemplate-class.md)両方が純粋仮想関数をオーバーライドします。 任意のクラスから派生した`CDocTemplate`も、この関数をオーバーライドしなければなりません。

##  <a name="getnextdoc"></a>  CDocTemplate::GetNextDoc

識別されるリストの要素を取得*Rpo*、設定し、 *Rpo*一覧の次のエントリの位置の値にします。

```
virtual CDocument* GetNextDoc(POSITION& rPos) const = 0;
```

### <a name="return-value"></a>戻り値

このテンプレートに関連付けられているドキュメントの一覧で、次のドキュメントへのポインター。

### <a name="parameters"></a>パラメーター

*Rpo*<br/>
以前の呼び出しによって返される位置の値への参照を[GetFirstDocPosition](#getfirstdocposition)または`GetNextDoc`します。

### <a name="remarks"></a>Remarks

場合は、取得された最後の要素を一覧での新しい値*Rpo* NULL に設定されます。

使用することができます`GetNextDoc`への呼び出しを初期位置を確立する場合は、順方向の反復ループで[GetFirstDocPosition](#getfirstdocposition)します。

位置の値がリスト内の有効な位置を表すことを確認する必要があります。 有効な場合は、Microsoft Foundation Class ライブラリのデバッグ バージョンはアサートします。

##  <a name="initialupdateframe"></a>  CDocTemplate::InitialUpdateFrame

フレーム ウィンドウを初期化し、必要に応じて、可視化します。

```
virtual void InitialUpdateFrame(
    CFrameWnd* pFrame,
    CDocument* pDoc,
    BOOL bMakeVisible = TRUE);
```

### <a name="parameters"></a>パラメーター

*pFrame*<br/>
最初の更新の必要があるフレーム ウィンドウです。

*pDoc*<br/>
フレームが関連付けられているドキュメントです。 NULL にすることができます。

*bMakeVisible*<br/>
フレームが表示され、アクティブになる必要があるかどうかを示します。

### <a name="remarks"></a>Remarks

呼び出す`IntitialUpdateFrame`で新しいフレームを作成した後`CreateNewFrame`します。 受信するには、そのフレーム ウィンドウ ビューは、この関数を呼び出すと、その`OnInitialUpdate`呼び出し。 また場合は、存在していなかった以前、アクティブなビュー、フレーム ウィンドウのプライマリ ビューがアクティブになります。プライマリ ビューは、子 AFX_IDW_PANE_FIRST の ID を持つビューです。 最後に、フレーム ウィンドウが表示される場合*bMakeVisible* 0 以外の場合します。 場合*bMakeVisible* 0、現在のフォーカスとフレーム ウィンドウの表示状態は変更されません。

新しいファイルとファイルを開くのフレームワークの実装を使用する場合は、この関数を呼び出す必要はありません。

##  <a name="loadtemplate"></a>  CDocTemplate::LoadTemplate

リソースを読み込み、指定された`CDocTemplate`または派生クラス。

```
virtual void LoadTemplate();
```

### <a name="remarks"></a>Remarks

リソースを読み込むために、フレームワークによって呼び出されます、指定された`CDocTemplate`または派生クラス。 通常ときに呼び出されます構築時を除く、テンプレートはグローバルに構築されています。 その場合、呼び出し`LoadTemplate`までが遅延される[とき](../../mfc/reference/cwinapp-class.md#adddoctemplate)が呼び出されます。

##  <a name="matchdoctype"></a>  CDocTemplate::MatchDocType

ドキュメントの種類とテンプレート間の一致で信頼度を決定します。

```
virtual Confidence MatchDocType(
    LPCTSTR lpszPathName,
    CDocument*& rpDocMatch);
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
型が決定されますが、ファイルのパス名。

*れていなくて*<br/>
によって、ファイルが指定されている場合、一致するドキュメントが割り当てられているドキュメントへのポインター*終了*は既に開いています。

### <a name="return-value"></a>戻り値

値、**信頼**列挙体は、次のように定義されます。

```
enum Confidence
    {
    noAttempt,
    maybeAttemptForeign,
    maybeAttemptNative,
    yesAttemptForeign,
    yesAttemptNative,
    yesAlreadyOpen
    };
```

### <a name="remarks"></a>Remarks

この関数を使用して、ファイルを開くときに使用するドキュメント テンプレートの種類を決定します。 アプリケーションでは、複数のファイルの種類をサポートする場合、することができます関数を使ってこの呼び出すことによって、指定されたファイルの適切な使用可能なドキュメント テンプレートのどれを判断`MatchDocType`を有効にして、に従ってテンプレートの選択内の各テンプレート信頼度の値が返されます。

によって、ファイルが指定されている場合*終了*が既に開いている場合は、この関数を返します`CDocTemplate::yesAlreadyOpen`ファイルのコピーと`CDocument`でオブジェクトにオブジェクト*れていなくて*します。

ファイルが開いていて、拡張機能でもない場合*終了*で指定された拡張機能と一致する`CDocTemplate::filterExt`、この関数を返します`CDocTemplate::yesAttemptNative`設定と*れていなくて*を NULL にします。 詳細については`CDocTemplate::filterExt`を参照してください[CDocTemplate::GetDocString](#getdocstring)します。

関数を返しますのかどうかは、どちらの場合は true、`CDocTemplate::yesAttemptForeign`します。

既定の実装は返されません`CDocTemplate::maybeAttemptForeign`または`CDocTemplate::maybeAttemptNative`します。 これら 2 つの値を使用して、アプリケーションに適した型の一致のロジックを実装するには、この関数をオーバーライド、**信頼**列挙体。

##  <a name="opendocumentfile"></a>  CDocTemplate::OpenDocumentFile

パスで指定されたファイルを開きます。

```
virtual CDocument* OpenDocumentFile(LPCTSTR lpszPathName) = 0;

virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszPathName,
    BOOL bAddToMRU) = 0;
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
[in]開かれているドキュメントを含むファイルのパスへのポインター。

*baddtomru です。*<br/>
[in]TRUE は、ドキュメントが最新のファイルのいずれかを示しますFALSE は、ドキュメントがない最新のファイルのいずれかを示します。

### <a name="return-value"></a>戻り値

ファイルの名前は、ドキュメントへのポインター*終了*;失敗した場合は NULL です。

### <a name="remarks"></a>Remarks

パスが指定されたファイルを開き*終了*します。 場合*終了*が null の場合、このテンプレートに関連付けられた型のドキュメントを含む新しいファイルが作成されます。

##  <a name="removedocument"></a>  CDocTemplate::RemoveDocument

によって示されるドキュメントを削除します*pDoc*このテンプレートに関連付けられているドキュメントの一覧から。

```
virtual void RemoveDocument(CDocument* pDoc);
```

### <a name="parameters"></a>パラメーター

*pDoc*<br/>
削除するドキュメントへのポインター。

### <a name="remarks"></a>Remarks

派生クラス`CMultiDocTemplate`と`CSingleDocTemplate`この関数をオーバーライドします。 独自のドキュメント テンプレート クラスを派生させるかどうか`CDocTemplate`、派生クラスは、この関数をオーバーライドする必要があります。

##  <a name="saveallmodified"></a>  CDocTemplate::SaveAllModified

変更されたすべてのドキュメントを保存します。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>戻り値

成功した場合は 0 以外それ以外の場合 0 を返します。

##  <a name="setcontainerinfo"></a>  CDocTemplate::SetContainerInfo

インプレース OLE 項目を編集するときに、OLE コンテナーのリソースを決定します。

```
void SetContainerInfo(UINT nIDOleInPlaceContainer);
```

### <a name="parameters"></a>パラメーター

*nIDOleInPlaceContainer*<br/>
埋め込みオブジェクトがアクティブになったときに使用されるリソースの ID。

### <a name="remarks"></a>Remarks

OLE オブジェクトは、インプレース アクティブ化されるときに使用されるリソースを設定するには、この関数を呼び出します。 これらのリソースには、メニューとアクセラレータ テーブルを含めることができます。 この関数が呼び出されます、通常、 [:initinstance](../../mfc/reference/cwinapp-class.md#initinstance)アプリケーションの関数。

関連付けられているメニュー *nIDOleInPlaceContainer*コンテナー アプリケーションのメニュー項目をマージするアクティブなインプレース項目のメニューを許可する区切り記号が含まれています。 サーバーとコンテナーのメニューのマージの詳細については、この記事を参照してください。[メニューとリソース (OLE)](../../mfc/menus-and-resources-ole.md)します。

##  <a name="setdefaulttitle"></a>  CDocTemplate::SetDefaultTitle

ドキュメントの既定のタイトルを読み込むし、ドキュメントのタイトル バーに表示するには、この関数を呼び出します。

```
virtual void SetDefaultTitle(CDocument* pDocument) = 0;
```

### <a name="parameters"></a>パラメーター

*pDocument*<br/>
タイトルを設定するがドキュメントへのポインター。

### <a name="remarks"></a>Remarks

既定のタイトルについては、の説明を参照してください。`CDocTemplate::docName`で[CDocTemplate::GetDocString](#getdocstring)します。

##  <a name="setserverinfo"></a>  CDocTemplate::SetServerInfo

サーバーのドキュメントが埋め込まれているまたはインプレースを編集するときは、リソースやクラスを決定します。

```
void SetServerInfo(
    UINT nIDOleEmbedding,
    UINT nIDOleInPlaceServer = 0,
    CRuntimeClass* pOleFrameClass = NULL,
    CRuntimeClass* pOleViewClass = NULL);
```

### <a name="parameters"></a>パラメーター

*nIDOleEmbedding*<br/>
別のウィンドウで、埋め込みオブジェクトを開いたときに使用されるリソースの ID。

*nIDOleInPlaceServer*<br/>
埋め込みオブジェクトが使用されているリソース ID では、インプレース アクティブ化されます。

*pOleFrameClass*<br/>
ポインターを[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)インプレース アクティブ化が発生したときに作成されるフレーム ウィンドウ オブジェクトのクラス情報を含む構造体。

*pOleViewClass*<br/>
ポインターを`CRuntimeClass`クラスについては、インプレース アクティブ化を行うときに作成したビュー オブジェクトを含む構造体。

### <a name="remarks"></a>Remarks

ユーザーは、埋め込みオブジェクトのアクティブ化を要求したときに、サーバー アプリケーションで使用されるリソースを特定するには、このメンバー関数を呼び出します。 これらのリソースは、メニューとアクセラレータ テーブルで構成されます。 この関数が呼び出されます、通常、`InitInstance`のアプリケーション。

関連付けられているメニュー *nIDOleInPlaceServer*サーバー メニューのマージするコンテナーのメニューを使用できるようにするための区切り記号が含まれています。 サーバーとコンテナーのメニューのマージの詳細については、この記事を参照してください。[メニューとリソース (OLE)](../../mfc/menus-and-resources-ole.md)します。

##  <a name="createpreviewframe"></a>  CDocTemplate::CreatePreviewFrame

豊富なプレビューに使用される子フレームを作成します。

```
CFrameWnd* CreatePreviewFrame(
    CWnd* pParentWnd,
    CDocument* pDoc);
```

### <a name="parameters"></a>パラメーター

*pParentWnd*<br/>
(通常は、シェルによって提供されます)、親ウィンドウへのポインター。

*pDoc*<br/>
コンテンツを持つがプレビューされます、ドキュメント オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

有効なポインターを`CFrameWnd`オブジェクト、または作成が失敗した場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="setpreviewinfo"></a>  CDocTemplate::SetPreviewInfo

プロセスのプレビュー ハンドラーの出力を設定します。

```
void SetPreviewInfo(
    UINT nIDPreviewFrame,
    CRuntimeClass* pPreviewFrameClass = NULL,
    CRuntimeClass* pPreviewViewClass = NULL);
```

### <a name="parameters"></a>パラメーター

*nIDPreviewFrame*<br/>
プレビュー フレームのリソース ID を指定します。

*pPreviewFrameClass*<br/>
プレビュー フレームのランタイム クラス情報構造体へのポインターを指定します。

*pPreviewViewClass*<br/>
プレビュー ビューのランタイム クラス情報構造体へのポインターを指定します。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CSingleDocTemplate クラス](../../mfc/reference/csingledoctemplate-class.md)<br/>
[CMultiDocTemplate クラス](../../mfc/reference/cmultidoctemplate-class.md)<br/>
[CDocument クラス](../../mfc/reference/cdocument-class.md)<br/>
[CView クラス](../../mfc/reference/cview-class.md)<br/>
[CScrollView クラス](../../mfc/reference/cscrollview-class.md)<br/>
[CEditView クラス](../../mfc/reference/ceditview-class.md)<br/>
[CFormView クラス](../../mfc/reference/cformview-class.md)<br/>
[CFrameWnd クラス](../../mfc/reference/cframewnd-class.md)<br/>
[CMDIChildWnd クラス](../../mfc/reference/cmdichildwnd-class.md)
