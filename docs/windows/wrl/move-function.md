---
title: Move 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::Move
helpviewer_keywords:
- Move function
ms.assetid: c9525426-97e8-4d8c-9877-b689d8a0dc67
ms.openlocfilehash: 1a03216197462090f38d3bc2065fe227f0667919
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2019
ms.locfileid: "54337310"
---
# <a name="move-function"></a>Move 関数

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
template<class T>
inline typename RemoveReference<T>::Type&& Move(
   _Inout_ T&& arg
);
```

### <a name="parameters"></a>パラメーター

*T*<br/>
引数の型。

*arg*<br/>
移動する引数。

## <a name="return-value"></a>戻り値

パラメーター *arg*参照または右辺値参照の特徴の後に存在する場合、削除されました。

## <a name="remarks"></a>Remarks

指定した引数を 1 つの場所から移動します。

詳細については、次を参照してください。、**移動セマンティクス**の[右辺値参照宣言子: & &](../../cpp/rvalue-reference-declarator-amp-amp.md)します。

## <a name="requirements"></a>必要条件

**ヘッダー:** internal.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)