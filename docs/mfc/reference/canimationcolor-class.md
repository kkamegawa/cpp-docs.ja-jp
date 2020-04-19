---
title: CAnimationColor クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::CAnimationColor
- AFXANIMATIONCONTROLLER/CAnimationColor::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationColor::GetB
- AFXANIMATIONCONTROLLER/CAnimationColor::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetG
- AFXANIMATIONCONTROLLER/CAnimationColor::GetR
- AFXANIMATIONCONTROLLER/CAnimationColor::GetValue
- AFXANIMATIONCONTROLLER/CAnimationColor::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationColor::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationColor::m_bValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_gValue
- AFXANIMATIONCONTROLLER/CAnimationColor::m_rValue
helpviewer_keywords:
- CAnimationColor [MFC], CAnimationColor
- CAnimationColor [MFC], AddTransition
- CAnimationColor [MFC], GetB
- CAnimationColor [MFC], GetDefaultValue
- CAnimationColor [MFC], GetG
- CAnimationColor [MFC], GetR
- CAnimationColor [MFC], GetValue
- CAnimationColor [MFC], SetDefaultValue
- CAnimationColor [MFC], GetAnimationVariableList
- CAnimationColor [MFC], m_bValue
- CAnimationColor [MFC], m_gValue
- CAnimationColor [MFC], m_rValue
ms.assetid: 88bfabd4-efeb-4652-87e8-304253d8e48c
ms.openlocfilehash: ee6003a22db78c2a510579c3d717fec887f8a6ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62151176"
---
# <a name="canimationcolor-class"></a>CAnimationColor クラス

赤、緑、および青の各色要素をアニメーション化できる機能を実装します。

## <a name="syntax"></a>構文

```
class CAnimationColor : public CAnimationBaseObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationColor::CAnimationColor](#canimationcolor)|オーバーロードされます。 アニメーションの色オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationColor::AddTransition](#addtransition)|赤、緑、および青のコンポーネントの遷移を追加します。|
|[CAnimationColor::GetB](#getb)|青のコンポーネントを表す CAnimationVariable にアクセスをできます。|
|[CAnimationColor::GetDefaultValue](#getdefaultvalue)|色のコンポーネントの既定値を返します。|
|[CAnimationColor::GetG](#getg)|緑のコンポーネントを表す CAnimationVariable にアクセスをできます。|
|[CAnimationColor::GetR](#getr)|赤のコンポーネントを表す CAnimationVariable にアクセスをできます。|
|[CAnimationColor::GetValue](#getvalue)|現在の値を返します。|
|[CAnimationColor::SetDefaultValue](#setdefaultvalue)|既定値を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationColor::GetAnimationVariableList](#getanimationvariablelist)|カプセル化されたアニメーション変数リストに配置します。 (上書き[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist))。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAnimationColor::operator COLORREF](#operator_colorref)||
|[CAnimationColor::operator=](#operator_eq)|CAnimationColor に色を割り当てます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationColor::m_bValue](#m_bvalue)|アニメーションの色の青のコンポーネントを表すアニメーションをカプセル化された変数です。|
|[CAnimationColor::m_gValue](#m_gvalue)|アニメーションの色の緑のコンポーネントを表すアニメーションをカプセル化された変数です。|
|[CAnimationColor::m_rValue](#m_rvalue)|アニメーションの色の赤の要素を表すアニメーションをカプセル化された変数。|

## <a name="remarks"></a>Remarks

CAnimationColor クラスは、3 つの CAnimationVariable オブジェクトをカプセル化し、アプリケーションでの色を表すことができます。 たとえば、画面上の任意のオブジェクトの色をアニメーション化するこのクラスを使用できます (テキストの色のように背景色など)。 アプリケーションでこのクラスを使用するには、だけこのクラスのオブジェクトをインスタンス化、CAnimationController::AddAnimationObject を使用してアニメーション コント ローラーに追加し、赤、緑、および青のコンポーネントに適用される各遷移の AddTransition を呼び出します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationColor`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationColor::AddTransition

赤、緑、および青のコンポーネントの遷移を追加します。

```
void AddTransition(
    CBaseTransition* pRTransition,
    CBaseTransition* pGTransition,
    CBaseTransition* pBTransition);
```

### <a name="parameters"></a>パラメーター

*pRTransition*<br/>
赤の要素の遷移します。

*pGTransition*<br/>
緑のコンポーネントを遷移します。

*pBTransition*<br/>
青のコンポーネントを遷移します。

### <a name="remarks"></a>Remarks

色のコンポーネントを表すアニメーション変数に適用する遷移の内部一覧に指定された遷移を追加するには、この関数を呼び出します。 遷移を追加するとすぐに適用され、内部リストに格納されているはありません。 遷移を (特定の値のストーリー ボードに追加された) に適用されます CAnimationController::AnimateGroup を呼び出すとします。 色コンポーネントの 1 つに、移行を適用する不要な場合は、NULL を渡すことができます。

##  <a name="canimationcolor"></a>  CAnimationColor::CAnimationColor

CAnimationColor オブジェクトを構築します。

```
CAnimationColor();

CAnimationColor(
    COLORREF color,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
既定の色を指定します。

*nGroupID*<br/>
グループ ID を指定します

*nObjectID*<br/>
オブジェクト ID を指定します

*dwUserData*<br/>
ユーザー定義データを指定します。

### <a name="remarks"></a>Remarks

オブジェクトは、既定値を赤、緑、青、オブジェクト ID とグループ ID は、0 に設定されますで構築されます。 SetDefaultValue と SetID を使用して実行時に後で変更できます。

##  <a name="getanimationvariablelist"></a>  CAnimationColor::GetAnimationVariableList

カプセル化されたアニメーション変数リストに配置します。

```
virtual void GetAnimationVariableList(CList<CAnimationVariable*>& lst);
```

### <a name="parameters"></a>パラメーター

*lst*<br/>
関数から制御が戻るときに、赤、緑、青のコンポーネントを表す 3 つの CAnimationVariable オブジェクトへのポインターを格納します。

##  <a name="getb"></a>  CAnimationColor::GetB

青のコンポーネントを表す CAnimationVariable にアクセスをできます。

```
CAnimationVariable& GetB();
```

### <a name="return-value"></a>戻り値

青のコンポーネントを表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

青のコンポーネントを表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getdefaultvalue"></a>  CAnimationColor::GetDefaultValue

色のコンポーネントの既定値を返します。

```
COLORREF GetDefaultValue();
```

### <a name="return-value"></a>戻り値

RGB コンポーネントの既定値を含む COLORREF 値。

### <a name="remarks"></a>Remarks

コンス トラクターまたは SetDefaultValue によって以前に設定された既定値を取得するには、この関数を呼び出します。

##  <a name="getg"></a>  CAnimationColor::GetG

緑のコンポーネントを表す CAnimationVariable にアクセスをできます。

```
CAnimationVariable& GetG();
```

### <a name="return-value"></a>戻り値

カプセル化された CAnimationVariable 表す緑要素への参照。

### <a name="remarks"></a>Remarks

基になる CAnimationVariable 表す緑要素に直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getr"></a>  CAnimationColor::GetR

赤のコンポーネントを表す CAnimationVariable にアクセスをできます。

```
CAnimationVariable& GetR();
```

### <a name="return-value"></a>戻り値

赤のコンポーネントを表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

赤のコンポーネントを表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getvalue"></a>  CAnimationColor::GetValue

現在の値を返します。

```
BOOL GetValue(COLORREF& color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
出力します。 このメソッドが戻るときに、現在の値を格納します。

### <a name="return-value"></a>戻り値

現在の値が正常に取得された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

アニメーションの色の現在の値を取得するには、この関数を呼び出します。 このメソッドが失敗した、または色コンポーネントの基になる COM オブジェクトが初期化されていない、色には、コンス トラクターまたは SetDefaultValue によって以前に設定された既定値が含まれています。

##  <a name="m_bvalue"></a>  CAnimationColor::m_bValue

アニメーションの色の青のコンポーネントを表すアニメーションをカプセル化された変数です。

```
CAnimationVariable m_bValue;
```

##  <a name="m_gvalue"></a>  CAnimationColor::m_gValue

アニメーションの色の緑のコンポーネントを表すアニメーションをカプセル化された変数です。

```
CAnimationVariable m_gValue;
```

##  <a name="m_rvalue"></a>  CAnimationColor::m_rValue

アニメーションの色の赤の要素を表すアニメーションをカプセル化された変数。

```
CAnimationVariable m_rValue;
```

##  <a name="operator_colorref"></a>  CAnimationColor::operator COLORREF

```
operator COLORREF();
```

### <a name="return-value"></a>戻り値

##  <a name="operator_eq"></a>  CAnimationColor::operator=

CAnimationColor に色を割り当てます。

```
void operator=(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
新しい値をアニメーションの色を指定します。

### <a name="remarks"></a>Remarks

お勧めするアニメーションの開始する前にこの演算子は SetDefaultValue で、作成した場合の色要素の基になる COM オブジェクトを再作成を呼び出すためです。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

##  <a name="setdefaultvalue"></a>  CAnimationColor::SetDefaultValue

既定値を設定します。

```
void SetDefaultValue(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
赤、緑、青のコンポーネントの新しい既定値を指定します。

### <a name="remarks"></a>Remarks

この関数を使用すると、アニメーション オブジェクトを既定値を設定できます。 このメソッドは、アニメーションの色の色要素に対する既定値を割り当てます。 作成した場合は、基になる COM オブジェクトも再作成します。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
