---
title: _controlfp_s
ms.date: 04/05/2018
api_name:
- _controlfp_s
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
- controlfp_s
- _controlfp_s
helpviewer_keywords:
- floating-point numbers, control word
- controlfp_s function
- floating-point functions, setting control word
- EM_AMBIGUOUS
- _controlfp_s function
ms.assetid: a51fc3f6-ab13-41f0-b227-6bf02d98e987
ms.openlocfilehash: 0d12c139f305a3c66419a4e27905ac9f73345f4d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942880"
---
# <a name="_controlfp_s"></a>_controlfp_s

浮動小数点制御ワードの取得および設定を行います。 これは、「[CRT のセキュリティ機能](../../c-runtime-library/security-features-in-the-crt.md)」の説明にあるとおり、セキュリティが強化されたバージョンの [_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md) です。

## <a name="syntax"></a>構文

```C
errno_t _controlfp_s(
    unsigned int *currentControl,
    unsigned int newControl,
    unsigned int mask
);
```

### <a name="parameters"></a>パラメーター

*currentControl*<br/>
現在の制御ワードのビット値。

*基準*<br/>
新しい制御ワードのビット値。

*隠す*<br/>
新しく設定する制御ワード ビットのマスク。

## <a name="return-value"></a>戻り値

成功した場合は0、または**errno**値エラーコード。

## <a name="remarks"></a>Remarks

**_Controlfp_s**関数は、プラットフォームに依存しない、より安全なバージョンの **_control87**です。これは、 *currentcontrol*に格納されているアドレスに浮動小数点制御ワードを取得し、 *newcontrol*を使用して設定します。 この値のビットは、浮動小数点のコントロールの状態を示します。 浮動小数点のコントロールの状態を使用すると、プログラムで使用する浮動小数点演算パッケージの精度、丸め、および無限大の各モードをプラットフォームに応じて変更できます。 **_Controlfp_s**を使用して、浮動小数点例外のマスクまたはマスク解除を行うこともできます。

*Mask*の値が0の場合、 **_controlfp_s**は浮動小数点制御ワードを取得し、取得した値を*currentcontrol*に格納します。

*Mask*が0以外の場合、制御ワードの新しい値が設定されます。*Mask*で設定されている (つまり1に等しい) ビットについては、 *new*の対応するビットが制御ワードの更新に使用されます。 言い換えると、 *fpcntrl* = ((*fpcntrl* & ~*mask*) &#124; (*newcontrol* & *mask*)) では、 *fpcntrl*は浮動小数点制御ワードです。 このシナリオでは、変更が完了した後に*Currentcontrol*が値に設定されます。これは、古い制御ワードのビット値ではありません。

> [!NOTE]
> 既定では、ランタイム ライブラリは、すべての浮動小数点例外をマスクします。

**_controlfp_s**は、Intel (x86)、x64、および ARM プラットフォームの **_control87**関数とほぼ同じです。 X86、x64、または ARM プラットフォームを対象としている場合は、 **_control87**または **_controlfp_s**を使用できます。

**_Control87**と **_controlfp_s**の違いは、denormal 値の扱い方です。 Intel (x86)、x64、および ARM プラットフォームの場合、 **_control87**は DENORMAL オペランド例外マスクを設定およびクリアできます。 **_controlfp_s**では、DENORMAL オペランドの例外マスクは変更されません。 次の例に、この違いを示します。

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call.
unsigned int current_word = 0;
_controlfp_s( &current_word, _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged.
```

マスク定数 (*mask*) と新しいコントロール値 (*newcontrol*) に使用できる値は、次の16進値の表に示されています。 次に示すように、これらの関数の引数として、16進数値を明示的に指定するのではなく、下記の移植性の高い定数 ( **_MCW_EM、** **など)** を使用します。

Intel (x86) から派生したプラットフォームでは、DENORMAL 入出力値がハードウェアでサポートされています。 x86 では DENORMAL 値を保持するように動作します。 ARM プラットフォームおよび SSE2 をサポートする x64 プラットフォームでは、DENORMAL のオペランドと結果をフラッシュするか、強制的にゼロにすることができます。 **_Controlfp_s**、 **_controlfp**、および **_control87**の各関数は、この動作を変更するマスクを提供します。 このマスクの使用例を次に示します。

```C
unsigned int current_word = 0;
_controlfp_s(&current_word, _DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp_s(&current_word, _DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

ARM プラットフォームでは、 **_controlfp_s**関数は、fpscr レジスタに適用されます。 X64 アーキテクチャでは、MXCSR レジスタに格納されている SSE2 制御ワードのみが影響を受けます。 Intel (x86) プラットフォームでは、 **_controlfp_s**は X87 と SSE2 の両方の制御ワードに影響します (存在する場合)。 2つの制御ワードが相互に一貫性を持たない可能性があります (たとえば、 [__control87_2](control87-controlfp-control87-2.md)を以前に呼び出したため)。2つの制御ワードの間に矛盾がある場合、 **_controlfp_s**は*Currentcontrol*の**EM_AMBIGUOUS**フラグを設定します。 これは、返された制御ワードが両方の浮動小数点制御ワードの状態を正確に表していない可能性があるという警告です。

ARM および x64 アーキテクチャでは、無限大モードまたは浮動小数点の精度の変更はサポートされていません。 有効桁数の制御マスクが x64 プラットフォームで使用されている場合、関数はアサーションを発生させ、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。

マスクが正しく設定されていないと、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、この関数は無効なパラメーターの例外を生成します。 実行の継続が許可された場合、この関数は**einval**を返し、 **errno**を**einval**に設定します。

共通言語ランタイム (CLR) は浮動小数点の既定の精度のみをサポートするため、 [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)を使用してコンパイルすると、この関数は無視されます。

### <a name="mask-constants-and-values"></a>定数と値をマスクする

**_MCW_EM** mask の場合、これをオフにすると例外が設定され、ハードウェアの例外が発生します。設定すると、例外が非表示になります。 **アンダーフロー**または**オーバーフロー**が発生した場合、次の浮動小数点命令が実行されるまで、ハードウェア例外はスローされません。 (_s) ハードウェア例外を生成するには、すぐに、または**オーバーフロー**が**発生した**後で、fwait MASM 命令を呼び出します。

|マスク|16 進値|定数|16 進値|
|----------|---------------|--------------|---------------|
|**_MCW_DN**(Denormal コントロール)|0x03000000|**_DN_SAVE**<br /><br /> **フラッシュ (_D)**|0x00000000<br /><br /> 0x01000000|
|**_MCW_EM**(割り込み例外マスク)|0x0008001F|**無効 (_C)**<br /><br /> **_EM_DENORMAL**<br /><br /> **ゼロ除算 (_S)**<br /><br /> **_EM_OVERFLOW**<br /><br /> **アンダーフロー (_S)**<br /><br /> **正確でない (_C)**|0x00000010<br /><br /> 0x00080000<br /><br /> 0x00000008<br /><br /> 0x00000004<br /><br /> 0x00000002<br /><br /> 0x00000001|
|**_MCW_IC**(無限大制御)<br /><br /> (ARM または x64 プラットフォームではサポートされていません)。|0x00040000|**_ アフィン (_D)**<br /><br /> **すべての射影 (_C)**|0x00040000<br /><br /> 0x00000000|
|**_MCW_RC**(丸め制御)|0x00000300|**上書き (_R)**<br /><br /> **開始 (_S)**<br /><br /> **_RC_DOWN**<br /><br /> **_RC_NEAR**|0x00000300<br /><br /> 0x00000200<br /><br /> 0x00000100<br /><br /> 0x00000000|
|**_MCW_PC**(精度制御)<br /><br /> (ARM または x64 プラットフォームではサポートされていません)。|0x00030000|**Pc24 (_D)** (24 ビット)<br /><br /> **Pc53 (_D)** (53 ビット)<br /><br /> **_ 64**(64 ビット)|0x00020000<br /><br /> 0x00010000<br /><br /> 0x00000000|

## <a name="requirements"></a>必要条件

|ルーチンによって返される値|必須ヘッダー|
|-------------|---------------------|
|**_controlfp_s**|\<float.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_contrlfp_s.c
// processor: x86
// This program uses _controlfp_s to output the FP control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word;
    int err;

    // Show original FP control word and do calculation.
    err = _controlfp_s(&control_word, 0, 0);
    if ( err ) /* handle error here */;

    printf( "Original: 0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    err = _controlfp_s(&control_word, _PC_24, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "24-bit:   0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    err = _controlfp_s(&control_word, _CW_DEFAULT, MCW_PC);
    if ( err ) /* handle error here */;

    printf( "Default:  0x%.4x\n", control_word );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x9001f
0.1 * 0.1 = 1.000000000000000e-002
24-bit:   0xa001f
0.1 * 0.1 = 9.999999776482582e-003
Default:  0x9001f
0.1 * 0.1 = 1.000000000000000e-002
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)<br/>
[_clear87、_clearfp](clear87-clearfp.md)<br/>
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)<br/>
[_control87、_controlfp、\__control87_2](control87-controlfp-control87-2.md)<br/>
