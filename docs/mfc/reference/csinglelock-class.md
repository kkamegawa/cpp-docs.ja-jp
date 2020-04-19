---
title: CSingleLock クラス
ms.date: 11/04/2016
f1_keywords:
- CSingleLock
- AFXMT/CSingleLock
- AFXMT/CSingleLock::CSingleLock
- AFXMT/CSingleLock::IsLocked
- AFXMT/CSingleLock::Lock
- AFXMT/CSingleLock::Unlock
helpviewer_keywords:
- CSingleLock [MFC], CSingleLock
- CSingleLock [MFC], IsLocked
- CSingleLock [MFC], Lock
- CSingleLock [MFC], Unlock
ms.assetid: 7dae7288-8066-4a3e-85e0-78d28bfc6bc8
ms.openlocfilehash: 31bd43f7f7a6fbccd4680db013ac5c654123061e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324104"
---
# <a name="csinglelock-class"></a>CSingleLock クラス

マルチスレッド プログラムで 1 つのリソースのアクセス制御に使うアクセス コントロール機構を表します。

## <a name="syntax"></a>構文

```
class CSingleLock
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSingleLock::CSingleLock](#csinglelock)|`CSingleLock` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSingleLock::IsLocked](#islocked)|オブジェクトがロックされているかどうかを決定します。|
|[CSingleLock::Lock](#lock)|同期オブジェクトを待機します。|
|[CSingleLock::Unlock](#unlock)|同期オブジェクトを解放します。|

## <a name="remarks"></a>Remarks

`CSingleLock` 基本クラスはありません。

同期クラスを使用するには[CSemaphore](../../mfc/reference/csemaphore-class.md)、 [CMutex](../../mfc/reference/cmutex-class.md)、 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)、および[CEvent](../../mfc/reference/cevent-class.md)、いずれかを作成する必要があります、`CSingleLock`または[CMultiLock](../../mfc/reference/cmultilock-class.md)オブジェクトを待機し、同期オブジェクトを解放します。 使用`CSingleLock`のみ必要がある場合、一度に 1 つのオブジェクトで待機します。 使用して、`CMultiLock`特定の時刻に使用できる複数のオブジェクトがある場合。

使用する、`CSingleLock`オブジェクト、被制御リソースのクラスのメンバー関数内でそのコンス トラクターを呼び出します。 呼び出して、 [IsLocked](#islocked)メンバー関数は、リソースが使用可能なかどうかを判断します。 である場合は、メンバー関数の残りの部分を続行します。 リソースが利用できない場合は、一定のリソースが解放されるまでの時間を待つか、エラーを返します。 リソースの使用が完了したら、後、 [Unlock](#unlock)関数の場合、`CSingleLock`オブジェクトがもう一度、使用するか、許可するが、`CSingleLock`オブジェクトを破棄します。

`CSingleLock` オブジェクトから派生したオブジェクトの存在を必要と[CSyncObject](../../mfc/reference/csyncobject-class.md)します。 これは、通常は、被制御リソースのクラスのデータ メンバーです。 使用する方法の詳細についての`CSingleLock`オブジェクトは、記事をご覧ください。[マルチ スレッド。同期クラスの使用方法](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

`CSingleLock`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmt.h

##  <a name="csinglelock"></a>  CSingleLock::CSingleLock

`CSingleLock` オブジェクトを構築します。

```
explicit CSingleLock(
    CSyncObject* pObject,
    BOOL bInitialLock = FALSE);
```

### <a name="parameters"></a>パラメーター

*pObject*<br/>
アクセスする同期オブジェクトを指します。 Nll は指定できません。

*bInitialLock*<br/>
最初に、指定したオブジェクトにアクセスしようとするかどうかを指定します。

### <a name="remarks"></a>Remarks

この関数は一般制御されるリソースのアクセス メンバー関数内から呼び出されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#19](../../mfc/codesnippet/cpp/csinglelock-class_1.h)]

##  <a name="islocked"></a>  CSingleLock::IsLocked

オブジェクトに関連付けられた決定、`CSingleLock`オブジェクトが非シグナル (使用不可)。

```
BOOL IsLocked();
```

### <a name="return-value"></a>戻り値

オブジェクトがロックされている場合は 0 以外それ以外の場合 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#20](../../mfc/codesnippet/cpp/csinglelock-class_2.h)]

##  <a name="lock"></a>  CSingleLock::Lock

指定された同期オブジェクトによって制御されるリソースにアクセスするには、この関数を呼び出して、`CSingleLock`コンス トラクター。

```
BOOL Lock(DWORD dwTimeOut = INFINITE);
```

### <a name="parameters"></a>パラメーター

*dwTimeOut*<br/>
使用できる同期オブジェクトを待機する時間を指定します (通知)。 場合、無限`Lock`を返す前に、オブジェクトがシグナル状態になるまで待機します。

### <a name="return-value"></a>戻り値

関数が成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

同期オブジェクトがシグナル状態になる場合`Lock`が正常に返され、スレッドは、オブジェクトを所有します。 同期オブジェクトを非シグナル状態にした場合 (利用不可)、`Lock`同期オブジェクトで指定されたミリ秒数までシグナル状態になるを待機は、 *dwTimeOut*パラメーター。 同期オブジェクトが指定された時間内シグナル状態になるいないしなかった場合`Lock`エラーを返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

##  <a name="unlock"></a>  CSingleLock::Unlock

によって所有されている同期オブジェクトを解放`CSingleLock`します。

```
BOOL Unlock();

BOOL Unlock(
    LONG lCount,
    LPLONG lPrevCount = NULL);
```

### <a name="parameters"></a>パラメーター

*lCount*<br/>
リリースへのアクセスの数。 1 以上であることが必要です。 指定された量を最大値を超えるオブジェクトの数となる、カウントは変更されませんし、関数は FALSE を返します。

*lPrevCount*<br/>
同期オブジェクトの前のカウントを受け取るように、変数へのポインター。 NULL の場合、前のカウントは返されません。

### <a name="return-value"></a>戻り値

関数が成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

この関数を呼び出して`CSingleLock`のデストラクター。

セマフォの 1 つ以上のアクセス数を解放する必要がある場合の 2 番目の形式を使用して、`Unlock`リリースへのアクセスの数を指定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#21](../../mfc/codesnippet/cpp/csinglelock-class_3.h)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CMultiLock クラス](../../mfc/reference/cmultilock-class.md)
