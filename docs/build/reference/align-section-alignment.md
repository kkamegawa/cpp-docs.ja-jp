---
title: /ALIGN (セクションの配置)
ms.date: 12/29/2017
f1_keywords:
- VC.Project.VCLinkerTool.Alignment
- /align
helpviewer_keywords:
- sections, specifying alignment
- ALIGN linker option
- /ALIGN linker option
- -ALIGN linker option
- section alignment
- sections
ms.openlocfilehash: d8d2e6a859c68af473d49dc04b76f0a15056aa56
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295267"
---
# <a name="align-section-alignment"></a>/ALIGN (セクションの配置)

## <a name="syntax"></a>構文

> **/ALIGN**[**:**_number_]

### <a name="arguments"></a>引数

*number*<br/>
配置の値 (バイト単位)。

## <a name="remarks"></a>Remarks

**/Align**オプションは、プログラムのリニア アドレス空間内の各セクションの配置を指定します。 *数*引数をバイト単位で、2 の累乗である必要があります。 既定では 4 K (4096 です)。 配置が無効なイメージを生成した場合、リンカーは警告を発行します。

デバイス ドライバーなどのアプリケーションを作成していない場合は、配置を変更する必要ありません。

配置パラメーターを特定のセクションのアラインメントを変更することは、 [/section](section-specify-section-attributes.md)オプション。

配置の値を指定するは、最大のセクションの配置より小さくすることはできません。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. オプションを入力して、**追加オプション**ボックス。 選択**OK**または**適用**して変更を適用します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
