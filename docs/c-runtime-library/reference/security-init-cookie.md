---
title: __security_init_cookie
ms.date: 11/04/2016
api_name:
- __security_init_cookie
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- security_init_cookie
- __security_init_cookie
helpviewer_keywords:
- security cookie [C++]
- __security_init_cookie function
- security_init_cookie function
- global security cookie
ms.assetid: 32119905-0897-4a1c-84ca-bffd16c9b2af
ms.openlocfilehash: 9f7e9924f4a96803749418d777e5ee2020f9df78
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948715"
---
# <a name="__security_init_cookie"></a>__security_init_cookie

グローバル セキュリティ クッキーを初期化します。

## <a name="syntax"></a>構文

```C
void __security_init_cookie(void);
```

## <a name="remarks"></a>Remarks

グローバル セキュリティ クッキーは、[/GS (バッファーのセキュリティ チェック)](../../build/reference/gs-buffer-security-check.md) を指定してコンパイルされたコードおよび例外処理を使用するコードでバッファー オーバーランから保護するために使用されます。 オーバーランから保護されている関数を開始するときにクッキーはスタックに配置され、関数が終了するときにスタックの値がグローバルなクッキーと比較されます。 違いがある場合はバッファー オーバーランが発生したことを意味し、プログラムは直ちに終了します。

通常、初期化時に**は、CRT**によってメソッドが呼び出されます。 たとえば、 [/entry](../../build/reference/entry-entry-point-symbol.md)を使用してエントリポイントを指定する場合など、CRT の初期化を省略した場合は、自分で **__ securityinitcookie**を呼び出す必要があります。 既定**値が指定**されていない場合は、グローバルセキュリティ cookie が既定値に設定され、バッファーオーバーランによる保護が損なわれます。 攻撃者はこの既定の cookie 値を悪用してバッファーオーバーランのチェックを破ることができるため、独自のエントリポイントを定義するときは常に、 **__ security_s**を呼び出すことをお勧めします。

オーバーランによって保護されている関数が入力される前に、その呼び出しを**行う必要が**あります。それ以外の場合は、擬似的なバッファーオーバーランが検出されます。 詳細については、「[C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)」(C ランタイム エラー R6035) をご覧ください。

## <a name="example"></a>例

「[C Runtime Error R6035](../../error-messages/tool-errors/c-runtime-error-r6035.md)」(C ランタイム エラー R6035) の例をご覧ください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**__security_init_cookie**|\<process.h>|

**__ securityinitcookie**は、標準の C ランタイムライブラリの Microsoft 拡張機能です。 (_s) 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[Microsoft セキュリティレスポンスセンター](https://www.microsoft.com/msrc?rtc=1)
