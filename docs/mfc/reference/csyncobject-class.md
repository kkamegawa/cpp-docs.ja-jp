---
title: CSyncObject クラス
ms.date: 11/04/2016
f1_keywords:
- CSyncObject
- AFXMT/CSyncObject
- AFXMT/CSyncObject::CSyncObject
- AFXMT/CSyncObject::Lock
- AFXMT/CSyncObject::Unlock
- AFXMT/CSyncObject::m_hObject
helpviewer_keywords:
- CSyncObject [MFC], CSyncObject
- CSyncObject [MFC], Lock
- CSyncObject [MFC], Unlock
- CSyncObject [MFC], m_hObject
ms.assetid: c62ea6eb-a17b-4e01-aed4-321fc435a5f4
ms.openlocfilehash: 842ff5f98f05425fbbb511d112ae3e4fd65ff076
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324871"
---
# <a name="csyncobject-class"></a>CSyncObject クラス

Win32 の同期オブジェクトに共通の機能を提供する純粋仮想クラスです。

## <a name="syntax"></a>構文

```
class CSyncObject : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSyncObject::CSyncObject](#csyncobject)|`CSyncObject` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSyncObject::Lock](#lock)|同期オブジェクトにアクセスします。|
|[CSyncObject::Unlock](#unlock)|同期オブジェクトにアクセスします。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CSyncObject::operator ハンドル](#operator_handle)|同期オブジェクトへのアクセスを提供します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CSyncObject::m_hObject](#m_hobject)|基になる同期オブジェクトへのハンドル。|

## <a name="remarks"></a>Remarks

Microsoft Foundation Class ライブラリは、いくつかのクラスから派生した`CSyncObject`します。 これらは[CEvent](../../mfc/reference/cevent-class.md)、 [CMutex](../../mfc/reference/cmutex-class.md)、 [CCriticalSection](../../mfc/reference/ccriticalsection-class.md)、および[CSemaphore](../../mfc/reference/csemaphore-class.md)します。

同期オブジェクトを使用する方法については、この記事を参照してください。[マルチ スレッド。同期クラスの使用方法](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CSyncObject`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmt.h

##  <a name="csyncobject"></a>  CSyncObject::CSyncObject

指定された名前を使用して、同期オブジェクトを構築します。

```
explicit CSyncObject(LPCTSTR pstrName);
virtual ~CSyncObject();
```

### <a name="parameters"></a>パラメーター

*pstrName*<br/>
オブジェクトの名前。 NULL の場合、 *pstrName*は null になります。

##  <a name="lock"></a>  CSyncObject::Lock

同期オブジェクトによって制御されるリソースにアクセスするには、この関数を呼び出します。

```
virtual BOOL Lock(DWORD dwTimeout = INFINITE);
```

### <a name="parameters"></a>パラメーター

*dwTimeout*<br/>
使用できる同期オブジェクトを待機するミリ秒単位の時間を指定します (通知)。 場合、無限`Lock`を返す前に、オブジェクトがシグナル状態になるまで待機します。

### <a name="return-value"></a>戻り値

関数が成功した場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

同期オブジェクトがシグナル状態になる場合`Lock`が正常に返され、スレッドは、オブジェクトを所有します。 同期オブジェクトを非シグナル状態にした場合 (利用不可)、`Lock`同期オブジェクトで指定されたミリ秒数までシグナル状態になるを待機は、 *dwTimeOut*パラメーター。 同期オブジェクトが指定された時間内シグナル状態になるいないしなかった場合`Lock`エラーを返します。

##  <a name="m_hobject"></a>  CSyncObject::m_hObject

基になる同期オブジェクトへのハンドル。

```
HANDLE m_hObject;
```

##  <a name="operator_handle"></a>  CSyncObject::operator ハンドル

ハンドルを取得するこの演算子を使用して、`CSyncObject`オブジェクト。

```
operator HANDLE() const;
```

### <a name="return-value"></a>戻り値

成功した場合、同期オブジェクトのハンドルそれ以外の場合は NULL です。

### <a name="remarks"></a>Remarks

ハンドルを使用して、Windows Api を直接呼び出すことができます。

##  <a name="unlock"></a>  CSyncObject::Unlock

宣言`Unlock`パラメーターなしでは、純粋仮想関数とから派生したすべてのクラスでオーバーライドする必要があります`CSyncObject`します。

```
virtual BOOL Unlock() = 0; virtual BOOL Unlock(
    LONG lCount,
    LPLONG lpPrevCount = NULL);
```

### <a name="parameters"></a>パラメーター

*lCount*<br/>
既定の実装では使用されません。

*lpPrevCount*<br/>
既定の実装では使用されません。

### <a name="return-value"></a>戻り値

既定の実装を常に TRUE を返します。

### <a name="remarks"></a>Remarks

常に、2 つのパラメーター宣言の既定の実装では、TRUE を返します。 この関数は呼び出し元のスレッドによって所有されている同期オブジェクトへのアクセスを解放します。 2 番目の宣言は、被制御リソースの 1 つ以上のアクセスを許可するセマフォなどの同期オブジェクトに対して提供されます。

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
