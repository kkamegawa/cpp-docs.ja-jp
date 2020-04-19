---
title: _nolock 関数
ms.date: 11/04/2016
helpviewer_keywords:
- _nolock functions
- nolock functions
ms.assetid: 7d651d87-38d2-4303-9897-fdb5f7a3e899
ms.openlocfilehash: 7bd0592fb8dc43307a902714723d1b1e43207d1c
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/11/2019
ms.locfileid: "57746410"
---
# <a name="nolock-functions"></a>_nolock 関数

これらは、ロックを実行しない関数です。 最大のパフォーマンスを必要とするユーザーに提供されます。 詳細については、「[マルチスレッド ライブラリのパフォーマンス](../c-runtime-library/multithreaded-libraries-performance.md)」をご覧ください。

_nolock 関数は、プログラムが真のシングル スレッドの場合、または、その独自のロックを実行する場合にのみ使用します。

## <a name="no-lock-routines"></a>ロックを実行しないルーチン

[_fclose_nolock](../c-runtime-library/reference/fclose-nolock.md)

[_fflush_nolock](../c-runtime-library/reference/fflush-nolock.md)

[_fgetc_nolock、_fgetwc_nolock](../c-runtime-library/reference/fgetc-nolock-fgetwc-nolock.md)

[_fread_nolock](../c-runtime-library/reference/fread-nolock.md)

[_fseek_nolock、_fseeki64_nolock](../c-runtime-library/reference/fseek-nolock-fseeki64-nolock.md)

[_ftell_nolock、_ftelli64_nolock](../c-runtime-library/reference/ftell-nolock-ftelli64-nolock.md)

[_fwrite_nolock](../c-runtime-library/reference/fwrite-nolock.md)

[_getc_nolock、_getwc_nolock](../c-runtime-library/reference/getc-nolock-getwc-nolock.md)

[_getch_nolock、_getwch_nolock](../c-runtime-library/reference/getch-nolock-getwch-nolock.md)

[_getchar_nolock、_getwchar_nolock](../c-runtime-library/reference/getchar-nolock-getwchar-nolock.md)

[_getche_nolock、_getwche_nolock](../c-runtime-library/reference/getche-nolock-getwche-nolock.md)

[_getdcwd_nolock、_wgetdcwd_nolock](../c-runtime-library/reference/getdcwd-nolock-wgetdcwd-nolock.md)

[_putc_nolock、_putwc_nolock](../c-runtime-library/reference/putc-nolock-putwc-nolock.md)

[_putch_nolock、_putwch_nolock](../c-runtime-library/reference/putch-nolock-putwch-nolock.md)

[_putchar_nolock、_putwchar_nolock](../c-runtime-library/reference/putchar-nolock-putwchar-nolock.md)

[_ungetc_nolock、_ungetwc_nolock](../c-runtime-library/reference/ungetc-nolock-ungetwc-nolock.md)

[_ungetch_nolock、_ungetwch_nolock](../c-runtime-library/reference/ungetch-ungetwch-ungetch-nolock-ungetwch-nolock.md)

## <a name="see-also"></a>関連項目

[入出力](../c-runtime-library/input-and-output.md)<br/>
[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
