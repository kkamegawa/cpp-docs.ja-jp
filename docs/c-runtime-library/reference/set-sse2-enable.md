---
title: _set_SSE2_enable
ms.date: 04/05/2018
api_name:
- _set_SSE2_enable
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
- api-ms-win-crt-math-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_SSE2_enable
- set_SSE2_enable
helpviewer_keywords:
- _set_SSE2_enable function
- Streaming SIMD Extensions 2 instructions
- set_SSE2_enable function
ms.assetid: 55db895d-fc1e-475a-9110-b781a9bb51c5
ms.openlocfilehash: 8838282db851c6811a3f24c75a03b31c5870e6d3
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70948358"
---
# <a name="_set_sse2_enable"></a>_set_SSE2_enable

CRT 数値演算ルーチンでの Streaming SIMD 拡張命令 2 (SSE2) 命令の使用を有効または無効にします。 (この関数は、x64 アーキテクチャでは利用できません。SSE2 が既定で有効になっているためです。)

## <a name="syntax"></a>構文

```C
int _set_SSE2_enable(
   int flag
);
```

### <a name="parameters"></a>パラメーター

*flag*<br/>
SSE2 実装を有効にする場合は 1、SSE2 実装を無効にする場合は 0。 既定では、SSE2 実装はこれをサポートするプロセッサでは有効です。

## <a name="return-value"></a>戻り値

SSE2 実装が有効な場合はゼロ以外、SSE2 実装が無効になっている場合はゼロを返します。

## <a name="remarks"></a>Remarks

次の関数には、 **_set_SSE2_enable**を使用して有効にできる SSE2 実装があります。

- [atan](atan-atanf-atanl-atan2-atan2f-atan2l.md)

- [ceil](ceil-ceilf-ceill.md)

- [exp](exp-expf.md)

- [floor](floor-floorf-floorl.md)

- [log](log-logf-log10-log10f.md)

- [log10](log-logf-log10-log10f.md)

- [modf](modf-modff-modfl.md)

- [pow](pow-powf-powl.md)

これらの関数の SSE2 実装では、既定の実装とは若干異なる回答が生じる場合があります。SSE2 の中間値は 64 ビットの浮動小数点数ですが、既定の実装の中間値は、80 ビットの浮動小数点数であるためです。

> [!NOTE]
> [/Oi (組み込み関数の生成)](../../build/reference/oi-generate-intrinsic-functions.md)コンパイラオプションを使用してプロジェクトをコンパイルした場合、 **_set_SSE2_enable**が効果を持たないように見えることがあります。 **/Oi**コンパイラオプションは、コンパイラに対して、CRT 呼び出しを置き換えるために組み込みを使用する権限を与えます。この動作は、 **_set_SSE2_enable**の効果よりも優先されます。 **/Oi**が **_set_SSE2_enable**をオーバーライドしないことを保証するには、 **/Oi-** を使用してプロジェクトをコンパイルします。 これは、 **/Oi**を暗示する他のコンパイラスイッチを使用する場合にも適しています。

SSE2 実装はすべての例外がマスクされる場合にのみ使用します。 例外をマスクするには、[_control87、_controlfp](control87-controlfp-control87-2.md) を使用します。

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_set_SSE2_enable**|\<math.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_set_SSE2_enable.c
// processor: x86
#include <math.h>
#include <stdio.h>

int main()
{
   int i = _set_SSE2_enable(1);

   if (i)
      printf("SSE2 enabled.\n");
   else
      printf("SSE2 not enabled; processor does not support SSE2.\n");
}
```

```Output
SSE2 enabled.
```

## <a name="see-also"></a>関連項目

[CRT ライブラリの機能](../../c-runtime-library/crt-library-features.md)<br/>
