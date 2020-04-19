---
title: _CrtGetReportHook
ms.date: 11/04/2016
api_name:
- _CrtGetReportHook
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
- CrtGetReportHook
- _CrtGetReportHook
helpviewer_keywords:
- CrtGetReportHook function
- _CrtGetReportHook function
ms.assetid: 922758ed-7edd-4359-9c92-0535192dc11a
ms.openlocfilehash: bc005dda435b5e11d6c3c886de180ed85b9c2a04
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942401"
---
# <a name="_crtgetreporthook"></a>_CrtGetReportHook

デバッグ レポート プロセスのために C ランタイムにフックするクライアント定義レポート関数を取得します (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
_CRT_REPORT_HOOK _CrtGetReportHook( void );
```

## <a name="return-value"></a>戻り値

現在のクライアント定義レポート関数を返します。

## <a name="remarks"></a>Remarks

**_CrtGetReportHook**を使用すると、アプリケーションは、C ランタイムデバッグライブラリのレポートプロセスの現在のレポート関数を取得できます。

フックをサポートするその他のランタイム関数の使い方の詳細と、独自のクライアント定義フック関数の記述方法については、「[デバッグ用フック関数の作成](/visualstudio/debugger/debug-hook-function-writing)」を参照してください。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtGetReportHook**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="example"></a>例

**_CrtSetReportHook**の使用例については、「[レポート](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/report)」を参照してください。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_CrtSetReportHook](crtsetreporthook.md)<br/>
