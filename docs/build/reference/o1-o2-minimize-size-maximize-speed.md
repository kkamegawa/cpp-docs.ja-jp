---
title: /O1、/O2 (プログラム サイズ、実行速度)
ms.date: 09/25/2017
f1_keywords:
- /o2
- /o1
helpviewer_keywords:
- maximize speed compiler option [C++]
- minimize size compiler option [C++]
- -O2 compiler option [C++]
- fast code
- small code
- O2 compiler option [C++]
- /O2 compiler option [C++]
- -O1 compiler option [C++]
- O1 compiler option [C++]
- /O1 compiler option [C++]
ms.assetid: 2d1423f5-53d9-44da-8908-b33a351656c2
ms.openlocfilehash: d33fe6bceae09267fd3f79ffe3dc26864e87c764
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320358"
---
# <a name="o1-o2-minimize-size-maximize-speed"></a>/O1、/O2 (プログラム サイズ、実行速度)

定義済みのサイズに影響するオプションのセットと生成されるコードの速度を選択します。

## <a name="syntax"></a>構文

> /O1/O2

## <a name="remarks"></a>Remarks

**/O1**と **/O2**コンパイラ オプションで、一度にいくつかの特定の最適化オプションを設定する簡単な方法です。 **/O1**オプションは、ほとんどの場合に最小のコードを作成する個々 の最適化オプションを設定します。 **/O2**オプションは、ほとんどの場合に最も高速なコードを作成するオプションを設定します。 **/O2**オプションは、リリース ビルドの既定値。 この表に、特定のオプションが設定されている **/O1**と **/O2**:

|オプション|等価です。|
|------------|-------------------|
|**/O1** (サイズ最小化)|[/Og](og-global-optimizations.md) [/Os](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|
|**/O2** (速度を最大化)|[/Og](og-global-optimizations.md) [/Oi](oi-generate-intrinsic-functions.md) [/Ot](os-ot-favor-small-code-favor-fast-code.md) [/Oy](oy-frame-pointer-omission.md) [/Ob2](ob-inline-function-expansion.md) [/GF](gf-eliminate-duplicate-strings.md) [/Gy](gy-enable-function-level-linking.md)|

**/O1**と **/O2**は相互に排他的です。

> [!NOTE]
> **x86 固有**これらのオプションでは、フレーム ポインターの省略の使用 ([/Oy](oy-frame-pointer-omission.md)) オプション。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **構成プロパティ**、オープン**C/C++** 選択し、**最適化**プロパティ ページ。

1. 変更、**最適化**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Optimization%2A>

## <a name="see-also"></a>関連項目

[/O オプション (コードの最適化)](o-options-optimize-code.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/EH (例外処理モデル)](eh-exception-handling-model.md)
