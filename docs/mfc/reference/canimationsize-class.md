---
title: CAnimationSize クラス
ms.date: 11/04/2016
f1_keywords:
- CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::CAnimationSize
- AFXANIMATIONCONTROLLER/CAnimationSize::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCX
- AFXANIMATIONCONTROLLER/CAnimationSize::GetCY
- AFXANIMATIONCONTROLLER/CAnimationSize::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetValue
- AFXANIMATIONCONTROLLER/CAnimationSize::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationSize::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cxValue
- AFXANIMATIONCONTROLLER/CAnimationSize::m_cyValue
helpviewer_keywords:
- CAnimationSize [MFC], CAnimationSize
- CAnimationSize [MFC], AddTransition
- CAnimationSize [MFC], GetCX
- CAnimationSize [MFC], GetCY
- CAnimationSize [MFC], GetDefaultValue
- CAnimationSize [MFC], GetValue
- CAnimationSize [MFC], SetDefaultValue
- CAnimationSize [MFC], GetAnimationVariableList
- CAnimationSize [MFC], m_cxValue
- CAnimationSize [MFC], m_cyValue
ms.assetid: ea06d1b5-502c-44a3-82ca-8bd6ba6a9364
ms.openlocfilehash: f52016afe39da900dca4847d29beccb97d829b60
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325118"
---
# <a name="canimationsize-class"></a>CAnimationSize クラス

サイズをアニメーション化できるサイズ オブジェクトの機能を実装します。

## <a name="syntax"></a>構文

```
class CAnimationSize : public CAnimationBaseObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationSize::CAnimationSize](#canimationsize)|オーバーロードされます。 アニメーションの size オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationSize::AddTransition](#addtransition)|幅と高さの遷移を追加します。|
|[CAnimationSize::GetCX](#getcx)|CAnimationVariable の幅を表すには、アクセスを提供します。|
|[CAnimationSize::GetCY](#getcy)|CAnimationVariable の高さを表すには、アクセスを提供します。|
|[CAnimationSize::GetDefaultValue](#getdefaultvalue)|幅と高さの既定値を返します。|
|[CAnimationSize::GetValue](#getvalue)|現在の値を返します。|
|[CAnimationSize::SetDefaultValue](#setdefaultvalue)|既定値を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationSize::GetAnimationVariableList](#getanimationvariablelist)|カプセル化されたアニメーション変数リストに配置します。 (上書き[CAnimationBaseObject::GetAnimationVariableList](../../mfc/reference/canimationbaseobject-class.md#getanimationvariablelist))。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CAnimationSize::operator CSize](#operator_csize)|CSize、CAnimationSize に変換します。|
|[CAnimationSize::operator=](#operator_eq)|CAnimationSize szSrc に割り当てます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationSize::m_cxValue](#m_cxvalue)|アニメーションのサイズの幅を表すアニメーションをカプセル化された変数です。|
|[CAnimationSize::m_cyValue](#m_cyvalue)|アニメーションのサイズの高さを表すアニメーションをカプセル化された変数です。|

## <a name="remarks"></a>Remarks

CAnimationSize クラスは、2 つの CAnimationVariable オブジェクトをカプセル化し、アプリケーションのサイズを表すことができます。 任意の 2 つのサイズをアニメーション化するこのクラスを使用するなど、画面上の次元のオブジェクト (四角形のような制御など)。 アプリケーションでこのクラスを使用するには、だけこのクラスのオブジェクトをインスタンス化、CAnimationController::AddAnimationObject を使用してアニメーション コント ローラーに追加し、幅や高さに適用される各遷移の AddTransition を呼び出します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CAnimationBaseObject](../../mfc/reference/canimationbaseobject-class.md)

`CAnimationSize`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="addtransition"></a>  CAnimationSize::AddTransition

幅と高さの遷移を追加します。

```
void AddTransition(
    CBaseTransition* pCXTransition,
    CBaseTransition* pCYTransition);
```

### <a name="parameters"></a>パラメーター

*pCXTransition*<br/>
幅の遷移へのポインター。

*pCYTransition*<br/>
高さの遷移へのポインター。

### <a name="remarks"></a>Remarks

幅と高さのアニメーション変数に適用する遷移の内部一覧に指定された遷移を追加するには、この関数を呼び出します。 遷移を追加するとすぐに適用され、内部リストに格納されているはありません。 遷移を (特定の値のストーリー ボードに追加された) に適用されます CAnimationController::AnimateGroup を呼び出すとします。 ディメンションの 1 つに、移行を適用する不要な場合は、NULL を渡すことができます。

##  <a name="canimationsize"></a>  CAnimationSize::CAnimationSize

アニメーションの size オブジェクトを構築します。

```
CAnimationSize();

CAnimationSize(
    const CSize& szDefault,
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>パラメーター

*szDefault*<br/>
既定のサイズを指定します。

*nGroupID*<br/>
グループ ID を指定します

*nObjectID*<br/>
オブジェクト ID を指定します

*dwUserData*<br/>
ユーザー定義データを指定します。

### <a name="remarks"></a>Remarks

幅、高さの既定値を持つオブジェクトが構築されたオブジェクトの ID とグループ ID は、0 に設定されます。 SetDefaultValue と SetID を使用して実行時に後で変更できます。

##  <a name="getanimationvariablelist"></a>  CAnimationSize::GetAnimationVariableList

カプセル化されたアニメーション変数リストに配置します。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& lst);
```

### <a name="parameters"></a>パラメーター

*lst*<br/>
関数から制御が戻るときに、幅と高さを表す 2 つの CAnimationVariable オブジェクトへのポインターを格納します。

##  <a name="getcx"></a>  CAnimationSize::GetCX

CAnimationVariable の幅を表すには、アクセスを提供します。

```
CAnimationVariable& GetCX();
```

### <a name="return-value"></a>戻り値

幅を表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

幅を表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getcy"></a>  CAnimationSize::GetCY

CAnimationVariable の高さを表すには、アクセスを提供します。

```
CAnimationVariable& GetCY();
```

### <a name="return-value"></a>戻り値

高さを表すカプセル化された CAnimationVariable への参照。

### <a name="remarks"></a>Remarks

高さを表す、基になる CAnimationVariable への直接アクセスを取得するには、このメソッドを呼び出すことができます。

##  <a name="getdefaultvalue"></a>  CAnimationSize::GetDefaultValue

幅と高さの既定値を返します。

```
CSize GetDefaultValue();
```

### <a name="return-value"></a>戻り値

既定値を含む CSize オブジェクト。

### <a name="remarks"></a>Remarks

コンス トラクターまたは SetDefaultValue によって以前に設定された既定値を取得するには、この関数を呼び出します。

##  <a name="getvalue"></a>  CAnimationSize::GetValue

現在の値を返します。

```
BOOL GetValue(CSize& szValue);
```

### <a name="parameters"></a>パラメーター

*szValue*<br/>
出力します。 このメソッドが戻るときに、現在の値を格納します。

### <a name="return-value"></a>戻り値

現在の値が正常に取得された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

アニメーションのサイズの現在の値を取得するには、この関数を呼び出します。 このメソッドが失敗した、または幅とサイズを基になる COM オブジェクトが初期化されていない、szValue には、コンス トラクターまたは SetDefaultValue によって以前に設定された既定値が含まれています。

##  <a name="m_cxvalue"></a>  CAnimationSize::m_cxValue

アニメーションのサイズの幅を表すアニメーションをカプセル化された変数です。

```
CAnimationVariable m_cxValue;
```

##  <a name="m_cyvalue"></a>  CAnimationSize::m_cyValue

アニメーションのサイズの高さを表すアニメーションをカプセル化された変数です。

```
CAnimationVariable m_cyValue;
```

##  <a name="operator_csize"></a>  CAnimationSize::operator CSize

CSize、CAnimationSize に変換します。

```
operator CSize();
```

### <a name="return-value"></a>戻り値

CSize とサイズをアニメーションの現在の値。

### <a name="remarks"></a>Remarks

この関数は、GetValue を内部的に呼び出します。 GetValue 何らかの理由で失敗した場合、返されるサイズは幅と高さの既定値が格納されます。

##  <a name="operator_eq"></a>  CAnimationSize::operator=

CAnimationSize szSrc に割り当てます。

```
void operator=(const CSize& szSrc);
```

### <a name="parameters"></a>パラメーター

*szSrc*<br/>
CSize またはサイズを指します。

### <a name="remarks"></a>Remarks

CAnimationSize szSrc に割り当てます。 お勧めするアニメーションの開始する前にこの演算子は SetDefaultValue で、作成した場合は、幅と高さの基になる COM オブジェクトを再作成を呼び出すためです。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

##  <a name="setdefaultvalue"></a>  CAnimationSize::SetDefaultValue

既定値を設定します。

```
void SetDefaultValue(const CSize& szDefault);
```

### <a name="parameters"></a>パラメーター

*szDefault*<br/>
新しい既定のサイズを指定します。

### <a name="remarks"></a>Remarks

この関数を使用すると、アニメーション オブジェクトを既定値を設定できます。 このメソッドは、既定値をアニメーションのサイズの幅と高さに割り当てます。 作成した場合は、基になる COM オブジェクトも再作成します。 イベント (ValueChanged または IntegerValueChanged) には、このアニメーション オブジェクトをサブスクライブしている場合は、これらのイベントを再度有効にする必要があります。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
