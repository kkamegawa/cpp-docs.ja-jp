---
title: 再配布する DLL の決定
ms.date: 07/15/2019
helpviewer_keywords:
- redistributing DLLs
- DLLs [C++], redistributing
- dependencies [C++], application deployment and
- application deployment [C++], DLL redistribution
- deploying applications [C++], DLL redistribution
ms.assetid: f7a2cb42-fb48-42ab-abd2-b35e2fd5601a
ms.openlocfilehash: 82fb582cae129b517a96deb3d4a9572ef8370a9d
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894483"
---
# <a name="determining-which-dlls-to-redistribute"></a>再配布する DLL の決定

Visual Studio によって提供されるライブラリ DLL を使用するアプリケーションをビルドする場合、アプリケーションを実行するユーザーもその DLL を自分のコンピューター上に持っている必要があります。 多くのユーザーは Visual Studio をインストールしていないと考えられるので、それらの DLL をユーザーに提供する必要があります。 Visual Studio では、これらの DLL を、アプリケーションのインストーラーに含めることができる*再頒布可能ファイル*として利用できるようにしています。

再頒布可能 DLL をインストーラーに含めやすくするために、DLL はスタンドアロンの*再頒布可能パッケージ*として入手できます。 これらはアーキテクチャ固有の実行可能ファイルであり、集中配置を使用してユーザーのコンピューターに再頒布可能ファイルをインストールします。 Vcredist など\_x86.exe ライブラリをインストール、32 ビットの x86 と x64 の両方のコンピューター、vcredist\_x64.exe x64 の 64 ビット ライブラリをインストールするコンピューター、および vcredist\_ARM.exe ARM 用のライブラリのインストールコンピューター。 Microsoft では Windows Update サービスを利用して、これらのライブラリを個別に更新するため、集中配置をお勧めします。 Visual Studio インストールのコピーに加え、現在の再頒布可能パッケージをダウンロードして利用できます。 現在および以前のツールセットの両方でサポートされる最新の再頒布可能パッケージへのリンクについては、「[最新のサポートされる Visual C++ のダウンロード](https://support.microsoft.com/help/2977003/the-latest-supported-visual-c-downloads)」を参照してください。 以前の特定のバージョンの再頒布可能パッケージは、[Microsoft ダウンロード センター](https://go.microsoft.com/fwlink/p/?LinkId=158431)で "Visual C++ 再頒布可能パッケージ" を検索すると見つけることができます。

配置する再頒布可能パッケージのメジャー バージョン番号は、アプリケーションの作成に使用した Visual Studio ツールセットのバージョンと一致している必要があります。マイナー バージョンは同じかそれ以上である必要があります。 Visual Studio 2017 と Visual Studio 2015 のツールセットのバージョン番号には互換性があります。つまり、Visual Studio 2017 の再頒布可能ファイルは、2015 ツールセットを使用してビルドされたアプリで使用することができます。 互換性があっても、2017 ツールセットを使用してビルドされたアプリでの 2015 の再頒布可能ファイルの使用はサポートされません。 サポートされるのは、ご利用のツールセットのバージョンと同じであるか、それ以降の再頒布可能パッケージの使用のみです。

*マージ モジュール* を使用して、インストーラーに再頒布可能 DLL を含めることもできます。 これらの Microsoft インストーラー モジュールはアプリケーションのインストーラーに含まれており、このインストーラーでインストールされます。 再頒布可能 DLL のマージ モジュールは、Visual Studio インストール ディレクトリの \\VC\\Redist\MSVC\\*バージョン*\\MergeModules\\ の下にあります。 以前のバージョンの Visual Studio では、これらのファイルは \\Program Files または \\Program Files (x86) ディレクトリの Common Files\\Merge Modules サブディレクトリにあります。 これらのファイルの詳細については、「[マージ モジュールを使用したコンポーネントの再配布](redistributing-components-by-using-merge-modules.md)」を参照してください。

個々の再頒布可能 DLL は、Visual Studio のインストールにも含まれています。 既定では、Visual Studio インストール ディレクトリの \\VC\\Redist\\MSVC\\*バージョン* フォルダーにインストールされます。 *バージョン* 番号は、再頒布可能ファイルの 1 つの共有セットの異なるマイナー ビルド番号を表す場合があります。 これらのディレクトリにある、最新バージョンのライブラリ DLL ファイル、再頒布可能パッケージ、またはマージ モジュールを使用してください。 これらのライブラリを、ご利用のアプリケーションと同じディレクトリにインストールすると、ローカル配置でライブラリを使用することができます。 ローカル配置は、配置済みのアプリケーションに更新プログラムを適用する必要があるため、お勧めしません。 再頒布可能パッケージを使用する集中配置をお勧めします。

アプリケーションと共に再配布する必要がある DLL を判断するには、アプリケーションが依存する DLL の完全な一覧を収集します。 これらは通常、リンカーへのインポート ライブラリ入力として一覧表示されます。 既定では、vcruntime やユニバーサル C ランタイム ライブラリ (UCRT) などの特定のライブラリは含まれません。 アプリまたはその依存関係のいずれかで LoadLibrary を使用して動的に DLL を読み込むと、その DLL がリンカーへの入力で一覧表示されない場合があります。 動的に読み込まれた DLL の一覧を収集する方法の 1 つは、「[Visual C++ アプリケーションの依存関係の理解](understanding-the-dependencies-of-a-visual-cpp-application.md)」で説明されているように、ご利用のアプリで Dependency Walker (depends.exe) を実行することです。 残念ながら、このツールは期限が切れており、特定の Dll が見つからないことが報告される場合があります。

依存関係の一覧がある場合は、Microsoft Visual Studio インストール ディレクトリにある Redist.txt ファイルにリンクされている一覧、または Visual Studio のコピーのマイクロソフト ソフトウェア ライセンス条項の「頒布可能コード ファイル」セクションで言及されている再頒布可能 DLL の "再配布リスト" と比較してください。 Visual Studio 2017 については、「[Microsoft Visual Studio 2017 の頒布可能コード (ユーティリティ、機能拡張、および BuildServer ファイルを含む)](https://go.microsoft.com/fwlink/p/?linkid=823098)」を参照してください。 Visual Studio 2015 については、「[Microsoft Visual Studio 2015 および Microsoft Visual Studio 2015 SDK の頒布可能コード (ユーティリティおよび BuildServer ファイルを含む)](https://go.microsoft.com/fwlink/p/?linkid=799794)」を参照してください。 Visual Studio 2013 の一覧は、オンラインで「[Microsoft Visual Studio 2013 および Microsoft Visual Studio 2013 SDK 用頒布可能コード](https://go.microsoft.com/fwlink/p/?LinkId=313603)」から利用できます。

Visual Studio 2015 より前のバージョンの Visual Studio では、C ランタイム ライブラリ (CRT) は msvc*バージョン*.dll に再頒布可能 DLL として含まれていました。 Visual Studio 2015 以降では、CRT の関数は vcruntime と UCRT にリファクタリングされました。 UCRT は、Windows Update で管理される、Windows 10 のシステム コンポーネントになりました。 すべての Windows 10 オペレーティング システムで利用できます。 以前のオペレーティング システムにアプリケーションを配置するには、UCRT も再配布する必要がある場合があります。 以前のバージョンの UCRT は Visual Studio の再頒布可能ファイルに含まれています。これは、まだいずれのバージョンの UCRT もインストールされていない場合にのみ、Windows 10 より前のオペレーティング システムのみにインストールされます。 Microsoft System Update パッケージとしてダウンレベル システム用の UCRT のインストール可能なバージョンについては、Microsoft ダウンロード センターの [Windows 10 ユニバーサル C ランタイム](https://www.microsoft.com/download/details.aspx?id=48234)に関するページを参照してください。

Visual Studio に含まれているすべてのファイルを再配布することはできません。再配布を許可されているのは、Redist.txt またはオンラインの "REDIST list" で指定されているファイルだけです。 アプリケーションのデバッグ バージョンと、各種の Visual C++ デバッグ DLL は、再配布できません。 詳細については、「[配置方法の選択](choosing-a-deployment-method.md)」を参照してください。

次の表に、アプリケーションが依存する可能性がある一部の Visual C++ DLL を示します。

|Visual C++ ライブラリ|説明|対象|
|--------------------------|-----------------|----------------|
|vcruntime*version*.dll|ネイティブ コード用のランタイム ライブラリ|標準の C および C++ 言語の起動と終了サービスを使用するアプリケーション。|
|vccorlib*version*.dll|マネージド コード用のランタイム ライブラリ。|マネージド コード用の C++ 言語サービスを使用するアプリケーション。|
|msvcp*version*.dll および msvcp*version*_*dotnumber*.dll|ネイティブ コード用の C++ 標準ライブラリ。|[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)を使用するアプリケーション。|
|concrt*version*.dll|ネイティブ コード用のコンカレンシー ランタイム ライブラリ。|[コンカレンシー ランタイム](../parallel/concrt/concurrency-runtime.md)を使用するアプリケーション。|
|mfc*version*.dll|MFC (Microsoft Foundation Class) ライブラリ|[MFC ライブラリ](../mfc/mfc-desktop-applications.md)を使用するアプリケーション。|
|mfc*version* *language*.dll|MFC (Microsoft Foundation Classes) ライブラリ リソース。|MFC 用の特定の言語リソースを使用するアプリケーション。|
|mfc*version*u.dll|Unicode をサポートする MFC ライブラリ|[MFC ライブラリ](../mfc/mfc-desktop-applications.md)を使用し、Unicode のサポートを必要とするアプリケーション。|
|mfcmifc80.dll|MFC マネージド インターフェイス ライブラリ|[MFC ライブラリ](../mfc/mfc-desktop-applications.md)と [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)を使用するアプリケーション。|
|mfcm*version*.dll|MFC マネージド ライブラリ|[MFC ライブラリ](../mfc/mfc-desktop-applications.md)と [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)を使用するアプリケーション。|
|mfcm*version*u.dll|Unicode をサポートする MFC マネージド ライブラリ|[MFC ライブラリ](../mfc/mfc-desktop-applications.md)と [Windows フォーム コントロール](/dotnet/framework/winforms/controls/index)を使用し、Unicode のサポートを必要とするアプリケーション。|
|vcamp*version*.dll|ネイティブ コード用の AMP ライブラリ。|[C++ AMP ライブラリ](../parallel/amp/cpp-amp-cpp-accelerated-massive-parallelism.md) コードを使用するアプリケーション。|
|vcomp*version*.dll|ネイティブ コード用の OpenMP ライブラリ。|[C++ OpenMP ライブラリ](../parallel/openmp/openmp-in-visual-cpp.md) コードを使用するアプリケーション。|

> [!NOTE]
> Active Template Library を別の DLL として再配布する必要がなくなりました。 その機能はヘッダーとスタティック ライブラリに移動されました。

アプリケーションと共にこのような DLL を再配布する方法の詳細については、「[Visual C++ ファイルの再配布](redistributing-visual-cpp-files.md)」を参照してください。 例については、「[配置例](deployment-examples.md)」を参照してください。

システム Dll はオペレーティング システムの一部であるため、通常は再配布する必要はありません。 ただし、Microsoft オペレーティング システムの複数のバージョンでアプリケーションを実行する場合など、これが該当しない可能性もあります。 この場合、使用許諾契約書を必ずお読みください。 また、Windows Update や Service Pack を通じて、または Microsoft が提供する再頒布可能パッケージを使用して、システム DLL のアップグレードを試みてください。

## <a name="see-also"></a>関連項目

[配置方法の選択](choosing-a-deployment-method.md)<br/>
[デスクトップ アプリケーションの配置](deploying-native-desktop-applications-visual-cpp.md)
