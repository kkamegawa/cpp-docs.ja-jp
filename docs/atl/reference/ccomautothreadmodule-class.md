---
title: CComAutoThreadModule クラス
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 9b0fa685bf9a7de94b158bd62b00161c1b58562d
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866174"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule クラス

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>パラメーター

*ThreadAllocator*<br/>
からスレッド選択を管理するクラス。 既定値は[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)です。

## <a name="members"></a>メンバー

### <a name="methods"></a>メソッド

|||
|-|-|
|[CreateInstance](#createinstance)|スレッドを選択し、関連付けられているアパートメント内にオブジェクトを作成します。|
|[GetDefaultThreads](#getdefaultthreads)|雑音プロセッサの数に基づいて、モジュールのスレッド数を動的に計算します。|
|[Init](#init)|モジュールのスレッドを作成します。|
|[[Lock] (ロック)](#lock)|モジュールと現在のスレッドのロックカウントをインクリメントします。|
|[ロック](#unlock)|モジュールと現在のスレッドのロックカウントをデクリメントします。|

### <a name="data-members"></a>データ メンバー

### <a name="data-members"></a>データ メンバー

|||
|-|-|
|[dwThreadID](#dwthreadid)|現在のスレッドの識別子を格納します。|
|[m_Allocator](#m_allocator)|スレッドの選択を管理します。|
|[m_nThreads](#m_nthreads)|モジュール内のスレッドの数を格納します。|
|[m_pApartments](#m_papartments)|モジュールのアパートメントを管理します。|

## <a name="remarks"></a>解説

> [!NOTE]
>  このクラスは互換性のために残されていますが、 [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md)と[CAtlModule](../../atl/reference/catlmodule-class.md)の派生クラスに置き換えられています。 次の情報は、ATL の古いリリースで使用されます。

`CComAutoThreadModule` は、 [CComModule](../../atl/reference/ccommodule-class.md)から派生して、Exe および Windows サービス用のスレッドプールされたアパートメントモデルの COM サーバーを実装します。 `CComAutoThreadModule` は[CComApartment](../../atl/reference/ccomapartment-class.md)を使用して、モジュール内の各スレッドのアパートメントを管理します。

複数のアパートメントにオブジェクトを作成する場合は、`CComAutoThreadModule` からモジュールを派生させます。 また、オブジェクトのクラス定義に[DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread)マクロを追加して、クラスファクトリとして[CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md)を指定する必要があります。

既定では、ATL COM AppWizard (Visual Studio .NET の ATL プロジェクトウィザード) は `CComModule`からモジュールを派生させます。 `CComAutoThreadModule`を使用するには、クラス定義を変更します。 次に例を示します。

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlbase. h

##  <a name="createinstance"></a>CComAutoThreadModule:: CreateInstance

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>パラメーター

*pfnCreateInstance*<br/>
からCreator 関数へのポインター。

*riid*<br/>
から要求されたインターフェイスの IID。

*ppvObj*<br/>
入出力*Riid*によって識別されるインターフェイスポインターへのポインター。 オブジェクトがこのインターフェイスをサポートしていない場合、 *ppvObj*は NULL に設定されます。

### <a name="return-value"></a>戻り値

標準の HRESULT 値。

### <a name="remarks"></a>解説

スレッドを選択し、関連付けられているアパートメント内にオブジェクトを作成します。

##  <a name="dwthreadid"></a>CComAutoThreadModule::d wThreadID

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
DWORD dwThreadID;
```

### <a name="remarks"></a>解説

現在のスレッドの識別子を格納します。

##  <a name="getdefaultthreads"></a>CComAutoThreadModule:: GetDefaultThreads

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>戻り値

EXE モジュールに作成されるスレッドの数。

### <a name="remarks"></a>解説

この静的関数は、プロセッサの数に基づいて、EXE モジュールのスレッドの最大数を動的に計算します。 既定では、この戻り値は、スレッドを作成するために[Init](#init)メソッドに渡されます。

##  <a name="init"></a>CComAutoThreadModule:: Init

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>パラメーター

*p*<br/>
からオブジェクトマップエントリの配列へのポインター。

*h*<br/>
から`DLLMain` または `WinMain`に渡される HINSTANCE。

*plibid*<br/>
からプロジェクトに関連付けられているタイプライブラリの LIBID へのポインター。

*nThreads*<br/>
から作成されるスレッドの数。 既定では、 *nThreads*は[GetDefaultThreads](#getdefaultthreads)によって返される値です。

### <a name="remarks"></a>解説

データメンバーを初期化し、 *nThreads*によって指定されたスレッドの数を作成します。

##  <a name="lock"></a>CComAutoThreadModule:: Lock

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
LONG Lock();
```

### <a name="return-value"></a>戻り値

診断またはテストに役立つ可能性のある値。

### <a name="remarks"></a>解説

モジュールと現在のスレッドのロックカウントに対してアトミックインクリメントを実行します。 `CComAutoThreadModule` は、モジュールのロックカウントを使用して、クライアントがモジュールにアクセスしているかどうかを判断します。 現在のスレッドのロック数は、統計のために使用されます。

##  <a name="m_allocator"></a>CComAutoThreadModule:: m_Allocator

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>解説

スレッド選択を管理するオブジェクト。 既定では、`ThreadAllocator` クラステンプレートパラメーターは[CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md)です。

##  <a name="m_nthreads"></a>CComAutoThreadModule:: m_nThreads

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
int m_nThreads;
```

### <a name="remarks"></a>解説

EXE モジュール内のスレッドの数を格納します。 [Init](#init)が呼び出されると、`m_nThreads` が*nThreads*パラメーター値に設定されます。 各スレッドに関連付けられているアパートメントは、 [CComApartment](../../atl/reference/ccomapartment-class.md)オブジェクトによって管理されます。

##  <a name="m_papartments"></a>CComAutoThreadModule:: m_pApartments

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>解説

は、 [CComApartment](../../atl/reference/ccomapartment-class.md)オブジェクトの配列をポイントし、それぞれがモジュールのアパートメントを管理します。 配列内の要素の数は、 [m_nThreads](#m_nthreads)のメンバーに基づいています。

##  <a name="unlock"></a>CComAutoThreadModule:: Unlock

ATL 7.0 の場合、`CComAutoThreadModule` は互換性のために残されています。詳細については、「 [Atl モジュールクラス](../../atl/atl-module-classes.md)」を参照してください。

```
LONG Unlock();
```

### <a name="return-value"></a>戻り値

診断またはテストに役立つ可能性のある値。

### <a name="remarks"></a>解説

モジュールのロック数と現在のスレッドのアトミックデクリメントを実行します。 `CComAutoThreadModule` は、モジュールのロックカウントを使用して、クライアントがモジュールにアクセスしているかどうかを判断します。 現在のスレッドのロック数は、統計のために使用されます。

モジュールのロックカウントが0になると、モジュールをアンロードできます。

## <a name="see-also"></a>参照

[クラスの概要](../../atl/atl-class-overview.md)<br/>
[モジュールクラス](../../atl/atl-module-classes.md)
