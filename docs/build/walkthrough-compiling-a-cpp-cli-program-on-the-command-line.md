---
title: 'チュートリアル: コンパイルする c++/cli コマンドラインで CLI プログラム'
ms.date: 04/23/2019
ms.assetid: cef41c88-faf9-439d-8423-25aa3f5674dd
ms.openlocfilehash: 8a5c5659367350a80725b365ef9c431bbec209d1
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877457"
---
# <a name="walkthrough-compiling-a-ccli-program-on-the-command-line"></a>チュートリアル: コンパイルする c++/cli コマンドラインで CLI プログラム

共通言語ランタイム (CLR) を対象とし、.NET Framework を使用する Visual C++ プログラムを作成して、コマンド ラインでビルドできます。 Visual C++ では C++/CLI プログラミング言語がサポートされます。このプログラミング言語には、.NET プログラミング モデルを対象とする追加の型と演算子があります。 概要については、C +/cli CLI 言語を参照してください[C + での .NET プログラミング/cli (Visual C)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)。

このチュートリアルでは、テキスト エディターを使って基本的な C++/CLI プログラムを作成し、コマンド ラインでコンパイルします。 (表示されているプログラムをタイプするのではなく、自分の C++/CLI プログラムを使用するか、別のヘルプ記事の C++/CLI コード サンプルを使用できます。 この手法はビルドと UI 要素がない小さなモジュールをテストする場合に便利です。)

## <a name="prerequisites"></a>必須コンポーネント

C++ 言語の基本を理解します。

## <a name="compiling-a-ccli-program"></a>C++/CLI プログラムのコンパイル

次の手順は、.NET Framework クラスを使用する C++/CLI コンソール アプリケーションをコンパイルする方法を示します。

C++ のコンパイルを有効にする/cli、CLI を使用する必要がある、 [/clr](reference/clr-common-language-runtime-compilation.md)コンパイラ オプション。 MSVC コンパイラが MSIL コードを含む .exe ファイルを生成します: または MSIL とネイティブ コードの混合、および、必要な .NET Framework ライブラリへのリンク。

### <a name="to-compile-a-ccli-application-on-the-command-line"></a>C++/CLI アプリケーションをコマンド ラインでコンパイルするには

1. 開く、**開発者コマンド プロンプト**ウィンドウ。 具体的な手順については、次を参照してください。[開発者コマンド プロンプト ウィンドウを開く](building-on-the-command-line.md#developer_command_prompt)します。

   コンピューターのオペレーティング システムと構成によっては、コードを正常にコンパイルするために管理者の資格情報が必要な場合があります。 コマンド プロンプトのショートカット メニューを開き、選択し、右クリックし、管理者としてコマンド プロンプト ウィンドウを実行する**詳細** > **管理者として実行**します。

1. コマンド プロンプトで、「`notepad basicclr.cpp`」と入力します。

   選択**はい**ファイルを作成するように要求しているときにします。

1. メモ帳で、次の行を入力します。

   ```cpp
   int main()
   {
       System::Console::WriteLine("This is a C++/CLI program.");
   }
   ```

1. メニュー バーで、**ファイル** > **保存**します。

   .NET Framework クラスを使用する Visual C ソース ファイルを作成した (<xref:System.Console>) で、<xref:System>名前空間。

1. コマンド プロンプトで、「`cl /clr basicclr.cpp`」と入力します。 cl.exe コンパイラによって、ソース コードは MSIL を含む .obj ファイルにコンパイルされ、リンカーが実行されて basicclr.exe という名前の実行可能プログラムが生成されます。

1. basicclr.exe プログラムを実行するには、コマンド プロンプトで「`basicclr`」と入力します。

   プログラムは、次のテキストを表示して終了します。

   ```Output
   This is a C++/CLI program.
   ```

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)<br/>
[プロジェクトおよびビルド システム](projects-and-build-systems-cpp.md)<br/>
[MSVC コンパイラ オプション](reference/compiler-options.md)
