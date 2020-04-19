---
title: /arch (x64)
ms.date: 10/01/2019
ms.assetid: ecda22bf-5bed-43f4-99fb-88aedd83d9d8
ms.openlocfilehash: 0ade6d9f744339ebaf38981d81334340b56080cb
ms.sourcegitcommit: 4517932a67bbf2db16cfb122d3bef57a43696242
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2019
ms.locfileid: "71816221"
---
# <a name="arch-x64"></a>/arch (x64)

x64 でのコード生成のアーキテクチャを指定します。 「 [/Arch (x86)](arch-x86.md) 」および「 [/arch (ARM)](arch-arm.md)」も参照してください。

## <a name="syntax"></a>構文

```
/arch:[AVX|AVX2|AVX512]
```

## <a name="arguments"></a>引数

**/arch: AVX**<br/>
Advanced Vector Extensions 命令の使用を有効にします。

**/arch:AVX2**<br/>
Advanced Vector Extensions 2 命令の使用を有効にします。

**/arch: AVX512**<br/>
Intel Advanced Vector Extensions 512 命令を使用できるようにします。

## <a name="remarks"></a>コメント

**/Arch**オプションを使用すると、特定の命令セット拡張機能を使用できます。特に、INTEL および AMD のプロセッサで使用可能なベクター計算で使用できます。 一般に、最近導入されたプロセッサは、古いプロセッサでサポートされているものよりも多くの拡張機能をサポートする場合があります。ただし、特定のプロセッサのドキュメントを参照するか、 を使用して命令セット拡張機能のサポートをテストする必要があります。命令セット拡張を使用してコードを実行する前の [__cpuid](../../intrinsics/cpuid-cpuidex.md)。

**/arch**は、ネイティブ関数のコード生成にのみ影響します。 [/Clr](clr-common-language-runtime-compilation.md)を使用してコンパイルする場合、 **/arch**はマネージ関数のコード生成には影響しません。

プロセッサ拡張機能には、次の特性があります。

- 既定のモードでは、スカラー浮動小数点演算とベクトル計算に SSE2 命令が使用されます。 これらの手順では、単精度、倍精度、1、2、4、8バイトの整数値、および単精度と倍精度のスカラー浮動小数点値の128ビットベクトルを使用して計算を実行できます。

- **AVX**は、128ビットまたは256ビットのベクターを許可するベクターおよび浮動小数点スカラー命令の代替命令エンコーディングを導入し、すべてのベクトル結果を完全なベクターサイズにゼロから拡張します。 (従来の互換性のために、SSE スタイルのベクター命令は、ビット127を超えるすべてのビットを保持します)。ほとんどの浮動小数点演算は、256ビットに拡張されています。

- **AVX2**は、最も多くの整数演算を256ビットベクトルに拡張し、(FMA) 命令の使用を有効にします。

- **AVX-512**では、512ビットベクターとその他のオプション機能を許可する別の命令エンコード形式が導入されました。 追加の操作の手順も追加されました。

各 **/arch**オプションでは、そのオプションに関連付けられている他の非ベクター命令を使用することもできます。 例として、 **/arch: AVX2**を指定した場合の特定の bmi 命令の使用があります。

`__AVX__` プリプロセッサシンボルは、 **/arch: AVX**、 **/arch: AVX2** 、または **/arch: AVX512**コンパイラオプションが指定されている場合に定義されます。 `__AVX2__` プリプロセッサシンボルは、 **/arch: AVX2**または **/arch: AVX512**コンパイラオプションが指定されている場合に定義されます。 `__AVX512F__`、`__AVX512CD__`、`__AVX512BW__`、`__AVX512DQ__` および `__AVX512VL__` プリプロセッサシンボルは、 **/arch: AVX512**コンパイラオプションが指定されている場合に定義されます。 詳細については、「 [Predefined Macros](../../preprocessor/predefined-macros.md)」を参照してください。 **/Arch: AVX2**オプションは Visual Studio 2013 Update 2、version 12.0.34567.1 で導入されました。 **/Arch: AVX512**のサポートは visual studio 2017 で追加され、visual studio 2019 で拡張されました。

### <a name="to-set-the-archavx-archavx2-or-archavx512-compiler-option-in-visual-studio"></a>Visual Studio で/arch: AVX、/arch: AVX2、または/arch: AVX512 コンパイラオプションを設定するには

1. プロジェクトの **[プロパティページ]** ダイアログボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]** 、 **[CC++ /]** フォルダー の順に選択します。

1. **[コード生成]** プロパティページを選択します。

1. **[拡張命令セットを有効にする]** ドロップダウンボックスで、 **[advanced vector extensions (/arch: AVX)]** 、 **[advanced vector EXTENSIONS 2 (/arch: AVX2)** ]、または **[ADVANCED vector extensions 512 (/arch: AVX512)** ] を選択します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 「<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>」を参照してください。

## <a name="see-also"></a>参照

[/arch (最小限の CPU アーキテクチャ)](arch-minimum-cpu-architecture.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
