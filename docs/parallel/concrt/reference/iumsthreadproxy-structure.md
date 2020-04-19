---
title: IUMSThreadProxy 構造体
ms.date: 11/04/2016
f1_keywords:
- IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::EnterHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::ExitHyperCriticalRegion
- CONCRTRM/concurrency::IUMSThreadProxy::IUMSThreadProxy::GetCriticalRegionType
helpviewer_keywords:
- IUMSThreadProxy structure
ms.assetid: 61c69b7e-5c37-4048-bcb4-e75c536afd86
ms.openlocfilehash: f4fb43a4223cad8cc63049d2a0f8345e48b90f17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77139969"
---
# <a name="iumsthreadproxy-structure"></a>IUMSThreadProxy 構造体

実行スレッドの抽象化です。 ユーザー モード スケジュール可能 (UMS) スレッドをスケジューラに付与するには、スケジューラ ポリシー要素 `SchedulerKind` の値を `UmsThreadDefault` に設定し、さらに `IUMSScheduler` インターフェイスを実装する必要があります。 UMS スレッドは、Windows 7 以上のバージョンの 64 ビット オペレーティング システムでのみサポートされます。

## <a name="syntax"></a>構文

```cpp
struct IUMSThreadProxy : public IThreadProxy;
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[IUMSThreadProxy:: EnterCriticalRegion](#entercriticalregion)|クリティカルな領域を入力するために呼び出されます。 クリティカルなリージョン内では、スケジューラは、リージョン内で発生する非同期ブロック操作を監視しません。 これは、UMS スレッドに対して、ページフォールト、スレッド保留、カーネルの非同期プロシージャ呼び出し (Apc) などのために、スケジューラに再表示されないことを意味します。|
|[IUMSThreadProxy:: EnterHyperCriticalRegion](#enterhypercriticalregion)|ハイパークリティカル領域を開始するために呼び出されます。 ハイパークリティカルなリージョン内では、スケジューラは、リージョン内で発生するブロッキング操作を監視しません。 つまり、スケジューラは、関数呼び出しをブロックしたり、ブロック、ページフォールト、スレッド保留、カーネル非同期プロシージャ呼び出し (Apc) などの UMS スレッドに対して再実行されたりすることはありません。|
|[IUMSThreadProxy:: ExitCriticalRegion](#exitcriticalregion)|クリティカルな領域を終了するために呼び出されます。|
|[IUMSThreadProxy:: ExitHyperCriticalRegion](#exithypercriticalregion)|ハイパークリティカルな領域を終了するために呼び出されます。|
|[IUMSThreadProxy:: GetCriticalRegionType](#getcriticalregiontype)|スレッドプロキシが含まれているクリティカルな領域の種類を返します。 ハイパークリティカルなリージョンはクリティカルなリージョンのスーパーセットであるため、コードがクリティカルなリージョンに入ってからハイパークリティカルなリージョンに入った場合、`InsideHyperCriticalRegion` が返されます。|

## <a name="inheritance-hierarchy"></a>継承階層

[IThreadProxy](ithreadproxy-structure.md)

`IUMSThreadProxy`

## <a name="requirements"></a>［要件］

**ヘッダー:** concrtrm. h

**名前空間:** concurrency

## <a name="entercriticalregion"></a>IUMSThreadProxy:: EnterCriticalRegion メソッド

クリティカルな領域を入力するために呼び出されます。 クリティカルなリージョン内では、スケジューラは、リージョン内で発生する非同期ブロック操作を監視しません。 これは、UMS スレッドに対して、ページフォールト、スレッド保留、カーネルの非同期プロシージャ呼び出し (Apc) などのために、スケジューラに再表示されないことを意味します。

```cpp
virtual int EnterCriticalRegion() = 0;
```

### <a name="return-value"></a>戻り値

クリティカル領域の新しい深さ。 重要なリージョンは再入可能です。

## <a name="enterhypercriticalregion"></a>IUMSThreadProxy:: EnterHyperCriticalRegion メソッド

ハイパークリティカル領域を開始するために呼び出されます。 ハイパークリティカルなリージョン内では、スケジューラは、リージョン内で発生するブロッキング操作を監視しません。 つまり、スケジューラは、関数呼び出しをブロックしたり、ブロック、ページフォールト、スレッド保留、カーネル非同期プロシージャ呼び出し (Apc) などの UMS スレッドに対して再実行されたりすることはありません。

```cpp
virtual int EnterHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>戻り値

ハイパークリティカルなリージョンの新しい深さ。 ハイパークリティカルなリージョンは再入可能です。

### <a name="remarks"></a>解説

スケジューラは、呼び出すメソッドと、そのような地域でどのようなロックが取得されるかについて、細心の注意を払っている必要があります。 このような領域内のコードが、スケジューラによって保持されているロックによってブロックされると、デッドロックが発生する可能性があります。

## <a name="exitcriticalregion"></a>IUMSThreadProxy:: ExitCriticalRegion メソッド

クリティカルな領域を終了するために呼び出されます。

```cpp
virtual int ExitCriticalRegion() = 0;
```

### <a name="return-value"></a>戻り値

クリティカル領域の新しい深さ。 重要なリージョンは再入可能です。

## <a name="exithypercriticalregion"></a>IUMSThreadProxy:: ExitHyperCriticalRegion メソッド

ハイパークリティカルな領域を終了するために呼び出されます。

```cpp
virtual int ExitHyperCriticalRegion() = 0;
```

### <a name="return-value"></a>戻り値

ハイパークリティカルなリージョンの新しい深さ。 ハイパークリティカルなリージョンは再入可能です。

## <a name="getcriticalregiontype"></a>IUMSThreadProxy:: GetCriticalRegionType メソッド

スレッドプロキシが含まれているクリティカルな領域の種類を返します。 ハイパークリティカルなリージョンはクリティカルなリージョンのスーパーセットであるため、コードがクリティカルなリージョンに入ってからハイパークリティカルなリージョンに入った場合、`InsideHyperCriticalRegion` が返されます。

```cpp
virtual CriticalRegionType GetCriticalRegionType() const = 0;
```

### <a name="return-value"></a>戻り値

スレッドプロキシが含まれているクリティカルな領域の種類。

## <a name="see-also"></a>参照

[コンカレンシー名前空間](concurrency-namespace.md)<br/>
[IUMSScheduler 構造体](iumsscheduler-structure.md)
