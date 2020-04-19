---
title: /CLRIMAGETYPE (CLR イメージのタイプの指定)
ms.date: 05/16/2019
f1_keywords:
- /CLRIMAGETYPE
- VC.Project.VCLinkerTool.CLRImageType
helpviewer_keywords:
- /CLRIMAGETYPE linker option
- -CLRIMAGETYPE linker option
ms.assetid: 04c60ee6-9dd7-4391-bc03-6926ad0fa116
ms.openlocfilehash: ee2e2ce359a4b877551adf9af71e0187b42cfd42
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837493"
---
# <a name="clrimagetype-specify-type-of-clr-image"></a>/CLRIMAGETYPE (CLR イメージのタイプの指定)

リンク イメージで CLR イメージ タイプを設定します。

## <a name="syntax"></a>構文

> **/CLRIMAGETYPE:** {**IJW**|**PURE**|**SAFE**|**SAFE32BITPREFERRED**}

## <a name="remarks"></a>解説

リンカーは、ネイティブ オブジェクトだけでなく、[/clr](clr-common-language-runtime-compilation.md) を使用してコンパイルされた MSIL オブジェクトも受け入れます。 **/clr:pure** および **/clr:safe** コンパイラ オプションは Visual Studio 2015 では非推奨になり、Visual Studio 2017 以降ではサポートされていません。 同じビルドに混在するオブジェクトを渡すと、生成される出力ファイルの検証可能性は、既定で入力モジュールの最低レベルの検証可能性と等しくなります。 たとえば、ネイティブ イメージと ( **/clr** を使用してコンパイルされた) 混合モード イメージを渡すと、結果のイメージは混合モード イメージになります。

**/CLRIMAGETYPE** を使用すると、必要に応じてより低い検証可能性を指定できます。

ファイルの CLR イメージのタイプを判断する方法については、「 [/CLRHEADER](clrheader.md)」を参照してください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成プロパティ]** ノードを展開します。

1. **[リンカー]** ノードを展開します。

1. **[詳細]** プロパティ ページを選択します。

1. **[CLR イメージ タイプ]** プロパティを変更します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRImageType%2A>

## <a name="see-also"></a>関連項目

- [MSVC リンカーのリファレンス](linking.md)
- [MSVC リンカー オプション](linker-options.md)
