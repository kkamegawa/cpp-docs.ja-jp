---
title: 'チュートリアル: コンパイルする c++/cli コマンドラインで/CX プログラム'
ms.date: 04/23/2019
ms.assetid: 626f5544-69ed-4736-83a9-f11389b371b2
ms.openlocfilehash: cbf5a48de3c029e36fc6daabe2b3f0db55dc173c
ms.sourcegitcommit: 18d3b1e9cdb4fc3a76f7a650c31994bdbd2bde64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/29/2019
ms.locfileid: "64877165"
---
# <a name="walkthrough-compiling-a-ccx-program-on-the-command-line"></a>チュートリアル: コンパイルする c++/cli コマンドラインで/CX プログラム

> [!NOTE] 
> 新しい UWP アプリとコンポーネントは、お勧めしますを使用すること[ C++/WinRT](/windows/uwp/cpp-and-winrt-apis/)、標準 c++ 17 の言語プロジェクションの Windows ランタイム Api です。 C +/cli WinRT はバージョン 1803 以降から Windows 10 SDK で使用できます。 C +/cli WinRT はヘッダー ファイル、完全に実装されは最新の Windows API にファースト クラスのアクセス提供するために設計されています。

MicrosoftC++コンパイラ (MSVC) がサポートC++コンポーネント拡張 (C++/CX)、Windows ランタイム プログラミング モデルを対象とするその他の種類と演算子があります。 使用することができますC++/CX 用ユニバーサル Windows プラットフォーム (UWP) と Windows デスクトップ アプリをビルドします。 詳細については、次を参照してください。 [A ツアーの C+/cli CX](https://msdn.microsoft.com/magazine/dn166929.aspx)と[Component Extensions for Runtime Platforms](../extensions/component-extensions-for-runtime-platforms.md)します。

このチュートリアルでは、テキスト エディターを使って基本的な C++/CX プログラムを作成し、コマンド ラインでコンパイルします。 (表示されているプログラムをタイプするのではなく、自分の C++/CX プログラムを使用するか、別のヘルプ記事の C++/CX コード サンプルを使用できます。 この手法はビルドと UI 要素がない小さなモジュールをテストする場合に便利です。)

> [!NOTE]
> Visual Studio IDE を使って C++/CX プログラムをコンパイルすることもできます。 IDE には、設計、デバッグ、エミュレーション、およびコマンド ラインでは利用できないデプロイのサポートが含まれているために、IDE を使用して、ユニバーサル Windows プラットフォーム (UWP) アプリを構築することをお勧めします。 詳細については、次を参照してください。[で C++ UWP アプリの作成](/windows/uwp/get-started/create-a-basic-windows-10-app-in-cpp)です。

## <a name="prerequisites"></a>必須コンポーネント

C++ 言語の基本を理解します。

## <a name="compiling-a-ccx-program"></a>C++/CX プログラムのコンパイル

C++ のコンパイルを有効にする/cli CX が使用する必要があります、 [/ZW](reference/zw-windows-runtime-compilation.md)コンパイラ オプション。 MSVC コンパイラは、Windows ランタイムを対象とし、必要なライブラリへのリンクされた .exe ファイルを生成します。

#### <a name="to-compile-a-ccx-application-on-the-command-line"></a>コマンド ラインで C++/CX アプリケーションをコンパイルするには:

1. 開く、**開発者コマンド プロンプト**ウィンドウ。 (上、**開始**ウィンドウを開いて、**アプリ**します。 開く、 **Visual Studio Tools** 、バージョンの Visual Studio は、下のフォルダーをクリックして、**開発者コマンド プロンプト**ショートカットです)。開発者コマンド プロンプト ウィンドウを開く方法の詳細については、次を参照してください。[コマンドラインから MSVC ツールセットを使用して](building-on-the-command-line.md)します。

   コンピューターのオペレーティング システムと構成によっては、コードを正常にコンパイルするために管理者の資格情報が必要な場合があります。 を管理者としてコマンド プロンプト ウィンドウを実行するには、のショートカット メニューを開き**開発者コマンド プロンプト**選び、**管理者として実行**します。

1. コマンド プロンプトで次のように入力します。**メモ帳」と**します。

   選択**はい**ファイルを作成するように要求しているときにします。

1. メモ帳で、次の行を入力します。

    ```cpp
    using namespace Platform;

    int main(Platform::Array<Platform::String^>^ args)
    {
        Platform::Details::Console::WriteLine("This is a C++/CX program.");
    }
    ```

1. メニュー バーで、**ファイル** > **保存**します。

   作成した、 C++ Windows ランタイムを使用するソース ファイル[Platform 名前空間](../cppcx/platform-namespace-c-cx.md)名前空間。

1. コマンド プロンプトで次のように入力します。 **cl/EHsc/ZW」と/link/SUBSYSTEM:CONSOLE**します。 cl.exe コンパイラは、ソース コードを .obj ファイルにコンパイルした後、リンカーを実行して basiccx.exe という名前の実行プログラムを生成します。 (、 [/EHsc](reference/eh-exception-handling-model.md)コンパイラ オプションは、C++ 例外処理モデルを指定し、 [/link](reference/link-pass-options-to-linker.md)フラグをコンソール アプリケーションを指定します)。

1. コマンド プロンプトで、basiccx.exe プログラムを実行する入力**basiccx**します。

   プログラムは、次のテキストを表示して終了します。

    ```Output
    This is a C++/CX program.
    ```

## <a name="see-also"></a>関連項目

[プロジェクトおよびビルド システム](projects-and-build-systems-cpp.md)<br/>
[MSVC コンパイラ オプション](reference/compiler-options.md)
