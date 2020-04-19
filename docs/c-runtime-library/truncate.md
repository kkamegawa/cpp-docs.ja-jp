---
title: _TRUNCATE
ms.date: 11/04/2016
f1_keywords:
- _TRUNCATE
- TRUNCATE
helpviewer_keywords:
- TRUNCATE constant
- _TRUNCATE constant
ms.assetid: ad093dbf-1aa5-4bd2-9268-efc68afd8434
ms.openlocfilehash: b472fceffa6284baaaf4dc1780ab54399fdd42c7
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301679"
---
# <a name="_truncate"></a>_TRUNCATE

文字列の切り捨て動作を指定します。

## <a name="syntax"></a>構文

```
#include <stdlib.h>
```

## <a name="remarks"></a>コメント

`_TRUNCATE` が `count` パラメーターとして次の関数に渡されると、切り捨て動作が有効になります。

[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)

[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)

[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)

[mbsrtowcs_s](../c-runtime-library/reference/mbsrtowcs-s.md)

[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)

[wcsrtombs_s](../c-runtime-library/reference/wcsrtombs-s.md)

[_snprintf_s、_snprintf_s_l、_snwprintf_s、_snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)

[vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)

コピー先のバッファーが小さすぎて文字列全体を保持できない場合、これらの関数の通常の動作ではエラー状況として、その状況を処理します (「[パラメーターの検証](../c-runtime-library/parameter-validation.md)」を参照してください)。 ただし、`_TRUNCATE` を渡すことで文字列の切り捨てが有効になっている場合は、これらの関数はコピー先バッファーが null で終わるようにしながら、バッファーに収まる限りの文字列のみをコピーし、正常終了の値を返します。

文字列の切り捨てにより、関係する関数の戻り値が変わります。 次の関数は、切り捨てが行われなかった場合は 0 を返し、切り捨てが行われた場合は `STRUNCATE` を返します。

[strncpy_s、_strncpy_s_l、wcsncpy_s、_wcsncpy_s_l、_mbsncpy_s、_mbsncpy_s_l](../c-runtime-library/reference/strncpy-s-strncpy-s-l-wcsncpy-s-wcsncpy-s-l-mbsncpy-s-mbsncpy-s-l.md)

[strncat_s、_strncat_s_l、wcsncat_s、_wcsncat_s_l、_mbsncat_s、_mbsncat_s_l](../c-runtime-library/reference/strncat-s-strncat-s-l-wcsncat-s-wcsncat-s-l-mbsncat-s-mbsncat-s-l.md)

[wcstombs_s、_wcstombs_s_l](../c-runtime-library/reference/wcstombs-s-wcstombs-s-l.md)

[mbstowcs_s、_mbstowcs_s_l](../c-runtime-library/reference/mbstowcs-s-mbstowcs-s-l.md)

次の関数は、切り捨てが行われなかった場合はコピーした文字数を返し、切り捨てが行われた場合は -1 を返します (元の snprintf 関数の動作と一致)。

[_snprintf_s、_snprintf_s_l、_snwprintf_s、_snwprintf_s_l](../c-runtime-library/reference/snprintf-s-snprintf-s-l-snwprintf-s-snwprintf-s-l.md)

[vsnprintf_s、_vsnprintf_s、_vsnprintf_s_l、_vsnwprintf_s、_vsnwprintf_s_l](../c-runtime-library/reference/vsnprintf-s-vsnprintf-s-vsnprintf-s-l-vsnwprintf-s-vsnwprintf-s-l.md)

## <a name="example"></a>使用例

```c
// crt_truncate.c
#include <stdlib.h>
#include <errno.h>

int main()
{
   char src[] = "1234567890";
   char dst[5];
   errno_t err = strncpy_s(dst, _countof(dst), src, _TRUNCATE);
   if ( err == STRUNCATE )
      printf( "truncation occurred!\n" );
   printf( "'%s'\n", dst );
}
```

```Output
truncation occurred!
'1234'
```

## <a name="see-also"></a>関連項目

[グローバル定数](../c-runtime-library/global-constants.md)
