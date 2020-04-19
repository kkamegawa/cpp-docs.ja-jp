---
title: CDiscreteTransition クラス
ms.date: 11/04/2016
f1_keywords:
- CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::CDiscreteTransition
- AFXANIMATIONCONTROLLER/CDiscreteTransition::Create
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_dblFinalValue
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_delay
- AFXANIMATIONCONTROLLER/CDiscreteTransition::m_hold
helpviewer_keywords:
- CDiscreteTransition [MFC], CDiscreteTransition
- CDiscreteTransition [MFC], Create
- CDiscreteTransition [MFC], m_dblFinalValue
- CDiscreteTransition [MFC], m_delay
- CDiscreteTransition [MFC], m_hold
ms.assetid: b4d84fb3-ccaa-451c-a69b-6b50dcb9b9c8
ms.openlocfilehash: 7087dfa13972737f0a1244d2cc9a7088b23dc184
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506863"
---
# <a name="cdiscretetransition-class"></a>CDiscreteTransition クラス

不連続遷移をカプセル化します。

## <a name="syntax"></a>構文

```
class CDiscreteTransition : public CBaseTransition;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDiscreteTransition:: CDiscreteTransition](#cdiscretetransition)|離散遷移オブジェクトを構築し、そのパラメーターを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDiscreteTransition:: Create](#create)|遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。 ( [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)をオーバーライドします)。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CDiscreteTransition:: m_dblFinalValue](#m_dblfinalvalue)|遷移の終了時のアニメーション変数の値。|
|[CDiscreteTransition:: m_delay](#m_delay)|瞬間的なスイッチが最終的な値になるのを待機する時間。|
|[CDiscreteTransition:: m_hold](#m_hold)|変数が最終的な値に保持される時間の長さ。|

## <a name="remarks"></a>Remarks

個別の遷移では、アニメーション変数は指定された遅延時間の初期値のままになり、その後すぐに指定された最終値に切り替えられ、一定の期間、その値のままになります。 すべての遷移は自動的にクリアされるため、operator new を使用して割り当てることをお勧めします。 カプセル化された IuiAnimateGroup 遷移 COM オブジェクトは、次に NULL になるまで、CAnimationController:: によって作成されます。 この COM オブジェクトの作成後にメンバー変数を変更しても効果はありません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CDiscreteTransition](../../mfc/reference/cdiscretetransition-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="cdiscretetransition"></a>CDiscreteTransition:: CDiscreteTransition

離散遷移オブジェクトを構築し、そのパラメーターを初期化します。

```
CDiscreteTransition(
    UI_ANIMATION_SECONDS delay,
    DOUBLE dblFinalValue,
    UI_ANIMATION_SECONDS hold);
```

### <a name="parameters"></a>パラメーター

*よる*<br/>
瞬間的なスイッチが最終的な値になるのを待機する時間。

*dblFinalValue*<br/>
遷移の終了時のアニメーション変数の値。

*まま*<br/>
変数が最終的な値に保持される時間の長さ。

##  <a name="create"></a>  CDiscreteTransition::Create

遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

*pLibrary*<br/>
標準遷移のライブラリを定義する、 [Iuiの遷移 Tionlibrary インターフェイス](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)へのポインター。

### <a name="return-value"></a>戻り値

移行が正常に作成された場合は TRUE。それ以外の場合は FALSE。

##  <a name="m_dblfinalvalue"></a>  CDiscreteTransition::m_dblFinalValue

遷移の終了時のアニメーション変数の値。

```
DOUBLE m_dblFinalValue;
```

##  <a name="m_delay"></a>CDiscreteTransition:: m_delay

瞬間的なスイッチが最終的な値になるのを待機する時間。

```
UI_ANIMATION_SECONDS m_delay;
```

##  <a name="m_hold"></a>CDiscreteTransition:: m_hold

変数が最終的な値に保持される時間の長さ。

```
UI_ANIMATION_SECONDS m_hold;
```

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
