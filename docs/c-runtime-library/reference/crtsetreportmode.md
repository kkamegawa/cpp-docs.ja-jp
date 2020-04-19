---
title: _CrtSetReportMode
ms.date: 11/04/2016
api_name:
- _CrtSetReportMode
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
- _CrtSetReportMode
- CrtSetReportMode
helpviewer_keywords:
- _CrtSetReportMode function
- CrtSetReportMode function
ms.assetid: 3ecc6a12-afdd-4242-b046-8187ff6d4b36
ms.openlocfilehash: ae7e83ac009d572f8a9f6484519b0cdfb7499ce3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938462"
---
# <a name="_crtsetreportmode"></a>_CrtSetReportMode

**_CrtDbgReport**によって生成される特定のレポートの種類の出力先、および[_ASSERT、_ASSERTE、_ASSERT_EXPR macros](assert-asserte-assert-expr-macros.md)、_ASSERT、_ASSERTE、_ などの[_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)を呼び出すすべてのマクロの宛先を指定します。 [ASSERT_EXPR マクロ](assert-asserte-assert-expr-macros.md)、 [_RPT、_RPTF、_RPTW、_RPTFW マクロ](rpt-rptf-rptw-rptfw-macros.md)、_RPT、_RPTF、_RPTW、 [_RPTFW マクロ](rpt-rptf-rptw-rptfw-macros.md)(デバッグバージョンのみ)。

## <a name="syntax"></a>構文

```C
int _CrtSetReportMode(
   int reportType,
   int reportMode
);
```

### <a name="parameters"></a>パラメーター

*reportType*<br/>
レポートの種類: **_CRT_WARN**、 **_CRT_ERROR**、および **_CRT_ASSERT**。

*reportMode*<br/>
*ReportType*の新しいレポートモードまたはモード。

## <a name="return-value"></a>戻り値

正常に完了すると、 **_CrtSetReportMode**は、 *reportType*で指定されたレポートの種類に対して以前のレポートモードを返します。 無効な値が*reportType*として渡された場合、または*reportmode*に無効なモードが指定されている場合、 **_CrtSetReportMode**は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、この関数は**errno**を**EINVAL**に設定し、-1 を返します。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_CrtSetReportMode** **_CrtDbgReport**の出力先を指定します。 マクロ[_ASSERT](assert-asserte-assert-expr-macros.md)、 [_ASSERTE](assert-asserte-assert-expr-macros.md)、 [_RPT](rpt-rptf-rptw-rptfw-macros.md)、および[_RPTF](rpt-rptf-rptw-rptfw-macros.md)は **_CrtDbgReport**を呼び出しているため、 **_CrtSetReportMode**はマクロで指定されたテキストの出力先を指定します。

[_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtSetReportMode**の呼び出しはプリプロセス中に削除されます。

**_CrtSetReportMode**を呼び出してメッセージの出力先を定義しない場合は、次の既定値が有効になります。

- アサーション エラーとエラーは、デバッグ メッセージ ウィンドウに送られます。

- Windows アプリケーションからの警告は、デバッガーの出力ウィンドウに送られます。

- コンソール アプリケーションからの警告は表示されません。

次の表は、Crtdbg.h で定義されているレポートの種類の一覧です。

|レポートの種類|説明|
|-----------------|-----------------|
|**_CRT_WARN**|早急の対応を必要としない警告、メッセージ、および情報。|
|**_CRT_ERROR**|エラー、回復不能な問題、および早急の対応を必要とする問題。|
|**_CRT_ASSERT**|アサーションエラー ( **FALSE**に評価されるアサート式)。|

**_CrtSetReportMode**関数は、 *reportmode*で指定された新しいレポートモードを*reportType*で指定されたレポートの種類に割り当て、以前に定義した*reportType*のレポートモードを返します。 次の表に、 *Reportmode*に使用できる選択肢と、 **_CrtDbgReport**の結果の動作を示します。 これらのオプションは、Crtdbg.h でビット フラグとして定義されています。

|レポート モード|_CrtDbgReport の動作|
|-----------------|-----------------------------|
|**_CRTDBG_MODE_DEBUG**|デバッガーの出力ウィンドウにメッセージを書き込みます。|
|**_CRTDBG_MODE_FILE**|ユーザーが指定したファイル ハンドルにメッセージを書き込みます。 書き込み先として使用する特定のファイルまたはストリームを定義するには、[_CrtSetReportFile](crtsetreportfile.md) を呼び出す必要があります。|
|**_CRTDBG_MODE_WNDW**|[[中止](abort.md)]、 **[再試行]** 、および **[無視]** の各ボタンと共にメッセージを表示するメッセージボックスを作成します。|
|**_CRTDBG_REPORT_MODE**|指定された*reportType*の*reportmode*を返します。<br /><br /> 1   **_CRTDBG_MODE_FILE**<br /><br /> 2 **_CRTDBG_MODE_DEBUG**<br /><br /> 4 **_CRTDBG_MODE_WNDW**|

各レポートの種類は、1 つ、2 つ、または 3 つのモードか、モードなしを使用して報告できます。 したがって、1 つのレポートの種類に対して複数の書き込み先を定義することができます。 たとえば、次のコードフラグメントでは、アサーションエラーがデバッグメッセージウィンドウと**stderr**の両方に送信されます。

```C
_CrtSetReportMode( _CRT_ASSERT, _CRTDBG_MODE_FILE | _CRTDBG_MODE_WNDW );
_CrtSetReportFile( _CRT_ASSERT, _CRTDBG_FILE_STDERR );
```

さらに、各レポートの種類のレポート モードは、個別に制御できます。 たとえば、 **_CRT_WARN**の*reportType*を出力デバッグ文字列に送信するように指定し、前に説明したように、 **_CRT_ASSERT**はデバッグメッセージウィンドウを使用して表示し、 **stderr**に送信することができます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_CrtSetReportMode**|\<crtdbg.h>|\<errno.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**ライブラリ**[CRT ライブラリ機能](../../c-runtime-library/crt-library-features.md)のデバッグバージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
