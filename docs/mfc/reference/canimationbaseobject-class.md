---
title: CAnimationBaseObject クラス
ms.date: 03/27/2019
f1_keywords:
- CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CAnimationBaseObject
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ApplyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ClearTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::ContainsVariable
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::CreateTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::DetachFromController
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableIntegerValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::EnableValueChangedEvent
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::GetAnimationVariableList
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::SetParentAnimationObjects
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_bAutodestroyTransitions
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_dwUserData
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nGroupID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_nObjectID
- AFXANIMATIONCONTROLLER/CAnimationBaseObject::m_pParentController
helpviewer_keywords:
- CAnimationBaseObject [MFC], CAnimationBaseObject
- CAnimationBaseObject [MFC], ApplyTransitions
- CAnimationBaseObject [MFC], ClearTransitions
- CAnimationBaseObject [MFC], ContainsVariable
- CAnimationBaseObject [MFC], CreateTransitions
- CAnimationBaseObject [MFC], DetachFromController
- CAnimationBaseObject [MFC], EnableIntegerValueChangedEvent
- CAnimationBaseObject [MFC], EnableValueChangedEvent
- CAnimationBaseObject [MFC], GetAutodestroyTransitions
- CAnimationBaseObject [MFC], GetGroupID
- CAnimationBaseObject [MFC], GetObjectID
- CAnimationBaseObject [MFC], GetUserData
- CAnimationBaseObject [MFC], SetAutodestroyTransitions
- CAnimationBaseObject [MFC], SetID
- CAnimationBaseObject [MFC], SetUserData
- CAnimationBaseObject [MFC], GetAnimationVariableList
- CAnimationBaseObject [MFC], SetParentAnimationObjects
- CAnimationBaseObject [MFC], m_bAutodestroyTransitions
- CAnimationBaseObject [MFC], m_dwUserData
- CAnimationBaseObject [MFC], m_nGroupID
- CAnimationBaseObject [MFC], m_nObjectID
- CAnimationBaseObject [MFC], m_pParentController
ms.assetid: 76b25917-940e-4eba-940f-31d270702603
ms.openlocfilehash: e9c5ed98d654eb37be7ab8523d44c9da6eecd9c7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152632"
---
# <a name="canimationbaseobject-class"></a>CAnimationBaseObject クラス

すべてのアニメーション オブジェクトの基底クラスです。

## <a name="syntax"></a>構文

```
class CAnimationBaseObject : public CObject;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CAnimationBaseObject::CAnimationBaseObject](#canimationbaseobject)|オーバーロードされます。 アニメーション オブジェクトを構築します。|
|[CAnimationBaseObject::~CAnimationBaseObject](#_dtorcanimationbaseobject)|デストラクターです。 アニメーション オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationBaseObject::ApplyTransitions](#applytransitions)|カプセル化されたアニメーション変数にストーリー ボードへの遷移を追加します。|
|[CAnimationBaseObject::ClearTransitions](#cleartransitions)|関連するすべての遷移を削除します。|
|[CAnimationBaseObject::ContainsVariable](#containsvariable)|アニメーション オブジェクトが特定のアニメーション変数を含めるかどうかを判断します。|
|[CAnimationBaseObject::CreateTransitions](#createtransitions)|アニメーション オブジェクトに関連付けられている遷移を作成します。|
|[CAnimationBaseObject::DetachFromController](#detachfromcontroller)|親アニメーション コント ローラーからアニメーション オブジェクトをデタッチします。|
|[CAnimationBaseObject::EnableIntegerValueChangedEvent](#enableintegervaluechangedevent)|整数値が変更されたイベント ハンドラーを設定します。|
|[CAnimationBaseObject::EnableValueChangedEvent](#enablevaluechangedevent)|値が変更されたイベント ハンドラーを設定します。|
|[CAnimationBaseObject::GetAutodestroyTransitions](#getautodestroytransitions)|関連する遷移が自動的に破棄されるかどうかを指示します。|
|[CAnimationBaseObject::GetGroupID](#getgroupid)|現在のグループ ID を返します。|
|[CAnimationBaseObject::GetObjectID](#getobjectid)|現在のオブジェクト ID を返します。|
|[CAnimationBaseObject::GetUserData](#getuserdata)|ユーザー定義データを返します。|
|[CAnimationBaseObject::SetAutodestroyTransitions](#setautodestroytransitions)|切り替え効果を自動的に破棄するためのフラグを設定します。|
|[CAnimationBaseObject::SetID](#setid)|新しい Id を設定します。|
|[CAnimationBaseObject::SetUserData](#setuserdata)|ユーザー定義データを設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CAnimationBaseObject::GetAnimationVariableList](#getanimationvariablelist)|含まれるアニメーション変数へのポインターを収集します。|
|[CAnimationBaseObject::SetParentAnimationObjects](#setparentanimationobjects)|アニメーション変数をアニメーション オブジェクトとそのコンテナーに含まれている間にリレーションシップを確立します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CAnimationBaseObject::m_bAutodestroyTransitions](#m_bautodestroytransitions)|関連する遷移を自動的に破棄する必要があるかどうかを指定します。|
|[CAnimationBaseObject::m_dwUserData](#m_dwuserdata)|ユーザー定義データを保存します。|
|[CAnimationBaseObject::m_nGroupID](#m_ngroupid)|アニメーション オブジェクトのグループ ID を指定します。|
|[CAnimationBaseObject::m_nObjectID](#m_nobjectid)|アニメーション オブジェクトのオブジェクト ID を指定します。|
|[CAnimationBaseObject::m_pParentController](#m_pparentcontroller)|親アニメーション コント ローラーへのポインター。|

## <a name="remarks"></a>Remarks

このクラスは、すべてのアニメーション オブジェクトの基本のメソッドを実装します。 アニメーション オブジェクトでは、値、ポイント、サイズ、四角形を表すしたり、色のカスタム エンティティと同様に、アプリケーションにすることができます。 アニメーション オブジェクトは、アニメーションのグループ (CAnimationGroup を参照してください) に格納されます。 各グループは、個別にアニメーション化して、ストーリー ボードのアナログとして扱うことができます。 アニメーション オブジェクトでは、1 つまたは複数のアニメーション変数 (CAnimationVariable を参照してください)、論理表現によってカプセル化します。 たとえば、CAnimationRect には、4 つのアニメーション変数四角形の各辺に 1 つの変数にはが含まれています。 各アニメーション オブジェクトのクラスは、遷移をカプセル化されたアニメーション変数に適用するために使用する必要があります、オーバー ロードされた AddTransition メソッドを公開します。 アニメーション オブジェクトを (必要に応じて) オブジェクト ID で識別できます、グループ id。 グループ ID が正しいグループに、アニメーション オブジェクトを配置するために必要なには、オブジェクトが ID が 0 の既定のグループ内に配置グループ ID が指定されていない場合。 さまざまな GroupID で SetID を呼び出した場合、アニメーション オブジェクトは (新しいグループは、必要な場合に作成されます)、別のグループに移動されます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CAnimationBaseObject`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="_dtorcanimationbaseobject"></a>  CAnimationBaseObject::~CAnimationBaseObject

デストラクターです。 アニメーション オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CAnimationBaseObject();
```

##  <a name="applytransitions"></a>  CAnimationBaseObject::ApplyTransitions

カプセル化されたアニメーション変数にストーリー ボードへの遷移を追加します。

```
virtual BOOL ApplyTransitions(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDependOnKeyframes);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
ストーリー ボードへのポインター。

*bDependOnKeyframes*<br/>
False の場合、このメソッドは、キーフレームに依存しないこれらの遷移だけを追加します。

### <a name="return-value"></a>戻り値

遷移が正常に追加された場合は TRUE。

### <a name="remarks"></a>Remarks

ストーリー ボードを AddTransition (派生クラスではオーバー ロードされたメソッド) に追加されている、関連する遷移を追加します。

##  <a name="canimationbaseobject"></a>  CAnimationBaseObject::CAnimationBaseObject

アニメーション オブジェクトを構築します。

```
CAnimationBaseObject();

CAnimationBaseObject(
    UINT32 nGroupID,
    UINT32 nObjectID = (UINT32)-1,
    DWORD dwUserData = 0);
```

### <a name="parameters"></a>パラメーター

*nGroupID*<br/>
グループ ID を指定します

*nObjectID*<br/>
オブジェクト ID を指定します

*dwUserData*<br/>
ユーザー定義のデータ、アニメーション オブジェクトに関連付けられた、実行時に後で取得することができます。

### <a name="remarks"></a>Remarks

アニメーション オブジェクトを構築し、既定のオブジェクト ID (0) とグループ ID (0) を割り当てます。

##  <a name="cleartransitions"></a>  CAnimationBaseObject::ClearTransitions

関連するすべての遷移を削除します。

```
virtual void ClearTransitions(BOOL bAutodestroy);
```

### <a name="parameters"></a>パラメーター

*bAutodestroy*<br/>
Transition オブジェクトを自動的に破棄またはだけ関連一覧から削除するかどうかを指定します。

### <a name="remarks"></a>Remarks

関連するすべての遷移を削除し、bAutodestroy または m_bAutodestroyTransitions フラグが TRUE の場合は、それらを破棄します。 遷移は、スタックにない割り当てられている場合にのみ、自動的に破棄する必要があります。 上記のフラグが FALSE の場合は、遷移だけ関連する遷移の内部リストから削除されます。

##  <a name="containsvariable"></a>  CAnimationBaseObject::ContainsVariable

アニメーション オブジェクトが特定のアニメーション変数を含めるかどうかを判断します。

```
virtual BOOL ContainsVariable(IUIAnimationVariable* pVariable);
```

### <a name="parameters"></a>パラメーター

*pVariable*<br/>
アニメーション変数へのポインター。

### <a name="return-value"></a>戻り値

アニメーション オブジェクトにアニメーション変数が含まれている場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

PVariable で指定された、アニメーション変数がアニメーション オブジェクト内に含まれるかどうかを判断するこのメソッドを使用できます。 その種類に応じて、アニメーション オブジェクトは、いくつかのアニメーション変数を含めることができます。 たとえば、CAnimationColor には (赤、緑、および青) 色コンポーネントごとに 1 つずつ、3 つの変数が含まれています。 アニメーション変数の値が変更されたとき、Windows Animation API は ValueChanged または IntegerValueChanged イベント (有効な場合)、および、このイベントのパラメーターがインターフェイスのアニメーション変数 IUIAnimationVariable へのポインターを送信します。 このメソッドは、アニメーションに含まれている COM オブジェクトへのポインターからのポインターを取得するのに役立ちます。

##  <a name="createtransitions"></a>  CAnimationBaseObject::CreateTransitions

アニメーション オブジェクトに関連付けられている遷移を作成します。

```
BOOL CreateTransitions();
```

### <a name="return-value"></a>戻り値

遷移が正常に作成された場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

アニメーションの派生オブジェクトにカプセル化されたアニメーション変数の一覧をループし、各アニメーション変数に関連付けられている遷移を作成します。

##  <a name="detachfromcontroller"></a>  CAnimationBaseObject::DetachFromController

親アニメーション コント ローラーからアニメーション オブジェクトをデタッチします。

```
void DetachFromController();
```

### <a name="remarks"></a>Remarks

このメソッドは、内部的に使用されます。

##  <a name="enableintegervaluechangedevent"></a>  CAnimationBaseObject::EnableIntegerValueChangedEvent

整数値が変更されたイベント ハンドラーを設定します。

```
virtual void EnableIntegerValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*pController*<br/>
親のコント ローラーへのポインター。

*bEnable*<br/>
有効にする、または整数値の変更イベントを無効にするかどうかを指定します。

### <a name="remarks"></a>Remarks

整数値が変更されたイベント ハンドラーが有効になっている場合は、CAnimationController::OnAnimationIntegerValueChanged メソッドは、CAnimationController 派生クラスでオーバーライドする必要がありますでこのイベントを処理することができます。 このメソッドは、アニメーションの整数値が変更されるたびに呼び出されます。

##  <a name="enablevaluechangedevent"></a>  CAnimationBaseObject::EnableValueChangedEvent

値が変更されたイベント ハンドラーを設定します。

```
virtual void EnableValueChangedEvent(
    CAnimationController* pController,
    BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*pController*<br/>
親のコント ローラーへのポインター。

*bEnable*<br/>
有効にする、または値の変更イベントを無効にするかどうかを指定します。

### <a name="remarks"></a>Remarks

値が変更されたイベント ハンドラーが有効になっている場合は、CAnimationController::OnAnimationValueChanged メソッドは、CAnimationController 派生クラスでオーバーライドする必要がありますでこのイベントを処理することができます。 このメソッドは、アニメーションの値が変更されるたびに呼び出されます。

##  <a name="getanimationvariablelist"></a>  CAnimationBaseObject::GetAnimationVariableList

含まれるアニメーション変数へのポインターを収集します。

```
virtual void GetAnimationVariableList(
    CList<CAnimationVariable*,
    CAnimationVariable*>& list) = 0;
```

### <a name="parameters"></a>パラメーター

*リスト*<br/>
アニメーション オブジェクトに含まれるアニメーション変数を代入するリスト。

### <a name="remarks"></a>Remarks

この純粋仮想メソッドは、派生クラスでオーバーライドする必要があります。 その種類に応じて、アニメーション オブジェクトには、1 つまたは複数のアニメーション変数が含まれています。 CAnimationPoint では、X および Y 座標をそれぞれの 2 つの変数を含まれています。 CAnimationBaseObject の基本クラスは、アニメーション変数の一覧で操作を実行するいくつかのジェネリック メソッドを実装します。ApplyTransitions, ClearTransitions, EnableValueChangedEvent, EnableIntegerValueChangedEvent. これらのメソッドは呼び出す GetAnimationVariableList で、特定のアニメーション オブジェクトに含まれる実際のアニメーション変数が派生クラスに入力されます、リストをループし、必要なアクションを実行します。 カスタム アニメーション オブジェクトを作成する場合に追加する必要があります*一覧*そのオブジェクトに含まれるすべてのアニメーション変数。

##  <a name="getautodestroytransitions"></a>  CAnimationBaseObject::GetAutodestroyTransitions

関連する遷移が自動的に破棄されるかどうかを指示します。

```
BOOL GetAutodestroyTransitions() const;
```

### <a name="return-value"></a>戻り値

TRUE の場合、関連する遷移を自動的に破棄します。FALSE の場合、transition オブジェクトがアプリケーションを呼び出すことによって割り当て解除する必要があります。

### <a name="remarks"></a>Remarks

既定ではこのフラグは TRUE です。 スタック上のトランジションの割り当てや、呼び出し元アプリケーションによって遷移の割り当てを解除する必要がある場合にのみ、このフラグを設定します。

##  <a name="getgroupid"></a>  CAnimationBaseObject::GetGroupID

現在のグループ ID を返します。

```
UINT32 GetGroupID() const;
```

### <a name="return-value"></a>戻り値

現在のグループ id。

### <a name="remarks"></a>Remarks

このメソッドを使用して、グループ ID を取得するには グループ ID が設定されていない場合に明示的にコンス トラクターまたは SetID に 0 ですね。

##  <a name="getobjectid"></a>  CAnimationBaseObject::GetObjectID

現在のオブジェクト ID を返します。

```
UINT32 GetObjectID() const;
```

### <a name="return-value"></a>戻り値

現在のオブジェクト id。

### <a name="remarks"></a>Remarks

このメソッドを使用して、オブジェクト ID を取得するには オブジェクト ID が設定されていない場合に明示的にコンス トラクターまたは SetID に 0 ですね。

##  <a name="getuserdata"></a>  CAnimationBaseObject::GetUserData

ユーザー定義データを返します。

```
DWORD GetUserData() const;
```

### <a name="return-value"></a>戻り値

カスタム データの値。

### <a name="remarks"></a>Remarks

実行時にカスタム データを取得するには、このメソッドを呼び出します。 明示的にまたは SetUserData コンス トラクターで初期化されてがいない場合は、返される値を 0 になります。

##  <a name="m_bautodestroytransitions"></a>  CAnimationBaseObject::m_bAutodestroyTransitions

関連する遷移を自動的に破棄する必要があるかどうかを指定します。

```
BOOL m_bAutodestroyTransitions;
```

##  <a name="m_dwuserdata"></a>  CAnimationBaseObject::m_dwUserData

ユーザー定義データを保存します。

```
DWORD m_dwUserData;
```

##  <a name="m_ngroupid"></a>  CAnimationBaseObject::m_nGroupID

アニメーション オブジェクトのグループ ID を指定します。

```
UINT32 m_nGroupID;
```

##  <a name="m_nobjectid"></a>  CAnimationBaseObject::m_nObjectID

アニメーション オブジェクトのオブジェクト ID を指定します。

```
UINT32 m_nObjectID;
```

##  <a name="m_pparentcontroller"></a>  CAnimationBaseObject::m_pParentController

親アニメーション コント ローラーへのポインター。

```
CAnimationController* m_pParentController;
```

##  <a name="setautodestroytransitions"></a>  CAnimationBaseObject::SetAutodestroyTransitions

切り替え効果を自動的に破棄するためのフラグを設定します。

```
void SetAutodestroyTransitions(BOOL bValue);
```

### <a name="parameters"></a>パラメーター

*bValue*<br/>
自動破棄フラグを指定します。

### <a name="remarks"></a>Remarks

新しい演算子を使用して、transition オブジェクトを割り当てた場合にのみ、このフラグを設定します。 Transition オブジェクトがスタックに割り当てられているいくつかの理由で、自動の破棄フラグが FALSE にする必要があります。 既定ではこのフラグは TRUE です。

##  <a name="setid"></a>  CAnimationBaseObject::SetID

新しい Id を設定します。

```
void SetID(
    UINT32 nObjectID,
    UINT32 nGroupID = 0);
```

### <a name="parameters"></a>パラメーター

*nObjectID*<br/>
新しいオブジェクトの ID を指定します

*nGroupID*<br/>
新しいグループの ID を指定します

### <a name="remarks"></a>Remarks

オブジェクト ID とグループ ID を変更することができます。 現在の ID、新しいグループの ID と異なる場合は、アニメーション オブジェクトがもう 1 つ (新しいグループを作成するグループ、必要な場合) に移動されます。

##  <a name="setparentanimationobjects"></a>  CAnimationBaseObject::SetParentAnimationObjects

アニメーション変数をアニメーション オブジェクトとそのコンテナーに含まれている間にリレーションシップを確立します。

```
virtual void SetParentAnimationObjects();
```

### <a name="remarks"></a>Remarks

このヘルパーは、アニメーション オブジェクトとそのコンテナーに含まれるアニメーション変数間の関係を確立するために使用できます。 アニメーション変数をループし、各アニメーション変数を親アニメーション オブジェクトへのバック ポインターを設定します。 現在の実装で CAnimationBaseObject::ApplyTransitions で実際の関係が確立されている、したがって戻りポインターが設定されていない CAnimationGroup::Animate を呼び出すまでです。 CAnimationVariable からオブジェクトのイベントと親のアニメーションを取得する必要性を処理するときに、関係を知ることが役立つ可能性がありますに。 CAnimationVariable::GetParentAnimationObject を使用します。

##  <a name="setuserdata"></a>  CAnimationBaseObject::SetUserData

ユーザー定義データを設定します。

```
void SetUserData (DWORD dwUserData);
```

### <a name="parameters"></a>パラメーター

*dwUserData*<br/>
カスタム データを指定します。

### <a name="remarks"></a>Remarks

このメソッドを使用して、アニメーション オブジェクトとカスタム データを関連付けます。 このデータを取得できます後で実行時に GetUserData で。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
