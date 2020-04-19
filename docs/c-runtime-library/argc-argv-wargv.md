---
title: __argcでは、 __argvでは、 __wargv
description: Microsoft C ランタイムライブラリのグローバル定数 __argc、__argv、および __wargvについて説明します。
ms.date: 11/04/2016
api_name:
- __wargv
- __argv
- __argc
api_location:
- msvcrt120.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- __argv
- __argc
- __wargv
helpviewer_keywords:
- __argv
- __wargv
- __argc
ms.assetid: 17001b0a-04ad-4762-b3a6-c54847f02d7c
no-loc:
- __argc
- __argv
- __wargv
- main
- wmain
ms.openlocfilehash: 86a22a7391c7bde34d7734631a2970a45851dda3
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123982"
---
# <a name="opno-loc__argc-opno-loc__argv-opno-loc__wargv"></a>__argcでは、 __argvでは、 __wargv

`__argc` グローバル変数は、プログラムに渡されるコマンド ライン引数の数です。 `__argv` は、プログラム引数を含む 1 バイト文字列またはマルチバイト文字列の配列へのポインターです。`__wargv` は、プログラム引数を含むワイド文字列の配列へのポインターです。 これらのグローバル変数によって、`main` または `wmain` に引数が提供されます。

## <a name="syntax"></a>構文

```C
extern int __argc;
extern char ** __argv;
extern wchar_t ** __wargv;
```

## <a name="remarks"></a>Remarks

`main` 関数を使用するプログラムでは、`__argc` および `__argv` は、プログラムの起動に使用されるコマンド ラインを使用してプログラムの起動時に初期化されます。 コマンド ラインは解析されて個々の引数になり、ワイルドカードは展開されます。 引数の数は `__argc` に代入され、引数の文字列はヒープ上に割り当てられ、引数の配列へのポインターは `__argv` に代入されます。 ワイド文字および `wmain` 関数を使用するようにコンパイルされたプログラムでは、ワイド文字列として引数は解析されワイルドカードは展開されて、引数の文字列の配列へのポインターは `__wargv` に代入されます。

移植性のあるコードの場合、`main` に渡される引数を使用してプログラムでコマンド ライン引数を取得することをお勧めします。

### <a name="generic-text-routine-mappings"></a>汎用テキストルーチンのマッピング

|Tchar.h のルーチン|_UNICODE が未定義の場合|_UNICODE が定義されている場合|
|---------------------|---------------------------|-----------------------|
|`__targv`|`__argv`|`__wargv`|

## <a name="requirements"></a>要件

|グローバル変数|必須ヘッダー|
|---------------------|---------------------|
|`__argc`では、 `__argv`では、 `__wargv`|\<stdlib.h>、\<cstdlib> (C++)|

`__argc`、`__argv`、および `__wargv` は Microsoft 拡張機能です。 互換性の詳細については、「[互換性](../c-runtime-library/compatibility.md)」を参照してください。

## <a name="see-also"></a>関連項目

[グローバル変数](../c-runtime-library/global-variables.md)の\
[main 関数とコマンドライン引数C++()](../cpp/main-function-command-line-args.md)\
[main の代わりに wmain を使用する](../cpp/using-wmain-instead-of-main.md)
