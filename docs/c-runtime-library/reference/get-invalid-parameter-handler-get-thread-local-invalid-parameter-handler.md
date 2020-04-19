---
title: _get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler
ms.date: 11/04/2016
api_name:
- _get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
api_location:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _get_invalid_parameter_handler
- stdlib/_get_invalid_parameter_handler
- _get_thread_local_invalid_parameter_handler
- stdlib/_get_thread_local_invalid_parameter_handler
helpviewer_keywords:
- _get_thread_local_invalid_parameter_handler function
- _get_invalid_parameter_handler function
ms.assetid: a176da0e-38ca-4d99-92bb-b0e2b8072f53
ms.openlocfilehash: 572d21696d38c47fe0f67d68af5eb249aeb94319
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857807"
---
# <a name="_get_invalid_parameter_handler-_get_thread_local_invalid_parameter_handler"></a>_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler

CRT が無効な引数を検出したときに呼び出される関数を取得します。

## <a name="syntax"></a>構文

```C
_invalid_parameter_handler _get_invalid_parameter_handler(void);
_invalid_parameter_handler _get_thread_local_invalid_parameter_handler(void);
```

## <a name="return-value"></a>戻り値

現在設定されている無効なパラメーター ハンドラー関数を指すポインター、または何も設定されていない場合は Null ポインターです。

## <a name="remarks"></a>Remarks

**_Get_invalid_parameter_handler**関数は、現在設定されているグローバルの無効なパラメーターハンドラーを取得します。 無効なグローバル パラメーター ハンドラーが設定されていない場合は、Null ポインターを返します。 同様に、 **_get_thread_local_invalid_parameter_handler**は、呼び出されたスレッドの現在のスレッドローカルの無効なパラメーターハンドラーを取得します。ハンドラーが設定されていない場合は、null ポインターを取得します。 グローバルとスレッド ローカルの無効なパラメーター ハンドラーを設定する方法については、「[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)」を参照してください。

返される無効なパラメーター ハンドラー関数ポインターには、次の型があります。

```C
typedef void (__cdecl* _invalid_parameter_handler)(
    wchar_t const*,
    wchar_t const*,
    wchar_t const*,
    unsigned int,
    uintptr_t
    );
```

無効なパラメーター ハンドラーの詳細については、「[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)」内のプロトタイプを参照してください。

## <a name="requirements"></a>要件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_get_invalid_parameter_handler**、 **_get_thread_local_invalid_parameter_handler**|C: \<stdlib.h><br /><br /> C++: \<cstdlib> または \<stdlib.h>|

**_Get_invalid_parameter_handler**関数と **_get_thread_local_invalid_parameter_handler**関数は、Microsoft 固有の関数です。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>参照

[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[CRT 関数のセキュリティが強化されたバージョン](../../c-runtime-library/security-enhanced-versions-of-crt-functions.md)<br/>
