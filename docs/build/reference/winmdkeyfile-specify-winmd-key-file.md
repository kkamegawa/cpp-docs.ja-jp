---
title: /WINMDKEYFILE (キー ファイルの指定)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKeyFile
ms.assetid: 65d88fdc-fff9-49ea-8cfc-b2f408741734
ms.openlocfilehash: 4b0c847bc5be6c73b78af4aa15b0074c712cc840
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316458"
---
# <a name="winmdkeyfile-specify-winmd-key-file"></a>/WINMDKEYFILE (キー ファイルの指定)

キーまたは Windows ランタイム メタデータ (.winmd) ファイルに署名するキーのペアを指定します。

```
/WINMDKEYFILE:filename
```

## <a name="remarks"></a>Remarks

似ています、 [/KEYFILE](keyfile-specify-key-or-key-pair-to-sign-an-assembly.md) .winmd ファイルに適用されるリンカー オプション。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**リンカー**フォルダー。

1. 選択、 **Windows メタデータ**プロパティ ページ。

1. **Windows メタデータ キー ファイル**ボックスに、ファイルの場所を入力します。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
