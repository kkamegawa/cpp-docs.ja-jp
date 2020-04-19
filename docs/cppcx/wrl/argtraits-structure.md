---
title: ArgTraits 構造体
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::ArgTraits
- event/Microsoft::WRL::Details::ArgTraits::args
helpviewer_keywords:
- Microsoft::WRL::Details::ArgTraits structure
- Microsoft::WRL::Details::ArgTraits::args constant
ms.assetid: 58ae4115-c1bc-48c8-b01b-e60554841c30
ms.openlocfilehash: c13e7fec3289b66b40e44f91404a50cba7a473b1
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821715"
---
# <a name="argtraits-structure"></a>ArgTraits 構造体

は WRL インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。

## <a name="syntax"></a>構文

```cpp
template<typename TMemberFunction>
struct ArgTraits;

template<typename TDelegateInterface>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(void)>;

template<typename TDelegateInterface, typename TArg1>
struct ArgTraits<HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1)>;

template<typename TDelegateInterface, typename TArg1, typename TArg2>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)(TArg1, TArg2, TArg3)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8)>;

template<
    typename TDelegateInterface,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9
>
struct ArgTraits<
    HRESULT (STDMETHODCALLTYPE TDelegateInterface::*)
             (TArg1, TArg2, TArg3, TArg4, TArg5, TArg6, TArg7, TArg8, TArg9)>;
```

### <a name="parameters"></a>パラメーター

*TMemberFunction*<br/>
`Invoke` メソッドシグネチャと一致しない ArgTraits 構造体の Typename パラメーター。

*TDelegateInterface*<br/>
デリゲートインターフェイス。

*TArg1*<br/>
`Invoke` メソッドの1番目の引数の型。

*TArg2*<br/>
`Invoke` メソッドの2番目の引数の型。

*TArg3*<br/>
`Invoke` メソッドの3番目の引数の型。

*TArg4*<br/>
`Invoke` メソッドの4番目の引数の型。

*TArg5*<br/>
`Invoke` メソッドの5番目の引数の型。

*TArg6*<br/>
`Invoke` メソッドの6番目の引数の型。

*TArg7*<br/>
`Invoke` メソッドの7番目の引数の型。

*TArg8*<br/>
`Invoke` メソッドの8番目の引数の型。

*TArg9*<br/>
`Invoke` メソッドの9番目の引数の型。

## <a name="remarks"></a>Remarks

`ArgTraits` 構造体は、指定されたデリゲートインターフェイスと、指定された数のパラメーターを持つ匿名メンバー関数を宣言します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック Typedef

[名前]       | 説明
---------- | ----------------------
`Arg1Type` | TArg1 の typedef。
`Arg2Type` | TArg2 の typedef。
`Arg3Type` | TArg3 の typedef。
`Arg4Type` | TArg4 の typedef。
`Arg5Type` | TArg5 の typedef。
`Arg6Type` | TArg6 の typedef。
`Arg7Type` | TArg7 の typedef。
`Arg8Type` | TArg8 の typedef。
`Arg9Type` | TArg9 の typedef。

### <a name="public-constants"></a>パブリック定数

[名前]                     | 説明
------------------------ | ---------------------------------------------------------------------------------------
[ArgTraits:: args](#args) | デリゲートインターフェイスの `Invoke` メソッドのパラメーター数のカウントを保持します。

## <a name="inheritance-hierarchy"></a>継承階層

`ArgTraits`

## <a name="requirements"></a>要件

**ヘッダー:** イベント .h

**名前空間:** Microsoft:: WRL::D etails

## <a name="args"></a>ArgTraits:: args

は WRL インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Remarks

デリゲートインターフェイスの `Invoke` メソッドのパラメーター数のカウントを保持します。 `args` が-1 の場合、`Invoke` メソッドシグネチャに一致することはできません。
