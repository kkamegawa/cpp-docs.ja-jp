---
title: CAccelerateDecelerateTransition クラス
ms.date: 11/04/2016
f1_keywords:
- CAccelerateDecelerateTransition
- afxanimationcontroller/CAccelerateDecelerateTransition
helpviewer_keywords:
- CAccelerateDecelerateTransition class [MFC]
ms.assetid: b1f31ee8-bb11-4ccc-b124-365fb02b025c
ms.openlocfilehash: 1e55e81b4d9b5c324f86bfd141b74d9faa362d94
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507739"
---
# <a name="cacceleratedeceleratetransition-class"></a>CAccelerateDecelerateTransition クラス

加速減速遷移を実装します。

## <a name="syntax"></a>構文

```
class CAccelerateDecelerateTransition : public CBaseTransition;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAccelerateDecelerateTransition::CAccelerateDecelerateTransition](#cacceleratedeceleratetransition)|遷移オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAccelerateDecelerateTransition::Create](#create)|遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。 ( [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)をオーバーライドします)。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAccelerateDecelerateTransition::m_accelerationRatio](#m_accelerationratio)|期間の短縮に費やした時間の比率。|
|[CAccelerateDecelerateTransition::m_decelerationRatio](#m_decelerationratio)|期間に減速に費やされた時間の比率。|
|[CAccelerateDecelerateTransition::m_duration](#m_duration)|遷移の継続時間。|
|[CAccelerateDecelerateTransition::m_finalValue](#m_finalvalue)|遷移の終了時のアニメーション変数の値。|

## <a name="remarks"></a>Remarks

加速減速遷移中、アニメーション変数は、指定された値で終了する遷移の時間を短縮し、減速します。 異なる加速度と減速率を指定することにより、変数を個別に加速および減速する速度を制御できます。 初期速度がゼロの場合、加速率は変数が加速する期間の割合を示します。同様に減速します。 初期速度が0以外の場合は、ベロシティが0に達してから遷移が終了するまでの時間の割合を示します。 加速率と減速率は、最大値の1.0 に合計する必要があります。 すべての遷移は自動的にクリアされるため、operator new を使用して割り当てることをお勧めします。 カプセル化された IuiAnimateGroup 遷移 COM オブジェクトは、次に NULL になるまで、CAnimationController:: によって作成されます。 この COM オブジェクトの作成後にメンバー変数を変更しても効果はありません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CAccelerateDecelerateTransition`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="cacceleratedeceleratetransition"></a>  CAccelerateDecelerateTransition::CAccelerateDecelerateTransition

遷移オブジェクトを構築します。

```
CAccelerateDecelerateTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE accelerationRatio = 0.3,
    DOUBLE decelerationRatio = 0.3);
```

### <a name="parameters"></a>パラメーター

*duration*<br/>
遷移の継続時間。

*finalValue*<br/>
遷移の終了時のアニメーション変数の値。

*accelerationRatio*<br/>
期間の短縮に費やした時間の比率。

*decelerationRatio*<br/>
期間に減速に費やされた時間の比率。

##  <a name="create"></a>  CAccelerateDecelerateTransition::Create

遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* *\not used*\);
```

### <a name="parameters"></a>パラメーター

*pLibrary*<br/>
標準遷移のライブラリを定義する、 [Iuiの遷移 Tionlibrary インターフェイス](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)へのポインター。

### <a name="return-value"></a>戻り値

移行が正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="m_accelerationratio"></a>  CAccelerateDecelerateTransition::m_accelerationRatio

期間の短縮に費やした時間の比率。

```
DOUBLE m_accelerationRatio;
```

##  <a name="m_decelerationratio"></a>CAccelerateDecelerateTransition::m_decelerationRatio

期間に減速に費やされた時間の比率。

```
DOUBLE m_decelerationRatio;
```

##  <a name="m_duration"></a>CAccelerateDecelerateTransition::m_duration

遷移の継続時間。

```
UI_ANIMATION_SECONDS m_duration;
```

##  <a name="m_finalvalue"></a>  CAccelerateDecelerateTransition::m_finalValue

遷移の終了時のアニメーション変数の値。

```
DOUBLE m_finalValue;
```

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
