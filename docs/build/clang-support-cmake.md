---
title: Visual Studio CMake プロジェクトでの clang/LLVM のサポート
ms.date: 07/01/2019
ms.description: Configure a CMake project in Visual Studio to use the Clang/LLVM toolchain.
helpviewer_keywords:
- Clang support for C++ CMake projects
ms.openlocfilehash: a71f9dc98f74247788558d1b7dccf3e117f43072
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416022"
---
# <a name="clangllvm-support-in-visual-studio-cmake-projects"></a>Visual Studio CMake プロジェクトでの clang/LLVM のサポート

::: moniker range="<=vs-2017"

Clang support は Visual Studio 2019 で利用できます。

::: moniker-end

::: moniker range="vs-2019"

Clang と共に Visual Studio を使用して、 C++ Windows または Linux を対象とする cmake プロジェクトを編集し、デバッグすることができます。

**Windows**: Visual Studio 2019 バージョン16.1 には、windows を対象とする cmake プロジェクトでの clang/llvm での編集、ビルド、およびデバッグのサポートが含まれています。

**Linux**: Linux cmake プロジェクトでは、特別な Visual Studio のサポートは必要ありません。 ディストリビューションのパッケージマネージャーを使用して Clang をインストールし、CMakeLists .txt ファイルに適切なコマンドを追加することができます。

## <a name="install"></a>インストール

Visual Studio で最適な IDE サポートを利用するには、最新の Clang compiler tools for Windows を使用することをお勧めします。 まだインストールしていない場合は、Visual Studio インストーラーを開いて、[デスクトップ開発] の [オプションコンポーネント**を使用したC++**   **C++ Windows 用 clang compiler** ] を選択してインストールできます。 カスタム clang のインストールを使用する場合は、  **C++ v142 build tools の clang-cl**のコンポーネントを確認してください。

![Clang コンポーネントのインストール](media/clang-install-vs2019.png)

## <a name="create-a-new-configuration"></a>新しい構成を作成する

新しい Clang 構成を CMake プロジェクトに追加するには、次のようにします。

1. **ソリューションエクスプローラー**で CMakeLists を右クリックし、 **[プロジェクトの cmake の設定]** を選択します。

1. **[構成]** で、 **[構成の追加]** ボタンを押します。

   ![構成の追加](media/cmake-add-config-icon.png)

1. 目的の Clang 構成を選択します (Windows および Linux 用に個別の Clang 構成が用意されていることに注意してください)。その後、 **[選択]** を押します。

   ![CMake Clang 構成](media/cmake-clang-configuration.png)

1. この構成を変更するには、 **Cmake 設定エディター**を使用します。 詳細については、「 [Visual Studio で CMake ビルド設定をカスタマイズ](customize-cmake-settings.md)する」を参照してください。

## <a name="modify-an-existing-configuration-to-use-clang"></a>Clang を使用するように既存の構成を変更する

Clang を使用するように既存の構成を変更するには、次の手順を実行します。

1. **ソリューションエクスプローラー**で CMakeLists を右クリックし、 **[プロジェクトの cmake の設定]** を選択します。

1. **[全般]** で、 **[ツールセット]** ドロップダウンを選択し、目的の clang ツールセットを選択します。

   ![CMake Clang ツールセット](media/cmake-clang-toolset.png)

## <a name="custom-clang-locations"></a>カスタム Clang の場所

既定では、Visual Studio は次の2つの場所で Clang を検索します。

- ウィンドウVisual Studio インストーラーに付属する Clang/LLVM の内部でインストールされたコピー。
- (Windows および Linux)PATH 環境変数。

**Cmake の設定**で**CMAKE_C_COMPILER**と**CMAKE_CXX_COMPILER** cmake 変数を設定することによって、別の場所を指定できます。

![CMake Clang ツールセット](media/clang-location-cmake.png)

## <a name="clang-compatibility-modes"></a>Clang 互換モード

Windows 構成の場合、既定では、CMake は clang [-cl](https://llvm.org/devmtg/2014-04/PDFs/Talks/clang-cl.pdf)モードで clang を呼び出し、標準ライブラリの Microsoft 実装によるリンクを呼び出します。 既定では、 **clang-cl**は `C:\Program Files (x86)\Microsoft Visual Studio\2019\Common7\IDE\CommonExtensions\Microsoft\Llvm\bin`にあります。

Cmake の**変数とキャッシュ**の **[Cmake の設定]** でこれらの値を変更できます。 [**詳細変数の表示] を**クリックします。 下にスクロールして**CMAKE_CXX_COMPILER**を見つけ、 **[参照]** ボタンをクリックして別のコンパイラパスを指定します。

## <a name="edit-build-and-debug"></a>編集、ビルド、およびデバッグ

Clang 構成を設定したら、プロジェクトをビルドしてデバッグすることができます。 Visual Studio は、Clang コンパイラを使用していることを検出し、IntelliSense、強調表示、ナビゲーション、およびその他の編集機能を提供します。 **出力ウィンドウ**にエラーと警告が表示されます。

デバッグ時には、ブレークポイント、メモリとデータの視覚化、およびその他のほとんどのデバッグ機能を使用できます。 エディットコンティニュなどの一部のコンパイラ依存機能は、Clang 構成では使用できません。

![CMake Clang デバッグ](media/clang-debug-visualize.png)

::: moniker-end
