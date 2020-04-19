---
title: /INCREMENTAL (インクリメンタル リンクを行う)
ms.date: 11/04/2016
f1_keywords:
- /incremental
- VC.Project.VCLinkerTool.LinkIncremental
helpviewer_keywords:
- /INCREMENTAL linker option
- -INCREMENTAL linker option
- INCREMENTAL linker option
- link incrementally option
- LINK tool [C++], options for full linking
- incremental linking
ms.assetid: 135656ff-94fa-4ad4-a613-22e1a2a5d16b
ms.openlocfilehash: 189affe57694a8369e9cf7ac98815cc5888b69aa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270013"
---
# <a name="incremental-link-incrementally"></a>/INCREMENTAL (インクリメンタル リンクを行う)

```
/INCREMENTAL[:NO]
```

## <a name="remarks"></a>Remarks

リンカーによる、インクリメンタル リンクの処理方法を制御します。

既定では、インクリメンタル リンクは実行されます。 既定で設定されたインクリメンタル リンクをオーバーライドするには、/INCREMENTAL:NO と指定します。

インクリメンタル リンクされた、プログラムは機能的には、非インクリメンタル リンクされているプログラムです。 ただし、以降のインクリメンタル リンク、インクリメンタル リンクされた実行可能ファイル、静的ライブラリ、またはダイナミック リンク ライブラリ ファイルの準備が完了するため。

- コードとデータの埋め込みのためには、非インクリメンタル リンクされたプログラムよりも大きいです。 余白は、ファイルを再作成せずに関数とデータのサイズを大きくようにリンカーを使用できます。

- ジャンプ サンクを使って、新しいアドレスに関数を再配置する場合があります。

   > [!NOTE]
   > 最終リリース ビルドに埋め込みやサンクが含まれていないことを確認するには、プログラムを非インクリメンタル リンクします。

既定の設定に関係なくインクリメンタル リンクを行うには、/INCREMENTAL と指定します。 このオプションを選択すると、リンカーは、インクリメンタル リンクができない場合は、警告を発行し、プログラムを非インクリメンタル リンクします。 一部のオプションや状況によっては、/INCREMENTAL がオーバーライドされる場合もあります。

大半のプログラムでは、インクリメンタル リンクができます。 ただし、変更箇所が大きすぎたり、インクリメンタル リンクと矛盾するオプションが指定されていると、実行できません。 フル リンクを実行するには、次のいずれかを行います。

- インクリメンタル リンクをオフ (/INCREMENTAL:NO) にする。

- /OPT:REF オプションを指定する。

- /OPT:ICF オプションを指定する。

- /OPT:LBR オプションを指定する。

- /ORDER オプションを指定する。

/INCREMENTAL が暗黙的に指定すると[/debug](debug-generate-debug-info.md)を指定します。

以下の場合もフル リンクが行われます。

- インクリメンタル ステータス (.ilk) ファイルが見つからない場合。 LINK では、以降のインクリメンタル リンク用に新しい .ilk ファイルを作成します。

- .ilk ファイルに対する書き込み権限がない場合。 (リンクを無視する .ilk ファイルとリンク非増分します。)

- 出力ファイル .exe または .dll が見つからない場合。

- .ilk、.exe、または .dll のタイムスタンプを変更した場合。

- LINK オプションを変更した場合。 ビルド間で LINK オプションを変更すると、ほとんどの場合、フル リンクが行われます。

- オブジェクト (.obj) ファイルを追加または省略した場合。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**リンカー**フォルダー。

1. **[全般]** プロパティ ページをクリックします。

1. 変更、**インクリメンタル リンクを有効にする**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.LinkIncremental%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
