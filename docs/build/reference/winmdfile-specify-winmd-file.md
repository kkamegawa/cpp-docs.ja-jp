---
title: /WINMDFILE (winmd ファイルの指定)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.GenerateWindowsMetadataFile
ms.assetid: 062b41b3-14d6-432c-a361-fdb66e918931
ms.openlocfilehash: 5d24d1d1aad8442f549dcb1aa4bd6414070c282c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316484"
---
# <a name="winmdfile-specify-winmd-file"></a>/WINMDFILE (winmd ファイルの指定)

によって生成される Windows ランタイム メタデータ (.winmd) 出力ファイルのファイル名を指定します、 [/WINMD](winmd-generate-windows-metadata.md)リンカー オプション。

```
/WINMDFILE:filename
```

## <a name="remarks"></a>Remarks

指定されている値を使用して`filename`既定の .winmd ファイル名を上書きする (`binaryname`.winmd)。 ".Winmd"を追加しないことに注意してください。`filename`します。  複数の値が表示されている場合、 **/WINMDFILE**コマンドライン、最後の 1 つが優先されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**リンカー**フォルダー。

1. 選択、 **Windows メタデータ**プロパティ ページ。

1. **Windows メタデータ ファイル**ボックスに、ファイルの場所を入力します。

## <a name="see-also"></a>関連項目

[/WINMD (Windows メタデータの生成)](winmd-generate-windows-metadata.md)<br/>
[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
