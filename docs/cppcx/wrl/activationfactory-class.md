---
title: ActivationFactory クラス
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::ActivationFactory
- module/Microsoft::WRL::ActivationFactory::AddRef
- module/Microsoft::WRL::ActivationFactory::GetIids
- module/Microsoft::WRL::ActivationFactory::GetRuntimeClassName
- module/Microsoft::WRL::ActivationFactory::GetTrustLevel
- module/Microsoft::WRL::ActivationFactory::QueryInterface
- module/Microsoft::WRL::ActivationFactory::Release
helpviewer_keywords:
- Microsoft::WRL::ActivationFactory class
- Microsoft::WRL::ActivationFactory::ActivationFactory, constructor
- Microsoft::WRL::ActivationFactory::AddRef method
- Microsoft::WRL::ActivationFactory::GetIids method
- Microsoft::WRL::ActivationFactory::GetRuntimeClassName method
- Microsoft::WRL::ActivationFactory::GetTrustLevel method
- Microsoft::WRL::ActivationFactory::QueryInterface method
- Microsoft::WRL::ActivationFactory::Release method
ms.assetid: 5faddf1f-43b6-4f8a-97de-8c9d3ae1e1ff
ms.openlocfilehash: 8e5132f4a8711f6420cd9b52751550a96d10d8fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62303891"
---
# <a name="activationfactory-class"></a>ActivationFactory クラス

1 つ以上のクラスを Windows ランタイムによってアクティブ化できるようにします。

## <a name="syntax"></a>構文

```cpp
template <
    typename I0 = Details::Nil,
    typename I1 = Details::Nil,
    typename I2 = Details::Nil
>
class ActivationFactory :
    public Details::RuntimeClass<
        typename Details::InterfaceListHelper<
            IActivationFactory,
            I0,
            I1,
            I2,
            Details::Nil
        >::TypeT,
        RuntimeClassFlags<WinRt | InhibitWeakReference>,
        false
    >;
```

### <a name="parameters"></a>パラメーター

*I0*<br/>
0 番目のインターフェイスです。

*I1*<br/>
最初のインターフェイス。

*I2*<br/>
2 番目のインターフェイス。

## <a name="remarks"></a>Remarks

`ActivationFactory` 登録メソッドとの基本的な機能を提供します、`IActivationFactory`インターフェイス。 `ActivationFactory` カスタム ファクトリの実装を提供することもできます。

次のコード フラグメントでは、シンボリック ActivationFactory を使用する方法を示しています。

[!code-cpp[wrl-microsoft__wrl__activationfactory#1](../codesnippet/CPP/activationfactory-class_1.cpp)]

次のコード フラグメントは、使用する方法を示します、[実装](implements-structure.md)3 つ以上のインターフェイス Id を指定する構造体。

`struct MyFactory : ActivationFactory<Implements<I1, I2, I3>, I4, I5>;`

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                                       | 説明
---------------------------------------------------------- | ------------------------------------------
[ActivationFactory::ActivationFactory](#activationfactory) | 初期化します、`ActivationFactory`クラス。

### <a name="public-methods"></a>パブリック メソッド

名前                                                           | 説明
-------------------------------------------------------------- | --------------------------------------------------------------------------------------------
[ActivationFactory::AddRef](#addref)                           | 現在の参照カウントをインクリメント`ActivationFactory`オブジェクト。
[ActivationFactory::GetIids](#getiids)                         | 実装されたインターフェイス Id の配列を取得します。
[ActivationFactory::GetRuntimeClassName](#getruntimeclassname) | オブジェクトのランタイム クラス名を取得、現在`ActivationFactory`をインスタンス化します。
[Activationfactory::gettrustlevel](#gettrustlevel)             | オブジェクトの信頼レベルを取得、現在`ActivationFactory`をインスタンス化します。
[ActivationFactory::QueryInterface](#queryinterface)           | 指定したインターフェイスへのポインターを取得します。
[ActivationFactory::Release](#release)                         | 現在の参照カウントをデクリメント`ActivationFactory`オブジェクト。

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

## <a name="requirements"></a>必要条件

**ヘッダー:** module.h

**名前空間:** Microsoft::wrl

## <a name="activationfactory"></a>ActivationFactory::ActivationFactory

初期化します、`ActivationFactory`クラス。

```cpp
ActivationFactory();
```

## <a name="addref"></a>ActivationFactory::AddRef

現在の参照カウントをインクリメント`ActivationFactory`オブジェクト。

```cpp
STDMETHOD_(
   ULONG,
   AddRef
)();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合は失敗を示す HRESULT。

## <a name="getiids"></a>ActivationFactory::GetIids

実装されたインターフェイス Id の配列を取得します。

```cpp
STDMETHOD(
   GetIids
)(_Out_ ULONG *iidCount, _Deref_out_ _Deref_post_cap_(*iidCount) IID **iids);
```

### <a name="parameters"></a>パラメーター

*iidCount*<br/>
ときにこの操作が完了すると、インターフェイス Id の数、 *iid*配列。

*iid*<br/>
この操作が完了したらの配列は、インターフェイス Id を実装します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合は失敗を示す HRESULT。 E_OUTOFMEMORY は、可能性のあるエラーの HRESULT です。

## <a name="getruntimeclassname"></a>ActivationFactory::GetRuntimeClassName

オブジェクトのランタイム クラス名を取得、現在`ActivationFactory`をインスタンス化します。

```cpp
STDMETHOD(
   GetRuntimeClassName
)(_Out_ HSTRING* runtimeName);
```

### <a name="parameters"></a>パラメーター

*runtimeName*<br/>
ときにこの操作が完了すると、オブジェクトのランタイム クラス名を含む文字列を識別するハンドルを現在`ActivationFactory`をインスタンス化します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合は失敗を示す HRESULT。

## <a name="gettrustlevel"></a>Activationfactory::gettrustlevel

オブジェクトの信頼レベルを取得、現在`ActivationFactory`をインスタンス化します。

```cpp
STDMETHOD(
   GetTrustLevel
)(_Out_ TrustLevel* trustLvl);
```

### <a name="parameters"></a>パラメーター

*trustLvl*<br/>
この操作が完了したら、信頼レベルのランタイム クラス、`ActivationFactory`をインスタンス化します。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、アサーション エラーが発生したと*trustLvl*に設定されている`FullTrust`します。

## <a name="queryinterface"></a>ActivationFactory::QueryInterface

指定したインターフェイスへのポインターを取得します。

```cpp
STDMETHOD(
   QueryInterface
)(REFIID riid, _Deref_out_ void **ppvObject);
```

### <a name="parameters"></a>パラメーター

*riid*<br/>
インターフェイス ID。

*ppvObject*<br/>
この操作が完了すると、パラメーターで指定されたインターフェイスへのポインター *riid*します。

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合は失敗を示す HRESULT。

## <a name="release"></a>ActivationFactory::Release

現在の参照カウントをデクリメント`ActivationFactory`オブジェクト。

```cpp
STDMETHOD_(
   ULONG,
   Release
)();
```

### <a name="return-value"></a>戻り値

成功した場合は S_OK、そうでない場合は失敗を示す HRESULT。
