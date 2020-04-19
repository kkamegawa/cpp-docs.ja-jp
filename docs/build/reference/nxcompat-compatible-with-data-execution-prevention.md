---
title: /NXCOMPAT (データ実行防止との互換性)
description: Microsoft C/C++ (MSVC)/NXCOMPAT リンカーオプションについて説明します。このオプションは、実行可能ファイルをデータ実行防止 (DEP) と互換性のあるものとしてマークします。
ms.date: 12/17/2019
f1_keywords:
- /NXCOMPAT
helpviewer_keywords:
- /NXCOMPAT linker option
- -NXCOMPAT linker option
- NXCOMPAT linker option
ms.openlocfilehash: f3a0906a49e3524fff3e1ef1643d1eceee28f169
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75298988"
---
# <a name="nxcompat-compatible-with-data-execution-prevention"></a>/NXCOMPAT (データ実行防止との互換性)

実行可能ファイルが Windows データ実行防止機能と互換性があることを示します。

## <a name="syntax"></a>構文

> **/NXCOMPAT** **[:NO]**

## <a name="remarks"></a>コメント

既定では、 **/NXCOMPAT**はオンになっています。

**/NXCOMPAT: NO**を使用して、実行可能ファイルをデータ実行防止との互換性なしに明示的に指定できます。

データ実行防止の詳細については、以下を参照してください。

- [データ実行防止](/windows/win32/Memory/data-execution-prevention)

- [データ実行防止 (Windows Embedded)](/previous-versions/windows/embedded/ms913190\(v=winembedded.5\))

### <a name="to-set-this-linker-option-in-visual-studio"></a>このリンカー オプションを Visual Studio で設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]**  > [**リンカー** > **コマンドライン**] プロパティページを選択します。

1. **[追加オプション]** ボックスにオプションを入力します。 **[OK]** または **[適用]** を選択して変更を適用します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 「 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>」を参照してください。

## <a name="see-also"></a>関連項目

[MSVC リンカーリファレンス](linking.md)\
[MSVC リンカー オプション](linker-options.md)
