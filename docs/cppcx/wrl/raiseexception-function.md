---
title: RaiseException 関数
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- internal/Microsoft::WRL::Details::RaiseException
helpviewer_keywords:
- RaiseException function
ms.assetid: f9c74f6d-112a-4d2e-900f-622f795d5dbf
ms.openlocfilehash: 08305c5d59d7e272aac87ad9aa183c8e82588632
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62231354"
---
# <a name="raiseexception-function"></a>RaiseException 関数

WRL インフラストラクチャをサポートし、コードから直接使用するものではありません。

## <a name="syntax"></a>構文

```cpp
inline void __declspec(noreturn)   RaiseException(
      HRESULT hr,
      DWORD dwExceptionFlags = EXCEPTION_NONCONTINUABLE);
```

### <a name="parameters"></a>パラメーター

*hr*<br/>
中に発生します。 例外の例外コード失敗した操作の HRESULT。

*dwExceptionFlags*<br/>
継続可能の例外 (フラグの値は 0)、または (フラグの値が 0 以外) noncontinuable の例外を示すフラグ。 既定では、例外は、継続不可能は。

## <a name="remarks"></a>Remarks

呼び出し元のスレッドで例外が発生します。

詳細については、Windows を参照してください。`RaiseException`関数。

## <a name="requirements"></a>必要条件

**ヘッダー:** internal.h

**名前空間:** Microsoft::WRL::Details

## <a name="see-also"></a>関連項目

[Microsoft::WRL::Details 名前空間](microsoft-wrl-details-namespace.md)