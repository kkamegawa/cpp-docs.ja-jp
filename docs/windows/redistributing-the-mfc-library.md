---
title: MFC ライブラリの再配布
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, redistributing
- redistributing MFC library
ms.assetid: 72714ce1-385e-4c1c-afa5-96b03e873866
ms.openlocfilehash: 7b38299bc39ce282769e40e915847b2220ec28ca
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965608"
---
# <a name="redistributing-the-mfc-library"></a>MFC ライブラリの再配布

アプリケーションを MFC ライブラリに動的にリンクする場合は、一致する MFC DLL を再配布する必要があります。 たとえば、ご使用の MFC アプリが、Visual Studio 2015 に付属するバージョンの MFC を使用してビルドされている場合、アプリがナロー文字または Unicode サポートのためにコンパイルされているかに応じて、mfc140.dll または mfc140u.dl を再配布する必要があります。

> [!NOTE]
>  Visual Studio 2015 RTM では、mfc140.dll ファイルは再頒布可能ファイル ディレクトリから除外されました。 代わりに、Visual Studio 2015 で Windows\system32 および Windows\syswow64 ディレクトリにインストールされるバージョンを使用できます。

すべての MFC DLL で共有バージョンの C ランタイム ライブラリ (CRT) が使用されるため、CRT の再配布も必要になる場合があります。 Visual Studio 2015 に付属するバージョンの MFC では、Windows 10 の一部として配布される、ユニバーサル CRT ライブラリが使用されます。 以前のバージョンの Windows で Visual Studio 2015 を使用してビルドされた MFC アプリケーションを実行するには、ユニバーサル CRT を再配布する必要があります。 ユニバーサル CRT をオペレーティング システム コンポーネントとして、またはローカル配置を使用して再配布する方法については、「[Introducing the Universal CRT](https://devblogs.microsoft.com/cppblog/introducing-the-universal-crt/)」 (ユニバーサル CRT の概要) を参照してください。 サポートされているバージョンの Windows での集中配置のために universal CRT をダウンロードするには、「 [windows 10 Universal C Runtime](https://www.microsoft.com/download/details.aspx?id=48234)」を参照してください。 ローカル配置用の再頒布可能なアーキテクチャ固有のバージョンの ucrtbase.dll は、Windows SDK にあります。 Visual Studio では、これらは既定で C:\Program Files (x86)\Windows Kits\10\Redist\ucrt\DLLs\ のアーキテクチャ固有のサブディレクトリにインストールされます。

ご使用のアプリが以前のバージョンの MFC ライブラリを使用してビルドされている場合は、再頒布可能ファイルのディレクトリから一致する CRT DLL を再配布する必要があります。 たとえば、ご使用の MFC アプリケーションが Visual Studio 2013 (vc120) ツールセットを使用してビルドされている場合、msvcr120.dll を再配布する必要があります。 一致する mfc`<version>`u.dll または mfc`<version>`.dll の再配布も必要です。

アプリケーションを MFC に静的にリンクした場合 (つまり、 **[プロパティ ページ]** ダイアログ ボックスの **[全般]** タブの **[スタティック ライブラリで MFC を使用する]** を指定した場合)、MFC DLL を再配布する必要はありません。 静的リンクはアプリケーションのテストや内部での配置を行う場合でも該当しますが、MFC の再配布にはそれを使用しないことをお勧めします。 Visual C++ ライブラリを配置するための推奨される方法の詳細については、「[配置方法の選択](choosing-a-deployment-method.md)」を参照してください。

アプリケーションで WebBrowser コントロールを実装した MFC クラス ([CHtmlView クラス](../mfc/reference/chtmlview-class.md)や [CHtmlEditView クラス](../mfc/reference/chtmleditview-class.md)など) を使用する場合は、ターゲット コンピューターのコモン コントロール ファイルが最新になるように、Microsoft Internet Explorer の最新バージョンをインストールすることもお勧めします。 (少なくとも、Internet Explorer 4.0 が必要です)。Internet Explorer コンポーネントのインストール方法の詳細については、Microsoft サポート web サイトの記事 185375: Internet Explorer の1つの EXE インストールを作成する方法」を参照してください。

アプリケーションで MFC データベース クラス ([CRecordset クラス](../mfc/reference/crecordset-class.md)や [CRecordView クラス](../mfc/reference/crecordview-class.md)など) を使用する場合は、必要な ODBC および ODBC ドライバーを再配布する必要があります。

MFC アプリケーションが Windows フォーム コントロールを使用している場合は、アプリケーションと共に mfcmifc80.dll を再配布する必要があります。 この DLL は厳密な名前で署名された .NET アセンブリです。アプリケーションと共にそのアプリケーションのローカル フォルダーに再配布できます。また、[Gacutil.exe (グローバル アセンブリ キャッシュ ツール)](/dotnet/framework/tools/gacutil-exe-gac-tool) を使用し、グローバル アセンブリ キャッシュ (GAC) に配置して再配布することもできます。

MFC DLL を再配布する場合は、デバッグ バージョンではなく、リテール バージョンを再配布することを確認してください。 DLL のデバッグ バージョンは再配布できません。 MFC DLL のデバッグ バージョンの名前の末尾には "d"が付きます (たとえば、Mfc140d.dll)。

MFC を再配布するには、VCRedist_*アーキテクチャ*.exe、または Visual Studio と共にインストールされるマージ モジュールを使用するか、あるいは MFC DLL をアプリケーションと同じフォルダーに配置します。 MFC を再配布する方法の詳細については、「[Visual C++ ファイルの再配布](redistributing-visual-cpp-files.md)」を参照してください。

## <a name="installation-of-localized-mfc-components"></a>テクニカル ノート 56: ローカライズされた MFC コンポーネントのインストール

MFC ローカリゼーション DLL をインストールしてアプリケーションをローカライズする場合は、再頒布可能マージ ファイル (.msm) を使用する必要があります。 たとえば、アプリケーションを x86 コンピューターでローカライズする場合は、Microsoft_VC`<version>`_MFCLOC_x86.msm を x86 コンピューターのインストール パッケージにマージする必要があります。

再頒布可能 .msm ファイルには、ローカライズに使用される DLL が含まれます。 サポートされているそれぞれの言語に対して、1 つの DLL があります。 これらの DLL は、インストール プロセスによって、ターゲット コンピューターの %windir%\system32\ フォルダーにインストールされます。

MFC アプリケーションのローカライズ方法の詳細については、「[テクニカル ノート 57: MFC コンポーネントのローカライズ](../mfc/tn057-localization-of-mfc-components.md)」を参照してください。

MFC のローカライズ用 DLL を再配布するには、MFC DLL をアプリケーションのローカル フォルダーに配置します。 Visual C++ ライブラリを再配布する方法の詳細については、「[Visual C++ ファイルの再配布](redistributing-visual-cpp-files.md)」を参照してください。

## <a name="see-also"></a>関連項目

[Visual C++ ファイルの再配布](redistributing-visual-cpp-files.md)
