---
title: Visual Studio プロジェクトでの Clang/LLVM のサポート
ms.date: 08/30/2019
ms.description: Configure a Visual Studio MSBuild project to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ MSBuild projects
ms.openlocfilehash: 819f96bf2fd949f80ae72ca878ba7eb9cb1bffcc
ms.sourcegitcommit: c3283062ce4e382aec7f11626d358a37caf8cdbb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/13/2020
ms.locfileid: "75914363"
---
# <a name="clangllvm-support-in-visual-studio-projects"></a>Visual Studio プロジェクトでの Clang/LLVM のサポート

::: moniker range="<=vs-2017"

CMake プロジェクトと MSBuild プロジェクトの両方の Clang サポートは、Visual Studio 2019 で利用できます。

::: moniker-end

::: moniker range="vs-2019"

Clang と共に Visual Studio 2019 バージョン16.2 を使用して、Windows またはC++ Linux を対象とする Visual Studio プロジェクト (MSBuild) を編集、ビルド、デバッグすることができます。

## <a name="install"></a>のインストール

Visual Studio で最適な IDE サポートを利用するには、最新の Clang compiler tools for Windows を使用することをお勧めします。 これらのツールをまだ持っていない場合は、Visual Studio インストーラーを開き、[デスクトップ開発] の [オプションコンポーネント**を使用C++** して **C++ Clang tools for Windows** ] を選択してインストールできます。 コンピューターで既存の Clang インストールを使用する場合は、  **C++ v142 build tools の clang-cl を選択します。** 省略可能なコンポーネント。 Microsoft C++標準ライブラリには、現在、Clang 8.0.0; 以降が必要です。Clang のバンドル版は、標準ライブラリの Microsoft の実装で更新プログラムを最新の状態に維持するために自動的に更新されます。 

![Clang コンポーネントのインストール](media/clang-install-vs2019.png)

## <a name="configure-a-windows-project-to-use-clang-tools"></a>Clang tools を使用するように Windows プロジェクトを構成する

Clang を使用するように Visual Studio プロジェクトを構成するには、**ソリューションエクスプローラー**でプロジェクトノードを右クリックし、 **[プロパティ]** を選択します。 通常は、ダイアログの上部にある **[すべての構成]** を選択する必要があります。 次に、[**全般** > **プラットフォームツールセット**] で、 **[llvm (clang-cl)]** を選択し、[ **OK]** をクリックします。

![Clang コンポーネントのインストール](media/clang-msbuild-prop-page.png)

Visual Studio にバンドルされている Clang ツールを使用している場合は、追加の手順は必要ありません。 Windows プロジェクトの場合、既定では、Visual Studio は clang [-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)モードで clang を呼び出し、標準ライブラリの Microsoft 実装によるリンクを呼び出します。 既定では、 **clang-cl**は `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`にあります。

カスタム Clang インストールを使用している場合は、**プロジェクト** > **プロパティ** > の [**VC++ ディレクトリ** > ]**構成プロパティ** > [**実行可能ファイル] を変更できます。** カスタム Clang インストールルートをそこに最初のディレクトリとして追加するか、 `LLVMInstallDir`プロパティの値を変更することによって、ディレクトリを指定します。 詳細について[は、「カスタム LLVM の場所の設定](#custom_llvm_location)」を参照してください。

## <a name="configure-a-linux-project-to-use-clang-tools"></a>Clang tools を使用するように Linux プロジェクトを構成する

Linux プロジェクトの場合、Visual Studio では Clang GCC と互換性のあるフロントエンドが使用されます。 プロジェクトプロパティとほぼすべてのコンパイラフラグは同じです

Clang を使用するように Visual Studio Linux プロジェクトを構成するには

1. **ソリューションエクスプローラー**でプロジェクトノードを右クリックし、 **[プロパティ]** を選択します。 
1. 通常は、ダイアログの上部にある **[すべての構成]** を選択する必要があります。 
1. Windows Subsystem for Linux を使用している場合は、[**全般**>**プラットフォームツールセット**] で**WSL_Clang_1_0**を選択します。または、リモートコンピューターまたは VM を使用している場合は**Remote_Clang_1_0**します。
1. **[OK]** を押します。

![Clang コンポーネントのインストール](media/clang-msbuild-prop-page.png)

Linux では、Visual Studio は既定で PATH 環境プロパティで検出された最初の Clang の場所を使用します。 カスタムの`LLVMInstallDir` Clang インストールを使用している場合は、プロパティの値を変更するか、または**プロジェクト** > の**プロパティ** > **VC++ ディレクトリ** >  **の下のパスを置き換える必要があります。構成プロパティ** > の**実行可能なディレクトリ**。 詳細について[は、「カスタム LLVM の場所の設定](#custom_llvm_location)」を参照してください。

## <a name="custom_llvm_location"></a>カスタム LLVM の場所を設定する

1つ以上のプロジェクトに対して LLVM のカスタムパスを設定するには、*ディレクトリ*を作成し、そのファイルをプロジェクトのルートフォルダーに追加します。 これをルートソリューションフォルダーに追加して、ソリューション内のすべてのプロジェクトに適用できます。 ファイルは次のようになります (ただし実際のパスに置き換えてください)。

```xml
<Project>
  <PropertyGroup>
    <LLVMInstallDir>c:\MyLLVMRootDir</LLVMInstallDir>
  </PropertyGroup>
</Project>
```

## <a name="set-additional-properties-edit-build-and-debug"></a>追加のプロパティの設定、編集、ビルド、およびデバッグ

Clang 構成を設定したら、プロジェクトノードでもう一度右クリックし、[プロジェクトの**再読み込み**] をクリックします。 これで、Clang ツールを使用してプロジェクトをビルドおよびデバッグできるようになりました。 Visual Studio は、Clang コンパイラを使用していることを検出し、IntelliSense、強調表示、ナビゲーション、およびその他の編集機能を提供します。 **出力ウィンドウ**にエラーと警告が表示されます。 Clang 構成のプロジェクトプロパティページは、MSVC の場合と非常によく似ていますが、Clang 構成では、エディットコンティニュなどの一部のコンパイラに依存する機能は使用できません。 プロパティページで使用できない clang コンパイラまたはリンカーオプションを設定するには、 **[構成プロパティ]** の下にある [プロパティ ページの [ > **CC++ /(またはリンカー)** ] > **コマンドライン** > **追加のオプション**] を選択します。

デバッグ時には、ブレークポイント、メモリとデータの視覚化、およびその他のほとんどのデバッグ機能を使用できます。  

![Clang デバッグ](media/clang-debug-msbuild.png)

::: moniker-end
