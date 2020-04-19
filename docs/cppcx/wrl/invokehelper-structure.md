---
title: InvokeHelper 構造体
ms.date: 10/18/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::InvokeHelper
- event/Microsoft::WRL::Details::InvokeHelper::callback_
- event/Microsoft::WRL::Details::InvokeHelper::Invoke
- event/Microsoft::WRL::Details::InvokeHelper::InvokeHelper
helpviewer_keywords:
- Microsoft::WRL::Details::InvokeHelper structure
- Microsoft::WRL::Details::callback_ data member
- Microsoft::WRL::Details::Invoke method
- Microsoft::WRL::Details::InvokeHelper, constructor
ms.assetid: 555ad2bc-4dd6-4e65-a2e2-1242c395f0e5
ms.openlocfilehash: 3fcba210d4018d22487d234b437acfee3634cec6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386136"
---
# <a name="invokehelper-structure"></a>InvokeHelper 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template<typename TDelegateInterface, typename TCallback, unsigned int argCount>
struct InvokeHelper;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 0> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 1> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 2> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 3> :
    public Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 4> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 5> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 6> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 7> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 8> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;

template<typename TDelegateInterface, typename TCallback>
struct InvokeHelper<TDelegateInterface, TCallback, 9> :
    Microsoft::WRL::RuntimeClass<
        RuntimeClassFlags<Delegate>,
        TDelegateInterface
    >;
```

### <a name="parameters"></a>パラメーター

*TDelegateInterface*<br/>
デリゲートのインターフェイス型。

*TCallback*<br/>
イベント ハンドラー関数の型。

*argCount*<br/>
引数の数、`InvokeHelper`特殊化します。

## <a name="remarks"></a>Remarks

実装を提供、`Invoke()`方法、指定した数値と引数の型に基づいています。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前     | 説明
-------- | -----------------------------------------------------------------------------
`Traits` | 各イベント ハンドラーの引数の型を定義するクラスのシノニムです。

### <a name="public-constructors"></a>パブリック コンストラクター

名前                                        | 説明
------------------------------------------- | -------------------------------------------------------
[Invokehelper::invokehelper](#invokehelper) | `InvokeHelper` クラスの新しいインスタンスを初期化します。

### <a name="public-methods"></a>パブリック メソッド

名前                            | 説明
------------------------------- | -----------------------------------------------------------------------------------
[Invokehelper::invoke](#invoke) | 指定した数の引数を含むシグネチャを持つイベント ハンドラーを呼び出します。

### <a name="public-data-members"></a>パブリック データ メンバー

名前                                 | 説明
------------------------------------ | ----------------------------------------------------------
[InvokeHelper::callback_](#callback) | イベントが発生したときに呼び出すイベント ハンドラーを表します。

## <a name="inheritance-hierarchy"></a>継承階層

`InvokeHelper`

## <a name="requirements"></a>必要条件

**ヘッダー:** event.h

**名前空間:** Microsoft::WRL::Details

## <a name="callback"></a>Invokehelper::callback _

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
TCallback callback_;
```

### <a name="remarks"></a>Remarks

イベントが発生したときに呼び出すイベント ハンドラーを表します。

`TCallback`テンプレート パラメーターは、イベント ハンドラーの種類を指定します。

## <a name="invoke"></a>Invokehelper::invoke

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
STDMETHOD(
   Invoke
)();
STDMETHOD(
   Invoke
)(typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
STDMETHOD(
   Invoke
)( typename Traits;
```

### <a name="parameters"></a>パラメーター

*arg1*<br/>
引数 1 です。

*arg2*<br/>
引数 2 を指定します。

*arg3*<br/>
引数 3 です。

*arg4*<br/>
4 の引数。

*arg5*<br/>
5 の引数。

*arg6*<br/>
引数 6 です。

*arg7*<br/>
7 の引数。

*arg8*<br/>
8 の引数。

*arg9*<br/>
9 の引数。

### <a name="return-value"></a>戻り値

成功した場合は s_ok を返します。それ以外の場合、エラーを示す HRESULT。

### <a name="remarks"></a>Remarks

指定した数の引数を含むシグネチャを持つイベント ハンドラーを呼び出します。

## <a name="invokehelper"></a>Invokehelper::invokehelper

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
explicit InvokeHelper(
   TCallback callback
);
```

### <a name="parameters"></a>パラメーター

*callback*<br/>
イベント ハンドラー。

### <a name="remarks"></a>Remarks

`InvokeHelper` クラスの新しいインスタンスを初期化します。

`TCallback`テンプレート パラメーターは、イベント ハンドラーの種類を指定します。
