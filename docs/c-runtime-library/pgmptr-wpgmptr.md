---
title: _pgmptr、_wpgmptr
ms.date: 11/04/2016
f1_keywords:
- pgmptr
- _pgmptr
- wpgmptr
- _wpgmptr
helpviewer_keywords:
- wpgmptr function
- _wpgmptr function
- _pgmptr function
- pgmptr function
ms.assetid: 4d44b515-0eff-4136-8bc4-684195f218f5
ms.openlocfilehash: beff0401d0aa2aa21819e58618ef4c02795d4393
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75300158"
---
# <a name="_pgmptr-_wpgmptr"></a>_pgmptr、_wpgmptr

実行可能ファイルのパスです。 非推奨。[_get_pgmptr](../c-runtime-library/reference/get-pgmptr.md) と [_get_wpgmptr](../c-runtime-library/reference/get-wpgmptr.md) を使用してください。

## <a name="syntax"></a>構文

```
extern char *_pgmptr;
extern wchar_t *_wpgmptr;
```

## <a name="remarks"></a>コメント

コマンド インタープリター (Cmd.exe) からプログラムを実行すると、`_pgmptr` は実行可能ファイルの完全なパスに自動的に初期化されます。 たとえば、Hello.exe が C:\BIN にあり、C:\BIN がパス内にある場合は、次のように、実行時に `_pgmptr` が C:\BIN\Hello.exe に設定されます。

```
C> hello
```

プログラムがコマンド ラインから実行されない場合は、`_pgmptr` はプログラム名 (ファイルの基本名。ファイル名拡張子を除く)、またはファイル名、相対パス、または完全なパスに初期化される可能性があります。

`_wpgmptr` は、ワイド文字版の `_pgmptr` で、`wmain` を使用するプログラムで使用されます。

### <a name="generic-text-routine-mappings"></a>汎用テキスト ルーチンのマップ

|Tchar.h のルーチン|_UNICODE および _MBCS が未定義の場合|_MBCS が定義されている場合|_UNICODE が定義されている場合|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tpgmptr`|`_pgmptr`|`_pgmptr`|`_wpgmptr`|

## <a name="requirements"></a>要件

|[Variable]|必須ヘッダー|
|--------------|---------------------|
|`_pgmptr`、`_wpgmptr`|\<stdlib.h>|

## <a name="example"></a>使用例

次のプログラムで、`_pgmptr` の使用方法を示します。

```c
// crt_pgmptr.c
// compile with: /W3
// The following program demonstrates the use of _pgmptr.
//
#include <stdio.h>
#include <stdlib.h>
int main( void )
{
   printf("The full path of the executing program is : %Fs\n",
     _pgmptr); // C4996
   // Note: _pgmptr is deprecated; use _get_pgmptr instead
}
```

`%Fs` を `%S`に、`main` を `wmain` に変更することで、`_wpgmptr` を使用できます。

## <a name="see-also"></a>関連項目

[グローバル変数](../c-runtime-library/global-variables.md)
