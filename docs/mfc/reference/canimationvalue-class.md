---
title: CAnimationValue クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::CAnimationValue
- AFXANIMATIONCONTROLLER/CAnimationValue::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationValue::GetValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationValue::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationValue::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationValue::m_value
helpviewer_keywords:
- CAnimationValue [MFC], CAnimationValue
- CAnimationValue [MFC], AddTransition
- CAnimationValue [MFC], GetValue
- CAnimationValue [MFC], GetVariable
- CAnimationValue [MFC], SetDefaultValue
- CAnimationValue [MFC], GetAnimationVariableList
- CAnimationValue [MFC], m_value
ms.assetid: 78c5ae19-ede5-4f20-bfbe-68b467b603c2
ms.openlocfilehash: 86a2caa8946bcafeabf85687a24b2430ecefe790
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338689"
---
# <a name="canimationvalue-class"></a>CAnimationValue クラス

1 つの値を持つアニメーション オブジェクトの機能を実装します。

## <a name="syntax"></a>構文

```
class CAnimationValue : public CAnimationBaseObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationValue::CAnimationValue](#canimationvalue)|オーバーロードされます。 CAnimationValue オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationValue::AddTransition](#addtransition)|値に適用するへの移行を追加します。|
|[CAnimationValue::GetValue](#getvalue)|オーバーロードされます。 現在の値を取得します。|
|[CAnimationValue::GetVariable](#getvariable)|カプセル化されたアニメーション変数へのアクセスを提供します。|
|[CAnimationValue::SetDefaultValue](#setdefaultvalue)|既定値を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationValue::GetAnimationVariableList](#getanimationvariablelist)|カプセル化されたアニメーション変数リストに配置します。 (上書き[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist))。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAnimationValue::operator 倍](#operator_double)|CAnimationValue と double 型の間の変換を提供します。|
|[CAnimationValue::operator INT32](#operator_int32)|CAnimationValue と INT32 との間の変換を提供します。|
|[CAnimationValue::operator=](#operator_eq)|オーバーロードされます。 CAnimationValue に INT32 値を割り当てます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationValue::m_value](#m_value)|アニメーション値を表すアニメーションをカプセル化された変数です。|

## <a name="remarks"></a>Remarks

CAnimationValue クラスは、1 つの CAnimationVariable オブジェクトをカプセル化し、アプリケーションで単一のアニメーション化された値を表すことができます。 アニメーションの透過性 (フェード効果) の角度 (オブジェクトを回転させる) をこのクラスを使用するなど、それ以外の場合、1 つのアニメーション化された値によってアニメーションを作成する必要がある場合。 アプリケーションでこのクラスを使用するには、だけこのクラスのオブジェクトをインスタンス化、CAnimationController::AddAnimationObject を使用してアニメーション コント ローラーに追加し、値に適用される各遷移の AddTransition を呼び出します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationValue`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationValue::AddTransition

値に適用するへの移行を追加します。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>パラメーター

*pTransition*<br/>
移行のオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

切り替え効果をアニメーション変数に適用する遷移の内部リストに追加するには、この関数を呼び出します。 遷移を追加するとすぐに適用され、内部リストに格納されているはありません。 遷移を (特定の値のストーリー ボードに追加された) に適用されます CAnimationController::AnimateGroup を呼び出すとします。

##  <a name="canimationvalue"></a>  CAnimationValue::CAnimationValue

CAnimationValue オブジェクトを構築します。

```
CAnimationValue();

CAnimationValue(
    DOUBLE dblDefaultValue,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>パラメーター

*dblDefaultValue*<br/>
既定値を指定します。

*nGroupID*<br/>
グループ ID を指定します

*nObjectID*<br/>
オブジェクト ID を指定します

*dwUserData*<br/>
ユーザー定義データを指定します。

### <a name="remarks"></a>Remarks

既定のプロパティを持つ CAnimationValue オブジェクトを作成します。 グループ ID とオブジェクト ID の既定値は 0 に設定されます。

##  <a name="getanimationvariablelist"></a>  CAnimationValue::GetAnimationVariableList

カプセル化されたアニメーション変数リストに配置します。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>パラメーター

*lst*<br/>
関数から制御が戻るときにアニメーション化された値を表す CAnimationVariable へのポインターが含まれています。

##  <a name="getvalue"></a>  CAnimationValue::GetValue

現在の値を取得します。

```
BOOL GetValue(DOUBLE& dblValue);
BOOL GetValue(INT32& nValue);
```

### <a name="parameters"></a>パラメーター

*dblValue*<br/>
出力します。 関数が返されるときにアニメーション変数の現在の値が含まれています。

*nValue*<br/>
出力します。 関数が返されるときにアニメーション変数の現在の値が含まれています。

### <a name="return-value"></a>戻り値

現在の値が正常に取得された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

現在の値を取得するには、この関数を呼び出します。 この実装では、カプセル化された COM オブジェクトを呼び出すし、呼び出しが失敗した場合、このメソッドはコンス トラクター、または SetDefaultValue で設定されている既定値を返します。

##  <a name="getvariable"></a>  CAnimationValue::GetVariable

カプセル化されたアニメーション変数へのアクセスを提供します。

```
CAnimationVariable& GetVariable();
```

### <a name="return-value"></a>戻り値

カプセル化されたアニメーション変数への参照。

### <a name="remarks"></a>Remarks

カプセル化されたアニメーション変数にアクセスするのにには、このメソッドを使用します。 CAnimationVariable からアニメーション変数が作成されていない場合、ポインターが NULL を指定できます、IUIAnimationVariable の基になるオブジェクトへのアクセスを取得します。

##  <a name="m_value"></a>  CAnimationValue::m_value

アニメーション値を表すアニメーションをカプセル化された変数です。

```
CAnimationVariable m_value;
```

##  <a name="operator_double"></a>  CAnimationValue::operator DOUBLE

CAnimationValue と double 型の間の変換を提供します。

```
operator DOUBLE();
```

### <a name="return-value"></a>戻り値

アニメーションの値の現在の値。

### <a name="remarks"></a>Remarks

CAnimationValue と double 型の間の変換を提供します。 内部的には、このメソッドは、GetValue の呼び出しし、エラーをチェックしません。 GetValue が失敗した場合、返される値は、コンス トラクター、または SetDefaultValue で以前に設定された既定値が含まれます。

##  <a name="operator_int32"></a>  CAnimationValue::operator INT32

CAnimationValue と INT32 との間の変換を提供します。

```
operator INT32();
```

### <a name="return-value"></a>戻り値

整数として値をアニメーションの現在の値。

### <a name="remarks"></a>Remarks

CAnimationValue と INT32 との間の変換を提供します。 内部的には、このメソッドは、GetValue の呼び出しし、エラーをチェックしません。 GetValue が失敗した場合、返される値は、コンス トラクター、または SetDefaultValue で以前に設定された既定値が含まれます。

##  <a name="operator_eq"></a>  CAnimationValue::operator=

CAnimationValue を double 型の値を割り当てます。

```
void operator=(DOUBLE dblVal);
void operator=(INT32 nVal);
```

### <a name="parameters"></a>パラメーター

*dblVal*<br/>
アニメーションの値に割り当てられる値を指定します。

*nVal*<br/>
アニメーションの値に割り当てられる値を指定します。

### <a name="remarks"></a>Remarks

CAnimationValue を double 型の値を割り当てます。 この値は、カプセル化されたアニメーション変数の既定値として設定されます。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

##  <a name="setdefaultvalue"></a>  CAnimationValue::SetDefaultValue

既定値を設定します。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>パラメーター

*dblDefaultValue*<br/>
既定値を指定します。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、既定値を設定できます。 既定値は、アニメーションが開始されていない、基になる COM オブジェクトが作成されていないときに、アプリケーションに返されます。 CAnimationVarible にカプセル化された、基になる COM オブジェクトが既に作成されている場合、このメソッドで再作成、そのため、もう一度 EnableValueChanged/EnableIntegerValueChanged メソッドを呼び出す必要があります。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
