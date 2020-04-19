---
title: SimpleActivationFactory クラス
ms.date: 09/07/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleActivationFactory
- module/Microsoft::WRL::SimpleActivationFactory::ActivateInstance
- module/Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::SimpleActivationFactory::GetTrustLevel
helpviewer_keywords:
- Microsoft::WRL::SimpleActivationFactory class
- Microsoft::WRL::SimpleActivationFactory::ActivateInstance method
- Microsoft::WRL::SimpleActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::SimpleActivationFactory::GetTrustLevel method
ms.assetid: aff768e0-0038-4fd7-95d2-ad7d308da41c
ms.openlocfilehash: 1831a816d0967c2ca53f941128639ea368c1b727
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403101"
---
# <a name="simpleactivationfactory-class"></a>SimpleActivationFactory クラス

Windows ランタイムまたはクラシック COM の基底クラスを作成するための基本的なメカニズムを提供します。

## <a name="syntax"></a>構文

```cpp
template<typename Base>
class SimpleActivationFactory : public ActivationFactory<>;
```

### <a name="parameters"></a>パラメーター

*ベース*<br/>
基本クラスです。

## <a name="remarks"></a>Remarks

基底クラスには、既定のコンス トラクターを提供する必要があります。

次のコード例で SimpleActivationFactory を使用する方法を示します、 [ActivatableClassWithFactoryEx](activatableclass-macros.md)マクロ。

`ActivatableClassWithFactoryEx(MyClass, SimpleActivationFactory, MyServerName);`

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[SimpleActivationFactory::ActivateInstance メソッド](#activateinstance)|指定したインターフェイスのインスタンスを作成します。|
|[SimpleActivationFactory::GetRuntimeClassName メソッド](#getruntimeclassname)|指定されたクラスのインスタンスのランタイム クラス名を取得、*ベース*クラス テンプレート パラメーター。|
|[SimpleActivationFactory::GetTrustLevel メソッド](#gettrustlevel)|指定されたクラスのインスタンスの信頼レベルを取得、*ベース*クラス テンプレート パラメーター。|

## <a name="inheritance-hierarchy"></a>継承階層

`I0`

`ChainInterfaces`

`I0`

`RuntimeClassBase`

`ImplementsHelper`

`DontUseNewUseMake`

`RuntimeClassFlags`

`RuntimeClassBaseT`

`RuntimeClass`

`ActivationFactory`

`SimpleActivationFactory`

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="activateinstance"></a>Simpleactivationfactory::activateinstance メソッド

指定したインターフェイスのインスタンスを作成します。

```cpp
STDMETHOD( ActivateInstance )(
    _Deref_out_ IInspectable **ppvObject
);
```

#### <a name="parameters"></a>パラメーター

*ppvObject*<br/>
ときにこの操作が完了したらで指定されたオブジェクトのインスタンスへのポインター、`Base`クラス テンプレート パラメーター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

場合`__WRL_STRICT__`が定義されている、アサート エラーが生成クラス テンプレート パラメーターで指定された基本クラスから派生していない場合[RuntimeClass](runtimeclass-class.md)、WinRt または WinRtClassicComMix で構成されていないまたは[RuntimeClassType](runtimeclasstype-enumeration.md)列挙値。

## <a name="getruntimeclassname"></a>Simpleactivationfactory::getruntimeclassname メソッド

指定されたクラスのインスタンスのランタイム クラス名を取得、`Base`クラス テンプレート パラメーター。

```cpp
STDMETHOD( GetRuntimeClassName )(
    _Out_ HSTRING* runtimeName
);
```

#### <a name="parameters"></a>パラメーター

*runtimeName*<br/>
この操作の完了時、ランタイム クラス名。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

場合`__WRL_STRICT__`は、定義されている、assert エラーが発生して、クラスが指定されている場合、`Base`クラス テンプレート パラメーターはありませんから派生した[RuntimeClass](runtimeclass-class.md)、WinRt または WinRtClassicComMixで構成されていないまたは[RuntimeClassType](runtimeclasstype-enumeration.md)列挙値。

## <a name="gettrustlevel"></a>Simpleactivationfactory::gettrustlevel メソッド

指定されたクラスのインスタンスの信頼レベルを取得、`Base`クラス テンプレート パラメーター。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

#### <a name="parameters"></a>パラメーター

*trustLvl*<br/>
この操作が完了時は、現在のクラスのオブジェクトの信頼レベル。

### <a name="return-value"></a>戻り値

常に s_ok を返します。
