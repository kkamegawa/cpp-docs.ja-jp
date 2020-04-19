---
title: CComSafeDeleteCriticalSection クラス
ms.date: 11/04/2016
f1_keywords:
- CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Init
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Lock
- ATLCORE/ATL::CComSafeDeleteCriticalSection::Term
- ATLCORE/ATL::m_bInitialized
helpviewer_keywords:
- CComSafeDeleteCriticalSection class
ms.assetid: 4d2932c4-ba8f-48ec-8664-1db8bed01314
ms.openlocfilehash: da83bc5d0c2ebb79aee07f30069144368169fc26
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821650"
---
# <a name="ccomsafedeletecriticalsection-class"></a>CComSafeDeleteCriticalSection クラス

このクラスには、クリティカルセクションオブジェクトの所有権を取得および解放するためのメソッドが用意されています。

## <a name="syntax"></a>構文

```
class CComSafeDeleteCriticalSection : public CComCriticalSection
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|[名前]|説明|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection](#ccomsafedeletecriticalsection)|コンストラクターです。|
|[CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection](#dtor)|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|[名前]|説明|
|----------|-----------------|
|[CComSafeDeleteCriticalSection::Init](#init)|クリティカルセクションオブジェクトを作成し、初期化します。|
|[CComSafeDeleteCriticalSection::Lock](#lock)|クリティカルセクションオブジェクトの所有権を取得します。|
|[CComSafeDeleteCriticalSection::Term](#term)|クリティカルセクションオブジェクトによって使用されているシステムリソースを解放します。|

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[m_bInitialized](#m_binitialized)|内部 `CRITICAL_SECTION` オブジェクトが初期化されているかどうかを示すフラグを指定します。|

## <a name="remarks"></a>Remarks

`CComSafeDeleteCriticalSection` はクラス[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)から派生します。 ただし、`CComSafeDeleteCriticalSection` では、 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)に対する追加の安全性メカニズムが提供されます。

`CComSafeDeleteCriticalSection` のインスタンスがスコープ外に出るか、明示的にメモリから削除されると、基になるクリティカルセクションオブジェクトが有効な場合は自動的にクリーンアップされます。 また、基になるクリティカルセクションオブジェクトがまだ割り当てられていないか、既にメモリから解放されている場合、 [CComSafeDeleteCriticalSection:: Term](#term)メソッドは正常に終了します。

クリティカルセクションのヘルパークラスの詳細については、「 [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md) 」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md)

`CComSafeDeleteCriticalSection`

## <a name="requirements"></a>要件

**ヘッダー:** atlcore .h

##  <a name="ccomsafedeletecriticalsection"></a>  CComSafeDeleteCriticalSection::CComSafeDeleteCriticalSection

コンストラクターです。

```
CComSafeDeleteCriticalSection();
```

### <a name="remarks"></a>Remarks

[M_bInitialized](#m_binitialized)データメンバーを FALSE に設定します。

##  <a name="dtor"></a>CComSafeDeleteCriticalSection:: ~ CComSafeDeleteCriticalSection

デストラクターです。

```
~CComSafeDeleteCriticalSection() throw();
```

### <a name="remarks"></a>Remarks

[M_bInitialized](#m_binitialized)データメンバーが TRUE に設定されている場合は、メモリから内部 `CRITICAL_SECTION` オブジェクトを解放します。

##  <a name="init"></a>  CComSafeDeleteCriticalSection::Init

[Init](/visualstudio/debugger/init)の基底クラスの実装を呼び出し、成功した場合は[m_bInitialized](#m_binitialized)を TRUE に設定します。

```
HRESULT Init() throw();
```

### <a name="return-value"></a>戻り値

[CComCriticalSection:: Init](../../atl/reference/ccomcriticalsection-class.md#init)の結果を返します。

##  <a name="lock"></a>  CComSafeDeleteCriticalSection::Lock

[Lock](ccomcriticalsection-class.md#lock)の基本クラスの実装を呼び出します。

```
HRESULT Lock();
```

### <a name="return-value"></a>戻り値

[CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock)の結果を返します。

### <a name="remarks"></a>Remarks

このメソッドは、エントリ時に[m_bInitialized](#m_binitialized)データメンバーが TRUE に設定されていることを前提としています。 この条件が満たされない場合、デバッグビルドでアサーションが生成されます。

関数の動作の詳細については、「 [CComCriticalSection:: Lock](../../atl/reference/ccomcriticalsection-class.md#lock)」を参照してください。

##  <a name="m_binitialized"></a>  CComSafeDeleteCriticalSection::m_bInitialized

内部 `CRITICAL_SECTION` オブジェクトが初期化されているかどうかを示すフラグを指定します。

```
bool m_bInitialized;
```

### <a name="remarks"></a>Remarks

`m_bInitialized` データメンバーは、 [CComSafeDeleteCriticalSection](../../atl/reference/ccomsafedeletecriticalsection-class.md)クラスに関連付けられている基になる `CRITICAL_SECTION` オブジェクトの有効性を追跡するために使用されます。 このフラグが TRUE に設定されていない場合、基になる `CRITICAL_SECTION` オブジェクトはメモリから解放されません。

##  <a name="term"></a>  CComSafeDeleteCriticalSection::Term

内部 `CRITICAL_SECTION` オブジェクトが有効な場合は、 [CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term)の基本クラスの実装を呼び出します。

```
HRESULT Term() throw();
```

### <a name="return-value"></a>戻り値

[CComCriticalSection:: Term](../../atl/reference/ccomcriticalsection-class.md#term)の結果を返します。入力時に[m_bInitialized](#m_binitialized)が FALSE に設定されている場合は S_OK します。

### <a name="remarks"></a>Remarks

内部 `CRITICAL_SECTION` オブジェクトが有効でない場合でも、このメソッドを呼び出すことは安全です。 [M_bInitialized](#m_binitialized)データメンバーが TRUE に設定されている場合、このクラスのデストラクターはこのメソッドを呼び出します。

## <a name="see-also"></a>関連項目

[CComCriticalSection クラス](../../atl/reference/ccomcriticalsection-class.md)<br/>
[クラスの概要](../../atl/atl-class-overview.md)
