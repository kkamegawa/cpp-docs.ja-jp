---
title: /fp (浮動小数点の動作を指定してください)
ms.date: 11/09/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.floatingPointModel
- VC.Project.VCCLWCECompilerTool.FloatingPointExceptions
- /fp
- VC.Project.VCCLWCECompilerTool.floatingPointModel
- VC.Project.VCCLCompilerTool.FloatingPointExceptions
helpviewer_keywords:
- -fp compiler option [C++]
- /fp compiler option [C++]
ms.assetid: 10469d6b-e68b-4268-8075-d073f4f5d57e
ms.openlocfilehash: 25b228c16f534ca227d50bfdf632fdacb5703cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292356"
---
# <a name="fp-specify-floating-point-behavior"></a>/fp (浮動小数点の動作を指定してください)

コンパイラによる浮動小数点式、最適化、および例外の処理方法を指定します。 **/Fp**オプションかどうか、生成されたコードは、浮動小数点環境の丸めモード、例外マスク、および、ある動作の変更点し、現在、正確な浮動小数点状態を確認を返すかどうかを指定結果。 コンパイラがソースの操作と式の順序を維持し、NaN の伝達を標準に準拠しているコードを生成するかどうか、または代わりにして可能性がありますの順序を変更または操作にまとめるの簡略化を使用してより効率的なコードが生成するかどうかを制御します。標準で許可されていない代数変換します。

## <a name="syntax"></a>構文

> **/fp:** [**precise** | **strict** | **fast** | **except**[ **-** ]]

### <a name="arguments"></a>引数

#### <a name="precise"></a>正確です

既定では、コンパイラを使用して`/fp:precise`動作します。

`/fp:precise`コンパイラは浮動小数点コードのプロパティを生成し、ターゲット マシンのオブジェクト コードを最適化するときに丸め処理の順序付けと、元の式を保持します。 コンパイラが式の評価中に次の 4 つの特定の時点で、ソース コードの有効桁数に丸められます。 割り当てである丸めない、浮動小数点引数は、関数呼び出しに渡されるとき、および浮動小数点値が関数呼び出しから返されます。 マシンの有効桁数で中間の計算を実行できます。 丸めない中間の計算を明示的に丸めるために使用できます。

コンパイラは、変換は、ビットごとのと同じ結果を生成することが保証されても再関連付けまたは配布などの浮動小数点式に代数変換を行いません。
特殊な値 (NaN、+ infinity、無限大、-0.0) を含む式は、IEEE 754 仕様に従って処理されます。 たとえば、`x != x`に評価される**true** x が NaN の場合。 浮動小数点*短縮系*、下を組み合わせた浮動小数点演算は、機械語命令を生成することが、`/fp:precise`します。

コンパイラで実行するコードを生成、[既定の浮動小数点環境](#the-default-floating-point-environment)浮動小数点環境のアクセスまたは実行時に変更がいないことを前提としています。 つまり、こと、コードはいない浮動小数点例外をマスク解除、読み取りまたは書き込み浮動小数点ステータス レジスタ、または丸めモードを変更すると仮定します。

浮動小数点コードが操作と、浮動小数点のステートメント内の式の順序に依存しない場合 (重要でない場合など、かどうか`a * b + a * c`として計算されます`(b + c) * a`または`2 * a`として`a + a`)、を検討してください。[/fp:fast](#fast)オプションは、高速より効率的なコードを生成できます。 コード両方演算よぶ式、順序に依存しにアクセスまたは場合 (たとえば、丸めモードを変更するか、浮動小数点例外をトラップする) の浮動小数点環境を変更しますを使用[/fp: 厳密な](#strict)します。

#### <a name="strict"></a>strict

`/fp:strict` 似た動作が`/fp:precise`は、コンパイラはソースの順序を保持、およびデータベース オブジェクト、ターゲット マシン コードを生成し、最適化する場合、浮動小数点コードのプロパティを丸め、および特殊な値を処理するときに、標準の監視します。 さらに、プログラムがアクセス安全に、または実行時の浮動小数点環境を変更する可能性があります。

`/fp:strict`、コンパイラにより安全に浮動小数点例外をマスク解除、読み取りまたは書き込み浮動小数点ステータス レジスタ、または、丸めモードを変更するには、プログラム コードを生成します。 式の評価中に次の 4 つの特定の時点で、ソース コードの有効桁数に丸められます。 割り当てである丸めない、浮動小数点引数は、関数呼び出しに渡されるとき、および浮動小数点値が関数呼び出しから返されます。 マシンの有効桁数で中間の計算を実行できます。 丸めない中間の計算を明示的に丸めるために使用できます。 コンパイラは、変換は、ビットごとのと同じ結果を生成することが保証されても再関連付けまたは配布などの浮動小数点式に代数変換を行いません。 特殊な値 (NaN、+ infinity、無限大、-0.0) を含む式は、IEEE 754 仕様に従って処理されます。 たとえば、`x != x`に評価される**true** x が NaN の場合。 浮動小数点の短縮形は生成されません`/fp:strict`します。

`/fp:strict` より負荷`/fp:precise`のため、コンパイラは、例外をトラップし、プログラムへのアクセスまたは実行時に、浮動小数点環境を変更できるようにする追加の手順を挿入する必要があります。 使用の場合は、コードではソース コードの順序付けと、丸め処理が必要ですか、または特殊な値に依存していますが、この機能を使用しない、`/fp:precise`します。 それ以外の場合、使用を検討して`/fp:fast`、高速で小さいコードを生成することができます。

#### <a name="fast"></a>高速します。

`/fp:fast`オプションの順序を変更、結合、または速度と領域の浮動小数点コードを最適化するために浮動小数点演算を簡略化にコンパイラを使用できます。 コンパイラは、代入ステートメントで丸め処理を省略することもできます、丸めない、または関数呼び出し。 操作の順序を変更、場合でも、このような変換が著しく異なる丸め動作になる結合規則および分配法を使用して、代数変換を実行します。 その他によって生成されたものと、この強化された最適化のため一部浮動小数点演算の結果が異なる場合があります`/fp`オプション。 特殊な値 (NaN、+ infinity、無限大、-0.0) は反映されませんまたは IEEE 754 標準に従って厳密に動作します。 浮動小数点の短縮形を生成することが`/fp:fast`します。 コンパイラは基になるアーキテクチャは、で、まだバインドされて`/fp:fast`、およびその他の最適化を使用して利用可能な場合があります、 [/arch](arch-minimum-cpu-architecture.md)オプション。

`/fp:fast`コンパイラは、既定の浮動小数点環境で実行するコードを生成し、浮動小数点環境がアクセスされていないかどうか、または実行時に変更ことを前提としています。 つまり、こと、コードはいない浮動小数点例外をマスク解除、読み取りまたは書き込み浮動小数点ステータス レジスタ、または丸めモードを変更すると仮定します。

`/fp:fast` 浮動小数点式の丸め処理の順序付けと厳密なソース コードを必要としないと、NaN などの特殊な値を処理するための標準の規則に依存しないプログラムに対するものです。 場合は、浮動小数点コードが順序付けと丸め処理、ソース コードの保持が必要ですか、または使用して、特別な値の標準の動作に依存[/fp: 正確な](#precise)します。 浮動小数点の例外をマスク解除または浮動小数点状態を確認、使用する場合は、コードでは、アクセスまたは浮動小数点丸めモードを変更する環境を変更、 [/fp: 厳密な](#strict)します。

#### <a name="except"></a>除く

`/fp:except`オプションはマスクされていない、浮動小数点例外が発生した位置の正確なポイントで発生して、その他の浮動小数点例外が発生しなかったことを確実にコードを生成します。 既定では、`/fp:strict`オプションにより`/fp:except`、および`/fp:precise`はありません。 `/fp:except`オプションと互換性がない`/fp:fast`します。 おかげで、オプションを明示的に無効にできます`/fp:except-`します。

なお`/fp:except`自体は、浮動小数点例外を有効にしませんが浮動小数点例外を有効にするプログラムに必要になります。 参照してください[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)浮動小数点例外を有効にする方法についてはします。

## <a name="remarks"></a>Remarks

複数`/fp`同じコンパイラのコマンドラインでオプションを指定できます。 いずれかのみ`/fp:strict`、 `/fp:fast`、および`/fp:precise`一度にオプションを有効にすることができます。 これらのオプションの 1 つ以上がコマンドラインで指定されている場合は、以降のオプションが優先され、コンパイラ警告が生成されます。 `/fp:strict`と`/fp:except`オプションと互換性がない`/clr`します。

[/Za](za-ze-disable-language-extensions.md) (ANSI 互換性) オプションと互換性がない`/fp`します。

### <a name="using-compiler-directives-to-control-floating-point-behavior"></a>コンパイラ ディレクティブを使用して、浮動小数点の動作を制御するには

コンパイラが提示する、コマンドラインで指定された浮動小数点の動作をオーバーライドする次の 3 つのプラグマ ディレクティブ: [float_control](../../preprocessor/float-control.md)、 [fenv_access](../../preprocessor/fenv-access.md)、および[fp_contract](../../preprocessor/fp-contract.md). これらのディレクティブを使用して、関数内ではなく、関数レベルでの浮動小数点の動作を制御することができます。 これらのディレクティブに直接対応しないことに注意してください、`/fp`オプション。 この表に示しますが、どのように`/fp`オプションとプラグマ ディレクティブは、相互にマップします。 詳細については、個々 のオプションとプラグマ ディレクティブのドキュメントを参照してください。

||float_control(precise)|float_control(except)|fenv_access|fp_contract|
|-|-|-|-|-|
|`/fp:fast`|オフ|オフ|オフ|on|
|`/fp:precise`|on|オフ|オフ|on|
|`/fp:strict`|on|on|on|オフ|

### <a name="the-default-floating-point-environment"></a>既定の浮動小数点環境

プロセスが初期化されるときに、*浮動小数点環境の既定*設定されます。 この環境のすべての浮動小数点例外をマスク、最も近い値に丸めるに丸めモードを設定 (`FE_TONEAREST`)、あるを保持 (denormal) の有効桁 (仮数) の既定の有効桁数を使用して値を**float**、 **double**、および**long double**数値を使用して、サポートされている場合は、無限大コントロールを既定のアフィン モードに設定します。

### <a name="floating-point-environment-access-and-modification"></a>浮動小数点環境へのアクセスおよび変更

Microsoft Visual C ランタイムにアクセスして、浮動小数点環境を変更するいくつかの機能を提供します。 以下の[_controlfp](../../c-runtime-library/reference/control87-controlfp-control87-2.md)、 [_clearfp](../../c-runtime-library/reference/clear87-clearfp.md)、および[_statusfp](../../c-runtime-library/reference/status87-statusfp-statusfp2.md)とそのバリエーションです。 コードがアクセスまたは浮動小数点環境を変更する際に、適切なプログラムの動作を確保する`fenv_access`する必要がありますを有効にする、いずれかによって、`/fp:strict`オプションまたはの使用による、`fenv_access`プラグマは、これらの関数を有効にします。 ときに`fenv_access`が有効になっていない場合は、アクセスまたは浮動小数点環境の変更可能性がプログラムの予期しない動作: コードは、浮動小数点環境への要求された変更を優先しないことがあります浮動小数点ステータス レジスタを報告しない可能性があります。想定または現在の結果。浮動小数点の予期しない例外が発生するし、予期される浮動小数点の例外は発生しません。

コードでは、アクセスまたは浮動小数点環境を変更、ときにする必要があるコードを組み合わせると、`fenv_access`がないコードでは有効です`fenv_access`を有効にします。 コードで、`fenv_access`が有効でないと見なされます、プラットフォームの既定の浮動小数点環境が実際には、および浮動小数点のステータスのアクセスまたは変更されていないこと。 保存してコントロールを持たない関数に転送する前に、ローカル浮動小数点環境を既定の状態に復元するをお勧め`fenv_access`を有効にします。 この例では、どのように`float_control`プラグマを設定および復元できます。

```cpp
#pragma float_control(strict, on, push)
// Code that uses /fp:strict mode
#pragma float_control(pop)
```

### <a name="floating-point-rounding-modes"></a>浮動小数点丸めモード

両方の`/fp:precise`と`/fp:fast`コンパイラが既定の浮動小数点環境で実行するコードを生成し、環境がアクセスされていないかどうか、または実行時に変更ことを前提としています。 つまり、こと、コードはいない浮動小数点例外をマスク解除、読み取りまたは書き込み浮動小数点ステータス レジスタ、または丸めモードを変更すると仮定します。  ただし、一部のプログラムは、浮動小数点環境を変更する必要があります。 たとえば、このサンプルでは、浮動小数点丸めモードを変更することで浮動小数点の乗算のエラーの境界を計算します。

```cpp
// fp_error_bounds.cpp
#include <iostream>
#include <limits>
using namespace std;

int main(void)
{
    float a = std::<float>::max();
    float b = -1.1;
    float cLower = 0.0;
    float cUpper = 0.0;
    unsigned int control_word = 0;
    int err = 0;

    // compute lower error bound.
    // set rounding mode to -infinity.
    err = _controlfp_s(&control_word, _RC_DOWN, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_DOWN, _MCW_RC) failed with error:" << err << endl;
    }  
    cLower = a * b;

    // compute upper error bound.
    // set rounding mode to +infinity.
    err = _controlfp_s(&control_word, _RC_UP, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _RC_UP, _MCW_RC) failed with error:" << err << endl;
    }
    cUpper = a * b;

    // restore default rounding mode.
    err = _controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC);
    if (err)
    {
        cout << "_controlfp_s(&control_word, _CW_DEFAULT, _MCW_RC) failed with error:" << err << endl;
    }
    // display error bounds.
    cout << "cLower = " << cLower << endl;
    cout << "cUpper = " << cUpper << endl;
    return 0;
}
```

コンパイラには、浮動小数点環境下で、既定値が前提としていますので`/fp:fast`と`/fp:precise`への呼び出しを無視する無料`_controlfp_s`します。 たとえば、両方を使用してコンパイルされるときに`/O2`と`/fp:precise`x86 アーキテクチャでは、境界が計算されていないと、サンプル プログラムの出力します。

```Output
cLower = -inf
cUpper = -inf
```

両方のコンパイル時に`/O2`と`/fp:strict`x86 アーキテクチャでは、サンプル プログラムの出力します。

```Output
cLower = -inf
cUpper = -3.40282e+38
```

### <a name="floating-point-special-values"></a>浮動小数点の特殊な値

`/fp:precise`と`/fp:strict`、特殊な値 (NaN、+ infinity、無限大、-0.0) を含む式は、IEEE 754 仕様に従って動作します。 `/fp:fast`、これらの特殊な値の動作が IEEE 754 と一貫性がない可能性があります。

このサンプルは、特殊な値の動作の違いを示します`/fp:precise`、`/fp:strict`と`/fp:fast`:。

```cpp
// fp_special_values.cpp
#include <stdio.h>
#include <cmath>

float gf0 = -0.0;

int main()
{
    float f1 = INFINITY;
    float f2 = NAN;
    float f3 = -INFINITY;
    bool a, b;
    float c, d, e;
    a = (f1 == f1);
    b = (f2 == f2);
    c = (f1 - f1);
    d = (f2 - f2);
    printf("INFINITY == INFINITY : %d\n", a);
    printf("NAN == NAN           : %d\n", b);
    printf("INFINITY - INFINITY  : %f\n", c);
    printf("NAN - NAN            : %f\n", d);

    e = gf0 / abs(f3);
    printf("std::signbit(-0.0/-INFINITY): %d\n", std::signbit(c));
    return 0;
}
```

コンパイルした場合`/O2``/fp:precise`または`/O2` `/fp:strict` x86 アーキテクチャでは、出力は、IEEE 754 仕様に一致します。

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 0
INFINITY - INFINITY  : -nan(ind)
NAN - NAN            : -nan(ind)
std::signbit(-0.0/-INFINITY): 1
```

コンパイルされたときに`/O2` `/fp:fast` x86 アーキテクチャでは、出力は、IEEE 754 と矛盾します。

```Output
INFINITY == INFINITY : 1
NAN == NAN           : 1
INFINITY - INFINITY  : 0.000000
NAN - NAN            : 0.000000
std::signbit(-0.0/-INFINITY): 0
```

### <a name="floating-point-algebraic-transformations"></a>代数の浮動小数点の変換

`/fp:precise`と`/fp:strict`コンパイラが数学的変換を実行していない、変換は、ビットごとのと同じ結果を生成することが保証されています。 コンパイラが下には、このような変換を実行できます`/fp:fast`します。 たとえば、式`a * b + a * c`サンプル関数で`algebraic_transformation`にコンパイルされる可能性があります`a * (b + c)``/fp:fast`します。 このような変換は実行しません`/fp:precise`または`/fp:strict`、コンパイラが生成および`a * b + a * c`します。

```cpp
float algebraic_transformation (float a, float b, float c)
{
    return a * b + a * c;
}
```

### <a name="floating-point-explicit-casting-points"></a>浮動小数点の明示的なキャストのポイント

`/fp:precise`と`/fp:strict`コンパイラが式の評価中に次の 4 つの特定の時点で、ソース コードの有効桁数に丸められます: で、割り当てに丸めない、浮動小数点引数が関数の呼び出しに渡されると、ときに、浮動小数点値は、関数呼び出しから返されます。 丸めない中間の計算を明示的に丸めるために使用できます。 `/fp:fast`、ソース コードの精度を保証するためにこれらのポイントでの明示的なキャストが生成されません。 このサンプルで異なる動作`/fp`オプション。

```cpp
float casting(float a, float b)
{
    return 5.0*((double)(a+b));
}
```

使用してコンパイルされるときに`/O2``/fp:precise`または`/O2` `/fp:strict`、明示的な型キャストが両方型キャストと x64 の場合、生成されたコードで関数戻り値のポイントを挿入することを確認できますアーキテクチャ。

```asm
        addss    xmm0, xmm1
        cvtss2sd xmm0, xmm0
        mulsd    xmm0, QWORD PTR __real@4014000000000000
        cvtsd2ss xmm0, xmm0
        ret      0
```

`/O2` `/fp:fast`すべての型キャストを最適化するため、生成されたコードが簡略化します。

```asm
        addss    xmm0, xmm1
        mulss    xmm0, DWORD PTR __real@40a00000
        ret      0
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++**  > **コード生成**プロパティ ページ。

1. 変更、**浮動小数点モデル**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.floatingPointModel%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
