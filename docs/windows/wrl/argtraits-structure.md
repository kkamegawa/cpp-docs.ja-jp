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
ms.openlocfilehash: 17109508cf99888ccde79be39a41c5361da24c6e
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336469"
---
# <a name="argtraits-structure"></a>ArgTraits 構造体

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

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
Typename パラメーターことはできませんと一致する ArgTraits 構造体の`Invoke`メソッド シグネチャ。

*TDelegateInterface*<br/>
デリゲートのインターフェイスです。

*TArg1*<br/>
最初の引数の型、`Invoke`メソッド。

*TArg2*<br/>
2 番目の引数の型、`Invoke`メソッド。

*TArg3*<br/>
3 番目の引数の型、`Invoke`メソッド。

*TArg4*<br/>
4 番目の引数の型、`Invoke`メソッド。

*TArg5*<br/>
5 番目の引数の型、`Invoke`メソッド。

*TArg6*<br/>
6 番目の引数の型、`Invoke`メソッド。

*TArg7*<br/>
7 番目の引数の型、`Invoke`メソッド。

*TArg8*<br/>
8 番目の引数の型、`Invoke`メソッド。

*TArg9*<br/>
9 番目の引数の型、`Invoke`メソッド。

## <a name="remarks"></a>Remarks

`ArgTraits`構造体は、インターフェイス、およびパラメーターの数が指定された匿名のメンバー関数に指定したデリゲートを宣言します。

## <a name="members"></a>メンバー

### <a name="public-typedefs"></a>パブリック typedef

名前       | 説明
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

名前                     | 説明
------------------------ | ---------------------------------------------------------------------------------------
[Argtraits::args](#args) | パラメーターの数のカウントを保持、`Invoke`デリゲート インターフェイスのメソッド。

## <a name="inheritance-hierarchy"></a>継承階層

`ArgTraits`

## <a name="requirements"></a>必要条件

**ヘッダー:** event.h

**名前空間:** Microsoft::WRL::Details

## <a name="args"></a>Argtraits::args

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

```cpp
static const int args = -1;
```

### <a name="remarks"></a>Remarks

パラメーターの数のカウントを保持、`Invoke`デリゲート インターフェイスのメソッド。 ときに`args`-1 とに一致することができますなし、`Invoke`メソッド シグネチャ。
