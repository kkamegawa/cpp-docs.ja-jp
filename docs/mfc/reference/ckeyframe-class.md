---
title: CKeyFrame クラス
ms.date: 11/04/2016
f1_keywords:
- CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::CKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboard
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAfterTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::AddToStoryboardAtOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetExistingKeyframe
- AFXANIMATIONCONTROLLER/CKeyFrame::GetOffset
- AFXANIMATIONCONTROLLER/CKeyFrame::GetTransition
- AFXANIMATIONCONTROLLER/CKeyFrame::m_offset
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pExistingKeyFrame
- AFXANIMATIONCONTROLLER/CKeyFrame::m_pTransition
helpviewer_keywords:
- CKeyFrame [MFC], CKeyFrame
- CKeyFrame [MFC], AddToStoryboard
- CKeyFrame [MFC], AddToStoryboardAfterTransition
- CKeyFrame [MFC], AddToStoryboardAtOffset
- CKeyFrame [MFC], GetExistingKeyframe
- CKeyFrame [MFC], GetOffset
- CKeyFrame [MFC], GetTransition
- CKeyFrame [MFC], m_offset
- CKeyFrame [MFC], m_pExistingKeyFrame
- CKeyFrame [MFC], m_pTransition
ms.assetid: d050a562-20f6-4c65-8ce5-ccb3aef1a20e
ms.openlocfilehash: c2c6add30757e1d83b70001679b37a7a22b9d7d6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392610"
---
# <a name="ckeyframe-class"></a>CKeyFrame クラス

アニメーションのキーフレームを表します。

## <a name="syntax"></a>構文

```
class CKeyFrame : public CBaseKeyFrame;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CKeyFrame::CKeyFrame](#ckeyframe)|オーバーロードされます。 その他のキーフレームに依存するキーフレームを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CKeyFrame::AddToStoryboard](#addtostoryboard)|ストーリー ボードにキーフレームを追加します。 (上書き[CBaseKeyFrame::AddToStoryboard](../../mfc/reference/cbasekeyframe-class.md#addtostoryboard))。|
|[CKeyFrame::AddToStoryboardAfterTransition](#addtostoryboardaftertransition)|移行後のストーリー ボードにキーフレームを追加します。|
|[CKeyFrame::AddToStoryboardAtOffset](#addtostoryboardatoffset)|オフセットでストーリー ボードにキーフレームを追加します。|
|[CKeyFrame::GetExistingKeyframe](#getexistingkeyframe)|このキーフレームによって異なりますキーフレームへのポインターを返します。|
|[CKeyFrame::GetOffset](#getoffset)|その他のキーフレームからのオフセットを返します。|
|[CKeyFrame::GetTransition](#gettransition)|このキーフレームによって異なります遷移へのポインターを返します。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CKeyFrame::m_offset](#m_offset)|M_pExistingKeyFrame に格納されているキーフレームから離れるときに、このキーフレームのオフセットを指定します。|
|[CKeyFrame::m_pExistingKeyFrame](#m_pexistingkeyframe)|既存の keframe へのポインターを格納します。 このキーフレームは、既存のキーフレームに m_offset でストーリー ボードに追加されます。|
|[CKeyFrame::m_pTransition](#m_ptransition)|このキーフレームから開始する切り替え効果へのポインターを格納します。|

## <a name="remarks"></a>Remarks

このクラスは、アニメーションのキーフレームを実装します。 キーフレームは、ストーリー ボード内の特定の時点を表し、遷移の開始と終了時刻を指定するために使用できます。 キーフレームは、その他のキーフレームに基づいて、秒単位からのオフセットがあると遷移に基づいてまたはしこの遷移の終了時刻の時点を表すをします。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CBaseKeyFrame](../../mfc/reference/cbasekeyframe-class.md)

[CKeyFrame](../../mfc/reference/ckeyframe-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxanimationcontroller.h

##  <a name="addtostoryboard"></a>  CKeyFrame::AddToStoryboard

ストーリー ボードにキーフレームを追加します。

```
virtual BOOL AddToStoryboard(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
ストーリー ボードへのポインター。

*bDeepAdd*<br/>
キーフレームを追加または再帰的に移行するかどうかを指定します。

### <a name="return-value"></a>戻り値

キーフレームを正常に追加された場合は TRUE。

### <a name="remarks"></a>Remarks

このメソッドは、ストーリー ボードにキーフレームを追加します。 他のキーフレームや遷移に依存して bDeepAdd が TRUE には、このメソッドは、再帰的に追加しようとします。

##  <a name="addtostoryboardaftertransition"></a>  CKeyFrame::AddToStoryboardAfterTransition

移行後のストーリー ボードにキーフレームを追加します。

```
BOOL AddToStoryboardAfterTransition(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
ストーリー ボードへのポインター。

*bDeepAdd*<br/>
遷移の再帰的に追加するかどうかを指定します。

### <a name="return-value"></a>戻り値

キーフレームを正常に追加された場合は TRUE。

### <a name="remarks"></a>Remarks

この関数は、移行後のストーリー ボードにキーフレームを追加するためにフレームワークによって呼び出されます。

##  <a name="addtostoryboardatoffset"></a>  CKeyFrame::AddToStoryboardAtOffset

オフセットでストーリー ボードにキーフレームを追加します。

```
virtual BOOL AddToStoryboardAtOffset(
    IUIAnimationStoryboard* pStoryboard,
    BOOL bDeepAdd);
```

### <a name="parameters"></a>パラメーター

*pStoryboard*<br/>
ストーリー ボードへのポインター。

*bDeepAdd*<br/>
キーフレームを追加するこのキーフレームが再帰的に依存するかどうかを指定します。

### <a name="return-value"></a>戻り値

キーフレームを正常に追加された場合は TRUE。

### <a name="remarks"></a>Remarks

この関数は、オフセットでストーリー ボードにキーフレームを追加するためにフレームワークによって呼び出されます。

##  <a name="ckeyframe"></a>  CKeyFrame::CKeyFrame

遷移に依存するキーフレームを構築します。

```
CKeyFrame(CBaseTransition* pTransition);

CKeyFrame(
    CBaseKeyFrame* pKeyframe,
    UI_ANIMATION_SECONDS offset = 0.0);
```

### <a name="parameters"></a>パラメーター

*pTransition*<br/>
遷移へのポインター。

*pKeyframe*<br/>
キーフレームへのポインター。

*オフセット*<br/>
Pkeyframe で指定されたキーフレームからの秒単位のオフセット。

### <a name="remarks"></a>Remarks

構築されたキーフレームは、指定の移行が終了すると、ストーリー ボード内の特定の時点を表します。

##  <a name="getexistingkeyframe"></a>  CKeyFrame::GetExistingKeyframe

このキーフレームによって異なりますキーフレームへのポインターを返します。

```
CBaseKeyFrame* GetExistingKeyframe();
```

### <a name="return-value"></a>戻り値

キーフレーム、またはこのキーフレームは、その他のキーフレームに依存しない場合は NULL に有効なポインター。

### <a name="remarks"></a>Remarks

これは、アクセサーをキーフレームこのキーフレームによって異なります。

##  <a name="getoffset"></a>  CKeyFrame::GetOffset

その他のキーフレームからのオフセットを返します。

```
UI_ANIMATION_SECONDS GetOffset();
```

### <a name="return-value"></a>戻り値

その他のキーフレームからの秒数でオフセットします。

### <a name="remarks"></a>Remarks

その他のキーフレームから秒単位のオフセットを判断するこのメソッドを呼び出す必要があります。

##  <a name="gettransition"></a>  CKeyFrame::GetTransition

このキーフレームによって異なります遷移へのポインターを返します。

```
CBaseTransition* GetTransition();
```

### <a name="return-value"></a>戻り値

遷移、またはこのキーフレームが遷移に依存しない場合は NULL に有効なポインター。

### <a name="remarks"></a>Remarks

これは、このキーフレームによって異なります遷移するアクセサーです。

##  <a name="m_offset"></a>  CKeyFrame::m_offset

M_pExistingKeyFrame に格納されているキーフレームから離れるときに、このキーフレームのオフセットを指定します。

```
UI_ANIMATION_SECONDS m_offset;
```

##  <a name="m_pexistingkeyframe"></a>  CKeyFrame::m_pExistingKeyFrame

既存の keframe へのポインターを格納します。 このキーフレームは、既存のキーフレームに m_offset でストーリー ボードに追加されます。

```
CBaseKeyFrame* m_pExistingKeyFrame;
```

##  <a name="m_ptransition"></a>  CKeyFrame::m_pTransition

このキーフレームから開始する切り替え効果へのポインターを格納します。

```
CBaseTransition* m_pTransition;
```

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
