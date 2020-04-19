---
title: Visual Studio での C/C++ プロジェクトとビルドシステム
ms.description: Use Visual Studio to compile and build C++ projects for Windows, ARM or Linux based on any project system.
ms.date: 07/17/2019
helpviewer_keywords:
- builds [C++]
- C++ projects, building
- projects [C++], building
- builds [C++], options
- C++, build options
ms.assetid: fa6ed4ff-334a-4d99-b5e2-a1f83d2b3008
ms.topic: overview
ms.openlocfilehash: 1548f82b62163600b5220c553bebcea72020abbc
ms.sourcegitcommit: 7750e4c291d56221c8893120c56a1fe6c9af60d6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274739"
---
# <a name="cc-projects-and-build-systems-in-visual-studio"></a>Visual Studio での C/C++ プロジェクトとビルドシステム

Visual Studio を使用して、IntelliSense を完全にサポートC++するコードベースを編集、コンパイル、ビルドすることができます。そのコードを Visual Studio プロジェクトに変換したり、MSVC ツールセットを使用してコンパイルしたりする必要はありません。 たとえば、Windows コンピューター上の Visual Studio でクロスプラットフォームの CMake プロジェクトを編集し、リモートの Linux コンピューターで g + + を使用して Linux 用にコンパイルできます。

## <a name="c-compilation"></a>C++コンパイル

プログラムをC++ビルドするには、1つまたは複数のファイルからソースコードをコンパイルしてから、それらのファイルを実行可能ファイル (.exe)、動的読み込みライブラリ (.dll)、またはスタティックライブラリ (.lib) にリンクします。 

基本C++コンパイルには、次の3つの主要な手順が含まれます。



- C++コンパイラは、各翻訳単位をオブジェクトファイル (.obj) にコンパイルし、設定されているすべてのコンパイラオプションを適用します。


- *リンカー*は、設定されているリンカーオプションを適用して、オブジェクトファイルを1つの実行可能ファイルにマージします。 

## <a name="the-msvc-toolset"></a>MSVC ツールセット

Microsoft C++コンパイラ、リンカー、標準ライブラリ、および関連ユーティリティは、MSVC コンパイラツールセット ("ツールチェーン" または "ビルドツール" とも呼ばれます) を構成します。 これらは Visual Studio に含まれています。 また、ツールセットをダウンロードして、 [Build Tools For Visual Studio 2019 のダウンロード場所](https://visualstudio.microsoft.com/downloads/#build-tools-for-visual-studio-2019)から無料のスタンドアロンパッケージとして使用することもできます。

コマンドラインから直接 MSVC compiler (cl.exe) を呼び出すことによって、単純なプログラムをビルドできます。 次のコマンドは、1つのソースコードファイルを受け入れ、cl.exe を呼び出して、 *hello .exe*という名前の実行可能ファイルをビルドします。 

```cmd
cl /EHsc hello.cpp
```
ここで、コンパイラ (cl.exe) によってC++プリプロセッサとリンカーが自動的に呼び出され、最終的な出力ファイルが生成されることに注意してください。  詳細については、「[コマンドラインでのビルド](building-on-the-command-line.md)」を参照してください。

## <a name="build-systems-and-projects"></a>ビルドシステムとプロジェクト

ほとんどの実際のプログラムでは、複数の構成 (デバッグとリリース)、複数のプラットフォーム (x86、x64、ARM など) 、特定の順序でコンパイルする必要がある実行可能ファイルの為にいくつかの*ビルドシステム*を使用して複数のソースファイルをコンパイルする複雑な作業を管理します。あなたが設定したビルド構成ファイルを、ビルドシステムはコンパイラを呼び出す前に入力として受け入れます。 実行可能ファイルをビルドするために必要なソースコードファイルとビルド構成ファイルのセットは、"*プロジェクト*" と呼ばれます。 

次の一覧は、Visual Studio プロジェクトのさまざまなC++オプションを示しています。

- Visual Studio IDE を使用して Visual Studio プロジェクトを作成し、プロパティページを使用して構成します。 Visual Studio プロジェクトでは、Windows 上で実行されるプログラムが生成されます。 概要については、Visual Studio ドキュメントの「[コンパイルとビルド](/visualstudio/ide/compiling-and-building-in-visual-studio)」を参照してください。

- CMakeLists .txt ファイルが含まれているフォルダーを開きます。 CMake のサポートは、Visual Studio に統合されています。 IDE を使用して、CMake ファイルを変更せずに編集、テスト、およびデバッグを行うことができます。 これにより、異なるエディターを使用している可能性のある他のユーザーと同じ CMake プロジェクトで作業することができます。 CMake は、クロスプラットフォームの開発に推奨されるアプローチです。 詳細については、「 [CMake プロジェクト](cmake-projects-in-visual-studio.md)」を参照してください。
 
- プロジェクトファイルのない、ソースファイルの圧縮されていないフォルダーを開きます。 Visual Studio では、ヒューリスティックを使用してファイルをビルドします。 これは、小さなコンソールアプリケーションをコンパイルして実行する簡単な方法です。 詳細については、「[フォルダープロジェクトを開く](open-folder-projects-cpp.md)」を参照してください。

- メイクファイルまたはその他のビルドシステム構成ファイルが含まれているフォルダーを開きます。 JSON ファイルをフォルダーに追加することで、任意のビルドコマンドを呼び出すように Visual Studio を構成できます。 詳細については、「[フォルダープロジェクトを開く](open-folder-projects-cpp.md)」を参照してください。
 
- Visual Studio で Windows メイクファイルを開きます。 詳細については、「 [NMAKE リファレンス](reference/nmake-reference.md)」を参照してください。

## <a name="msbuild-from-the-command-line"></a>コマンドラインからの MSBuild 

コマンドラインオプションと共に .vcxproj ファイルを渡すことによって、コマンドラインから MSBuild を呼び出すことができます。 この方法では、MSBuild について十分に理解する必要があり、必要な場合にのみ推奨されます。 詳細については、「[MSBuild](msbuild-visual-cpp.md)」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

[Visual Studio プロジェクト](creating-and-managing-visual-cpp-projects.md) Visual Studio でネイティブビルドシステム (MSBuild) を使用して C++ プロジェクトを作成、構成、およびビルドする方法。

[CMake プロジェクト](cmake-projects-in-visual-studio.md)Visual Studio で CMake プロジェクトをコーディング、ビルド、および配置する方法について説明します。

[フォルダープロジェクトを開く](open-folder-projects-cpp.md) Visual Studio を使用して、任意のビルドシステムに基づいたあるいはビルドシステムのない C++ プロジェクトのコーディング、ビルド、配置を行う方法。 

[リリースビルド](release-builds.md)エンドユーザーにデプロイするために最適化されたリリースビルドを作成およびトラブルシューティングする方法。

[コマンド ラインから MSVC ツールセットを使用する](building-on-the-command-line.md)<br/>
Visual Studio IDE を使用するのではなく、コマンドラインから直接 C/C++ コンパイラおよびビルドツールを使用する方法について説明します。

[Visual Studio での dll のビルド](dlls-in-visual-cpp.md)Visual Studio で C/C++ dll (共有ライブラリ) を作成、デバッグ、および配置する方法について説明します。

[チュートリアル: スタティックライブラリ](walkthrough-creating-and-using-a-static-library-cpp.md)の作成と使用 .lib バイナリファイルの作成方法。

[CC++ /分離アプリケーションと Side-by-side アセンブリのビルド](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)分離アプリケーションと side-by-side アセンブリの概念に基づいて、Windows デスクトップアプリケーションの配置モデルについて説明します。

[64 C++ビット、x64 ターゲット用のプロジェクトの構成](configuring-programs-for-64-bit-visual-cpp.md)MSVC build ツールを使用して64ビットの x64 ハードウェアを対象にする方法。

[ARM C++プロセッサのプロジェクトを構成する](configuring-programs-for-arm-processors-visual-cpp.md)MSVC build ツールを使用して ARM ハードウェアを対象にする方法。

[コードの最適化](optimizing-your-code.md)プログラムガイド付き最適化を含むさまざまな方法でコードを最適化する方法。

[WINDOWS XP 用プログラムの構成](configuring-programs-for-windows-xp.md)MSVC build ツールを使用して Windows XP を対象にする方法。

[C/C++ ビルドのリファレンス](reference/c-cpp-building-reference.md)<br/>
C++ でのプログラムのビルド、コンパイラ オプションとリンカー オプション、およびさまざまなビルド ツールに関する参照記事へのリンクがあります。
