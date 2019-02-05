---
title: IID_PPV_ARGS_Helper 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: 5ef4dd6c9db2d19e0c8a4143c5b4ed3f0ac75f6a
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894121"
---
# <a name="iidppvargshelper-function"></a>IID_PPV_ARGS_Helper 関数

指定された引数の型から派生することを確認、`IUnknown`インターフェイス。

> [!IMPORTANT]
> このテンプレートの特殊化は WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。 使用[IID_PPV_ARGS](/windows/desktop/api/combaseapi/nf-combaseapi-iid_ppv_args)代わりにします。

## <a name="syntax"></a>構文

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
引数の型*pp*します。

*pp*<br/>
二重間接ポインター。

## <a name="return-value"></a>戻り値

引数*pp*ポインターにする-、- へのポインターにキャスト**void**します。

## <a name="remarks"></a>Remarks

コンパイル時エラーが生成テンプレート パラメーター *T*から派生していない`IUnknown`します。

## <a name="requirements"></a>必要条件

**ヘッダー:** client.h

