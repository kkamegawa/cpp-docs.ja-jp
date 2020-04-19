---
title: CComMultiThreadModelNoCS クラス
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: 01c7f953b6b8916394ee4c2b5b27cf84af52b920
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497081"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS クラス

`CComMultiThreadModelNoCS`クリティカルセクションのロックまたはロック解除機能を使用せずに、変数の値をインクリメントおよびデクリメントするためのスレッドセーフなメソッドを提供します。

## <a name="syntax"></a>構文

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

|名前|説明|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)クラスを参照します。|
|[CComMultiThreadModelNoCS:: CriticalSection](#criticalsection)|参照クラス`CComFakeCriticalSection`。|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|参照クラス`CComMultiThreadModelNoCS`。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|雑音指定された変数の値をスレッドセーフな方法でデクリメントします。|
|[CComMultiThreadModelNoCS::Increment](#increment)|雑音指定された変数の値をスレッドセーフな方法でインクリメントします。|

## <a name="remarks"></a>Remarks

`CComMultiThreadModelNoCS`は、変数をインクリメントおよびデクリメントするためのスレッドセーフメソッドを提供するという点で、 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)に似ています。 ただし、を使用`CComMultiThreadModelNoCS`してクリティカルセクションクラスを参照する場合、や`Unlock`など`Lock`のメソッドは何も行いません。

通常は、 `CComMultiThreadModelNoCS` **typedef**名を`ThreadModelNoCS`使用します。 この**typedef**は、、 `CComMultiThreadModelNoCS` `CComMultiThreadModel`、および[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)で定義されています。

> [!NOTE]
>  グローバル**typedef**名[CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)と[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)は参照`CComMultiThreadModelNoCS`しません。

に`ThreadModelNoCS`加えて、 `CComMultiThreadModelNoCS`は`AutoCriticalSection`および`CriticalSection`を定義します。 これらの2つの**typedef**名は、 [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)を参照します。これは、クリティカルセクションの取得と解放に関連付けられた空のメソッドを提供します。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection

を使用`CComMultiThreadModelNoCS`する場合 、typedef `AutoCriticalSection`名はクラス[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)を参照します。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Remarks

は`CComFakeCriticalSection`クリティカルセクションを提供しないため、メソッドは何も行いません。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)と[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)には、の`AutoCriticalSection`定義も含まれています。 次の表は、スレッドモデルクラスと、によって`AutoCriticalSection`参照されるクリティカルセクションクラスとの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

に`AutoCriticalSection`加えて、 **typedef**名[CriticalSection](#criticalsection)を使用することもできます。 CRT スタートアップコードを`AutoCriticalSection`削除する場合は、グローバルオブジェクトまたは静的クラスメンバーにを指定しないでください。

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)」を参照してください。

##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection

を使用`CComMultiThreadModelNoCS`する場合 、typedef `CriticalSection`名はクラス[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)を参照します。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Remarks

は`CComFakeCriticalSection`クリティカルセクションを提供しないため、メソッドは何も行いません。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)と[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)には、の`CriticalSection`定義も含まれています。 次の表は、スレッドモデルクラスと、によって`CriticalSection`参照されるクリティカルセクションクラスとの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

に`CriticalSection`加えて、 **typedef**名`AutoCriticalSection`を使用することもできます。 CRT スタートアップコードを`AutoCriticalSection`削除する場合は、グローバルオブジェクトまたは静的クラスメンバーにを指定しないでください。

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)」を参照してください。

##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement

この静的関数は、Win32 関数[InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement)を呼び出します。これにより、 *p*が指す変数の値が減少します。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からデクリメントする変数へのポインター。

### <a name="return-value"></a>戻り値

デクリメントの結果が0の場合、 `Decrement`は0を返します。 デクリメントの結果が0以外の場合、戻り値も0以外になりますが、デクリメントの結果と一致しない可能性があります。

### <a name="remarks"></a>Remarks

**InterlockedDecrement**を使用すると、複数のスレッドがこの変数を同時に使用することを防ぐことができます。

##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment

この静的関数は、Win32 関数[InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement)を呼び出します。これにより、 *p*が指す変数の値がインクリメントされます。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からインクリメントする変数へのポインター。

### <a name="return-value"></a>戻り値

インクリメントの結果が0の場合、 **increment**は0を返します。 インクリメントの結果が0以外の場合、戻り値も0以外になりますが、インクリメントの結果と一致しない可能性があります。

### <a name="remarks"></a>Remarks

**InterlockedIncrement**を使用すると、複数のスレッドがこの変数を同時に使用することを防ぐことができます。

##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS

を使用`CComMultiThreadModelNoCS`する場合 、typedef `ThreadModelNoCS`名は`CComMultiThreadModelNoCS`単にを参照します。

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Remarks

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)と[CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md)には、の`ThreadModelNoCS`定義も含まれています。 次の表は、スレッドモデルクラスとによって`ThreadModelNoCS`参照されるクラスの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

`ThreadModelNoCS`のの`CComMultiThreadModelNoCS`定義は`CComMultiThreadModel` 、と`CComSingleThreadModel`と対称であることに注意してください。 たとえば、の`CComMultiThreadModel::AutoCriticalSection`サンプルコードが次の**typedef**を宣言したとします。

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

に対し`ThreadModel`て指定されたクラス (など) `_ThreadModel`に関係なく、はそれに応じて`CComMultiThreadModelNoCS`解決します。

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)」を参照してください。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
