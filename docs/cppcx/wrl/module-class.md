---
title: Module クラス
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::Module
- module/Microsoft::WRL::Module::Create
- module/Microsoft::WRL::Module::DecrementObjectCount
- module/Microsoft::WRL::Module::GetActivationFactory
- module/Microsoft::WRL::Module::GetClassObject
- module/Microsoft::WRL::Module::GetModule
- module/Microsoft::WRL::Module::GetObjectCount
- module/Microsoft::WRL::Module::IncrementObjectCount
- module/Microsoft::WRL::Module::Module
- module/Microsoft::WRL::Module::objectCount_Data
- module/Microsoft::WRL::Module::RegisterCOMObject
- module/Microsoft::WRL::Module::RegisterObjects
- module/Microsoft::WRL::Module::RegisterWinRTObject
- module/Microsoft::WRL::Module::releaseNotifier_
- module/Microsoft::WRL::Module::Terminate
- module/Microsoft::WRL::Module::~Module
- module/Microsoft::WRL::Module::UnregisterCOMObject
- module/Microsoft::WRL::Module::UnregisterObjects
- module/Microsoft::WRL::Module::UnregisterWinRTObject
helpviewer_keywords:
- Microsoft::WRL::Module class
- Microsoft::WRL::Module::Create method
- Microsoft::WRL::Module::DecrementObjectCount method
- Microsoft::WRL::Module::GetActivationFactory method
- Microsoft::WRL::Module::GetClassObject method
- Microsoft::WRL::Module::GetModule method
- Microsoft::WRL::Module::GetObjectCount method
- Microsoft::WRL::Module::IncrementObjectCount method
- Microsoft::WRL::Module::Module, constructor
- Microsoft::WRL::Module::objectCount_ data member
- Microsoft::WRL::Module::RegisterCOMObject method
- Microsoft::WRL::Module::RegisterObjects method
- Microsoft::WRL::Module::RegisterWinRTObject method
- Microsoft::WRL::Module::releaseNotifier_ data member
- Microsoft::WRL::Module::Terminate method
- Microsoft::WRL::Module::~Module, destructor
- Microsoft::WRL::Module::UnregisterCOMObject method
- Microsoft::WRL::Module::UnregisterObjects method
- Microsoft::WRL::Module::UnregisterWinRTObject method
ms.assetid: dd67e3b8-c2e1-4f53-8c0f-565a140ba649
ms.openlocfilehash: db3eb123382ac70f6198d094c5eb3fe44d3bbcd9
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345786"
---
# <a name="module-class"></a>Module クラス

関連するオブジェクトから成るコレクションを表します。

## <a name="syntax"></a>構文

```cpp
template<ModuleType moduleType>
class Module;

template<>
class Module<InProc> : public Details::ModuleBase;

template<>
class Module<OutOfProc> : public Module<InProc>;
```

### <a name="parameters"></a>パラメーター

*moduleType*<br/>
1 つ以上を組み合わせた[ModuleType](moduletype-enumeration.md)列挙値。

## <a name="members"></a>メンバー

### <a name="protected-classes"></a>保護されているクラス

名前                                                                                | 説明
----------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------
[Module::GenericReleaseNotifier](module-genericreleasenotifier-class.md) | 現在のモジュールの最後のオブジェクトがリリースされたときに、イベント ハンドラーを呼び出します。 イベント ハンドラーは、ラムダをファンクター、または関数へのポインターによって指定されます。
[Module::methodreleasenotifier](module-methodreleasenotifier-class.md)   | 現在のモジュールの最後のオブジェクトがリリースされたときに、イベント ハンドラーを呼び出します。 イベント ハンドラーは、オブジェクトとそのメソッドへのポインター メンバーによって指定されます。
[Module::ReleaseNotifier](module-releasenotifier-class.md)               | モジュールの最後のオブジェクトがリリースされたときに、イベント ハンドラーを呼び出します。

### <a name="public-constructors"></a>パブリック コンストラクター

名前                             | 説明
-------------------------------- | -----------------------------------------------------------
[モジュール:: ~ モジュール](#tilde-module) | 現在のインスタンスの初期化を解除、`Module`クラス。

### <a name="protected-constructors"></a>プロテクト コンストラクター

名前                      | 説明
------------------------- | ---------------------------------------------------
[Module::module](#module) | `Module` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

名前                                                    | 説明
------------------------------------------------------- | --------------------------------------------------------------------------------------------------
[Module::create](#create)                               | モジュールのインスタンスを作成します。
[Module::DecrementObjectCount](#decrementobjectcount)   | モジュールによって追跡されるオブジェクトの数をデクリメントします。
[Module::GetActivationFactory](#getactivationfactory)   | モジュールのアクティベーション ファクトリを取得します。
[Module::getclassobject](#getclassobject)               | クラス ファクトリのキャッシュを取得します。
[Module::GetModule](#getmodule)                         | モジュールのインスタンスを作成します。
[Module::GetObjectCount](#getobjectcount)               | このモジュールによって管理されるオブジェクトの数を取得します。
[Module::IncrementObjectCount](#incrementobjectcount)   | モジュールによって追跡されるオブジェクトの数をインクリメントします。
[Module::RegisterCOMObject](#registercomobject)         | 他のアプリケーションがそれらに接続できるように、1 つまたは複数の COM オブジェクトを登録します。
[Module::registerobjects](#registerobjects)             | 他のアプリケーションがそれらに接続できるように、COM または Windows ランタイムのオブジェクトを登録します。
[Module::RegisterWinRTObject](#registerwinrtobject)     | 他のアプリケーションがそれらに接続できるように、1 つまたは複数の Windows ランタイム オブジェクトを登録します。
[Module::terminate](#terminate)                         | シャット ダウンするモジュールによってインスタンス化されるすべてのファクトリをによりします。
[Module::UnregisterCOMObject](#unregistercomobject)     | 他のアプリケーションが接続することが原因の 1 つまたは複数の COM オブジェクトを解除します。
[Module::unregisterobjects](#unregisterobjects)         | 他のアプリケーションがそれらに接続できないように、指定したモジュール内のオブジェクトを登録解除します。
[Module::UnregisterWinRTObject](#unregisterwinrtobject) | 他のアプリケーションがそれらに接続できないように、1 つまたは複数の Windows ランタイム オブジェクトを登録解除します。

### <a name="protected-methods"></a>プロテクト メソッド

名前                      | 説明
------------------------- | --------------------------------
[Module::create](#create) | モジュールのインスタンスを作成します。

### <a name="protected-data-members"></a>プロテクト データ メンバー

名前                                         | 説明
-------------------------------------------- | --------------------------------------------------------------------------------------------------------
[Module::objectcount _](#objectcount)         | 多くのクラスが作成されたの追跡、[ように](make-function.md)関数。
[Module::releaseNotifier_](#releasenotifier) | ポインターを保持する`ReleaseNotifier`オブジェクト。

### <a name="macros"></a>[マクロ]

名 |説明-----|--- [ActivatableClass](activatableclass-macros.md) | 指定したクラスのインスタンスを作成できるファクトリを含む内部キャッシュを設定します。 このマクロは、既定のファクトリとグループの ID パラメーターを指定します。
[ActivatableClassWithFactory](activatableclass-macros.md) |指定したクラスのインスタンスを作成できるファクトリを含む内部キャッシュを設定します。 このマクロでは、特定の工場出荷時のパラメーターを指定することができます。
[ActivatableClassWithFactoryEx](activatableclass-macros.md) |指定したクラスのインスタンスを作成できるファクトリを含む内部キャッシュを設定します。 このマクロでは、特定のファクトリとグループの ID パラメーターを指定することができます。

## <a name="inheritance-hierarchy"></a>継承階層

`ModuleBase`

`Module`

`Module`

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="tilde-module"></a>モジュール:: ~ モジュール

現在のインスタンスの初期化を解除、`Module`クラス。

```cpp
virtual ~Module();
```

## <a name="create"></a>Module::create

モジュールのインスタンスを作成します。

```cpp
WRL_NOTHROW static Module& Create();
template<typename T>
WRL_NOTHROW static Module& Create(
   T callback
);
template<typename T>
WRL_NOTHROW static Module& Create(
   _In_ T* object,
   _In_ void (T::* method)()
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
モジュールの種類。

*callback*<br/>
モジュールの最後のインスタンス オブジェクトを解放するときに呼び出されます。

*object*<br/>
*オブジェクト*と*メソッド*パラメーターの組み合わせで使用されます。 ポイント最後のインスタンス オブジェクト、モジュールの最後のインスタンスのオブジェクトがリリースされたときにします。

*method*<br/>
*オブジェクト*と*メソッド*パラメーターの組み合わせで使用されます。 モジュールの最後のインスタンスのオブジェクトがリリースされたときに、最後のインスタンス オブジェクトのメソッドを指します。

### <a name="return-value"></a>戻り値

モジュールへの参照。

## <a name="decrementobjectcount"></a>Module::decrementobjectcount

モジュールによって追跡されるオブジェクトの数をデクリメントします。

```cpp
virtual long DecrementObjectCount();
```

### <a name="return-value"></a>戻り値

デクリメント操作の前にカウントします。

## <a name="getactivationfactory"></a>Module::GetActivationFactory

モジュールのアクティベーション ファクトリを取得します。

```cpp
WRL_NOTHROW HRESULT GetActivationFactory(
   _In_ HSTRING pActivatibleClassId,
   _Deref_out_ IActivationFactory **ppIFactory,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>パラメーター

*pActivatibleClassId*<br/>
ランタイム クラスの IID。

*ppIFactory*<br/>
指定されたランタイム クラスの IActivationFactory します。

*serverName*<br/>
現在のモジュールでクラス ファクトリのサブセットの名前。 使用されるサーバー名を指定、 [ActivatableClassWithFactoryEx](activatableclass-macros.md)マクロ、または指定`nullptr`を既定のサーバー名を取得します。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。GetActivationFactory によってそれ以外の場合、HRESULT が返されます。

## <a name="getclassobject"></a>Module::getclassobject

クラス ファクトリのキャッシュを取得します。

```cpp
HRESULT GetClassObject(
   REFCLSID clsid,
   REFIID riid,
   _Deref_out_ void **ppv,
   wchar_t* serverName = nullptr
);
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
クラスの id。

*riid*<br/>
要求したインターフェイス ID です。

*ppv*<br/>
返されるオブジェクトへのポインター。

*serverName*<br/>
いずれかで指定されているサーバー名、 `ActivatableClassWithFactory`、 `ActivatableClassWithFactoryEx`、または`ActivatableClass`マクロ; または`nullptr`を既定のサーバー名を取得します。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

このメソッドは、Windows ランタイムではなく COM にのみ使用します。 このメソッドを公開のみ`IClassFactory`メソッド。

## <a name="getmodule"></a>Module::GetModule

モジュールのインスタンスを作成します。

```cpp
static Module& GetModule();
WRL_NOTHROW static Module& GetModule();
```

### <a name="return-value"></a>戻り値

モジュールへの参照。

## <a name="getobjectcount"></a>Module::GetObjectCount

このモジュールによって管理されるオブジェクトの数を取得します。

```cpp
virtual long GetObjectCount() const;
```

### <a name="return-value"></a>戻り値

このモジュールによって管理されるオブジェクトの現在数。

## <a name="incrementobjectcount"></a>Module::IncrementObjectCount

モジュールによって追跡されるオブジェクトの数をインクリメントします。

```cpp
virtual long IncrementObjectCount();
```

### <a name="return-value"></a>戻り値

インクリメント操作の前にカウントします。

## <a name="module"></a>Module::module

`Module` クラスの新しいインスタンスを初期化します。

```cpp
Module();
```

### <a name="remarks"></a>Remarks

このコンス トラクターは保護され、ということはできません、`new`キーワード。 代わりに、いずれかを呼び出す[module::getmodule](#getmodule)または[module::create](#create)します。

## <a name="objectcount"></a>Module::objectcount _

多くのクラスが作成されたの追跡、[ように](make-function.md)関数。

```cpp
volatile long objectCount_;
```

## <a name="registercomobject"></a>Module::RegisterCOMObject

他のアプリケーションがそれらに接続できるように、1 つまたは複数の COM オブジェクトを登録します。

```cpp
WRL_NOTHROW virtual HRESULT RegisterCOMObject(
   const wchar_t* serverName,
   IID* clsids,
   IClassFactory** factories,
   DWORD* cookies,
   unsigned int count);
```

### <a name="parameters"></a>パラメーター

*serverName*<br/>
サーバーの完全修飾名。

*clsid*<br/>
登録する Clsid の配列。

*ファクトリ*<br/>
パブリッシュされるかどうかをクラスのオブジェクトの IUnknown インターフェイスの配列。

*Cookie*<br/>
操作が完了したらは、登録され、そのオブジェクト クラスを識別する値へのポインターの配列。 これらの値は使用後で登録を取り消します。

*count*<br/>
登録する Clsid の数。

### <a name="return-value"></a>戻り値

S_OK 場合成功します。それ以外の場合、HRESULT を理由を示す CO_E_OBJISREG など、操作に失敗しました。

### <a name="remarks"></a>Remarks

COM オブジェクトは、CLSCTX 列挙型の別個の列挙子に登録されます。

登録済みのオブジェクトへの接続の種類が現在の組み合わせで指定された*comflag*テンプレート パラメーターと REGCLS 列挙体の REGCLS_SUSPENDED 列挙子。

## <a name="registerobjects"></a>Module::registerobjects

他のアプリケーションがそれらに接続できるように、COM または Windows ランタイムのオブジェクトを登録します。

```cpp
HRESULT RegisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>パラメーター

*module*<br/>
COM または Windows ランタイム オブジェクトの配列。

*serverName*<br/>
オブジェクトを作成したサーバーの名前です。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、理由を示す HRESULT 操作に失敗しました。

## <a name="registerwinrtobject"></a>Module::RegisterWinRTObject

他のアプリケーションがそれらに接続できるように、1 つまたは複数の Windows ランタイム オブジェクトを登録します。

```cpp
HRESULT RegisterWinRTObject(const wchar_t* serverName,
   wchar_t** activatableClassIds,
   WINRT_REGISTRATION_COOKIE* cookie,
   unsigned int count)
```

### <a name="parameters"></a>パラメーター

*serverName*<br/>
この操作によって影響を受けるオブジェクトのサブセットを指定する名前。

*activatableClassIds*<br/>
登録のアクティブ化可能な Clsid の配列。

*cookie*<br/>
登録済みのクラス オブジェクトを識別する値。 この値は、登録を取り消すに後で使用されます。

*count*<br/>
登録するオブジェクトの数。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラーの hresult 値理由を示す CO_E_OBJISREG など、操作に失敗しました。

## <a name="releasenotifier"></a>Module::releasenotifier _

ポインターを保持する`ReleaseNotifier`オブジェクト。

```cpp
ReleaseNotifier *releaseNotifier_;
```

## <a name="terminate"></a>Module::terminate

シャット ダウンするモジュールによってインスタンス化されるすべてのファクトリをによりします。

```cpp
void Terminate();
```

### <a name="remarks"></a>Remarks

キャッシュのファクトリを解放します。

## <a name="unregistercomobject"></a>Module::unregistercomobject

他のアプリケーションが接続することが原因の 1 つまたは複数の COM オブジェクトを解除します。

```cpp
virtual HRESULT UnregisterCOMObject(
   const wchar_t* serverName,
   DWORD* cookies,
   unsigned int count
```

### <a name="parameters"></a>パラメーター

*serverName*<br/>
(未使用)

*Cookie*<br/>
登録するクラスのオブジェクトを識別する値へのポインターの配列。 配列がによって作成された、 [RegisterCOMObject](#registercomobject)メソッド。

*count*<br/>
登録を解除するクラスの数。

### <a name="return-value"></a>戻り値

この操作が成功した場合は s_ok を返します。それ以外の場合、エラーの理由を示す hresult 値の操作に失敗しました。

## <a name="unregisterobjects"></a>Module::unregisterobjects

他のアプリケーションがそれらに接続できないように、指定したモジュール内のオブジェクトを登録解除します。

```cpp
HRESULT UnregisterObjects(
   ModuleBase* module,
   const wchar_t* serverName);
```

### <a name="parameters"></a>パラメーター

*module*<br/>
モジュールへのポインター。

*serverName*<br/>
この操作によって影響を受けるオブジェクトのサブセットを指定する修飾名。

### <a name="return-value"></a>戻り値

この操作が成功した場合は s_ok を返します。それ以外の場合、エラー理由を示す HRESULT がこの操作に失敗しました。

## <a name="unregisterwinrtobject"></a>Module::unregisterwinrtobject

他のアプリケーションがそれらに接続できないように、1 つまたは複数の Windows ランタイム オブジェクトを登録解除します。

```cpp
virtual HRESULT UnregisterWinRTObject(
   unsigned int,
   _Inout_ WINRT_REGISTRATION_COOKIE* cookie
);
```

### <a name="parameters"></a>パラメーター

*cookie*<br/>
登録を取り消すことは、クラス オブジェクトを識別する値へのポインター。
