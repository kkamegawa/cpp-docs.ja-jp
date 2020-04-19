---
title: /arch (ARM)
ms.date: 11/04/2016
ms.assetid: 4f1406ff-f174-487c-a126-8ab06cf447c1
ms.openlocfilehash: b732a74d5fe223fdaf3b161d4ae92093ab5df407
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295204"
---
# <a name="arch-arm"></a>/arch (ARM)

ARM でのコード生成のアーキテクチャを指定します。 参照してください[/arch (x86)](arch-x86.md)と[/arch (x64)](arch-x64.md)します。

## <a name="syntax"></a>構文

```
/arch:[ARMv7VE|VFPv4]
```

## <a name="arguments"></a>引数

**/arch:ARMv7VE**<br/>
ARMv7VE 仮想化拡張命令の使用を有効にします。

**/arch:VFPv4**<br/>
ARM VFPv4 命令の使用を有効にします。 このオプションを指定しない場合は、VFPv3 が既定値です。

## <a name="remarks"></a>Remarks

`_M_ARM_FP` (ARM のみ) 用のマクロを示します。 存在する場合、 **/arch**コンパイラ オプションを使用します。 詳細については、「 [Predefined Macros](../../preprocessor/predefined-macros.md)」を参照してください。

使用すると[/clr](clr-common-language-runtime-compilation.md)をコンパイルする **/arch**マネージ関数のコード生成に影響を与えません。 **/arch**だけでネイティブ関数の生成のコードに影響します。

### <a name="to-set-the-archarmv7ve-or-archvfpv4-compiler-option-in-visual-studio"></a>Visual Studio で、/arch:ARMv7VE または/arch:VFPv4 コンパイラ オプションを設定するには

1. 開く、**プロパティ ページ**プロジェクトのダイアログ ボックス。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、 **C/C++** フォルダー。

1. 選択、**コマンドライン**プロパティ ページ。

1. **追加オプション**ボックスで、追加`/arch:ARMv7VE`または`/arch:VFPv4`します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.EnableEnhancedInstructionSet%2A>

## <a name="see-also"></a>関連項目

[/arch (最小限の CPU アーキテクチャ)](arch-minimum-cpu-architecture.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
