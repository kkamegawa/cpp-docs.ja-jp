---
title: 'チュートリアル: 独自のダイナミックリンクライブラリを作成してC++使用する ()'
description: C++ を使って Visual Studio で Windows ダイナミック リンク ライブラリ (DLL) を作成します。
ms.custom: conceptual
ms.date: 08/22/2019
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: 37dc59dfb77af9fff240c0d44b21de84b17d073b
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127843"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>チュートリアル: 独自のダイナミックリンクライブラリを作成してC++使用する ()

このステップバイステップチュートリアルでは、Visual Studio IDE を使用して、Microsoft C++ (MSVC) で記述された独自のダイナミックリンクライブラリ (DLL) を作成する方法について説明します。 次に、別C++のアプリから DLL を使用する方法を示します。 Dll (UNIX ベースのオペレーティングシステムでは*共有ライブラリ*とも呼ばれます) は、最も便利な種類の Windows コンポーネントの1つです。 これらは、コードとリソースを共有したり、アプリのサイズを縮小したりするための手段として使用できます。 Dll を使用すると、アプリのサービスと拡張を簡単に行うことができます。

このチュートリアルでは、いくつかの数値演算関数を実装する DLL を作成します。 次に、DLL の関数を使用するコンソールアプリを作成します。 また、Windows Dll で使用されるプログラミング手法と規約の概要についても説明します。

このチュートリアルでは、次の作業について説明します。

- Visual Studio で DLL プロジェクトを作成します。

- エクスポートされた関数と変数を DLL に追加します。

- Visual Studio でコンソール アプリ プロジェクトを作成します。

- コンソール アプリで DLL からインポートした関数と変数を使います。

- 完成したアプリを実行します。

静的にリンクされたライブラリと同様、DLL は変数、関数、およびリソースを名前で_エクスポート_します。 クライアントアプリは、これらの変数、関数、およびリソースを使用するために名前を_インポート_します。 静的にリンクされるライブラリとは異なり、読み込み時または実行時に Windows によってアプリのインポートが DLL のエクスポートに結合されます。リンク時に結合するのではありません。 これらの結合を行うには、標準 C++ コンパイル モデルには含まれていない補足情報が Windows に必要です。 MSVC コンパイラには、この補足情報を提供するための Microsoft 固有の C++ 拡張機能がいくつか実装されています。 これらの拡張機能について順次説明していきます。

このチュートリアルでは 2 つの Visual Studio ソリューションを作成します。DLL を構築するものと、クライアント アプリを構築するものです。 DLL は、C の呼び出し規約を使用します。 プラットフォーム、呼び出し規約、およびリンク規約が一致する限り、他のプログラミング言語で記述されたアプリから呼び出すことができます。 クライアント アプリでは、読み込み時に Windows によってアプリが DLL にリンクされる、"_暗黙的リンク_" を使います。 このリンクを使うことで、静的にリンクされたライブラリの関数と同じように、DLL で指定した関数をアプリから呼び出すことができます。

このチュートリアルでは一部の一般的な状況を扱っていません。 このコードでは、他のC++プログラミング言語による dll の使用については説明しません。 [リソースのみの dll を作成](creating-a-resource-only-dll.md)する方法、または[明示的なリンク](linking-an-executable-to-a-dll.md#linking-explicitly)を使用して、読み込み時ではなく実行時に dll を読み込む方法については説明しません。 MSVC と Visual Studio を使用してこれらすべてを行うことができます。

DLL に関する詳細情報へのリンクについては、「[Visual Studio での C/C++ Dll の作成](dlls-in-visual-cpp.md)」をご覧ください。 暗黙のリンクと明示的なリンクの詳細については、「[使用するリンク方法を決定](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)する」を参照してください。 C 言語リンケージ規則C++を使用するプログラミング言語で使用するための dll を作成する方法については、「 [c 言語の実行可能ファイルで使用する関数のエクスポートC++ ](exporting-cpp-functions-for-use-in-c-language-executables.md)」を参照してください。 .NET 言語で使う DLL を作成する方法については、「[DLL 関数の Visual Basic アプリケーションからの呼び出し方](calling-dll-functions-from-visual-basic-applications.md)」をご覧ください。

## <a name="prerequisites"></a>前提条件

- Microsoft Windows 7 またはそれ以降のバージョンを稼働しているコンピューター。 最適な開発作業のためには、Windows 10 をお勧めします。

::: moniker range=">=vs-2017"

- Visual Studio。 Visual Studio をダウンロードしてインストールする方法について詳しくは、「[Visual Studio のインストール](/visualstudio/install/install-visual-studio)」をご覧ください。 インストーラーを実行するときに、 **[C++ によるデスクトップ開発]** ワークロードがオンになっていることを確認してください。 Visual Studio をインストールしたときにこのワークロードをインストールしていなくても問題ありません。 インストーラーをもう一度実行して、すぐにインストールできます。

   ![C++ によるデスクトップ開発](media/desktop-development-with-cpp.png "C++ によるデスクトップ開発")

::: moniker-end

::: moniker range="vs-2015"

- Visual Studio。 Visual Studio 2015 をダウンロードしてインストールする方法については、「 [Visual studio 2015 のインストール](/visualstudio/install/install-visual-studio-2015?view=vs-2015)」を参照してください。 既定ではインストールされないC++ため、カスタムインストールを使用して、コンパイラとツールをインストールします。

::: moniker-end

- Visual Studio IDE の使用に関する基本事項の理解。 以前に Windows デスクトップ アプリを使ったことがあれば、おそらく問題ありません。 概要については、[Visual Studio IDE の機能ツアー](/visualstudio/ide/visual-studio-ide)に関するページをご覧ください。

- 内容を理解するための、C++ 言語の基本に関する十分な理解。 あまり複雑な作業は行わないので、ご安心ください。

::: moniker range="vs-2017"

> [!NOTE]
> このチュートリアルでは、Visual Studio 2017 バージョン15.9 以降を使用していることを前提としています。 以前のバージョンの Visual Studio 2017 では、コードテンプレートに欠陥があるか、別のユーザーインターフェイスダイアログが使用されていました。 問題を回避するには、Visual Studio インストーラーを使用して Visual Studio 2017 をバージョン15.9 以降に更新します。

::: moniker-end

## <a name="create-the-dll-project"></a>DLL プロジェクトを作成する

この一連のタスクでは、DLL のプロジェクトを作成して、コードを追加し、ビルドします。 最初に、Visual Studio IDE を起動して、必要に応じてサインインします。 手順は、使用している Visual Studio のバージョンによって多少異なります。 このページの左上のコントロールで適切なバージョンを選択していることを確認してください。

::: moniker range=">=vs-2019"

### <a name="to-create-a-dll-project-in-visual-studio-2019"></a>Visual Studio 2019 で DLL プロジェクトを作成するには

1. メニューバーで [**ファイル**>**新規**>**プロジェクト**] を選択し、 **[新しいプロジェクトの作成]** ダイアログボックスを開きます。

   ![新しい DLL プロジェクトを作成する](media/create-new-dll-project-2019.png "MathLibrary プロジェクトを作成する")

1. ダイアログの上部で、 **[言語]** を **[C++]** に、 **[プラットフォーム]** を **[Windows]** に、 **[プロジェクト タイプ]** を **[ライブラリ]** に設定します。

1. フィルター処理されたプロジェクトの種類の一覧から、 **[ダイナミックリンクライブラリ (DLL)]** を選択し、 **[次へ]** をクリックします。

1. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「 *MathLibrary* 」と入力して、プロジェクトの名前を指定します。 既定の **[場所]** と **[ソリューション名]** の値はそのままにします。 **ソリューション**を**新しいソリューションを作成**するように設定します。 オンになっている場合は **、[ソリューションとプロジェクトを同じディレクトリに配置する**] チェックボックスをオフにします。

1. **[作成]** ボタンをクリックしてプロジェクトを作成します。

ソリューションが作成されると、Visual Studio の **[ソリューションエクスプローラー]** ウィンドウに生成されたプロジェクトとソースファイルが表示されます。

![Visual Studio で生成されたソリューション](media/mathlibrary-solution-explorer-162.png "Visual Studio で生成されたソリューション")

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-dll-project-in-visual-studio-2017"></a>Visual Studio 2017 で DLL プロジェクトを作成するには

1. メニューバーで、[**ファイル**>**新しい**>**プロジェクト**] を選択して **[新しいプロジェクト]** ダイアログボックスを開きます。

1. **[新しいプロジェクト]** ダイアログボックスの左ペインで、[**インストールされている** > **Visual C++**  > **Windows デスクトップ**] を選択します。 中央のウィンドウで、 **[ダイナミックリンクライブラリ (DLL)]** を選択します。 **[名前]** ボックスに「 *MathLibrary* 」と入力して、プロジェクトの名前を指定します。 既定の **[場所]** と **[ソリューション名]** の値はそのままにします。 **ソリューション**を**新しいソリューションを作成**するように設定します。 オフになっている場合は、**ソリューションのディレクトリを作成**します。

   ![MathLibrary プロジェクトに名前を指定する](media/mathlibrary-new-project-name-159.png "MathLibrary プロジェクトに名前を指定する")

1. **[OK]** ボタンを選択すると、プロジェクトが作成されます。

ソリューションが作成されると、Visual Studio の **[ソリューションエクスプローラー]** ウィンドウに生成されたプロジェクトとソースファイルが表示されます。

![Visual Studio で生成されたソリューション](media/mathlibrary-solution-explorer-159.png "Visual Studio で生成されたソリューション")

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-dll-project-in-visual-studio-2015-and-older-versions"></a>Visual Studio 2015 およびそれ以前のバージョンで DLL プロジェクトを作成するには

1. メニュー バーで、 **[ファイル]** > **[新規作成]** > **[プロジェクト]** を選択します。

1. **[新しいプロジェクト]** ダイアログ ボックスの左側のウィンドウで、 **[インストール済み]**  >  **[テンプレート]** を展開して **[Visual C++]** を選択してから、中央のウィンドウで **[Win32 コンソール アプリケーション]** を選択します。 **[名前]** エディットボックスに「 *MathLibrary* 」と入力して、プロジェクトの名前を指定します。 既定の **[場所]** と **[ソリューション名]** の値はそのままにします。 **ソリューション**を**新しいソリューションを作成**するように設定します。 オフになっている場合は、**ソリューションのディレクトリを作成**します。

   ![MathLibrary プロジェクトに名前を指定する](media/mathlibrary-project-name.png "MathLibrary プロジェクトに名前を指定する")

1. **[OK]** ボタンを選択して **[新しいプロジェクト]** ダイアログを閉じ、 **[Win32 アプリケーション ウィザード]** を起動します。

   ![Win32 アプリケーションウィザードの概要](media/mathlibrary-project-wizard-1.png "Win32 アプリケーションウィザードの概要")

1. **[次へ]** ボタンをクリックします。 **[アプリケーションの設定]** ページの **[アプリケーションの種類]** の下で、 **[DLL]** を選択します。

   ![Win32 アプリケーションウィザードでの DLL の作成](media/mathlibrary-project-wizard-2.png "Win32 アプリケーションウィザードでの DLL の作成")

1. **[完了]** をクリックすると、プロジェクトが作成されます。

ウィザードでソリューションが完了したら、Visual Studio の **[ソリューション エクスプローラー]** ウィンドウで、生成されたプロジェクトとソース ファイルを確認できます。

![Visual Studio で生成されたソリューション](media/mathlibrary-solution-explorer-153.png "Visual Studio で生成されたソリューション")

::: moniker-end

現時点では、この DLL にはほとんど意味がありません。 次に、DLL によってエクスポートされる関数を宣言するヘッダーファイルを作成し、関数定義を DLL に追加して、さらに便利にします。

### <a name="to-add-a-header-file-to-the-dll"></a>DLL にヘッダー ファイルを追加するには

1. 関数のヘッダー ファイルを作成するには、メニュー バーで **[プロジェクト]**  >  **[新しい項目の追加]** の順に選択します。

1. **[新しい項目の追加]** ダイアログ ボックスの左側のウィンドウで、 **[Visual C++]** を選択します。 中央のウィンドウで、 **[ヘッダー ファイル (.h)]** をクリックします。 ヘッダーファイルの名前として*MathLibrary*を指定します。

   ![[新しい項目の追加] ダイアログでヘッダーを追加する](media/mathlibrary-add-new-item-header-file.png "[新しい項目の追加] ダイアログボックスにヘッダーファイルを追加する")

1. **[追加]** ボタンを選択して空白のヘッダー ファイルを生成します。これは新しいエディター ウィンドウに表示されます。

   ![エディターの空の MathLibrary ファイル](media/edit-empty-mathlibrary-header.png "エディターの空の MathLibrary ファイル")

1. ヘッダー ファイルの内容を次のコードに置き換えます。

   ```cpp
   // MathLibrary.h - Contains declarations of math functions
   #pragma once

   #ifdef MATHLIBRARY_EXPORTS
   #define MATHLIBRARY_API __declspec(dllexport)
   #else
   #define MATHLIBRARY_API __declspec(dllimport)
   #endif

   // The Fibonacci recurrence relation describes a sequence F
   // where F(n) is { n = 0, a
   //               { n = 1, b
   //               { n > 1, F(n-2) + F(n-1)
   // for some initial integral values a and b.
   // If the sequence is initialized F(0) = 1, F(1) = 1,
   // then this relation produces the well-known Fibonacci
   // sequence: 1, 1, 2, 3, 5, 8, 13, 21, 34, ...

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   extern "C" MATHLIBRARY_API void fibonacci_init(
       const unsigned long long a, const unsigned long long b);

   // Produce the next value in the sequence.
   // Returns true on success and updates current value and index;
   // false on overflow, leaves current value and index unchanged.
   extern "C" MATHLIBRARY_API bool fibonacci_next();

   // Get the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned long long fibonacci_current();

   // Get the position of the current value in the sequence.
   extern "C" MATHLIBRARY_API unsigned fibonacci_index();
   ```

このヘッダー ファイルでは、2 つの初期値を指定して、一般化されたフィボナッチ数列を生成するための関数をいくつか宣言しています。 `fibonacci_init(1, 1)` を呼び出すと、有名なフィボナッチ数の数列が生成されます。

ファイルの上部にあるプリプロセッサのステートメントに注目します。 DLL プロジェクトの新しいプロジェクトテンプレートでは、定義済みのプリプロセッサマクロに **_PROJECTNAME_&#95;エクスポート**を追加します。 この例では、Visual Studio によって、MathLibrary DLL プロジェクトのビルド時に **MATHLIBRARY&#95;EXPORTS** が定義されます。

**MATHLIBRARY&#95;EXPORTS** マクロを定義すると、**MATHLIBRARY&#95;API** マクロにより関数の宣言上で `__declspec(dllexport)` 修飾子が設定されます。 この修飾子は、他のアプリケーションで使用するために、DLL から関数または変数をエクスポートするようにコンパイラとリンカーに指示します。 **MATHLIBRARY&#95;EXPORTS** が未定義の場合 (たとえば、クライアント アプリケーションによってヘッダー ファイルが含まれる場合)、**MATHLIBRARY&#95;API** によって宣言に `__declspec(dllimport)` 修飾子が適用されます。 この修飾子によって、アプリケーションへの関数または変数のインポートが最適化されます。 詳細については、「[dllexport、dllimport](../cpp/dllexport-dllimport.md)」をご覧ください。

### <a name="to-add-an-implementation-to-the-dll"></a>DLL に実装を追加するには

::: moniker range=">=vs-2019"

1. **ソリューションエクスプローラー**で、 **[ソースファイル]** ノードを右クリックし、[ > **新しい項目**の**追加**] を選択します。 前の手順で新しいヘッダーファイルを追加したのと同じ方法で、 *MathLibrary*という名前の新しい .cpp ファイルを作成します。

1. エディター ウィンドウで、既に開いている場合は **MathLibrary.cpp** のタブを選択します。 そうでない場合は、**ソリューションエクスプローラー**で、 **MathLibrary**プロジェクトの **[Source Files]** フォルダーにある**MathLibrary**をダブルクリックして開きます。

1. エディターで、MathLibrary.cpp ファイルの内容を次のコードに置き換えます。

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "pch.h" // use stdafx.h in Visual Studio 2017 and earlier
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

::: moniker-end

::: moniker range="<=vs-2017"

1. エディター ウィンドウで、既に開いている場合は **MathLibrary.cpp** のタブを選択します。 そうでない場合は、**ソリューションエクスプローラー**で、 **MathLibrary**プロジェクトの **[Source Files]** フォルダーにある**MathLibrary**をダブルクリックして開きます。

1. エディターで、MathLibrary.cpp ファイルの内容を次のコードに置き換えます。

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h" // use pch.h in Visual Studio 2019 and later
   #include <utility>
   #include <limits.h>
   #include "MathLibrary.h"

   // DLL internal state variables:
   static unsigned long long previous_;  // Previous value, if any
   static unsigned long long current_;   // Current sequence value
   static unsigned index_;               // Current seq. position

   // Initialize a Fibonacci relation sequence
   // such that F(0) = a, F(1) = b.
   // This function must be called before any other function.
   void fibonacci_init(
       const unsigned long long a,
       const unsigned long long b)
   {
       index_ = 0;
       current_ = a;
       previous_ = b; // see special case when initialized
   }

   // Produce the next value in the sequence.
   // Returns true on success, false on overflow.
   bool fibonacci_next()
   {
       // check to see if we'd overflow result or position
       if ((ULLONG_MAX - previous_ < current_) ||
           (UINT_MAX == index_))
       {
           return false;
       }

       // Special case when index == 0, just return b value
       if (index_ > 0)
       {
           // otherwise, calculate next sequence value
           previous_ += current_;
       }
       std::swap(current_, previous_);
       ++index_;
       return true;
   }

   // Get the current value in the sequence.
   unsigned long long fibonacci_current()
   {
       return current_;
   }

   // Get the current index position in the sequence.
   unsigned fibonacci_index()
   {
       return index_;
   }
   ```

::: moniker-end

今のところすべてが機能していることを確認するために、ダイナミック リンク ライブラリをコンパイルします。 コンパイルするには、メニュー バーで **[ビルド]**  >  **[ソリューションのビルド]** の順に選択します。 DLL および関連するコンパイラ出力は、ソリューションフォルダーの直下にある*Debug*というフォルダーに配置されます。 リリースビルドを作成する場合、出力は*release*というフォルダーに配置されます。 出力は次のようになります。

::: moniker range=">=vs-2019"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>pch.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2017"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>dllmain.cpp
1>MathLibrary.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

::: moniker range="vs-2015"

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

::: moniker-end

これで、Visual Studio を使用して DLL を作成できました。 次は、DLL によってエクスポートされた関数を使用するクライアント アプリを作成します。

## <a name="create-a-client-app-that-uses-the-dll"></a>DLL を使用するクライアント アプリを作成する

DLL を作成する場合は、クライアントアプリでの使用方法について検討してください。 関数を呼び出したり、DLL によってエクスポートされたデータにアクセスしたりするには、コンパイル時にクライアントのソースコードで宣言を使用できるようにする必要があります。 リンク時に、リンカーは関数呼び出しまたはデータアクセスを解決するための情報を必要とします。 DLL は、この情報を*インポートライブラリ*に提供します。これには、実際のコードではなく、関数とデータを検索する方法に関する情報を含むファイルが含まれます。 そして実行時に、オペレーティング システムによって見つけられる場所で、クライアントが DLL を利用できる必要があります。

クライアントアプリプロジェクトは、独自のものでも、サードパーティ製でも、DLL を使用するためにいくつかの情報を必要とします。 DLL のエクスポートを宣言するヘッダー、リンカーのインポートライブラリ、および DLL 自体を検索する必要があります。 1つの解決策は、これらのすべてのファイルをクライアントプロジェクトにコピーすることです。 クライアントの開発中に変更される可能性が低いサード パーティ製の DLL については、この方法がそれらを使うための最善の方法である場合があります。 ただし、自分で DLL もビルドする場合は、重複を避けることをお勧めします。 開発中の DLL ファイルのローカルコピーを作成すると、誤って別のコピーではなく1つのコピーでヘッダーファイルを変更したり、古いライブラリを使用したりする可能性があります。

同期されていないコードを回避するには、dll プロジェクトから直接 DLL ヘッダーファイルをインクルードするために、クライアントプロジェクトにインクルードパスを設定することをお勧めします。 また、クライアント プロジェクトのライブラリ パスを設定して、DLL プロジェクトから DLL インポート ライブラリをインクルードするようにします。 最後に、DLL プロジェクトから、ビルドされた DLL をクライアントビルド出力ディレクトリにコピーします。 この手順により、自分でビルドする同じ DLL のコードをクライアント アプリで使えます。

::: moniker range=">=vs-2019"

### <a name="to-create-a-client-app-in-visual-studio"></a>Visual Studio でクライアントアプリを作成するには

1. メニューバーで [**ファイル**>**新規**>**プロジェクト**] を選択し、 **[新しいプロジェクトの作成]** ダイアログボックスを開きます。

1. ダイアログの上部で、 **[言語]** を **[C++]** に、 **[プラットフォーム]** を **[Windows]** に、 **[プロジェクト タイプ]** を **[コンソール]** に設定します。

1. フィルター処理されたプロジェクト タイプの一覧から、 **[コンソール アプリ]** を選択して、 **[次へ]** を選択します。

1. **[新しいプロジェクトの構成]** ページで、 **[プロジェクト名]** ボックスに「 *MathClient* 」と入力して、プロジェクトの名前を指定します。 既定の **[場所]** と **[ソリューション名]** の値はそのままにします。 **ソリューション**を**新しいソリューションを作成**するように設定します。 オンになっている場合は **、[ソリューションとプロジェクトを同じディレクトリに配置する**] チェックボックスをオフにします。

   ![クライアントプロジェクトの名前を指定する](media/mathclient-project-name-2019.png "クライアントプロジェクトの名前を指定する")

1. **[作成]** ボタンを選択してクライアント プロジェクトを作成します。

最小コンソールアプリケーションプロジェクトが作成されます。 メイン ソース ファイルの名前は、以前に入力したプロジェクト名と同じです。 この例では、**MathClient.cpp** という名前が付いています。 これはビルドできますが、まだ DLL が使われていません。

::: moniker-end

::: moniker range="vs-2017"

### <a name="to-create-a-client-app-in-visual-studio-2017"></a>Visual Studio 2017 でクライアント アプリを作成するには

1. 作成したC++ DLL を使用するアプリを作成するには、メニューバーで [**ファイル**>**新しい**>**プロジェクト**] を選択します。

1. **[新しいプロジェクト]** ダイアログの左側のウィンドウで、 **[インストール済み]** [Visual C++] >  の下の **[Windows デスクトップ]** を選択します。 中央のウィンドウで、 **[Windows コンソールアプリケーション]** を選択します。 **[名前]** ボックスに、プロジェクトの名前として*MathClient*を指定します。  既定の **[場所]** と **[ソリューション名]** の値はそのままにします。 **ソリューション**を**新しいソリューションを作成**するように設定します。 オフになっている場合は、**ソリューションのディレクトリを作成**します。

   ![クライアントプロジェクトの名前を指定する](media/mathclient-new-project-name-159.png "クライアントプロジェクトの名前を指定する")

1. **[OK]** を選択して、クライアントアプリプロジェクトを作成します。

最小コンソールアプリケーションプロジェクトが作成されます。 メイン ソース ファイルの名前は、以前に入力したプロジェクト名と同じです。 この例では、**MathClient.cpp** という名前が付いています。 これはビルドできますが、まだ DLL が使われていません。

::: moniker-end

::: moniker range="vs-2015"

### <a name="to-create-a-client-app-in-visual-studio-2015"></a>Visual Studio 2015 でクライアントアプリを作成するには

1. 作成したC++ DLL を使用するアプリを作成するには、メニューバーで [**ファイル**>**新しい**>**プロジェクト**] を選択します。

1. **[新しいプロジェクト]** ダイアログの左側のウィンドウで、 **[インストール済み]** [テンプレート] > [Visual C++] >  の下の **[Win32]** を選択します。 中央のウィンドウで **[Win32 コンソール アプリケーション]** をクリックします。 **[名前]** ボックスに、プロジェクトの名前として*MathClient*を指定します。 既定の **[場所]** と **[ソリューション名]** の値はそのままにします。 **ソリューション**を**新しいソリューションを作成**するように設定します。 オフになっている場合は、**ソリューションのディレクトリを作成**します。

   ![クライアントプロジェクトの名前を指定する](media/mathclient-project-name.png "クライアントプロジェクトの名前を指定する")

1. **[OK]** ボタンを選択して **[新しいプロジェクト]** ダイアログを閉じ、 **[Win32 アプリケーション ウィザード]** を起動します。 **[Win32 アプリケーション ウィザード]** ダイアログ ボックスの **[概要]** ページで、 **[次へ]** をクリックします。

1. **[アプリケーションの設定]** ページの **[アプリケーションの種類]** の下で、 **[コンソール アプリケーション]** がまだ選択されていない場合はこれを選択します。

1. **[完了]** をクリックすると、プロジェクトが作成されます。

ウィザードが完了したら、最小限のコンソール アプリケーション プロジェクトが自動的に作成されます。 メイン ソース ファイルの名前は、以前に入力したプロジェクト名と同じです。 この例では、**MathClient.cpp** という名前が付いています。 これはビルドできますが、まだ DLL が使われていません。

::: moniker-end

次に、ソースコード内の MathLibrary 関数を呼び出すには、プロジェクトに*MathLibrary*ファイルが含まれている必要があります。 クライアント アプリ プロジェクトにこのヘッダー ファイルをコピーした後、既存のアイテムとしてこれをプロジェクトに追加することができます。 この方法は、サード パーティ製のライブラリに最適である場合があります。 ただし、DLL とクライアントのコードを同時に操作している場合、ヘッダーファイルは同期されない可能性があります。この問題を回避するには、プロジェクトに **[追加のインクルードディレクトリ]** パスを設定し、元のヘッダーへのパスを含めます。

### <a name="to-add-the-dll-header-to-your-include-path"></a>インクルード パスに DLL のヘッダーを追加するには

1. **[ソリューション エクスプローラー]** で **[MathClient]** ノードを右クリックして、 **[プロパティ ページ]** ダイアログを開きます。

1. **[構成]** ドロップダウンボックスで、 **[すべての構成]** を選択します (まだ選択されていない場合)。

1. 左側のウィンドウで、 **[構成プロパティ]**  > [ **CC++ /**  > **全般**] の順に選択します。

1. プロパティ ウィンドウで、 **[追加のインクルード ディレクトリ]** エディット ボックスの横にあるドロップダウン コントロールを選択してから、 **[編集]** を選択します。

   ![追加のインクルードディレクトリのプロパティを編集します。](media/mathclient-additional-include-directories-property.png "追加のインクルードディレクトリのプロパティを編集します。")

1. **[追加のインクルード ディレクトリ]** ダイアログ ボックスの上部のウィンドウ内をダブルクリックして、編集コントロールを有効にします。 または、フォルダーアイコンをクリックして新しいエントリを作成します。

1. 編集コントロールで、**MathLibrary.h** ヘッダー ファイルの場所へのパスを指定します。 省略記号 ( **...** ) コントロールを選択して、適切なフォルダーを参照できます。

   また、クライアントソースファイルから DLL ヘッダーファイルが格納されているフォルダーへの相対パスを入力することもできます。 指示に従って、DLL とは別のソリューションにクライアントプロジェクトを配置した場合、相対パスは次のようになります。

   `..\..\MathLibrary\MathLibrary`

   DLL とクライアントプロジェクトが同じソリューション内にある場合、相対パスは次のようになります。

   `..\MathLibrary`

   DLL プロジェクトとクライアントプロジェクトが他のフォルダーにある場合は、一致するように相対パスを調整します。 または、省略記号コントロールを使用してフォルダーを参照します。

   ![ヘッダーの場所を "追加のインクルードディレクトリ" プロパティに追加します。](media/mathclient-additional-include-directories.png "ヘッダーの場所を "追加のインクルードディレクトリ" プロパティに追加します。")

1. **[追加のインクルードディレクトリ]** ダイアログボックスでヘッダーファイルへのパスを入力したら、 **[OK]** をクリックします。 **[プロパティページ]** ダイアログボックスで、 **[OK]** をクリックして変更を保存します。

これで **MathLibrary.h** ファイルをインクルードして、それで宣言した関数をクライアント アプリケーション内で使えるようになりました。 次のコードを使って、**MathClient.cpp** の内容を置き換えます。

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
// #include "pch.h" Uncomment for Visual Studio 2017 and earlier
#include <iostream>
#include "MathLibrary.h"

int main()
{
    // Initialize a Fibonacci relation sequence.
    fibonacci_init(1, 1);
    // Write out the sequence values until overflow.
    do {
        std::cout << fibonacci_index() << ": "
            << fibonacci_current() << std::endl;
    } while (fibonacci_next());
    // Report count of values written before overflow.
    std::cout << fibonacci_index() + 1 <<
        " Fibonacci sequence values fit in an " <<
        "unsigned 64-bit integer." << std::endl;
}
```

このコードはコンパイルできますが、リンクはできません。 クライアントアプリを今すぐビルドすると、エラー一覧に LNK2019 エラーがいくつか表示されます。 これは、プロジェクトにいくつかの情報が不足しているためです。プロジェクトが*MathLibrary*ライブラリに対する依存関係をまだ持っていないことが指定されていません。 また、 *MathLibrary*ファイルの検索方法をリンカーに指示していません。

この問題を解決するには、ライブラリファイルをクライアントアプリプロジェクトに直接コピーします。 リンカーは、このファイルを自動的に検索して使用します。 ただし、ライブラリとクライアントアプリの両方が開発中である場合は、もう一方のコピーでは表示されない変更が生じる可能性があります。 この問題を回避するには、 **[追加の依存関係]** プロパティを設定して、プロジェクトが*MathLibrary*に依存していることをビルドシステムに伝えます。 また、プロジェクトに追加の**ライブラリディレクトリ**パスを設定して、リンクするときに元のライブラリへのパスを含めることもできます。

### <a name="to-add-the-dll-import-library-to-your-project"></a>プロジェクトに DLL インポート ライブラリを追加するには

1. **ソリューションエクスプローラー**で **[MathClient]** ノードを右クリックし、 **[プロパティ]** をクリックして、 **[プロパティページ]** ダイアログを開きます。

1. **[構成]** ドロップダウンボックスで、 **[すべての構成]** を選択します (まだ選択されていない場合)。 これにより、すべてのプロパティの変更がデバッグビルドとリリースビルドの両方に適用されます。

1. 左側のウィンドウで、 **[構成プロパティ]**  > [**リンカー** > **入力**] を選択します。 プロパティ ウィンドウで、 **[追加の依存ファイル]** エディット ボックスの横にあるドロップダウン コントロールを選択してから、 **[編集]** を選択します。

   !["追加の依存関係" プロパティを編集します。](media/mathclient-additional-dependencies-property.png ""追加の依存関係" プロパティを編集します。")

1. **[追加の依存関係]** ダイアログで、上部の編集コントロールの一覧に*MathLibrary*を追加します。

   ![ライブラリの依存関係を追加する](media/mathclient-additional-dependencies.png "ライブラリの依存関係を追加する")

1. **[OK]** を選択して、 **[プロパティ ページ]** ダイアログ ボックスに戻ります。

1. 左側のウィンドウで、 **[構成プロパティ]**  > [**リンカー** > **全般**] を選択します。 プロパティ ウィンドウで、 **[追加のライブラリ ディレクトリ]** エディット ボックスの横にあるドロップダウン コントロールを選択してから、 **[編集]** を選択します。

   ![追加のライブラリディレクトリのプロパティを編集します。](media/mathclient-additional-library-directories-property.png "追加のライブラリディレクトリのプロパティを編集します。")

1. **[追加のライブラリ ディレクトリ]** ダイアログ ボックスの上部のウィンドウ内をダブルクリックして、編集コントロールを有効にします。 編集コントロールで、**MathLibrary.lib** ファイルの場所へのパスを指定します。 既定では、DLL ソリューションフォルダーの直下にある*Debug*というフォルダーにあります。 リリースビルドを作成すると、ファイルは*release*というフォルダーに配置されます。 `$(IntDir)` マクロを使用して、作成するビルドの種類に関係なく、リンカーが DLL を検索できるようにすることができます。 指示に従って、DLL プロジェクトとは別のソリューションにクライアントプロジェクトを配置した場合、相対パスは次のようになります。

   `..\..\MathLibrary\$(IntDir)`

   DLL とクライアントプロジェクトが他の場所にある場合は、一致するように相対パスを調整します。

   ![ライブラリディレクトリを追加する](media/mathclient-additional-library-directories.png "ライブラリディレクトリを追加する")

1. **[追加のライブラリ ディレクトリ]** ダイアログ ボックスにライブラリ ファイルへのパスを入力したら、 **[OK]** ボタンを選択して **[プロパティ ページ]** ダイアログ ボックスに戻ります。 **[OK]** を選択してプロパティの変更を保存します。

これでクライアント アプリを正常にコンパイルおよびリンクできるようになりましたが、実行のために必要なものはまだ何も含まれていません。 オペレーティング システムによってアプリが読み込まれると、MathLibrary DLL が検索されます。 特定のシステム ディレクトリ、環境パス、またはアプリのローカル ディレクトリに DLL が見つからない場合、読み込みは失敗します。 オペレーティングシステムによっては、次のようなエラーメッセージが表示されます。

![MathLibrary DLL が見つかりませんエラー](media/mathclient-system-error-mathlibrary-dll-not-found.png "MathLibrary DLL が見つかりませんエラー")

この問題を回避する方法の 1 つは、ビルド プロセスの一環として、クライアントの実行可能ファイルが置かれているディレクトリに DLL をコピーすることです。 **ビルド後のイベント**をプロジェクトに追加して、DLL をビルド出力ディレクトリにコピーするコマンドを追加できます。 ここで指定されたコマンドは、DLL が存在しないか変更されている場合にのみ DLL をコピーします。 この例では、ビルド構成に基づいて、マクロを使用してデバッグまたはリリースの場所にコピーします。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>ビルド後のイベントで DLL をコピーするには

1. **ソリューションエクスプローラー**で **[MathClient]** ノードを右クリックし、 **[プロパティ]** をクリックして、 **[プロパティページ]** ダイアログを開きます。

1. **[構成]** ドロップダウン ボックスで、 **[すべての構成]** がまだ選択されていない場合はこれを選択します。

1. 左側のウィンドウで、 **[構成プロパティ]** を選択して、ビルド**後のイベント** ** > ビルドイベント > ** します。

1. プロパティペインで、**コマンドライン** フィールドの 編集 コントロールを選択します。 指示に従って、DLL プロジェクトとは別のソリューションにクライアントプロジェクトを配置した場合は、次のコマンドを入力します。

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   DLL とクライアントプロジェクトが他のディレクトリにある場合は、一致するように DLL の相対パスを変更します。

   ![ビルド後コマンドを追加する](media/mathclient-post-build-command-line.png "ビルド後コマンドを追加する")

1. **[OK]** ボタンを選択して、プロジェクト プロパティに変更を保存します。

これで、クライアント アプリのビルドと実行に必要なものがすべて揃いました。 メニュー バーで **[ビルド]**  >  **[ソリューションのビルド]** の順に選択して、アプリケーションをビルドします。 Visual Studio の **[出力]** ウィンドウには、使用している visual studio のバージョンに応じて、次の例のようなものが表示されます。

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

これで、DLL の関数を呼び出すアプリケーションの作成が完了しました。 アプリケーションを実行してその動作を確認してみましょう。 メニュー バーで、 **[デバッグ]**  >  **[デバッグなしで開始]** の順に選択します。 プログラムを実行するためのコマンド ウィンドウが Visual Studio により開かれます。 出力の最後の部分は次のようになります。

![デバッグなしでクライアントアプリを起動する](media/mathclient-run-without-debugging.png "デバッグなしでクライアントアプリを起動する")

任意のキーを押して、コマンド ウィンドウを閉じます。

DLL とクライアント アプリケーションを作成したので、実験を行えます。 クライアント アプリのコードにブレークポイントを設定して、デバッガーでアプリを実行してみます。 ライブラリの呼び出しにステップ インするときの動作を確認します。 ライブラリに他の関数を追加するか、DLL を使用する別のクライアント アプリを作成します。

アプリを配置するときに、使われる DLL も配置する必要があります。 ビルドする Dll を作成したり、サードパーティからインクルードしたりする最も簡単な方法は、アプリと同じディレクトリに配置することです。 これは、*アプリローカル展開*と呼ばれています。 配置の詳細については、「 [Deployment in Visual C++](../windows/deployment-in-visual-cpp.md)」を参照してください。

## <a name="see-also"></a>参照

[DLL 関数の Visual Basic アプリケーションからの呼び出し方](calling-dll-functions-from-visual-basic-applications.md)
