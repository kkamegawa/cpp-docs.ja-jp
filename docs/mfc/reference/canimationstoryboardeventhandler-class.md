---
title: CAnimationStoryboardEventHandler クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::CreateInstance
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardStatusChanged
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::OnStoryboardUpdated
- AFXANIMATIONCONTROLLER/CAnimationStoryboardEventHandler::SetAnimationController
helpviewer_keywords:
- CAnimationStoryboardEventHandler [MFC], CAnimationStoryboardEventHandler
- CAnimationStoryboardEventHandler [MFC], CreateInstance
- CAnimationStoryboardEventHandler [MFC], OnStoryboardStatusChanged
- CAnimationStoryboardEventHandler [MFC], OnStoryboardUpdated
- CAnimationStoryboardEventHandler [MFC], SetAnimationController
ms.assetid: 10a7e86b-c02d-4124-9a2e-61ecf8ac62fc
ms.openlocfilehash: d12f38491cf3aafca41756ce97e1cad44deb67d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338260"
---
# <a name="canimationstoryboardeventhandler-class"></a>CAnimationStoryboardEventHandler クラス

ストーリーボードのステータスの変更時またはストーリーボードの更新時に Animation API によって呼び出されるコールバックを実装します。

## <a name="syntax"></a>構文

```
class CAnimationStoryboardEventHandler : public CUIAnimationStoryboardEventHandlerBase<CAnimationStoryboardEventHandler>;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler](#canimationstoryboardeventhandler)|`CAnimationStoryboardEventHandler` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationStoryboardEventHandler::CreateInstance](#createinstance)|インスタンスを作成します`CAnimationStoryboardEventHandler`コールバック。|
|[CAnimationStoryboardEventHandler::OnStoryboardStatusChanged](#onstoryboardstatuschanged)|処理`OnStoryboardStatusChanged`イベントで、ストーリー ボードの状態が変更されたときに発生する (上書き`CUIAnimationStoryboardEventHandlerBase::OnStoryboardStatusChanged`)。|
|[CAnimationStoryboardEventHandler::OnStoryboardUpdated](#onstoryboardupdated)|処理`OnStoryboardUpdated`イベントで、ストーリー ボードが更新されたときに発生する (上書き`CUIAnimationStoryboardEventHandlerBase::OnStoryboardUpdated`)。|
|[CAnimationStoryboardEventHandler::SetAnimationController](#setanimationcontroller)|イベントをルーティングするアニメーション コント ローラーへのポインターを格納します。|

## <a name="remarks"></a>Remarks

このイベント ハンドラーが作成されに渡される`IUIAnimationStoryboard::SetStoryboardEventHandler`メソッドを呼び出すときに`CAnimationController::EnableStoryboardEventHandler`します。

## <a name="inheritance-hierarchy"></a>継承階層

`CUIAnimationCallbackBase`

`CUIAnimationStoryboardEventHandlerBase`

`CAnimationStoryboardEventHandler`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="canimationstoryboardeventhandler"></a>  CAnimationStoryboardEventHandler::CAnimationStoryboardEventHandler

CAnimationStoryboardEventHandler オブジェクトを構築します。

```
CAnimationStoryboardEventHandler();
```

##  <a name="createinstance"></a>  CAnimationStoryboardEventHandler::CreateInstance

CAnimationStoryboardEventHandler コールバックのインスタンスを作成します。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CAnimationController* pAnimationController,
    IUIAnimationStoryboardEventHandler** ppHandler);
```

### <a name="parameters"></a>パラメーター

*pAnimationController*<br/>
イベントを受信するアニメーション コント ローラーへのポインター。

*ppHandler*

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="onstoryboardstatuschanged"></a>  CAnimationStoryboardEventHandler::OnStoryboardStatusChanged

ストーリー ボードの状態が変更されたときに発生する OnStoryboardStatusChanged イベントを処理します。

```
IFACEMETHOD(OnStoryboardStatusChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in UI_ANIMATION_STORYBOARD_STATUS newStatus,
    __in UI_ANIMATION_STORYBOARD_STATUS previousStatus);
```

### <a name="parameters"></a>パラメーター

*ストーリー ボード*<br/>
状態が変更されたストーリー ボードへのポインター。

*newStatus*<br/>
新しいストーリー ボードの状態を指定します。

*previousStatus*<br/>
以前のストーリー ボードの状態を指定します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は s_ok を返します。それ以外の場合 E_FAIL します。

##  <a name="onstoryboardupdated"></a>  CAnimationStoryboardEventHandler::OnStoryboardUpdated

ストーリー ボードが更新されたときに発生する OnStoryboardUpdated イベントを処理します。

```
IFACEMETHOD(OnStoryboardUpdated) (__in IUIAnimationStoryboard* storyboard);
```

### <a name="parameters"></a>パラメーター

*ストーリー ボード*<br/>
更新された、ストーリー ボードへのポインター。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は s_ok を返します。それ以外の場合 E_FAIL します。

##  <a name="setanimationcontroller"></a>  CAnimationStoryboardEventHandler::SetAnimationController

イベントをルーティングするアニメーション コント ローラーへのポインターを格納します。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>パラメーター

*pAnimationController*<br/>
イベントを受信するアニメーション コント ローラーへのポインター。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
