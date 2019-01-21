---
title: MakeAndInitialize 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAndInitialize
ms.assetid: 71ceeb12-d2a2-4317-b010-3dcde1b39467
ms.openlocfilehash: ba34b1fde546187e823a73a063bce9f69f4e7e89
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54336653"
---
# <a name="makeandinitialize-function"></a>MakeAndInitialize 関数

指定した Windows ランタイム クラスを初期化します。 同じモジュールで定義されているコンポーネントをインスタンス化するのにには、この関数を使用します。

## <a name="syntax"></a>構文

```cpp
template <
    typename T,
    typename I,
    typename TArg1,
    typename TArg2,
    typename TArg3,
    typename TArg4,
    typename TArg5,
    typename TArg6,
    typename TArg7,
    typename TArg8,
    typename TArg9>
HRESULT MakeAndInitialize(
    _Outptr_result_nullonfailure_ I** ppvObject,
    TArg1 &&arg1,
    TArg2 &&arg2,
    TArg3 &&arg3,
    TArg4 &&arg4,
    TArg5 &&arg5,
    TArg6 &&arg6,
    TArg7 &&arg7,
    TArg8 &&arg8,
    TArg9 &&arg9) throw()
```

### <a name="parameters"></a>パラメーター

*T*<br/>
ユーザー指定のクラスから継承する`WRL::RuntimeClass`します。

*TArg1*<br/>
指定されたランタイム クラスに渡される引数 1 の型。

*TArg2*<br/>
指定されたランタイム クラスに渡される引数 2 の型。

*TArg3*<br/>
指定されたランタイム クラスに渡される引数 3 の型。

*TArg4*<br/>
指定されたランタイム クラスに渡される引数 4 の型。

*TArg5*<br/>
指定されたランタイム クラスに渡される 5 引数の型。

*TArg6*<br/>
指定されたランタイム クラスに渡される 6 引数の型。

*TArg7*<br/>
指定されたランタイム クラスに渡される 7 引数の型。

*TArg8*<br/>
指定されたランタイム クラスに渡される 8 引数の型。

*TArg9*<br/>
指定されたランタイム クラスに渡される 9 引数の型。

*arg1*<br/>
指定されたランタイム クラスに渡される引数 1 です。

*arg2*<br/>
指定されたランタイム クラスに渡される引数 2

*arg3*<br/>
指定されたランタイム クラスに渡される引数 3 です。

*arg4*<br/>
指定されたランタイム クラスに渡される引数 4 です。

*arg5*<br/>
指定されたランタイム クラスに渡される引数 5 です。

*arg6*<br/>
指定されたランタイム クラスに渡される引数 6 です。

*arg7*<br/>
指定されたランタイム クラスに渡される引数 7 です。

*arg8*<br/>
指定されたランタイム クラスに渡される引数 8 です。

*arg9*<br/>
指定されたランタイム クラスに渡される引数 9 です。

## <a name="return-value"></a>戻り値

HRESULT 値。

## <a name="remarks"></a>Remarks

「[方法:WRL コンポーネント直接インスタンス化](how-to-instantiate-wrl-components-directly.md)についてはこの関数の相違点と[Microsoft::WRL::Make](make-function.md)、および例についてはします。

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)