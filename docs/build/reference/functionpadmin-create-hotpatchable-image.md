---
title: /FUNCTIONPADMIN (ホットパッチ可能なイメージの作成)
ms.date: 03/09/2018
f1_keywords:
- /functionpadmin
helpviewer_keywords:
- -FUNCTIONPADMIN linker option
- /FUNCTIONPADMIN linker option
ms.assetid: 25b02c13-1add-4fbd-add9-fcb30eb2cae7
ms.openlocfilehash: 699da3cea9914b5a10bdf769015d41c33936a902
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292396"
---
# <a name="functionpadmin-create-hotpatchable-image"></a>/FUNCTIONPADMIN (ホットパッチ可能なイメージの作成)

ホットパッチ用のイメージを準備します。

## <a name="syntax"></a>構文

> **/FUNCTIONPADMIN**[**:**_space_]

### <a name="arguments"></a>引数

*space*<br/>
(バイト単位) の各関数の先頭に追加するパディングの量。 X86 上でこの既定値は 5 バイトの埋め込みと x64 の既定値は 6 バイト。 他のターゲットに値を指定する必要があります。

## <a name="remarks"></a>Remarks

ホットパッチ可能なイメージを生成するために、リンカーのためには、.obj ファイルする必要がありますでコンパイルされている[/hotpatch (ホットパッチ可能なイメージの作成)](hotpatch-create-hotpatchable-image.md)します。

コンパイルして、cl.exe の 1 つの呼び出しを使用してイメージをリンクするときに **/hotpatch**意味 **/functionpadmin**します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. 入力、 **/FUNCTIONPADMIN**オプション**追加オプション**します。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
