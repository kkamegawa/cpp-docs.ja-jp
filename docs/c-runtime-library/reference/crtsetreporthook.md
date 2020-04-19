---
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 77c1e499c66a76027e872783e256754ef72e465d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938511"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

C ランタイム デバッグ レポート プロセスにフックして、クライアント定義レポート関数をインストールします (デバッグ バージョンのみ)。

## <a name="syntax"></a>構文

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>パラメーター

*reportHook*<br/>
C ランタイム デバッグ レポート プロセスにフックする新しいクライアント定義レポート関数。

## <a name="return-value"></a>戻り値

以前のクライアント定義レポート関数を返します。

## <a name="remarks"></a>Remarks

**_CrtSetReportHook**を使用すると、アプリケーションは、C ランタイムデバッグライブラリのレポートプロセスで独自のレポート関数を使用できます。 その結果、デバッグ レポートを生成するために [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) が呼び出されるたびに、アプリケーションのレポート関数が先に呼び出されます。 この機能により、アプリケーションはデバッグレポートのフィルター処理などの操作を実行し、特定の割り当ての種類に焦点を当てたり、 **_CrtDbgReport**を使用して使用できない宛先にレポートを送信したりすることができます。 [_Debug](../../c-runtime-library/debug.md)が定義されていない場合、 **_CrtSetReportHook**の呼び出しはプリプロセス中に削除されます。

**_CrtSetReportHook**のより堅牢なバージョンについては、 [_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md)を参照してください。

**_CrtSetReportHook**関数は、 *reporthook*に指定された新しいクライアント定義レポート関数をインストールし、以前のクライアント定義フックを返します。 次の例は、クライアント定義レポート フックをどのようにプロトタイプ宣言するかを示しています。

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

ここで、 *reportType*はデバッグレポートの種類 ( **_CRT_WARN**、 **_CRT_ERROR**、または **_CRT_ASSERT**) で、*メッセージ*はレポートに含まれる完全にアセンブルされたデバッグユーザーメッセージであり、**戻り**値はです。 **_CrtDbgReport**によって返される、クライアント定義レポート関数によって指定されます。 使用できるレポートの種類の詳細については、[_CrtSetReportMode](crtsetreportmode.md) 関数を参照してください。

クライアント定義レポート関数でデバッグメッセージが完全に処理され、それ以上のレポートが必要ない場合、関数は**TRUE**を返す必要があります。 関数が**FALSE**を返すと、 **_CrtDbgReport**が呼び出され、レポートの種類、モード、およびファイルの現在の設定を使用してデバッグレポートが生成されます。 また、戻り値として **_CrtDbgReport**を指定することによっ**て、アプリケーション**はデバッグの中断を発生させるかどうかを制御することもできます。 デバッグレポートの構成方法と生成方法の詳細については、「 **_CrtSetReportMode**、 [_CrtSetReportFile](crtsetreportfile.md)、および **_CrtDbgReport**」を参照してください。

フックをサポートするその他のランタイム関数の使い方の詳細と、独自のクライアント定義フック関数の記述方法については、「[デバッグ用フック関数の作成](/visualstudio/debugger/debug-hook-function-writing)」を参照してください。

> [!NOTE]
> アプリケーションが **/clr**でコンパイルされ、アプリケーションが main を終了した後でレポート関数が呼び出された場合、レポート関数が CRT 関数を呼び出すと clr は例外をスローします。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="libraries"></a>ライブラリ

[C ランタイム ライブラリ](../../c-runtime-library/crt-library-features.md)のデバッグ バージョンのみ。

## <a name="see-also"></a>関連項目

[デバッグ ルーチン](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
