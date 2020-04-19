---
title: /WINMDKEYCONTAINER (キー コンテナーの指定)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 0b6cb42fc391d94634ae90e5a4cc17e69a14ff09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316516"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (キー コンテナーの指定)

Windows メタデータ (.winmd) ファイルに署名するキー コンテナーを指定します。

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Remarks

似ています、 [/KEYCONTAINER](keycontainer-specify-a-key-container-to-sign-an-assembly.md)リンカー オプション (.winmd) ファイルに適用されます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**リンカー**フォルダー。

1. 選択、 **Windows メタデータ**プロパティ ページ。

1. **Windows メタデータ キー コンテナー**ボックスに、場所を入力します。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
