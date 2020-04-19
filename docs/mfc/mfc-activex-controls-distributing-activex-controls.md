---
title: MFC ActiveX コントロール:ActiveX コントロールの配布
ms.date: 09/12/2018
f1_keywords:
- GetWindowsDirectory
- GetSystemDirectory
helpviewer_keywords:
- MFC ActiveX controls [MFC], ANSI or Unicode versions
- RegSvr32.exe
- MFC ActiveX controls [MFC], distributing
- distributing MFC ActiveX controls
- redistributable files, MFC ActiveX controls
- GetSystemDirectory method [MFC]
- registering ActiveX controls
- MSVCRT40.dll
- registry [MFC], registering controls
- LoadLibrary method, registering ActiveX controls
- MFC40U.DLL
- MFC40.DLL
- GetWindowsDirectory method [MFC]
- installing ActiveX controls
- GetProcAddress method, registering ActiveX controls
- MFC ActiveX controls [MFC], installing
- MFC ActiveX controls [MFC], registering
- registering controls
- OLEPRO32.DLL
ms.assetid: cd70ac9b-f613-4879-9e81-6381fdfda2a1
ms.openlocfilehash: 409ace2197396cf7adbd330cfbd891745a23cf53
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392701"
---
# <a name="mfc-activex-controls-distributing-activex-controls"></a>MFC ActiveX コントロール:ActiveX コントロールの配布

この記事では、ActiveX コントロールの再配布に関連するいくつかの問題について説明します。

- [ANSI または Unicode コントロールのバージョン](#_core_ansi_or_unicode_control_versions)

- [ActiveX コントロールと再頒布可能 Dll をインストールします。](#_core_installing_activex_controls_and_redistributable_dlls)

- [コントロールの登録](#_core_registering_controls)

>[!IMPORTANT]
> ActiveX は、新規の開発が使用できないレガシ テクノロジです。 ActiveX の置き換えの最新のテクノロジの詳細については、次を参照してください。 [ActiveX コントロール](activex-controls.md)します。

##  <a name="_core_ansi_or_unicode_control_versions"></a> ANSI または Unicode コントロールのバージョン

コントロール、またはその両方の ANSI または Unicode のバージョンに付属するかどうかを決定する必要があります。 この決定は、ANSI と Unicode 文字セットに固有の移植性の要因に基づきます。

さまざまな Win32 オペレーティング システム間で最大の移植性の ANSI のコントロールは、すべての Win32 オペレーティング システムで機能を許可します。 Unicode のコントロールは、Windows 95 または Windows 98 ではなく Windows nt (version 3.51 以降) のみに動作します。 移植性が重視される場合、ANSI コントロールである場合。 コントロールは、Windows NT でのみ実行は、Unicode コントロールを出荷することができます。 両方を付属し、アプリケーションがユーザーのオペレーティング システムの最も適切なバージョンをインストールすることもできます。

##  <a name="_core_installing_activex_controls_and_redistributable_dlls"></a> ActiveX コントロールと再頒布可能 Dll をインストールします。

ActiveX コントロールを提供するセットアップ プログラムは、Windows ディレクトリの特殊なサブディレクトリを作成し、コントロールのインストールする必要があります。これで OCX ファイル。

> [!NOTE]
>  Windows を使用して、`GetWindowsDirectory`セットアップ プログラムでの API は、Windows ディレクトリの名前を取得します。 サブディレクトリ名を会社または製品の名前から派生することがあります。

セットアップ プログラムは、Windows システム ディレクトリに必要な DLL ファイルを再頒布可能パッケージをインストールする必要があります。 Dll のいずれかが既にユーザーのコンピューターに存在する場合、セットアップ プログラムする必要があります、バージョンをインストールするバージョンとを比較します。 そのバージョン番号が既にインストールされているファイルよりも高い場合にのみ、ファイルを再インストールします。

ActiveX コントロールは、OLE コンテナー アプリケーションでのみ使用できる、ので、コントロールと OLE Dll の完全なセットを配布する必要はありません。 上位のアプリケーション (または、オペレーティング システム自体) が、標準 OLE インストールされている Dll を持つことを想定できます。

##  <a name="_core_registering_controls"></a> コントロールの登録

コントロールを使用できますが、Windows の登録データベースに適切なエントリを作成する必要があります。 一部の ActiveX コントロール コンテナーは、新しいコントロールを登録するユーザーのメニュー項目を提供しますが、この機能は、すべてのコンテナーで使用できない可能性があります。 そのため、セットアップ プログラムがインストールされている場合に、コントロールを登録するようにしたい場合があります。

場合は、代わりに直接コントロールを登録するセットアップ プログラムを記述することができます。

使用して、`LoadLibrary`をコントロールの DLL を読み込む Windows API。 次に、 `GetProcAddress` "DllRegisterServer"関数のアドレスを取得します。 最後に、呼び出し、`DllRegisterServer`関数。 次のコード サンプルでは 1 つの可能なメソッドを`hLib`は、コントロールのハンドルを格納および`lpDllEntryPoint`"DllRegisterServer"関数のアドレスを格納します。

[!code-cpp[NVC_MFC_AxCont#16](../mfc/codesnippet/cpp/mfc-activex-controls-distributing-activex-controls_1.cpp)]

コントロールの直接登録の利点は、する必要はありませんを起動し、別のプロセス (つまり、REGSVR32) を読み込むインストール時間を短縮です。 さらに、登録は、内部のプロセスであるため、セットアップ プログラムがエラーを処理し、外部のプロセスよりも優れていますが予期しない状況のことができます。

> [!NOTE]
>  呼び出す必要がありますが、セットアップ プログラムでは、ActiveX コントロールをインストールする前に`OleInitialize`します。 セットアップ プログラムが完了したら、呼び出す`OleUnitialize`します。 これにより、OLE システム Dll が ActiveX コントロールを登録するための適切な状態であります。

MFCx0.DLL を登録する必要があります。

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)
