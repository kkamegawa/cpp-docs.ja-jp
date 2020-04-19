---
title: stdin、stdout、stderr
ms.date: 10/23/2018
f1_keywords:
- stdin
- stderr
- stdout
helpviewer_keywords:
- stdout function
- standard output stream
- standard error stream
- stdin function
- standard input stream
- stderr function
ms.assetid: badd4735-596d-4498-857c-ec8b7e670e4c
ms.openlocfilehash: 5de1ff01282f30ad133f909cb87f5d7c8d521ae5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741951"
---
# <a name="stdin-stdout-stderr"></a>stdin、stdout、stderr

## <a name="syntax"></a>構文

```
FILE *stdin;
FILE *stdout;
FILE *stderr;
#include <stdio.h>
```

## <a name="remarks"></a>解説

これらは、入力、出力、エラー出力の標準ストリームです。

既定では、標準入力はキーボードから読み取られ、標準出力と標準エラーは画面に出力されます。

標準ストリームにアクセスするには、次のストリーム ポインターを使用できます。

|ポインター|ストリーム|
|-------------|------------|
|`stdin`|標準入力|
|`stdout`|標準出力|
|`stderr`|標準エラー|

これらのポインターは、関数への引数として使用できます。 [getchar](../c-runtime-library/reference/getchar-getwchar.md) や [putchar](../c-runtime-library/reference/putchar-putwchar.md) などのいくつかの関数では、`stdin` と `stdout` が自動的に使用されます。

これらのポインターは定数であり、新しい値を割り当てることはできません。 ディスク ファイルやその他のデバイスにストリームをリダイレクトするには、[freopen](../c-runtime-library/reference/freopen-wfreopen.md) 関数を使用できます。 オペレーティング システムでは、プログラムの標準入力と出力をコマンド レベルでリダイレクトすることができます。

## <a name="see-also"></a>関連項目

[ストリーム入出力](../c-runtime-library/stream-i-o.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
