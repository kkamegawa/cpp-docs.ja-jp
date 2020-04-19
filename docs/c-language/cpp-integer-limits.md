---
title: C とC++整数の制限
ms.date: 10/21/2019
helpviewer_keywords:
- limits, integer
- limits, integer constants
- integer limits
ms.assetid: 0c23cbd6-29fb-4d9c-b689-5984e19748de
ms.openlocfilehash: 6940f36e37ec58ca8fe23c9062928cbf90b125bd
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778373"
---
# <a name="c-and-c-integer-limits"></a>C とC++整数の制限

**Microsoft 固有の仕様**

次の表に、C とC++での整数型の制限を示します。 これらの制限は、C 標準ヘッダーファイル `<limits.h>` で定義されています。 標準C++ライブラリヘッダー `<limits>` には、`<limits.h>` を含む `<climits>` が含まれています。

Microsoft C では、サイズが8ビット、16ビット、32ビット、または64ビットの整数型である、サイズ設定された整数変数の宣言も許可されます。 C のサイズ設定された整数の詳細については、「サイズ設定された[整数型](../c-language/c-sized-integer-types.md)」を参照してください。

## <a name="limits-on-integer-constants"></a>整数定数の制限

|**定数**|説明|[値]|
|------------------|-------------|-----------|
|**CHAR_BIT**|ビット フィールドではない最小変数のビット数。|8|
|**SCHAR_MIN**|**signed char** 型変数の最小値。|-128|
|**SCHAR_MAX**|**signed char** 型変数の最大値。|127|
|**UCHAR_MAX**|**unsigned char** 型変数の最大値。|255 (0xff)|
|**CHAR_MIN**|**char** 型変数の最小値。|-128 (/J オプションが使用される場合は 0)|
|**CHAR_MAX**|**char** 型変数の最小値。|-127 (/J オプションが使用される場合は 255)|
|**MB_LEN_MAX**|多文字定数の最大バイト数。|5|
|**SHRT_MIN**|**short** 型変数の最小値。|-32768|
|**SHRT_MAX**|**short** 型変数の最大値。|32767|
|**USHRT_MAX**|**unsigned short** 型変数の最大値。|65535 (0xffff)|
|**INT_MIN**|**int** 型変数の最小値。|-2147483647 - 1|
|**INT_MAX**|**int** 型変数の最大値。|2147483647|
|**UINT_MAX**|**unsigned int** 型変数の最大値。|4294967295 (0xffffffff)|
|**LONG_MIN**|**long** 型変数の最小値。|-2147483647 - 1|
|**LONG_MAX**|**long** 型変数の最大値。|2147483647|
|**ULONG_MAX**|**unsigned long** 型変数の最大値。|4294967295 (0xffffffff)|
|**LLONG_MIN**|**Long long**型の変数の最小値。|-9223372036854775807-1|
|**LLONG_MAX**|**Long long**型の変数の最大値。|9,223,372,036,854,775,807|
|**ULLONG_MAX**|**Unsigned long long**型の変数の最大値。|18446744073709551615 (0xffffffffffffffff)|

値が最大の整数表現を超えると、Microsoft コンパイラでエラーが生成されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C 整数定数](../c-language/c-integer-constants.md)
