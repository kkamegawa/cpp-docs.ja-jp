---
title: CInstantaneousTransition クラス
ms.date: 11/04/2016
f1_keywords:
- CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::CInstantaneousTransition
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::Create
- AFXANIMATIONCONTROLLER/CInstantaneousTransition::m_dblFinalValue
helpviewer_keywords:
- CInstantaneousTransition [MFC], CInstantaneousTransition
- CInstantaneousTransition [MFC], Create
- CInstantaneousTransition [MFC], m_dblFinalValue
ms.assetid: c3d5121f-2c6b-4221-9e57-10e082a31120
ms.openlocfilehash: f3861bbbc0fc138dcb0f2a8b969ed9bde41335bd
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505934"
---
# <a name="cinstantaneoustransition-class"></a>CInstantaneousTransition クラス

即時遷移をカプセル化します。

## <a name="syntax"></a>構文

```
class CInstantaneousTransition : public CBaseTransition;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CInstantaneousTransition:: CInstantaneousTransition](#cinstantaneoustransition)|遷移オブジェクトを構築し、その最終的な値を初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CInstantaneousTransition::Create](#create)|遷移ライブラリを呼び出して、カプセル化された遷移 COM オブジェクトを作成します。 ( [Cbasetransition:: Create](../../mfc/reference/cbasetransition-class.md#create)をオーバーライドします)。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CInstantaneousTransition::m_dblFinalValue](#m_dblfinalvalue)|遷移の終了時のアニメーション変数の値。|

## <a name="remarks"></a>Remarks

瞬時の遷移中に、アニメーション変数の値が現在の値から指定した最終的な値に瞬時に変化します。 この遷移の期間は常に0です。 すべての遷移は自動的にクリアされるため、operator new を使用して割り当てることをお勧めします。 カプセル化された IuiAnimateGroup 遷移 COM オブジェクトは、次に NULL になるまで、CAnimationController:: によって作成されます。 この COM オブジェクトの作成後にメンバー変数を変更しても効果はありません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

[CInstantaneousTransition](../../mfc/reference/cinstantaneoustransition-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="cinstantaneoustransition"></a>CInstantaneousTransition:: CInstantaneousTransition

遷移オブジェクトを構築し、その最終的な値を初期化します。

```
CInstantaneousTransition(DOUBLE dblFinalValue);
```

### <a name="parameters"></a>パラメーター

*dblFinalValue*<br/>
遷移の終了時のアニメーション変数の値。

##  <a name="create"></a>  CInstantaneousTransition::Create

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

##  <a name="m_dblfinalvalue"></a>  CInstantaneousTransition::m_dblFinalValue

遷移の終了時のアニメーション変数の値。

```
DOUBLE m_dblFinalValue;
```

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
