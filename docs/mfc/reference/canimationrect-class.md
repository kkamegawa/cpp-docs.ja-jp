---
title: CAnimationRect クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::CAnimationRect
- AFXANIMATIONCONTROLLER/CAnimationRect::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationRect::GetBottom
- AFXANIMATIONCONTROLLER/CAnimationRect::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetLeft
- AFXANIMATIONCONTROLLER/CAnimationRect::GetRight
- AFXANIMATIONCONTROLLER/CAnimationRect::GetTop
- AFXANIMATIONCONTROLLER/CAnimationRect::GetValue
- AFXANIMATIONCONTROLLER/CAnimationRect::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationRect::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bFixedSize
- AFXANIMATIONCONTROLLER/CAnimationRect::m_bottomValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_leftValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_rightValue
- AFXANIMATIONCONTROLLER/CAnimationRect::m_szInitial
- AFXANIMATIONCONTROLLER/CAnimationRect::m_topValue
helpviewer_keywords:
- CAnimationRect [MFC], CAnimationRect
- CAnimationRect [MFC], AddTransition
- CAnimationRect [MFC], GetBottom
- CAnimationRect [MFC], GetDefaultValue
- CAnimationRect [MFC], GetLeft
- CAnimationRect [MFC], GetRight
- CAnimationRect [MFC], GetTop
- CAnimationRect [MFC], GetValue
- CAnimationRect [MFC], SetDefaultValue
- CAnimationRect [MFC], GetAnimationVariableList
- CAnimationRect [MFC], m_bFixedSize
- CAnimationRect [MFC], m_bottomValue
- CAnimationRect [MFC], m_leftValue
- CAnimationRect [MFC], m_rightValue
- CAnimationRect [MFC], m_szInitial
- CAnimationRect [MFC], m_topValue
ms.assetid: 0294156d-241e-4a57-92b2-31234fe557d6
ms.openlocfilehash: 84c4cf92894a9ece2021417445c9d7ab94ee6bdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62378181"
---
# <a name="canimationrect-class"></a>CAnimationRect クラス

四角形の 4 辺をアニメーション化できる機能を実装します。

## <a name="syntax"></a>構文

```
class CAnimationRect : public CAnimationBaseObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationRect::CAnimationRect](#canimationrect)|オーバーロードされます。 アニメーションの rect オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationRect::AddTransition](#addtransition)|左、上、右、下の座標の遷移を追加します。|
|[CAnimationRect::GetBottom](#getbottom)|CAnimationVariable 下端の座標を表すには、アクセスを提供します。|
|[CAnimationRect::GetDefaultValue](#getdefaultvalue)|四角形の境界の既定値を返します。|
|[CAnimationRect::GetLeft](#getleft)|CAnimationVariable 左座標を表すには、アクセスを提供します。|
|[CAnimationRect::GetRight](#getright)|右の座標を表す CAnimationVariable にアクセスをできます。|
|[CAnimationRect::GetTop](#gettop)|CAnimationVariable 上端の座標を表すには、アクセスを提供します。|
|[CAnimationRect::GetValue](#getvalue)|現在の値を返します。|
|[CAnimationRect::SetDefaultValue](#setdefaultvalue)|既定値を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationRect::GetAnimationVariableList](#getanimationvariablelist)|カプセル化されたアニメーション変数リストに配置します。 (上書き[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist))。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAnimationRect::operator RECT](#operator_rect)|CAnimationRect を可変噴出口に変換します。|
|[CAnimationRect::operator=](#operator_eq)|CAnimationRect rect に割り当てます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationRect::m_bFixedSize](#m_bfixedsize)|四角形のサイズが固定されているかどうかを指定します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationRect::m_bottomValue](#m_bottomvalue)|アニメーションの四角形の下部を表すカプセル化されたアニメーション変数をバインドします。|
|[CAnimationRect::m_leftValue](#m_leftvalue)|アニメーションの四角形の左を表すカプセル化されたアニメーション変数をバインドします。|
|[CAnimationRect::m_rightValue](#m_rightvalue)|アニメーションの四角形の右側を表すカプセル化されたアニメーション変数をバインドします。|
|[CAnimationRect::m_szInitial](#m_szinitial)|アニメーションの四角形の初期サイズを指定します。|
|[CAnimationRect::m_topValue](#m_topvalue)|アニメーションの四角形の上部を表すカプセル化されたアニメーション変数をバインドします。|

## <a name="remarks"></a>Remarks

CAnimationRect クラスは、4 つの CAnimationVariable オブジェクトをカプセル化し、四角形のアプリケーションで表すことができます。 アプリケーションでこのクラスを使用するには、だけこのクラスのオブジェクトをインスタンス化、CAnimationController::AddAnimationObject を使用してアニメーション コント ローラーに追加し、左側、右側の上端と下端の座標に適用される各遷移の AddTransition を呼び出します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationRect`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationRect::AddTransition

左、上、右、下の座標の遷移を追加します。

```
void AddTransition(
    CBaseTransition* pLeftTransition,
    CBaseTransition* pTopTransition,
    CBaseTransition* pRightTransition,
    CBaseTransition* pBottomTransition);
```

### <a name="parameters"></a>パラメーター

*pLeftTransition*<br/>
左側の遷移を指定します。

*pTopTransition*<br/>
上側の遷移を指定します。

*pRightTransition*<br/>
右側の遷移を指定します。

*pBottomTransition*<br/>
下の辺の遷移を指定します。

### <a name="remarks"></a>Remarks

各四角形の辺のアニメーション変数に適用する遷移の内部一覧に指定された遷移を追加するには、この関数を呼び出します。 遷移を追加するとすぐに適用され、内部リストに格納されているはありません。 遷移を (特定の値のストーリー ボードに追加された) に適用されます CAnimationController::AnimateGroup を呼び出すとします。 四角形の辺のいずれかに遷移を適用する不要な場合は、NULL を渡すことができます。

##  <a name="canimationrect"></a>  CAnimationRect::CAnimationRect

CAnimationRect オブジェクトを構築します。

```
CAnimationRect();

CAnimationRect(
    const CRect& rect,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    const CPoint& pt,
    const CSize& sz,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);

CAnimationRect(
    int nLeft,
    int nTop,
    int nRight,
    int nBottom,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
既定の長方形を指定します。

*nGroupID*<br/>
グループ ID を指定します

*nObjectID*<br/>
オブジェクト ID を指定します

*dwUserData*<br/>
ユーザー定義データを指定します。

*pt*<br/>
左上隅の座標。

*sz*<br/>
四角形のサイズ。

*nLeft*<br/>
左側のバインドの座標を指定します。

*nTop*<br/>
バインドされている最上位の座標を指定します。

*nRight*<br/>
適切なバインドの座標を指定します。

*nBottom*<br/>
バインドされている下部の座標を指定します。

### <a name="remarks"></a>Remarks

既定値で左、上、右、下、オブジェクト ID とグループの ID を 0 に設定されるオブジェクトが構築されます。 SetDefaultValue と SetID を使用して実行時に後で変更できます。

##  <a name="getanimationvariablelist"></a>  CAnimationRect::GetAnimationVariableList

カプセル化されたアニメーション変数リストに配置します。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>パラメーター

*lst*<br/>
関数から制御が戻るときに、四角形の座標を表す 4 つの CAnimationVariable オブジェクトへのポインターを格納します。

##  <a name="getbottom"></a>  CAnimationRect::GetBottom

CAnimationVariable 下端の座標を表すには、アクセスを提供します。

```
CAnimationVariable& GetBottom();
```

### <a name="return-value"></a>戻り値

下端の座標を表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

下端の座標を表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getdefaultvalue"></a>  CAnimationRect::GetDefaultValue

四角形の境界の既定値を返します。

```
CRect GetDefaultValue();
```

### <a name="return-value"></a>戻り値

左、右、上、下の既定値を含む CRect 値です。

### <a name="remarks"></a>Remarks

コンス トラクターまたは SetDefaultValue によって以前に設定された既定値を取得するには、この関数を呼び出します。

##  <a name="getleft"></a>  CAnimationRect::GetLeft

CAnimationVariable 左座標を表すには、アクセスを提供します。

```
CAnimationVariable& GetLeft();
```

### <a name="return-value"></a>戻り値

左の座標を表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

左の座標を表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getright"></a>  CAnimationRect::GetRight

右の座標を表す CAnimationVariable にアクセスをできます。

```
CAnimationVariable& GetRight();
```

### <a name="return-value"></a>戻り値

右の座標を表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

右の座標を表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="gettop"></a>  CAnimationRect::GetTop

CAnimationVariable 上端の座標を表すには、アクセスを提供します。

```
CAnimationVariable& GetTop();
```

### <a name="return-value"></a>戻り値

上端の座標を表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

上端の座標を表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getvalue"></a>  CAnimationRect::GetValue

現在の値を返します。

```
BOOL GetValue(CRect& rect);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
出力します。 このメソッドが戻るときに、現在の値を格納します。

### <a name="return-value"></a>戻り値

現在の値が正常に取得された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

四角形のアニメーションの現在の値を取得するには、この関数を呼び出します。 このメソッドが失敗したや基になる COM オブジェクトの左の場合は、上、右、下は初期化されていません、rect にはコンス トラクターまたは SetDefaultValue によって以前に設定された既定値が含まれています。

##  <a name="m_bfixedsize"></a>  CAnimationRect::m_bFixedSize

四角形のサイズが固定されているかどうかを指定します。

```
BOOL m_bFixedSize;
```

### <a name="remarks"></a>Remarks

このメンバーが true の場合は、右側の四角形のサイズが固定されてし、下部にある値が左上隅が固定サイズに従って移動するたびに再計算します。 この値を簡単に、画面の周りの四角形を移動する場合は TRUE に設定します。 ここでは右下隅の座標に適用される遷移は無視されます。 サイズは、オブジェクトを構築するか、SetDefaultValue ときに内部的に格納されます。 既定では、このメンバーは、FALSE に設定されます。

##  <a name="m_bottomvalue"></a>  CAnimationRect::m_bottomValue

アニメーションの四角形の下部を表すカプセル化されたアニメーション変数をバインドします。

```
CAnimationVariable m_bottomValue;
```

##  <a name="m_leftvalue"></a>  CAnimationRect::m_leftValue

アニメーションの四角形の左を表すカプセル化されたアニメーション変数をバインドします。

```
CAnimationVariable m_leftValue;
```

##  <a name="m_rightvalue"></a>  CAnimationRect::m_rightValue

アニメーションの四角形の右側を表すカプセル化されたアニメーション変数をバインドします。

```
CAnimationVariable m_rightValue;
```

##  <a name="m_szinitial"></a>  CAnimationRect::m_szInitial

アニメーションの四角形の初期サイズを指定します。

```
CSize m_szInitial;
```

##  <a name="m_topvalue"></a>  CAnimationRect::m_topValue

アニメーションの四角形の上部を表すカプセル化されたアニメーション変数をバインドします。

```
CAnimationVariable m_topValue;
```

##  <a name="operator_rect"></a>  CAnimationRect::operator RECT

CAnimationRect を可変噴出口に変換します。

```
operator RECT();
```

### <a name="return-value"></a>戻り値

可変噴出口として四角形をアニメーションの現在の値

### <a name="remarks"></a>Remarks

この関数は、GetValue を内部的に呼び出します。 GetValue 何らかの理由で失敗した場合、返された四角形は四角形の座標のすべての既定値が格納されます。

##  <a name="operator_eq"></a>  CAnimationRect::operator=

CAnimationRect rect に割り当てます。

```
void operator=(const RECT& rect);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
アニメーションの四角形の新しい値。

### <a name="remarks"></a>Remarks

お勧めするアニメーションの開始する前にこの演算子は SetDefaultValue で、作成した場合の色要素の基になる COM オブジェクトを再作成を呼び出すためです。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

##  <a name="setdefaultvalue"></a>  CAnimationRect::SetDefaultValue

既定値を設定します。

```
void SetDefaultValue(const CRect& rect);
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
左、上、右、下の新しい既定値を指定します。

### <a name="remarks"></a>Remarks

この関数を使用すると、アニメーション オブジェクトを既定値を設定できます。 このメソッドは、四角形の境界を既定値を割り当てます。 作成した場合は、基になる COM オブジェクトも再作成します。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
