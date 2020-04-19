---
title: _ASSERT、_ASSERTE、_ASSERT_EXPR マクロ
ms.date: 11/04/2016
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
- _ASSERTE
- ASSERTE
- _ASSERT
- _ASSERT_EXPR
helpviewer_keywords:
- debugging [CRT], using macros
- _ASSERTE macro
- macros, debugging with
- debug reporting macros
- _ASSERT macro
- _ASSERT_EXPR macro
ms.assetid: e98fd2a6-7f5e-4aa8-8fe8-e93490deba36
ms.openlocfilehash: efdf7852734d8367d053b1300cd32b8a9195d0cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70943757"
---
# <a name="_assert-_asserte-_assert_expr-macros"></a>_ASSERT、_ASSERTE、_ASSERT_EXPR マクロ

式を評価し、結果が**False**の場合はデバッグレポートを生成します (デバッグバージョンのみ)。

## <a name="syntax"></a>構文

```C
// Typical usage:
_ASSERT_EXPR( booleanExpression, message );
_ASSERT( booleanExpression );
_ASSERTE( booleanExpression );
```

### <a name="parameters"></a>パラメーター

*booleanExpression*<br/>
0 以外 (true) または 0 (false) に評価されるスカラー式 (ポインター式)。

*message*<br/>
レポートの一部として表示するワイド文字列。

## <a name="remarks"></a>Remarks

**_ASSERT_EXPR**、 **_ASSERT** 、および **_ASSERTE**マクロは、デバッグプロセス中に前提を確認するためのクリーンで簡単なメカニズムを備えたアプリケーションを提供します。 アプリケーションの製品版ビルドで呼び出されないようにするために `#ifdef` ステートメントで囲む必要がないため、これらのマクロには高い柔軟性があります。 この柔軟性は、 [_DEBUG](../../c-runtime-library/debug.md) マクロを使用することで実現されます。 **_ASSERT_EXPR**、 **_ASSERT** 、および **_ASSERTE**は、コンパイル時に **_debug**が定義されている場合にのみ使用できます。 **_Debug**が定義されていない場合、これらのマクロの呼び出しはプリプロセス中に削除されます。

**_ASSERT_EXPR**、 **_ASSERT** 、および **_ASSERTE**は、 *booleanExpression*引数を評価し、結果が**false** (0) の場合、診断メッセージを出力し、 [_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)を呼び出してデバッグレポートを生成します。 **_ASSERT**マクロは、単純な診断メッセージを出力します。 **_ASSERTE**には、メッセージ内の失敗した式の文字列形式が含まれ、 **_ASSERT_EXPR**は診断メッセージに*メッセージ*文字列を含めます。 *BooleanExpression*が0以外に評価された場合、これらのマクロは何も実行しません。

**_ASSERT_EXPR**、 **_ASSERT** 、 **_ASSERTE** invoke **_CrtDbgReportW**。これにより、すべての出力がワイド文字になります。 **_ASSERTE**では、unicode 文字が*booleanExpression*に正しく出力され、 **_ASSERT_EXPR**は unicode 文字を*メッセージ*に出力します。

**_ASSERTE**マクロは失敗した式を指定するため、 **_ASSERT_EXPR**では、生成されたレポートでメッセージを指定することができます。これにより、ユーザーはアプリケーションのソースコードを参照せずに問題を特定できます。 ただし、 **_ASSERT_EXPR**によって出力されるすべての*メッセージ*と **_ASSERTE**によって評価されるすべての式は、文字列定数としてアプリケーションの出力 (デバッグバージョン) ファイルに含まれるという点で欠点があります。 そのため、 **_ASSERT_EXPR**または **_ASSERTE**に多数の呼び出しが行われると、これらの式によって出力ファイルのサイズが大幅に増加する可能性があります。

[_CrtSetReportMode](crtsetreportmode.md) や [_CrtSetReportFile](crtsetreportfile.md) 関数で明示的に指定しない限り、以下と等しい設定を持つメッセージがポップアップ ダイアログ ボックスに表示されます。

```C
_CrtSetReportMode(CRT_ASSERT, _CRTDBG_MODE_WNDW);
````

**_CrtDbgReportW**は、現在のレポートモードまたは **_CRT_ASSERT**レポートの種類に定義されているファイルに基づいて、デバッグレポートを生成し、その出力先または変換先を決定します。 既定では、アサーション エラーとエラーは、デバッグ メッセージ ウィンドウに送られます。 [_CrtSetReportMode](crtsetreportmode.md) 関数と [_CrtSetReportFile](crtsetreportfile.md) 関数は、各レポートの種類の宛先を定義するために使用されます。

出力先がデバッグメッセージウィンドウで、ユーザーが **[再試行]** ボタンをクリックすると、 **_CrtDbgReportW**は1を返します。これにより、 **_ASSERT_EXPR**、 **_ASSERT** 、 **_ASSERTE**の各マクロによってデバッガーが起動されます。ジャストインタイム (JIT) デバッグが有効になります。

レポート処理の詳細については、 [_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md) 関数を参照してください。 アサーション失敗を解決し、これらのマクロをデバッグ エラーの処理機構として使用する方法の詳細については、「 [確認とレポートのためのマクロの使用](/visualstudio/debugger/macros-for-reporting)」を参照してください。

**_ASSERT**マクロに加えて、 [ASSERT](assert-macro-assert-wassert.md)マクロを使用してプログラムロジックを検証することもできます。 このマクロは、ライブラリのデバッグ バージョンとリリース バージョンの両方で使用できます。 [_RPT、_RPTF](rpt-rptf-rptw-rptfw-macros.md) デバッグ マクロをデバッグ レポート生成のために使用することもできますが、式の評価は行いません。 **_RPT**マクロは、単純なレポートを生成します。 **_RPTF**マクロには、生成されたレポートでレポートマクロが呼び出されたソースファイルと行番号が含まれています。 これらのマクロのワイド文字バージョンを使用できます ( **_RPTW**、 **_RPTFW**)。 ワイド文字バージョンは、ワイド文字列がすべての文字列パラメーターと出力で使用できるという点を除き、ナロー文字バージョンと同一です。

**_ASSERT_EXPR**、 **_ASSERT** 、 **_ASSERTE**はマクロであり、crtdbg.h > を\<含めることによって使用できますが、 **_debug**が定義されている場合、アプリケーションは C ランタイムライブラリのデバッグバージョンとリンクする必要があります。これらのマクロは、他のランタイム関数を呼び出します。

## <a name="requirements"></a>必要条件

|マクロ|必須ヘッダー|
|-----------|---------------------|
|**_ASSERT_EXPR**、 **_ASSERT**、 **_ASSERTE**|\<crtdbg.h>|

## <a name="example"></a>例

このプログラムでは、 **_ASSERT**マクロと **_ASSERTE**マクロが呼び出され、条件`string1 == string2`がテストされます。 条件が失敗した場合、これらのマクロは診断メッセージを出力します。 このプログラムでは、 **printf**関数の代わりに、マクロの **_RPT**と **_RPTF**のグループも実行されます。

```C
// crt_ASSERT_macro.c
// compile with: /D_DEBUG /MTd /Od /Zi /link /verbose:lib /debug
//
// This program uses the _ASSERT and _ASSERTE debugging macros.
//

#include <stdio.h>
#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main()
{
   char *p1, *p2;

   // The Reporting Mode and File must be specified
   // before generating a debug report via an assert
   // or report macro.
   // This program sends all report types to STDOUT.
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDOUT);
   _CrtSetReportMode(_CRT_ASSERT, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ASSERT, _CRTDBG_FILE_STDOUT);

   // Allocate and assign the pointer variables.
   p1 = (char *)malloc(10);
   strcpy_s(p1, 10, "I am p1");
   p2 = (char *)malloc(10);
   strcpy_s(p2, 10, "I am p2");

   // Use the report macros as a debugging
   // warning mechanism, similar to printf.
   // Use the assert macros to check if the
   // p1 and p2 variables are equivalent.
   // If the expression fails, _ASSERTE will
   // include a string representation of the
   // failed expression in the report.
   // _ASSERT does not include the
   // expression in the generated report.
   _RPT0(_CRT_WARN,
       "Use the assert macros to evaluate the expression p1 == p2.\n");
   _RPTF2(_CRT_WARN, "\n Will _ASSERT find '%s' == '%s' ?\n", p1, p2);
   _ASSERT(p1 == p2);

   _RPTF2(_CRT_WARN, "\n\n Will _ASSERTE find '%s' == '%s' ?\n",
          p1, p2);
   _ASSERTE(p1 == p2);

   _RPT2(_CRT_ERROR, "'%s' != '%s'\n", p1, p2);

   free(p2);
   free(p1);

   return 0;
}
```

```Output
Use the assert macros to evaluate the expression p1 == p2.
crt_ASSERT_macro.c(54) :
Will _ASSERT find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(55) : Assertion failed!
crt_ASSERT_macro.c(58) :

Will _ASSERTE find 'I am p1' == 'I am p2' ?
crt_ASSERT_macro.c(59) : Assertion failed: p1 == p2
'I am p1' != 'I am p2'
```

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[assert マクロ、_assert、_wassert](assert-macro-assert-wassert.md)<br/>
[_RPT、_RPTF、_RPTW、_RPTFW Macros](rpt-rptf-rptw-rptfw-macros.md)<br/>
