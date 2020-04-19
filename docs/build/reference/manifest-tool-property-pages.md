---
title: マニフェスト ツールのプロパティ ページ
ms.date: 07/24/2019
ms.topic: article
f1_keywords:
- VC.Project.VCManifestTool.SuppressStartupBanner
- VC.Project.VCManifestTool.VerboseOutput
- VC.Project.VCManifestTool.AssemblyIdentity
- VC.Project.VCManifestTool.AdditionalManifestFiles
- VC.Project.VCManifestTool.InputResourceManifests
- VC.Project.VCManifestTool.EmbedManifest
- VC.Project.VCManifestTool.OutputManifestFile
- VC.Project.VCManifestTool.ResourceOutputFileName
- VC.Project.VCManifestTool.GenerateCatalogFiles
- VC.Project.VCManifestTool.ManifestFromManagedAssembly
- VC.Project.VCManifestTool.SuppressDependencyElement
- VC.Project.VCManifestTool.GenerateCategoryTags
- VC.Project.VCManifestTool.EnableDPIAwareness
- VC.Project.VCManifestTool.TypeLibraryFile
- VC.Project.VCManifestTool.RegistrarScriptFile
- VC.Project.VCManifestTool.ComponentFileName
- VC.Project.VCManifestTool.ReplacementsFile
- VC.Project.VCManifestTool.UpdateFileHashes
- VC.Project.VCManifestTool.UpdateFileHashesSearchPath
- vc.project.AdditionalOptionsPage
ms.assetid: f33499c4-7733-42d9-80e3-8a5018786965
ms.openlocfilehash: d9b074667614da8d83fae7b00b49bf63c9390b69
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927679"
---
# <a name="manifest-tool-property-pages"></a>マニフェスト ツールのプロパティ ページ

これらのページを使用して、 [Mt](/windows/win32/sbscs/mt-exe)の全般オプションを指定します。 これらのページについては、「**プロジェクト** > **プロパティ** > の**構成プロパティ** > **マニフェストツール**」を参照してください。

## <a name="general-property-page"></a>[全般] プロパティページ

### <a name="suppress-startup-banner"></a>著作権情報の非表示

   **[はい (/nologo)]** の場合、マニフェスト ツールを起動したとき、Microsoft の標準的な著作権情報が隠されます。 ビルド プロセスの一部として、あるいはビルド環境から mt.exe を実行するとき、ログ ファイルに不要な出力を表示しない場合、このオプションを使用します。

### <a name="verbose-output"></a>詳細出力

   **[はい (/verbose)]** の場合、マニフェスト生成中、追加のビルド情報が表示されます。

### <a name="assembly-identity"></a>アセンブリ Id * *

[\<assemblyIdentity> 要素](/visualstudio/deployment/assemblyidentity-element-clickonce-application)の属性を ID 文字列を指定するには、/identity オプションを使用します。 ID 文字列は `name` 属性の値で始まり、後ろに*属性* = *値*のペアが続きます。 ID 文字列の属性はコンマで区切られます。

Id 文字列の例を次に示します。`Microsoft.Windows.Common-Controls, processorArchitecture=x86, version=6.0.0.0, type=win32, publicKeyToken=6595b64144ccf1df`

## <a name="input-and-output-property-page"></a>[入力および出力] プロパティページ     

###  <a name="additional-manifest-files"></a>追加のマニフェストファイル

**/manifest** オプションを使用して、マニフェスト ツールで処理またはマージされる追加のマニフェスト ファイルの完全パスを指定します。 完全パスはセミコロンで区切ります。 (-manifest [manifest1] [manifest2]...)

###  <a name="input-resource-manifests"></a>入力リソースマニフェスト

**/inputresource** オプションを使用して、マニフェスト ツールに入力される RT_MANIFEST 型のリソースの完全パスを指定します。 パスの後には、特定のリソース ID を続けることができます。 例えば:

`dll_with_manifest.dll;#1`

###  <a name="embed-manifest"></a>埋め込みマニフェスト

- **[はい]** を指定すると、プロジェクト システムによって、アプリケーション マニフェスト ファイルがアセンブリに埋め込まれます。

- **[いいえ]** を指定すると、プロジェクト システムによって、アプリケーション マニフェスト ファイルがスタンドアロン ファイルとして作成されます。

###  <a name="output-manifest-file"></a>出力マニフェストファイル

出力マニフェスト ファイルの名前を指定します。 マニフェスト ツールで操作されるマニフェスト ファイルが 1 つだけの場合、このプロパティは省略できます。 (-out: [ファイル]; # [リソース ID])

###  <a name="manifest-resource-file"></a>マニフェストリソースファイル

マニフェストをプロジェクト出力に埋め込むために使用する出力リソース ファイルを指定します。

###  <a name="generate-catalog-files"></a>カタログファイルの生成

**/makecdfs** オプションを使用して、カタログを作成するために使用されるカタログ定義ファイル (.cdf ファイル) をマニフェスト ツールで生成するように指定します。 /makecdfs

###  <a name="generate-manifest-from-managedassembly"></a>ManagedAssembly からマニフェストを生成します

マネージド アセンブリからマニフェストを生成します (-managedassemblyname: [ファイル])

###  <a name="suppress-dependency-element"></a>Dependency 要素の非表示

-Managedassembly と共に使用します。 最終的なマニフェストに依存関係要素の生成を抑制します。 (-nodependency)

###  <a name="generate-category-tags"></a>カテゴリタグを生成する

-Managedassembly と共に使用します。 -category を指定すると、カテゴリタグが生成されます。 (-category)

###  <a name="dpi-awareness"></a>DPI 認識

アプリケーションが DPI 対応かどうかを指定します。 既定では、この設定は MFC プロジェクトの場合は **[はい]** 、それ以外の場合は **[いいえ]** に指定されています。これは、MFC プロジェクトのみが DPI 認識でビルドされるためです。 別の DPI 設定を扱うコードを追加すると、この設定をオーバーライドして **[はい]** にすることができます。 DPI 対応ではないのに DPI 対応として設定すると、アプリケーションが不明瞭にまたは小さく見えることがあります。

**いずれ**

- **None**
- **高 DPI 対応**
- **モニターあたりの高 DPI 対応**

## <a name="isolated-com-property-page"></a>分離 COM プロパティページ

分離 COM の詳細については、「[分離アプリケーション](/windows/win32/SbsCs/isolated-applications)」と[「方法:COM コンポーネント](../how-to-build-isolated-applications-to-consume-com-components.md)を使用するための分離アプリケーションをビルドします。

###  <a name="type-library-file"></a>タイプライブラリファイル

Regfree 対し COM マニフェストのサポートに使用するタイプライブラリを指定します。 (-tlb: [ファイル])

###  <a name="registrar-script-file"></a>レジストラースクリプトファイル

Regfree 対し COM マニフェストサポートに使用するレジストラースクリプトファイルを指定します。 (-rgs: [ファイル])

###  <a name="component-file-name"></a>コンポーネントファイル名

指定された .tlb または .rgs から構築されたコンポーネントのファイル名を指定します。 (-dll: [ファイル])

###  <a name="replacements-file"></a>置換ファイル

RGS ファイル内の置換可能な文字列の値を含むファイルを指定します。 (置換: [ファイル])

## <a name="advanced-property-page"></a>[詳細設定] プロパティページ

###  <a name="update-file-hashes"></a>ファイルハッシュの更新

File 要素で指定されたファイルのハッシュを計算し、この値を使用して hash 属性を更新します。 (hashupdate: [パス])

###  <a name="update-file-hashes-search-path"></a>ファイルハッシュの更新の検索パス

ファイルハッシュの更新時に使用する検索パスを指定します。

###  <a name="additional-options"></a>追加オプション

追加オプション


## <a name="see-also"></a>関連項目

[C++プロジェクトプロパティページのリファレンス](property-pages-visual-cpp.md)
