---
title: ストリームの状態
ms.date: 11/19/2018
helpviewer_keywords:
- streams, states
ms.assetid: 5f28c968-f132-403f-968c-8417ff315e52
ms.openlocfilehash: f725fa16e8d669975dbc02c6eefd727085bbeb7c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57743349"
---
# <a name="stream-states"></a>ストリームの状態

ストリームの有効な状態および状態遷移を、次の図に示します。

![ストリームの状態ダイアグラム](../c-runtime-library/media/stream.gif "ストリームの状態ダイアグラム")

円の矢印はそれぞれ安定状態を示しています。 線の矢印はそれぞれストリームを操作する関数呼び出しの結果発生する、遷移を示しています。 5 つの関数グループで、状態遷移が発生する可能性があります。

最初の 3 つのグループの関数は、\<stdio.h> で宣言されます。

- バイトの読み込み関数 — [fgetc](../c-runtime-library/reference/fgetc-fgetwc.md)、[fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fread](../c-runtime-library/reference/fread.md)、[fscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[getc](../c-runtime-library/reference/getc-getwc.md)、[getchar](../c-runtime-library/reference/getc-getwc.md)、[gets](../c-runtime-library/gets-getws.md)、[scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、および [ungetc](../c-runtime-library/reference/ungetc-ungetwc.md)

- バイトの書き込み関数 — [fprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fputc](../c-runtime-library/reference/fputc-fputwc.md)、[fputs](../c-runtime-library/reference/fputs-fputws.md)、[fwrite](../c-runtime-library/reference/fwrite.md)、[printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)、[putc](../c-runtime-library/reference/putc-putwc.md)、[putchar](../c-runtime-library/reference/putc-putwc.md)、[puts](../c-runtime-library/reference/puts-putws.md)、[vfprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、および [vprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)

- 位置関数 — [fflush](../c-runtime-library/reference/fflush.md)、[fseek](../c-runtime-library/reference/fseek-fseeki64.md)、[fsetpos](../c-runtime-library/reference/fsetpos.md)、および [rewind](../c-runtime-library/reference/rewind.md)

残り 2 つのグループの関数は、\<wchar.h> で宣言されます。

- ワイド文字の読み込み関数 — [fgetwc](../c-runtime-library/reference/fgetc-fgetwc.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[fwscanf](../c-runtime-library/reference/fscanf-fscanf-l-fwscanf-fwscanf-l.md)、[getwc](../c-runtime-library/reference/getc-getwc.md)、[getwchar](../c-runtime-library/reference/getc-getwc.md)、[ungetwc](../c-runtime-library/reference/ungetc-ungetwc.md)、および [wscanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)

- ワイド文字の書き込み関数 — [fwprintf](../c-runtime-library/reference/fprintf-fprintf-l-fwprintf-fwprintf-l.md)、[fputwc](../c-runtime-library/reference/fputc-fputwc.md)、[fputws](../c-runtime-library/reference/fputs-fputws.md)、[putwc](../c-runtime-library/reference/putc-putwc.md)、[putwchar](../c-runtime-library/reference/fputc-fputwc.md)、[vfwprintf](../c-runtime-library/reference/vfprintf-vfprintf-l-vfwprintf-vfwprintf-l.md)、[vwprintf](../c-runtime-library/reference/vprintf-vprintf-l-vwprintf-vwprintf-l.md)、および [wprintf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)

この状態の図は、ほとんどの書き込み操作と読み取り操作の間でいずれかの位置関数を呼び出す必要があることを示しています。

- ストリームの最後の操作が書き込みであった場合、読み込み関数を呼び出すことはできません。

- 読み取り操作がファイルの終わり (EOF) インジケーターを設定しない限り、ストリームの最後の操作が読み取りであった場合は、書き込み関数を呼び出すことはできません。

最後に、この状態の図は、位置操作が後に使用できる有効な関数呼び出しの数を減らすことはないことを示しています。

## <a name="see-also"></a>関連項目

[ファイルとストリーム](../c-runtime-library/files-and-streams.md)
