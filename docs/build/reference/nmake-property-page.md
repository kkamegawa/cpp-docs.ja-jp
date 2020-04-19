---
title: NMake プロパティ ページ (Windows C++)| Microsoft Docs
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCNMakeTool.ReBuildCommandLine
- VC.Project.VCNMakeTool.CleanCommandLine
- VC.Project.VCNMakeTool.Output
- VC.Project.VCNMakeTool.BuildCommandLine
helpviewer_keywords:
- NMake property page
ms.assetid: bd20cb52-9f1d-4240-b4fc-4f43205ac94b
ms.openlocfilehash: c0dbe537635fe6698f814f3d8456f0caa9c8c796
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320605"
---
# <a name="nmake-property-page"></a>NMake プロパティ ページ

**[NMake]** プロパティ ページでは、NMake プロジェクトのビルド設定を指定できます。 (NMAKE の Microsoft による実装は、[ように](https://wikipedia.org/wiki/Make_(software)))。

NMake プロジェクトの詳細については、「[Creating a Makefile Project](creating-a-makefile-project.md)」 (メイクファイル プロジェクトの作成) を参照してください。 Windows 以外のメイクファイル プロジェクトでは、次を参照してください[メイクファイル プロジェクトのプロパティ (Linux c)](../../linux/prop-pages/makefile-linux.md)、[一般的なプロジェクト プロパティ (Android c メイクファイル)](/visualstudio/cross-platform/general-makefile-android-prop-page)または[NMake のプロパティ (Android c)](/visualstudio/cross-platform/nmake-android-prop-page).

**[NMake]** プロパティ ページには、以下のプロパティがあります。

## <a name="uielement-list"></a>UIElement の一覧

- **ビルド コマンド ライン**

   **[ビルド]** が **[ビルド]** メニューでクリックされたときに実行されるコマンドを指定します。

- **すべてリビルド コマンド ライン**

   **[すべてリビルド]** が **[ビルド]** メニューでクリックされたときに実行されるコマンドを指定します。

- **クリーン コマンド ライン**

   **[クリーン]** が **[ビルド]** メニューでクリックされたときに実行されるコマンドを指定します。

- **出力**

   コマンド ラインの出力が含まれるファイルの名前を指定します。 既定では、このファイル名はプロジェクト名に基づきます。

- **プリプロセッサの定義**

   ソース ファイルを使用する任意のプリプロセッサの定義を指定します。 既定値は、現在のプラットフォームと構成によって決定されます。

- **インクルードの検索パス**

   コンパイラでインクルード ファイルを検索するディレクトリを指定します。

- **強制インクルード**

   プロジェクト ファイルに含まれない場合でも、プリプロセッサによって自動的に処理されるファイルを指定します。

- **アセンブリの検索パス**

   .NET アセンブリを解決しようとするときに、.NET Framework で検索するディレクトリを指定します。

- **アセンブリの強制使用**

   .NET Framework で自動的に処理されるアセンブリを指定します。

- **その他のオプション**

   C++ ファイルを解析するときに使用する IntelliSense に対する追加のコンパイラ スイッチを指定します。

アクセスする方法については、 **NMake**プロパティ ページを参照してください[Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

このプロジェクトのメンバーにプログラムを使ってアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCNMakeTool>」を参照してください。

## <a name="see-also"></a>関連項目

[C++ プロジェクト プロパティ ページの参照](property-pages-visual-cpp.md)<br>
