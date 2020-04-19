---
title: Windows C++プロジェクトプロパティページリファレンス-Visual Studio
ms.date: 08/28/2019
helpviewer_keywords:
- project-file macro
- project properties [C++], default values
- user-defined values
- project properties [C++], setting
- macros, project-file
- property pages, project settings
- C++ projects, properties
- build macro
- user-defined macros
ms.assetid: 13ffe3ea-1bc3-4bee-be5e-053a8a99cce4
ms.openlocfilehash: c9fd4fc00e86e0660972fc0bd37b66b2fea02ee0
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177466"
---
# <a name="windows-c-project-property-page-reference"></a>Windows C++プロジェクトプロパティページリファレンス

Visual Studio では、プロジェクトのプロパティページを使用して、コンパイラオプション、リンカーオプション、ファイルパス、およびその他のビルド設定を指定します。 使用できるプロパティおよびプロパティページは、プロジェクトの種類によって異なります。 たとえば、メイクファイルプロジェクトには、MFC または Win32 コンソールプロジェクトに存在しない NMake プロパティページがあります。 **プロパティページ**を開くには、メインメニューから [**プロジェクト** > の**プロパティ**] を選択するか、**ソリューションエクスプローラー**でプロジェクトノードを右クリックして **[プロパティ]** を選択します。 個々のファイルには、そのファイルに対してのみコンパイルオプションとビルドオプションを設定できるプロパティページもあります。 次の図は、MFC プロジェクトのプロパティページを示しています。

![プロジェクトのC++プロパティページ](media/example-prop-page.png)

このセクションでは、プロパティページ自体のクイックリファレンスを示します。 プロパティページに表示されるオプションと設定は、独自のトピックで詳細に説明されており、プロパティページのトピックからリンクされています。 プロジェクトのプロパティの詳細については、「 [Visual Studio でのコンパイラとビルドのプロパティの設定C++ ](../working-with-project-properties.md)」を参照してください。

Linux プロジェクトのプロパティページについては、「 [linux C++プロパティページリファレンス](../../linux/prop-pages-linux.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

- [[全般] プロパティ ページ (プロジェクト)](general-property-page-project.md)
- [[全般] プロパティ ページ (ファイル)](general-property-page-file.md)
- [[詳細設定] プロパティページ](advanced-property-page.md)
- [[VC++ ディレクトリ] プロパティ ページ](vcpp-directories-property-page.md)
- [[リンカー] プロパティ ページ](linker-property-pages.md)
- [[マニフェスト ツール] プロパティ ページ](manifest-tool-property-pages.md)
- [[HLSL] プロパティ ページ](hlsl-property-pages.md)
- [[コマンド ライン] プロパティ ページ](command-line-property-pages.md)
- [[カスタム ビルド ステップ] プロパティ ページ: 全般](custom-build-step-property-page-general.md)
- [参照の追加](../adding-references-in-visual-cpp-projects.md)
- [[マネージド リソース] プロパティ ページ](managed-resources-property-page.md)
- [[MIDL] プロパティ ページ](midl-property-pages.md)
- [NMake プロパティ ページ](nmake-property-page.md)
- [[リソース] プロパティ ページ](resources-property-pages.md)
- [[Web 参照] プロパティ ページ](web-references-property-page.md)
- [[XML データ ジェネレーター ツール] プロパティ ページ](xml-data-generator-tool-property-page.md)
- [[XML ドキュメント ジェネレーター] プロパティ ページ](xml-document-generator-tool-property-pages.md)

## <a name="see-also"></a>関連項目

[方法: プロジェクトの依存関係を作成および削除する](/visualstudio/ide/how-to-create-and-remove-project-dependencies)<br/>
[方法: 構成を作成および編集する](/visualstudio/ide/how-to-create-and-edit-configurations)<br/>
[Linux C++プロパティページリファレンス](../../linux/prop-pages-linux.md)
