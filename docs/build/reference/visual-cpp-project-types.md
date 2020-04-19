---
title: Visual C++ プロジェクトの種類
ms.date: 08/13/2019
helpviewer_keywords:
- programs [C++], projects
- project templates [Visual Studio], C++
- TODO comments [C++]
- projects [C++], types
- templates [C++], projects
- applications [C++], projects
- C++ projects, types
ms.assetid: 7337987e-1e7b-4120-9a4b-94f0401f15e7
ms.openlocfilehash: f234f9a05a871fe474b783a68f644cb4f2b1c2e7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498443"
---
# <a name="c-project-templates"></a>C++ プロジェクト テンプレート

Visual Studio プロジェクトテンプレートでは、作成するプロジェクトの種類に適したソースコードファイル、コンパイラオプション`#include` 、メニュー、ツールバー、アイコン、参照、およびステートメントが生成されます。 Visual Studio には、いくつC++かの種類のプロジェクトテンプレートが含まれており、それらの多くに対してウィザードが用意されているため、プロジェクトを作成するときにプロジェクトをカスタマイズできます。 プロジェクトを作成したらすぐにプロジェクトをビルドし、アプリケーションを実行できます。アプリケーションを開発しながら、断続的にビルドすることをお勧めします。

> [!NOTE]
> C++ プロジェクト テンプレートを使用して C 言語プロジェクトを作成できます。 生成されたプロジェクトで、.cpp ファイル名拡張子を持つファイルを検索して .c に変更します。 次に、プロジェクト (ソリューションではない) の **[プロジェクトのプロパティ]** ページで、 **[構成プロパティ]** 、 **[C/C++]** の順に展開し、 **[詳細]** を選択します。 **[コンパイル言語の選択]** 設定を **[C コードとしてコンパイル (/TC)]** に変更します。

## <a name="project-templates"></a>プロジェクト テンプレート

Visual Studio に含まれるプロジェクト テンプレートは、製品のバージョンとインストールされているワークロードによって異なります。 ワークロードを使用C++してデスクトップ開発をインストールした場合、 C++ Visual Studio にはこれらのプロジェクトテンプレートがあります。

### <a name="windows-desktop"></a>Windows デスクトップ

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[Windows コンソール アプリケーション](../../windows/creating-a-console-application.md)|Windows コンソール アプリケーションを作成するためのプロジェクトです。|
|[Windows デスクトップ アプリケーション](../../windows/walkthrough-creating-windows-desktop-applications-cpp.md)|Windows デスクトップ (Win32) アプリケーションを作成するためのプロジェクトです。|
|[ダイナミック リンク ライブラリ](../walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)|ダイナミック リンク ライブラリ (DLL) を作成するためのプロジェクトです。|
|[スタティック ライブラリ](../../windows/walkthrough-creating-and-using-a-static-library-cpp.md)|スタティック ライブラリ (LIB) を作成するためのプロジェクトです。|
|[Windows デスクトップ ウィザード](../../windows/windows-desktop-wizard.md)|追加のオプションを使って Windows デスクトップ アプリケーションとライブラリを作成するためのウィザードです。|

### <a name="general"></a>全般

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|空のプロジェクト|アプリケーション、ライブラリ、DLL を作成するための空のプロジェクトです。 必要なコードやリソースを追加する必要があります。|
|[メイクファイル プロジェクト](creating-a-makefile-project.md)|Windows メイクファイルを Visual Studio プロジェクトにラップするプロジェクト。 (Visual Studio でその他のメイクファイルを開くには、 [[フォルダーを開く](../open-folder-projects-cpp.md)] を使用します。|
|共有アイテム プロジェクト|複数のプロジェクト間でコードファイルまたはリソースファイルを共有するために使用されるプロジェクトです。 このプロジェクトの種類では、実行可能ファイルは生成されません。|

### <a name="atl"></a>[ATL]

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[ATL プロジェクト](../../atl/reference/creating-an-atl-project.md)|Active Template Library を使用するプロジェクトです。|

### <a name="test"></a>テスト

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[ネイティブ単体テスト プロジェクト](/visualstudio/test/writing-unit-tests-for-c-cpp-with-the-microsoft-unit-testing-framework-for-cpp)|ネイティブ C++ 単体テストを含むプロジェクトです。|

### <a name="mfc"></a>MFC

MFC および ATL のサポート コンポーネントを Visual Studio のインストールに追加した場合、これらのプロジェクト テンプレートが Visual Studio に追加されます。

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|[MFC アプリケーション](../../mfc/reference/creating-an-mfc-application.md)|Microsoft Foundation Class (MFC) ライブラリを使用するアプリケーションを作成するためのプロジェクトです。|
|[MFC ActiveX コントロール](../../mfc/reference/creating-an-mfc-activex-control.md)|MFC ライブラリを使用する ActiveX コントロールを作成するためのプロジェクトです。|
|[MFC DLL](../../mfc/reference/creating-an-mfc-dll-project.md)|MFC ライブラリを使うダイナミックリンク ライブラリを作成するためのプロジェクトです。|

### <a name="windows-universal-apps"></a>Windows ユニバーサル アプリ

C++ Windows ユニバーサル プラットフォーム ツール コンポーネントを Visual Studio のインストールに追加した場合、これらのプロジェクト テンプレートが Visual Studio に追加されます。

C++ でのユニバーサル Windows アプリの概要については、「[ユニバーサル Windows アプリ (C++)](../../cppcx/universal-windows-apps-cpp.md)」をご覧ください。

|プロジェクト テンプレート|説明|
|----------------------|-----------------------------|
|空のアプリケーション|定義済みのコントロールまたはレイアウトのない単一ページ ユニバーサル Windows プラットフォーム (UWP) アプリ用のプロジェクトです。|
|DirectX 11 アプリ|DirectX 11 を使用するユニバーサル Windows プラットフォーム アプリ用のプロジェクトです。|
|DirectX 12 アプリ|DirectX 12 を使用するユニバーサル Windows プラットフォーム アプリ用のプロジェクトです。|
|DirectX 11 および XAML アプリ|DirectX 11 と XAML を使用するユニバーサル Windows プラットフォーム アプリ用のプロジェクトです。|
|単体テスト アプリ|ユニバーサル Windows プラットフォーム (UWP) アプリ用の単体テスト アプリを作成するためのプロジェクトです。|
|DLL|ユニバーサル Windows プラットフォーム アプリまたはランタイム コンポーネントで使用できるネイティブ ダイナミック リンク ライブラリ (DLL) 用のプロジェクトです。|
|スタティック ライブラリ|ユニバーサル Windows プラットフォーム アプリまたはランタイム コンポーネントで使用できるネイティブ スタティック リンク ライブラリ (LIB) 用のプロジェクトです。|
|Windows ランタイム コンポーネント|ユニバーサル Windows プラットフォーム アプリが使用できる Windows ランタイム コンポーネント用のプロジェクトです。アプリを記述するプログラミング言語は問いません。|
|Windows アプリケーション パッケージ プロジェクト|デスクトップ アプリケーションのサイドロードまたは Microsoft ストアでの配布を可能にする UWP パッケージを作成するプロジェクトです。|

## <a name="todo-comments"></a>TODO コメント

プロジェクト テンプレートによって生成されたファイルの多くには TODO コメントが含まれています。このコメントは、独自のソース コードを作成できる場所を特定するのに役立ちます。 コードを追加する方法について詳しくは、「[コード ウィザードを使用した機能の追加](../../ide/adding-functionality-with-code-wizards-cpp.md)」および「[リソース ファイルの操作](../../windows/working-with-resource-files.md)」をご覧ください。


