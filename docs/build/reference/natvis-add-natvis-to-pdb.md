---
title: /NATVIS (PDB に Natvis を追加する)
ms.date: 08/10/2017
f1_keywords:
- /natvis
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- NATVIS linker option
- /NATVIS linker option
- -NATVIS linker option
- Add Natvis file to PDB
ms.assetid: 8747fc0c-701a-4796-bb4d-818ab4465cca
ms.openlocfilehash: e758a49b41a17d805b752947cd1944087c8ff852
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320618"
---
# <a name="natvis-add-natvis-to-pdb"></a>/NATVIS (PDB に Natvis を追加する)

> /NATVIS:*filename*

## <a name="parameters"></a>パラメーター

*ファイル名*<br/>
PDB ファイルに追加する Natvis ファイル。 Natvis ファイルの PDB にデバッガーの視覚化を埋め込みます。

## <a name="remarks"></a>Remarks

/NATVIS オプションには、Natvis ファイルで定義されているデバッガーの視覚化が埋め込まれる*filename* LINK によって生成される PDB ファイルにします。 これにより、デバッガーは .natvis ファイルとは無関係に視覚エフェクトを表示できます。 1 つ以上の Natvis ファイルを生成される PDB ファイルに埋め込むには、複数の/NATVIS オプションを使用できます。

使用して PDB ファイルが作成されていない場合、リンクが/NATVIS を無視する[/debug](debug-generate-debug-info.md)オプション。 .Natvis ファイルの作成と使用については、次を参照してください。 [Visual Studio デバッガーでネイティブ オブジェクトのカスタム ビューの作成](/visualstudio/debugger/create-custom-views-of-native-objects)です。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**コマンドライン**プロパティ ページで、**リンカー**フォルダー。

1. /NATVIS オプションを追加、**追加オプション**テキスト ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- このオプションでは、同等のプログラムはありません。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
