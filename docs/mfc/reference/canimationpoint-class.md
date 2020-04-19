---
title: CAnimationPoint クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::CAnimationPoint
- AFXANIMATIONCONTROLLER/CAnimationPoint::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetX
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetY
- AFXANIMATIONCONTROLLER/CAnimationPoint::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_xValue
- AFXANIMATIONCONTROLLER/CAnimationPoint::m_yValue
helpviewer_keywords:
- CAnimationPoint [MFC], CAnimationPoint
- CAnimationPoint [MFC], AddTransition
- CAnimationPoint [MFC], GetDefaultValue
- CAnimationPoint [MFC], GetValue
- CAnimationPoint [MFC], GetX
- CAnimationPoint [MFC], GetY
- CAnimationPoint [MFC], SetDefaultValue
- CAnimationPoint [MFC], GetAnimationVariableList
- CAnimationPoint [MFC], m_xValue
- CAnimationPoint [MFC], m_yValue
ms.assetid: 5dc4d46f-e695-4681-b15c-544b78b3e317
ms.openlocfilehash: 15f06d2fa3478570d2f784879a13e7b68515e746
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218539"
---
# <a name="canimationpoint-class"></a>CAnimationPoint クラス

座標をアニメーション化できる点の機能を実装します。

## <a name="syntax"></a>構文

```
class CAnimationPoint : public CAnimationBaseObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationPoint::CAnimationPoint](#canimationpoint)|オーバーロードされます。 CAnimationPoint オブジェクトを作成します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationPoint::AddTransition](#addtransition)|X の遷移を追加します。 座標と Y 座標。|
|[CAnimationPoint::GetDefaultValue](#getdefaultvalue)|既定値を返しますの X 座標と Y 座標。|
|[CAnimationPoint::GetValue](#getvalue)|現在の値を返します。|
|[CAnimationPoint::GetX](#getx)|X 座標の CAnimationVariable へのアクセスを提供します。|
|[CAnimationPoint::GetY](#gety)|CAnimationVariable する Y 座標でのアクセスを提供します。|
|[CAnimationPoint::SetDefaultValue](#setdefaultvalue)|既定値を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationPoint::GetAnimationVariableList](#getanimationvariablelist)|カプセル化されたアニメーション変数リストに配置します。 (上書き[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist))。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAnimationPoint::operator CPoint](#operator_cpoint)|CPoint、CAnimationPoint に変換します。|
|[CAnimationPoint::operator=](#operator_eq)|CAnimationPoint ptSrc に割り当てます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationPoint::m_xValue](#m_xvalue)|カプセル化されたアニメーション変数を表す X アニメーション ポイントの座標。|
|[CAnimationPoint::m_yValue](#m_yvalue)|アニメーション ポイントの Y 座標を表すアニメーションをカプセル化された変数です。|

## <a name="remarks"></a>Remarks

CAnimationPoint クラスは、2 つの CAnimationVariable オブジェクトをカプセル化し、アプリケーションでポイントを表すことができます。 たとえば、このクラスを使用すると、(文字列, 円, ポイントなど) など、画面上のオブジェクトの位置をアニメーション化します。 アプリケーションでこのクラスを使用するだけこのクラスのオブジェクトをインスタンス化、CAnimationController::AddAnimationObject を使用してアニメーション コント ローラーに追加および呼び出しに適用される各遷移の AddTransition X または Y 座標。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationPoint`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationPoint::AddTransition

X の遷移を追加します。 座標と Y 座標。

```
void AddTransition(
    CBaseTransition* pXTransition,
    CBaseTransition* pYTransition);
```

### <a name="parameters"></a>パラメーター

*pXTransition*<br/>
X 座標の遷移へのポインター。

*pYTransition*<br/>
Y の遷移へのポインターを調整します。

### <a name="remarks"></a>Remarks

X のアニメーション変数に適用する遷移の内部一覧に指定された遷移を追加するには、この関数を呼び出す座標と Y 座標。 遷移を追加するとすぐに適用され、内部リストに格納されているはありません。 遷移を (特定の値のストーリー ボードに追加された) に適用されます CAnimationController::AnimateGroup を呼び出すとします。 座標のいずれかに遷移を適用する不要な場合は、NULL を渡すことができます。

##  <a name="canimationpoint"></a>  CAnimationPoint::CAnimationPoint

CAnimationPoint オブジェクトを作成します。

```
CAnimationPoint();

CAnimationPoint(
    const CPoint& ptDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>パラメーター

*ptDefault*<br/>
既定のポイントの座標を指定します。

*nGroupID*<br/>
グループ ID を指定します

*nObjectID*<br/>
オブジェクト ID を指定します

*dwUserData*<br/>
ユーザー定義データを指定します。

### <a name="remarks"></a>Remarks

CAnimationPoint オブジェクトは、既定のプロパティを構築します。 既定のポイント座標、グループ ID とオブジェクト ID が 0 に設定されます。

##  <a name="getanimationvariablelist"></a>  CAnimationPoint::GetAnimationVariableList

カプセル化されたアニメーション変数リストに配置します。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*, CAnimationVariable*>& lst);
```

### <a name="parameters"></a>パラメーター

*lst*<br/>
関数から制御が戻るときに、X と Y 座標を表す 2 つの CAnimationVariable オブジェクトへのポインターを格納します。

##  <a name="getdefaultvalue"></a>  CAnimationPoint::GetDefaultValue

既定値を返しますの X 座標と Y 座標。

```
CPoint GetDefaultValue();
```

### <a name="return-value"></a>戻り値

ポイント含んでいる既定値。

### <a name="remarks"></a>Remarks

コンス トラクターまたは SetDefaultValue によって以前に設定された既定値を取得するには、この関数を呼び出します。

##  <a name="getvalue"></a>  CAnimationPoint::GetValue

現在の値を返します。

```
BOOL GetValue(CPoint& ptValue);
```

### <a name="parameters"></a>パラメーター

*ptValue*<br/>
出力します。 このメソッドが戻るときに、現在の値を格納します。

### <a name="return-value"></a>戻り値

現在の値が正常に取得された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

アニメーション ポイントの現在の値を取得するには、この関数を呼び出します。 このメソッドが失敗または基になる COM オブジェクト X と Y 座標が初期化されていない、ptValue には、コンス トラクターまたは SetDefaultValue によって以前に設定された既定値が含まれています。

##  <a name="getx"></a>  CAnimationPoint::GetX

X 座標の CAnimationVariable へのアクセスを提供します。

```
CAnimationVariable& GetX();
```

### <a name="return-value"></a>戻り値

X を表すカプセル化された CAnimationVariable への参照を調整します。

### <a name="remarks"></a>Remarks

X を表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができますを調整します。

##  <a name="gety"></a>  CAnimationPoint::GetY

CAnimationVariable する Y 座標でのアクセスを提供します。

```
CAnimationVariable& GetY();
```

### <a name="return-value"></a>戻り値

Y 座標を表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

Y 座標を表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="m_xvalue"></a>  CAnimationPoint::m_xValue

カプセル化されたアニメーション変数を表す X アニメーション ポイントの座標。

```
CAnimationVariable m_xValue;
```

##  <a name="m_yvalue"></a>  CAnimationPoint::m_yValue

アニメーション ポイントの Y 座標を表すアニメーションをカプセル化された変数です。

```
CAnimationVariable m_yValue;
```

##  <a name="operator_cpoint"></a>  CAnimationPoint::operator CPoint

CPoint、CAnimationPoint に変換します。

```
operator CPoint();
```

### <a name="return-value"></a>戻り値

CAnimationPoint CPoint としての現在の値。

### <a name="remarks"></a>Remarks

この関数は、GetValue を内部的に呼び出します。 返されるポイントが X の既定値を含める GetValue 何らかの理由で失敗した場合、座標と Y 座標。

##  <a name="operator_eq"></a>  CAnimationPoint::operator =

CAnimationPoint ptSrc に割り当てます。

```
void operator=(const CPoint& ptSrc);
```

### <a name="parameters"></a>パラメーター

*ptSrc*<br/>
CPoint またはポイントを指します。

### <a name="remarks"></a>Remarks

CAnimationPoint ptSrc に割り当てます。 いるアニメーションの開始前にこの演算子は、SetDefaultValue を呼び出すため、基になる COM を再作成するオブジェクトの X および Y 座標が作成されている場合に行うことをお勧めします。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

##  <a name="setdefaultvalue"></a>  CAnimationPoint::SetDefaultValue

既定値を設定します。

```
void SetDefaultValue(const POINT& ptDefault);
```

### <a name="parameters"></a>パラメーター

*ptDefault*<br/>
既定のポイント値を指定します。

### <a name="remarks"></a>Remarks

この関数を使用すると、アニメーション オブジェクトを既定値を設定できます。 このメソッドは、割り当てる既定値をアニメーションのポイントの座標 X と Y 座標。 作成した場合は、基になる COM オブジェクトも再作成します。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
