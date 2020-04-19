---
title: _fpieee_flt
ms.date: 04/05/2018
api_name:
- _fpieee_flt
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fpieee_flt
- _fpieee_flt
helpviewer_keywords:
- _fpieee_flt function
- exception handling, floating-point
- floating-point exception handling
- fpieee_flt function
ms.assetid: 2bc4801e-0eed-4e73-b518-215da8cc9740
ms.openlocfilehash: 8835a3184300f1c56f1123a09aa48cd34a387c87
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70957027"
---
# <a name="_fpieee_flt"></a>_fpieee_flt

IEEE 浮動小数点例外用のユーザー定義トラップ ハンドラーを呼び出します。

## <a name="syntax"></a>構文

```C
int _fpieee_flt(
   unsigned long excCode,
   struct _EXCEPTION_POINTERS *excInfo,
   int handler(_FPIEEE_RECORD *)
);
```

### <a name="parameters"></a>パラメーター

*excCode*<br/>
例外コード。

*excInfo*<br/>
Windows NT 例外情報構造体へのポインター。

*ヘッダー*<br/>
ユーザーの IEEE トラップ ハンドラー ルーチンへのポインター。

## <a name="return-value"></a>戻り値

**_Fpieee_flt**の戻り値は、*ハンドラー*によって返される値です。 そのため、構造化例外処理 (SEH) 機構の except 句で IEEE フィルター ルーチンが使用される場合があります。

## <a name="remarks"></a>Remarks

**_Fpieee_flt**関数は、IEEE 浮動小数点例外用のユーザー定義トラップハンドラーを呼び出し、関連するすべての情報を提供します。 このルーチンは SEH 機構の例外フィルターとして機能し、必要に応じて独自の IEEE 例外ハンドラーが呼び出されます。

**_FPIEEE_RECORD**構造体には、IEEE 浮動小数点例外に関する情報が含まれています (Fpieee. h に定義されています)。 この構造体は、 **_fpieee_flt**によってユーザー定義トラップハンドラーに渡されます。

|_FPIEEE_RECORD フィールド|説明|
|----------------------------|-----------------|
|**RoundingMode**<br/>**Precision**|これらの**符号なし** **int**フィールドには、例外が発生した時点の浮動小数点環境に関する情報が含まれます。|
|**操作**|この**符号なし** **int**フィールドは、トラップを発生させた操作の種類を示します。 型が比較 ( **_FpCodeCompare**) の場合**は、_FPIEEE_COMPARE_RESULT フィールドに**特殊な値 (fpieee. h で定義) のいずれかを指定できます。 変換の種類 ( **_FpCodeConvert**) は、浮動小数点変換操作中にトラップが発生したことを示します。 **Operand1**と**結果**の型を調べて、試行されている変換の種類を特定できます。|
|**Operand1**<br/>**Operand2**<br/>**結果**|これらの **_FPIEEE_VALUE**構造体は、提案された結果とオペランドの型と値を示します。 各構造体には、次のフィールドが含まれます。<br /><br /> **オペレーティング andvalid** -応答する値が有効かどうかを示すフラグ。<br />**Format** -対応する値のデータ型。 対応する値が有効でなくても、形式の種類が返されることがあります。<br />**値**-結果またはオペランドのデータ値。|
|**原因**<br/>**Enable**<br/>**ステータス**|**_FPIEEE_EXCEPTION_FLAGS**は、浮動小数点例外の種類ごとに1つのビットフィールドを格納します。 これらのフィールドと、[_controlfp](control87-controlfp-control87-2.md) に指定される例外をマスクするために使用される引数との間には対応関係があります。 各ビットの正確な意味はコンテキストに依存します。<br /><br /> **原因**-各ビットセットビットは、発生した特定の例外を示します。<br />**Enable** -各設定ビットは、特定の例外が現在マスク解除されていることを示します。<br />**Status** -各設定ビットは、特定の例外が現在保留中であることを示します。 これには、 **_controlfp**によってマスクされたために発生していない例外が含まれます。|

無効になっている保留中の例外は、有効にされたときに発生します。 これにより、 **_fpieee_flt**を例外フィルターとして使用するときに未定義の動作が発生する可能性があります。 浮動小数点例外を有効にする前に、必ず [_clearfp](clear87-clearfp.md) を呼び出してください。

## <a name="requirements"></a>必要条件

|関数|必須ヘッダー|
|--------------|---------------------|
|**_fpieee_flt**|\<fpieee.h>|

互換性の詳細については、「 [互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_fpieee.c
// This program demonstrates the implementation of
// a user-defined floating-point exception handler using the
// _fpieee_flt function.

#include <fpieee.h>
#include <excpt.h>
#include <float.h>
#include <stddef.h>

int fpieee_handler( _FPIEEE_RECORD * );

int fpieee_handler( _FPIEEE_RECORD *pieee )
{
   // user-defined ieee trap handler routine:
   // there is one handler for all
   // IEEE exceptions

   // Assume the user wants all invalid
   // operations to return 0.

   if ((pieee->Cause.InvalidOperation) &&
       (pieee->Result.Format == _FpFormatFp32))
   {
        pieee->Result.Value.Fp32Value = 0.0F;

        return EXCEPTION_CONTINUE_EXECUTION;
   }
   else
      return EXCEPTION_EXECUTE_HANDLER;
}

#define _EXC_MASK    \
    _EM_UNDERFLOW  + \
    _EM_OVERFLOW   + \
    _EM_ZERODIVIDE + \
    _EM_INEXACT

int main( void )
{
   // ...

   __try {
      // unmask invalid operation exception
      _controlfp_s(NULL, _EXC_MASK, _MCW_EM);

      // code that may generate
      // fp exceptions goes here
   }
   __except ( _fpieee_flt( GetExceptionCode(),
                GetExceptionInformation(),
                fpieee_handler ) ){

      // code that gets control

      // if fpieee_handler returns
      // EXCEPTION_EXECUTE_HANDLER goes here

   }

   // ...
}
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
[_controlfp_s](controlfp-s.md)<br/>
