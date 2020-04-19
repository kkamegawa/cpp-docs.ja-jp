---
title: デスクトップアプリケーション (ビジュアルC++)
ms.date: 07/28/2019
ms.assetid: a020b534-293c-44e2-aa48-516c43ddeb8f
ms.topic: overview
ms.openlocfilehash: 98909097cf791d55f5971a89643839e07b0c60d1
ms.sourcegitcommit: ea9d78dbb93bf3f8841dde93dbc12bd66f6f32ff
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/22/2019
ms.locfileid: "72778507"
---
# <a name="desktop-applications-visual-c"></a>デスクトップアプリケーション (ビジュアルC++)

C++の*デスクトップアプリケーション*は、Windows api の完全なセットにアクセスできるネイティブアプリケーションであり、ウィンドウまたはシステムコンソールで実行されます。 のC++デスクトップアプリケーションは windows 10 を通じて windows xp で実行できます (ただし、windows xp は正式にはサポートされなくなり、その後に導入された windows api は多数あります)。

デスクトップアプリケーションは、Windows 10 を実行する Pc 上でも、XBox、Windows Phone、Surface Hub、およびその他のデバイスでも実行できるユニバーサル Windows プラットフォーム (UWP) アプリとは異なります。 デスクトップと UWP アプリケーションの詳細については、「[テクノロジを選択する](/windows/win32/choose-your-technology)」を参照してください。

## <a name="desktop-bridge"></a>デスクトップブリッジ

Windows 10 では、既存のデスクトップアプリケーションまたは COM オブジェクトを UWP アプリとしてパッケージ化し、タッチなどの UWP 機能を追加したり、最新の Windows API セットから Api を呼び出したりすることができます。 また、UWP アプリを Visual Studio のデスクトップソリューションに追加し、1つのパッケージにまとめてパッケージ化し、Windows Api を使用してそれらの間で通信を行うこともできます。

Visual Studio 2017 バージョン15.4 以降では、Windows アプリケーションパッケージプロジェクトを作成して、既存のデスクトップアプリケーションをパッケージ化する作業を大幅に簡略化できます。 デスクトップアプリケーションで使用するレジストリ呼び出しまたは Api に関していくつかの制限が適用されますが、多くの場合、アプリケーションパッケージで実行中に同様の機能を実現する代替コードパスを作成できます。 詳細については、[デスクトップ ブリッジ](/windows/uwp/porting/desktop-to-uwp-root)に関するページをご覧ください。

## <a name="terminology"></a>用語

- *Win32*アプリケーションは、の windows デスクトップアプリケーションでC++あり、ネイティブな[Windows C api と COM api、またはその両方、または COM api](/windows/win32/apiindex/windows-api-list)と標準ライブラリ api、およびサードパーティのライブラリを使用できます。 ウィンドウで実行される Win32 アプリケーションでは、開発者が Windows プロシージャ関数内で Windows メッセージを明示的に操作する必要があります。 名前にかかわらず、Win32 アプリケーションは、32ビット (x86) または64ビット (x64) のバイナリとしてコンパイルできます。 Visual Studio IDE では、x86 と Win32 という用語は同義です。

- [コンポーネントオブジェクトモデル (COM)](/windows/win32/com/the-component-object-model)は、さまざまな言語で記述されたプログラムが相互に通信できるようにするための仕様です。 多くの Windows コンポーネントは COM オブジェクトとして実装され、オブジェクトの作成、インターフェイスの検出、およびオブジェクトの破棄に関する標準的な COM 規則に従います。  デスクトップアプリケーションからC++ com オブジェクトを使用するのは比較的簡単ですが、独自の com オブジェクトを作成する方がより高度です。 [Active Template Library (ATL)](../atl/atl-com-desktop-components.md)には、COM 開発を簡略化するマクロとヘルパー関数が用意されています。

- MFC アプリケーションは、ユーザーインターフェイスを作成するために[Microsoft Foundation Classes](../mfc/mfc-desktop-applications.md)を使用する Windows デスクトップアプリケーションです。 MFC アプリケーションでは、CRT および標準ライブラリの Api だけでなく、COM コンポーネントを使用することもできます。 MFC には、 C++ウィンドウメッセージループと Windows api に対するオブジェクト指向のシンラッパーが用意されています。 MFC は、多くのユーザーインターフェイスコントロールまたはカスタムユーザーコントロールを持つアプリケーション (特にエンタープライズ型のアプリケーション) の既定の選択肢です。 MFC には、ウィンドウの管理、シリアル化、テキスト操作、印刷、リボンなどの最新のユーザーインターフェイス要素に便利なヘルパークラスが用意されています。 MFC を効果的に使用するには、Win32 に精通している必要があります。

- /Cli アプリケーションまたはコンポーネントは、( C++標準で許可されてC++いるように) 構文の拡張機能を使用して、.Net とネイティブの C++ コードの間の対話を可能にします。 C++  /Cli C++アプリケーションは、ネイティブで実行されるパーツと、.Net 基底クラスライブラリへのアクセスを持つ .NET Framework で実行される部分を持つことができます。 C++または Visual Basic でC++ C#記述されたコードを操作する必要があるネイティブコードがある場合は、/cli を使用することをお勧めします。 これは、ユーザーインターフェイスコードではなく、.NET Dll で使用することを目的としています。 詳細については、「[C++/CLI による .NET プログラミング (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)」を参照してください。

のデスクトップアプリケーションでC++は、C ランタイム (CRT) と標準ライブラリのクラスと関数、COM オブジェクト、および windows API と総称されるパブリック windows 関数を使用できます。 でのC++Windows デスクトップアプリケーションの概要については、「 [Win32 およびC++](/windows/win32/LearnWin32/learn-to-program-for-windows)の概要」を参照してください。

## <a name="in-this-section"></a>このセクションの内容

|Title|説明|
|-----------|-----------------|
|[C++ による Windows コンソール アプリケーション](console-applications-in-visual-cpp.md)|コンソール アプリに関する情報が含まれています。 Win32 (または Win64) コンソール アプリケーションには、独自のウィンドウとメッセージ ループはありません。 コンソール ウィンドウで動作し、入出力はコマンド ラインを使用して扱われます。|
|[チュートリアル: Windows デスクトップ アプリケーション (C++) の作成](walkthrough-creating-windows-desktop-applications-cpp.md)|単純な Windows デスクトップアプリケーションを作成します。|
|[空の Windows デスクトップ アプリケーションの作成](creating-an-empty-windows-desktop-application.md)|既定のファイルを持たない Windows デスクトッププロジェクトを作成する方法。|
|[空の Win32 アプリケーションへのファイルの追加](adding-files-to-an-empty-win32-applications.md)|空のプロジェクトにファイルを追加する方法。|
|[リソース ファイルの操作](working-with-resource-files.md)|画像、アイコン、文字列テーブル、およびその他のリソースをデスクトップアプリケーションに追加する方法。|
|[DirectX を使用してゲームを作成C++するためのリソース ()](resources-for-creating-a-game-using-directx.md)|でC++ゲームを作成するためのコンテンツへのリンク。|
|[チュートリアル: スタティックライブラリの作成と使用](walkthrough-creating-and-using-a-static-library-cpp.md)|.Lib バイナリファイルを作成する方法。|
|[方法: Windows デスクトップ アプリケーションでの Windows 10 SDK の使用](how-to-use-the-windows-10-sdk-in-a-windows-desktop-application.md)|Windows 10 SDK を使用してビルドするプロジェクトの設定手順が示されています。|

## <a name="related-articles"></a>関連トピック

|Title|説明|
|-----------|-----------------|
|[Windows 開発](/windows/win32/index)|Windows API と COM に関する情報が含まれています (一部の Windows API とサードパーティ製 DLL は、COM オブジェクトとして実装されています)。|
|[Hilo: Windows 7 対応 C++ アプリケーションの開発](https://msdn.microsoft.com/library/windows/desktop/ff708696.aspx)|手荷物の受け取り場所に基づくユーザー インターフェイスを作成するために、Windows Animation と Direct2D を使用するリッチ クライアントの Windows デスクトップ アプリケーションを作成する方法について説明します。  このチュートリアルは、Windows 7 以降では更新されていませんが、Win32 プログラミングについて詳しく説明しています。|
|[C++ でプログラミングする Windows の概要](overview-of-windows-programming-in-cpp.md)|でC++の Windows デスクトッププログラミングの主な機能について説明します。|

## <a name="see-also"></a>関連項目

[Visual Studio での C++](../overview/visual-cpp-in-visual-studio.md)
