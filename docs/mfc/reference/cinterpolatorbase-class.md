---
title: CInterpolatorBase クラス
ms.date: 11/04/2016
f1_keywords:
- CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CInterpolatorBase
- AFXANIMATIONCONTROLLER/CInterpolatorBase::CreateInstance
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDependencies
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::GetFinalValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateValue
- AFXANIMATIONCONTROLLER/CInterpolatorBase::InterpolateVelocity
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetCustomInterpolator
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetDuration
- AFXANIMATIONCONTROLLER/CInterpolatorBase::SetInitialValueAndVelocity
helpviewer_keywords:
- CInterpolatorBase [MFC], CInterpolatorBase
- CInterpolatorBase [MFC], CreateInstance
- CInterpolatorBase [MFC], GetDependencies
- CInterpolatorBase [MFC], GetDuration
- CInterpolatorBase [MFC], GetFinalValue
- CInterpolatorBase [MFC], InterpolateValue
- CInterpolatorBase [MFC], InterpolateVelocity
- CInterpolatorBase [MFC], SetCustomInterpolator
- CInterpolatorBase [MFC], SetDuration
- CInterpolatorBase [MFC], SetInitialValueAndVelocity
ms.assetid: bbc3dce7-8398-47f9-b97e-e4fd2d737232
ms.openlocfilehash: d1fc675b1014ab9a099e8310b52b7458f2bff65f
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/09/2019
ms.locfileid: "68916193"
---
# <a name="cinterpolatorbase-class"></a>CInterpolatorBase クラス

アニメーション変数の新しい値を計算する必要があるときに、Animation API によって呼び出されるコールバックを実装します。

## <a name="syntax"></a>構文

```
class CInterpolatorBase : public CUIAnimationInterpolatorBase<CInterpolatorBase>;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CInterpolatorBase:: CInterpolatorBase](#cinterpolatorbase)|オブジェクトを`CInterpolatorBase`構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CInterpolatorBase::CreateInstance](#createinstance)|のインスタンスを作成`CInterpolatorBase`し、カスタム interpolator へのポインターを格納します。これは、イベントを処理します。|
|[CInterpolatorBase::GetDependencies](#getdependencies)|Interpolator の依存関係を取得します。 ( `CUIAnimationInterpolatorBase::GetDependencies`をオーバーライドします)。|
|[CInterpolatorBase:: GetDuration](#getduration)|Interpolator の継続時間を取得します。 ( `CUIAnimationInterpolatorBase::GetDuration`をオーバーライドします)。|
|[CInterpolatorBase:: GetFinalValue](#getfinalvalue)|Interpolator が潜在顧客の最終的な値を取得します。 ( `CUIAnimationInterpolatorBase::GetFinalValue`をオーバーライドします)。|
|[CInterpolatorBase::InterpolateValue](#interpolatevalue)|指定されたオフセットで値を補`CUIAnimationInterpolatorBase::InterpolateValue`間します (をオーバーライドします)。|
|[CInterpolatorBase::InterpolateVelocity](#interpolatevelocity)|指定されたオフセットで速度を補`CUIAnimationInterpolatorBase::InterpolateVelocity`間します (オーバーライドします)。|
|[CInterpolatorBase:: SetCustomInterpolator](#setcustominterpolator)|イベントを処理するカスタム interpolator へのポインターを格納します。|
|[CInterpolatorBase:: SetDuration](#setduration)|Interpolator の継続時間 (オーバーライド`CUIAnimationInterpolatorBase::SetDuration`) を設定します。|
|[CInterpolatorBase:: SetInitialValueAndVelocity](#setinitialvalueandvelocity)|Interpolator の初期値とベロシティを設定します。 ( `CUIAnimationInterpolatorBase::SetInitialValueAndVelocity`をオーバーライドします)。|

## <a name="remarks"></a>Remarks

このハンドラーは、 `IUIAnimationTransitionFactory::CreateTransition` `CCustomTransition`オブジェクトがアニメーション初期化プロセスの一部として作成されるときに、によって`CAnimationController::AnimateGroup`作成され、に渡されます (から開始)。 通常、このクラスを直接使用する必要はありません。すべてのイベントを`CCustomInterpolator`派生クラスにルーティングするだけで、そのポインターは`CCustomTransition`のコンストラクターに渡されます。

## <a name="inheritance-hierarchy"></a>継承階層

`CUIAnimationCallbackBase`

`CUIAnimationInterpolatorBase`

`CInterpolatorBase`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="cinterpolatorbase"></a>CInterpolatorBase:: CInterpolatorBase

CInterpolatorBase オブジェクトを構築します。

```
CInterpolatorBase();
```

##  <a name="createinstance"></a>  CInterpolatorBase::CreateInstance

CInterpolatorBase のインスタンスを作成し、カスタム interpolator へのポインターを格納します。これは、イベントを処理します。

```
static COM_DECLSPEC_NOTHROW HRESULT CreateInstance(
    CCustomInterpolator* pInterpolator,
    IUIAnimationInterpolator** ppHandler);
```

### <a name="parameters"></a>パラメーター

*pInterpolator*<br/>
カスタム interpolator へのポインター。

*ppHandler*<br/>
Output. 関数がを返したときの CInterpolatorBase のインスタンスへのポインターを格納します。

### <a name="return-value"></a>戻り値

##  <a name="getdependencies"></a>  CInterpolatorBase::GetDependencies

Interpolator の依存関係を取得します。

```
IFACEMETHOD(GetDependencies)(
    __out UI_ANIMATION_DEPENDENCIES* initialValueDependencies,
    __out UI_ANIMATION_DEPENDENCIES* initialVelocityDependencies,
    __out UI_ANIMATION_DEPENDENCIES* durationDependencies);
```

### <a name="parameters"></a>パラメーター

*initialValueDependencies*<br/>
Output. SetInitialValueAndVelocity に渡される初期値に依存する interpolator の側面。

*initialVelocityDependencies*<br/>
Output. SetInitialValueAndVelocity に渡される初期速度に依存する interpolator の側面。

*durationDependencies*<br/>
Output. SetDuration に渡された期間に依存する interpolator の側面。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 CCustomInterpolator が設定されていない場合、またはカスタム実装が GetDependencies メソッドから FALSE を返す場合は、E_FAIL を返します。

##  <a name="getduration"></a>CInterpolatorBase:: GetDuration

Interpolator の継続時間を取得します。

```
IFACEMETHOD(GetDuration)(__out UI_ANIMATION_SECONDS* duration);
```

### <a name="parameters"></a>パラメーター

*duration*<br/>
Output. 遷移の期間 (秒単位)。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 CCustomInterpolator が設定されていない場合、またはカスタム実装が GetDuration メソッドから FALSE を返す場合は、E_FAIL を返します。

##  <a name="getfinalvalue"></a>  CInterpolatorBase::GetFinalValue

Interpolator が潜在顧客の最終的な値を取得します。

```
IFACEMETHOD(GetFinalValue)(__out DOUBLE* value);
```

### <a name="parameters"></a>パラメーター

*value*<br/>
Output. 遷移の終了時の変数の最終的な値。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 CCustomInterpolator が設定されていない場合、またはカスタム実装が GetFinalValue メソッドから FALSE を返す場合は、E_FAIL を返します。

##  <a name="interpolatevalue"></a>  CInterpolatorBase::InterpolateValue

指定されたオフセットで値を補間します。

```
IFACEMETHOD(InterpolateValue)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* value);
```

### <a name="parameters"></a>パラメーター

*オフセット*<br/>
遷移の開始からのオフセット。 オフセットは、常に0以上、移行の継続時間よりも短くなります。 遷移の継続時間が0の場合、このメソッドは呼び出されません。

*value*<br/>
Output. 補間値。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 CCustomInterpolator が設定されていない場合、またはカスタム実装が InterpolateValue メソッドから FALSE を返す場合は、E_FAIL を返します。

##  <a name="interpolatevelocity"></a>  CInterpolatorBase::InterpolateVelocity

指定されたオフセットで速度を補間します。

```
IFACEMETHOD(InterpolateVelocity)(
    __in UI_ANIMATION_SECONDS offset,
    __out DOUBLE* velocity);
```

### <a name="parameters"></a>パラメーター

*オフセット*<br/>
遷移の開始からのオフセット。 オフセットは、常に0以上、移行の期間以下であることを示します。 遷移の継続時間が0の場合、このメソッドは呼び出されません。

*報酬*<br/>
Output. オフセット位置の変数の速度。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 CCustomInterpolator が設定されていない場合、またはカスタム実装が InterpolateVelocity メソッドから FALSE を返す場合は、E_FAIL を返します。

##  <a name="setcustominterpolator"></a>  CInterpolatorBase::SetCustomInterpolator

イベントを処理するカスタム interpolator へのポインターを格納します。

```
void SetCustomInterpolator(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>パラメーター

*pInterpolator*<br/>
カスタム interpolator へのポインター。

##  <a name="setduration"></a>CInterpolatorBase:: SetDuration

Interpolator の継続時間を設定します。

```
IFACEMETHOD(SetDuration)(__in UI_ANIMATION_SECONDS duration);
```

### <a name="parameters"></a>パラメーター

*duration*<br/>
遷移の継続時間。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 CCustomInterpolator が設定されていない場合、またはカスタム実装が SetDuration メソッドから FALSE を返す場合は、E_FAIL を返します。

##  <a name="setinitialvalueandvelocity"></a>CInterpolatorBase:: SetInitialValueAndVelocity

Interpolator の初期値とベロシティを設定します。

```
IFACEMETHOD(SetInitialValueAndVelocity)(
    __in DOUBLE initialValue,
    __in DOUBLE initialVelocity);
```

### <a name="parameters"></a>パラメーター

*initialValue*<br/>
遷移の開始時の変数の値。

*初期速度*<br/>
遷移の開始時の変数の速度。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、S_OK を返します。 CCustomInterpolator が設定されていない場合、またはカスタム実装が SetInitialValueAndVelocity メソッドから FALSE を返す場合は、E_FAIL を返します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
