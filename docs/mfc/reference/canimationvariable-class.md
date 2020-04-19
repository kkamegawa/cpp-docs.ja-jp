---
title: CAnimationVariable クラス
ms.date: 03/27/2019
f1_keywords:
- CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::CAnimationVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::AddTransition
- AFXANIMATIONCONTROLLER/CAnimationVariable::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::Create
- AFXANIMATIONCONTROLLER/CAnimationVariable::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::GetVariable
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::SetParentAnimationObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_dblDefaultValue
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_lstTransitions
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_pParentObject
- AFXANIMATIONCONTROLLER/CAnimationVariable::m_variable
helpviewer_keywords:
- CAnimationVariable [MFC], CAnimationVariable
- CAnimationVariable [MFC], AddTransition
- CAnimationVariable [MFC], ApplyTransitions
- CAnimationVariable [MFC], ClearTransitions
- CAnimationVariable [MFC], Create
- CAnimationVariable [MFC], CreateTransitions
- CAnimationVariable [MFC], EnableIntegerValueChangedEvent
- CAnimationVariable [MFC], EnableValueChangedEvent
- CAnimationVariable [MFC], GetDefaultValue
- CAnimationVariable [MFC], GetParentAnimationObject
- CAnimationVariable [MFC], GetValue
- CAnimationVariable [MFC], GetVariable
- CAnimationVariable [MFC], SetDefaultValue
- CAnimationVariable [MFC], SetParentAnimationObject
- CAnimationVariable [MFC], m_bAutodestroyTransitions
- CAnimationVariable [MFC], m_dblDefaultValue
- CAnimationVariable [MFC], m_lstTransitions
- CAnimationVariable [MFC], m_pParentObject
- CAnimationVariable [MFC], m_variable
ms.assetid: 506e697e-31a8-4033-a27e-292f4d7b42d9
ms.openlocfilehash: b6767ed42d66aff467ef36bd2a7b5234ad181ced
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507537"
---
# <a name="canimationvariable-class"></a>CAnimationVariable クラス

アニメーション変数を表します。

## <a name="syntax"></a>構文

```
class CAnimationVariable;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationVariable:: CAnimationVariable](#canimationvariable)|アニメーション変数オブジェクトを構築します。|
|[CAnimationVariable:: ~ CAnimationVariable](#_dtorcanimationvariable)|デストラクターです。 CAnimationVariable オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationVariable::AddTransition](#addtransition)|遷移を追加します。|
|[CAnimationVariable::ApplyTransitions](#applytransitions)|内部リストからストーリーボードに遷移を追加します。|
|[CAnimationVariable::ClearTransitions](#cleartransitions)|遷移をクリアします。|
|[CAnimationVariable::Create](#create)|基になるアニメーション変数 COM オブジェクトを作成します。|
|[CAnimationVariable::CreateTransitions](#createtransitions)|このアニメーション変数に適用されるすべての遷移を作成します。|
|[CAnimationVariable::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|IntegerValueChanged イベントを有効または無効にします。|
|[CAnimationVariable::EnableValueChangedEvent](#enablevaluechangedevent)|ValueChanged イベントを有効または無効にします。|
|[CAnimationVariable:: GetDefaultValue](#getdefaultvalue)|既定値を返します。|
|[CAnimationVariable::GetParentAnimationObject](#getparentanimationobject)|親のアニメーションオブジェクトを返します。|
|[CAnimationVariable:: GetValue](#getvalue)|オーバーロードされます。 アニメーション変数の現在の値を返します。|
|[CAnimationVariable:: GetVariable](#getvariable)|Iuiの変数 COM オブジェクトへのポインターを返します。|
|[CAnimationVariable:: SetDefaultValue](#setdefaultvalue)|既定値を設定し、Iuiの変数 COM オブジェクトを解放します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationVariable::SetParentAnimationObject](#setparentanimationobject)|アニメーション変数とアニメーションオブジェクトの間のリレーションシップを設定します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationVariable::m_bAutodestroyTransitions](#m_bautodestroytransitions)|関連する遷移オブジェクトを削除するかどうかを指定します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationVariable:: m_dblDefaultValue](#m_dbldefaultvalue)|Iuiの変数に反映される既定値を指定します。|
|[CAnimationVariable::m_lstTransitions](#m_lsttransitions)|このアニメーション変数をアニメーション化する遷移の一覧が含まれています。|
|[CAnimationVariable:: m_pParentObject](#m_pparentobject)|このアニメーション変数をカプセル化するアニメーションオブジェクトへのポインター。|
|[CAnimationVariable:: m_variable](#m_variable)|Iuiの変数 COM オブジェクトへのポインターを格納します。 COM オブジェクトがまだ作成されていない場合、または作成に失敗した場合は NULL。|

## <a name="remarks"></a>Remarks

CAnimationVariable クラスは、Iuiの変数 COM オブジェクトをカプセル化します。 また、ストーリーボードのアニメーション変数に適用される遷移の一覧も保持されます。 CAnimationVariable オブジェクトは、アニメーションオブジェクトに埋め込まれており、アプリケーションでアニメーション化された値、ポイント、サイズ、色、および四角形を表すことができます。

## <a name="inheritance-hierarchy"></a>継承階層

`CAnimationVariable`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="_dtorcanimationvariable"></a>CAnimationVariable:: ~ CAnimationVariable

デストラクターです。 CAnimationVariable オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CAnimationVariable();
```

##  <a name="addtransition"></a>  CAnimationVariable::AddTransition

遷移を追加します。

```
void AddTransition(CBaseTransition* pTransition);
```

### <a name="parameters"></a>パラメーター

*pTransition*<br/>
追加する遷移へのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、アニメーション変数に適用される遷移の内部リストに遷移を追加するために呼び出されます。 アニメーションがスケジュールされている場合は、この一覧をクリアする必要があります。

##  <a name="applytransitions"></a>  CAnimationVariable::ApplyTransitions

内部リストからストーリーボードに遷移を追加します。

```
void ApplyTransitions(
    CAnimationController* pController,
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>パラメーター

*pController*<br/>
親アニメーションコントローラーへのポインター。

*pStoryboard*<br/>
ストーリーボードへのポインター。

*bDependOnKeyframes*<br/>
このメソッドがキーフレームに依存する遷移を追加する必要がある場合は TRUE。

### <a name="remarks"></a>Remarks

このメソッドは、内部リストからストーリーボードへの遷移を追加します。 最上位のコードから何度も呼び出され、キーフレームに依存せず、キーフレームに依存する切り替え効果を追加します。 基になるアニメーション変数 COM オブジェクトが作成されていない場合、このメソッドはこのステージで作成します。

##  <a name="canimationvariable"></a>CAnimationVariable:: CAnimationVariable

アニメーション変数オブジェクトを構築します。

```
CAnimationVariable(DOUBLE dblDefaultValue = 0.0);
```

### <a name="parameters"></a>パラメーター

*dblDefaultValue*<br/>
既定値を指定します。

### <a name="remarks"></a>Remarks

アニメーション変数オブジェクトを構築し、その既定値を設定します。 変数がアニメーション化されていない場合、またはアニメーション化できない場合は、既定値が使用されます。

##  <a name="cleartransitions"></a>  CAnimationVariable::ClearTransitions

遷移をクリアします。

```
void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>パラメーター

*bAutodestroy*<br/>
このメソッドが遷移オブジェクトを削除する必要があるかどうかを指定します。

### <a name="remarks"></a>Remarks

このメソッドは、遷移の内部リストからすべての遷移を削除します。 BAutodestroy が TRUE の場合、または m_bAutodestroyTransitions が TRUE の場合、遷移は削除されます。 それ以外の場合、呼び出し元は遷移オブジェクトの割り当てを解除する必要があります。

##  <a name="create"></a>  CAnimationVariable::Create

基になるアニメーション変数 COM オブジェクトを作成します。

```
virtual BOOL Create(IUIAnimationManager* pManager);
```

### <a name="parameters"></a>パラメーター

*pManager*<br/>
アニメーションマネージャーへのポインター。

### <a name="return-value"></a>戻り値

アニメーション変数が正常に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、基になるアニメーション変数 COM オブジェクトを作成し、その既定値を設定します。

##  <a name="createtransitions"></a>  CAnimationVariable::CreateTransitions

このアニメーション変数に適用されるすべての遷移を作成します。

```
BOOL CreateTransitions(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* \*not used*\);
```

### <a name="parameters"></a>パラメーター

*pLibrary*<br/>
標準遷移のライブラリを定義する、 [Iuiの遷移 Tionlibrary インターフェイス](/windows/win32/api/uianimation/nn-uianimation-iuianimationtransitionlibrary)へのポインター。

### <a name="return-value"></a>戻り値

遷移が正常に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、変数の遷移の内部リストに追加された遷移を作成する必要がある場合に、フレームワークによって呼び出されます。

##  <a name="enableintegervaluechangedevent"></a>  CAnimationVariable::EnableIntegerValueChangedEvent

IntegerValueChanged イベントを有効または無効にします。

```
void EnableIntegerValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*pController*<br/>
親コントローラーへのポインター。

*bEnable*<br/>
TRUE-enable イベント、FALSE-disable イベント。

### <a name="remarks"></a>Remarks

ValueChanged イベントが有効になっている場合、フレームワークは、仮想メソッド CAnimationController:: OnAnimationIntegerValueChanged を呼び出します。 このイベントを処理するために、CAnimationController から派生したクラスでオーバーライドする必要があります。 このメソッドは、アニメーション変数の整数値が変更されるたびに呼び出されます。

##  <a name="enablevaluechangedevent"></a>  CAnimationVariable::EnableValueChangedEvent

ValueChanged イベントを有効または無効にします。

```
void EnableValueChangedEvent (
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*pController*<br/>
親コントローラーへのポインター。

*bEnable*<br/>
TRUE-enable イベント、FALSE-disable イベント。

### <a name="remarks"></a>Remarks

ValueChanged イベントが有効になっている場合、フレームワークは、仮想メソッド CAnimationController:: OnAnimationValueChanged を呼び出します。 このイベントを処理するために、CAnimationController から派生したクラスでオーバーライドする必要があります。 このメソッドは、アニメーション変数の値が変更されるたびに呼び出されます。

##  <a name="getdefaultvalue"></a>CAnimationVariable:: GetDefaultValue

既定値を返します。

```
DOUBLE GetDefaultValue() const;
```

### <a name="return-value"></a>戻り値

既定値。

### <a name="remarks"></a>Remarks

アニメーション変数の既定値を取得するには、この関数を使用します。 既定値は、コンストラクターまたは SetDefaultValue メソッドで設定できます。

##  <a name="getparentanimationobject"></a>  CAnimationVariable::GetParentAnimationObject

親のアニメーションオブジェクトを返します。

```
CAnimationBaseObject* GetParentAnimationObject();
```

### <a name="return-value"></a>戻り値

リレーションシップが確立されている場合は、親アニメーションオブジェクトへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

このメソッドを呼び出すと、親アニメーションオブジェクト (コンテナー) へのポインターを取得できます。

##  <a name="getvalue"></a>  CAnimationVariable::GetValue

アニメーション変数の現在の値を返します。

```
HRESULT GetValue(DOUBLE& dblValue);
HRESULT GetValue(INT32& nValue);
```

### <a name="parameters"></a>パラメーター

*dblValue*<br/>
アニメーション変数の現在の値。

*nValue*<br/>
アニメーション変数の現在の値。

### <a name="return-value"></a>戻り値

値が正常に取得された場合は S_OK、基になるアニメーション変数が作成されていない場合はです。 それ以外の場合は HRESULT エラーコード。

### <a name="remarks"></a>Remarks

このメソッドは、アニメーション変数の現在の値を取得するために呼び出すことができます。 基になる COM オブジェクトが作成されていない場合、この関数から制御が戻ったときに、dblValue に既定値が含まれます。

##  <a name="getvariable"></a>CAnimationVariable:: GetVariable

Iuiの変数 COM オブジェクトへのポインターを返します。

```
IUIAnimationVariable* GetVariable();
```

### <a name="return-value"></a>戻り値

Iuianimation Variable COM オブジェクトへの有効なポインター。アニメーション変数が作成されなかった場合、または作成できない場合は NULL。

### <a name="remarks"></a>Remarks

この関数を使用すると、基になる Iuiの変数 COM オブジェクトにアクセスし、必要に応じてそのメソッドを直接呼び出すことができます。

##  <a name="m_bautodestroytransitions"></a>  CAnimationVariable::m_bAutodestroyTransitions

関連する遷移オブジェクトを削除するかどうかを指定します。

```
BOOL m_bAutodestroyTransitions;
```

### <a name="remarks"></a>Remarks

この値を TRUE に設定すると、遷移オブジェクトが内部的な遷移の一覧から削除されるときに、そのオブジェクトが強制的に削除されます。 この値が FALSE の場合、アプリケーションを呼び出すことによって遷移を削除する必要があります。 遷移の一覧は、アニメーションがスケジュールされた後は常にクリアされます。 既定値は FALSE です。

##  <a name="m_dbldefaultvalue"></a>CAnimationVariable:: m_dblDefaultValue

Iuiの変数に反映される既定値を指定します。

```
DOUBLE m_dblDefaultValue;
```

##  <a name="m_lsttransitions"></a>  CAnimationVariable::m_lstTransitions

このアニメーション変数をアニメーション化する遷移の一覧が含まれています。

```
CObList m_lstTransitions;
```

##  <a name="m_pparentobject"></a>CAnimationVariable:: m_pParentObject

このアニメーション変数をカプセル化するアニメーションオブジェクトへのポインター。

```
CAnimationBaseObject* m_pParentObject;
```

##  <a name="m_variable"></a>CAnimationVariable:: m_variable

Iuiの変数 COM オブジェクトへのポインターを格納します。 COM オブジェクトがまだ作成されていない場合、または作成に失敗した場合は NULL。

```
ATL::CComPtr<IUIAnimationVariable> m_variable;
```

##  <a name="setdefaultvalue"></a>CAnimationVariable:: SetDefaultValue

既定値を設定し、Iuiの変数 COM オブジェクトを解放します。

```
void SetDefaultValue(DOUBLE dblDefaultValue);
```

### <a name="parameters"></a>パラメーター

*dblDefaultValue*<br/>
新しい既定値を指定します。

### <a name="remarks"></a>Remarks

既定値をリセットするには、このメソッドを使用します。 このメソッドは、内部 Iuianimation Variable COM オブジェクトを解放します。したがって、アニメーション変数を再作成すると、基になる COM オブジェクトが新しい既定値を取得します。 既定値は、アニメーション変数を表す COM オブジェクトが作成されない場合、または変数がアニメーション化されていない場合に、GetValue によって返されます。

##  <a name="setparentanimationobject"></a>  CAnimationVariable::SetParentAnimationObject

アニメーション変数とアニメーションオブジェクトの間のリレーションシップを設定します。

```
void SetParentAnimationObject(CAnimationBaseObject* pParentObject);
```

### <a name="parameters"></a>パラメーター

*pParentObject*<br/>
この変数を格納しているアニメーションオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、アニメーション変数とそれをカプセル化するアニメーションオブジェクトとの間に一対一のリレーションシップを確立するために、内部的に呼び出されます。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
