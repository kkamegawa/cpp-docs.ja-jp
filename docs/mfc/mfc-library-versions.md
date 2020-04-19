---
title: MFC ライブラリのバージョン
ms.date: 05/08/2019
helpviewer_keywords:
- class libraries [MFC], building versions
- version information [MFC], MFC library
- MFC class library
- MFC class library, building
- MFC libraries
- MFC, library versions
- libraries [MFC], versions
ms.openlocfilehash: b8e32366d9ff43bd6e5770f64f0ba9d8bf6e56ab
ms.sourcegitcommit: 00e26915924869cd7eb3c971a7d0604388abd316
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2019
ms.locfileid: "65524796"
---
# <a name="mfc-library-versions"></a>MFC ライブラリのバージョン

MFC ライブラリは 1 バイトの ANSI をサポートするバージョンで利用でき、マルチバイト文字セット (MBCS) のコードだけではなく、Unicode (UTF 16LE、Windows ネイティブ文字セットとしてエンコードされます) をサポートするバージョン。 各 MFC バージョンは、共有 DLL またはスタティック ライブラリとして使用できます。 MFC コントロールのサイズを非常に機密性の高い、およびそれらのコントロールは必要ありませんアプリケーション用のダイアログ ボックスが含まれている小さな MFC スタティック ライブラリ バージョンもあります。 MFC ライブラリでは、両方のデバッグで使用可能なし、サポートされているアーキテクチャ x86、x64、および ARM プロセッサを含むのバージョンをリリースします。 両方のアプリケーション (.exe ファイル) を作成して、MFC ライブラリの任意のバージョンの Dll。 マネージ コードとのやり取りのコンパイルされた MFC ライブラリのセットもします。 MFC Dll の共有をライブラリのバイナリの互換性を示すためにバージョン番号が含まれます。

## <a name="automatic-linking-of-mfc-library-versions"></a>MFC ライブラリのバージョンの自動リンク

MFC ヘッダー ファイルには、ビルド環境で定義された値に基づいてリンクには、MFC ライブラリの正しいバージョン自動的に決定します。 MFC ヘッダー ファイルでは、特定のバージョンの MFC ライブラリにリンクする、リンカーに指示するコンパイラ ディレクティブを追加します。

たとえば、AFX です。H ヘッダー ファイル、リンカーは、完全な静的限られた静的、または共有 DLL バージョンの MFC; にリンクするにはANSI/MBCS または Unicode のバージョン。ビルド構成によっては、デバッグ、または製品のバージョン:

```cpp
#ifndef _AFXDLL
    #ifdef _AFX_NO_MFC_CONTROLS_IN_DIALOGS
        #ifdef _DEBUG
            #pragma comment(lib, "afxnmcdd.lib")
        #else
            #pragma comment(lib, "afxnmcd.lib")
        #endif
        #pragma comment(linker, "/include:__afxNoMFCControlSupportInDialogs")
        #pragma comment(linker, "/include:__afxNoMFCControlContainerInDialogs")
    #endif
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "nafxcwd.lib")
        #else
            #pragma comment(lib, "nafxcw.lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "uafxcwd.lib")
        #else
            #pragma comment(lib, "uafxcw.lib")
        #endif
    #endif
#else
    #ifndef _UNICODE
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "d.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "d.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER ".lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER ".lib")
        #endif
    #else
        #ifdef _DEBUG
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "ud.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "ud.lib")
        #else
            #pragma comment(lib, "mfc" _MFC_FILENAME_VER "u.lib")
            #pragma comment(lib, "mfcs" _MFC_FILENAME_VER "u.lib")
        #endif
    #endif
#endif
```

MFC ヘッダー ファイルには、MFC ライブラリ、Win32 ライブラリ、OLE ライブラリ、サンプルから作成された OLE ライブラリ、ODBC ライブラリ、および具合をなど、必要なすべてのライブラリでリンクするディレクティブも含まれます。

## <a name="ansi-mbcs-and-unicode"></a>ANSI、MBCS および Unicode

MFC の ANSI/MBCS バージョンのライブラリは、ASCII などの両方の 1 バイト文字セットをサポートし、Shift JIS などのマルチバイト文字セットします。 Unicode の MFC ライブラリのバージョンでは、その UTF 16LE ワイド文字のエンコードされた形式で Unicode をサポートします。 Utf-8 エンコードの Unicode のサポートは、MFC の ANSI/MBCS ライブラリのバージョンを使用します。

IDE で 1 バイト、マルチバイト、文字またはワイド文字の Unicode 文字列と文字のサポートを使用して、プロジェクトの構成を設定するには、使用、**プロジェクト プロパティ**ダイアログ。 **構成プロパティ** > **全般** ページで、設定、**文字セット**プロパティを**未設定**を使用する、1 バイト文字セットです。 プロパティを設定**マルチ バイト文字セットを使用して**、マルチバイト文字セットを使用するまたは**Unicode 文字セットを使用して**utf-16 としてエンコードされた Unicode を使用します。

MFC プロジェクトは、プリプロセッサ シンボルを使用して\_UNICODE utf-16 ワイド文字の Unicode のサポートを示すために、 \_MBCS を示す MBCS をサポートします。 これらのオプションは、プロジェクトで相互に排他的です。

## <a name="mfc-static-library-naming-conventions"></a>MFC のスタティック ライブラリの名前付け規則

MFC のスタティック ライブラリは、次の命名規則を使用します。 ライブラリ名があるフォーム

> <em>u</em>AFX<em>cd</em>します。LIB

小文字の斜体に示すように文字が、次の表の意味が示すように指定子のプレース ホルダーです。

|指定子|値と意味|
|---------------|-------------------------|
|*u*|(N) を ANSI/MBCS または Unicode (U);ダイアログで MFC コントロールなしのバージョンを省略します。|
|*c*|MFC コントロール (CW) ダイアログ ボックスで、または (NMCD) なしのバージョン|
|*d*|デバッグまたはリリース:D = デバッグ。リリースの指定子を省略します。|

次の表のすべてのライブラリが含まれるビルドがサポートされているアーキテクチャの \atlmfc\lib ディレクトリで事前に作成します。

|ライブラリ|説明|
|-------------|-----------------|
|NAFXCW.LIB|MFC のスタティック リンク ライブラリ、リリース バージョン|
|NAFXCWD.LIB|MFC のスタティック リンク ライブラリ、デバッグ バージョン|
|UAFXCW.LIB|Unicode のサポート、リリース バージョンの MFC のスタティック リンク ライブラリ|
|UAFXCWD.LIB|Unicode のサポート、デバッグ バージョンの MFC のスタティック リンク ライブラリ|
|AFXNMCD します。LIB|MFC のスタティック リンク ライブラリのリリース バージョン、MFC ダイアログ コントロール|
|AFXNMCDD します。LIB|デバッグ バージョン、MFC ダイアログ コントロールの MFC のスタティック リンク ライブラリ|

同じ基本名と .pdb 拡張子を持つファイルをデバッガーでは、各静的ライブラリの入手できます。

## <a name="mfc-shared-dll-naming-conventions"></a>MFC は、DLL の名前付け規則を共有します。

MFC 共有 Dll も構造化された名前付け規則に従ってください。 これにより、簡単にする必要があります目的に使用する DLL やライブラリを確認します。

MFC Dll が*バージョン*バイナリの互換性を示す番号。 その他のライブラリとプロジェクト内での互換性を保証するためにコンパイラ ツールセットと同じバージョンを持つ MFC Dll を使用します。

|[DLL]|説明|
|---------|-----------------|
|MFC*バージョン*します。DLL|MFC DLL、ANSI または MBCS リリース バージョン|
|MFC*バージョン*U.DLL|MFC DLL、Unicode のリリース バージョン|
|MFC*バージョン*D.DLL|MFC DLL、ANSI または MBCS のデバッグ バージョン|
|MFC*バージョン*UD します。DLL|MFC DLL、Unicode のデバッグ バージョン|
|MFCM*バージョン*します。DLL|Windows フォーム コントロールと MFC DLL ANSI または MBCS リリース バージョン|
|MFCM*バージョン*U.DLL|Windows フォーム コントロールと Unicode のリリース バージョンの MFC DLL|
|MFCM*バージョン*D.DLL|Windows フォーム コントロールと MFC DLL ANSI または MBCS のデバッグ バージョン|
|MFCM*version*UD.DLL|Windows フォーム コントロールと Unicode のデバッグ バージョンの MFC DLL|

アプリケーションや MFC 拡張 Dll を使用して、これらの共有 Dll の構築に必要なインポート ライブラリは、DLL と同じ基本名があるが、.lib ファイル名拡張子です。 コードに小さな静的ライブラリ共有 Dll を使用するとリンクも必要があります。このライブラリの名前は MFCS*バージョン*{U} {D} .lib します。

一致する MFC を含める必要がありますが、アプリケーションまたは MFC 拡張 DLL からかどうか、MFC の共有 DLL バージョンにリンクしている動的に場合、*バージョン*します。DLL または MFC*バージョン*U.DLL、製品を展開するときにします。

ビジュアルの一覧についてC++Dll を参照してください、アプリケーションと共に配布できます[Microsoft Visual Studio 2017 および Microsoft Visual Studio 2017 SDK (が含まれていますユーティリティおよび BuildServer ファイルを含む) の再頒布可能コード](/visualstudio/productinfo/2017-redistribution-vs)または[Visual Studio 2019 の再頒布可能コード](/visualstudio/releases/2019/redistribution)します。

MFC の MBCS および Unicode のサポートの詳細については、次を参照してください。 [Unicode およびマルチバイト文字セット (MBCS) のサポート](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md)します。

## <a name="dynamic-link-library-support"></a>ダイナミック リンク ライブラリのサポート

MFC と非 MFC の両方の実行可能ファイルで使用できる Dll を作成するのにか、static または shared 動的 MFC ライブラリを使用できます。 これら「レギュラー」または"レギュラー MFC Dll"とも呼ばれますが、MFC 拡張 Dll だけができると区別するため使用 MFC アプリと MFC Dll。 MFC のスタティック ライブラリを使用してビルドされた DLL とも呼ばれます、USRDLL の古い参照は、MFC DLL プロジェクト プリプロセッサ シンボルを定義するため、  **\_USRDLL**します。 共有 Dll を MFC を使用する DLL とも呼ばれますを AFXDLL の古い参照は、プリプロセッサ シンボルを定義するので、  **\_AFXDLL**します。

MFC のスタティック ライブラリをリンクする DLL プロジェクトを作成するときに、DLL は、MFC Dll を共有することがなく展開できます。 DLL プロジェクトが MFC のインポート ライブラリにリンクするときに*バージョン*します。LIB または MFC*バージョン*U.LIB、一致するデプロイする必要があります MFC DLL の MFC の共有*バージョン*します。DLL または MFC*バージョン*DLL と共に U.DLL します。 詳細については、次を参照してください。 [Dll](../build/dlls-in-visual-cpp.md)します。

## <a name="see-also"></a>関連項目

[MFC の一般的なトピック](../mfc/general-mfc-topics.md)
