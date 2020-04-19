---
title: COleServerItem クラス
ms.date: 11/04/2016
f1_keywords:
- COleServerItem
- AFXOLE/COleServerItem
- AFXOLE/COleServerItem::COleServerItem
- AFXOLE/COleServerItem::AddOtherClipboardData
- AFXOLE/COleServerItem::CopyToClipboard
- AFXOLE/COleServerItem::DoDragDrop
- AFXOLE/COleServerItem::GetClipboardData
- AFXOLE/COleServerItem::GetDocument
- AFXOLE/COleServerItem::GetEmbedSourceData
- AFXOLE/COleServerItem::GetItemName
- AFXOLE/COleServerItem::GetLinkSourceData
- AFXOLE/COleServerItem::GetObjectDescriptorData
- AFXOLE/COleServerItem::IsConnected
- AFXOLE/COleServerItem::IsLinkedItem
- AFXOLE/COleServerItem::NotifyChanged
- AFXOLE/COleServerItem::OnDoVerb
- AFXOLE/COleServerItem::OnDraw
- AFXOLE/COleServerItem::OnDrawEx
- AFXOLE/COleServerItem::OnGetClipboardData
- AFXOLE/COleServerItem::OnGetExtent
- AFXOLE/COleServerItem::OnInitFromData
- AFXOLE/COleServerItem::OnQueryUpdateItems
- AFXOLE/COleServerItem::OnRenderData
- AFXOLE/COleServerItem::OnRenderFileData
- AFXOLE/COleServerItem::OnRenderGlobalData
- AFXOLE/COleServerItem::OnSetColorScheme
- AFXOLE/COleServerItem::OnSetData
- AFXOLE/COleServerItem::OnSetExtent
- AFXOLE/COleServerItem::OnUpdate
- AFXOLE/COleServerItem::OnUpdateItems
- AFXOLE/COleServerItem::SetItemName
- AFXOLE/COleServerItem::GetDataSource
- AFXOLE/COleServerItem::OnHide
- AFXOLE/COleServerItem::OnOpen
- AFXOLE/COleServerItem::OnShow
- AFXOLE/COleServerItem::m_sizeExtent
helpviewer_keywords:
- COleServerItem [MFC], COleServerItem
- COleServerItem [MFC], AddOtherClipboardData
- COleServerItem [MFC], CopyToClipboard
- COleServerItem [MFC], DoDragDrop
- COleServerItem [MFC], GetClipboardData
- COleServerItem [MFC], GetDocument
- COleServerItem [MFC], GetEmbedSourceData
- COleServerItem [MFC], GetItemName
- COleServerItem [MFC], GetLinkSourceData
- COleServerItem [MFC], GetObjectDescriptorData
- COleServerItem [MFC], IsConnected
- COleServerItem [MFC], IsLinkedItem
- COleServerItem [MFC], NotifyChanged
- COleServerItem [MFC], OnDoVerb
- COleServerItem [MFC], OnDraw
- COleServerItem [MFC], OnDrawEx
- COleServerItem [MFC], OnGetClipboardData
- COleServerItem [MFC], OnGetExtent
- COleServerItem [MFC], OnInitFromData
- COleServerItem [MFC], OnQueryUpdateItems
- COleServerItem [MFC], OnRenderData
- COleServerItem [MFC], OnRenderFileData
- COleServerItem [MFC], OnRenderGlobalData
- COleServerItem [MFC], OnSetColorScheme
- COleServerItem [MFC], OnSetData
- COleServerItem [MFC], OnSetExtent
- COleServerItem [MFC], OnUpdate
- COleServerItem [MFC], OnUpdateItems
- COleServerItem [MFC], SetItemName
- COleServerItem [MFC], GetDataSource
- COleServerItem [MFC], OnHide
- COleServerItem [MFC], OnOpen
- COleServerItem [MFC], OnShow
- COleServerItem [MFC], m_sizeExtent
ms.assetid: 80256df6-3888-4256-944b-787d4b2e6b0d
ms.openlocfilehash: dcae304e8571ecb5743002638ea23f13c3e21517
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741347"
---
# <a name="coleserveritem-class"></a>COleServerItem クラス

OLE アイテムへのサーバー インターフェイスが用意されています。

## <a name="syntax"></a>構文

```
class COleServerItem : public CDocItem
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[COleServerItem:: COleServerItem](#coleserveritem)|`COleServerItem` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleServerItem:: AddOtherClipboardData](#addotherclipboarddata)|`COleDataSource`オブジェクトにプレゼンテーション形式と変換形式を配置します。|
|[COleServerItem:: CopyToClipboard](#copytoclipboard)|項目をクリップボードにコピーします。|
|[COleServerItem::D oDragDrop](#dodragdrop)|ドラッグアンドドロップ操作を実行します。|
|[COleServerItem:: GetClipboardData](#getclipboarddata)|データ転送 (ドラッグアンドドロップまたはクリップボード) で使用するデータソースを取得します。|
|[COleServerItem:: GetDocument](#getdocument)|アイテムを含むサーバードキュメントを返します。|
|[COleServerItem:: GetEmbedSourceData](#getembedsourcedata)|OLE 項目の CF_EMBEDSOURCE データを取得します。|
|[COleServerItem::GetItemName](#getitemname)|項目の名前を返します。 リンクアイテムにのみ使用されます。|
|[COleServerItem:: GetLinkSourceData](#getlinksourcedata)|OLE 項目の CF_LINKSOURCE データを取得します。|
|[COleServerItem:: Getobject記述子データ](#getobjectdescriptordata)|OLE 項目の CF_OBJECTDESCRIPTOR データを取得します。|
|[COleServerItem::IsConnected](#isconnected)|項目が現在アクティブなコンテナーにアタッチされているかどうかを示します。|
|[COleServerItem::IsLinkedItem](#islinkeditem)|項目がリンクされた OLE 項目を表すかどうかを示します。|
|[COleServerItem::NotifyChanged](#notifychanged)|自動リンク更新を使用してすべてのコンテナーを更新します。|
|[COleServerItem::OnDoVerb](#ondoverb)|動詞を実行するために呼び出されます。|
|[COleServerItem:: OnDraw](#ondraw)|コンテナーが項目の描画を要求したときに呼び出されます。実装が必要です。|
|[COleServerItem::OnDrawEx](#ondrawex)|特殊な項目の描画に対して呼び出されます。|
|[COleServerItem::OnGetClipboardData](#ongetclipboarddata)|クリップボードにコピーされるデータを取得するために、フレームワークによって呼び出されます。|
|[COleServerItem::OnGetExtent](#ongetextent)|OLE 項目のサイズを取得するためにフレームワークによって呼び出されます。|
|[COleServerItem:: OnInitFromData](#oninitfromdata)|指定されたデータ転送オブジェクトの内容を使用して OLE 項目を初期化するために、フレームワークによって呼び出されます。|
|[COleServerItem::OnQueryUpdateItems](#onqueryupdateitems)|リンクされた項目の更新が必要かどうかを判断するために呼び出されます。|
|[COleServerItem:: OnRenderData](#onrenderdata)|遅延表示の一部としてデータを取得します。|
|[COleServerItem::OnRenderFileData](#onrenderfiledata)|遅延レンダリングの一部`CFile`として、オブジェクトにデータを取得します。|
|[COleServerItem::OnRenderGlobalData](#onrenderglobaldata)|遅延レンダリングの一部として、データを HGLOBAL に取得します。|
|[COleServerItem::OnSetColorScheme](#onsetcolorscheme)|項目の配色を設定するために呼び出されます。|
|[COleServerItem:: OnSetData](#onsetdata)|項目のデータを設定するために呼び出されます。|
|[COleServerItem:: OnSetExtent](#onsetextent)|OLE 項目のサイズを設定するためにフレームワークによって呼び出されます。|
|[COleServerItem:: OnUpdate](#onupdate)|項目が属するドキュメントの一部が変更されたときに呼び出されます。|
|[COleServerItem:: OnUpdateItems](#onupdateitems)|サーバードキュメント内のすべての項目のプレゼンテーションキャッシュを更新するために呼び出されます。|
|[COleServerItem:: SetItemName](#setitemname)|項目の名前を設定します。 リンクアイテムにのみ使用されます。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[COleServerItem:: GetDataSource](#getdatasource)|変換形式を格納するために使用するオブジェクトを取得します。|
|[COleServerItem::OnHide](#onhide)|OLE 項目を非表示にするためにフレームワークによって呼び出されます。|
|[COleServerItem:: OnOpen](#onopen)|独自のトップレベルウィンドウで OLE 項目を表示するために、フレームワークによって呼び出されます。|
|[COleServerItem:: OnShow](#onshow)|コンテナーが項目を表示するように要求したときに呼び出されます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[COleServerItem:: m_sizeExtent](#m_sizeextent)|OLE 項目がどの程度表示されるかをサーバーに通知します。|

## <a name="remarks"></a>Remarks

リンクアイテムは、サーバードキュメントの一部またはすべてを表すことができます。 埋め込みアイテムは、常にサーバードキュメント全体を表します。

クラス`COleServerItem`は、通常はコンテナーアプリケーションからの要求に応答して、OLE システムダイナミックリンクライブラリ (dll) によって呼び出される、オーバーライド可能な複数のメンバー関数を定義します。 これらのメンバー関数を使用すると、コンテナーアプリケーションはさまざまな方法で項目を間接的に操作できます。たとえば、表示、動詞の実行、さまざまな形式でのデータの取得などです。

を使用`COleServerItem`するには、クラスを派生させ、 [OnDraw](#ondraw)および[Serialize](../../mfc/reference/cobject-class.md#serialize)メンバー関数を実装します。 関数`OnDraw`は、項目のメタファイル表現を提供し、コンテナーアプリケーションが複合ドキュメントを開いたときに表示されるようにします。 `Serialize` の`CObject`関数は、項目のネイティブ表現を提供し、サーバーアプリケーションとコンテナーアプリケーションの間で埋め込み項目を転送できるようにします。 [OnGetExtent](#ongetextent)は、項目のサイズをコンテナーに提供し、コンテナーが項目のサイズを変更できるようにします。

サーバーと関連トピックの詳細については、「 [サーバー:サーバー](../../mfc/servers-implementing-a-server.md)の実装と "コンテナー/サーバーアプリケーションの作成" に関する記事[の「コンテナー:高度な](../../mfc/containers-advanced-features.md)機能。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

`COleServerItem`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole

##  <a name="addotherclipboarddata"></a>COleServerItem:: AddOtherClipboardData

この関数を呼び出して、指定した`COleDataSource`オブジェクトの OLE 項目のプレゼンテーション形式と変換形式を配置します。

```
void AddOtherClipboardData(COleDataSource* pDataSource);
```

### <a name="parameters"></a>パラメーター

*pDataSource*<br/>
データを配置`COleDataSource`するオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

アイテムのプレゼンテーション形式 (メタファイル画像) を提供するには、 [OnDraw](#ondraw)メンバー関数を実装している必要があります。 他の変換形式をサポートするには、 [Getdatasource](#getdatasource)から返された[COleDataSource](../../mfc/reference/coledatasource-class.md)オブジェクトを使用して登録し、サポートする形式のデータを提供するように[OnRenderData](#onrenderdata)メンバー関数をオーバーライドします。

##  <a name="coleserveritem"></a>COleServerItem:: COleServerItem

オブジェクトを`COleServerItem`構築し、それをサーバードキュメントのドキュメント項目のコレクションに追加します。

```
COleServerItem(
    COleServerDoc* pServerDoc,
    BOOL bAutoDelete);
```

### <a name="parameters"></a>パラメーター

*pServerDoc*<br/>
新しい項目を格納するドキュメントへのポインター。

*bAutoDelete*<br/>
オブジェクトへのリンクが解放されたときにオブジェクトを削除できるかどうかを示すフラグです。 オブジェクトがドキュメントのデータの`COleServerItem`重要な部分であり、削除する必要がある場合は、この値を FALSE に設定します。 オブジェクトが、フレームワークによって削除できるドキュメントのデータ内の範囲を識別するために使用される二次的な構造体である場合は、これを TRUE に設定します。

##  <a name="copytoclipboard"></a>  COleServerItem::CopyToClipboard

OLE 項目をクリップボードにコピーするには、この関数を呼び出します。

```
void CopyToClipboard(BOOL bIncludeLink = FALSE);
```

### <a name="parameters"></a>パラメーター

*bIncludeLink*<br/>
リンクデータをクリップボードにコピーする必要がある場合は、TRUE に設定します。 サーバーアプリケーションがリンクをサポートしていない場合は、FALSE に設定します。

### <a name="remarks"></a>Remarks

関数は、 [OnGetClipboardData](#ongetclipboarddata)メンバー関数を使用して、サポートされている形式で OLE 項目のデータを含む[COleDataSource](../../mfc/reference/coledatasource-class.md)オブジェクトを作成します。 次に、関数は`COleDataSource` 、 [COleDataSource:: setclipboard](../../mfc/reference/coledatasource-class.md#setclipboard)関数を使用してクリップボードにオブジェクトを配置します。 オブジェクト`COleDataSource`には、アイテムのネイティブデータとその表現が CF_METAFILEPICT 形式で含まれています。また、サポートするように選択した変換形式のデータも含まれています。 このメンバー関数が機能するには、[シリアル化](../../mfc/reference/cobject-class.md#serialize)と[OnDraw](#ondraw)を実装している必要があります。

##  <a name="dodragdrop"></a>COleServerItem::D oDragDrop

`DoDragDrop`メンバー関数を呼び出して、ドラッグアンドドロップ操作を実行します。

```
DROPEFFECT DoDragDrop(
    LPCRECT lpRectItem,
    CPoint ptOffset,
    BOOL bIncludeLink = FALSE,
    DWORD dwEffects = DROPEFFECT_COPY | DROPEFFECT_MOVE,
    LPCRECT lpRectStartDrag = NULL);
```

### <a name="parameters"></a>パラメーター

*lpRectItem*<br/>
クライアント領域を基準とした、画面上の項目の四角形 (ピクセル単位)。

*ptOffset*<br/>
ドラッグ時のマウス位置の*lpItemRect*からのオフセット。

*bIncludeLink*<br/>
リンクデータをクリップボードにコピーする必要がある場合は、TRUE に設定します。 アプリケーションがリンクをサポートしていない場合は、FALSE に設定します。

*dwEffects*<br/>
ドラッグ元がドラッグ操作で許可する効果 (コピー、移動、およびリンクの組み合わせ) を決定します。

*lpRectStartDrag*<br/>
ドラッグが実際に開始される場所を定義する四角形へのポインター。 詳細については、「解説」を参照してください。

### <a name="return-value"></a>戻り値

DROPEFFECT 列挙子の値。 DROPEFFECT_MOVE の場合は、元のデータを削除する必要があります。

### <a name="remarks"></a>Remarks

ドラッグアンドドロップ操作はすぐには開始されません。 マウスカーソルが、 *lpRectStartDrag*で指定された四角形から離れるか、指定されたミリ秒数が経過するまで待機します。 *LpRectStartDrag*が NULL の場合は、マウスカーソルが1ピクセルを移動するとドラッグが開始されるように、既定の四角形が使用されます。

遅延時間は、レジストリキーの設定によって指定されます。 遅延時間を変更するには、 [cwinapp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)または[Cwinapp:: writeprofilestring](../../mfc/reference/cwinapp-class.md#writeprofileint)を呼び出します。 遅延時間を指定しない場合は、既定値の200ミリ秒が使用されます。 ドラッグの遅延時間は次のように格納されます。

- Windows NT のドラッグ遅延時間は HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay. に格納されます

- Windows 3.x のドラッグ遅延時間は、WIN に格納されます。INI ファイル ([Windows}] セクションの下)。

- Windows 95/98 のドラッグ遅延時間は、WIN のキャッシュされたバージョンに格納されます.INI.

ドラッグ遅延情報をレジストリまたはに格納する方法の詳細については、「」を参照してください。INI ファイルの「Windows SDK の[Writeprofilestring](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 」を参照してください。

##  <a name="getclipboarddata"></a>COleServerItem:: GetClipboardData

[Copytoclipboard](#copytoclipboard)を呼び出した場合に、クリップボードにコピーされるすべてのデータを、指定された[COleDataSource](../../mfc/reference/coledatasource-class.md)オブジェクトに格納するには、この関数を呼び出します ( [system.windows.dragdrop.dodragdrop](#dodragdrop)を呼び出した場合も同じデータが転送されます)。

```
void GetClipboardData(
    COleDataSource* pDataSource,
    BOOL bIncludeLink = FALSE,
    LPPOINT lpOffset = NULL,
    LPSIZE lpSize = NULL);
```

### <a name="parameters"></a>パラメーター

*pDataSource*<br/>
サポートされ`COleDataSource`ているすべての形式で OLE 項目のデータを受け取るオブジェクトへのポインター。

*bIncludeLink*<br/>
リンクデータをクリップボードにコピーする必要がある場合は TRUE。 サーバーアプリケーションがリンクをサポートしていない場合は FALSE。

*lpOffset*<br/>
オブジェクトの原点からのマウスカーソルのオフセット (ピクセル単位)。

*lpSize*<br/>
オブジェクトのサイズ (ピクセル単位)。

### <a name="remarks"></a>Remarks

この関数は、 [Getembedsourcedata](#getembedsourcedata)メンバー関数を呼び出して OLE アイテムのネイティブデータを取得し、 [AddOtherClipboardData](#addotherclipboarddata)メンバー関数を呼び出して、プレゼンテーション形式とサポートされている変換形式を取得します。 *Bincludelink*が TRUE の場合、この関数は、項目のリンクデータを取得するために[GetLinkSourceData](#getlinksourcedata)も呼び出します。

によって`CopyToClipboard`指定された形式の前また`COleDataSource`は後に、オブジェクトに書式を配置する場合は、この関数をオーバーライドします。

##  <a name="getdatasource"></a>COleServerItem:: GetDataSource

サーバーアプリケーションがサポートする変換形式を格納するために使用される[COleDataSource](../../mfc/reference/coledatasource-class.md)オブジェクトを取得するには、この関数を呼び出します。

```
COleDataSource* GetDataSource();
```

### <a name="return-value"></a>戻り値

変換形式を格納`COleDataSource`するために使用するオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

サーバーアプリケーションでデータ転送操作中にさまざまな形式のデータを提供する場合は、この関数によって`COleDataSource`返されるオブジェクトにそれらの形式を登録します。 たとえば、クリップボードまたはドラッグアンドドロップ操作のために OLE 項目の CF_TEXT 表現を指定する場合は、この関数が返す`COleDataSource`オブジェクトを使用して形式を登録し、 `OnRenderXxxData`メンバー関数をにオーバーライドします。データを指定します。

##  <a name="getdocument"></a>COleServerItem:: GetDocument

項目が含まれているドキュメントへのポインターを取得するには、この関数を呼び出します。

```
COleServerDoc* GetDocument() const;
```

### <a name="return-value"></a>戻り値

項目を格納しているドキュメントへのポインター。項目がドキュメントの一部でない場合は NULL。

### <a name="remarks"></a>Remarks

これにより、 `COleServerItem`引数としてコンストラクターに渡されたサーバードキュメントにアクセスできるようになります。

##  <a name="getembedsourcedata"></a>  COleServerItem::GetEmbedSourceData

OLE 項目の CF_EMBEDSOURCE データを取得するには、この関数を呼び出します。

```
void GetEmbedSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>パラメーター

*lpStgMedium*<br/>
OLE 項目の CF_EMBEDSOURCE データを受け取る[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体へのポインター。

### <a name="remarks"></a>Remarks

この形式は、項目のネイティブデータを含みます。 この関数が正常に`Serialize`機能するためには、メンバー関数が実装されている必要があります。

その結果は、 [COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata)を使用してデータソースに追加できます。 この関数は、 [COleServerItem:: OnGetClipboardData](#ongetclipboarddata)によって自動的に呼び出されます。

詳細については、Windows SDK の「 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 」を参照してください。

##  <a name="getitemname"></a>  COleServerItem::GetItemName

項目の名前を取得するには、この関数を呼び出します。

```
const CString& GetItemName() const;
```

### <a name="return-value"></a>戻り値

項目の名前。

### <a name="remarks"></a>Remarks

通常は、リンクされたアイテムに対してのみこの関数を呼び出します。

##  <a name="getlinksourcedata"></a>  COleServerItem::GetLinkSourceData

OLE 項目の CF_LINKSOURCE データを取得するには、この関数を呼び出します。

```
BOOL GetLinkSourceData(LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>パラメーター

*lpStgMedium*<br/>
OLE 項目の CF_LINKSOURCE データを受け取る[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

この形式には、OLE 項目の種類を記述する CLSID と、OLE 項目を含むドキュメントを検索するために必要な情報が含まれます。

結果は、 [COleDataSource:: CacheData](../../mfc/reference/coledatasource-class.md#cachedata)を使用してデータソースに追加できます。 この関数は、 [OnGetClipboardData](#ongetclipboarddata)によって自動的に呼び出されます。

詳細については、Windows SDK の「 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 」を参照してください。

##  <a name="getobjectdescriptordata"></a>COleServerItem:: Getobject記述子データ

OLE 項目の CF_OBJECTDESCRIPTOR データを取得するには、この関数を呼び出します。

```
void GetObjectDescriptorData(
    LPPOINT lpOffset,
    LPSIZE lpSize,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>パラメーター

*lpOffset*<br/>
OLE 項目の左上隅からのマウスクリックのオフセット。 NULL を指定できます。

*lpSize*<br/>
OLE 項目のサイズ。 NULL を指定できます。

*lpStgMedium*<br/>
OLE 項目の CF_OBJECTDESCRIPTOR データを受け取る[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体へのポインター。

### <a name="remarks"></a>Remarks

情報は、 *lpStgMedium*によっ`STGMEDIUM`て示される構造体にコピーされます。 この形式には、[特殊な貼り付け] ダイアログに必要な情報が含まれています。

詳細については、Windows SDK の「 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) 」を参照してください。

##  <a name="isconnected"></a>  COleServerItem::IsConnected

OLE 項目が接続されているかどうかを確認するには、この関数を呼び出します。

```
BOOL IsConnected() const;
```

### <a name="return-value"></a>戻り値

項目が接続されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

1つ以上のコンテナーが項目を参照している場合、OLE 項目は接続されていると見なされます。 参照カウントが0より大きいか、または埋め込みアイテムである場合、アイテムは接続されます。

##  <a name="islinkeditem"></a>  COleServerItem::IsLinkedItem

OLE 項目がリンクされた項目であるかどうかを確認するには、この関数を呼び出します。

```
BOOL IsLinkedItem() const;
```

### <a name="return-value"></a>戻り値

項目がリンクされた項目の場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

項目が有効で、ドキュメントの埋め込み項目の一覧に返されない場合は、項目がリンクされます。 リンクアイテムは、コンテナーに接続されている場合もあれば、接続されていない場合もあります。

リンクされた項目と埋め込み項目の両方に同じクラスを使用するのが一般的です。 `IsLinkedItem`リンクされた項目の動作を埋め込み項目とは異なる方法で行うことができます。ただし、コードは多くの場合に共通です。

##  <a name="m_sizeextent"></a>COleServerItem:: m_sizeExtent

このメンバーは、コンテナードキュメントに表示されるオブジェクトの量をサーバーに通知します。

```
CSize m_sizeExtent;
```

### <a name="remarks"></a>Remarks

[OnSetExtent](#onsetextent)の既定の実装では、このメンバーが設定されます。

##  <a name="notifychanged"></a>  COleServerItem::NotifyChanged

リンク項目が変更された後に、この関数を呼び出します。

```
void NotifyChanged(DVASPECT nDrawAspect = DVASPECT_CONTENT);
```

### <a name="parameters"></a>パラメーター

*nDrawAspect*<br/>
OLE 項目のどの側面が変更されたかを示す DVASPECT 列挙の値。 このパラメーターには、次のいずれかの値を指定できます。

- DVASPECT_CONTENT Item は、コンテナー内に埋め込みオブジェクトとして表示できるように表現されます。

- なりますが項目は、参照ツールで表示できるように "サムネイル" 表現で表示されます。

- DVASPECT_ICON Item はアイコンで表されます。

- DVASPECT_DOCPRINT Item は、[ファイル] メニューの [印刷] コマンドを使用して印刷されたかのように表されます。

### <a name="remarks"></a>Remarks

コンテナー項目が自動リンクを使用してドキュメントにリンクされている場合、その項目は変更内容を反映して更新されます。 Microsoft Foundation Class ライブラリを使用して記述されたコンテナーアプリケーションでは、 [COleClientItem:: OnChange](../../mfc/reference/coleclientitem-class.md#onchange)が応答として呼び出されます。

##  <a name="ondoverb"></a>  COleServerItem::OnDoVerb

指定された動詞を実行するためにフレームワークによって呼び出されます。

```
virtual void OnDoVerb(LONG iVerb);
```

### <a name="parameters"></a>パラメーター

*iVerb*<br/>
実行する動詞を指定します。 次のいずれかを指定できます。

|[値]|説明|シンボル|
|-----------|-------------|------------|
|0|主動詞|OLEIVERB_PRIMARY|
|1|2番目の動詞|(なし)|
|- 1|編集する項目の表示|OLEIVERB_SHOW|
|- 2|別のウィンドウで項目を編集する|OLEIVERB_OPEN|
|- 3|項目の非表示|OLEIVERB_HIDE|

-1 の値は、通常、別の動詞のエイリアスです。 開いている編集がサポートされていない場合、-2 は-1 と同じ効果があります。 その他の値については、Windows SDK の「 [IOleObject::D oVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 」を参照してください。

### <a name="remarks"></a>Remarks

コンテナーアプリケーションが Microsoft Foundation Class ライブラリで記述されている場合、対応する`COleClientItem`オブジェクトの[COleClientItem:: Activate](../../mfc/reference/coleclientitem-class.md#activate)メンバー関数が呼び出されると、この関数が呼び出されます。 プライマリ動詞または OLEIVERB_SHOW が指定されている場合、既定の実装は[Onshow](#onshow)メンバー関数を呼び出し、2次動詞または OLEIVERB_OPEN が指定されている場合は[OnOpen](#onopen) 、OLEIVERB_HIDE が指定されている場合は[onshow](#onhide)を呼び出します。 *Iverb*が上`OnShow`に示した動詞の1つではない場合、既定の実装はを呼び出します。

プライマリ動詞が項目を表示しない場合は、この関数をオーバーライドします。 たとえば、項目がサウンド記録であり、その主動詞が再生されている場合、項目を再生するためにサーバーアプリケーションを表示する必要はありません。

詳細については、Windows SDK の「 [IOleObject::D oVerb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 」を参照してください。

##  <a name="ondraw"></a>  COleServerItem::OnDraw

OLE 項目をメタファイルにレンダリングするために、フレームワークによって呼び出されます。

```
virtual BOOL OnDraw(
    CDC* pDC,
    CSize& rSize) = 0;
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
項目を描画する[CDC](../../mfc/reference/cdc-class.md)オブジェクトへのポインター。 属性関数を呼び出すことができるように、表示コンテキストは属性の表示コンテキストに自動的に接続されます。

*rSize*<br/>
メタファイルの描画に使用するサイズ (HIMETRIC 単位)。

### <a name="return-value"></a>戻り値

項目が正常に描画された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

OLE 項目のメタファイル表現は、コンテナーアプリケーションで項目を表示するために使用されます。 コンテナーアプリケーションが Microsoft Foundation Class ライブラリで書き込まれた場合、メタファイルは、対応する[COleClientItem](../../mfc/reference/coleclientitem-class.md)オブジェクトの[Draw](../../mfc/reference/coleclientitem-class.md#draw)メンバー関数によって使用されます。 既定の実装はありません。 指定したデバイスコンテキストに項目を描画するには、この関数をオーバーライドする必要があります。

##  <a name="ondrawex"></a>COleServerItem:: OnDrawEx

すべての描画のためにフレームワークによって呼び出されます。

```
virtual BOOL OnDrawEx(
    CDC* pDC,
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
項目を描画する[CDC](../../mfc/reference/cdc-class.md)オブジェクトへのポインター。 DC は属性 DC に自動的に接続されるので、属性関数を呼び出すことができます。ただし、これにより、メタファイルのデバイス固有の状態が作成されます。

*nDrawAspect*<br/>
DVASPECT 列挙子の値。 このパラメーターには、次のいずれかの値を指定できます。

- DVASPECT_CONTENT Item は、コンテナー内に埋め込みオブジェクトとして表示できるように表現されます。

- なりますが項目は、参照ツールで表示できるように "サムネイル" 表現で表示されます。

- DVASPECT_ICON Item はアイコンで表されます。

- DVASPECT_DOCPRINT Item は、[ファイル] メニューの [印刷] コマンドを使用して印刷されたかのように表されます。

*rSize*<br/>
HIMETRIC 単位の項目のサイズ。

### <a name="return-value"></a>戻り値

項目が正常に描画された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

Dvaspect が DVASPECT_CONTENT `OnDraw`と等しい場合、既定の実装はを呼び出します。それ以外の場合は、失敗します。

DVASPECT_ICON やなりますがなど、DVASPECT_CONTENT 以外の側面のプレゼンテーションデータを提供するには、この関数をオーバーライドします。

##  <a name="ongetclipboarddata"></a>  COleServerItem::OnGetClipboardData

[Copytoclipboard](#copytoclipboard)メンバー関数の呼び出し`COleDataSource`によってクリップボードに配置されるすべてのデータを格納するオブジェクトを取得するために、フレームワークによって呼び出されます。

```
virtual COleDataSource* OnGetClipboardData(
    BOOL bIncludeLink,
    LPPOINT lpOffset,
    LPSIZE lpSize);
```

### <a name="parameters"></a>パラメーター

*bIncludeLink*<br/>
リンクデータをクリップボードにコピーする必要がある場合は、TRUE に設定します。 サーバーアプリケーションがリンクをサポートしていない場合は、FALSE に設定します。

*lpOffset*<br/>
オブジェクトの原点からのマウスカーソルのオフセット (ピクセル単位)。

*lpSize*<br/>
オブジェクトのサイズ (ピクセル単位)。

### <a name="return-value"></a>戻り値

クリップボードデータを格納している[COleDataSource](../../mfc/reference/coledatasource-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

この関数の既定の実装では、 [GetClipboardData](#getclipboarddata)を呼び出します。

##  <a name="ongetextent"></a>  COleServerItem::OnGetExtent

OLE 項目のサイズ (HIMETRIC 単位) を取得するためにフレームワークによって呼び出されます。

```
virtual BOOL OnGetExtent(
    DVASPECT nDrawAspect,
    CSize& rSize);
```

### <a name="parameters"></a>パラメーター

*nDrawAspect*<br/>
範囲を取得する OLE 項目の側面を指定します。 このパラメーターには、次のいずれかの値を指定できます。

- DVASPECT_CONTENT Item は、コンテナー内に埋め込みオブジェクトとして表示できるように表現されます。

- なりますが項目は、参照ツールで表示できるように "サムネイル" 表現で表示されます。

- DVASPECT_ICON Item はアイコンで表されます。

- DVASPECT_DOCPRINT Item は、[ファイル] メニューの [印刷] コマンドを使用して印刷されたかのように表されます。

*rSize*<br/>
OLE 項目の`CSize`サイズを受け取るオブジェクトへの参照。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

コンテナーアプリケーションが Microsoft Foundation Class ライブラリで記述されている場合、対応する`COleClientItem`オブジェクトの[getextent](../../mfc/reference/coleclientitem-class.md#getextent)メンバー関数が呼び出されると、この関数が呼び出されます。 既定の実装では、何も行われません。 自分で実装する必要があります。 OLE 項目のサイズの要求を処理するときに特殊な処理を実行する場合は、この関数をオーバーライドします。

##  <a name="onhide"></a>  COleServerItem::OnHide

OLE 項目を非表示にするためにフレームワークによって呼び出されます。

```
virtual void OnHide();
```

### <a name="remarks"></a>Remarks

既定の呼び出し`COleServerDoc::OnShowDocument( FALSE )`。 また、この関数は、OLE 項目が非表示になっていることをコンテナーに通知します。 OLE 項目を非表示にするときに特別な処理を実行する場合は、この関数をオーバーライドします。

##  <a name="oninitfromdata"></a>  COleServerItem::OnInitFromData

*Pdataobject*の内容を使用して OLE 項目を初期化するために、フレームワークによって呼び出されます。

```
virtual BOOL OnInitFromData(
    COleDataObject* pDataObject,
    BOOL bCreation);
```

### <a name="parameters"></a>パラメーター

*pDataObject*<br/>
OLE 項目を初期化するためのさまざまな形式のデータを格納している OLE データオブジェクトへのポインター。

*bCreation*<br/>
コンテナーアプリケーションによって新しく作成された OLE 項目を初期化するために関数が呼び出される場合は TRUE。 関数が既に存在する OLE 項目の内容を置き換えるために呼び出される場合は FALSE。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

*Bcreation*が TRUE の場合、コンテナーが現在の選択内容に基づいて Insert New オブジェクトを実装すると、この関数が呼び出されます。 選択したデータは、新しい OLE 項目を作成するときに使用されます。 たとえば、スプレッドシートプログラムでセルの範囲を選択し、[新しいオブジェクトの挿入] を使用して、選択した範囲の値に基づいてグラフを作成する場合などです。 既定の実装では、何も行われません。 *Pdataobject*によって提供される形式から許容される形式を選択し、提供されたデータに基づいて OLE 項目を初期化するには、この関数をオーバーライドします。 これは高度なオーバーライド可能です。

詳細については、Windows SDK の「 [IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) 」を参照してください。

##  <a name="onopen"></a>  COleServerItem::OnOpen

OLE 項目を配置ではなく、サーバーアプリケーションの別のインスタンスに表示するために、フレームワークによって呼び出されます。

```
virtual void OnOpen();
```

### <a name="remarks"></a>Remarks

既定の実装は、OLE 項目を含むドキュメントを表示する最初のフレームウィンドウをアクティブにします。アプリケーションがミニサーバーの場合は、既定の実装によってメインウィンドウが表示されます。 また、この関数は、OLE 項目が開かれたことをコンテナーに通知します。

OLE 項目を開くときに特別な処理を実行する場合は、この関数をオーバーライドします。 これは、リンクアイテムを開いたときに選択項目をリンクに設定する場合に特に一般的です。

詳細については、Windows SDK の「 [IOleClientSite:: OnShowWindow](/windows/win32/api/oleidl/nf-oleidl-ioleclientsite-onshowwindow) 」を参照してください。

##  <a name="onqueryupdateitems"></a>  COleServerItem::OnQueryUpdateItems

現在のサーバードキュメント内のリンクされた項目が古いかどうかを判断するために、フレームワークによって呼び出されます。

```
virtual BOOL OnQueryUpdateItems();
```

### <a name="return-value"></a>戻り値

ドキュメントに更新が必要な項目が含まれている場合は0以外の。すべての項目が最新の場合は0。

### <a name="remarks"></a>Remarks

ソースドキュメントが変更されていても、ドキュメントの変更を反映するようにリンクアイテムが更新されていない場合、アイテムは最新ではありません。

##  <a name="onrenderdata"></a>COleServerItem:: OnRenderData

指定された形式でデータを取得するためにフレームワークによって呼び出されます。

```
virtual BOOL OnRenderData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium);
```

### <a name="parameters"></a>パラメーター

*lpFormatEtc*<br/>
情報が要求される形式を指定する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。

*lpStgMedium*<br/>
データが返される[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体を指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

指定された形式は、遅延レンダリング`COleDataSource`のために[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)または[DelayRenderFileData](../../mfc/reference/coledatasource-class.md#delayrenderfiledata)メンバー関数を使用してオブジェクトに以前に配置されています。 指定されたストレージメディアがファイルまたはメモリのいずれかである場合、この関数の既定の実装は、 [OnRenderFileData](#onrenderfiledata)または[OnRenderGlobalData](#onrenderglobaldata)をそれぞれ呼び出します。 これらの形式のいずれも指定しない場合、既定の実装は0を返し、何も行いません。

*LpStgMedium*-> *tymed*が TYMED_NULL の場合、STGMEDIUM は*lpFormatEtc-> tymed*によって指定されたとおりに割り当てられ、入力される必要があります。 TYMED_NULL がない場合は、データを格納する STGMEDIUM を設定する必要があります。

これは高度なオーバーライド可能です。 要求された形式とメディアにデータを提供するには、この関数をオーバーライドします。 データによっては、この関数の他のバージョンの1つをオーバーライドすることが必要になる場合があります。 データが小さく、サイズが固定されている`OnRenderGlobalData`場合は、をオーバーライドします。 データがファイル内にある場合、またはサイズが可変の場合`OnRenderFileData`は、をオーバーライドします。

詳細については、Windows SDK の「 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)、 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)、 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)、および[tymed](/windows/win32/api/objidl/ne-objidl-tymed) 」を参照してください。

##  <a name="onrenderfiledata"></a>  COleServerItem::OnRenderFileData

ストレージメディアがファイルの場合に、指定された形式でデータを取得するためにフレームワークによって呼び出されます。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>パラメーター

*lpFormatEtc*<br/>
情報が要求される形式を指定する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。

*pFile*<br/>
データを表示`CFile`するオブジェクトを指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

指定された形式は、遅延レンダリング`COleDataSource`のために[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)メンバー関数を使用してオブジェクトに既に配置されています。 この関数の既定の実装では、単に FALSE が返されます。

これは高度なオーバーライド可能です。 要求された形式とメディアにデータを提供するには、この関数をオーバーライドします。 データによっては、この関数の他のバージョンの1つをオーバーライドすることが必要になる場合があります。 複数の記憶域メディアを処理する場合は、 [OnRenderData](#onrenderdata)を上書きします。 データがファイル内にある場合、またはサイズが可変の場合は、 [OnRenderFileData](#onrenderfiledata)をオーバーライドします。

詳細については、Windows SDK の「 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 」と「 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 」を参照してください。

##  <a name="onrenderglobaldata"></a>  COleServerItem::OnRenderGlobalData

指定されたストレージメディアがグローバルメモリである場合に、指定された形式でデータを取得するためにフレームワークによって呼び出されます。

```
virtual BOOL OnRenderGlobalData(
    LPFORMATETC lpFormatEtc,
    HGLOBAL* phGlobal);
```

### <a name="parameters"></a>パラメーター

*lpFormatEtc*<br/>
情報が要求される形式を指定する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。

*phGlobal*<br/>
データが返されるグローバルメモリへのハンドルを指します。 メモリが割り当てられていない場合は、このパラメーターを NULL にすることができます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

指定された形式は、遅延レンダリング`COleDataSource`のために[DelayRenderData](../../mfc/reference/coledatasource-class.md#delayrenderdata)メンバー関数を使用してオブジェクトに既に配置されています。 この関数の既定の実装では、単に FALSE が返されます。

*Phglobal*が NULL の場合、新しい HGLOBAL が割り当てられ、 *phglobal*で返される必要があります。 それ以外の場合は、 *Phglobal*によって指定された HGLOBAL にデータを格納する必要があります。 HGLOBAL に配置されるデータの量は、メモリブロックの現在のサイズを超えることはできません。 また、ブロックをより大きなサイズに再割り当てすることはできません。

これは高度なオーバーライド可能です。 要求された形式とメディアにデータを提供するには、この関数をオーバーライドします。 データによっては、この関数の他のバージョンの1つをオーバーライドすることが必要になる場合があります。 複数の記憶域メディアを処理する場合は、 [OnRenderData](#onrenderdata)を上書きします。 データがファイル内にある場合、またはサイズが可変の場合は、 [OnRenderFileData](#onrenderfiledata)をオーバーライドします。

詳細については、Windows SDK の「 [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 」と「 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) 」を参照してください。

##  <a name="onsetcolorscheme"></a>  COleServerItem::OnSetColorScheme

OLE 項目の編集時に使用するカラーパレットを指定するために、フレームワークによって呼び出されます。

```
virtual BOOL OnSetColorScheme(const LOGPALETTE* lpLogPalette);
```

### <a name="parameters"></a>パラメーター

*lpLogPalette*<br/>
Windows [Logpalette](/windows/win32/api/wingdi/ns-wingdi-logpalette)構造体へのポインター。

### <a name="return-value"></a>戻り値

カラーパレットが使用されている場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

Microsoft Foundation Class ライブラリを使用してコンテナーアプリケーションを作成した場合、対応する`COleClientItem`オブジェクトの[IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme)関数が呼び出されると、この関数が呼び出されます。 既定の実装では、FALSE が返されます。 推奨されるパレットを使用する場合は、この関数をオーバーライドします。 サーバーアプリケーションは、推奨されるパレットを使用する必要はありません。

詳細については、Windows SDK の「 [IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 」を参照してください。

##  <a name="onsetdata"></a>  COleServerItem::OnSetData

OLE 項目のデータを指定されたデータに置き換えるために、フレームワークによって呼び出されます。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>パラメーター

*lpFormatEtc*<br/>
データの形式を指定する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体へのポインター。

*lpStgMedium*<br/>
データが存在する[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体へのポインター。

*bRelease*<br/>
関数呼び出しの完了後にストレージメディアの所有権を持つユーザーを示します。 呼び出し元は、ストレージメディアの代わりに割り当てられたリソースを解放する担当者を決定します。 呼び出し元は、 *Brelease*を設定することによってこれを行います。 *Brelease*が0以外の場合、サーバー項目は所有権を取得し、使用が終了したときにそのメディアを解放します。 *Brelease*が0の場合、呼び出し元は所有権を保持し、サーバー項目は呼び出しの間だけストレージメディアを使用できます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

サーバー項目は、データが正常に取得されるまで、データの所有権を取得しません。 つまり、0が返された場合、所有権は取得されません。 データソースが所有権を取得すると、 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium)関数を呼び出すことによってストレージメディアが解放されます。

既定の実装では、何も行われません。 OLE 項目のデータを指定したデータに置き換えるには、この関数をオーバーライドします。 これは高度なオーバーライド可能です。

詳細については、Windows SDK の「 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)、 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)、および[ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 」を参照してください。

##  <a name="onsetextent"></a>  COleServerItem::OnSetExtent

フレームワークによって呼び出され、コンテナードキュメント内の使用可能な領域を OLE 項目に通知します。

```
virtual BOOL OnSetExtent(
    DVASPECT nDrawAspect,
    const CSize& size);
```

### <a name="parameters"></a>パラメーター

*nDrawAspect*<br/>
境界が指定されている OLE 項目の側面を指定します。 このパラメーターには、次のいずれかの値を指定できます。

- DVASPECT_CONTENT Item は、コンテナー内に埋め込みオブジェクトとして表示できるように表現されます。

- なりますが項目は、参照ツールで表示できるように "サムネイル" 表現で表示されます。

- DVASPECT_ICON Item はアイコンで表されます。

- DVASPECT_DOCPRINT Item は、[ファイル] メニューの [印刷] コマンドを使用して印刷されたかのように表されます。

*size*<br/>
OLE 項目の新しいサイズを指定する[CSize](../../atl-mfc-shared/reference/csize-class.md)構造体。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

コンテナーアプリケーションが Microsoft Foundation Class ライブラリで記述されている場合、対応する`COleClientItem`オブジェクトの[setextent](../../mfc/reference/coleclientitem-class.md#setextent)メンバー関数が呼び出されると、この関数が呼び出されます。 *Ndrawaspect*が DVASPECT_CONTENT の場合、既定の実装は、 [m_sizeExtent](#m_sizeextent)メンバーを指定されたサイズに設定します。それ以外の場合は0を返します。 項目のサイズを変更するときに特別な処理を実行するには、この関数をオーバーライドします。

##  <a name="onshow"></a>  COleServerItem::OnShow

OLE 項目を適切に表示するようにサーバーアプリケーションに指示するために、フレームワークによって呼び出されます。

```
virtual void OnShow();
```

### <a name="remarks"></a>Remarks

通常、この関数は、コンテナーアプリケーションのユーザーが項目を作成したり、項目を表示する必要がある編集などの動詞を実行したりするときに呼び出されます。 既定の実装では、インプレースアクティブ化が試行されます。 これが失敗した場合、関数`OnOpen`は、メンバー関数を呼び出して、OLE 項目を別のウィンドウに表示します。

OLE 項目が表示されるときに特別な処理を実行する場合は、この関数をオーバーライドします。

##  <a name="onupdate"></a>COleServerItem:: OnUpdate

項目が変更されたときにフレームワークによって呼び出されます。

```
virtual void OnUpdate(
    COleServerItem* pSender,
    LPARAM lHint,
    CObject* pHint,
    DVASPECT nDrawAspect);
```

### <a name="parameters"></a>パラメーター

*pSender*<br/>
ドキュメントを変更した項目へのポインター。 NULL を指定できます。

*lHint*<br/>
変更に関する情報を格納します。

*pHint*<br/>
変更に関する情報を格納しているオブジェクトへのポインター。

*nDrawAspect*<br/>
DVASPECT 列挙子の値。 このパラメーターには、次のいずれかの値を指定できます。

- DVASPECT_CONTENT Item は、コンテナー内に埋め込みオブジェクトとして表示できるように表現されます。

- なりますが項目は、参照ツールで表示できるように "サムネイル" 表現で表示されます。

- DVASPECT_ICON Item はアイコンで表されます。

- DVASPECT_DOCPRINT Item は、[ファイル] メニューの [印刷] コマンドを使用して印刷されたかのように表されます。

### <a name="remarks"></a>Remarks

既定の実装では、ヒントまたは送信者に関係なく、 [Notifychanged](#notifychanged)が呼び出されます。

##  <a name="onupdateitems"></a>COleServerItem:: OnUpdateItems

サーバードキュメント内のすべての項目を更新するために、フレームワークによって呼び出されます。

```
virtual void OnUpdateItems();
```

### <a name="remarks"></a>Remarks

既定の実装は、ドキュメント内`COleClientItem`のすべてのオブジェクトに対して [UpdateLink](../../mfc/reference/coleclientitem-class.md#updatelink) を呼び出します。

##  <a name="setitemname"></a>COleServerItem:: SetItemName

リンク項目を作成してその名前を設定するときに、この関数を呼び出します。

```
void SetItemName(LPCTSTR lpszItemName);
```

### <a name="parameters"></a>パラメーター

*lpszItemName*<br/>
項目の新しい名前へのポインター。

### <a name="remarks"></a>Remarks

名前は、ドキュメント内で一意である必要があります。 サーバーアプリケーションがリンクされた項目を編集するために呼び出されると、アプリケーションはこの名前を使用して項目を検索します。 埋め込みアイテムに対しては、この関数を呼び出す必要はありません。

## <a name="see-also"></a>関連項目

[MFC サンプル HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[CDocItem クラス](../../mfc/reference/cdocitem-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem クラス](../../mfc/reference/coleclientitem-class.md)<br/>
[COleServerDoc クラス](../../mfc/reference/coleserverdoc-class.md)<br/>
[COleTemplateServer クラス](../../mfc/reference/coletemplateserver-class.md)
