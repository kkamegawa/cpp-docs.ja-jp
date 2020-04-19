---
title: COleDataSource クラス
ms.date: 11/04/2016
f1_keywords:
- COleDataSource
- AFXOLE/COleDataSource
- AFXOLE/COleDataSource::COleDataSource
- AFXOLE/COleDataSource::CacheData
- AFXOLE/COleDataSource::CacheGlobalData
- AFXOLE/COleDataSource::DelayRenderData
- AFXOLE/COleDataSource::DelayRenderFileData
- AFXOLE/COleDataSource::DelaySetData
- AFXOLE/COleDataSource::DoDragDrop
- AFXOLE/COleDataSource::Empty
- AFXOLE/COleDataSource::FlushClipboard
- AFXOLE/COleDataSource::GetClipboardOwner
- AFXOLE/COleDataSource::OnRenderData
- AFXOLE/COleDataSource::OnRenderFileData
- AFXOLE/COleDataSource::OnRenderGlobalData
- AFXOLE/COleDataSource::OnSetData
- AFXOLE/COleDataSource::SetClipboard
helpviewer_keywords:
- COleDataSource [MFC], COleDataSource
- COleDataSource [MFC], CacheData
- COleDataSource [MFC], CacheGlobalData
- COleDataSource [MFC], DelayRenderData
- COleDataSource [MFC], DelayRenderFileData
- COleDataSource [MFC], DelaySetData
- COleDataSource [MFC], DoDragDrop
- COleDataSource [MFC], Empty
- COleDataSource [MFC], FlushClipboard
- COleDataSource [MFC], GetClipboardOwner
- COleDataSource [MFC], OnRenderData
- COleDataSource [MFC], OnRenderFileData
- COleDataSource [MFC], OnRenderGlobalData
- COleDataSource [MFC], OnSetData
- COleDataSource [MFC], SetClipboard
ms.assetid: 02c8ee7d-8e10-4463-8613-bb2a0305ca69
ms.openlocfilehash: 5cd573590bc1adb303e0b4c5cd600b9fa6c685b2
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127856"
---
# <a name="coledatasource-class"></a>COleDataSource クラス

OLE アプリケーションが、クリップボード操作やドラッグ アンド ドロップ操作のようなデータ転送操作中に用意するデータを置くキャッシュの役目をします。

## <a name="syntax"></a>構文

```
class COleDataSource : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[COleDataSource:: COleDataSource](#coledatasource)|`COleDataSource` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[COleDataSource:: CacheData](#cachedata)|`STGMEDIUM` 構造体を使用して、指定された形式でデータを提供します。|
|[COleDataSource:: CacheGlobalData](#cacheglobaldata)|は、HGLOBAL を使用して、指定された形式でデータを提供します。|
|[COleDataSource::D elayRenderData](#delayrenderdata)|遅延レンダリングを使用して、指定された形式でデータを提供します。|
|[COleDataSource::D elayRenderFileData](#delayrenderfiledata)|`CFile` ポインターに指定された形式でデータを提供します。|
|[COleDataSource::D elaySetData](#delaysetdata)|`OnSetData`でサポートされているすべての形式に対して呼び出されます。|
|[COleDataSource::D oDragDrop](#dodragdrop)|データソースでドラッグアンドドロップ操作を実行します。|
|[COleDataSource:: Empty](#empty)|データの `COleDataSource` オブジェクトを空にします。|
|[COleDataSource:: FlushClipboard](#flushclipboard)|すべてのデータをクリップボードに表示します。|
|[COleDataSource:: GetClipboardOwner](#getclipboardowner)|クリップボードに配置されたデータがまだ存在していることを確認します。|
|[COleDataSource:: OnRenderData](#onrenderdata)|遅延表示の一部としてデータを取得します。|
|[COleDataSource:: OnRenderFileData](#onrenderfiledata)|遅延表示の一部として `CFile` にデータを取得します。|
|[COleDataSource:: OnRenderGlobalData](#onrenderglobaldata)|遅延レンダリングの一部として、データを HGLOBAL に取得します。|
|[COleDataSource:: OnSetData](#onsetdata)|`COleDataSource` オブジェクトのデータを置換するために呼び出されます。|
|[COleDataSource:: SetClipboard](#setclipboard)|`COleDataSource` オブジェクトをクリップボードに配置します。|

## <a name="remarks"></a>コメント

OLE データソースは直接作成できます。 また、 [COleClientItem](../../mfc/reference/coleclientitem-class.md)クラスと[COleServerItem](../../mfc/reference/coleserveritem-class.md)クラスは、`CopyToClipboard` と `DoDragDrop` メンバー関数に応答して OLE データソースを作成します。 簡単な説明については、「 [COleServerItem:: CopyToClipboard](../../mfc/reference/coleserveritem-class.md#copytoclipboard) 」を参照してください。 クライアント項目またはサーバー項目クラスの `OnGetClipboardData` メンバー関数をオーバーライドして、`CopyToClipboard` または `DoDragDrop` メンバー関数用に作成された OLE データソースのデータにクリップボード形式を追加します。

転送用にデータを準備する場合は常に、このクラスのオブジェクトを作成し、データに最適な方法を使用してデータを入力する必要があります。 データソースへの挿入方法は、データがすぐに提供されるか (即時レンダリング)、または必要に応じて (遅延レンダリング)、直接影響を受けます。 使用するクリップボード形式 (および省略可能な[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体) を渡すことによってデータを提供するすべてのクリップボード形式について、 [DelayRenderData](#delayrenderdata)を呼び出します。

データソースとデータ転送の詳細については、「[データオブジェクトとデータソース (OLE)](../../mfc/data-objects-and-data-sources-ole.md)」を参照してください。 また、「[クリップボード](../../mfc/clipboard.md)」のトピックでは、OLE クリップボードのメカニズムについて説明しています。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDataSource`

## <a name="requirements"></a>要件

**ヘッダー:** afxole

##  <a name="cachedata"></a>COleDataSource:: CacheData

データ転送操作中にデータが提供される形式を指定するには、この関数を呼び出します。

```
void CacheData(
    CLIPFORMAT cfFormat,
    LPSTGMEDIUM lpStgMedium,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>パラメーター

*cfFormat*<br/>
データを提供するクリップボード形式。 このパラメーターには、定義済みのクリップボード形式、またはネイティブ Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)関数によって返される値のいずれかを指定できます。

*lpStgMedium*<br/>
指定された形式のデータを含む[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体を指します。

*lpFormatEtc*<br/>
データが提供される形式を記述する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。 *CfFormat*で指定されたクリップボード形式以外の追加の書式情報を指定する場合は、このパラメーターの値を指定します。 NULL の場合は、`FORMATETC` 構造内の他のフィールドに既定値が使用されます。

### <a name="remarks"></a>コメント

この関数は即時レンダリングを使用してデータを提供するため、データを指定する必要があります。 データは必要になるまでキャッシュされます。

[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体を使用してデータを指定します。 また、指定するデータの量が、HGLOBAL を使用して効率的に転送するのに十分ではない場合は、`CacheGlobalData` メンバー関数を使用することもできます。

を呼び出した後、`lpFormatEtc` の `ptd` メンバー `CacheData`、 *lpStgMedium*の内容は、呼び出し元ではなく、データオブジェクトによって所有されます。

遅延レンダリングを使用するには、 [DelayRenderData](#delayrenderdata)または[DelayRenderFileData](#delayrenderfiledata)メンバー関数を呼び出します。 MFC によって処理される遅延レンダリングの詳細については、「[データオブジェクトとデータソース: 操作](../../mfc/data-objects-and-data-sources-manipulation.md)」を参照してください。

詳細については、Windows SDK の「 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体と[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体」を参照してください。

詳細については、Windows SDK の「 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 」を参照してください。

##  <a name="cacheglobaldata"></a>COleDataSource:: CacheGlobalData

データ転送操作中にデータが提供される形式を指定するには、この関数を呼び出します。

```
void CacheGlobalData(
    CLIPFORMAT cfFormat,
    HGLOBAL hGlobal,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>パラメーター

*cfFormat*<br/>
データを提供するクリップボード形式。 このパラメーターには、定義済みのクリップボード形式、またはネイティブ Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)関数によって返される値のいずれかを指定できます。

*hGlobal*<br/>
指定された形式のデータを格納するグローバルメモリブロックへのハンドル。

*lpFormatEtc*<br/>
データが提供される形式を記述する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。 *CfFormat*で指定されたクリップボード形式以外の追加の書式情報を指定する場合は、このパラメーターの値を指定します。 NULL の場合は、`FORMATETC` 構造内の他のフィールドに既定値が使用されます。

### <a name="remarks"></a>コメント

この関数は、即時レンダリングを使用してデータを提供するため、関数を呼び出すときにデータを指定する必要があります。データは必要になるまでキャッシュされます。 大量のデータを提供する場合や、構造化されたストレージメディアが必要な場合は、`CacheData` メンバー関数を使用します。

遅延レンダリングを使用するには、 [DelayRenderData](#delayrenderdata)または[DelayRenderFileData](#delayrenderfiledata)メンバー関数を呼び出します。 MFC によって処理される遅延レンダリングの詳細については、「[データオブジェクトとデータソース: 操作](../../mfc/data-objects-and-data-sources-manipulation.md)」を参照してください。

詳細については、Windows SDK の[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を参照してください。

詳細については、Windows SDK の「 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 」を参照してください。

##  <a name="coledatasource"></a>COleDataSource:: COleDataSource

`COleDataSource` オブジェクトを構築します。

```
COleDataSource();
```

##  <a name="delayrenderdata"></a>COleDataSource::D elayRenderData

データ転送操作中にデータが提供される形式を指定するには、この関数を呼び出します。

```
void DelayRenderData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>パラメーター

*cfFormat*<br/>
データを提供するクリップボード形式。 このパラメーターには、定義済みのクリップボード形式、またはネイティブ Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)関数によって返される値のいずれかを指定できます。

*lpFormatEtc*<br/>
データが提供される形式を記述する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。 *CfFormat*で指定されたクリップボード形式以外の追加の書式情報を指定する場合は、このパラメーターの値を指定します。 NULL の場合は、`FORMATETC` 構造内の他のフィールドに既定値が使用されます。

### <a name="remarks"></a>コメント

この関数は、遅延レンダリングを使用してデータを提供するため、データはすぐには提供されません。 [OnRenderData](#onrenderdata)または[OnRenderGlobalData](#onrenderglobaldata)メンバー関数は、データを要求するために呼び出されます。

`CFile` オブジェクトを使用してデータを指定しない場合は、この関数を使用します。 `CFile` オブジェクトを使用してデータを指定する場合は、 [DelayRenderFileData](#delayrenderfiledata)メンバー関数を呼び出します。 MFC によって処理される遅延レンダリングの詳細については、「[データオブジェクトとデータソース: 操作](../../mfc/data-objects-and-data-sources-manipulation.md)」を参照してください。

直接レンダリングを使用するには、 [Cachedata](#cachedata)関数または[CacheGlobalData](#cacheglobaldata)メンバー関数を呼び出します。

詳細については、Windows SDK の[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を参照してください。

詳細については、Windows SDK の「 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 」を参照してください。

##  <a name="delayrenderfiledata"></a>COleDataSource::D elayRenderFileData

データ転送操作中にデータが提供される形式を指定するには、この関数を呼び出します。

```
void DelayRenderFileData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>パラメーター

*cfFormat*<br/>
データを提供するクリップボード形式。 このパラメーターには、定義済みのクリップボード形式、またはネイティブ Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)関数によって返される値のいずれかを指定できます。

*lpFormatEtc*<br/>
データが提供される形式を記述する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。 *CfFormat*で指定されたクリップボード形式以外の追加の書式情報を指定する場合は、このパラメーターの値を指定します。 NULL の場合は、`FORMATETC` 構造内の他のフィールドに既定値が使用されます。

### <a name="remarks"></a>コメント

この関数は、遅延レンダリングを使用してデータを提供するため、データはすぐには提供されません。 [OnRenderFileData](#onrenderfiledata)メンバー関数は、データを要求するために呼び出されます。

`CFile` オブジェクトを使用してデータを指定する場合は、この関数を使用します。 `CFile` オブジェクトを使用しない場合は、 [DelayRenderData](#delayrenderdata)メンバー関数を呼び出します。 MFC によって処理される遅延レンダリングの詳細については、「[データオブジェクトとデータソース: 操作](../../mfc/data-objects-and-data-sources-manipulation.md)」を参照してください。

直接レンダリングを使用するには、 [Cachedata](#cachedata)関数または[CacheGlobalData](#cacheglobaldata)メンバー関数を呼び出します。

詳細については、Windows SDK の[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を参照してください。

詳細については、Windows SDK の「 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 」を参照してください。

##  <a name="delaysetdata"></a>COleDataSource::D elaySetData

データソースの内容の変更をサポートするには、この関数を呼び出します。

```
void DelaySetData(
    CLIPFORMAT cfFormat,
    LPFORMATETC lpFormatEtc = NULL);
```

### <a name="parameters"></a>パラメーター

*cfFormat*<br/>
データを配置するクリップボード形式。 このパラメーターには、定義済みのクリップボード形式、またはネイティブ Windows [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw)関数によって返される値のいずれかを指定できます。

*lpFormatEtc*<br/>
データが置換される形式を記述する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。 *CfFormat*で指定されたクリップボード形式以外の追加の書式情報を指定する場合は、このパラメーターの値を指定します。 NULL の場合は、`FORMATETC` 構造内の他のフィールドに既定値が使用されます。

### <a name="remarks"></a>コメント

[Onsetdata](#onsetdata)は、このような場合にフレームワークによって呼び出されます。 これは、フレームワークが[COleServerItem:: GetDataSource](../../mfc/reference/coleserveritem-class.md#getdatasource)からデータソースを返す場合にのみ使用されます。 `DelaySetData` が呼び出されない場合、`OnSetData` 関数は呼び出されません。 サポートするクリップボードまたは `FORMATETC` 形式ごとに `DelaySetData` を呼び出す必要があります。

詳細については、Windows SDK の[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を参照してください。

詳細については、Windows SDK の「 [RegisterClipboardFormat](/windows/win32/api/winuser/nf-winuser-registerclipboardformatw) 」を参照してください。

##  <a name="dodragdrop"></a>COleDataSource::D oDragDrop

`DoDragDrop` メンバー関数を呼び出して、このデータソースに対してドラッグアンドドロップ操作を実行します。通常は、 [CWnd:: OnLButtonDown](../../mfc/reference/cwnd-class.md#onlbuttondown)ハンドラーを使用します。

```
DROPEFFECT DoDragDrop(
    DWORD dwEffects = DROPEFFECT_COPY|DROPEFFECT_MOVE|DROPEFFECT_LINK,
    LPCRECT lpRectStartDrag = NULL,
    COleDropSource* pDropSource = NULL);
```

### <a name="parameters"></a>パラメーター

*dwEffects*<br/>
このデータソースで許可されているドラッグアンドドロップ操作。 次の1つまたは複数を指定できます。

- コピー操作を実行する DROPEFFECT_COPY ます。

- 移動操作を実行 DROPEFFECT_MOVE ことができます。

- 削除されたデータから元のデータへのリンクを確立 DROPEFFECT_LINK ことができます。

- DROPEFFECT_SCROLL は、ドラッグのスクロール操作が発生する可能性があることを示します。

*lpRectStartDrag*<br/>
ドラッグが実際に開始される場所を定義する四角形へのポインター。 詳細については、「解説」を参照してください。

*pDropSource*<br/>
ドロップ元を指します。 NULL の場合、 [COleDropSource](../../mfc/reference/coledropsource-class.md)の既定の実装が使用されます。

### <a name="return-value"></a>戻り値

ドラッグアンドドロップ操作によって生成されるドロップ効果。それ以外の場合は、指定された四角形を離れる前にユーザーがマウスボタンを離したため、操作が開始されない場合は DROPEFFECT_NONE。

### <a name="remarks"></a>コメント

ドラッグアンドドロップ操作はすぐには開始されません。 マウスカーソルが、 *lpRectStartDrag*で指定された四角形から離れるか、指定されたミリ秒数が経過するまで待機します。 *LpRectStartDrag*が NULL の場合、四角形のサイズは1ピクセルです。

遅延時間は、レジストリキーの設定によって指定されます。 遅延時間を変更するには、 [cwinapp:: WriteProfileString](../../mfc/reference/cwinapp-class.md#writeprofilestring)または[Cwinapp:: writeprofilestring](../../mfc/reference/cwinapp-class.md#writeprofileint)を呼び出します。 遅延時間を指定しない場合は、既定値の200ミリ秒が使用されます。 ドラッグの遅延時間は次のように格納されます。

- Windows NT のドラッグ遅延時間は HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Windows\NT\CurrentVersion\IniFileMapping\win.ini\Windows\DragDelay. に格納されます

- Windows 3.x のドラッグ遅延時間は、WIN に格納されます。INI ファイル ([Windows}] セクションの下)。

- Windows 95/98 のドラッグ遅延時間は、WIN のキャッシュされたバージョンに格納されます.INI.

ドラッグ遅延情報をレジストリまたはに格納する方法の詳細については、「」を参照してください。INI ファイルの「Windows SDK の[Writeprofilestring](/windows/win32/api/winbase/nf-winbase-writeprofilestringw) 」を参照してください。

詳細については、「 [OLE ドラッグアンドドロップ](../../mfc/drag-and-drop-ole.md)」を参照してください。

##  <a name="empty"></a>COleDataSource:: Empty

データの `COleDataSource` オブジェクトを空にするには、この関数を呼び出します。

```
void Empty();
```

### <a name="remarks"></a>コメント

キャッシュと遅延の両方の表示形式は空になるため、再利用できます。

詳細については、Windows SDK の「 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) 」を参照してください。

##  <a name="flushclipboard"></a>COleDataSource:: FlushClipboard

クリップボードにあるデータをレンダリングし、アプリケーションのシャットダウン後にクリップボードからデータを貼り付けることができるようにします。

```
static void PASCAL FlushClipboard();
```

### <a name="remarks"></a>コメント

[Setclipboard](#setclipboard)を使用してクリップボードにデータを格納します。

##  <a name="getclipboardowner"></a>COleDataSource:: GetClipboardOwner

[Setclipboard](#setclipboard)が最後に呼び出されてからクリップボードのデータが変更されたかどうかを判断し、存在する場合は現在の所有者を識別します。

```
static COleDataSource* PASCAL GetClipboardOwner();
```

### <a name="return-value"></a>戻り値

現在クリップボードにあるデータソース。クリップボードに何もない場合、またはクリップボードが呼び出し元アプリケーションによって所有されていない場合は NULL。

##  <a name="onrenderdata"></a>COleDataSource:: OnRenderData

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

### <a name="remarks"></a>コメント

指定された形式は、遅延レンダリングのために[DelayRenderData](#delayrenderdata)または[DelayRenderFileData](#delayrenderfiledata)メンバー関数を使用して、以前に `COleDataSource` オブジェクトに配置されています。 指定されたストレージメディアがファイルまたはメモリのいずれかである場合、この関数の既定の実装は[OnRenderFileData](#onrenderfiledata)または[OnRenderGlobalData](#onrenderglobaldata)を呼び出します。 これらの形式のいずれも指定しない場合、既定の実装では0が返され、何も実行されません。 MFC によって処理される遅延レンダリングの詳細については、「[データオブジェクトとデータソース: 操作](../../mfc/data-objects-and-data-sources-manipulation.md)」を参照してください。

*LpStgMedium*-> *tymed*が TYMED_NULL 場合、`STGMEDIUM` は、 *> lpFormatEtc tymed*によって指定されたとおりに割り当てられ、入力される必要があります。 TYMED_NULL ない場合は、データを入力して `STGMEDIUM` を設定する必要があります。

これは高度なオーバーライド可能です。 要求された形式とメディアでデータを提供するには、この関数をオーバーライドします。 データによっては、この関数の他のバージョンの1つをオーバーライドすることが必要になる場合があります。 データが小さく、サイズが固定されている場合は、`OnRenderGlobalData`をオーバーライドします。 データがファイル内にある場合、またはサイズが可変の場合は、`OnRenderFileData`をオーバーライドします。

詳細については、Windows SDK の「 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1) and [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体、 [Tymed](/windows/win32/api/objidl/ne-objidl-tymed)列挙型、および[IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 」を参照してください。

##  <a name="onrenderfiledata"></a>COleDataSource:: OnRenderFileData

指定されたストレージメディアがファイルの場合に、指定された形式でデータを取得するためにフレームワークによって呼び出されます。

```
virtual BOOL OnRenderFileData(
    LPFORMATETC lpFormatEtc,
    CFile* pFile);
```

### <a name="parameters"></a>パラメーター

*lpFormatEtc*<br/>
情報が要求される形式を指定する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。

*pFile*<br/>
データが表示される[CFile](../../mfc/reference/cfile-class.md)オブジェクトを指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>コメント

指定された形式は、遅延レンダリングのために[DelayRenderData](#delayrenderdata)メンバー関数を使用して、以前に `COleDataSource` オブジェクトに配置されています。 この関数の既定の実装では、単に FALSE が返されます。

これは高度なオーバーライド可能です。 要求された形式とメディアでデータを提供するには、この関数をオーバーライドします。 データによっては、この関数の他のバージョンの1つをオーバーライドすることが必要になる場合があります。 複数の記憶域メディアを処理する場合は、 [OnRenderData](#onrenderdata)を上書きします。 データがファイル内にある場合、またはサイズが可変の場合は、`OnRenderFileData`をオーバーライドします。 MFC によって処理される遅延レンダリングの詳細については、「[データオブジェクトとデータソース: 操作](../../mfc/data-objects-and-data-sources-manipulation.md)」を参照してください。

詳細については、Windows SDK の「 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) Structure and [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 」を参照してください。

##  <a name="onrenderglobaldata"></a>COleDataSource:: OnRenderGlobalData

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
データが返されるグローバルメモリへのハンドルを指します。 まだ割り当てられていない場合は、このパラメーターを NULL にすることができます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>コメント

指定された形式は、遅延レンダリングのために[DelayRenderData](#delayrenderdata)メンバー関数を使用して、以前に `COleDataSource` オブジェクトに配置されています。 この関数の既定の実装では、単に FALSE が返されます。

*Phglobal*が NULL の場合、新しい HGLOBAL が割り当てられ、 *phglobal*で返される必要があります。 それ以外の場合は、 *Phglobal*によって指定された HGLOBAL にデータを格納する必要があります。 HGLOBAL に配置されるデータの量は、メモリブロックの現在のサイズを超えることはできません。 また、ブロックをより大きなサイズに再割り当てすることはできません。

これは高度なオーバーライド可能です。 要求された形式とメディアでデータを提供するには、この関数をオーバーライドします。 データによっては、この関数の他のバージョンの1つをオーバーライドすることが必要になる場合があります。 複数の記憶域メディアを処理する場合は、 [OnRenderData](#onrenderdata)を上書きします。 データがファイル内にある場合、またはサイズが可変の場合は、 [OnRenderFileData](#onrenderfiledata)をオーバーライドします。 MFC によって処理される遅延レンダリングの詳細については、「[データオブジェクトとデータソース: 操作](../../mfc/data-objects-and-data-sources-manipulation.md)」を参照してください。

詳細については、Windows SDK の「 [FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc) Structure and [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata) 」を参照してください。

##  <a name="onsetdata"></a>COleDataSource:: OnSetData

指定された形式で `COleDataSource` オブジェクトのデータを設定または置換するために、フレームワークによって呼び出されます。

```
virtual BOOL OnSetData(
    LPFORMATETC lpFormatEtc,
    LPSTGMEDIUM lpStgMedium,
    BOOL bRelease);
```

### <a name="parameters"></a>パラメーター

*lpFormatEtc*<br/>
データが置換される形式を指定する[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体を指します。

*lpStgMedium*<br/>
`COleDataSource` オブジェクトの現在の内容を置き換えるデータを格納している[STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)構造体を指します。

*bRelease*<br/>
関数呼び出しの完了後にストレージメディアの所有権を持つユーザーを示します。 呼び出し元は、ストレージメディアの代わりに割り当てられたリソースを解放する担当者を決定します。 呼び出し元は、 *Brelease*を設定することによってこれを行います。 *Brelease*が0以外の場合、データソースは所有権を取得し、使用が終了したときにそのメディアを解放します。 *Brelease*が0の場合、呼び出し元は所有権を保持し、データソースは呼び出しの間だけストレージメディアを使用できます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>コメント

データソースは、データが正常に取得されるまでデータの所有権を取得しません。 つまり、`OnSetData` が0を返す場合、所有権は取得されません。 データソースが所有権を取得すると、 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium)関数を呼び出すことによってストレージメディアが解放されます。

既定の実装では、何も行われません。 指定された形式のデータを置き換えるには、この関数をオーバーライドします。 これは高度なオーバーライド可能です。

詳細については、Windows SDK の「 [STGMEDIUM](/windows/win32/api/objidl/ns-objidl-ustgmedium~r1)および[FORMATETC](/windows/win32/api/objidl/ns-objidl-formatetc)構造体」と「 [ReleaseStgMedium](/windows/win32/api/ole2/nf-ole2-releasestgmedium) and [IDataObject:: GetData](/windows/win32/api/objidl/nf-objidl-idataobject-getdata)関数」を参照してください。

##  <a name="setclipboard"></a>COleDataSource:: SetClipboard

[Cachedata](#cachedata)、 [CacheGlobalData](#cacheglobaldata)、 [DelayRenderData](#delayrenderdata)、または[DelayRenderFileData](#delayrenderfiledata)のいずれかの関数を呼び出した後、`COleDataSource` オブジェクトに格納されているデータをクリップボードに格納します。

```
void SetClipboard();
```

## <a name="see-also"></a>参照

[MFC サンプル HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDataObject クラス](../../mfc/reference/coledataobject-class.md)
