---
title: CCustomTransition クラス
ms.date: 11/04/2016
f1_keywords:
- CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::CCustomTransition
- AFXANIMATIONCONTROLLER/CCustomTransition::Create
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::SetInitialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialValueSpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_bInitialVelocitySpecified
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialValue
- AFXANIMATIONCONTROLLER/CCustomTransition::m_initialVelocity
- AFXANIMATIONCONTROLLER/CCustomTransition::m_pInterpolator
helpviewer_keywords:
- CCustomTransition [MFC], CCustomTransition
- CCustomTransition [MFC], Create
- CCustomTransition [MFC], SetInitialValue
- CCustomTransition [MFC], SetInitialVelocity
- CCustomTransition [MFC], m_bInitialValueSpecified
- CCustomTransition [MFC], m_bInitialVelocitySpecified
- CCustomTransition [MFC], m_initialValue
- CCustomTransition [MFC], m_initialVelocity
- CCustomTransition [MFC], m_pInterpolator
ms.assetid: 5bd3f492-940f-4290-a38b-fa68eb8f8401
ms.openlocfilehash: e0e5250b27ce6b902939ebcbfa03bf022a202788
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391284"
---
# <a name="ccustomtransition-class"></a>CCustomTransition クラス

カスタム遷移を実装します。

## <a name="syntax"></a>構文

```
class CCustomTransition : public CBaseTransition;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CCustomTransition::CCustomTransition](#ccustomtransition)|カスタム遷移オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CCustomTransition::Create](#create)|カプセル化された移行 COM オブジェクトを作成する遷移ライブラリを呼び出します。 (上書き[CBaseTransition::Create](../../mfc/reference/cbasetransition-class.md#create))。|
|[CCustomTransition::SetInitialValue](#setinitialvalue)|この遷移に関連付けられているアニメーション変数に適用される最初の値を設定します。|
|[CCustomTransition::SetInitialVelocity](#setinitialvelocity)|この遷移に関連付けられているアニメーション変数に適用される初期の速度を設定します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CCustomTransition::m_bInitialValueSpecified](#m_binitialvaluespecified)|SetInitialValue が初期値を指定するかどうかを指定します。|
|[CCustomTransition::m_bInitialVelocitySpecified](#m_binitialvelocityspecified)|SetInitialVelocity で初期速度を指定するかどうかを指定します。|
|[CCustomTransition::m_initialValue](#m_initialvalue)|初期値を格納します。|
|[CCustomTransition::m_initialVelocity](#m_initialvelocity)|初期速度を格納します。|
|[CCustomTransition::m_pInterpolator](#m_pinterpolator)|カスタム インターポレーターへのポインターを格納します。|

## <a name="remarks"></a>Remarks

CCustomTransitions クラスは、開発者がカスタム遷移を実装するを使用できます。 作成されたので、標準の遷移と使用が、そのコンス トラクターがパラメーターとしてカスタム インターポレーターへのポインターを受け取ります。 カスタム遷移を使用する次の手順に従います。1. CCustomInterpolator からクラスを派生し、実装には少なくとも InterpolateValue メソッド。 2. カスタム インターポレーター オブジェクトの有効期間でなければならないことのアニメーションの期間より長く使用されていることを確認します。 3. CCustomTransition オブジェクト インスタンス (新しい演算子を使用して) し、コンス トラクターでカスタム インターポレーターへのポインターを渡します。 4. これらのパラメーターがカスタム補間の必要な場合は、CCustomTransition::SetInitialValue と CCustomTransition::SetInitialVelocity を呼び出します。 5. アニメーション オブジェクト、カスタム アルゴリズムで値をアニメーション化する AddTransition メソッドにカスタム遷移へのポインターを渡します。 6. アニメーション オブジェクトの値を変更する必要がある場合は、Windows Animation API が CCustomInterpolator でに InterpolateValue (およびその他の関連するメソッド) を呼び出します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseTransition](../../mfc/reference/cbasetransition-class.md)

`CCustomTransition`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="ccustomtransition"></a>  CCustomTransition::CCustomTransition

カスタム遷移オブジェクトを構築します。

```
CCustomTransition(CCustomInterpolator* pInterpolator);
```

### <a name="parameters"></a>パラメーター

*pInterpolator*<br/>
カスタム インターポレーターへのポインター。

##  <a name="create"></a>  CCustomTransition::Create

カプセル化された移行 COM オブジェクトを作成する遷移ライブラリを呼び出します。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* */,
    IUIAnimationTransitionFactory* pFactory);
```

### <a name="parameters"></a>パラメーター

*pFactory*<br/>
カスタム遷移の作成を担当する遷移ファクトリへのポインター。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

このメソッドは、初期値と、この遷移に関連付けられているアニメーション変数に適用する初期速度使用設定できますも。 この目的のため、フレームワーク (CAnimationController::AnimateGroup を呼び出すときに行われます) 遷移をカプセル化された COM オブジェクトを作成する前に、SetInitialValue と SetInitialVelocity を呼び出す必要があります。

##  <a name="m_binitialvaluespecified"></a>  CCustomTransition::m_bInitialValueSpecified

SetInitialValue が初期値を指定するかどうかを指定します。

```
BOOL m_bInitialValueSpecified;
```

##  <a name="m_binitialvelocityspecified"></a>  CCustomTransition::m_bInitialVelocitySpecified

SetInitialVelocity で初期速度を指定するかどうかを指定します。

```
BOOL m_bInitialVelocitySpecified;
```

##  <a name="m_initialvalue"></a>  CCustomTransition::m_initialValue

初期値を格納します。

```
DOUBLE m_initialValue;
```

##  <a name="m_initialvelocity"></a>  CCustomTransition::m_initialVelocity

初期速度を格納します。

```
DOUBLE m_initialVelocity;
```

##  <a name="m_pinterpolator"></a>  CCustomTransition::m_pInterpolator

カスタム インターポレーターへのポインターを格納します。

```
CCustomInterpolator* m_pInterpolator;
```

##  <a name="setinitialvalue"></a>  CCustomTransition::SetInitialValue

この遷移に関連付けられているアニメーション変数に適用される最初の値を設定します。

```
void SetInitialValue(DOUBLE initialValue);
```

### <a name="parameters"></a>パラメーター

*initialValue*

##  <a name="setinitialvelocity"></a>  CCustomTransition::SetInitialVelocity

この遷移に関連付けられているアニメーション変数に適用される初期の速度を設定します。

```
void SetInitialVelocity(DOUBLE initialVelocity);
```

### <a name="parameters"></a>パラメーター

*initialVelocity*

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
