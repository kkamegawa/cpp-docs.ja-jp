---
title: _status87、_statusfp、_statusfp2
ms.date: 04/05/2018
api_name:
- _statusfp2
- _statusfp
- _status87
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
- _statusfp2
- _statusfp
- statusfp2
- _status87
- status87
- statusfp
helpviewer_keywords:
- floating-point functions, getting status word
- floating-point numbers, status word
- status87 function
- status word, getting floating point
- statusfp function
- _statusfp function
- _statusfp2 function
- statusfp2 function
- _status87 function
- floating-point functions
- status word
ms.assetid: 7ef963fa-b1fb-429d-94d6-fbf282ab7432
ms.openlocfilehash: 54faf70296ef41f2682f88a8edaa82ee0d2071d4
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70958092"
---
# <a name="_status87-_statusfp-_statusfp2"></a>_status87、_statusfp、_statusfp2

浮動小数点ステータス ワードを取得します。

## <a name="syntax"></a>構文

```C
unsigned int _status87( void );
unsigned int _statusfp( void );
void _statusfp2(unsigned int *px86, unsigned int *pSSE2)
```

### <a name="parameters"></a>パラメーター

*px86*<br/>
このアドレスには、x87 浮動小数点ユニットのステータス ワードが格納されます。

*pSSE2*<br/>
このアドレスには、SSE2 浮動小数点ユニットのステータス ワードが格納されます。

## <a name="return-value"></a>戻り値

**_Status87**と **_statusfp**の場合、返される値のビットは、浮動小数点の状態を示します。 「FLOAT」を参照してください。H **_statusfp**によって返されるビットの定義のためのインクルードファイル。 多くの数値演算ライブラリ関数は、予測できない結果を使用して浮動小数点ステータス ワードを変更します。 最適化では、 **_status87**、 **_statusfp**、および関連する関数の呼び出しに関する浮動小数点演算の順序変更、結合、および削除を行うことができます。 浮動小数点演算の順序を変更する最適化を防ぐには、[/Od (無効 (デバッグ))](../../build/reference/od-disable-debug.md) コンパイラ オプションまたは [fenv_access](../../preprocessor/fenv-access.md) プラグマ ディレクティブを使用します。 浮動小数点ステータスワードの既知の状態間で浮動小数点演算がほとんど実行されない場合は、 **_clearfp**と **_statusfp**の戻り値、および **_statusfp2**の戻り値のパラメーターも信頼性が高くなります。

## <a name="remarks"></a>Remarks

**_Statusfp**関数は、浮動小数点ステータスワードを取得します。 ステータス ワードとは、浮動小数点例外によって検出された浮動小数点プロセッサのステータスやその他の条件 (浮動小数点スタック オーバーフローおよびアンダーフローなど) の組み合わせです。 マスクされていない例外は、ステータス ワードのコンテンツが返される前にチェックされます。 これは、呼び出し元に保留中の例外を通知することを意味します。 X86 プラットフォームでは、 **_statusfp**は X87 および SSE2 浮動小数点のステータスの組み合わせを返します。 x64 プラットフォームでは、返される状態は、SSE の MXCSR の状態に基づいています。 ARM プラットフォームでは、 **_statusfp**は fpscr レジスタから状態を返します。

**_statusfp**は、プラットフォームに依存しない、ポータブルバージョンの **_status87**です。 これは Intel (x86) プラットフォームの **_status87**と同じであり、X64 および ARM プラットフォームでもサポートされています。 浮動小数点コードをすべてのアーキテクチャに移植できるようにするには、 **_statusfp**を使用します。 X86 プラットフォームのみを対象としている場合は、 **_status87**または **_statusfp**のいずれかを使用できます。

X87 と SSE2 の両方の浮動小数点プロセッサを持つチップ (Pentium IV など) には **_statusfp2**をお勧めします。 **_Statusfp2**の場合、x87 または SSE2 浮動小数点プロセッサの両方について、浮動小数点ステータスワードを使用してアドレスが入力されます。 X87 および SSE2 浮動小数点プロセッサをサポートするチップの場合、EM_AMBIGUOUS は1に設定されています。これは、 **_statusfp**または **_controlfp**が使用され、アクションが x87 または SSE2 浮動小数点ステータスワードを参照している可能性があるためです。 **_Statusfp2**関数は、x86 プラットフォームでのみサポートされています。

共通言語ランタイム (CLR) は浮動小数点の既定の精度のみをサポートするため、これらの関数は[/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)には役立ちません。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_status87**、 **_statusfp**、 **_statusfp2**|\<float.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_statusfp.c
// Build by using: cl /W4 /Ox /nologo crt_statusfp.c
// This program creates various floating-point errors and
// then uses _statusfp to display messages that indicate these problems.

#include <stdio.h>
#include <float.h>
#pragma fenv_access(on)

double test( void )
{
   double a = 1e-40;
   float b;
   double c;

   printf("Status = 0x%.8x - clear\n", _statusfp());

   // Assignment into b is inexact & underflows:
   b = (float)(a + 1e-40);
   printf("Status = 0x%.8x - inexact, underflow\n", _statusfp());

   // c is denormal:
   c = b / 2.0;
   printf("Status = 0x%.8x - inexact, underflow, denormal\n",
            _statusfp());

   // Clear floating point status:
   _clearfp();
   return c;
}

int main(void)
{
   return (int)test();
}
```

```Output
Status = 0x00000000 - clear
Status = 0x00000003 - inexact, underflow
Status = 0x00080003 - inexact, underflow, denormal
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
