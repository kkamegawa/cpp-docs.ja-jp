---
title: CBaseTransition クラス
ms.date: 03/27/2019
f1_keywords:
- CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::CBaseTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboard
- AFXANIMATIONCONTROLLER/CBaseTransition::AddToStoryboardAtKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::Clear
- AFXANIMATIONCONTROLLER/CBaseTransition::Create
- AFXANIMATIONCONTROLLER/CBaseTransition::GetEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::GetStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::GetTransition
- AFXANIMATIONCONTROLLER/CBaseTransition::GetType
- AFXANIMATIONCONTROLLER/CBaseTransition::IsAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::SetKeyframes
- AFXANIMATIONCONTROLLER/CBaseTransition::SetRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_bAdded
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pEndKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pRelatedVariable
- AFXANIMATIONCONTROLLER/CBaseTransition::m_pStartKeyframe
- AFXANIMATIONCONTROLLER/CBaseTransition::m_transition
- AFXANIMATIONCONTROLLER/CBaseTransition::m_type
helpviewer_keywords:
- CBaseTransition [MFC], CBaseTransition
- CBaseTransition [MFC], AddToStoryboard
- CBaseTransition [MFC], AddToStoryboardAtKeyframes
- CBaseTransition [MFC], Clear
- CBaseTransition [MFC], Create
- CBaseTransition [MFC], GetEndKeyframe
- CBaseTransition [MFC], GetRelatedVariable
- CBaseTransition [MFC], GetStartKeyframe
- CBaseTransition [MFC], GetTransition
- CBaseTransition [MFC], GetType
- CBaseTransition [MFC], IsAdded
- CBaseTransition [MFC], SetKeyframes
- CBaseTransition [MFC], SetRelatedVariable
- CBaseTransition [MFC], m_bAdded
- CBaseTransition [MFC], m_pEndKeyframe
- CBaseTransition [MFC], m_pRelatedVariable
- CBaseTransition [MFC], m_pStartKeyframe
- CBaseTransition [MFC], m_transition
- CBaseTransition [MFC], m_type
ms.assetid: dfe84007-bbc5-43b7-b5b8-fae9145573bf
ms.openlocfilehash: 37bf536403d0edfc16b098929a4758a6c6958cf1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164151"
---
# <a name="cbasetransition-class"></a>CBaseTransition クラス

基本遷移を表します。

## <a name="syntax"></a>構文

```
class CBaseTransition : public CObject;
```

## <a name="members"></a>メンバー

### <a name="public-enumerations"></a>パブリック列挙型

|名前|説明|
|----------|-----------------|
|[CBaseTransition::TRANSITION_TYPE 列挙型](#transition_type_enumeration)|現在 Windows Animation API の MFC 実装によってサポートされている遷移の種類を定義します。|

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CBaseTransition::CBaseTransition](#cbasetransition)|基本遷移オブジェクトを構築します。|
|[CBaseTransition::~CBaseTransition](#_dtorcbasetransition)|デストラクターです。 移行のオブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CBaseTransition::AddToStoryboard](#addtostoryboard)|ストーリー ボードへの移行を追加します。|
|[CBaseTransition::AddToStoryboardAtKeyframes](#addtostoryboardatkeyframes)|ストーリー ボードへの移行を追加します。|
|[CBaseTransition::Clear](#clear)|リリースは、IUIAnimationTransition COM オブジェクトをカプセル化されます。|
|[CBaseTransition::Create](#create)|COM の遷移を作成します。|
|[CBaseTransition::GetEndKeyframe](#getendkeyframe)|返しますでは、キーフレームを開始します。|
|[CBaseTransition::GetRelatedVariable](#getrelatedvariable)|関連する変数へのポインターを返します。|
|[CBaseTransition::GetStartKeyframe](#getstartkeyframe)|返しますでは、キーフレームを開始します。|
|[CBaseTransition::GetTransition](#gettransition)|オーバーロードされます。 基になる COM 遷移オブジェクトへのポインターを返します。|
|[CBaseTransition::GetType](#gettype)|型を返しますに移行します。|
|[CBaseTransition::IsAdded](#isadded)|遷移がストーリー ボードに追加されたかどうかを指示します。|
|[CBaseTransition::SetKeyframes](#setkeyframes)|移行するためのキーフレームを設定します。|
|[CBaseTransition::SetRelatedVariable](#setrelatedvariable)|アニメーション変数と遷移の間の関係を確立します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CBaseTransition::m_bAdded](#m_badded)|遷移がストーリー ボードに追加されたかどうかを指定します。|
|[CBaseTransition::m_pEndKeyframe](#m_pendkeyframe)|遷移の終点を指定するキーフレームへのポインターを格納します。|
|[CBaseTransition::m_pRelatedVariable](#m_prelatedvariable)|M_transition に格納されている遷移のアニメーションがアニメーション変数へのポインター。|
|[CBaseTransition::m_pStartKeyframe](#m_pstartkeyframe)|移行の開始を指定するキーフレームへのポインターを格納します。|
|[CBaseTransition::m_transition](#m_transition)|IUIAnimationTransition へのポインターを格納します。 COM の移行のオブジェクトが作成されていない場合は NULL です。|
|[CBaseTransition::m_type](#m_type)|移行の種類を格納します。|

## <a name="remarks"></a>Remarks

このクラスは、IUIAnimationTransition インターフェイスをカプセル化し、すべての移行の基本クラスとして機能します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CBaseTransition`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="_dtorcbasetransition"></a>  CBaseTransition:: ~ CBaseTransition

デストラクターです。 移行のオブジェクトが破棄されるときに呼び出されます。

```
virtual ~CBaseTransition();
```

##  <a name="addtostoryboard"></a>  CBaseTransition::AddToStoryboard

ストーリー ボードへの移行を追加します。

```
BOOL AddToStoryboard(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
関連する変数をアニメーション化されますが、ストーリー ボードへのポインター。

### <a name="return-value"></a>戻り値

ストーリー ボードへの移行を正常に追加する場合は TRUE。

### <a name="remarks"></a>Remarks

ストーリー ボードに関連する変数への移行を適用します。 このストーリー ボードでこの変数に適用される最初の遷移の場合は、ストーリー ボードの開始時の移行を開始します。 それ以外の場合、移行は、変数に最近追加の移行に追加されます。

##  <a name="addtostoryboardatkeyframes"></a>  CBaseTransition::AddToStoryboardAtKeyframes

ストーリー ボードへの移行を追加します。

```
BOOL AddToStoryboardAtKeyframes(IUIAnimationStoryboard* pStoryboard);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
関連する変数をアニメーション化されますが、ストーリー ボードへのポインター。

### <a name="return-value"></a>戻り値

ストーリー ボードへの移行を正常に追加する場合は TRUE。

### <a name="remarks"></a>Remarks

ストーリー ボードに関連する変数への移行を適用します。 開始キーフレームが指定されている場合、そのキーフレームでの移行が開始されます。 終了のキーフレームが指定されている場合、移行は開始キーフレームから開始し、最後のキーフレームの停止します。 Duration パラメーターを指定の移行が作成されている場合、その時間は、期間の開始と終了のキーフレームの間で上書きされます。 キーフレームが指定されていない場合、移行は、変数に最近追加の移行に追加されます。

##  <a name="cbasetransition"></a>  CBaseTransition::CBaseTransition

基本遷移オブジェクトを構築します。

```
CBaseTransition();
```

##  <a name="clear"></a>  CBaseTransition::Clear

リリースは、IUIAnimationTransition COM オブジェクトをカプセル化されます。

```
void Clear();
```

### <a name="remarks"></a>Remarks

このメソッドは、IUITransition インターフェイスのリークを防ぐために、派生クラスの Create メソッドから呼び出す必要があります。

##  <a name="create"></a>  CBaseTransition::Create

COM の遷移を作成します。

```
virtual BOOL Create(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory) = 0;
```

### <a name="parameters"></a>パラメーター

*pLibrary*<br/>
標準的な遷移を作成する遷移ライブラリへのポインター。 カスタムの切り替えには、NULL になります。

*pFactory*<br/>
カスタム遷移を作成する遷移ファクトリへのポインター。 標準の切り替えには、NULL になります。

### <a name="return-value"></a>戻り値

遷移 COM オブジェクトが正常に作成された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

これは、純粋仮想関数、派生クラスでオーバーライドする必要があります。 基になる COM 遷移オブジェクトをインスタンス化するためにフレームワークによって呼び出されます。

##  <a name="getendkeyframe"></a>  CBaseTransition::GetEndKeyframe

返しますでは、キーフレームを開始します。

```
CBaseKeyFrame* GetEndKeyframe();
```

### <a name="return-value"></a>戻り値

キーフレーム、または NULL のキーフレームの間の遷移を挿入しないようにする場合に有効なポインター。

### <a name="remarks"></a>Remarks

このメソッドは、SetKeyframes によって以前に設定されたキーフレーム オブジェクトへのアクセスに使用できます。 遷移は、ストーリー ボードに追加されている場合は、最上位のコードによって呼び出されます。

##  <a name="getrelatedvariable"></a>  CBaseTransition::GetRelatedVariable

関連する変数へのポインターを返します。

```
CAnimationVariable* GetRelatedVariable();
```

### <a name="return-value"></a>戻り値

アニメーション変数、または NULL SetRelatedVariable でアニメーション変数が設定されていない場合に有効なポインター。

### <a name="remarks"></a>Remarks

これは、関連するアニメーション変数にアクセサーです。

##  <a name="getstartkeyframe"></a>  CBaseTransition::GetStartKeyframe

返しますでは、キーフレームを開始します。

```
CBaseKeyFrame* GetStartKeyframe();
```

### <a name="return-value"></a>戻り値

キーフレームをまたはキーフレームを移行する必要があります起動しない場合は NULL に有効なポインター。

### <a name="remarks"></a>Remarks

このメソッドは、SetKeyframes によって以前に設定されたキーフレーム オブジェクトへのアクセスに使用できます。 遷移は、ストーリー ボードに追加されている場合は、最上位のコードによって呼び出されます。

##  <a name="gettransition"></a>  CBaseTransition::GetTransition

基になる COM 遷移オブジェクトへのポインターを返します。

```
IUIAnimationTransition* GetTransition(
    IUIAnimationTransitionLibrary* pLibrary,
    IUIAnimationTransitionFactory* pFactory);

IUIAnimationTransition* GetTransition();
```

### <a name="parameters"></a>パラメーター

*pLibrary*<br/>
標準的な遷移を作成する遷移ライブラリへのポインター。 カスタムの切り替えには、NULL になります。

*pFactory*<br/>
カスタム遷移を作成する遷移ファクトリへのポインター。 標準の切り替えには、NULL になります。

### <a name="return-value"></a>戻り値

IUIAnimationTransition または遷移の基になる場合は NULL に有効なポインターを作成することはできません。

### <a name="remarks"></a>Remarks

このメソッドは、基になる COM 遷移オブジェクトへのポインターを返し、必要な場合は作成します。

##  <a name="gettype"></a>  CBaseTransition::GetType

型を返しますに移行します。

```
TRANSITION_TYPE GetType() const;
```

### <a name="return-value"></a>戻り値

TRANSITION_TYPE のいずれかの列挙値です。

### <a name="remarks"></a>Remarks

このメソッドは、その型によって遷移オブジェクトを識別するために使用できます。 種類は、派生クラスでコンス トラクターで設定されます。

##  <a name="isadded"></a>  CBaseTransition::IsAdded

遷移がストーリー ボードに追加されたかどうかを指示します。

```
BOOL IsAdded();
```

### <a name="return-value"></a>戻り値

かどうか、ストーリー ボードの場合は FALSE に遷移が追加され、TRUE を返します。

### <a name="remarks"></a>Remarks

このフラグは、最上位のコードは、ストーリー ボードへの遷移を追加すると、内部的に設定されます。

##  <a name="m_badded"></a>  CBaseTransition::m_bAdded

遷移がストーリー ボードに追加されたかどうかを指定します。

```
BOOL m_bAdded;
```

##  <a name="m_pendkeyframe"></a>  CBaseTransition::m_pEndKeyframe

遷移の終点を指定するキーフレームへのポインターを格納します。

```
CBaseKeyFrame* m_pEndKeyframe;
```

##  <a name="m_prelatedvariable"></a>  CBaseTransition::m_pRelatedVariable

M_transition に格納されている遷移のアニメーションがアニメーション変数へのポインター。

```
CAnimationVariable* m_pRelatedVariable;
```

##  <a name="m_pstartkeyframe"></a>  CBaseTransition::m_pStartKeyframe

移行の開始を指定するキーフレームへのポインターを格納します。

```
CBaseKeyFrame* m_pStartKeyframe;
```

##  <a name="m_transition"></a>  CBaseTransition::m_transition

IUIAnimationTransition へのポインターを格納します。 COM の移行のオブジェクトが作成されていない場合は NULL です。

```
ATL::CComPtr<IUIAnimationTransition> m_transition;
```

##  <a name="m_type"></a>  CBaseTransition::m_type

移行の種類を格納します。

```
TRANSITION_TYPE m_type;
```

##  <a name="setkeyframes"></a>  CBaseTransition::SetKeyframes

移行するためのキーフレームを設定します。

```
void SetKeyframes(
    CBaseKeyFrame* pStart = NULL,
    CBaseKeyFrame* pEnd = NULL);
```

### <a name="parameters"></a>パラメーター

*pStart*<br/>
移行の開始を指定するキーフレームです。

*保留*<br/>
遷移の終点を指定するキーフレームです。

### <a name="remarks"></a>Remarks

この方法で指定したキーフレームの後を開始し、必要に応じて、保留が NULL でない場合は、終了への移行は、指定したキーフレームの前にします。 Duration パラメーターを指定の移行が作成されている場合、その時間は、期間の開始と終了のキーフレームの間で上書きされます。

##  <a name="setrelatedvariable"></a>  CBaseTransition::SetRelatedVariable

アニメーション変数と遷移の間の関係を確立します。

```
void SetRelatedVariable(CAnimationVariable* pVariable);
```

### <a name="parameters"></a>パラメーター

*pVariable*<br/>
関連するアニメーション変数へのポインター。

### <a name="remarks"></a>Remarks

アニメーション変数と遷移の間の関係を確立します。 遷移は、1 つの変数にのみ適用できます。

##  <a name="transition_type_enumeration"></a>  CBaseTransition::TRANSITION_TYPE 列挙型

現在 Windows Animation API の MFC 実装によってサポートされている遷移の種類を定義します。

```
enum TRANSITION_TYPE;
```

### <a name="remarks"></a>Remarks

移行の種類は、特定の遷移のコンス トラクターで設定されます。 たとえば、CSinusoidalTransitionFromRange は SINUSOIDAL_FROM_RANGE にその型を設定します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
