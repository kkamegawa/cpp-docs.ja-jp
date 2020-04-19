---
title: UNIX ユーザー向けC++ Microsoft の概要
ms.date: 10/23/2019
helpviewer_keywords:
- UNIX [C++]
ms.assetid: 36108b31-e7fa-49a8-a1f7-7077fcbec873
ms.openlocfilehash: 791c513553acbd300204746ae1e1dddf7a3ae5c4
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627000"
---
# <a name="introduction-to-microsoft-c-for-unix-users"></a>UNIX ユーザー向けC++ Microsoft の概要

このトピックでは、Visual Studio を初めて使用し、コマンドラインまたは Visual Studio を使用してC++生産性を向上させる必要があるすべての種類の UNIX ユーザー向けの情報を提供します。 Microsoft C++コンパイラで Visual Studio を使用して、Windows を対象にすることができます。 また、リモート Linux マシン、MinGW-mingw-w64、Windows Subsystem for Linux などの UNIX 環境で、Visual Studio IDE を GCC または Clang と共に使用することもできます。 Visual Studio C++でを使用するには、ワークロード**を使用しC++たデスクトップ開発**がインストールされている必要があります。 Visual Studio インストーラーを開いて、ワークロードをインストールするか、オプションのコンポーネントを追加または削除します。 リモートの linux マシンを対象とする場合は、ワークロード**を使用しC++て linux 開発**をインストールすることもできます。 Android または iOS の開発には、ワークロードを**使用C++したモバイル開発**をインストールします。

## <a name="getting-started-on-the-command-line"></a>コマンドラインの概要

UNIX のコマンドライン環境C++を使用する場合と同様の方法で、コマンドラインから Microsoft コンパイラを使用できます。 コマンド ラインの C と C++ コンパイラ (CL.EXE)、リンカー (LINK.EXE)、Microsoft バージョンの UNIX make ユーティリティである NMAKE.EXE を含むその他のツールを使用して、コマンド プロンプトからコンパイルします。

UNIX では、コマンドは /usr/bin などの共通のフォルダーにインストールされます。 Visual Studio の場合、コマンドライン ツールは Visual Studio のインストール ディレクトリにインストールされます。VC\bin サブディレクトリとそのサブディレクトリです。 UNIX とは異なり、これらのツールは普通のコマンド プロンプト ウィンドウでは利用できません。 コマンドラインツールを使用するには、特別な開発者コマンドプロンプトを使用して、プログラムをコンパイルC++するために必要なパスとその他の環境変数を設定する必要があります。 詳細については、「[コマンドラインでの C/C++ コードのビルド](../build/building-on-the-command-line.md)」および「[チュートリアル: コマンド ラインでのネイティブ C++ プログラムのコンパイル](../build/walkthrough-compiling-a-native-cpp-program-on-the-command-line.md)」を参照してください。

## <a name="debugging-your-code"></a>コードのデバッグ

Visual Studio debugger for Microsoft C++プロジェクトは、コマンドラインから、または IDE 内から使用できます。 [/Z7、/zi、/zi (デバッグ情報の形式)](../build/reference/z7-zi-zi-debug-information-format.md)スイッチを使用してコンパイルし、ソースのステップ実行を有効にします。 詳細については、「[ネイティブ コードのデバッグ](/visualstudio/debugger/debugging-native-code)」および「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照してください。

GCC または Clang でコンパイルされたプログラムの場合、Visual Studio は GDB、LLDB、または指定した任意のカスタムデバッガーを呼び出します。

## <a name="visual-studio-project-system"></a>Visual Studio プロジェクトシステム

Visual Studio プロジェクトシステムは MSBuild と呼ばれます。 XML 形式でプロジェクトファイルを使用します。C++プロジェクトファイルの拡張子は .vcxproj です。 それぞれが別のセットのコンパイラ オプションや別の言語でビルドされている可能性がある複数のライブラリおよび実行可能ファイルから構成されるアプリケーションは、1 つの*ソリューション*の一部である複数のプロジェクトに格納されます。 ソリューションは、複数のプロジェクトをグループ化するためのコンテナーの抽象化です。 プロジェクトに関する情報は、拡張子が .prj のプロジェクト ファイルに格納されます。 詳細については、「[Visual Studio のソリューションおよびプロジェクト](/visualstudio/ide/solutions-and-projects-in-visual-studio)」および「[C++ デスクトップ開発のための Visual Studio IDE の使用](../ide/using-the-visual-studio-ide-for-cpp-desktop-development.md)」を参照してください。 メインメニューから、[**ファイル** > **新しい** > **プロジェクト**] を選択して、使用可能な Visual Studio プロジェクトテンプレートを表示します。

Visual Studio 2017 以降では、CMake プロジェクトのサポートが追加されました。また、任意C++のビルドシステムで Microsoft コンパイラを使用するためのオプション、またはソースファイルの圧縮されていないフォルダーとプロジェクトファイルを使用することもできません。 詳細については、「visual [studio での Cmake プロジェクト](../build/cmake-projects-in-visual-studio.md)」と「 [Visual studio でフォルダープロジェクトを開く](../build/open-folder-projects-cpp.md)」を参照してください。

## <a name="microsoft-specific-modifiers"></a>Microsoft 固有の修飾子

Microsoft C++ コンパイラでは、Windows オペレーティング システムのプログラミングをサポートする目的で、標準 C++ プログラミング言語にいくつかの拡張機能が実装されます。 これらの拡張機能は、ストレージ クラス属性、関数の呼び出し規約、ベース アドレス指定などを指定するために使用されます。 サポートされているすべての C++ の拡張機能の完全な一覧については、「[Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)」を参照してください。

`/Za` コンパイラ オプションを使用して、C++ へのすべての Microsoft 固有の拡張機能を無効にすることができます。 複数のプラットフォームで実行するコードを記述する場合、このオプションが推奨されます。 `/Za` コンパイラ オプションの詳細については、「[/Za、/Ze (言語拡張機能の無効化)](../build/reference/za-ze-disable-language-extensions.md)」を参照してください。 コンパイラ準拠の詳細については、「 [Microsoft C++言語準拠テーブル](../overview/visual-cpp-language-conformance.md)」および「[非標準動作](../cpp/nonstandard-behavior.md)」を参照してください。 C++

## <a name="precompiled-headers"></a>プリコンパイル済みヘッダー

Microsoft C および C++ コンパイラは、インライン コードを含む、C または C++ コードをプリコンパイルするためのオプションを提供します。 このパフォーマンス機能を使用して、安定したコードの本体をコンパイルし、ファイル内のコードのコンパイル済みの状態を格納します。さらに、後続のコンパイル中に、プリコンパイルされたコードと開発中のコードを結合できます。 安定したコードは再コンパイルする必要がないので、後続のコンパイルが高速化します。

既定では、プリコンパイル済みのコードはすべて、ファイル *pch.h* と *pch.cpp* (Visual Studio 2017 以前では *stdafx.h* と *stdafx.cpp*) 内で指定されます。 プリコンパイルされたヘッダーの詳細については、「[プリコンパイル済みヘッダー ファイルの作成](../build/creating-precompiled-header-files.md)」を参照してください。

## <a name="related-sections"></a>関連項目

詳細については、「 [Windows での Linux プログラムの実行](../porting/porting-from-unix-to-win32.md)」を参照してください。

## <a name="see-also"></a>関連項目

[プロジェクトおよびビルド システム](../build/projects-and-build-systems-cpp.md)
