---
title: CEvent クラス
ms.date: 11/04/2016
f1_keywords:
- CEvent
- AFXMT/CEvent
- AFXMT/CEvent::CEvent
- AFXMT/CEvent::PulseEvent
- AFXMT/CEvent::ResetEvent
- AFXMT/CEvent::SetEvent
- AFXMT/CEvent::Unlock
helpviewer_keywords:
- CEvent [MFC], CEvent
- CEvent [MFC], PulseEvent
- CEvent [MFC], ResetEvent
- CEvent [MFC], SetEvent
- CEvent [MFC], Unlock
ms.assetid: df676042-ce27-4702-800a-e73ff4f44395
ms.openlocfilehash: fbf2d834163199107aae44bd5723ceff79e36f91
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506691"
---
# <a name="cevent-class"></a>CEvent クラス

イベントを表します。これは、イベントが発生したことを1つのスレッドが別のスレッドに通知できるようにする同期オブジェクトです。

## <a name="syntax"></a>構文

```
class CEvent : public CSyncObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CEvent:: CEvent](#cevent)|`CEvent` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CEvent::PulseEvent](#pulseevent)|イベントを使用可能 (シグナル状態) に設定し、待機中のスレッドを解放して、イベントを使用不可 (非シグナル状態) に設定します。|
|[CEvent::ResetEvent](#resetevent)|イベントを使用不可 (非シグナル状態) に設定します。|
|[CEvent::SetEvent](#setevent)|イベントを使用可能 (シグナル状態) に設定し、待機中のスレッドをすべて解放します。|
|[CEvent:: Unlock](#unlock)|イベントオブジェクトを解放します。|

## <a name="remarks"></a>Remarks

イベントは、スレッドがタスクを実行するタイミングを知る必要がある場合に便利です。 たとえば、データアーカイブにデータをコピーするスレッドは、新しいデータが利用可能になったときに通知を受ける必要があります。 `CEvent`オブジェクトを使用して、新しいデータが利用可能になったときにコピースレッドに通知することで、スレッドはできるだけ早くタスクを実行できます。

`CEvent`オブジェクトには、手動と自動の2種類があります。

少なくと`CEvent`も1つのスレッドが解放されると、自動オブジェクトは、シグナルを返さない (使用できない) 状態に自動的に戻ります。 既定では、 `CEvent`構築時に*bmanualreset*パラメーターにを渡し`TRUE`ていない限り、オブジェクトは自動です。

手動`CEvent`オブジェクトは、他の関数が呼び出されるまで、 [SetEvent](#setevent)または[ResetEvent](#resetevent)によって設定された状態のままになります。 手動`CEvent`オブジェクトを作成するには`TRUE` 、構築`bManualReset`時にパラメーターにを渡します。

`CEvent`オブジェクトを使用するには、 `CEvent`必要に応じてオブジェクトを構築します。 待機するイベントの名前を指定し、アプリケーションで最初に所有する必要があることを指定します。 コンストラクターから制御が戻ったときに、イベントにアクセスできます。 [SetEvent](#setevent)を呼び出してイベントオブジェクトを通知し (利用可能にします)、制御されたリソースへのアクセスが完了したら、 [Unlock](#unlock)を呼び出します。

オブジェクトを使用`CEvent`する別の方法として、制御する`CEvent`クラスにデータメンバーとして型の変数を追加する方法があります。 制御されたオブジェクトの構築時に、 `CEvent`データメンバーのコンストラクターを呼び出し、イベントが最初にシグナル状態になるかどうかを指定します。また、イベントの種類 (プロセス間で使用する場合) を指定します。境界)、および必要なセキュリティ属性。

この方法で`CEvent`オブジェクトによって制御されるリソースにアクセスするには、まず、リソースのアクセスメソッドに[CSingleLock](../../mfc/reference/csinglelock-class.md)型または[CMultiLock](../../mfc/reference/cmultilock-class.md)型の変数を作成します。 次に、 `Lock` lock オブジェクトのメソッド (たとえば、 [CMultiLock:: lock](../../mfc/reference/cmultilock-class.md#lock)) を呼び出します。 この時点で、スレッドはリソースへのアクセス権を取得し、リソースが解放されてアクセスできるまで待機します。または、リソースが解放されるまで待機し、タイムアウトし、リソースへのアクセスを取得できなくなります。 いずれの場合も、スレッドセーフな方法でリソースにアクセスしています。 リソースを解放するには`SetEvent` 、を呼び出してイベントオブジェクトを通知した`Unlock`後、lock オブジェクトのメソッド (たとえば、 [CMultiLock:: Unlock](../../mfc/reference/cmultilock-class.md#unlock)) を使用するか、ロックオブジェクトがスコープ外になるようにします。

オブジェクトの使用`CEvent`方法の詳細については[、「マルチスレッド:同期クラス](../../parallel/multithreading-how-to-use-the-synchronization-classes.md)の使用方法について説明します。

## <a name="example"></a>例

[!code-cpp[NVC_MFC_Utilities#45](../../mfc/codesnippet/cpp/cevent-class_1.cpp)]

[!code-cpp[NVC_MFC_Utilities#46](../../mfc/codesnippet/cpp/cevent-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CSyncObject](../../mfc/reference/csyncobject-class.md)

`CEvent`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxmt

##  <a name="cevent"></a>CEvent:: CEvent

名前付き`CEvent`オブジェクトまたは名前のないオブジェクトを構築します。

```
CEvent(
    BOOL bInitiallyOwn = FALSE,
    BOOL bManualReset = FALSE,
    LPCTSTR lpszName = NULL,
    LPSECURITY_ATTRIBUTES lpsaAttribute = NULL);
```

### <a name="parameters"></a>パラメーター

*ビン分割*<br/>
TRUE の場合、オブジェクト`CMultilock`または`CSingleLock`オブジェクトのスレッドが有効になります。 それ以外の場合は、リソースにアクセスしようとしているすべてのスレッドが待機する必要があります。

*bManualReset*<br/>
TRUE の場合、イベントオブジェクトが手動イベントであることを指定します。それ以外の場合、イベントオブジェクトは自動イベントです。

*lpszName*<br/>
  `CEvent` オブジェクトの名前。 オブジェクトがプロセスの境界を越えて使用される場合は、を指定する必要があります。 名前が既存のイベントと一致する場合、コンストラクターはその`CEvent`名前のイベントを参照する新しいオブジェクトを作成します。 名前がイベントではない既存の同期オブジェクトと一致する場合、構築は失敗します。 NULL の場合、名前は null になります。

*lpsaAttribute*<br/>
イベントオブジェクトのセキュリティ属性。 この構造の詳細については、Windows SDK の「 [SECURITY_ATTRIBUTES](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\)) 」を参照してください。

### <a name="remarks"></a>Remarks

`CEvent`オブジェクトにアクセスしたり解放したりするには、 [CMultiLock](../../mfc/reference/cmultilock-class.md)オブジェクトまたは[CSingleLock](../../mfc/reference/csinglelock-class.md)オブジェクトを作成し、その[Lock](../../mfc/reference/csinglelock-class.md#lock)および[Unlock](../../mfc/reference/csinglelock-class.md#unlock)メンバー関数を呼び出します。

`CEvent`オブジェクトの状態をシグナル状態に変更する (スレッドが待機する必要がない) 場合は、 [SetEvent](#setevent)または[PulseEvent](#pulseevent)を呼び出します。 `CEvent`オブジェクトの状態を非シグナル状態 (スレッドが待機する必要があります) に設定するには、 [ResetEvent](#resetevent)を呼び出します。

> [!IMPORTANT]
>  `CEvent`オブジェクトを作成した後、 [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror)を使用して、ミューテックスが既に存在していないことを確認します。 ミューテックスが予期せずに存在する場合は、不正なプロセスがスクワッティングであることを示している可能性があります。また、ミューテックスを悪用する可能性があります。 この場合、推奨されるセキュリティ意識の高い手順は、ハンドルを閉じて、オブジェクトの作成でエラーが発生したかのように続行することです。

##  <a name="pulseevent"></a>  CEvent::PulseEvent

イベントの状態をシグナル状態 (利用可能) に設定し、待機中のスレッドを解放して、自動的に非シグナル状態 (利用不可) にリセットします。

```
BOOL PulseEvent();
```

### <a name="return-value"></a>戻り値

関数が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

イベントが manual の場合は、待機中のすべてのスレッドが解放され、イベントは`PulseEvent`非シグナル状態に設定され、が返されます。 イベントが自動の場合、1つのスレッドが解放されると`PulseEvent` 、イベントは非シグナル状態に設定され、が返されます。

待機中のスレッドがない場合、またはスレッドをすぐに`PulseEvent`解放できない場合、はイベントの状態を非シグナル状態に設定し、を返します。

`PulseEvent`は、基に`PulseEvent`なる Win32 関数を使用します。これは、カーネルモードの非同期プロシージャ呼び出しによって待機状態から一時的に削除することができます。 したがって`PulseEvent` 、は信頼性が低く、新しいアプリケーションでは使用できません。 詳細については、「 [PulseEvent 関数](/windows/win32/api/winbase/nf-winbase-pulseevent)」を参照してください。

##  <a name="resetevent"></a>  CEvent::ResetEvent

[SetEvent](#setevent)メンバー関数によって明示的にシグナル状態に設定されるまで、イベントの状態を非シグナル状態に設定します。

```
BOOL ResetEvent();
```

### <a name="return-value"></a>戻り値

関数が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

これにより、このイベントにアクセスするすべてのスレッドが待機します。

このメンバー関数は、自動イベントでは使用されません。

##  <a name="setevent"></a>  CEvent::SetEvent

イベントの状態をシグナル状態に設定し、待機中のスレッドを解放します。

```
BOOL SetEvent();
```

### <a name="return-value"></a>戻り値

関数が正常に実行された場合は0以外。それ以外の場合は0。

### <a name="remarks"></a>Remarks

イベントが manual の場合、 [ResetEvent](#resetevent)が呼び出されるまでイベントはシグナル状態のままになります。 この場合、複数のスレッドを解放できます。 イベントが自動の場合、イベントは1つのスレッドが解放されるまでシグナル状態のままになります。 その後、システムはイベントの状態を非シグナル状態に設定します。 待機中のスレッドがない場合、状態は1つのスレッドが解放されるまでシグナル状態のままになります。

##  <a name="unlock"></a>CEvent:: Unlock

イベントオブジェクトを解放します。

```
BOOL Unlock();
```

### <a name="return-value"></a>戻り値

スレッドがイベントオブジェクトを所有し、イベントが自動イベントである場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このメンバー関数は、ロックオブジェクトを再利用する必要がある場合に、完了後に解放する自動イベントを現在所有しているスレッドによって呼び出されます。 ロックオブジェクトを再利用しない場合、この関数はロックオブジェクトのデストラクターによって呼び出されます。

## <a name="see-also"></a>関連項目

[CSyncObject クラス](../../mfc/reference/csyncobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
