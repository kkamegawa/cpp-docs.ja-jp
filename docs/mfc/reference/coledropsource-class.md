---
title: COleDropSource クラス
ms.date: 11/04/2016
f1_keywords:
- COleDropSource
- AFXOLE/COleDropSource
- AFXOLE/COleDropSource::COleDropSource
- AFXOLE/COleDropSource::GiveFeedback
- AFXOLE/COleDropSource::OnBeginDrag
- AFXOLE/COleDropSource::QueryContinueDrag
helpviewer_keywords:
- COleDropSource [MFC], COleDropSource
- COleDropSource [MFC], GiveFeedback
- COleDropSource [MFC], OnBeginDrag
- COleDropSource [MFC], QueryContinueDrag
ms.assetid: d3eecc5f-a70b-4a01-b705-7d2c098ebe17
ms.openlocfilehash: d93eb3de87b50f337f0d3edad65f5dc3013e8327
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127458"
---
# <a name="coledropsource-class"></a>COleDropSource クラス

データをドロップターゲットにドラッグできるようにします。

## <a name="syntax"></a>構文

```
class COleDropSource : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[COleDropSource::COleDropSource](#coledropsource)|`COleDropSource` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[COleDropSource:: System.windows.dragdrop.givefeedback>](#givefeedback)|ドラッグアンドドロップ操作中にカーソルを変更します。|
|[COleDropSource::OnBeginDrag](#onbegindrag)|ドラッグアンドドロップ操作中にマウスキャプチャを処理します。|
|[COleDropSource:: System.windows.dragdrop.querycontinuedrag>](#querycontinuedrag)|ドラッグ操作を続行するかどうかを確認します。|

## <a name="remarks"></a>解説

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)クラスは、ドラッグアンドドロップ操作の受信部分を処理します。 `COleDropSource` オブジェクトは、ドラッグ操作が開始されるタイミングを決定し、ドラッグ操作中にフィードバックを提供し、ドラッグ操作が終了するタイミングを決定します。

`COleDropSource` オブジェクトを使用するには、コンストラクターを呼び出すだけです。 これにより、マウスクリックなどのイベントを特定するプロセスを簡略化し、 [COleDataSource::D odragdrop](../../mfc/reference/coledatasource-class.md#dodragdrop)、 [COleClientItem::D odragdrop](../../mfc/reference/coleclientitem-class.md#dodragdrop)、または[COleServerItem::D odragdrop](../../mfc/reference/coleserveritem-class.md#dodragdrop)関数を使用してドラッグ操作を開始できます。 これらの関数は、`COleDropSource` オブジェクトを作成します。 `COleDropSource` のオーバーライド可能な関数の既定の動作を変更することもできます。 これらのメンバー関数は、フレームワークによって適切なタイミングで呼び出されます。

OLE を使用したドラッグアンドドロップ操作の詳細については、「 [ole ドラッグアンドドロップ](../../mfc/drag-and-drop-ole.md)」を参照してください。

詳細については、Windows SDK の「 [IDropSource](/windows/win32/api/oleidl/nn-oleidl-idropsource) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropSource`

## <a name="requirements"></a>［要件］

**ヘッダー:** afxole

##  <a name="coledropsource"></a>COleDropSource::COleDropSource

`COleDropSource` オブジェクトを構築します。

```
COleDropSource();
```

##  <a name="givefeedback"></a>COleDropSource:: System.windows.dragdrop.givefeedback>

[COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)または[COleDropTarget::D ragenter](../../mfc/reference/coledroptarget-class.md#ondragenter)を呼び出した後に、フレームワークによって呼び出されます。

```
virtual SCODE GiveFeedback(DROPEFFECT dropEffect);
```

### <a name="parameters"></a>パラメーター

*dropEffect*<br/>
ユーザーに表示する効果。通常は、選択したデータをこの時点でドロップが発生した場合に何が起こるかを示します。 通常、これは、 [cview:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)または[Cview:: OnDragOver](../../mfc/reference/cview-class.md#ondragover)への最新の呼び出しによって返される値です。 次の1つまたは複数を指定できます。

- DROPEFFECT_NONE 削除は許可されません。

- DROPEFFECT_COPY コピー操作が実行されます。

- 移動操作が実行さ DROPEFFECT_MOVE ます。

- DROPEFFECT_LINK、削除されたデータから元のデータへのリンクが確立されます。

- ドラッグのスクロール操作が実行されようとしている DROPEFFECT_SCROLL、またはターゲットで発生しようとしています。

### <a name="return-value"></a>戻り値

ドラッグが進行中の場合は DRAGDROP_S_USEDEFAULTCURSORS を返し、そうでない場合は NOERROR を返します。

### <a name="remarks"></a>解説

この関数をオーバーライドすると、この時点でドロップが発生した場合に何が起こるかについてユーザーにフィードバックを提供します。 既定の実装では、OLE の既定のカーソルが使用されます。 OLE を使用したドラッグアンドドロップ操作の詳細については、「 [ole ドラッグアンドドロップ](../../mfc/drag-and-drop-ole.md)」を参照してください。

詳細については、Windows SDK の「 [IDropSource:: system.windows.dragdrop.givefeedback>](/windows/win32/api/oleidl/nf-oleidl-idropsource-givefeedback)、 [IDropTarget::D Ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover)、および[IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) 」を参照してください。

##  <a name="onbegindrag"></a>COleDropSource::OnBeginDrag

マウスの左ボタンを押すなど、ドラッグ操作を開始できるイベントが発生したときにフレームワークによって呼び出されます。

```
virtual BOOL OnBeginDrag(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
選択されたデータを含むウィンドウを指します。

### <a name="return-value"></a>戻り値

ドラッグが許可されている場合は0以外。それ以外の場合は0。

### <a name="remarks"></a>解説

ドラッグプロセスの開始方法を変更する場合は、この関数をオーバーライドします。 既定の実装はマウスをキャプチャし、ユーザーがマウスの左ボタンまたは右ボタンをクリックするか ESC キーを押したときに、マウスを離します。

##  <a name="querycontinuedrag"></a>COleDropSource:: System.windows.dragdrop.querycontinuedrag>

ドラッグが開始された後、この関数は、ドラッグ操作が取り消されるか完了するまで、フレームワークによって繰り返し呼び出されます。

```
virtual SCODE QueryContinueDrag(
    BOOL bEscapePressed,
    DWORD dwKeyState);
```

### <a name="parameters"></a>パラメーター

*bEscapePressed*<br/>
`COleDropSource::QueryContinueDrag`の最後の呼び出し以降に ESC キーが押されたかどうかを示します。

*dwKeyState*<br/>
キーボードの修飾キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。

### <a name="return-value"></a>戻り値

ESC キーまたは右ボタンが押されている場合は DRAGDROP_S_CANCEL、ドラッグを開始する前に左ボタンが発生する場合は。 DROP 操作を実行する必要があるかどうかを DRAGDROP_S_DROP します。 それ以外の場合は S_OK。

### <a name="remarks"></a>解説

ドラッグが取り消された時点またはドロップが発生したポイントを変更する場合は、この関数をオーバーライドします。

既定の実装は、ドロップを開始するか、次のようにドラッグをキャンセルします。 ESC キーまたはマウスの右ボタンが押されたときに、ドラッグ操作をキャンセルします。 ドラッグを開始した後にマウスの左ボタンを離すと、ドロップ操作が開始されます。 それ以外の場合は S_OK を返し、それ以上の操作は実行しません。

この関数は頻繁に呼び出されるため、できるだけ最適化する必要があります。

## <a name="see-also"></a>参照

[MFC サンプル HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
