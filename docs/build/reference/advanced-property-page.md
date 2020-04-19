---
title: '[詳細設定] プロパティページ (プロジェクト)'
ms.date: 07/19/2019
f1_keywords:
- VC.Project.VCConfiguration.VCToolsVersion
ms.description: Use the Advanced property page in Visual Studio 2019 to set various properties for C++ projects.
ms.openlocfilehash: fae3c76d4a62e3b0409664b3630ad76ab601c52b
ms.sourcegitcommit: 610751254a01cba6ad15fb1e1764ecb2e71f66bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/18/2019
ms.locfileid: "68315531"
---
# <a name="advanced-property-page"></a>[詳細設定] プロパティページ

[詳細設定] プロパティページは、Visual Studio 2019 以降で使用できます。

::: moniker range="vs-2019"

## <a name="advanced-properties"></a>高度なプロパティ

- **ターゲットファイル拡張子**

   ビルド出力に使用するファイル拡張子を指定します。 既定値は、アプリケーションの場合は **.exe** 、スタティックライブラリの場合は **.lib** 、dll の場合は **.dll**です。

- **消去時に削除する拡張子**

   **[ビルド]** メニューの **[消去]** を選択すると、プロジェクトの構成がビルドされる中間ディレクトリからファイルが削除されます。 このプロパティで指定された拡張子を持つファイルは、 **[消去]** の実行時またはリビルドの実行時に削除されます。 ビルド システムでは、中間ディレクトリでこれらの拡張子を持つファイルのほかに、置かれている場所に関係なく、(.obj ファイルなどの中間出力を含む) 既存のビルドの出力も削除します。 ワイルドカード文字を指定できます。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProjectEngine.VCConfiguration.DeleteExtensionsOnClean%2A>」を参照してください。

- **ビルド ログ ファイル**

   プロジェクトをビルドしたときに作成されるログ ファイルの既定の場所を変更できます。 既定の場所は、マクロ $(IntDir)$(MSBuildProjectName).log によって指定されます。

   プロジェクト マクロを使用して、ディレクトリの場所を変更できます。 「[ビルドコマンドとプロパティの一般的なマクロ](common-macros-for-build-commands-and-properties.md)」を参照してください。

- **推奨されるビルドツールのアーキテクチャ**

   X86 または x64 のビルドツールを使用するかどうかを指定します。

- **デバッグライブラリを使用する**

   デバッグビルドとリリースビルドのどちらを作成するかを指定します。

- **Unity (ジャンボ) ビルドを有効にする**

   ビルドのパフォーマンスを向上さC++せるために、コンパイル前に多数のソースファイルが1つ以上の "unity" ファイルに結合されるビルドプロセスを有効にします。 Unity ゲームエンジンに関連付けられていません。

- **MFC の使用法**

   MFC プロジェクトが MFC DLL に静的にリンクするか動的にリンクするかを指定します。 非 MFC プロジェクトでは **[標準 Windows ライブラリを使用する]** を選択して、MFC の使用時にさまざまな Win32 ライブラリにリンクできます。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.useOfMfc%2A>」を参照してください。

- **文字セット**

   _UNICODE または _MBCS を設定する必要があるかどうかを定義します。 該当する場合は、リンカーのエントリ ポイントにも影響します。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.CharacterSet%2A>」を参照してください。

- **プロジェクト全体の最適化**

   [/GL](gl-whole-program-optimization.md) コンパイラ オプションと [/LTCG](ltcg-link-time-code-generation.md) リンカー オプションを指定します。 既定では、これはデバッグ構成に対しては無効で、リテール構成では有効になっています。

- **MSVC ツールセットのバージョン**

   プロジェクトのビルドに使用される MSVC ツールセットの完全バージョンを指定します。 ツールセットのさまざまな更新バージョンとプレビューバージョンがインストールされている場合は、ここで使用するバージョンを指定できます。

## <a name="ccli-properties"></a>C++/CLI のプロパティ

- **共通言語ランタイム サポート**

   [/clr](clr-common-language-runtime-compilation.md) コンパイラ オプションが使用されます。

   プログラムを使用してこのプロパティにアクセスする方法については、「<xref:Microsoft.VisualStudio.VCProject.VCProjectConfigurationProperties.ManagedExtensions%2A>」を参照してください。

- **.NET Framework 対象バージョン**

   マネージド プロジェクトでは、ターゲットにする .NET Framework バージョンを指定します。

- **マネージド インクリメンタル ビルドを有効にする**

   マネージド プロジェクトの場合、これによりアセンブリの生成時に、外部からの可視性の検出が可能になります。 マネージド プロジェクトへの変更が他のプロジェクトから見えない場合、依存プロジェクトはリビルドされません。 これにより、マネージド プロジェクトを含むソリューションのビルド時間を大幅に短縮できます。

::: moniker-end
