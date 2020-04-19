---
title: CAnimationVariableChangeHandler クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::OnValueChanged
- AFXANIMATIONCONTROLLER/CAnimationVariableChangeHandler::SetAnimationController
helpviewer_keywords:
- CAnimationVariableChangeHandler [MFC], OnValueChanged
- CAnimationVariableChangeHandler [MFC], SetAnimationController
ms.assetid: 2ea4996d-5c04-4dfc-be79-d42d55050795
ms.openlocfilehash: 92189ce5ea76811496d4462aa4254bbd03ebb219
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338143"
---
# <a name="canimationvariablechangehandler-class"></a>CAnimationVariableChangeHandler クラス

アニメーション変数の値が変化したときに Animation API によって呼び出されるコールバックを実装します。

## <a name="syntax"></a>構文

```
class CAnimationVariableChangeHandler : public CUIAnimationVariableChangeHandlerBase<CAnimationVariableChangeHandler>;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CAnimationVariableChangeHandler`|`CAnimationVariableChangeHandler` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CAnimationVariableChangeHandler::CreateInstance`|インスタンスを作成します`CAnimationVariableChangeHandler`オブジェクト。|
|[CAnimationVariableChangeHandler::OnValueChanged](#onvaluechanged)|アニメーション変数の値が変更されたときに呼び出されます。 ( `CUIAnimationVariableChangeHandlerBase::OnValueChanged`をオーバーライドします)。|
|[CAnimationVariableChangeHandler::SetAnimationController](#setanimationcontroller)|イベントをルーティングするアニメーション コント ローラーへのポインターを格納します。|

## <a name="remarks"></a>Remarks

このイベント ハンドラーが作成されに渡される`IUIAnimationVariable::SetVariableChangeHandler`メソッドを呼び出すときに`CAnimationVariable::EnableValueChangedEvent`または`CAnimationBaseObject::EnableValueChangedEvent`(アニメーション オブジェクトにカプセル化されたすべてのアニメーション変数には、このイベントできます)。

## <a name="inheritance-hierarchy"></a>継承階層

`CUIAnimationCallbackBase`

`CUIAnimationVariableChangeHandlerBase`

`CAnimationVariableChangeHandler`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="onvaluechanged"></a>  CAnimationVariableChangeHandler::OnValueChanged

アニメーション変数の値が変更されたときに呼び出されます。

```
IFACEMETHOD(OnValueChanged) (
    __in IUIAnimationStoryboard* storyboard,
    __in IUIAnimationVariable* variable,
    __in DOUBLE newValue,
    __in DOUBLE previousValue);
```

### <a name="parameters"></a>パラメーター

*ストーリー ボード*<br/>
変数をアニメーション化するストーリー ボード。

*variable*<br/>
更新されたアニメーション変数です。

*newValue*<br/>
新しい値。

*previousValue*<br/>
以前の値。

### <a name="return-value"></a>戻り値

メソッドが成功すると、S_OK を返します。 それ以外の場合、HRESULT エラー コードを返します。

##  <a name="setanimationcontroller"></a>  CAnimationVariableChangeHandler::SetAnimationController

イベントをルーティングするアニメーション コント ローラーへのポインターを格納します。

```
void SetAnimationController(CAnimationController* pAnimationController);
```

### <a name="parameters"></a>パラメーター

*pAnimationController*<br/>
イベントを受信するアニメーション コント ローラーへのポインター。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
