---
title: 'チュートリアル: 作成し、使用して、独自のダイナミック リンク ライブラリ (C++)'
ms.custom: conceptual
ms.date: 09/24/2018
helpviewer_keywords:
- libraries [C++], DLLs
- DLLs [C++], walkthroughs
ms.assetid: 3ae94848-44e7-4955-bbad-7d40f493e941
ms.openlocfilehash: c09fa369cd4e0b726d809fa709518574d4fdbc6e
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51330542"
---
# <a name="walkthrough-create-and-use-your-own-dynamic-link-library-c"></a>チュートリアル: 作成し、使用して、独自のダイナミック リンク ライブラリ (C++)

このステップ バイ ステップ チュートリアルでは、Visual Studio IDE を使用して、C++ で記述された独自ダイナミック リンク ライブラリ (DLL) を作成し、別の C++ アプリからそれを使用する方法を示します。 Dll は、最も役に立つの種類の Windows コンポーネントのいずれかです。 お客様のアプリのサイズを縮小して、サービスし、アプリを拡張しやすく、コードとリソースを共有する方法としてそれらを使用できます。 このチュートリアルでは、いくつかの数値演算関数を実装する DLL を作成し、DLL から関数を使用するコンソール アプリを作成します。 過程で、いくつかのプログラミング手法と Windows Dll で使用される規則の概要を取得します。

このチュートリアルでは、次の作業について説明します。

- Visual Studio で DLL プロジェクトを作成します。

- DLL にエクスポートされた関数および変数を追加します。

- Visual Studio でコンソール アプリ プロジェクトを作成します。

- 関数と、コンソール アプリで DLL からインポートされた変数を使用します。

- 完成したアプリを実行します。

などの静的リンク ライブラリ、DLL_エクスポート_変数、関数、およびリソース名、およびアプリで_インポート_これらの変数、関数、およびリソースを使用するこれらの名前。 静的にリンクされたライブラリとは異なりは、Windows は、読み込み時に、またはリンク時に接続することではなく、実行時に DLL のエクスポートに、アプリ内のインポートを接続します。 Windows では、これらの接続を作成する標準の C++ コンパイル モデルに含まれていない追加の情報が必要です。 Visual C コンパイラでは、この余分な情報を提供するために C に一部の Microsoft 固有拡張機能を実装します。 これらの拡張機能を説明します。

このチュートリアルは、2 つの Visual Studio ソリューションを作成します。DLL をビルドして、クライアント アプリを構築します。 DLL は、プラットフォームとの呼び出しとリンク規則に一致する限り、その他の言語を使用してビルドされたアプリから呼び出せるように C 呼び出し規則を使用します。 クライアント アプリは_暗黙的リンク_Windows が DLL 読み込み時に、アプリをリンクします。 このリンクには、アプリの静的にリンクされたライブラリで、関数と同じように DLL が指定した関数を呼び出すことができます。

このチュートリアルには、いくつかの一般的な状況がについて説明します。 他のプログラミング言語での C++ Dll の使用は表示されません。 リソース専用 DLL を作成する方法は表示されません。 負荷時ではなく、実行時に Dll を読み込む明示的リンクの使用も表示されません。 確実に、これらすべての作業を行う Visual C を使用することができます。 Dll に関する詳細情報へのリンクを参照してください。 [Visual c の Dll](../build/dlls-in-visual-cpp.md)します。 暗黙的なリンクと明示的なリンクの詳細については、次を参照してください。[をリンクする方法の決定使用](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)します。 C 言語のリンケージ規則を使用する言語のプログラミングを使用する C++ Dll を作成する方法の詳細については、次を参照してください。 [C 言語の実行可能ファイルで使用するための C++ 関数のエクスポート](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)します。 .NET 言語で使用するための Dll を作成する方法については、次を参照してください。 [Visual Basic アプリケーションから DLL 関数を呼び出す](../build/calling-dll-functions-from-visual-basic-applications.md)します。

このチュートリアルは、Visual Studio 2017 を使用しますが、コードおよび説明の大半は以前のバージョンに適用します。 新しいプロジェクトをビルドする手順は、Visual Studio 2017 バージョン 15.3 以降を変更します。 このチュートリアルでは、新しいと、古いバージョンのプロジェクトを作成する方法について説明します。 Visual Studio のバージョンに一致する手順を検索します。

## <a name="prerequisites"></a>必須コンポーネント

- Microsoft Windows 7 またはそれ以降のバージョンを実行するコンピューター。 開発のベスト エクスペリエンスを実現するには Windows 10 をお勧めします。

- Visual Studio 2017 のコピー。 ダウンロードして Visual Studio をインストールする方法については、次を参照してください。 [Visual Studio 2017 のインストール](/visualstudio/install/install-visual-studio)します。 インストーラーを実行するときに、以下のことを確認、 **C++ によるデスクトップ開発**ワークロードがチェックされます。 Visual Studio をインストールしたときに、このワークロードをインストールしなかった場合、心配しないでください。 インストーラーをもう一度実行して、今すぐインストールします。

   ![C++ によるデスクトップ開発](media/desktop-development-with-cpp.png "C++ によるデスクトップ開発")

- Visual Studio IDE の使用の基本を理解します。 前に、Windows デスクトップ アプリを使用した場合保持できます可能性があります。 概要については、次を参照してください。 [Visual Studio IDE 機能ツアー](/visualstudio/ide/visual-studio-ide)します。

- 十分な作業を進めるには C++ 言語の基礎について理解します。 ご心配なく、あまり複雑な何もしません。

## <a name="create-the-dll-project"></a>DLL プロジェクトを作成します。

この一連のタスクでのコードを追加、DLL のプロジェクトを作成、するをビルドします。 最初に、Visual Studio IDE を起動し、サインインする必要がある場合にサインインします。 Visual Studio 2017 バージョン 15.3 の手順については、先に。 以前のバージョンについては、後で、したがって前方にスキップする必要がある場合。

### <a name="to-create-a-dll-project-in-visual-studio-2017-version-153-or-later"></a>15.3 以降、Visual Studio 2017 バージョンで DLL プロジェクトを作成するには

1. メニュー バーで **[ファイル]** > **[新規作成]** > **[プロジェクト]** の順に選択し、**[新しいプロジェクト]** ダイアログ ボックスを開きます。

1. 左側のウィンドウで、**新しいプロジェクト** ダイアログ ボックスで、展開**インストール済み**と**Visual C**必要に応じて、選び、 **Windows デスクトップ**. 中央のウィンドウで次のように選択します。 **Windows デスクトップ ウィザード**します。 入力`MathLibrary`で、**名前**ボックスは、プロジェクトの名前を指定します。

   ![MathLibrary プロジェクト](media/mathlibrary-new-project-name-153.png "MathLibrary プロジェクトの名前")

1. 選択、 **OK**を閉じる、**新しいプロジェクト**ダイアログと開始、 **Windows デスクトップ プロジェクト**ウィザード。

1. **Windows デスクトップ プロジェクト**ウィザードの **アプリケーションの種類**、**ダイナミック リンク ライブラリ (.dll)** します。

   ![Windows デスクトップ プロジェクト ウィザードで DLL を作成する](media/mathlibrary-desktop-project-wizard-dll.png "Windows デスクトップ プロジェクト ウィザードで DLL を作成します。")

1. **[OK]** ボタンを選択すると、プロジェクトが作成されます。

> [!NOTE]
> 追加の手順では、Visual Studio 2017 バージョン 15.3 で問題を修正する必要があります。 次の手順を実行するかどうかは、この変更を行う必要があります。 を参照してください。
>
>1. **ソリューション エクスプ ローラー**は既にオンになっている場合、 **MathLibrary**プロジェクト**ソリューション 'MathLibrary'** します。
>
>1. メニュー バーで、**[プロジェクト]**  >  **[プロパティ]** を選択します。
>
>1. 左側のウィンドウで、**プロパティ ページ**ダイアログ ボックスで、 **プリプロセッサ** **構成プロパティ** > **C/C++**. 内容を確認して、**プリプロセッサの定義**プロパティ。<br/><br/>![プリプロセッサの定義のプロパティをチェック](media/mathlibrary-153bug-preprocessor-definitions-check.png "プリプロセッサの定義のプロパティを確認してください。")<br/><br/>表示された場合**MATHLIBRARY&#95;エクスポート**で、**プリプロセッサの定義**何も変更する必要はありませんし、一覧表示します。 表示された場合**MathLibrary&#95;エクスポート**代わりに、これらの手順を実行し、続行します。
>
>1. 上部にある、**プロパティ ページ**ダイアログ ボックスで、変更、**構成**ドロップダウンを**すべて構成**します。
>
>1. プロパティ ペインで、編集ボックスの横にあるドロップダウン コントロールを選択します。**プリプロセッサの定義**を選び、**編集**します。<br/><br/>![プリプロセッサの定義のプロパティを編集](media/mathlibrary-153bug-preprocessor-definitions-property.png "プリプロセッサの定義のプロパティの編集")
>
>1. 上部のペインで、**プリプロセッサの定義**ダイアログ ボックスで、新しいシンボルの場合は、追加`MATHLIBRARY_EXPORTS`します。<br/><br/>![MATHLIBRARY_EXPORTS シンボル](media/mathlibrary-153bug-preprocessor-definitions-dialog.png "MATHLIBRARY_EXPORTS 記号を追加します。")
>
>1. 選択 **[ok]** を閉じます、**プリプロセッサの定義**ダイアログ ボックスで、選択し**OK**プロジェクト プロパティに変更を保存します。

### <a name="to-create-a-dll-project-in-older-versions-of-visual-studio"></a>古いバージョンの Visual Studio で DLL プロジェクトを作成するには

1. メニュー バーで、**[ファイル]**  >  **[新規作成]**  >  **[プロジェクト]** を選択します。

1. 左側のウィンドウで、**新しいプロジェクト** ダイアログ ボックスで、展開**インストール済み** > **テンプレート**、選び**Visual C**と中央のウィンドウで選択して**Win32 コンソール アプリケーション**します。 入力`MathLibrary`で、**名前**編集ボックスに、プロジェクトの名前を指定します。

   ![MathLibrary プロジェクト](media/mathlibrary-project-name.png "MathLibrary プロジェクトの名前")

1. 選択、 **OK**を閉じる、**新しいプロジェクト**ダイアログと開始、 **Win32 アプリケーション ウィザード**します。

   ![Win32 アプリケーション ウィザード概要](media/mathlibrary-project-wizard-1.png "Win32 アプリケーション ウィザードの概要")

1. **[次へ]** ボタンをクリックします。 **アプリケーション設定**] ページ [**アプリケーションの種類**を選択します**DLL**します。

   ![Win32 アプリケーション ウィザードで DLL を作成する](media/mathlibrary-project-wizard-2.png "Win32 アプリケーション ウィザード内の DLL の作成")

1. **[完了]** をクリックすると、プロジェクトが作成されます。

ウィザードでは、ソリューションが完了したらで生成されたプロジェクトおよびソース ファイルを確認できます、**ソリューション エクスプ ローラー** Visual Studio のウィンドウ。

![Visual Studio でソリューションを生成](media/mathlibrary-solution-explorer-153.png "Visual Studio でソリューションを生成")

右ここで、この DLL 非常にほとんど意味がありません。 DLL 関数を宣言するヘッダー ファイルを作成する次に、エクスポートすると、しやすく DLL に関数定義を追加します。

### <a name="to-add-a-header-file-to-the-dll"></a>ヘッダー ファイル、DLL を追加するには

1. メニュー バーで、関数では、ヘッダー ファイルを作成するには、選択**プロジェクト** > **新しい項目の追加**します。

1. **新しい項目の追加**ダイアログ ボックスで、左側のウィンドウで、 **Visual C**します。 中央のウィンドウで、 **[ヘッダー ファイル (.h)]** をクリックします。 指定`MathLibrary.h`ヘッダー ファイルの名前として。

   ![[新しい項目の追加] ダイアログ ボックスのヘッダーの追加](media/mathlibrary-add-new-item-header-file.png "新しい項目の追加 ダイアログ ボックスのヘッダー ファイルの追加")

1. 選択、**追加**新しいエディター ウィンドウに表示される空白のヘッダー ファイルを生成するボタンをクリックします。

   ![エディターで空の MathLibrary.h ファイル](media/edit-empty-mathlibrary-header.png "エディターで空 MathLibrary.h ファイル")

1. このコードでは、ヘッダー ファイルの内容を置き換えます。

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

このヘッダー ファイルは、一般化されたフィボナッチ シーケンスでは、指定した 2 つの初期値を生成するいくつかの関数を宣言します。 呼び出し`fibonacci_init(1, 1)`使い慣れたフィボナッチ数のシーケンスを生成します。

プリプロセッサ ステートメントは、ファイルの上部にあることを確認します。 既定では、dll の場合、新しいプロジェクト テンプレートを追加します **<em>PROJECTNAME</em>&#95;エクスポート**DLL プロジェクトの定義済みプリプロセッサ マクロにします。 この例では、Visual Studio 定義**MATHLIBRARY&#95;エクスポート**MathLibrary DLL プロジェクトのビルド時。 (Visual Studio 2017 バージョン 15.3 でウィザードはありません。 このシンボルの定義を大文字に変換します。 "MathLibrary"プロジェクトの名前を付けるかどうかは、定義されたシンボルは MathLibrary&#95;MATHLIBRARY ではなくエクスポート&#95;エクスポートします。 That's 理由はこのシンボルを追加するのには、上の余分な手順があります)。

ときに、 **MATHLIBRARY&#95;エクスポート**マクロが定義されている、 **MATHLIBRARY&#95;API**マクロのセット、`__declspec(dllexport)`関数宣言に修飾子。 この修飾子は、コンパイラとリンカー関数または変数は、他のアプリケーションで使用できるように、DLL からエクスポートするように指示します。 ときに**MATHLIBRARY&#95;エクスポート**は、たとえば、クライアント アプリケーションで、ヘッダー ファイルが含まれている場合**MATHLIBRARY&#95;API**適用、`__declspec(dllimport)`修飾子を宣言。 この修飾子は、関数または変数で、アプリケーションのインポートを最適化します。 詳細については、次を参照してください。 [dllexport、dllimport](../cpp/dllexport-dllimport.md)します。

### <a name="to-add-an-implementation-to-the-dll"></a>DLL に実装を追加するには

1. エディター ウィンドウでタブを選択**MathLibrary.cpp**既に開いている場合。 ない場合で**ソリューション エクスプ ローラー**、オープン**MathLibrary.cpp**で、**ソース ファイル**のフォルダー、 **MathLibrary**プロジェクト。

1. エディターで、MathLibrary.cpp ファイルの内容を次のコードに置き換えます。

   ```cpp
   // MathLibrary.cpp : Defines the exported functions for the DLL.
   #include "stdafx.h"
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

これまでにすべて動作することを確認するには、ダイナミック リンク ライブラリをコンパイルします。 をコンパイルするには、選択**ビルド** > **ソリューションのビルド**メニュー バーでします。 出力は、ようになります。

```Output
1>------ Build started: Project: MathLibrary, Configuration: Debug Win32 ------
1>stdafx.cpp
1>MathLibrary.cpp
1>dllmain.cpp
1>Generating Code...
1>   Creating library C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.lib and object C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.exp
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.dll
1>MathLibrary.vcxproj -> C:\Users\username\Source\Repos\MathLibrary\Debug\MathLibrary.pdb (Partial PDB)
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

これで、Visual C を使用して DLL を作成しました。 次に、DLL によってエクスポートされた関数を使用するクライアント アプリを作成します。

## <a name="create-a-client-app-that-uses-the-dll"></a>DLL を使用するクライアント アプリを作成します。

DLL を作成するときに、DLL を使用する方法について考える必要があります。 DLL によってエクスポートされた関数を呼び出すコードをコンパイルするには、クライアントのソース コードで宣言を含める必要があります。 これらの DLL 関数の呼び出しが解決された場合、リンク時に、リンカーがいる必要があります、*ライブラリをインポート*Windows の実際のコードではなく、関数を検索する方法についての情報を含む特別なライブラリ ファイル。 実行時に、DLL をオペレーティング システムを検索する場所に、クライアントで利用できるにある必要があります。

DLL を使用するかどうか、所有またはサード パーティ製の DLL では、クライアント アプリ プロジェクトの必要があります検索にエクスポートする DLL を宣言するヘッダーと、リンカー、および DLL 自体用インポート ライブラリ。 1 つの方法では、これらすべてのファイルをクライアント プロジェクトにコピーします。 クライアントの開発中に変更する可能性があるサードパーティ製の Dll、このメソッドがそれらを使用する最善の方法で可能性があります。 ただしもに、DLL をビルドするときに重複を避けることをお勧めします。 開発中の DLL ファイルのコピーを作成する場合で 1 つのコピーがない他のヘッダー ファイルを変更または期限切れのライブラリを使用して誤って可能性があります。 この問題を回避するには、DLL プロジェクトから DLL のヘッダー ファイルをインクルードして、クライアント プロジェクトにインクルード パスを設定するをお勧めします。 また、DLL プロジェクトから DLL インポート ライブラリをインクルードするクライアント プロジェクトにライブラリ パスを設定します。 最後に、DLL プロジェクトからビルド出力ディレクトリにビルドされた DLL をコピーします。 この手順は、クライアント アプリをビルドする DLL の同じコードを使用できます。

### <a name="to-create-a-client-app-in-visual-studio-2017-version-153-or-later"></a>15.3 以降、Visual Studio 2017 バージョンでクライアント アプリを作成するには

1. メニュー バーで、作成した DLL を使用する C++ アプリを作成する次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

1. 左側のウィンドウで、**新しいプロジェクト**ダイアログ ボックスで、 **Windows デスクトップ**  **インストール済み** > **Visual C**します。 中央のウィンドウで次のように選択します。 **Windows デスクトップ ウィザード**します。 プロジェクトの名前を指定`MathClient`の**名前**編集ボックス。

   ![クライアント プロジェクトに名前を](media/mathclient-new-project-name-153.png "クライアント プロジェクトの名前")

1. 選択**OK**を開始する、 **Windows デスクトップ プロジェクト**ウィザード。 ウィザードで、次のように選択します。 **OK**クライアント アプリ プロジェクトを作成します。

### <a name="to-create-a-client-app-in-older-versions-of-visual-studio-2017"></a>Visual Studio 2017 の以前のバージョンでクライアント アプリを作成するには

1. メニュー バーで、作成した DLL を使用する C++ アプリを作成する次のように選択します。**ファイル** > **新規** > **プロジェクト**します。

1. 左側のウィンドウで、**新しいプロジェクト**ダイアログ ボックスで、 **Win32** **インストール済み** > **テンプレート** > **Visual C**します。 中央のウィンドウで **[Win32 コンソール アプリケーション]** をクリックします。 プロジェクトの名前を指定`MathClient`の**名前**編集ボックス。

   ![クライアント プロジェクトに名前を](media/mathclient-project-name.png "クライアント プロジェクトの名前")

1. 選択、 **OK**を閉じる、**新しいプロジェクト**ダイアログと開始、 **Win32 アプリケーション ウィザード**します。 **[Win32 アプリケーション ウィザード]** ダイアログ ボックスの **[概要]** ページで、 **[次へ]** をクリックします。

1. **アプリケーション設定**] ページ [**アプリケーションの種類**を選択します**コンソール アプリケーション**が選択されていない場合。

1. **[完了]** をクリックすると、プロジェクトが作成されます。

ウィザードが完了したら、最小限のコンソール アプリケーション プロジェクトが作成されます。 メインのソース ファイルの名前は、以前に入力したプロジェクト名と同じです。 この例では、名前付き**MathClient.cpp**します。 それをビルドすることができますが、まだ、DLL は使用されません。

次に、MathLibrary 関数を呼び出すソース コードで、プロジェクトが MathLibrary.h ファイルを含める必要があります。 クライアント アプリ プロジェクトにこのヘッダー ファイルをコピーし、既存のアイテムとしてプロジェクトに追加する可能性があります。 このメソッドは、サードパーティ製のライブラリに最適にできます。 ただしでの作業コード DLL のと同時に、クライアントとして場合、もう一方に表示されない 1 つのヘッダー ファイル内の変更を生じる可能性があります。 この問題を回避するには、変更、**追加のインクルード ディレクトリ**を元のヘッダーへのパスを含めるプロジェクト内のパス。

### <a name="to-add-the-dll-header-to-your-include-path"></a>DLL のヘッダーを追加する、パスを含める

1. 開く、**プロパティ ページ**の ダイアログ ボックス、 **MathClient**プロジェクト。

1. **構成**ドロップダウン ボックスで、**すべて構成**が選択されていない場合。

1. 左側のウィンドウで次のように選択します。**全般**  **構成プロパティ** > **c/c++** します。

1. プロパティ ペインで場合は、横にドロップダウン コントロールを選択して、**追加のインクルード ディレクトリ**エディット ボックスを選び、**編集**します。

   ![追加のインクルード ディレクトリ プロパティを編集](media/mathclient-additional-include-directories-property.png "追加のインクルード ディレクトリ プロパティの編集")

1. 上部のペインをダブルクリックして、**追加のインクルード ディレクトリ**エディット コントロールを有効にする ダイアログ ボックス。

1. エディット コントロールでの場所へのパスを指定します、 **MathLibrary.h**ヘッダー ファイル。 この場合、相対パスを使用できます。

   `..\..\MathLibrary\MathLibrary`

   ![ヘッダーの場所を追加のインクルード ディレクトリのプロパティに追加](media/mathclient-additional-include-directories.png "ヘッダーの場所を追加のインクルード ディレクトリのプロパティに追加")

1. ヘッダー ファイルへのパスを入力すると、**追加のインクルード ディレクトリ** ダイアログ ボックスで、選択、 **OK**に戻る ボタン、**プロパティ ページ**ダイアログ ボックスと選択し、 **OK**ボタンをクリックして変更を保存します。

ここで含めることができます、 **MathLibrary.h**ファイルを開き、クライアント アプリケーションで宣言する関数を使用します。 内容を置き換える**MathClient.cpp**このコードを使用しています。

```cpp
// MathClient.cpp : Client app for MathLibrary DLL.
#include "pch.h"
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

このコードをコンパイルするがリンクされていない、リンカーは、まだアプリをビルドするために必要なインポート ライブラリを検出できないため、ことができます。 リンカーは、正常にリンクする MathLibrary.lib ファイルを見つける必要があります。 設定して、ビルドに MathLibrary.lib ファイルを追加、**追加の依存関係**プロパティ。 ここでも、クライアント アプリ プロジェクトにライブラリ ファイルをコピーできますが、もう一方に表示されない 1 つのコピーでの変更が生じる可能性があります、ライブラリと、クライアント アプリの両方が開発中にある場合は。 この問題を回避するには、変更、**追加のライブラリ ディレクトリ**をリンクするときに、元のライブラリへのパスを含めるプロジェクト内のパス。

### <a name="to-add-the-dll-import-library-to-your-project"></a>DLL インポート ライブラリをプロジェクトに追加するには

1. 開く、**プロパティ ページ**の ダイアログ ボックス、 **MathClient**プロジェクト。

1. **構成**ドロップダウン ボックスで、**すべて構成**が選択されていない場合。

1. 左側のウィンドウで次のように選択します。**入力**  **構成プロパティ** > **リンカー**します。 プロパティ ペインで場合は、横にドロップダウン コントロールを選択して、**追加の依存関係**エディット ボックスを選び、**編集**します。

   ![追加の依存関係プロパティの編集](media/mathclient-additional-dependencies-property.png "追加の依存関係プロパティの編集")

1. **追加の依存関係**ダイアログ ボックスで、追加`MathLibrary.lib`上部の一覧にコントロールを編集します。

   ![ライブラリ依存関係を追加](media/mathclient-additional-dependencies.png "ライブラリ依存関係の追加")

1. 選択**OK**に戻る、**プロパティ ページ** ダイアログ ボックス。

1. 左側のウィンドウで次のように選択します。**全般**  **構成プロパティ** > **リンカー**します。 プロパティ ペインで場合は、横にドロップダウン コントロールを選択して、**追加のライブラリ ディレクトリ**エディット ボックスを選び、**編集**します。

   ![追加のライブラリ ディレクトリ プロパティを編集](media/mathclient-additional-library-directories-property.png "追加のライブラリ ディレクトリ プロパティの編集")

1. 上部のペインをダブルクリックして、**追加のライブラリ ディレクトリ**エディット コントロールを有効にする ダイアログ ボックス。 エディット コントロールでの場所へのパスを指定します、 **MathLibrary.lib**ファイル。 デバッグとリリースの両方に対して機能を構築するマクロを使用するには、この値を入力します。

   `..\..\MathLibrary\$(IntDir)`

   ![ライブラリ ディレクトリを追加](media/mathclient-additional-library-directories.png "ライブラリ ディレクトリを追加")

1. 内のライブラリ ファイルへのパスを入力すると、**追加のライブラリ ディレクトリ** ダイアログ ボックスで、選択、 **OK**に戻る ボタン、**プロパティ ページ** ダイアログ ボックス。

クライアント アプリをコンパイルおよびリンクが正常がまだがないすべてのものを実行する必要があります。 オペレーティング システムでは、アプリが読み込まれたら、MathLibrary DLL を検索します。 特定のシステム ディレクトリ、環境のパスまたはローカル アプリケーション ディレクトリに DLL が見つからない、負荷が失敗します。 この問題を回避する方法の 1 つでは、DLL をビルド プロセスの一環として、クライアント実行可能ファイルを格納するディレクトリにコピーします。 DLL をコピーするには、追加することができます、**ビルド後イベント**をプロジェクトにコマンドを追加するをコピーする DLL にビルド出力ディレクトリにします。 不足しているかが変更されたを使用してマクロとの間の構成のデバッグ、または製品の正しい場所にコピーする場合にのみ、ここで指定したコマンドは、DLL をコピーします。

### <a name="to-copy-the-dll-in-a-post-build-event"></a>ビルド後イベントの DLL をコピーするには

1. 開く、**プロパティ ページ**の ダイアログ ボックス、 **MathClient**まだ開いていない場合のプロジェクトします。

1. 構成のドロップダウン ボックスで、次のように選択します。**すべて構成**が選択されていない場合。

1. 左側のウィンドウで次のように選択します。**ビルド後イベント** **構成プロパティ**  >  **ビルド イベント** します。

1. プロパティ ペインでのエディット コントロールを選択、**コマンド ライン**フィールドし、このコマンドを入力します。

   `xcopy /y /d "..\..\MathLibrary\$(IntDir)MathLibrary.dll" "$(OutDir)"`

   ![ビルド後のコマンドを追加](media/mathclient-post-build-command-line.png "ビルド後コマンドの追加")

1. 選択、 **OK**プロジェクト プロパティに変更を保存するボタンをクリックします。

クライアント アプリになりましたをビルドして実行する必要があるすべてのものです。 選択して、アプリケーションをビルド**ビルド** > **ソリューションのビルド**メニュー バーでします。 **出力**よう Visual Studio のウィンドウがあります。

```Output
1>------ Build started: Project: MathClient, Configuration: Debug Win32 ------
1>pch.cpp
1>MathClient.cpp
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.exe
1>MathClient.vcxproj -> C:\Users\username\Source\Repos\MathClient\Debug\MathClient.pdb (Partial PDB)
1>1 File(s) copied
========== Build: 1 succeeded, 0 failed, 0 up-to-date, 0 skipped ==========
```

これで、DLL で関数を呼び出すアプリケーションを作成しました。 アプリケーションでそれが何を実行するようになりました。 メニュー バーで、**デバッグ** > **デバッグなしで開始**します。 Visual Studio では、プログラムで実行するコマンド ウィンドウを開きます。 出力の最後の部分のようになります。

![デバッグなしで開始クライアント アプリ](media/mathclient-run-without-debugging.png "デバッグなしで開始クライアント アプリ")

コマンド ウィンドウを消去する任意のキーを押します。

DLL とクライアント アプリケーションを作成するので、実験できます。 クライアント アプリのコードにブレークポイントを設定してくださいし、デバッガーでアプリを実行します。 ライブラリの呼び出しにステップ インするときの動作を参照してください。 ライブラリに他の関数を追加するか、DLL を使用する別のクライアント アプリを作成します。

アプリを展開するときにも使用して Dll を展開する必要があります。 サードパーティ製の Dll をビルドする、または含めることをアプリが使用できるようにする最も簡単な方法とも呼ばれる、アプリと同じディレクトリに挿入するには*アプリのローカル展開*します。 配置の詳細については、「 [Deployment in Visual C++](../ide/deployment-in-visual-cpp.md)」を参照してください。

## <a name="see-also"></a>関連項目

[Visual C++ の DLL](../build/dlls-in-visual-cpp.md)<br/>
[デスクトップ アプリケーションの配置](../ide/deploying-native-desktop-applications-visual-cpp.md)<br/>
[チュートリアル: プログラムの配置 (C++)](../ide/walkthrough-deploying-your-program-cpp.md)<br/>
[DLL 関数の Visual Basic アプリケーションからの呼び出し方](../build/calling-dll-functions-from-visual-basic-applications.md)