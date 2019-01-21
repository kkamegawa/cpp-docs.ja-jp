---
title: ロケールのカテゴリ
ms.date: 11/04/2016
f1_keywords:
- LC_MAX
- LC_MIN
- LC_MONETARY
- LC_TIME
- LC_NUMERIC
- LC_COLLATE
- LC_CTYPE
- LC_ALL
helpviewer_keywords:
- LC_MIN constant
- LC_MONETARY constant
- LC_CTYPE constant
- locale constants
- LC_MAX constant
- LC_ALL constant
- LC_TIME constant
- LC_NUMERIC constant
- LC_COLLATE constant
ms.assetid: 868f1493-fe5d-4722-acab-bfcd374a063a
ms.openlocfilehash: 841ff5a31bfe9ee5513f76970d3b834f698b92cc
ms.sourcegitcommit: a1fad0a266b20b313364a74b16c9ac45d089b1e9
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/11/2019
ms.locfileid: "54220193"
---
# <a name="locale-categories"></a>ロケールのカテゴリ

## <a name="syntax"></a>構文

```
#include <locale.h>
```

## <a name="remarks"></a>コメント

ロケールのカテゴリは、プログラムのロケール情報のどの部分を使用するかを指定する、ローカライズ ルーチンで使用されるマニフェスト定数です。 ロケールとは、地域性、つまり国や地域に関する情報であり、この情報に基づいてプログラムの特定の側面をカスタマイズできます。 ロケールに依存する領域としては、日付の形式や通貨値の表示形式などがあります。

|ロケールのカテゴリ|影響を受けるプログラムの部分|
|---------------------|-------------------------------|
|`LC_ALL`|ロケール固有のすべての動作 (すべてのカテゴリ)|
|`LC_COLLATE`|`strcoll` 関数と `strxfrm` 関数の動作|
|`LC_CTYPE`|文字処理関数の動作 (影響を受けない `isdigit`、`isxdigit`、`mbstowcs`、`mbtowc` を除く)|
|`LC_MAX`|`LC_TIME` と同じ|
|`LC_MIN`|`LC_ALL` と同じ|
|`LC_MONETARY`|`localeconv` 関数が返す通貨形式情報|
|`LC_NUMERIC`|`printf` などの書式化出力ルーチン、データ変換ルーチン、`localeconv` 関数が返す通貨形式以外の形式情報などで使用される小数点文字|
|`LC_TIME`|`strftime` 関数の動作|

例については、「[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)」をご覧ください。

## <a name="see-also"></a>「

[localeconv](../c-runtime-library/reference/localeconv.md)<br/>
[setlocale、_wsetlocale](../c-runtime-library/reference/setlocale-wsetlocale.md)<br/>
[strcoll 系関数](../c-runtime-library/strcoll-functions.md)<br/>
[strftime、wcsftime、_strftime_l、_wcsftime_l](../c-runtime-library/reference/strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm、wcsxfrm、_strxfrm_l、_wcsxfrm_l](../c-runtime-library/reference/strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[グローバル定数](../c-runtime-library/global-constants.md)
