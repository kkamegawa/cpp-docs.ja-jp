---
title: COleDropTarget クラス
ms.date: 11/04/2016
f1_keywords:
- COleDropTarget
- AFXOLE/COleDropTarget
- AFXOLE/COleDropTarget::COleDropTarget
- AFXOLE/COleDropTarget::OnDragEnter
- AFXOLE/COleDropTarget::OnDragLeave
- AFXOLE/COleDropTarget::OnDragOver
- AFXOLE/COleDropTarget::OnDragScroll
- AFXOLE/COleDropTarget::OnDrop
- AFXOLE/COleDropTarget::OnDropEx
- AFXOLE/COleDropTarget::Register
- AFXOLE/COleDropTarget::Revoke
helpviewer_keywords:
- COleDropTarget [MFC], COleDropTarget
- COleDropTarget [MFC], OnDragEnter
- COleDropTarget [MFC], OnDragLeave
- COleDropTarget [MFC], OnDragOver
- COleDropTarget [MFC], OnDragScroll
- COleDropTarget [MFC], OnDrop
- COleDropTarget [MFC], OnDropEx
- COleDropTarget [MFC], Register
- COleDropTarget [MFC], Revoke
ms.assetid: a58c9a48-6a93-4357-b078-4594df258311
ms.openlocfilehash: f5f101ca2c505e1b7c6b50b21af7d5aeef4ae625
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127882"
---
# <a name="coledroptarget-class"></a>COleDropTarget クラス

ウィンドウと OLE ライブラリの間の通信機構を提供します。

## <a name="syntax"></a>構文

```
class COleDropTarget : public CCmdTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[COleDropTarget::COleDropTarget](#coledroptarget)|`COleDropTarget` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[COleDropTarget:: OnDragEnter](#ondragenter)|カーソルがウィンドウに最初に入ったときに呼び出されます。|
|[COleDropTarget::OnDragLeave](#ondragleave)|カーソルがウィンドウの外にドラッグされると呼び出されます。|
|[COleDropTarget::OnDragOver](#ondragover)|カーソルがウィンドウの上にドラッグされたときに繰り返し呼び出されます。|
|[COleDropTarget:: OnDragScroll](#ondragscroll)|カーソルがウィンドウのスクロール領域にドラッグされているかどうかを判断するために呼び出されます。|
|[COleDropTarget::OnDrop](#ondrop)|データがウィンドウの既定のハンドラーにドロップされると呼び出されます。|
|[COleDropTarget::OnDropEx](#ondropex)|データがウィンドウの最初のハンドラーにドロップされるときに呼び出されます。|
|[COleDropTarget:: Register](#register)|ウィンドウを有効なドロップ先として登録します。|
|[COleDropTarget:: Revoke](#revoke)|ウィンドウが有効なドロップ先となるのを停止します。|

## <a name="remarks"></a>コメント

このクラスのオブジェクトを作成すると、ウィンドウは OLE ドラッグアンドドロップメカニズムを使用してデータを受け取ることができます。

ドロップコマンドを受け入れるウィンドウを取得するには、まず `COleDropTarget` クラスのオブジェクトを作成し、次に、必要な `CWnd` オブジェクトへのポインターを唯一のパラメーターとして[Register](#register)関数を呼び出します。

OLE を使用したドラッグアンドドロップ操作の詳細については、「 [ole ドラッグアンドドロップ](../../mfc/drag-and-drop-ole.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleDropTarget`

## <a name="requirements"></a>要件

**ヘッダー:** afxole

##  <a name="coledroptarget"></a>COleDropTarget::COleDropTarget

`COleDropTarget`クラスのオブジェクトを構築します。

```
COleDropTarget();
```

### <a name="remarks"></a>コメント

このオブジェクトをウィンドウに関連付けるには、 [Register](#register)を呼び出します。

##  <a name="ondragenter"></a>COleDropTarget:: OnDragEnter

カーソルが最初にウィンドウにドラッグされたときにフレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
カーソルが入っているウィンドウを指します。

*pDataObject*<br/>
削除できるデータを格納しているデータオブジェクトを指します。

*dwKeyState*<br/>
修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。

*視点*<br/>
クライアント座標におけるカーソルの現在の位置を格納します。

### <a name="return-value"></a>戻り値

*ポイント*によって指定された場所で削除が試行された場合に発生する効果。 次の1つまたは複数を指定できます。

- DROPEFFECT_NONE 削除は許可されません。

- DROPEFFECT_COPY コピー操作が実行されます。

- 移動操作が実行さ DROPEFFECT_MOVE ます。

- DROPEFFECT_LINK、削除されたデータから元のデータへのリンクが確立されます。

- ドラッグのスクロール操作が実行されようとしている DROPEFFECT_SCROLL、またはターゲットで発生しようとしています。

### <a name="remarks"></a>コメント

ウィンドウでドロップ操作を実行できるようにするには、この関数をオーバーライドします。 既定の実装では、 [CView:: OnDragEnter](../../mfc/reference/cview-class.md#ondragenter)が呼び出されます。この場合、既定で DROPEFFECT_NONE が返されます。

詳細については、Windows SDK の「 [IDropTarget::D ragenter](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragenter) 」を参照してください。

##  <a name="ondragleave"></a>COleDropTarget::OnDragLeave

ドラッグ操作が有効になっている間にカーソルがウィンドウから離れると、フレームワークによって呼び出されます。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
カーソルが出てくるウィンドウを指します。

### <a name="remarks"></a>コメント

ドラッグ操作が指定したウィンドウを離れるときに特別な動作が必要な場合は、この関数をオーバーライドします。 この関数の既定の実装では、 [CView:: OnDragLeave](../../mfc/reference/cview-class.md#ondragleave)が呼び出されます。

詳細については、Windows SDK の「 [IDropTarget::D ragleave](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragleave) 」を参照してください。

##  <a name="ondragover"></a>COleDropTarget::OnDragOver

カーソルがウィンドウの上にドラッグされると、フレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
カーソルがあるウィンドウをポイントします。

*pDataObject*<br/>
削除するデータを含むデータオブジェクトを指します。

*dwKeyState*<br/>
修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。

*視点*<br/>
クライアント座標におけるカーソルの現在の位置を格納します。

### <a name="return-value"></a>戻り値

*ポイント*によって指定された場所で削除が試行された場合に発生する効果。 次の1つまたは複数を指定できます。

- DROPEFFECT_NONE 削除は許可されません。

- DROPEFFECT_COPY コピー操作が実行されます。

- 移動操作が実行さ DROPEFFECT_MOVE ます。

- DROPEFFECT_LINK、削除されたデータから元のデータへのリンクが確立されます。

- DROPEFFECT_SCROLL は、ドラッグのスクロール操作が実行されるか、またはターゲットで発生することを示します。

### <a name="remarks"></a>コメント

ウィンドウでドロップ操作を実行できるようにするには、この関数をオーバーライドする必要があります。 この関数の既定の実装では、 [CView:: OnDragOver](../../mfc/reference/cview-class.md#ondragover)が呼び出されます。この場合、既定では DROPEFFECT_NONE が返されます。 この関数はドラッグアンドドロップ操作の間に頻繁に呼び出されるため、できるだけ最適化する必要があります。

詳細については、Windows SDK の「 [IDropTarget::D ragover](/windows/win32/api/oleidl/nf-oleidl-idroptarget-dragover) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCOleContainer#21](../../mfc/codesnippet/cpp/coledroptarget-class_1.cpp)]

##  <a name="ondragscroll"></a>COleDropTarget:: OnDragScroll

[Ondragenter](#ondragenter)または[OnDragOver](#ondragover)を呼び出して*ポイント*がスクロール領域にあるかどうかを判断する前に、フレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDragScroll(
    CWnd* pWnd,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
カーソルが現在の上にあるウィンドウをポイントします。

*dwKeyState*<br/>
修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。

*視点*<br/>
画面を基準とした、カーソルの位置 (ピクセル単位) を格納します。

### <a name="return-value"></a>戻り値

*ポイント*によって指定された場所で削除が試行された場合に発生する効果。 次の1つまたは複数を指定できます。

- DROPEFFECT_NONE 削除は許可されません。

- DROPEFFECT_COPY コピー操作が実行されます。

- 移動操作が実行さ DROPEFFECT_MOVE ます。

- DROPEFFECT_LINK、削除されたデータから元のデータへのリンクが確立されます。

- DROPEFFECT_SCROLL は、ドラッグのスクロール操作が実行されるか、またはターゲットで発生することを示します。

### <a name="remarks"></a>コメント

このイベントに特別な動作を提供する場合は、この関数をオーバーライドします。 この関数の既定の実装では、 [CView:: OnDragScroll](../../mfc/reference/cview-class.md#ondragscroll)が呼び出されます。これは、カーソルがウィンドウの境界内の既定のスクロール領域にドラッグされたときに、DROPEFFECT_NONE を返し、ウィンドウをスクロールします。

##  <a name="ondrop"></a>COleDropTarget::OnDrop

ドロップ操作が行われるときにフレームワークによって呼び出されます。

```
virtual BOOL OnDrop(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
カーソルが現在の上にあるウィンドウをポイントします。

*pDataObject*<br/>
削除するデータを含むデータオブジェクトを指します。

*dropEffect*<br/>
ユーザーが削除操作のために選択した効果。 次の1つまたは複数を指定できます。

- DROPEFFECT_COPY コピー操作が実行されます。

- 移動操作が実行さ DROPEFFECT_MOVE ます。

- DROPEFFECT_LINK、削除されたデータから元のデータへのリンクが確立されます。

*視点*<br/>
画面を基準とした、カーソルの位置 (ピクセル単位) を格納します。

### <a name="return-value"></a>戻り値

削除に成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

フレームワークは最初に[OnDropEx](#ondropex)を呼び出します。 `OnDropEx` 関数が削除を処理しない場合、フレームワークはこのメンバー関数を `OnDrop`呼び出します。 通常、アプリケーションは、マウスの右ボタンのドラッグアンドドロップを処理するために、view クラスの[OnDropEx](../../mfc/reference/cview-class.md#ondropex)をオーバーライドします。 通常、ビュークラス[OnDrop](../../mfc/reference/cview-class.md#ondrop)は、単純なドラッグアンドドロップの処理に使用されます。

`COleDropTarget::OnDrop` の既定の実装では、 [CView:: OnDrop](../../mfc/reference/cview-class.md#ondrop)が呼び出されます。この場合、既定では FALSE が返されます。

詳細については、Windows SDK の「 [IDropTarget::D の rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) 」を参照してください。

##  <a name="ondropex"></a>COleDropTarget::OnDropEx

ドロップ操作が行われるときにフレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropDefault,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
カーソルが現在の上にあるウィンドウをポイントします。

*pDataObject*<br/>
削除するデータを含むデータオブジェクトを指します。

*dropDefault*<br/>
ユーザーが現在のキーの状態に基づいて既定のドロップ操作を選択した場合の効果。 DROPEFFECT_NONE することができます。 ドロップ効果については、「解説」を参照してください。

*ドロップ*<br/>
ドロップソースがサポートするドロップ効果の一覧。 ドロップ効果の値は、ビットごとの OR ( **&#124;** ) 演算を使用して組み合わせることができます。 ドロップ効果については、「解説」を参照してください。

*視点*<br/>
画面を基準とした、カーソルの位置 (ピクセル単位) を格納します。

### <a name="return-value"></a>戻り値

*ポイント*によって指定された位置での削除が試行された結果のドロップ効果。 ドロップ効果については、「解説」を参照してください。

### <a name="remarks"></a>コメント

フレームワークは、まずこの関数を呼び出します。 削除を処理しない場合、フレームワークは[OnDrop](#ondrop)を呼び出します。 通常は、マウスの右ボタンのドラッグアンドドロップをサポートするために、view クラスの[OnDropEx](../../mfc/reference/cview-class.md#ondropex)をオーバーライドします。 通常、ビュークラス[OnDrop](../../mfc/reference/cview-class.md#ondrop)は、単純なドラッグアンドドロップのサポートのケースを処理するために使用されます。

`COleDropTarget::OnDropEx` の既定の実装では、 [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex)が呼び出されます。 既定では、 [CView:: OnDropEx](../../mfc/reference/cview-class.md#ondropex)は、 [OnDrop](#ondrop)メンバー関数を呼び出す必要があることを示すダミー値のみを返します。

ドロップ効果は、ドロップ操作に関連付けられているアクションを記述します。 次のドロップ効果の一覧を参照してください。

- DROPEFFECT_NONE 削除は許可されません。

- DROPEFFECT_COPY コピー操作が実行されます。

- 移動操作が実行さ DROPEFFECT_MOVE ます。

- DROPEFFECT_LINK、削除されたデータから元のデータへのリンクが確立されます。

- DROPEFFECT_SCROLL は、ドラッグのスクロール操作が実行されるか、またはターゲットで発生することを示します。

詳細については、Windows SDK の「 [IDropTarget::D の rop](/windows/win32/api/oleidl/nf-oleidl-idroptarget-drop) 」を参照してください。

##  <a name="register"></a>COleDropTarget:: Register

この関数を呼び出して、ウィンドウを OLE Dll に有効なドロップ先として登録します。

```
BOOL Register(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

*pWnd*<br/>
ドロップ先として登録されるウィンドウを指します。

### <a name="return-value"></a>戻り値

登録が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>コメント

Drop 操作を受け入れるには、この関数を呼び出す必要があります。

詳細については、Windows SDK の「 [RegisterDragDrop](/windows/win32/api/ole2/nf-ole2-registerdragdrop) 」を参照してください。

##  <a name="revoke"></a>COleDropTarget:: Revoke

ドロップ先として登録されているすべてのウィンドウを破棄する前に、この関数を呼び出します。ドロップターゲットの一覧から削除するには、 [Register](#register)を呼び出します。

```
virtual void Revoke();
```

### <a name="remarks"></a>コメント

この関数は、登録されたウィンドウの[OnDestroy](../../mfc/reference/cwnd-class.md#ondestroy)ハンドラーから自動的に呼び出されるため、通常はこの関数を明示的に呼び出す必要はありません。

詳細については、Windows SDK の「 [RevokeDragDrop](/windows/win32/api/ole2/nf-ole2-revokedragdrop) 」を参照してください。

## <a name="see-also"></a>参照

[MFC サンプル HIERSVR](../../overview/visual-cpp-samples.md)<br/>
[MFC サンプル OCLIENT](../../overview/visual-cpp-samples.md)<br/>
[CCmdTarget クラス](../../mfc/reference/ccmdtarget-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleDropSource クラス](../../mfc/reference/coledropsource-class.md)
