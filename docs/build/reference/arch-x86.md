---
title: /arch (x86)
ms.date: 10/01/2019
ms.assetid: 9dd5a75d-06e4-4674-aade-33228486078d
ms.openlocfilehash: b1e5501f6edd3eb016395380ff476250c0c388b9
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816310"
---
# <a name="arch-x86"></a>/arch (x86)

x86 でコード生成のアーキテクチャを指定します。 「 [/Arch (x64)](arch-x64.md) 」および「 [/arch (ARM)](arch-arm.md)」も参照してください。

## <a name="syntax"></a>構文

```
/arch:[IA32|SSE|SSE2|AVX|AVX2|AVX512]
```

## <a name="arguments"></a>引数

**/arch:IA32**<br/>
拡張命令なしを指定し、浮動小数点計算に x87 を指定します。

**/arch:SSE**<br/>
SSE 命令の使用を有効にします。

**/arch:SSE2**<br/>
SSE2 命令の使用を有効にします。 **/Arch**オプションが指定されていない場合、これは x86 プラットフォームの既定の命令です。

**/arch: AVX**<br/>
Advanced Vector Extensions 命令の使用を有効にします。

**/arch:AVX2**<br/>
Advanced Vector Extensions 2 命令の使用を有効にします。

**/arch: AVX512**<br/>
Intel Advanced Vector Extensions 512 命令を使用できるようにします。

## <a name="remarks"></a>コメント

**/Arch**オプションを使用すると、特定の命令セット拡張機能の使用を有効または無効にすることができます (特にベクター計算の場合)。 INTEL と AMD のプロセッサで使用できます。 一般に、最近導入されたプロセッサは、古いプロセッサでサポートされているものよりも多くの拡張機能をサポートする場合があります。ただし、特定のプロセッサのドキュメントを参照するか、 を使用して命令セット拡張機能のサポートをテストする必要があります。命令セット拡張を使用してコードを実行する前の [__cpuid](../../intrinsics/cpuid-cpuidex.md)。

**/arch**は、ネイティブ関数のコード生成にのみ影響します。 [/Clr](clr-common-language-runtime-compilation.md)を使用してコンパイルする場合、 **/arch**はマネージ関数のコード生成には影響しません。

**/Arch**オプションは、次の特性を持つ命令セット拡張機能を参照します。

- **IA32**は、ベクター演算を伴わず、浮動小数点計算に x87 を使用する、従来の32ビット x86 命令セットです。

- **SSE**では、最大4つの単精度浮動小数点値のベクターを使用して計算できます。 対応するスカラー浮動小数点命令も追加されました。

- **SSE2**では、単精度、倍精度、1、2、4、または8バイトの整数値の128ビットベクトルを使用して計算できます。 倍精度のスカラー命令も追加されました。

- **AVX**は、128ビットまたは256ビットのベクターを許可するベクターおよび浮動小数点スカラー命令の代替命令エンコーディングを導入し、すべてのベクトル結果を完全なベクターサイズにゼロから拡張します。 (従来の互換性のために、SSE スタイルのベクター命令は、ビット127を超えるすべてのビットを保持します)。ほとんどの浮動小数点演算は、256ビットに拡張されています。

- **AVX2**は、最も多くの整数演算を256ビットベクターに拡張し、(FMA) 命令の使用を有効にします。

- **AVX512**は、512ビットベクターとその他の特定のオプション機能を許可するもう1つの命令エンコード形式を導入しました。 追加の操作の手順も追加されました。

どの **/arch**が指定されているかによって、どのような場合にベクター命令を使用するかがオプティマイザーによって選択されます。 スカラー浮動小数点計算は、使用可能な場合は SSE または AVX 命令を使用して実行されます。 一部の呼び出し規約では、x87 スタックで浮動小数点引数を渡すことが指定されています。その結果、コードでは、浮動小数点計算に x87 と SSE/AVX 命令の両方を組み合わせて使用できます。 整数ベクター命令は、使用可能な場合は64ビット整数演算に使用することもできます。

Vector および浮動小数点のスカラー命令に加えて、各 **/arch**オプションでは、そのオプションに関連付けられている他の非ベクター命令を使用することもできます。 例として、最初に Intel Pentium Pro プロセッサに登場した CMOVcc 命令ファミリがあります。 SSE 命令は後続の Intel Pentium III プロセッサで導入されたため、 **/arch: IA32**が指定されている場合を除き、CMOVcc 命令が生成されることがあります。

通常、浮動小数点演算は x87 コードで倍精度 (64 ビット) に丸められますが、`_controlfp` を使用して、precision 制御を有効桁数 (80 ビット) または単精度 (32 ビット) に設定するなど、FP 制御ワードを変更できます。 詳細については、「[_control87、_controlfp、\__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md)」を参照してください。 SSE と AVX には、操作ごとに個別の単精度と倍精度の命令があるため、SSE/AVX コードに相当するものはありません。 これにより、浮動小数点演算の結果がユーザー変数に割り当てられるのではなく、さらに計算で直接使用された場合に、結果がどのように丸められるかを変更できます。 次に例を示します。

```cpp
r = f1 * f2 + d;  // Different results are possible on SSE/SSE2.
```

明示的に割り当てられる場合:

```cpp
t = f1 * f2;   // Do f1 * f2, round to the type of t.
r = t + d;     // This should produce the same overall result
               // whether x87 stack is used or SSE/SSE2 is used.
```

**/arch**と[/QIfist](qifist-suppress-ftol.md)を同じコンパイル単位で使用することはできません。 **/QIfist**オプションは、浮動小数点型から整数型への変換の丸め動作を変更します。 既定の動作では、切り捨て (0 方向の丸め) が使用されます。一方、 **/QIfist**オプションでは、浮動小数点環境の丸めモードを使用します。 これにより、すべての浮動小数点型から整数型への変換の動作が変更されるため、このフラグは非推奨とされます。 SSE または AVX に対してコンパイルする場合は、組み込み関数シーケンスを使用して浮動小数点環境の丸めモードを使用し、浮動小数点値を整数に丸めることができます。

```cpp
int convert_float_to_int(float x) {
    return _mm_cvtss_si32(_mm_set_ss(x));
}

int convert_double_to_int(double x) {
    return _mm_cvtsd_si32(_mm_set_sd(x));
}
```

@No__t-0、`__AVX__`、`__AVX2__`、`__AVX512F__`、`__AVX512CD__`、`__AVX512BW__`、`__AVX512DQ__`、`__AVX512VL__` マクロは、 **/arch**コンパイラオプションが使用されているかどうかを示します。 詳細については、「 [Predefined Macros](../../preprocessor/predefined-macros.md)」を参照してください。 **/Arch: AVX2**オプションと `__AVX2__` マクロは Visual Studio 2013 Update 2、version 12.0.34567.1 で導入されました。 **/Arch: AVX512**のサポートは visual studio 2017 で追加され、visual studio 2019 で拡張されました。

### <a name="to-set-this-compiler-option-for-avx-avx2-avx512-ia32-sse-or-sse2-in-visual-studio"></a>Visual Studio で AVX、AVX2、AVX512、IA32、SSE、または SSE2 のこのコンパイラオプションを設定するには

1. プロジェクトの **[プロパティページ]** ダイアログボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]** 、 **[CC++ /]** フォルダー の順に選択します。

1. **[コード生成]** プロパティページを選択します。

1. **[拡張命令セットを有効にする]** プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>

## <a name="see-also"></a>関連項目

[/arch (最小限の CPU アーキテクチャ)](arch-minimum-cpu-architecture.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
