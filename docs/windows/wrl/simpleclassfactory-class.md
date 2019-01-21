---
title: SimpleClassFactory クラス
ms.date: 09/7/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::SimpleClassFactory
- module/Microsoft::WRL::SimpleClassFactory::CreateInstance
helpviewer_keywords:
- Microsoft::WRL::SimpleClassFactory class
- Microsoft::WRL::SimpleClassFactory::CreateInstance method
ms.assetid: 6edda1b2-4e44-4e14-9364-72f519249962
ms.openlocfilehash: 9a4c169944d56b693efa681bf7089636477012ea
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336466"
---
# <a name="simpleclassfactory-class"></a>SimpleClassFactory クラス

基底クラスを作成するための基本的なメカニズムを提供します。

## <a name="syntax"></a>構文

```cpp
template<typename Base>
class SimpleClassFactory : public ClassFactory<>;
```

### <a name="parameters"></a>パラメーター

*ベース*<br/>
基本クラスです。

## <a name="remarks"></a>Remarks

基底クラスには、既定のコンス トラクターを提供する必要があります。

次のコード例は、使用する方法を示します`SimpleClassFactory`で、 [ActivatableClassWithFactoryEx](activatableclass-macros.md)マクロ。

`ActivatableClassWithFactoryEx(MyClass, SimpleClassFactory, MyServerName);`

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[SimpleClassFactory::CreateInstance メソッド](#createinstance)|指定したインターフェイスのインスタンスを作成します。|

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

`ClassFactory`

`SimpleClassFactory`

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="createinstance"></a>Simpleclassfactory::createinstance メソッド

指定したインターフェイスのインスタンスを作成します。

```cpp
STDMETHOD( CreateInstance )(
   _Inout_opt_ IUnknown* pUnkOuter,
   REFIID riid,
   _Deref_out_ void** ppvObject
);
```

#### <a name="parameters"></a>パラメーター

*pUnkOuter*<br/>
必要があります`nullptr`、それ以外の戻り値は CLASS_E_NOAGGREGATION します。

SimpleClassFactory には、集計をサポートしていません。 集計がサポートされており、作成されるオブジェクト、集計の一部であった*pUnkOuter*制御へのポインターになります`IUnknown`集計のインターフェイス。

*riid*<br/>
インターフェイスを作成するには、オブジェクトの ID。

*ppvObject*<br/>
ときにこの操作が完了したらで指定されたオブジェクトのインスタンスへのポインター、 *riid*パラメーター。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合はエラーを示す HRESULT。

### <a name="remarks"></a>Remarks

場合`__WRL_STRICT__`が定義されている、アサート エラーが生成クラス テンプレート パラメーターで指定された基本クラスから派生していない場合[RuntimeClass](runtimeclass-class.md)、ClassicCom または WinRtClassicComMix で構成されていないまたは[RuntimeClassType](runtimeclasstype-enumeration.md)列挙値。
