---
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: bf88bae40031f6e92d6f936ac8a50f85d6c4e36c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942278"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

[_CrtSetReportMode](crtsetreportmode.md)を使用して **_CRTDBG_MODE_FILE**を指定した後、メッセージテキストを受信するファイルハンドルを指定できます。 **_CrtSetReportFile**は[、_CrtDbgReport、_CrtDbgReportW](crtdbgreport-crtdbgreportw.md)によって、テキストの出力先を指定するためにも使用されます (デバッグバージョンのみ)。

## <a name="syntax"></a>構文

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>パラメーター

*reportType*<br/>
レポートの種類: **_CRT_WARN**、 **_CRT_ERROR**、および **_CRT_ASSERT**。

*reportFile*<br/>
*ReportType*の新しいレポートファイル。

## <a name="return-value"></a>戻り値

正常に完了すると、 **_CrtSetReportFile**は、 *reportType*で指定されたレポートの種類に対して定義されている前のレポートファイルを返します。 *ReportType*に無効な値が渡された場合、この関数は「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーを呼び出します。 実行の継続が許可された場合、 **errno**は**EINVAL**に設定され、関数は **_CRTDBG_HFILE_ERROR**を返します。 詳細については、「[errno、_doserrno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_CrtSetReportFile**は、 [_CrtSetReportMode](crtsetreportmode.md)関数と共に使用して、 **_CrtDbgReport**によって生成される特定のレポートの種類の宛先を定義します。 特定の種類のレポートに対して **_CRTDBG_MODE_FILE**レポートモードを割り当てるために **_CrtSetReportMode**が呼び出された場合は、 **_CrtSetReportFile**を呼び出して、変換先として使用する特定のファイルまたはストリームを定義します。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtSetReportFile**の呼び出しはプリプロセス中に削除されます。

次の一覧は、 *Reportfile*に使用できる選択肢と、 **_CrtDbgReport**の結果の動作を示しています。 これらのオプションは、Crtdbg.h でビット フラグとして定義されています。

- **ファイルハンドル**

   メッセージの送信先となるファイルのハンドル。 ハンドルの有効性は検証されません。 ファイルのハンドルを開いたり閉じたりする必要があります。 例えば:

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   メッセージを**stderr**に書き込みます。これは次のようにリダイレクトできます。

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   は、リダイレクトできる**stdout**にメッセージを書き込みます。

- **_CRTDBG_REPORT_FILE**

   現在のレポート モードを返します。

各レポートの種類によって使用されるレポート ファイルを個別に制御できます。 たとえば、 **_CRT_ERROR**の*reportType*を**Stderr**に報告し、 *reportType*の **_CRT_ASSERT**をユーザー定義のファイルハンドルまたはストリームに報告するように指定することができます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|オプション ヘッダー|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

コンソールは、ユニバーサル Windows プラットフォーム (UWP) アプリではサポートされていません。 コンソール、 **stdin**、 **stdout**、および**stderr**に関連付けられている標準ストリームハンドルは、C ランタイム関数が UWP アプリで使用できるようになる前にリダイレクトする必要があります。 互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

**ライブラリ**[CRT ライブラリ機能](../../c-runtime-library/crt-library-features.md)のデバッグバージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
