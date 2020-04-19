---
title: /VERSION (バージョン情報)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.Version
- /version
helpviewer_keywords:
- -VERSION linker option
- Version Information linker option
- version numbers, specifying in .exe
- /VERSION linker option
- VERSION linker option
ms.assetid: b86d0e86-dca6-4316-aee2-d863ccb9f223
ms.openlocfilehash: 626461fc7a9fc6dd7b6578e836733d154a66862a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316497"
---
# <a name="version-version-information"></a>/VERSION (バージョン情報)

```
/VERSION:major[.minor]
```

## <a name="arguments"></a>引数

*主要な*と*マイナー*<br/>
.Exe または .dll ファイルのヘッダーに必要なバージョン番号です。

## <a name="remarks"></a>Remarks

/VERSION オプションを使用すると、リンカーは、.exe または .dll ファイルのヘッダーにバージョン番号を配置します。 DUMPBIN を使用して、 [/HEADERS](headers.md) /VERSION の効果を確認する省略可能なヘッダー値のイメージ バージョン フィールドを表示します。

*メジャー*と*マイナー*引数が 0 ~ 65,535 の範囲の 10 進数。 既定ではバージョン 0.0 です。

/VERSION で指定された情報は、エクスプ ローラーでそのプロパティを表示するときに、アプリケーションに表示されるバージョン情報には影響しません。 バージョン情報は、アプリケーションのビルドに使用されるリソース ファイルから取得されます。 参照してください[バージョン情報エディター](../../windows/version-information-editor.md)詳細についてはします。

バージョン番号を挿入する別の方法は、[バージョン](version-c-cpp.md)モジュール定義ステートメント。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. をクリックして、**リンカー**フォルダー。

1. をクリックして、**全般**プロパティ ページ。

1. 変更、**バージョン**プロパティ。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Version%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
