---
title: intrinsic プラグマ
ms.date: 08/29/2019
f1_keywords:
- intrinsic_CPP
- vc-pragma.intrinsic
helpviewer_keywords:
- intrinsic pragma
- pragmas, intrinsic
ms.assetid: 25c86ac7-ef40-47b7-a2c0-fada9c5dc3c5
ms.openlocfilehash: bb4403abf5e278ed3727af660579e22ab69592c7
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220944"
---
# <a name="intrinsic-pragma"></a>intrinsic プラグマ

プラグマの引数リストで指定された関数の呼び出しが組み込みであることを指定します。

## <a name="syntax"></a>構文

> **#pragma 組み込み (** *function1* [ **,** _function2_ ...] **)**

## <a name="remarks"></a>Remarks

**組み込み**プラグマは、関数が既知の動作を持つことをコンパイラに指示します。 コンパイラは、関数を呼び出し、より優れたパフォーマンスを得られる場合は、関数呼び出しをインライン命令に置き換えないことがあります。

組み込み形式のライブラリ関数を以下に示します。 **組み込み**のプラグマが検出されると、指定した組み込み関数を含む最初の関数定義で有効になります。 効果は、ソースファイルの末尾、または同じ組み込み関数を指定する`function`プラグマの外観まで継続されます。 **組み込み**プラグマは、関数定義の外部でグローバルレベルでのみ使用できます。

次の関数には組み込みのフォームがあり、 [/Oi](../build/reference/oi-generate-intrinsic-functions.md)を指定するときに組み込みフォームが使用されます。

|||||
|-|-|-|-|
|[_disable](../intrinsics/disable.md)|[_outp](../c-runtime-library/outp-outpw-outpd.md)|[fabs](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|[strcmp](../c-runtime-library/reference/strcmp-wcscmp-mbscmp.md)|
|[_enable](../intrinsics/enable.md)|[_outpw](../c-runtime-library/outp-outpw-outpd.md)|[labs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcpy](../c-runtime-library/reference/strcpy-wcscpy-mbscpy.md)|
|[_inp](../c-runtime-library/inp-inpw-inpd.md)|[_rotl](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcmp](../c-runtime-library/reference/memcmp-wmemcmp.md)|[strlen](../c-runtime-library/reference/strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)|
|[_inpw](../c-runtime-library/inp-inpw-inpd.md)|[_rotr](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|[memcpy](../c-runtime-library/reference/memcpy-wmemcpy.md)||
|[_lrotl](../c-runtime-library/reference/lrotl-lrotr.md)|[_strset](../c-runtime-library/reference/strset-strset-l-wcsset-wcsset-l-mbsset-mbsset-l.md)|[memset](../c-runtime-library/reference/memset-wmemset.md)||
|[_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|[abs](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|[strcat](../c-runtime-library/reference/strcat-wcscat-mbscat.md)||

組み込み関数を使用するプログラムは、関数呼び出しのオーバーヘッドがないため、より高速になりますが、追加のコードが生成されるため、より大きい場合があります。

**x86 固有**

`_disable` と`_enable`の組み込みは、割り込みを無効または有効にするカーネルモード命令を生成します。カーネルモードドライバーで役立つ可能性があります。

### <a name="example"></a>例

を使用`cl -c -FAs sample.c`してコマンドラインから次のコードをコンパイルし、sample .asm を調べて、x86 命令 CLI および STI になることを確認します。

```cpp
// pragma_directive_intrinsic.cpp
// processor: x86
#include <dos.h>   // definitions for _disable, _enable
#pragma intrinsic(_disable)
#pragma intrinsic(_enable)
void f1(void) {
   _disable();
   // do some work here that should not be interrupted
   _enable();
}
int main() {
}
```

**終了 x86 固有**

次に示す浮動小数点関数には、真の組み込み形式はありません。 代わりに、引数をプログラム スタックにプッシュするのではなく、浮動小数点演算コプロセッサに直接渡すバージョンがあります。

|||||
|-|-|-|-|
|[acos](../c-runtime-library/reference/acos-acosf-acosl.md)|[cosh](../c-runtime-library/reference/cosh-coshf-coshl.md)|[pow](../c-runtime-library/reference/pow-powf-powl.md)|[tanh](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|
|[asin](../c-runtime-library/reference/asin-asinf-asinl.md)|[fmod](../c-runtime-library/reference/fmod-fmodf.md)|[sinh](../c-runtime-library/reference/sinh-sinhf-sinhl.md)||

次に示す浮動小数点関数には、 [/Oi](../build/reference/oi-generate-intrinsic-functions.md)、 [/og](../build/reference/og-global-optimizations.md)、および[/fp: fast](../build/reference/fp-specify-floating-point-behavior.md) (または、/og: [/ox](../build/reference/ox-full-optimization.md)、 [/O1](../build/reference/o1-o2-minimize-size-maximize-speed.md)、および[/O2](../build/reference/o1-o2-minimize-size-maximize-speed.md)を含む任意のオプション) を指定するときに、実際の組み込みフォームがあります。

|||||
|-|-|-|-|
|[atan](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[exp](../c-runtime-library/reference/exp-expf.md)|[log10](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sqrt](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|
|[atan2](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|[log](../c-runtime-library/reference/log-logf-log10-log10f.md)|[sin](../c-runtime-library/reference/sin-sinf-sinl.md)|[tan](../c-runtime-library/reference/tan-tanf-tanl.md)|
|[cos](../c-runtime-library/reference/cos-cosf-cosl.md)||||

[/Fp: strict](../build/reference/fp-specify-floating-point-behavior.md)または[/za](../build/reference/za-ze-disable-language-extensions.md)を使用すると、真の組み込み浮動小数点オプションの生成をオーバーライドできます。 浮動小数点関数はライブラリ ルーチンとして生成されます。これらのライブラリ ルーチンでは、引数はプログラム スタックにプッシュされずに、数値演算コプロセッサに直接渡されます。

ソーステキストのブロックの組み込みを有効または無効にする方法の詳細と例については、「 [#pragma 関数](../preprocessor/function-c-cpp.md)」を参照してください。

## <a name="see-also"></a>関連項目

[プラグマディレクティブと __ プラグマキーワード](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[コンパイラの組み込み](../intrinsics/compiler-intrinsics.md)
