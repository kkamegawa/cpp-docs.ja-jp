---
title: CMFCTabDropTarget クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragEnter
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragLeave
- AFXBASETABCTRL/CMFCTabDropTarget::OnDragOver
- AFXBASETABCTRL/CMFCTabDropTarget::OnDropEx
- AFXBASETABCTRL/CMFCTabDropTarget::Register
helpviewer_keywords:
- CMFCTabDropTarget [MFC], OnDragEnter
- CMFCTabDropTarget [MFC], OnDragLeave
- CMFCTabDropTarget [MFC], OnDragOver
- CMFCTabDropTarget [MFC], OnDropEx
- CMFCTabDropTarget [MFC], Register
ms.assetid: 9777b7b6-10da-4c4b-b1d1-7ea795b0f1cb
ms.openlocfilehash: d0090386b1ebb4d89b9a7613a0b2a28529decbe5
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127430"
---
# <a name="cmfctabdroptarget-class"></a>CMFCTabDropTarget クラス

タブコントロールと OLE ライブラリの間の通信機構を提供します。

## <a name="syntax"></a>構文

```
class CMFCTabDropTarget : public COleDropTarget
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|Name|説明|
|`CMFCTabDropTarget::CMFCTabDropTarget`|既定のコンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|Name|説明|
|[CMFCTabDropTarget:: OnDragEnter](#ondragenter)|ユーザーがオブジェクトをタブウィンドウにドラッグしたときに、フレームワークによって呼び出されます。 ( [COleDropTarget:: OnDragEnter](../../mfc/reference/coledroptarget-class.md#ondragenter)をオーバーライドします)。|
|[CMFCTabDropTarget:: OnDragLeave](#ondragleave)|フォーカスのあるタブウィンドウの外側でオブジェクトをドラッグすると、フレームワークによって呼び出されます。 ( [COleDropTarget:: OnDragLeave](../../mfc/reference/coledroptarget-class.md#ondragleave)をオーバーライドします。)|
|[CMFCTabDropTarget:: OnDragOver](#ondragover)|フォーカスのあるタブウィンドウにユーザーがオブジェクトをドラッグしたときに、フレームワークによって呼び出されます。 ( [COleDropTarget:: OnDragOver](../../mfc/reference/coledroptarget-class.md#ondragover)をオーバーライドします。)|
|[CMFCTabDropTarget:: OnDropEx](#ondropex)|ドラッグ操作の終了時にユーザーがマウスボタンを放すと、フレームワークによって呼び出されます。 ( [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)をオーバーライドします。)|
|[CMFCTabDropTarget:: Register](#register)|コントロールを、OLE ドラッグアンドドロップ操作の対象にできるコントロールとして登録します。|

### <a name="remarks"></a>解説

このクラスは、`CMFCBaseTabCtrl` クラスのドラッグアンドドロップのサポートを提供します。 アプリケーションが[AfxOleInit](ole-initialization.md#afxoleinit)関数を使用して OLE ライブラリを初期化する場合、`CMFCBaseTabCtrl` オブジェクトはドラッグアンドドロップ操作のために自身を登録します。

`CMFCTabDropTarget` クラスは、ドラッグ操作がアクティブになったときにカーソルの下にあるタブを作成することによって、基本クラスを拡張します。 ドラッグアンドドロップ操作の詳細については、「 [OLE ドラッグアンドドロップ](../../mfc/drag-and-drop-ole.md)」を参照してください。

## <a name="example"></a>例

`CMFCTabDropTarget` オブジェクトを構築して、その `Register` メソッドを使用する方法を、次の例に示します。

[!code-cpp[NVC_MFC_RibbonApp#39](../../mfc/reference/codesnippet/cpp/cmfctabdroptarget-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[COleDropTarget](../../mfc/reference/coledroptarget-class.md)

[CMFCTabDropTarget](../../mfc/reference/cmfctabdroptarget-class.md)

## <a name="requirements"></a>［要件］

**ヘッダー:** afxbasetabctrl.h

##  <a name="ondragenter"></a>CMFCTabDropTarget:: OnDragEnter

ユーザーがオブジェクトをタブウィンドウにドラッグしたときに、フレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDragEnter(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pWnd*|から未使用.|
|*pDataObject*|からユーザーがドラッグするオブジェクトへのポインター。|
|*dwKeyState*|から修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。|
|*視点*|からクライアント座標におけるカーソルの位置。|

### <a name="return-value"></a>戻り値

*ポイント*によって指定された場所でドロップが発生した場合の結果の効果。 次の1つまたは複数を指定できます。

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>解説

ツールバーフレームワークがカスタマイズモードでない場合、またはクリップボードのデータ形式が使用できない場合、このメソッドは DROPEFFECT_NONE を返します。 それ以外の場合は、指定されたパラメーターを使用して `CMFCBaseTabCtrl::OnDragEnter` を呼び出した結果を返します。

カスタマイズモードの詳細については、「 [Cmfctoolbar:: Iscustomization emode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)」を参照してください。 クリップボードのデータ形式の詳細については、「 [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)」を参照してください。

##  <a name="ondragleave"></a>CMFCTabDropTarget:: OnDragLeave

フォーカスのあるタブウィンドウの外側でオブジェクトをドラッグすると、フレームワークによって呼び出されます。

```
virtual void OnDragLeave(CWnd* pWnd);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pWnd*|から未使用.|

### <a name="remarks"></a>解説

このメソッドは、`CMFCBaseTabCtrl::OnDragLeave` メソッドを呼び出して、ドラッグ操作を実行します。

##  <a name="ondragover"></a>CMFCTabDropTarget:: OnDragOver

フォーカスのあるタブウィンドウにユーザーがオブジェクトをドラッグしたときに、フレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDragOver(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DWORD dwKeyState,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pWnd*|から未使用.|
|*pDataObject*|からユーザーがドラッグするオブジェクトへのポインター。|
|*dwKeyState*|から修飾子キーの状態を格納します。 これは、MK_CONTROL、MK_SHIFT、MK_ALT、MK_LBUTTON、MK_MBUTTON、および MK_RBUTTON の任意の数を組み合わせたものです。|
|*視点*|からクライアント座標でのマウスポインターの位置。|

### <a name="return-value"></a>戻り値

*ポイント*によって指定された場所でドロップが発生した場合の結果の効果。 次の1つまたは複数を指定できます。

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>解説

このメソッドは、ドラッグ操作がアクティブになったときに、カーソルの下にあるタブを作成します。 ツールバーフレームワークがカスタマイズモードでない場合、またはクリップボードのデータ形式が使用できない場合は DROPEFFECT_NONE が返されます。 それ以外の場合は、指定されたパラメーターを使用して `CMFCBaseTabCtrl::OnDragOver` を呼び出した結果を返します。

カスタマイズモードの詳細については、「 [Cmfctoolbar:: Iscustomization emode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)」を参照してください。 クリップボードのデータ形式の詳細については、「 [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)」を参照してください。

##  <a name="ondropex"></a>CMFCTabDropTarget:: OnDropEx

ドラッグ操作の終了時にユーザーがマウスボタンを放すと、フレームワークによって呼び出されます。

```
virtual DROPEFFECT OnDropEx(
    CWnd* pWnd,
    COleDataObject* pDataObject,
    DROPEFFECT dropEffect,
    DROPEFFECT dropList,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pWnd*|から未使用.|
|*pDataObject*|からユーザーがドラッグするオブジェクトへのポインター。|
|*dropEffect*|から既定のドロップ操作。|
|*ドロップ*|から未使用.|
|*視点*|からクライアント座標でのマウスポインターの位置。|

### <a name="return-value"></a>戻り値

結果として得られるドロップ効果。 次の1つまたは複数を指定できます。

- DROPEFFECT_NONE

- DROPEFFECT_COPY

- DROPEFFECT_MOVE

- DROPEFFECT_LINK

- DROPEFFECT_SCROLL

### <a name="remarks"></a>解説

ツールバーフレームワークがカスタマイズモードで、クリップボードのデータ形式が使用可能な場合、このメソッドは `CMFCBaseTabCtrl::OnDrop` を呼び出します。 `CMFCBaseTabCtrl::OnDrop` の呼び出しが0以外の値を返す場合、このメソッドは*Dropeffect*によって指定された既定のドロップ効果を返します。 それ以外の場合、このメソッドは DROPEFFECT_NONE を返します。 ドロップ効果の詳細については、「 [COleDropTarget:: OnDropEx](../../mfc/reference/coledroptarget-class.md#ondropex)」を参照してください。

カスタマイズモードの詳細については、「 [Cmfctoolbar:: Iscustomization emode](../../mfc/reference/cmfctoolbar-class.md#iscustomizemode)」を参照してください。 クリップボードのデータ形式の詳細については、「 [COleDataObject:: IsDataAvailable](../../mfc/reference/coledataobject-class.md#isdataavailable)」を参照してください。

##  <a name="register"></a>CMFCTabDropTarget:: Register

コントロールを、OLE ドラッグアンドドロップ操作の対象にできるコントロールとして登録します。

```
BOOL Register(CMFCBaseTabCtrl *pOwner);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pOwner*|からドロップ先として登録するタブコントロール。|

### <a name="return-value"></a>戻り値

登録が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

このメソッドは、 [COleDropTarget:: register](../../mfc/reference/coledroptarget-class.md#register)を呼び出して、ドラッグアンドドロップ操作のコントロールを登録します。

## <a name="see-also"></a>参照

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[OLE ドラッグアンドドロップ](../../mfc/drag-and-drop-ole.md)
