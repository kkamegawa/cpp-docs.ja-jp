---
title: _control87、_controlfp、__control87_2
ms.date: 08/29/2019
api_name:
- _control87
- _controlfp
- __control87_2
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
- _control87
- __control87_2
- control87
- _controlfp
- controlfp
- control87_2
- _control87_2
helpviewer_keywords:
- floating-point numbers, control word
- _control87 function
- control87 function
- controlfp function
- _controlfp function
- __control87_2 function
- floating-point functions, setting control word
- floating-point functions
- EM_AMBIGUOUS
- control87_2 function
ms.assetid: 0d09729d-d9a0-43d6-864c-43ff25e7e0c5
ms.openlocfilehash: 15700a5dabfbc3f8915e251bd8b9270f8f9c1a35
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942903"
---
# <a name="_control87-_controlfp-__control87_2"></a>_control87、_controlfp、__control87_2

浮動小数点制御ワードの取得および設定を行います。 **_Controlfp**のセキュリティが強化されたバージョンを利用できます。「 [_controlfp_s](controlfp-s.md)」を参照してください。

## <a name="syntax"></a>構文

```C
unsigned int _control87(
   unsigned int new,
   unsigned int mask
);
unsigned int _controlfp(
   unsigned int new,
   unsigned int mask
);
int __control87_2(
   unsigned int new,
   unsigned int mask,
   unsigned int* x86_cw,
   unsigned int* sse2_cw
);
```

### <a name="parameters"></a>パラメーター

*new*\
新しい制御ワードのビット値。

*隠す*\
新しく設定する制御ワード ビットのマスク。

*x86_cw*\
x87 浮動小数点ユニットの制御ワードが格納されます。 SSE2 制御ワードのみを設定するには、0 (**NULL**) を渡します。

*sse2_cw*\
SSE 浮動小数点ユニットの制御ワード。 X87 制御ワードのみを設定するには、0 (**NULL**) を渡します。

## <a name="return-value"></a>戻り値

**_Control87**と **_controlfp**の場合、返される値のビットは、浮動小数点のコントロールの状態を示します。 **_Control87**によって返されるビットの定義の詳細については、「FLOAT」を参照してください。始め.

**__Control87_2**の場合、戻り値は1で、成功を示します。

## <a name="remarks"></a>Remarks

**_Control87**関数は、浮動小数点制御ワードを取得して設定します。 浮動小数点制御ワードを使用すると、プログラムはプラットフォームに応じて、精度、丸め、および無限大の各モードを変更できます。 **_Control87**を使用して、浮動小数点例外のマスクまたはマスク解除を行うこともできます。 *Mask*の値が0の場合、 **_control87**は浮動小数点制御ワードを取得します。 *Mask*が0以外の場合、制御ワードの新しい値が設定されます。*Mask*でオン (つまり 1) のビットについては、 *new*の対応するビットを使用して制御ワードを更新します。 言い換えると、 **fpcntrl** = ((**fpcntrl** & ~*mask*) &#124; (*new* & *mask*)) では、 **fpcntrl**は浮動小数点制御ワードです。

> [!NOTE]
> 既定では、ランタイム ライブラリは、すべての浮動小数点例外をマスクします。

**_controlfp**はプラットフォームに依存しない **_control87**の移植可能なバージョンで、 **_control87**関数とほぼ同じです。 コードが複数のプラットフォームを対象としている場合は、 **_controlfp**または **_controlfp_s**を使用します。 **_Control87**と **_controlfp**の違いは、DENORMAL 値の扱い方です。 X86、x64、ARM、および ARM64 プラットフォームでは、 **_control87**は DENORMAL オペランドの例外マスクを設定およびクリアできます。 **_controlfp**では、DENORMAL オペランドの例外マスクは変更されません。 次の例に、この違いを示します。

```C
_control87( _EM_INVALID, _MCW_EM );
// DENORMAL is unmasked by this call
_controlfp( _EM_INVALID, _MCW_EM );
// DENORMAL exception mask remains unchanged
```

Mask 定数 (*mask*) と新しい制御値 (*new*) に使用できる値は、[制御単語マスクおよび値] テーブルに表示されます。 次に示すように、これらの関数の引数として、16進数値を明示的に指定するのではなく、下に一覧表示されている移植性のある定数 ( **_MCW_EM、** **など)** を使用します。

Intel x86 から派生したプラットフォームでは、ハードウェアでの DENORMAL 入力値と出力値がサポートされます。 x86 では DENORMAL 値を保持するように動作します。 ARM および ARM64 プラットフォームおよび SSE2 をサポートする x64 プラットフォームでは、DENORMAL のオペランドと結果をフラッシュするか、強制的にゼロにすることができます。 **_Controlfp**関数と **_control87**関数は、この動作を変更するマスクを提供します。 このマスクの使用例を次に示します。

```C
_controlfp(_DN_SAVE, _MCW_DN);
// Denormal values preserved on ARM platforms and on x64 processors with
// SSE2 support. NOP on x86 platforms.
_controlfp(_DN_FLUSH, _MCW_DN);
// Denormal values flushed to zero by hardware on ARM platforms
// and x64 processors with SSE2 support. Ignored on other x86 platforms.
```

ARM および ARM64 プラットフォームでは、 **_control87**および **_controlfp**関数は、fpscr レジスタに適用されます。 MXCSR レジスタに格納されている SSE2 制御ワードのみが、x64 プラットフォームで影響を受けます。 X86 プラットフォームでは、 **_control87**と **_controlfp**は、x87 と SSE2 の両方の制御ワードに影響します (存在する場合)。

関数 **__control87_2**を使用すると、X87 と SSE2 の両方の浮動小数点ユニットを一緒に制御することも、個別に制御することもできます。 両方の単位に影響を与えるには、2つの整数のアドレスを**x86_cw**と**sse2_cw**に渡します。 1つの単位にのみ影響を与える場合は、そのパラメーターのアドレスを渡しますが、もう一方には 0 (**NULL**) を渡します。 いずれかのパラメーターに対して 0 が渡されると、関数はその浮動小数点ユニットには影響しません。 コードの一部では x87 浮動小数点ユニットを使用し、別のパートでは SSE2 浮動小数点ユニットを使用する場合に便利です。

**__Control87_2**を使用して浮動小数点制御ワードに異なる値を設定すると、 **_control87**または **_controlfp**は、両方の浮動小数点単位の状態を表す単一の制御ワードを返すことができなくなる可能性があります。 このような場合、これらの関数は、返される整数値に**EM_AMBIGUOUS**フラグを設定して、2つの制御ワードの間に矛盾がないことを示します。 **EM_AMBIGUOUS**フラグは、返された制御ワードが両方の浮動小数点制御ワードの状態を正確に表していない可能性があることを示す警告です。

ARM、ARM64、および x64 プラットフォームでは、無限大モードまたは浮動小数点の精度の変更はサポートされていません。 有効桁数の制御マスクが x64 プラットフォームで使用されている場合、関数はアサーションを発生させ、「[パラメーターの検証](../../c-runtime-library/parameter-validation.md)」で説明されているように、無効なパラメーターハンドラーが呼び出されます。

> [!NOTE]
> **__control87_2**は、ARM、ARM64、または x64 プラットフォームではサポートされていません。 **__Control87_2**を使用して、ARM、ARM64、または x64 プラットフォーム用にプログラムをコンパイルすると、コンパイラによってエラーが生成されます。

これらの関数は、 [/clr (共通言語ランタイムのコンパイル)](../../build/reference/clr-common-language-runtime-compilation.md)を使用してコンパイルするときには無視されます。 共通言語ランタイム (CLR) では、浮動小数点の既定の精度のみがサポートされます。

### <a name="control-word-masks-and-values"></a>制御 (単語マスクと値を)

**_MCW_EM** mask では、マスクをクリアすると、ハードウェア例外を許可する例外が設定されます。マスクを設定すると、例外が非表示になります。 **アンダーフロー**または**オーバーフロー**が発生した場合、次の浮動小数点命令が実行されるまで、ハードウェア例外はスローされません。 (_s) ハードウェア例外を生成するには、すぐに、または**オーバーフロー**が**発生した**後で、 **fwait** MASM 命令を呼び出します。

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
|**_control87**、 **_controlfp**、 **_control87_2**|\<float.h>|

互換性の詳細については、「[互換性](../../c-runtime-library/compatibility.md)」を参照してください。

## <a name="example"></a>例

```C
// crt_cntrl87.c
// processor: x86
// compile by using: cl /W4 /arch:IA32 crt_cntrl87.c
// This program uses __control87_2 to output the x87 control
// word, set the precision to 24 bits, and reset the status to
// the default.

#include <stdio.h>
#include <float.h>
#pragma fenv_access (on)

int main( void )
{
    double a = 0.1;
    unsigned int control_word_x87 = 0;
    int result;

    // Show original x87 control word and do calculation.
    result = __control87_2(0, 0, &control_word_x87, 0 );
    printf( "Original: 0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Set precision to 24 bits and recalculate.
    result = __control87_2(_PC_24, MCW_PC, &control_word_x87, 0 );
    printf( "24-bit:   0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );

    // Restore default precision-control bits and recalculate.
    result = __control87_2( _CW_DEFAULT, MCW_PC, &control_word_x87, 0 );
    printf( "Default:  0x%.8x\n", control_word_x87 );
    printf( "%1.1f * %1.1f = %.15e\n", a, a, a * a );
}
```

```Output
Original: 0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
24-bit:   0x000a001f
0.1 * 0.1 = 9.999999776482582e-03
Default:  0x0009001f
0.1 * 0.1 = 1.000000000000000e-02
```

## <a name="see-also"></a>関連項目

[浮動小数点サポート](../../c-runtime-library/floating-point-support.md)\
[_clear87、_clearfp](clear87-clearfp.md)\
[_status87、_statusfp、_statusfp2](status87-statusfp-statusfp2.md)\
[_controlfp_s](controlfp-s.md)
