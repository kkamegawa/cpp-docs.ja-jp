---
title: VCBuild と MSBuild の比較
description: Visual studio C++ビルドシステムが、visual studio 2010 の VCBuild から MSBuild に変更されました。
ms.date: 10/25/2019
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
ms.openlocfilehash: afa9324d6074db72fd065cfa07c16349f86a615c
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626611"
---
# <a name="vcbuild-vs-msbuild-build-system-changes-in-visual-studio-2010"></a>VCBuild と MSBuild: Visual Studio 2010 でのビルドシステムの変更点

プロジェクトのC++ MSBuild システムは、Visual Studio 2010 で導入されました。 Visual Studio 2008 以前のリリースでは、VCBuild システムが使用されていました。 VCBuild に依存する特定のファイルの種類と概念は、MSBuild では存在しないか、異なる方法で表されます。 このドキュメントでは、現在のビルド システムにおける違いについて説明します。 Visual Studio 2008 プロジェクトを MSBuild に変換するには、Visual Studio 2010 を使用する必要があります。 プロジェクトを変換した後、最新バージョンの Visual Studio を使用して、現在の IDE およびコンパイラツールセットにアップグレードする必要があります。 Visual Studio 2010 の入手方法などの詳細については、 [Visual studio 2008 の手順](use-native-multi-targeting.md#instructions-for-visual-studio-2008)を参照してください。

以下のセクションでは、VCBuild から MSBuild への変更点をまとめます。 カスタムビルド規則または msbuild によって認識されないマクロがある場合は、「 [Visual C++ Studio プロジェクト](../build/creating-and-managing-visual-cpp-projects.md)」を参照して、これらの命令を msbuild システムに変換する方法を確認してください。 VCBuild から MSBuild への最初の変換は、中間の手順にすぎません。 プロジェクトファイルを完全に修正したり、エラーを発生させずにプログラムをコンパイルしたりする必要はありません。 Visual Studio 2010 を使用してプロジェクトを MSBuild 形式に変換するだけで、プロジェクトを最新バージョンの Visual Studio で使用できるようになります。

## <a name="vcproj-is-now-vcxproj"></a>.vcproj が .vcxproj になりました

プロジェクト ファイルには .vcproj というファイル名拡張子が使用されなくなりました。 Visual Studio 2010 では、Visual C++ Studio の以前のリリースで作成されたプロジェクトファイルが MSBuild 形式に自動的に変換されます。この形式では、プロジェクトファイルの .vcxproj 拡張子が使用されます。

## <a name="vsprops-is-now-props"></a>.vsprops が .props になりました

Visual Studio 2008 以前では、*プロジェクトプロパティシート*は、ファイル名拡張子が VSPROPS の XML ベースのファイルです。 プロジェクト プロパティ シートを利用すれば、コンパイラやリンカーなどのビルド ツールのスイッチを指定したり、ユーザー定義のマクロを作成したりできます。 MSBuild では、プロジェクトプロパティシートのファイル名拡張子は props です。

## <a name="custom-build-rules-and-rules-files"></a>カスタムビルド規則と規則ファイル

Visual Studio 2008 以前では、*規則ファイル*は、ファイル名拡張子が RULES の XML ベースのファイルです。 ルール ファイルを利用すれば、カスタム ビルド ルールを定義し、それを Visual Studio C++ プロジェクトのビルド プロセスに組み込むことができます。 カスタム ビルド ルールには 1 つまたは複数のファイル名拡張子を関連付けることができるため、このルールを利用すると、1 つまたは複数の出力ファイルを作成するツールに入力ファイルを渡すことができます。

MSBuild システムでは、カスタムビルド規則は、. rules ファイルではなく、.xml、props、および .targets の3種類のファイルで表されます。 以前のリリースの Visual C++ Studio を使用して作成された. rules ファイルが visual Studio 2010 に移行されると、同じ .xml、props、および .targets ファイルが作成され、元の rules ファイルと共にプロジェクトに格納されます。

> [!IMPORTANT]
> Visual Studio 2010 では、IDE は新しい規則の作成をサポートしていません。 そのため、以前のリリースの Visual C++ Studio を使用して作成されたプロジェクトのルールファイルを使用する最も簡単な方法は、プロジェクトを visual Studio 2010 に移行することです。

## <a name="inheritance-macros"></a>継承マクロ

Visual Studio 2008 以前では、 **$ (Inherit)** マクロは、プロジェクトのビルドシステムによって構成されるコマンドラインに継承されたプロパティを表示する順序を指定します。 **$(NoInherit)** マクロを使用すると、$(Inherit) が出現しても無視され、$(NoInherit) を使用しなければ継承されるプロパティがすべて継承されません。 たとえば、$(Inherit) マクロの既定では、[/I (Additional Include Directories)](../build/reference/i-additional-include-directories.md) コンパイラ オプションで指定されるファイルがコマンド ラインに追加されます。

Visual Studio 2010 では、1つ以上のリテラル値とプロパティマクロの連結としてプロパティの値を指定することで、継承がサポートされています。 **$(Inherit)** マクロと **$(NoInherit)** マクロはサポートされていません。

次の例では、プロパティ ページのプロパティにセミコロンで区切られた一覧が割り当てられています。 この一覧は *\<value>* リテラルと `MyProperty` プロパティの値を連結したもので構成されます。このプロパティは **$(** <em>MyProperty</em> **)** というマクロ表記でアクセスされます。

```
Property=<value>;$(MyProperty)
```

## <a name="vcxprojuser-files"></a>.vcxproj. ユーザーファイル

ユーザー ファイル (.vcxproj.user) によって、デバッグ設定やデプロイ設定など、ユーザー固有のプロパティが保管されます。 *.Vcxproj*ファイルは、特定のユーザーのすべてのプロジェクトに適用されます。

## <a name="vcxprojfilters-file"></a>.vcxproj. フィルターファイル

プロジェクトにファイルを追加するために**ソリューションエクスプローラー**を使用すると、ファイル名拡張子に基づいて、ファイルの追加先となる**ソリューションエクスプローラー**ツリービュー内の場所がフィルターファイル ( *.vcxproj. filters*) によって定義されます。

## <a name="vc-directories-settings"></a>VC + + ディレクトリの設定

Visual C++ ディレクトリ設定は [[VC++ ディレクトリ プロパティ ページ]](../ide/vcpp-directories-property-page.md) で指定されます。 Visual Studio 2008 以前では、ディレクトリ設定はユーザーごとに適用され、除外されたディレクトリの一覧は*sysincl*ファイルで指定されています。 

コマンド ラインで [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) を実行する場合、VC++ ディレクトリ設定を変更できません。 **[ツール]** メニューを開き、 **[設定のインポートとエクスポート]** をクリックし、 **[すべての設定をリセット]** オプションを選択した場合も設定を変更できません。

以前のリリースの Visual Studio で作成された *.vssettings*ファイルから VC + + ディレクトリ設定を移行するには、次の手順を実行します。

1. **[ツール]** メニューを開き、 **[設定のインポートとエクスポート]** をクリックします。
2. **[選択した環境設定のインポート]** を選択
3. ウィザードの指示に従います。

## <a name="see-also"></a>関連項目

[コマンド ラインでの MSBuild - C++](../build/msbuild-visual-cpp.md)
