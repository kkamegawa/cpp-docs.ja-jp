---
title: /WX (リンカー警告をエラーとして扱う)
ms.date: 11/04/2016
f1_keywords:
- /WX
helpviewer_keywords:
- /WX linker option
- -WX linker option
- WX linker option
ms.assetid: e4ba97c7-93f7-43ae-a4bb-d866790926c9
ms.openlocfilehash: b4b29ed364d39c5f105dded703b8530c08db35e6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316302"
---
# <a name="wx-treat-linker-warnings-as-errors"></a>/WX (リンカー警告をエラーとして扱う)

```
/WX[:NO]
```

## <a name="remarks"></a>Remarks

/WX には、リンカーが警告を生成する場合に生成される出力ファイルは行われません。

似ています **/WX**コンパイラ (を参照してください[/w、/W0、/W1、/W2、/W3、/W4、/w1、/w2、/w3、/w4、/Wall、/wd、//we、/wo、/Wv、/WX (警告レベル)](compiler-option-warning-level.md)詳細については)。 ただしを指定する **/WX**のコンパイルとは限りませんが **/WX**リンク フェーズが無効にも、明示的に指定する必要があります。 **/WX**ツールごとにします。

既定では、 **/WX**は無効です。 リンカー警告をエラーとして扱う、次のように指定します。 **/WX**します。 **/WX:NO**は指定しない場合と同じ **/WX**します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. オプションを入力、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
