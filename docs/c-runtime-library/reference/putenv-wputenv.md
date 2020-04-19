---
title: _putenv、_wputenv
ms.date: 11/04/2016
api_name:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 8fe699a476ea1dd09a6ce9922294bce398df16b2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949894"
---
# <a name="_putenv-_wputenv"></a>_putenv、_wputenv

環境変数を作成、変更、または削除します。 これらの関数にはセキュリティが強化されたバージョンがあります。「[_putenv_s、_wputenv_s](putenv-s-wputenv-s.md)」をご覧ください。

> [!IMPORTANT]
> この API は、Windows ランタイムで実行するアプリケーションでは使用できません。 詳細については、「[ユニバーサル Windows プラットフォーム アプリでサポートされていない CRT 関数](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md)」を参照してください。

## <a name="syntax"></a>構文

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>パラメーター

*envstring*<br/>
環境文字列定義。

## <a name="return-value"></a>戻り値

成功した場合は0を返し、エラーの場合は-1 を返します。

## <a name="remarks"></a>Remarks

**_Putenv**関数は、新しい環境変数を追加するか、既存の環境変数の値を変更します。 環境変数は、プロセス (たとえば、プログラムにリンクされるライブラリの既定の検索パス) が実行される環境を定義します。 **_wputenv**は、 **_putenv**のワイド文字バージョンです。 **_wputenv**への*envstring*引数は、ワイド文字列です。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

*Envstring*引数は、 *varname*=*value_string*形式の文字列へのポインターでなければなりません。 *varname*は、追加または変更する環境変数の名前、 *value_string*は変数の数値. *Varname*が既に環境の一部である場合、その値は*value_string*; に置き換えられます。それ以外の場合は、新しい*varname*変数とその*value_string*値が環境に追加されます。 変数を環境から削除するには、空の*value_string*を指定するか、または*varname*= だけを指定します。

**_putenv**と **_wputenv**は、現在のプロセスに対してローカルな環境にのみ影響します。これらのコマンドを使用して、コマンドレベルの環境を変更することはできません。 つまり、これらの関数は、ランタイム ライブラリからアクセスできるデータ構造体だけを対象とし、プロセス用にオペレーティング システムで作成された環境 "セグメント" は参照しません。 現在のプロセスが終了すると、環境は、呼び出し元プロセス (ほとんどの場合、オペレーティング システムのレベル) のレベルに戻ります。 ただし、変更された環境は、 **_spawn**、 **_exec**、または**システム**によって作成された新しいプロセスに渡すことができます。これらの新しいプロセスは、 **_putenv**および **_wputenv**によって追加された新しい項目を取得します。

環境エントリを直接変更しないでください。代わりに、 **_putenv**または **_wputenv**を使用して変更してください。 特に、 **_environ []** グローバル配列の要素を直接解放すると、無効なメモリアドレスにつながる可能性があります。

**getenv**と **_putenv**は、グローバル変数 **_environ**を使用して環境テーブルにアクセスします。 **_wgetenv**と **_wputenv**は **_wenviron**を使用します。 **_putenv**と **_wputenv**は、 **_environ**と **_wenviron**の値を変更する可能性があります。そのため、 **main**の引数を無効にし**て、** **wmain**への **_wenvp**引数を無効にすることができます。 そのため、環境情報にアクセスするには、 **_environ**または **_wenviron**を使用する方が安全です。 グローバル変数に対する **_putenv**と **_wputenv**の関係の詳細については、「 [_environ、_wenviron](../../c-runtime-library/environ-wenviron.md)」を参照してください。

> [!NOTE]
> **_Putenv**および **_getenv**ファミリの関数はスレッドセーフではありません。 **_getenv**は、 **_putenv**が文字列を変更している間に文字列ポインターを返すことがあり、これによってランダムなエラーが発生します。 これらの関数の呼び出しが同期されていることを確認する必要があります。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> または \<wchar.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

**_Putenv**の使用例については、 [getenv、_wgetenv](getenv-wgetenv.md)を参照してください。

## <a name="see-also"></a>関連項目

[プロセス制御と環境制御](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv、 _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv、_wsearchenv](searchenv-wsearchenv.md)<br/>
