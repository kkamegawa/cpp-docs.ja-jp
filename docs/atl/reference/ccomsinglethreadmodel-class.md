---
title: CComSingleThreadModel クラス
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 9b111e06ba475a5077ba36b2235e8bd530302189
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215455"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel クラス

このクラスには、変数の値をインクリメントおよびデクリメントするためのメソッドが用意されています。

## <a name="syntax"></a>構文

```
class CComSingleThreadModel
```

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

|Name|説明|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)クラスを参照します。|
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|クラス `CComFakeCriticalSection`を参照します。|
|[CComSingleThreadModel:: ThreadModelNoCS](#threadmodelnocs)|`CComSingleThreadModel`を参照します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|指定した変数の値をデクリメントします。 この実装はスレッドセーフではありません。|
|[CComSingleThreadModel:: Increment](#increment)|指定した変数の値をインクリメントします。 この実装はスレッドセーフではありません。|

## <a name="remarks"></a>コメント

`CComSingleThreadModel` には、変数の値をインクリメントおよびデクリメントするためのメソッドが用意されています。 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)や[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)とは異なり、これらのメソッドはスレッドセーフではありません。

通常は、 [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel)または[CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel)の2つの**typedef**名のいずれかを使用して `CComSingleThreadModel` を使用します。 各**typedef**によって参照されるクラスは、次の表に示すように、使用されるスレッドモデルによって異なります。

|Typedef|単一スレッドモデル|アパートメントスレッドモデル|フリースレッドモデル|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`;M = `CComMultiThreadModel`

`CComSingleThreadModel` 自体は、3つの**typedef**名を定義します。 `ThreadModelNoCS` 参照 `CComSingleThreadModel`です。 `AutoCriticalSection` および `CriticalSection` 参照クラス[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)。クリティカルセクションの所有権の取得と解放に関連付けられた空のメソッドを提供します。

## <a name="requirements"></a>要件

**ヘッダー:** atlbase. h

##  <a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

`CComSingleThreadModel`を使用する場合、 **typedef**名 `AutoCriticalSection` はクラス[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)を参照します。

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>コメント

`CComFakeCriticalSection` はクリティカルセクションを提供しないため、メソッドは何も行いません。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)と[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)には `AutoCriticalSection`の定義が含まれています。 次の表は、スレッドモデルクラスと `AutoCriticalSection`が参照するクリティカルセクションクラスの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

`AutoCriticalSection`だけでなく、 **typedef**名[CriticalSection](#criticalsection)を使用することもできます。 CRT スタートアップコードを削除する場合は、グローバルオブジェクトまたは静的クラスメンバーに `AutoCriticalSection` を指定しないでください。

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)」を参照してください。

##  <a name="criticalsection"></a>CComSingleThreadModel:: CriticalSection

`CComSingleThreadModel`を使用する場合、 **typedef**名 `CriticalSection` はクラス[CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md)を参照します。

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>コメント

`CComFakeCriticalSection` はクリティカルセクションを提供しないため、メソッドは何も行いません。

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)と[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)には `CriticalSection`の定義が含まれています。 次の表は、スレッドモデルクラスと `CriticalSection`が参照するクリティカルセクションクラスの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

`CriticalSection`だけでなく、 **typedef**名[AutoCriticalSection](#autocriticalsection)を使用することもできます。 CRT スタートアップコードを削除する場合は、グローバルオブジェクトまたは静的クラスメンバーに `AutoCriticalSection` を指定しないでください。

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)」を参照してください。

##  <a name="decrement"></a>CComSingleThreadModel::D ecrement

この静的関数は、 *p*が指す変数の値をデクリメントします。

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からデクリメントする変数へのポインター。

### <a name="return-value"></a>戻り値

デクリメントの結果。

##  <a name="increment"></a>CComSingleThreadModel:: Increment

この静的関数は、 *p*が指す変数の値をインクリメントします。

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からインクリメントする変数へのポインター。

### <a name="return-value"></a>戻り値

インクリメントの結果。

##  <a name="threadmodelnocs"></a>CComSingleThreadModel:: ThreadModelNoCS

`CComSingleThreadModel`を使用する場合、 **typedef**名 `ThreadModelNoCS` は単に `CComSingleThreadModel`を参照します。

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>コメント

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md)と[CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)には `ThreadModelNoCS`の定義が含まれています。 次の表は、スレッドモデルクラスと `ThreadModelNoCS`によって参照されるクラスの関係を示しています。

|クラスの定義|参照されるクラス|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>例

「 [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection)」を参照してください。

## <a name="see-also"></a>参照

[クラスの概要](../../atl/atl-class-overview.md)
