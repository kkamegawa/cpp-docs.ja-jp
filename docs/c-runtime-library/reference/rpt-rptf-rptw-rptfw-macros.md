---
title: _RPT、_RPTF、_RPTW、_RPTFW のマクロ
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
ms.openlocfilehash: 567fe0a68f5adad6f5d90ef3da9d673a75bb83a6
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949083"
---
# <a name="_rpt-_rptf-_rptw-_rptfw-macros"></a>_RPT、_RPTF、_RPTW、_RPTFW のマクロ

デバッグ レポートを生成してアプリケーションの進行状況を追跡します (デバッグ バージョンのみ)。 *N*は引数の引数の数を指定し、0、1、2、3、4、または5を指定できることに*注意して*ください。

## <a name="syntax"></a>構文

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>パラメーター

*reportType*<br/>
レポートの種類: **_CRT_WARN**、 **_CRT_ERROR**、または **_CRT_ASSERT**。

*format*<br/>
ユーザー メッセージの作成に使用される書式指定文字列。

*value*<br/>
*書式*によって使用される置換引数。

## <a name="remarks"></a>Remarks

これらのマクロはすべて、 *reportType*パラメーターと*format*パラメーターを受け取ります。 また、マクロ名に追加された数字で示される最大 4 つの追加引数を受け取る場合もあります。 たとえば、 **_RPT0**と **_RPTF0**は、追加の引数を受け取りません。 **_RPT1**と **_RPTF1** take、 **_RPT2** 、および **_RPTF2** *take と* **arg2**など*を受け取ります*。

**_RPT**マクロと **_RPTF**マクロは、デバッグプロセス中のアプリケーションの進行状況を追跡するために使用できるため、 [printf](printf-printf-l-wprintf-wprintf-l.md)関数に似ています。 ただし、これらのマクロは、アプリケーションの製品版ビルドで呼び出されないように **#ifdef**ステートメントで囲む必要がないため、 **printf**よりも柔軟です。 この柔軟性は、 [_debug](../../c-runtime-library/debug.md)マクロを使用することで実現されます。 **_RPT**マクロと **_RPTF**マクロは、 **_debug**フラグが定義されている場合にのみ使用できます。 **_Debug**が定義されていない場合、これらのマクロの呼び出しはプリプロセス中に削除されます。

**_RPTW**マクロと **_RPTFW**マクロは、これらのマクロのワイド文字バージョンです。 これらは**wprintf**のようなもので、ワイド文字列を引数として受け取ります。

**_RPT**マクロは、 [_CrtDbgReport](crtdbgreport-crtdbgreportw.md)関数を呼び出して、ユーザーメッセージを含むデバッグレポートを生成します。 **_RPTW**マクロは、 **_CrtDbgReportW**関数を呼び出して、ワイド文字で同じレポートを生成します。 **_RPTF**マクロと **_RPTFW**マクロは、ユーザーメッセージに加えて、レポートマクロが呼び出されたソースファイルと行番号を使用してデバッグレポートを作成します。 ユーザーメッセージは、 [printf](printf-printf-l-wprintf-wprintf-l.md)関数で定義されているのと同じ規則を使用して、 **arg**[*n*] 引数を*書式指定*文字列に置き換えることによって作成されます。

**_CrtDbgReport**または **_CrtDbgReportW**は、デバッグレポートを生成し、 *reportType*に対して定義されている現在のレポートモードおよびファイルに基づいて変換先を決定します。 [_CrtSetReportMode](crtsetreportmode.md) 関数と [_CrtSetReportFile](crtsetreportfile.md) 関数は、各レポートの種類の宛先を定義するために使用されます。

**_RPT**マクロが呼び出され、 **_CrtSetReportMode**も **_CrtSetReportFile**も呼び出されていない場合は、次のようにメッセージが表示されます。

|レポートの種類|出力先|
|-----------------|------------------------|
|**_CRT_WARN**|警告テキストは表示されません。|
|**_CRT_ERROR**|ポップアップ ウィンドウ。 `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);` が指定されている場合と同じです。|
|**_CRT_ASSERT**|**_CRT_ERROR**と同じです。|

変換先がデバッグメッセージウィンドウで、ユーザーが **[再試行]** ボタンをクリックすると、 **_CrtDbgReport**または **_CrtDbgReportW**は1を返します。これにより、just-in-time (JIT) デバッグが有効になっていれば、これらのマクロはデバッガーを開始します。 これらのマクロをデバッグ エラーの処理機構として使用する方法の詳細については、[確認とレポート用マクロの使用](/visualstudio/debugger/macros-for-reporting)に関するページを参照してください。

デバッグ レポートを生成するマクロが他にも 2 つ存在します。 [_ASSERT](assert-asserte-assert-expr-macros.md) マクロは、その式の引数が FALSE に評価される場合にのみ、レポートを生成します。 [_ASSERTE](assert-asserte-assert-expr-macros.md)は **_ASSERT**とまったく同じですが、生成されるレポートに失敗した式が含まれています。

## <a name="requirements"></a>必要条件

|マクロ|必須ヘッダー|
|-----------|---------------------|
|**_RPT**マクロ|\<crtdbg.h>|
|**_RPTF**マクロ|\<crtdbg.h>|
|**_RPTW**マクロ|\<crtdbg.h>|
|**_RPTFW**マクロ|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

これらはマクロであり、Crtdbg.h を組み込むと取得されますが、アプリケーションは、デバッグ ライブラリのいずれかとリンクする必要があります。これらのマクロは、他のランタイム関数を呼び出すからです。

## <a name="example"></a>例

「[_ASSERT](assert-asserte-assert-expr-macros.md)」のトピックの例を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
