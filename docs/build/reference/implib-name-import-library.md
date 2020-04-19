---
title: /IMPLIB (インポート ライブラリ名の設定)
ms.date: 11/04/2016
f1_keywords:
- /implib
- VC.Project.VCLinkerTool.ImportLIbrary
helpviewer_keywords:
- IMPLIB linker option
- /IMPLIB linker option
- -IMPLIB linker option
- import libraries, overriding default name
ms.assetid: fe8f71ab-7055-41b5-8ef8-2b97cfa4a432
ms.openlocfilehash: dc9a9220d55f7831a00f70ec155cc5b57a695818
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269987"
---
# <a name="implib-name-import-library"></a>/IMPLIB (インポート ライブラリ名の設定)

> /IMPLIB:*filename*

## <a name="parameters"></a>パラメーター

*ファイル名*<br/>
インポート ライブラリのユーザー指定の名前。 既定の名前が置き換えられます。

## <a name="remarks"></a>Remarks

/IMPLIB オプションには、エクスポートを含むプログラムをビルドするときにリンクが作成されるインポート ライブラリの既定の名前がオーバーライドされます。 既定の名前は、メイン出力ファイルと拡張機能の基本名から作成されます。 lib します。 プログラムには、次の 1 つ以上が指定されている場合、エクスポートが含まれます。

- [方式](../../cpp/dllexport-dllimport.md)ソース コード内のキーワード

- [エクスポート](exports.md).def ファイル内のステートメント

- [/Export](export-exports-a-function.md) LINK コマンド内の指定

リンクは、インポート ライブラリが作成されていない場合、/IMPLIB を無視します。 エクスポートが指定されていない場合、リンクは、インポート ライブラリを作成できません。 エクスポート ファイルをビルドに使用する場合、リンクでは、インポート ライブラリが既に存在し、作成されていないこと前提としています。 インポート ライブラリとエクスポート ファイルには、次を参照してください。 [LIB リファレンス](lib-reference.md)します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**詳細**プロパティ ページ。

1. 変更、**インポート ライブラリ**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ImportLibrary%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
