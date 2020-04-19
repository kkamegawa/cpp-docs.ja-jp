---
title: _invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson
ms.date: 11/04/2016
api_name:
- _invalid_parameter
- _invalid_parameter_noinfo
- _invalid_parameter_noinfo_noreturn
- _invoke_watson
api_location:
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- CORECRT/_invalid_parameter
- _invalid_parameter
- CORECRT/_invalid_parameter_noinfo
- _invalid_parameter_noinfo
- CORECRT/_invalid_parameter_noinfo_noreturn
- _invalid_parameter_noinfo_noreturn
- CORECRT/_invoke_watson
- _invoke_watson
ms.assetid: a4d6f1fd-ce56-4783-8719-927151a7a814
ms.openlocfilehash: b2714c140a2396d88c700689244c6ec04e12169c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70954607"
---
# <a name="_invalid_parameter-_invalid_parameter_noinfo-_invalid_parameter_noinfo_noreturn-_invoke_watson"></a>_invalid_parameter、_invalid_parameter_noinfo、_invalid_parameter_noinfo_noreturn、_invoke_watson

これらの関数は、CRT ライブラリ関数に渡された有効でないパラメーターを処理するために C ランタイム ライブラリによって使用されます。 有効でないパラメーターの既定の処理またはカスタマイズ可能な処理をサポートするために、自分のコードでこれらの関数を使用することもできます。

## <a name="syntax"></a>構文

```C
extern "C" void __cdecl
_invalid_parameter(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);

extern "C" void __cdecl
_invalid_parameter_noinfo(void);

extern "C" __declspec(noreturn) void __cdecl
_invalid_parameter_noinfo_noreturn(void);

extern "C" __declspec(noreturn) void __cdecl
_invoke_watson(
    wchar_t const* const expression,
    wchar_t const* const function_name,
    wchar_t const* const file_name,
    unsigned int   const line_number,
    uintptr_t      const reserved);
```

## <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
有効でないソース コード パラメーターの式を表す文字列。

*function_name*<br/>
ハンドラーを呼び出した関数の名前。

*file_name*<br/>
ハンドラーが呼び出されたソース コード ファイル。

*line_number*<br/>
ハンドラーが呼び出されたソース コードの行番号。

*reserved*<br/>
使用されません。

## <a name="return-value"></a>戻り値

これらの関数は値を返しません。 _Invalid_parameter_noinfo_noreturn 関数と関数は呼び出し元に戻りません **。また、** 場合によっては、呼び出し元に戻ら**ないこともあります** **(_t)** 。

## <a name="remarks"></a>Remarks

有効でないパラメーターが C ランタイム ライブラリ関数に渡された場合、ライブラリ関数は、*無効なパラメーター ハンドラー*を呼び出します。これは、いくつかの作業のうちのいずれかを行うためにプログラマによって指定された関数です。 たとえば、問題をユーザーにレポートする、ログに書き込む、デバッガーで中断する、プログラムを終了する、または何も行わない、などです。 プログラマによって関数が指定されていない場合**は、既定のハンドラーである**"既定のハンドラー" が呼び出されます。

既定では、有効でないパラメーターがデバッグコードで識別されると、CRT ライブラリ関数は verbose パラメーターを使用して関数の**パラメーター**を呼び出します。 非デバッグコードでは、空**のパラメーター**を使用して、**パラメーター**の関数を呼び出す (_t) 関数が呼び出されます。 非デバッグ CRT ライブラリ関数でプログラムの終了が必要な場合は、 **_invalid_parameter_noinfo_noreturn**関数が呼び出されます。この関数は、空のパラメーターを使用して**パラメーター**関数を呼び出し、その後に、次のように指定します。プログラムの終了を強制する watson 関数。

**パラメーター**関数は、ユーザー定義の無効なパラメーターハンドラーが設定されているかどうかを確認し、存在する場合はそれを呼び出します。 たとえば、現在のスレッドで [set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) の呼び出しでユーザー定義のスレッド ローカル ハンドラーが設定されている場合、それを呼び出し、次いでその関数は戻ります。 それ以外の場合、[set_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md) の呼び出しでユーザー定義の無効なグローバル パラメーター ハンドラーが設定されているなら、それを呼び出し、次いでその関数は戻ります。 それ以外の**場合は、既定のハンドラーが**呼び出されます。 既定**の動作では**、プログラムを終了します。 ユーザー定義のハンドラーは終了するか、戻るかのいずれかです。 確実に回復できるのでない限り、ユーザー定義のハンドラーでプログラムを終了することをお勧めします。

既定**のハンドラーが呼び出された**ときに、プロセッサが[__ fastfail](../../intrinsics/fastfail.md)操作をサポートしている場合は、 **FAST_FAIL_INVALID_ARG**のパラメーターを使用して呼び出され、プロセスが終了します。 それ以外の場合、Fail Fast 例外が発生します。これは、アタッチされているデバッガーでキャッチできます。 プロセスの継続が許可された場合、例外コードの状態**STATUS_INVALID_CRUNTIME_PARAMETER**を使用して、Windows **TerminateProcess**関数の呼び出しによって終了されます。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|------------------|
|**invalidparameter**、 **_invalid_parameter_noinfo_noreturn**、または**watson** (_d)、(_d)|\<corecrt.h >|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[関数リファレンス (アルファベット順)](crt-alphabetical-function-reference.md)<br/>
[_get_invalid_parameter_handler、_get_thread_local_invalid_parameter_handler](get-invalid-parameter-handler-get-thread-local-invalid-parameter-handler.md)<br/>
[_set_invalid_parameter_handler、_set_thread_local_invalid_parameter_handler](set-invalid-parameter-handler-set-thread-local-invalid-parameter-handler.md)<br/>
[パラメーターの検証](../../c-runtime-library/parameter-validation.md)<br/>
