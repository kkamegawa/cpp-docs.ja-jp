---
title: Make 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Make
helpviewer_keywords:
- Make function
ms.assetid: 66704143-df99-4a95-904d-ed99607e1034
ms.openlocfilehash: b45337ef773f93968570f62ab73c02d11fae88ff
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398194"
---
# <a name="make-function"></a>Make 関数

指定した Windows ランタイム クラスを初期化します。 同じモジュールで定義されているコンポーネントをインスタンス化するのにには、この関数を使用します。

## <a name="syntax"></a>構文

```cpp
template <
   typename T,
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
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8,
   TArg9 &&arg9
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7,
   typename TArg8
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7,
   TArg8 &&arg8
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6,
   typename TArg7
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6,
   TArg7 &&arg7
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5,
   typename TArg6
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5,
   TArg6 &&arg6
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4,
   typename TArg5
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4,
   TArg5 &&arg5
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3,
   typename TArg4
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3,
   TArg4 &&arg4
);
template <
   typename T,
   typename TArg1,
   typename TArg2,
   typename TArg3
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2,
   TArg3 &&arg3
);
template <
   typename T,
   typename TArg1,
   typename TArg2
>
ComPtr<T> Make(
   TArg1 &&arg1,
   TArg2 &&arg2
);
template <
   typename T,
   typename TArg1
>
ComPtr<T> Make(
   TArg1 &&arg1
);
template <
   typename T
>
ComPtr<T> Make();
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

A`ComPtr<T>`成功。 それ以外の場合は、オブジェクト`nullptr`します。

## <a name="remarks"></a>Remarks

「[方法:WRL コンポーネント直接インスタンス化](how-to-instantiate-wrl-components-directly.md)についてはこの関数の相違点と[Microsoft::WRL::Details::MakeAndInitialize](makeandinitialize-function.md)、および例についてはします。

## <a name="requirements"></a>必要条件

**ヘッダー:** implements.h

**名前空間:** Microsoft::wrl

## <a name="see-also"></a>関連項目

[Microsoft::WRL 名前空間](microsoft-wrl-namespace.md)