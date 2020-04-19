---
title: Visual Studio でC++の C/dll の作成
description: Visual Studio C++で dll を作成して使用する理由と方法の概要を説明します。
ms.date: 01/27/2020
helpviewer_keywords:
- executable files [C++]
- dynamic linking [C++]
- linking [C++], dynamic vs. static
- DLLs [C++]
- DLLs [C++], about DLLs
ms.assetid: 5216bca4-51e2-466b-b221-0e3e776056f0
ms.openlocfilehash: 7083924f137fa9283da40404c7d15183e59c0b1c
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821422"
---
# <a name="create-cc-dlls-in-visual-studio"></a>Visual Studio でC++の C/dll の作成

Windows では、ダイナミックリンクライブラリ (DLL) は、関数とリソースの共有ライブラリとして機能する実行可能ファイルの一種です。 動的リンクは、オペレーティングシステムの機能です。 これにより、実行可能ファイルが関数を呼び出したり、別のファイルに格納されているリソースを使用したりできるようになります。 これらの関数とリソースはコンパイルできるだけでなく、これらを使用する実行可能ファイルとは別に配置することができます。

DLL はスタンドアロンの実行可能ファイルではありません。 Dll は、Dll を呼び出すアプリケーションのコンテキストで実行されます。 オペレーティングシステムによって、DLL がアプリケーションのメモリ領域に読み込まれます。 これは、アプリケーションが読み込まれるとき (*暗黙のリンク*)、または実行時にオンデマンドで (*明示的なリンク*)、実行されます。 また、DLL は、実行可能ファイル間で関数とリソースを共有しやすくします。 メモリ内の DLL の内容には、同時に複数のアプリケーションがアクセスできます。

## <a name="differences-between-dynamic-linking-and-static-linking"></a>動的リンクと静的リンクの違い

静的リンクでは、スタティックライブラリ内のすべてのオブジェクトコードが、ビルド時にそれを使用する実行可能ファイルにコピーされます。 動的リンクには、実行時に Windows によって必要な情報のみが含まれ、データ項目または関数を含む DLL を検索して読み込むことができます。 DLL を作成するときに、この情報を含むインポートライブラリも作成します。 DLL を呼び出す実行可能ファイルをビルドすると、リンカーは、インポートライブラリ内のエクスポートされたシンボルを使用して、Windows ローダーのこの情報を格納します。 ローダーが DLL を読み込むと、DLL がアプリケーションのメモリ空間にマップされます。 存在する場合は、dll に必要な初期化を実行するために、`DllMain`の特別な関数が呼び出されます。

<a name="differences-between-applications-and-dlls"></a>

## <a name="differences-between-applications-and-dlls"></a>アプリケーションと Dll の違い

Dll とアプリケーションはどちらも実行可能モジュールですが、いくつかの点で異なります。 最も明白な違いは、DLL を実行できないことです。 システム側から見ると、アプリケーションと DLL には次の 2 つの根本的な違いがあります。

- アプリケーションでは、システム内の複数のインスタンスを同時に実行することができます。 DLL は、インスタンスを1つだけ持つことができます。

- アプリケーションは、プロセスとして読み込むことができます。 スタック、実行スレッド、グローバルメモリ、ファイルハンドル、メッセージキューなどを所有できます。 DLL はこれらを所有することはできません。

<a name="advantages-of-using-dlls"></a>

## <a name="advantages-of-using-dlls"></a>Dll を使用する利点

コードとリソースへの動的リンクには、静的リンクよりもいくつかの利点があります。

- 動的リンクはメモリを節約し、スワップを減らします。 多くのプロセスでは、DLL を同時に使用して、メモリ内の DLL の読み取り専用部分の1つのコピーを共有できます。 これに対し、静的にリンクされたライブラリを使用してビルドされるすべてのアプリケーションには、Windows がメモリに読み込む必要があるライブラリコードの完全なコピーがあります。

- ダイナミックリンクを使用すると、ディスク領域と帯域幅が節約されます。 複数のアプリケーションが、ディスク上の DLL を共有できます。 これに対して、スタティックリンクライブラリを使用してビルドされた各アプリケーションには、その実行可能イメージにリンクされたライブラリコードがあります。 これにより、より多くのディスク領域が使用され、転送に必要な帯域幅が増えます。

- メンテナンス、セキュリティの修正、およびアップグレードが簡単になります。 DLL で共通の関数を使用するアプリケーションでは、バグ修正を実装し、DLL に更新を配置できます。 Dll が更新された場合、それらを使用するアプリケーションを再コンパイルまたは再リンクする必要はありません。 新しい DLL は、デプロイされるとすぐに使用できるようになります。 これに対して、静的にリンクされたオブジェクトコードの修正を行う場合は、それを使用するすべてのアプリケーションを再リンクして再配置する必要があります。

- Dll を使用して、市場でのサポートを提供できます。 たとえば、表示ドライバー DLL を変更して、アプリケーションの出荷時に使用できなかった表示をサポートすることができます。

- 明示的リンクを使用して、実行時に Dll を検出して読み込むことができます。 たとえば、アプリケーションを再構築または再デプロイせずに新しい機能をアプリに追加するアプリケーション拡張機能などです。

- 動的リンクを使用すると、さまざまなプログラミング言語で記述されたアプリケーションのサポートが容易になります。 異なるプログラミング言語で書かれたプログラムでも、関数の呼び出し規則に従う限り、同じ DLL 関数を呼び出すことができます。 プログラムと DLL 関数は、次の方法で互換性がある必要があります。関数の引数がスタックにプッシュされる順序。 関数またはアプリケーションがスタックのクリーンアップを行うかどうか。 また、レジスタで引数が渡されるかどうかを示します。

- 動的リンクは、MFC (Microsoft Foundation Class) クラスを拡張するための機構を提供します。 既存の MFC クラスの派生クラスを作成し、MFC アプリケーションから使用可能な MFC 拡張 DLL に配置できます。

- 動的リンクを使用すると、アプリケーションの国際対応バージョンを簡単に作成できます。 Dll は、ロケール固有のリソースを提供するのに便利な方法です。これにより、アプリケーションの国際対応バージョンを簡単に作成できます。 アプリケーションの多くのローカライズされたバージョンを配布する代わりに、各言語の文字列とイメージを別のリソース DLL に配置することができます。 その後、実行時に、アプリケーションはそのロケールに対応するリソースを読み込むことができます。

Dll を使用する場合の潜在的な欠点は、アプリケーションが自己完結していないことです。 これは、個別の DLL モジュールの存在に依存します。これは、インストールの一部として、展開または検証する必要があります。

## <a name="more-information-on-how-to-create-and-use-dlls"></a>Dll を作成して使用する方法の詳細については、こちらを参照してください。

次の記事では、Visual Studio で C/C++ dll を作成する方法の詳細について説明します。

[チュートリアル: ダイナミックリンクライブラリ (C++) の作成と使用](walkthrough-creating-and-using-a-dynamic-link-library-cpp.md)\
Visual Studio を使用して DLL を作成および使用する方法について説明します。

[Dll の種類](kinds-of-dlls.md)\
ビルドできる各種 DLL に関する情報を提供します。

[DLL に関してよく寄せられる質問](dll-frequently-asked-questions.md)\
DLL に関してよく寄せられる質問への回答を示します。

[実行可能ファイルを DLL にリンク](linking-an-executable-to-a-dll.md)\
DLL との明示的なリンクと暗黙的なリンクについて説明します。

[DLL\ の初期化](run-time-library-behavior.md#initializing-a-dll)
Dll の読み込み時に実行する必要がある DLL 初期化コードについて説明します。

[Dll と Visual C++ランタイムライブラリの動作](run-time-library-behavior.md)\
ランタイムライブラリ DLL のスタートアップシーケンスについて説明します。

[LoadLibrary と AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)\
`LoadLibrary` と `AfxLoadLibrary` を使用して、実行時に DLL に明示的にリンクする方法について説明します。

[GetProcAddress](getprocaddress.md)\
`GetProcAddress` を使用して DLL 内のエクスポート関数のアドレスを取得する方法について説明します。

[FreeLibrary と AfxFreeLibrary](freelibrary-and-afxfreelibrary.md)\
DLL モジュールが不要になったときの `FreeLibrary` と `AfxFreeLibrary` の使用について説明します。

[ダイナミックリンクライブラリの検索順序](/windows/win32/Dlls/dynamic-link-library-search-order)\
Windows オペレーティング システムがシステム上の DLL を検索するために使用する検索パスについて説明します。

[Mfc\ に動的にリンクされるレギュラー MFC DLL のモジュール状態](module-states-of-a-regular-dll-dynamically-linked-to-mfc.md)
MFC に動的にリンクされるレギュラー MFC DLL のモジュールの状態について説明します。

[MFC 拡張 dll](extension-dlls-overview.md)\
既存の MFC クラスから派生した再利用可能なクラスを通常実装する Dll について説明します。

[リソースのみの DLL の作成](creating-a-resource-only-dll.md)\
アイコン、ビットマップ、文字列、ダイアログ ボックスなどのリソースだけを含む、リソースのみの DLL について説明します。

[MFC アプリケーションのローカライズされたリソース: サテライト dll](localized-resources-in-mfc-applications-satellite-dlls.md)\
混合言語にローカライズされるアプリケーションの作成に役立つ、サテライト DLL のサポートを強化します。

\[のインポートとエクスポート](importing-and-exporting.md)
アプリケーションへのパブリック シンボルのインポート、または DLL からの関数のエクスポートについて説明します。

[アクティブなテクノロジと dll](active-technology-and-dlls.md)\
オブジェクト サーバーを DLL 内部に実装できます。

[DLL\ でのオートメーション](automation-in-a-dll.md)
MFC DLL ウィザードの [オートメーション] オプションについて説明します。

[MFC dll の名前付け規則](../mfc/mfc-library-versions.md#mfc-static-library-naming-conventions)\
MFC に含まれる DLL やライブラリに適用される一定の名前付け規則について説明します。

[Visual Basic アプリケーションからの DLL 関数の呼び出し](calling-dll-functions-from-visual-basic-applications.md)\
Visual Basic アプリケーションから DLL 関数を呼び出す方法について説明します。

## <a name="related-sections"></a>関連セクション

[DLL\ の一部としての MFC の使用](../mfc/tn011-using-mfc-as-part-of-a-dll.md)
MFC ライブラリを Windows ダイナミックリンクライブラリの一部として使用できるようにするレギュラー MFC Dll について説明します。

[MFC\ の DLL バージョン](../mfc/tn033-dll-version-of-mfc.md)
Mfcxx.dll と MFCxxD .dll を使用する方法について説明します。ここで、x は MFC バージョン番号であり、mfc アプリケーションと MFC 拡張 Dll との共有ダイナミックリンクライブラリです。
