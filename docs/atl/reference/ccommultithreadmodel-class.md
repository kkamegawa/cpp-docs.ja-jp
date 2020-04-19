---
title: CComMultiThreadModel クラス
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 74fb68eead498685ef252968124368863e27be75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497102"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel クラス

`CComMultiThreadModel`変数の値をインクリメントおよびデクリメントするためのスレッドセーフなメソッドを提供します。

## <a name="syntax"></a>構文

```
class CComMultiThreadModel
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|[CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md)クラスを参照します。|
|[CComMultiThreadModel:: CriticalSection](#criticalsection)|[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)クラスを参照します。|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)クラスを参照します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComMultiThreadModel::D ecrement](#decrement)|雑音指定された変数の値をスレッドセーフな方法でデクリメントします。|
|[CComMultiThreadModel::Increment](#increment)|雑音指定された変数の値をスレッドセーフな方法でインクリメントします。|

## <a name="remarks"></a>Remarks

通常、を使用`CComMultiThreadModel`するには、[CComObjectThreadModel] (atl-typedef # CComObjectThreadModel または [CComGlobalsThreadModel]) のいずれかの**typedef**名を使用します (atl-typedef # CComGlobalsThreadModel)。 各**typedef**によって参照されるクラスは、次の表に示すように、使用されるスレッドモデルによって異なります。

|Typedef|単一スレッド|アパートメントスレッド|フリースレッド|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M =`CComMultiThreadModel`

`CComMultiThreadModel`は、3つの**typedef**名を定義します。 `AutoCriticalSection`クリティカルセクションの所有権を取得および解放するためのメソッドを提供するリファレンスクラス。`CriticalSection` `ThreadModelNoCS`references クラス [CComMultiThreadModelNoCS (CComMultiThreadModelNoCS-class.md)。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

を使用`CComMultiThreadModel`する場合 、typedef `AutoCriticalSection`名はクラス[CComAutoCriticalSection](ccomautocriticalsection-class.md)を参照します。これにより、クリティカルセクションオブジェクトの所有権を取得および解放するためのメソッドが提供されます。

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Remarks

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)と[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)には、の`AutoCriticalSection`定義も含まれています。 次の表は、スレッドモデルクラスと、によって`AutoCriticalSection`参照されるクリティカルセクションクラスとの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

に`AutoCriticalSection`加えて、 **typedef**名[CriticalSection](#criticalsection)を使用することもできます。 CRT スタートアップコードを`AutoCriticalSection`削除する場合は、グローバルオブジェクトまたは静的クラスメンバーにを指定しないでください。

### <a name="example"></a>例

次のコードは、 [CComObjectRootEx](ccomobjectrootex-class.md)の後にモデル`AutoCriticalSection`化されており、スレッド環境で使用されています。

```cpp
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```

次の表は、 `InternalAddRef` `ThreadModel`テンプレートパラメーターと、 `Lock`アプリケーションで使用されるスレッドモデルに応じて、メソッドとメソッドの結果を示しています。

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|メソッド|シングルスレッドまたはアパートメントスレッド|フリースレッド|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|インクリメントはスレッドセーフではありません。|インクリメントはスレッドセーフです。|
|`Lock`|何も行いません。ロックする重要なセクションがありません。|クリティカルセクションがロックされています。|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel:: ThreadModelNoCS

|メソッド|シングルスレッドまたはアパートメントスレッド|フリースレッド|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|インクリメントはスレッドセーフではありません。|インクリメントはスレッドセーフです。|
|`Lock`|何も行いません。ロックする重要なセクションがありません。|何も行いません。ロックする重要なセクションがありません。|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

を使用`CComMultiThreadModel`する場合 、typedef `CriticalSection`名はクラス[CComCriticalSection](ccomcriticalsection-class.md)を参照します。これにより、クリティカルセクションオブジェクトの所有権を取得および解放するためのメソッドが提供されます。

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Remarks

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)と[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)には、の`CriticalSection`定義も含まれています。 次の表は、スレッドモデルクラスと、によって`CriticalSection`参照されるクリティカルセクションクラスとの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

に`CriticalSection`加えて、 **typedef**名[AutoCriticalSection](#autocriticalsection)を使用することもできます。 CRT スタートアップコードを`AutoCriticalSection`削除する場合は、グローバルオブジェクトまたは静的クラスメンバーにを指定しないでください。

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection)」を参照してください。

##  <a name="decrement"></a>CComMultiThreadModel::D ecrement

この静的関数は、Win32 関数[InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)を呼び出します。これにより、 *p*が指す変数の値が減少します。

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からデクリメントする変数へのポインター。

### <a name="return-value"></a>戻り値

デクリメントの結果が0の場合、 `Decrement`は0を返します。 デクリメントの結果が0以外の場合、戻り値も0以外になりますが、デクリメントの結果と一致しない可能性があります。

### <a name="remarks"></a>Remarks

`InterlockedDecrement`複数のスレッドがこの変数を同時に使用できないようにします。

##  <a name="increment"></a>  CComMultiThreadModel::Increment

この静的関数は、Win32 関数[InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)を呼び出します。これにより、 *p*が指す変数の値がインクリメントされます。

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からインクリメントする変数へのポインター。

### <a name="return-value"></a>戻り値

インクリメントの結果が0の場合、 `Increment`は0を返します。 インクリメントの結果が0以外の場合、戻り値も0以外になりますが、インクリメントの結果と一致しない可能性があります。

### <a name="remarks"></a>Remarks

`InterlockedIncrement`複数のスレッドがこの変数を同時に使用できないようにします。

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

を使用`CComMultiThreadModel`する場合 、typedef `ThreadModelNoCS`名はクラス[CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md)を参照します。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Remarks

`CComMultiThreadModelNoCS`変数をインクリメントおよびデクリメントするためのスレッドセーフなメソッドを提供します。ただし、クリティカルセクションは提供されません。

[CComSingleThreadModel](ccomsinglethreadmodel-class.md)と`CComMultiThreadModelNoCS`には、の`ThreadModelNoCS`定義も含まれています。 次の表は、スレッドモデルクラスとによって`ThreadModelNoCS`参照されるクラスの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection)」を参照してください。

## <a name="see-also"></a>関連項目

[CComSingleThreadModel クラス](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection クラス](ccomautocriticalsection-class.md)<br/>
[CComCriticalSection クラス](ccomcriticalsection-class.md)<br/>
[クラスの概要](../atl-class-overview.md)
