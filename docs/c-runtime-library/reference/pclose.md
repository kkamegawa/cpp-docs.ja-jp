---
title: _pclose
ms.date: 11/04/2016
api_name:
- _pclose
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
- api-ms-win-crt-stdio-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _pclose
- pclose
helpviewer_keywords:
- _pclose function
- pclose function
- pipes, closing
ms.assetid: e2e31a9e-ba3a-4124-bcbb-c4040110b3d3
ms.openlocfilehash: 383dd96553463a2619537cf06fc6534770ed88d5
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70951083"
---
# <a name="_pclose"></a>_pclose

新しいコマンド プロセッサを待機し、関連するパイプのストリームを閉じます。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _pclose(
FILE *stream
);
```

### <a name="parameters"></a>パラメーター

*一連*<br/>
前の **_popen**の呼び出しからの戻り値。

## <a name="return-value"></a>戻り値

終了コマンドプロセッサの終了ステータスを返します。エラーが発生した場合は-1 を返します。 戻り値の形式は **_cwait**の場合と同じですが、下位バイトと上位バイトが交換される点が異なります。 Stream が**NULL**の場合、 **_pclose**は**errno**を**EINVAL**に設定し、-1 を返します。

エラー コードの詳細については、「[_doserrno、errno、_sys_errlist、_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)」をご覧ください。

## <a name="remarks"></a>Remarks

**_Pclose**関数は、関連付けられた **_popen**呼び出しによって開始されたコマンドプロセッサ (CMD.EXE) のプロセス ID を検索し、新しいコマンドプロセッサで[_cwait](cwait.md)呼び出しを実行して、関連付けられているパイプのストリームを閉じます。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_pclose**|\<stdio.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のすべてのバージョン。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[_pipe](pipe.md)<br/>
[_popen、_wpopen](popen-wpopen.md)<br/>
