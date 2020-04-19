---
title: CLinearTransitionFromSpeed クラス
ms.date: 11/04/2016
f1_keywords:
- CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::CLinearTransitionFromSpeed
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::Create
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CLinearTransitionFromSpeed::m_dblSpeed
helpviewer_keywords:
- CLinearTransitionFromSpeed [MFC], CLinearTransitionFromSpeed
- CLinearTransitionFromSpeed [MFC], Create
- CLinearTransitionFromSpeed [MFC], m_dblFinalValue
- CLinearTransitionFromSpeed [MFC], m_dblSpeed
ms.assetid: 8f159a1c-8893-4017-951e-09e5758aba7d
ms.openlocfilehash: 50c958a092478f4b9ec4e94f9e5e973a74c334c2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505713"
---
# <a name="clineartransitionfromspeed-class"></a>CLinearTransitionFromSpeed クラス

直線速度遷移をカプセル化します。

## <a name="syntax"></a>構文

```
class CLinearTransitionFromSpeed : public CBaseTransition;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CLinearTransitionFromSpeed:: CLinearTransitionFromSpeed](#clineartransitionfromspeed)|線形速度遷移オブジェクトを構築し、速度と最終的な値で初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CLinearTransitionFromSpeed::Create](#create)|遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。 ( [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)をオーバーライドします)。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CLinearTransitionFromSpeed:: m_dblFinalValue](#m_dblfinalvalue)|遷移の終了時のアニメーション変数の値。|
|[CLinearTransitionFromSpeed:: m_dblSpeed](#m_dblspeed)|変数のベロシティの絶対値。|

## <a name="remarks"></a>Remarks

線形速度遷移では、アニメーション変数の値が指定された速度で変化します。 遷移の期間は、初期値と指定された最終値の差によって決まります。 すべての遷移は自動的にクリアされるため、operator new を使用して割り当てることをお勧めします。 カプセル化された IuiAnimateGroup 遷移 COM オブジェクトは、次に NULL になるまで、CAnimationController:: によって作成されます。 この COM オブジェクトの作成後にメンバー変数を変更しても効果はありません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CLinearTransitionFromSpeed](../../mfc/reference/clineartransitionfromspeed-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="clineartransitionfromspeed"></a>CLinearTransitionFromSpeed:: CLinearTransitionFromSpeed

線形速度遷移オブジェクトを構築し、速度と最終的な値で初期化します。

```
CLinearTransitionFromSpeed(
    DOUBLE dblSpeed,
    DOUBLE dblFinalValue);
```

### <a name="parameters"></a>パラメーター

*dblSpeed*<br/>
変数のベロシティの絶対値。

*dblFinalValue*<br/>
遷移の終了時のアニメーション変数の値。

##  <a name="create"></a>  CLinearTransitionFromSpeed::Create

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

##  <a name="m_dblfinalvalue"></a>CLinearTransitionFromSpeed:: m_dblFinalValue

遷移の終了時のアニメーション変数の値。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_dblspeed"></a>CLinearTransitionFromSpeed:: m_dblSpeed

変数のベロシティの絶対値。

```
DOUBLE m_dblSpeed;
```

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
