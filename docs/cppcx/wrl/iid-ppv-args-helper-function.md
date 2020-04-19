---
title: IID_PPV_ARGS_Helper 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- client/IID_PPV_ARGS_Helper
helpviewer_keywords:
- IID_PPV_ARGS_Helper function
ms.assetid: afee9b23-8df1-4575-903f-e9ba748418f0
ms.openlocfilehash: e7733ae6084b64c20dff5a2c35d7a31c614d6e44
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500505"
---
# <a name="iid_ppv_args_helper-function"></a>IID_PPV_ARGS_Helper 関数

指定された引数の型が`IUnknown`インターフェイスから派生していることを確認します。

> [!IMPORTANT]
> このテンプレートの特殊化は WRL インフラストラクチャをサポートします。独自に作成したコードから直接使用するためのものではありません。 代わりに[IID_PPV_ARGS](/windows/win32/api/combaseapi/nf-combaseapi-iid_ppv_args)を使用してください。

## <a name="syntax"></a>構文

```cpp
template<typename T>
void** IID_PPV_ARGS_Helper(
   _Inout_ Microsoft::WRL::Details::ComPtrRef<T> pp
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
引数*pp*の型。

*ページ*<br/>
二重間接ポインター。

## <a name="return-value"></a>戻り値

**Void**へのポインターへのポインターにキャストする引数*pp* 。

## <a name="remarks"></a>Remarks

テンプレートパラメーター *T*がから`IUnknown`派生していない場合、コンパイル時エラーが生成されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** client.h

