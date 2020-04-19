---
title: CCubicTransition クラス
ms.date: 11/04/2016
f1_keywords:
- CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::CCubicTransition
- AFXANIMATIONCONTROLLER/CCubicTransition::Create
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CCubicTransition::m_dblFinalVelocity
- AFXANIMATIONCONTROLLER/CCubicTransition::m_duration
helpviewer_keywords:
- CCubicTransition [MFC], CCubicTransition
- CCubicTransition [MFC], Create
- CCubicTransition [MFC], m_dblFinalValue
- CCubicTransition [MFC], m_dblFinalVelocity
- CCubicTransition [MFC], m_duration
ms.assetid: 4fc30e9c-160c-45e1-bdbe-51adf8fee9c5
ms.openlocfilehash: b6bb626f944ce87748809a5eb03a6f06f92c3de5
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507140"
---
# <a name="ccubictransition-class"></a>CCubicTransition クラス

3 次遷移をカプセル化します。

## <a name="syntax"></a>構文

```
class CCubicTransition : public CBaseTransition;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CCubicTransition:: CCubicTransition](#ccubictransition)|遷移オブジェクトを構築し、そのパラメーターを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CCubicTransition::Create](#create)|遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。 ( [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)をオーバーライドします)。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CCubicTransition:: m_dblFinalValue](#m_dblfinalvalue)|遷移の終了時のアニメーション変数の値。|
|[CCubicTransition:: m_dblFinalVelocity](#m_dblfinalvelocity)|遷移の終了時の変数の速度。|
|[CCubicTransition:: m_duration](#m_duration)|遷移の継続時間。|

## <a name="remarks"></a>Remarks

3次遷移では、アニメーション変数の値は、その初期値から、指定された速度で終了する遷移の期間にわたって、指定された最終的な値に変わります。 すべての遷移は自動的にクリアされるため、operator new を使用して割り当てることをお勧めします。 カプセル化された IuiAnimateGroup 遷移 COM オブジェクトは、次に NULL になるまで、CAnimationController:: によって作成されます。 この COM オブジェクトの作成後にメンバー変数を変更しても効果はありません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCubicTransition`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="ccubictransition"></a>  CCubicTransition::CCubicTransition

遷移オブジェクトを構築し、そのパラメーターを初期化します。

```
CCubicTransition(
    UI_ANIMATION_SECONDS duration,
    DOUBLE finalValue,
    DOUBLE finalVelocity);
```

### <a name="parameters"></a>パラメーター

*duration*<br/>
遷移の継続時間。

*finalValue*<br/>
遷移の終了時のアニメーション変数の値。

*finalVelocity*<br/>
遷移の終了時の変数の速度。

##  <a name="create"></a>  CCubicTransition::Create

遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>パラメーター

*pLibrary*<br/>
標準遷移のライブラリを定義する、 [Iuiの遷移 Tionlibrary インターフェイス](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)へのポインター。

### <a name="return-value"></a>戻り値

移行が正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="m_dblfinalvalue"></a>  CCubicTransition::m_dblFinalValue

遷移の終了時のアニメーション変数の値。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblfinalvelocity"></a>  CCubicTransition::m_dblFinalVelocity

遷移の終了時の変数の速度。

```
DOUBLE m_dblFinalVelocity;
```

##  <a name="m_duration"></a>CCubicTransition:: m_duration

遷移の継続時間。

```
UI_ANIMATION_SECONDS m_duration;
```

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
