---
title: CWinApp クラス
ms.date: 07/15/2019
f1_keywords:
- CWinApp
- AFXWIN/CWinApp
- AFXWIN/CWinApp::CWinApp
- AFXWIN/CWinApp::AddDocTemplate
- AFXWIN/CWinApp::AddToRecentFileList
- AFXWIN/CWinApp::ApplicationRecoveryCallback
- AFXWIN/CWinApp::CloseAllDocuments
- AFXWIN/CWinApp::CreatePrinterDC
- AFXWIN/CWinApp::DelRegTree
- AFXWIN/CWinApp::DoMessageBox
- AFXWIN/CWinApp::DoWaitCursor
- AFXWIN/CWinApp::EnableD2DSupport
- AFXWIN/CWinApp::EnableHtmlHelp
- AFXWIN/CWinApp::EnableTaskbarInteraction
- AFXWIN/CWinApp::ExitInstance
- AFXWIN/CWinApp::GetApplicationRecoveryParameter
- AFXWIN/CWinApp::GetApplicationRecoveryPingInterval
- AFXWIN/CWinApp::GetApplicationRestartFlags
- AFXWIN/CWinApp::GetAppRegistryKey
- AFXWIN/CWinApp::GetDataRecoveryHandler
- AFXWIN/CWinApp::GetFirstDocTemplatePosition
- AFXWIN/CWinApp::GetHelpMode
- AFXWIN/CWinApp::GetNextDocTemplate
- AFXWIN/CWinApp::GetPrinterDeviceDefaults
- AFXWIN/CWinApp::GetProfileBinary
- AFXWIN/CWinApp::GetProfileInt
- AFXWIN/CWinApp::GetProfileString
- AFXWIN/CWinApp::GetSectionKey
- AFXWIN/CWinApp::HideApplication
- AFXWIN/CWinApp::HtmlHelp
- AFXWIN/CWinApp::InitInstance
- AFXWIN/CWinApp::IsTaskbarInteractionEnabled
- AFXWIN/CWinApp::LoadCursor
- AFXWIN/CWinApp::LoadIcon
- AFXWIN/CWinApp::LoadOEMCursor
- AFXWIN/CWinApp::LoadOEMIcon
- AFXWIN/CWinApp::LoadStandardCursor
- AFXWIN/CWinApp::LoadStandardIcon
- AFXWIN/CWinApp::OnDDECommand
- AFXWIN/CWinApp::OnIdle
- AFXWIN/CWinApp::OpenDocumentFile
- AFXWIN/CWinApp::ParseCommandLine
- AFXWIN/CWinApp::PreTranslateMessage
- AFXWIN/CWinApp::ProcessMessageFilter
- AFXWIN/CWinApp::ProcessShellCommand
- AFXWIN/CWinApp::ProcessWndProcException
- AFXWIN/CWinApp::Register
- AFXWIN/CWinApp::RegisterWithRestartManager
- AFXWIN/CWinApp::ReopenPreviousFilesAtRestart
- AFXWIN/CWinApp::RestartInstance
- AFXWIN/CWinApp::RestoreAutosavedFilesAtRestart
- AFXWIN/CWinApp::Run
- AFXWIN/CWinApp::RunAutomated
- AFXWIN/CWinApp::RunEmbedded
- AFXWIN/CWinApp::SaveAllModified
- AFXWIN/CWinApp::SelectPrinter
- AFXWIN/CWinApp::SetHelpMode
- AFXWIN/CWinApp::SupportsApplicationRecovery
- AFXWIN/CWinApp::SupportsAutosaveAtInterval
- AFXWIN/CWinApp::SupportsAutosaveAtRestart
- AFXWIN/CWinApp::SupportsRestartManager
- AFXWIN/CWinApp::Unregister
- AFXWIN/CWinApp::WinHelp
- AFXWIN/CWinApp::WriteProfileBinary
- AFXWIN/CWinApp::WriteProfileInt
- AFXWIN/CWinApp::WriteProfileString
- AFXWIN/CWinApp::EnableShellOpen
- AFXWIN/CWinApp::LoadStdProfileSettings
- AFXWIN/CWinApp::OnContextHelp
- AFXWIN/CWinApp::OnFileNew
- AFXWIN/CWinApp::OnFileOpen
- AFXWIN/CWinApp::OnFilePrintSetup
- AFXWIN/CWinApp::OnHelp
- AFXWIN/CWinApp::OnHelpFinder
- AFXWIN/CWinApp::OnHelpIndex
- AFXWIN/CWinApp::OnHelpUsing
- AFXWIN/CWinApp::RegisterShellFileTypes
- AFXWIN/CWinApp::SetAppID
- AFXWIN/CWinApp::SetRegistryKey
- AFXWIN/CWinApp::UnregisterShellFileTypes
- AFXWIN/CWinApp::m_bHelpMode
- AFXWIN/CWinApp::m_eHelpType
- AFXWIN/CWinApp::m_hInstance
- AFXWIN/CWinApp::m_lpCmdLine
- AFXWIN/CWinApp::m_nCmdShow
- AFXWIN/CWinApp::m_pActiveWnd
- AFXWIN/CWinApp::m_pszAppID
- AFXWIN/CWinApp::m_pszAppName
- AFXWIN/CWinApp::m_pszExeName
- AFXWIN/CWinApp::m_pszHelpFilePath
- AFXWIN/CWinApp::m_pszProfileName
- AFXWIN/CWinApp::m_pszRegistryKey
- AFXWIN/CWinApp::m_dwRestartManagerSupportFlags
- AFXWIN/CWinApp::m_nAutosaveInterval
- AFXWIN/CWinApp::m_pDataRecoveryHandler
helpviewer_keywords:
- CWinApp [MFC], CWinApp
- CWinApp [MFC], AddDocTemplate
- CWinApp [MFC], AddToRecentFileList
- CWinApp [MFC], ApplicationRecoveryCallback
- CWinApp [MFC], CloseAllDocuments
- CWinApp [MFC], CreatePrinterDC
- CWinApp [MFC], DelRegTree
- CWinApp [MFC], DoMessageBox
- CWinApp [MFC], DoWaitCursor
- CWinApp [MFC], EnableD2DSupport
- CWinApp [MFC], EnableHtmlHelp
- CWinApp [MFC], EnableTaskbarInteraction
- CWinApp [MFC], ExitInstance
- CWinApp [MFC], GetApplicationRecoveryParameter
- CWinApp [MFC], GetApplicationRecoveryPingInterval
- CWinApp [MFC], GetApplicationRestartFlags
- CWinApp [MFC], GetAppRegistryKey
- CWinApp [MFC], GetDataRecoveryHandler
- CWinApp [MFC], GetFirstDocTemplatePosition
- CWinApp [MFC], GetHelpMode
- CWinApp [MFC], GetNextDocTemplate
- CWinApp [MFC], GetPrinterDeviceDefaults
- CWinApp [MFC], GetProfileBinary
- CWinApp [MFC], GetProfileInt
- CWinApp [MFC], GetProfileString
- CWinApp [MFC], GetSectionKey
- CWinApp [MFC], HideApplication
- CWinApp [MFC], HtmlHelp
- CWinApp [MFC], InitInstance
- CWinApp [MFC], IsTaskbarInteractionEnabled
- CWinApp [MFC], LoadCursor
- CWinApp [MFC], LoadIcon
- CWinApp [MFC], LoadOEMCursor
- CWinApp [MFC], LoadOEMIcon
- CWinApp [MFC], LoadStandardCursor
- CWinApp [MFC], LoadStandardIcon
- CWinApp [MFC], OnDDECommand
- CWinApp [MFC], OnIdle
- CWinApp [MFC], OpenDocumentFile
- CWinApp [MFC], ParseCommandLine
- CWinApp [MFC], PreTranslateMessage
- CWinApp [MFC], ProcessMessageFilter
- CWinApp [MFC], ProcessShellCommand
- CWinApp [MFC], ProcessWndProcException
- CWinApp [MFC], Register
- CWinApp [MFC], RegisterWithRestartManager
- CWinApp [MFC], ReopenPreviousFilesAtRestart
- CWinApp [MFC], RestartInstance
- CWinApp [MFC], RestoreAutosavedFilesAtRestart
- CWinApp [MFC], Run
- CWinApp [MFC], RunAutomated
- CWinApp [MFC], RunEmbedded
- CWinApp [MFC], SaveAllModified
- CWinApp [MFC], SelectPrinter
- CWinApp [MFC], SetHelpMode
- CWinApp [MFC], SupportsApplicationRecovery
- CWinApp [MFC], SupportsAutosaveAtInterval
- CWinApp [MFC], SupportsAutosaveAtRestart
- CWinApp [MFC], SupportsRestartManager
- CWinApp [MFC], Unregister
- CWinApp [MFC], WinHelp
- CWinApp [MFC], WriteProfileBinary
- CWinApp [MFC], WriteProfileInt
- CWinApp [MFC], WriteProfileString
- CWinApp [MFC], EnableShellOpen
- CWinApp [MFC], LoadStdProfileSettings
- CWinApp [MFC], OnContextHelp
- CWinApp [MFC], OnFileNew
- CWinApp [MFC], OnFileOpen
- CWinApp [MFC], OnFilePrintSetup
- CWinApp [MFC], OnHelp
- CWinApp [MFC], OnHelpFinder
- CWinApp [MFC], OnHelpIndex
- CWinApp [MFC], OnHelpUsing
- CWinApp [MFC], RegisterShellFileTypes
- CWinApp [MFC], SetAppID
- CWinApp [MFC], SetRegistryKey
- CWinApp [MFC], UnregisterShellFileTypes
- CWinApp [MFC], m_bHelpMode
- CWinApp [MFC], m_eHelpType
- CWinApp [MFC], m_hInstance
- CWinApp [MFC], m_lpCmdLine
- CWinApp [MFC], m_nCmdShow
- CWinApp [MFC], m_pActiveWnd
- CWinApp [MFC], m_pszAppID
- CWinApp [MFC], m_pszAppName
- CWinApp [MFC], m_pszExeName
- CWinApp [MFC], m_pszHelpFilePath
- CWinApp [MFC], m_pszProfileName
- CWinApp [MFC], m_pszRegistryKey
- CWinApp [MFC], m_dwRestartManagerSupportFlags
- CWinApp [MFC], m_nAutosaveInterval
- CWinApp [MFC], m_pDataRecoveryHandler
ms.assetid: e426a3cd-0d15-40d6-bd55-beaa5feb2343
ms.openlocfilehash: e65ad8b5d8b14ff747adc55b517d9e695d9cbb66
ms.sourcegitcommit: 2f96e2fda591d7b1b28842b2ea24e6297bcc3622
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/18/2019
ms.locfileid: "71095757"
---
# <a name="cwinapp-class"></a>CWinApp クラス

Windows のアプリケーション オブジェクトを派生させるための基底クラスです。

## <a name="syntax"></a>構文

```
class CWinApp : public CWinThread
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CWinApp:: CWinApp](#cwinapp)|`CWinApp` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CWinApp::、Adddoctemplate](#adddoctemplate)|アプリケーションの利用可能なドキュメントテンプレートの一覧にドキュメントテンプレートを追加します。|
|[CWinApp::AddToRecentFileList](#addtorecentfilelist)|最近使用した (MRU) ファイルの一覧にファイル名を追加します。|
|[CWinApp::ApplicationRecoveryCallback](#applicationrecoverycallback)|アプリケーションが予期せず終了したときにフレームワークによって呼び出されます。|
|[CWinApp:: CloseAllDocuments](#closealldocuments)|開いているすべてのドキュメントを閉じます。|
|[CWinApp::CreatePrinterDC](#createprinterdc)|プリンターデバイスコンテキストを作成します。|
|[CWinApp::DelRegTree](#delregtree)|指定されたキーとそのすべてのサブキーを削除します。|
|[CWinApp::D oMessageBox](#domessagebox)|アプリケーションの[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)を実装します。|
|[CWinApp::D oWaitCursor](#dowaitcursor)|待機カーソルをオンまたはオフにします。|
|[CWinApp::EnableD2DSupport](#enabled2dsupport)|Application D2D のサポートを有効にします。 このメソッドは、メイン ウィンドウが初期化される前に呼び出します。|
|[CWinApp:: EnableHtmlHelp](#enablehtmlhelp)|WinHelp ではなく、アプリケーションの Html ヘルプを実装します。|
|[CWinApp::EnableTaskbarInteraction](#enabletaskbarinteraction)|タスクバーとの対話を有効にします。|
|[CWinApp:: ExitInstance](#exitinstance)|アプリケーションの終了時にクリーンアップするようにオーバーライドします。|
|[CWinApp::GetApplicationRecoveryParameter](#getapplicationrecoveryparameter)|アプリケーションの回復方法の入力パラメーターを取得します。|
|[CWinApp::GetApplicationRecoveryPingInterval](#getapplicationrecoverypinginterval)|再開マネージャーが復旧コールバック関数から戻るまで待機する時間を返します。|
|[CWinApp:: GetApplicationRestartFlags](#getapplicationrestartflags)|再起動マネージャーのフラグを返します。|
|[CWinApp::GetAppRegistryKey](#getappregistrykey)|HKEY_CURRENT_USER\\"Software" \RegistryKey\ProfileName. のキーを返します|
|[CWinApp:: GetDataRecoveryHandler](#getdatarecoveryhandler)|アプリケーションのこのインスタンスのデータ回復ハンドラーを取得します。|
|[CWinApp:: GetFirstDocTemplatePosition](#getfirstdoctemplateposition)|最初のドキュメントテンプレートの位置を取得します。|
|[CWinApp:: Ge@ Pmode](#gethelpmode)|アプリケーションによって使用されるヘルプの種類を取得します。|
|[CWinApp:: GetNextDocTemplate](#getnextdoctemplate)|ドキュメントテンプレートの位置を取得します。 再帰的に使用できます。|
|[CWinApp:: Getプリンター Devicedefaults](#getprinterdevicedefaults)|プリンターデバイスの既定値を取得します。|
|[CWinApp:: GetProfileBinary](#getprofilebinary)|アプリケーションののエントリからバイナリデータを取得します。INI ファイル。|
|[CWinApp:: GetProfileInt](#getprofileint)|アプリケーションののエントリから整数を取得します。INI ファイル。|
|[CWinApp:: GetProfileString](#getprofilestring)|アプリケーションののエントリから文字列を取得します。INI ファイル。|
|[CWinApp::GetSectionKey](#getsectionkey)|HKEY_CURRENT_USER\\"software"/registrykey\ appname lpszsectionのキーを返します。|
|[CWinApp::HideApplication](#hideapplication)|すべてのドキュメントを閉じる前に、アプリケーションを非表示にします。|
|[CWinApp::HtmlHelp](#htmlhelp)|Windows 関数`HTMLHelp`を呼び出します。|
|[CWinApp::InitInstance](#initinstance)|ウィンドウオブジェクトの作成など、Windows インスタンスの初期化を実行するには、をオーバーライドします。|
|[CWinApp::IsTaskbarInteractionEnabled](#istaskbarinteractionenabled)|Windows 7 タスクバーの対話が有効かどうかを示します。|
|[CWinApp:: LoadCursor](#loadcursor)|カーソルリソースを読み込みます。|
|[CWinApp::LoadIcon](#loadicon)|アイコンリソースを読み込みます。|
|[CWinApp::LoadOEMCursor](#loadoemcursor)|WINDOWS で**OCR_** 定数によって指定された windows OEM 定義済みカーソルを読み込みます。始め.|
|[CWinApp:: LoadOEMIcon](#loadoemicon)|WINDOWS で**OIC_** 定数によって指定された windows OEM 定義済みアイコンを読み込みます。始め.|
|[CWinApp:: LoadStandardCursor](#loadstandardcursor)|WINDOWS で**IDC_** 定数によって指定された windows 定義済みのカーソルを読み込みます。始め.|
|[CWinApp::LoadStandardIcon](#loadstandardicon)|WINDOWS で**IDI_** 定数によって指定された windows の定義済みアイコンを読み込みます。始め.|
|[CWinApp::OnDDECommand](#onddecommand)|動的データ交換 (DDE) の execute コマンドに応答して、フレームワークによって呼び出されます。|
|[CWinApp::OnIdle](#onidle)|をオーバーライドして、アプリケーション固有のアイドル時処理を実行します。|
|[CWinApp::OpenDocumentFile](#opendocumentfile)|ファイルからドキュメントを開くためにフレームワークによって呼び出されます。|
|[CWinApp::ParseCommandLine](#parsecommandline)|コマンドラインの個々のパラメーターとフラグを解析します。|
|[CWinApp::PreTranslateMessage](#pretranslatemessage)|Windows 関数[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)にディスパッチされる前に、メッセージをフィルター処理します。|
|[CWinApp::ProcessMessageFilter](#processmessagefilter)|アプリケーションに到着する前に、特定のメッセージをインターセプトします。|
|[CWinApp::ProcessShellCommand](#processshellcommand)|コマンドラインの引数とフラグを処理します。|
|[CWinApp::ProcessWndProcException](#processwndprocexception)|アプリケーションのメッセージおよびコマンドハンドラーによってスローされた未処理の例外をすべてインターセプトします。|
|[CWinApp::Register](#register)|カスタマイズされた登録を実行します。|
|[CWinApp::RegisterWithRestartManager](#registerwithrestartmanager)|アプリケーションを再起動マネージャーに登録します。|
|[CWinApp::ReopenPreviousFilesAtRestart](#reopenpreviousfilesatrestart)|アプリケーションが予期せず終了したときに開いたファイルを再起動マネージャーが再度開くかどうかを指定します。|
|[CWinApp::RestartInstance](#restartinstance)|再起動マネージャーによって開始されたアプリケーションの再起動を処理します。|
|[CWinApp::RestoreAutosavedFilesAtRestart](#restoreautosavedfilesatrestart)|再起動マネージャーが、アプリケーションの再起動時に自動保存されたファイルを復元するかどうかを指定します。|
|[CWinApp::Run](#run)|既定のメッセージループを実行します。 メッセージループをカスタマイズするには、をオーバーライドします。|
|[CWinApp:: RunAutomated](#runautomated)|アプリケーションのコマンドラインで **/Automation**オプションをテストします。 互換性のために残されています。 代わりに、 [ParseCommandLine](#parsecommandline)を呼び出した後、 [CCommandLineInfo:: m_bRunAutomated](../../mfc/reference/ccommandlineinfo-class.md#m_brunautomated)の値を使用します。|
|[CWinApp::RunEmbedded](#runembedded)|アプリケーションのコマンドラインで **/Embedding**オプションをテストします。 互換性のために残されています。 代わりに、 [ParseCommandLine](#parsecommandline)を呼び出した後、 [CCommandLineInfo:: m_bRunEmbedded](../../mfc/reference/ccommandlineinfo-class.md#m_brunembedded)の値を使用します。|
|[CWinApp:: SaveAllModified](#saveallmodified)|変更されたすべてのドキュメントを保存するようにユーザーに要求します。|
|[CWinApp:: SelectPrinter](#selectprinter)|以前にユーザーが [印刷] ダイアログボックスを使用して指定したプリンターを選択します。|
|[CWinApp:: Se@ Pmode](#sethelpmode)|アプリケーションによって使用されるヘルプの種類を設定し、初期化します。|
|[CWinApp::SupportsApplicationRecovery](#supportsapplicationrecovery)|予期せずに終了したアプリケーションを再起動マネージャーが回復するかどうかを指定します。|
|[CWinApp:: SupportsAutosaveAtInterval](#supportsautosaveatinterval)|再起動マネージャーが開いているドキュメントを一定の間隔で自動保存するかどうかを指定します。|
|[CWinApp:: SupportsAutosaveAtRestart](#supportsautosaveatrestart)|アプリケーションの再起動時に、再起動マネージャーが開いているドキュメントを自動保存するかどうかを指定します。|
|[CWinApp:: SupportsRestartManager](#supportsrestartmanager)|アプリケーションが再起動マネージャーをサポートしているかどうかを判断します。|
|[CWinApp:: 登録解除](#unregister)|オブジェクトによって登録されて`CWinApp`いることがわかっているすべての登録を解除します。|
|[CWinApp:: WinHelp](#winhelp)|Windows 関数`WinHelp`を呼び出します。|
|[CWinApp:: WriteProfileBinary](#writeprofilebinary)|アプリケーションののエントリにバイナリデータを書き込みます。INI ファイル。|
|[CWinApp:: WriteProfileInt](#writeprofileint)|アプリケーションののエントリに整数を書き込みます。INI ファイル。|
|[CWinApp::WriteProfileString](#writeprofilestring)|アプリケーションののエントリに文字列を書き込みます。INI ファイル。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CWinApp::EnableShellOpen](#enableshellopen)|ユーザーが Windows ファイルマネージャーからデータファイルを開くことを許可します。|
|[CWinApp::LoadStdProfileSettings](#loadstdprofilesettings)|標準を読み込みます。INI ファイルの設定を使用すると、MRU ファイルリスト機能が有効になります。|
|[CWinApp::OnContextHelp](#oncontexthelp)|アプリケーション内の SHIFT + F1 ヘルプを処理します。|
|[CWinApp::OnFileNew](#onfilenew)|ID_FILE_NEW コマンドを実装します。|
|[CWinApp::OnFileOpen](#onfileopen)|ID_FILE_OPEN コマンドを実装します。|
|[CWinApp::OnFilePrintSetup](#onfileprintsetup)|ID_FILE_PRINT_SETUP コマンドを実装します。|
|[CWinApp::OnHelp](#onhelp)|アプリケーション内で F1 ヘルプを (現在のコンテキストを使って) 処理します。|
|[CWinApp:: OnHelpFinder](#onhelpfinder)|ID_HELP_FINDER コマンドと ID_DEFAULT_HELP コマンドを処理します。|
|[CWinApp::OnHelpIndex](#onhelpindex)|ID_HELP_INDEX コマンドを処理し、既定のヘルプトピックを提供します。|
|[CWinApp::OnHelpUsing](#onhelpusing)|ID_HELP_USING コマンドを処理します。|
|[CWinApp::RegisterShellFileTypes](#registershellfiletypes)|すべてのアプリケーションのドキュメントの種類を Windows ファイルマネージャーに登録します。|
|[CWinApp::SetAppID](#setappid)|アプリケーションのアプリケーションユーザーモデル ID を明示的に設定します。 ユーザーインターフェイスをユーザーに提示する前に、このメソッドを呼び出す必要があります (最適な場所はアプリケーションコンストラクターです)。|
|[CWinApp:: SetRegistryKey](#setregistrykey)|ではなく、アプリケーション設定がレジストリに格納されます。INI ファイル。|
|[CWinApp::UnregisterShellFileTypes](#unregistershellfiletypes)|Windows ファイルマネージャーを使用して、すべてのアプリケーションのドキュメントの種類の登録を解除します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CWinApp:: m_bHelpMode](#m_bhelpmode)|ユーザーがヘルプコンテキストモードであるかどうかを示します (通常は SHIFT + F1 キーを使用して呼び出されます)。|
|[CWinApp:: m_eHelpType](#m_ehelptype)|アプリケーションで使用されるヘルプの種類を指定します。|
|[CWinApp:: m_hInstance](#m_hinstance)|アプリケーションの現在のインスタンスを識別します。|
|[CWinApp:: m_lpCmdLine](#m_lpcmdline)|アプリケーションのコマンドラインを指定する null で終わる文字列を指します。|
|[CWinApp:: m_nCmdShow](#m_ncmdshow)|ウィンドウを最初に表示する方法を指定します。|
|[CWinApp:: m_pActiveWnd](#m_pactivewnd)|OLE サーバーがアクティブになっている場合の、コンテナーアプリケーションのメインウィンドウへのポインター。|
|[CWinApp::m_pszAppID](#m_pszappid)|アプリケーションユーザーモデル ID。|
|[CWinApp::m_pszAppName](#m_pszappname)|アプリケーション名を示します。|
|[CWinApp::m_pszExeName](#m_pszexename)|アプリケーションのモジュール名。|
|[CWinApp:: m_pszHelpFilePath](#m_pszhelpfilepath)|アプリケーションのヘルプファイルへのパス。|
|[CWinApp:: m_pszProfileName](#m_pszprofilename)|アプリケーションの。INI ファイル名。|
|[CWinApp:: m_pszRegistryKey](#m_pszregistrykey)|アプリケーションプロファイル設定を格納するための完全なレジストリキーを決定するために使用されます。|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CWinApp:: m_dwRestartManagerSupportFlags](#m_dwrestartmanagersupportflags)|再起動マネージャーの動作を決定するフラグ。|
|[CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval)|自動保存の時間の長さ (ミリ秒単位)。|
|[CWinApp::m_pDataRecoveryHandler](#m_pdatarecoveryhandler)|アプリケーションのデータ復旧ハンドラーへのポインター。|

## <a name="remarks"></a>Remarks

アプリケーションオブジェクトには、アプリケーション (およびそのインスタンスの各インスタンス) を初期化し、アプリケーションを実行するためのメンバー関数が用意されています。

Microsoft Foundation クラスを使用する各アプリケーションには、から`CWinApp`派生したオブジェクトを1つだけ含めることができます。 このオブジェクトは、他のC++グローバルオブジェクトが構築されるときに作成され、 `WinMain` Windows が Microsoft Foundation Class ライブラリによって提供される関数を呼び出したときに既に使用できるようになります。 派生`CWinApp`オブジェクトをグローバルレベルで宣言します。

から`CWinApp`アプリケーションクラスを派生させる場合は、 [InitInstance](#initinstance)メンバー関数をオーバーライドして、アプリケーションのメインウィンドウオブジェクトを作成します。

Microsoft Foundation Class ライブラリには、 `CWinApp`メンバー関数に加えて、 `CWinApp`オブジェクトやその他のグローバル情報にアクセスするための次のグローバル関数が用意されています。

- [AfxGetApp](application-information-and-management.md#afxgetapp)オブジェクトへの`CWinApp`ポインターを取得します。

- [AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)現在のアプリケーションインスタンスへのハンドルを取得します。

- [AfxGetResourceHandle](application-information-and-management.md#afxgetresourcehandle)アプリケーションのリソースへのハンドルを取得します。

- [AfxGetAppName](application-information-and-management.md#afxgetappname)アプリケーション名を格納している文字列へのポインターを取得します。 また、 `CWinApp`オブジェクトへのポインターがある場合は、を`m_pszExeName`使用してアプリケーション名を取得します。

「 [CWinApp:クラスの詳細](../../mfc/cwinapp-the-application-class.md)については、次の概要などのアプリケーションクラスを参照してください。 `CWinApp`

- `CWinApp`-アプリケーションウィザードによって作成された派生コード。

- `CWinApp`アプリケーションの実行シーケンスのロール。

- `CWinApp`の既定のメンバー関数の実装。

- `CWinApp`キー overridables。

データ`m_hPrevInstance`メンバーはもう存在しません。 アプリケーションの別のインスタンスが実行されているかどうかを確認するには、名前付きミューテックスを使用します。 ミューテックスを開くことができない場合は、実行中のアプリケーションの他のインスタンスは存在しません。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWinThread](../../mfc/reference/cwinthread-class.md)

`CWinApp`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="adddoctemplate"></a>  CWinApp::AddDocTemplate

このメンバー関数を呼び出して、アプリケーションが保持する使用可能なドキュメントテンプレートの一覧にドキュメントテンプレートを追加します。

```
void AddDocTemplate(CDocTemplate* pTemplate);
```

### <a name="parameters"></a>パラメーター

*pTemplate*<br/>
追加するへの`CDocTemplate`ポインター。

### <a name="remarks"></a>Remarks

[RegisterShellFileTypes](#registershellfiletypes)を呼び出す前に、すべてのドキュメントテンプレートをアプリケーションに追加する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#35](../../mfc/reference/codesnippet/cpp/cwinapp-class_1.cpp)]

##  <a name="addtorecentfilelist"></a>  CWinApp::AddToRecentFileList

このメンバー関数を呼び出して、 *Lpszpathname*を MRU ファイルリストに追加します。

```
virtual void AddToRecentFileList(LPCTSTR lpszPathName);
```

### <a name="parameters"></a>パラメーター

*lpszPathName*<br/>
ファイルのパス。

### <a name="remarks"></a>Remarks

このメンバー関数を使用する前に、 [LoadStdProfileSettings](#loadstdprofilesettings)メンバー関数を呼び出して、現在の MRU ファイルリストを読み込む必要があります。

フレームワークは、ファイルを開くときにこのメンバー関数を呼び出します。または、[名前を付けて保存] コマンドを実行して、新しい名前でファイルを保存します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#36](../../mfc/reference/codesnippet/cpp/cwinapp-class_2.cpp)]

##  <a name="applicationrecoverycallback"></a>  CWinApp::ApplicationRecoveryCallback

アプリケーションが予期せず終了したときにフレームワークによって呼び出されます。

```
virtual DWORD ApplicationRecoveryCallback(LPVOID lpvParam);
```

### <a name="parameters"></a>パラメーター

*lpvParam*<br/>
から将来使用するために予約されています。

### <a name="return-value"></a>戻り値

このメソッドが成功した場合は0。エラーが発生した場合は0以外の。

### <a name="remarks"></a>Remarks

アプリケーションが再起動マネージャーをサポートしている場合、アプリケーションが予期せず終了したときに、フレームワークはこの関数を呼び出します。

の既定の`ApplicationRecoveryCallback`実装では`CDataRecoveryHandler` 、を使用して、現在開いているドキュメントの一覧をレジストリに保存します。 このメソッドは、ファイルを自動保存しません。

動作をカスタマイズするには、派生した[Cwinapp クラス](../../mfc/reference/cwinapp-class.md)でこの関数をオーバーライドするか、独自のアプリケーションの回復メソッドをパラメーターとして[CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)に渡します。

##  <a name="closealldocuments"></a>CWinApp:: CloseAllDocuments

終了する前にすべての開いているドキュメントを閉じるには、このメンバー関数を呼び出します。

```
void CloseAllDocuments(BOOL bEndSession);
```

### <a name="parameters"></a>パラメーター

*bEndSession*<br/>
Windows セッションを終了するかどうかを指定します。 セッションが終了している場合は TRUE です。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

を呼び出す`CloseAllDocuments`前に[hideapplication](#hideapplication)を呼び出してください。

##  <a name="createprinterdc"></a>  CWinApp::CreatePrinterDC

選択したプリンターからプリンターデバイスコンテキスト (DC) を作成するには、このメンバー関数を呼び出します。

```
BOOL CreatePrinterDC(CDC& dc);
```

### <a name="parameters"></a>パラメーター

*dc*<br/>
プリンターデバイスコンテキストへの参照。

### <a name="return-value"></a>戻り値

プリンターデバイスコンテキストが正常に作成された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

`CreatePrinterDC`参照渡しで渡すデバイスコンテキストを初期化して、出力に使用できるようにします。

関数が正常に実行された場合は、印刷が完了したら、デバイスコンテキストを破棄する必要があります。 [Cdc](../../mfc/reference/cdc-class.md)オブジェクトのデストラクターを使用することも、 [Cdc::D eletedc](../../mfc/reference/cdc-class.md#deletedc)を呼び出すことによって明示的に実行することもできます。

##  <a name="cwinapp"></a>CWinApp:: CWinApp

オブジェクトを`CWinApp`構築し、アプリケーション名として格納される*lpszappname*を渡します。

```
CWinApp(LPCTSTR lpszAppName = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszAppName*<br/>
Windows が使用するアプリケーション名を含む null で終わる文字列。 この引数が指定されていないか`CWinApp` NULL の場合、はリソース文字列 AFX_IDS_APP_TITLE または実行可能ファイルのファイル名を使用します。

### <a name="remarks"></a>Remarks

派生クラスの1つの`CWinApp`グローバルオブジェクトを作成する必要があります。 アプリケーションには、オブジェクト`CWinApp`を1つだけ含めることができます。 コンストラクターは`CWinApp`オブジェクトへのポインターを格納します`WinMain` 。これにより、は、オブジェクトのメンバー関数を呼び出してアプリケーションを初期化し、実行できるようになります。

##  <a name="delregtree"></a>  CWinApp::DelRegTree

特定のレジストリキーとそのすべてのサブキーを削除します。

```
LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName);

LONG DelRegTree(
    HKEY hParentKey,
    const CString& strKeyName,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*hParentKey*<br/>
レジストリキーを処理します。

*strKeyName*<br/>
削除するレジストリキーの名前を指定します。

*pTM*<br/>
CAtlTransactionManager オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合、戻り値は ERROR_SUCCESS です。 関数が失敗した場合、戻り値は Winerror.h で定義されている0以外のエラーコードになります。

### <a name="remarks"></a>Remarks

指定したキーとそのサブキーを削除するには、この関数を呼び出します。

##  <a name="domessagebox"></a>CWinApp::D oMessageBox

フレームワークは、このメンバー関数を呼び出して、グローバル関数[AfxMessageBox](cstring-formatting-and-message-box-display.md#afxmessagebox)のメッセージボックスを実装します。

```
virtual int DoMessageBox(
    LPCTSTR lpszPrompt,
    UINT nType,
    UINT nIDPrompt);
```

### <a name="parameters"></a>パラメーター

*lpszPrompt*<br/>
メッセージボックス内のテキストのアドレス。

*nType*<br/>
メッセージボックスの[スタイル](../../mfc/reference/styles-used-by-mfc.md#message-box-styles)。

*nIDPrompt*<br/>
ヘルプコンテキスト文字列のインデックス。

### <a name="return-value"></a>戻り値

と`AfxMessageBox`同じ値を返します。

### <a name="remarks"></a>Remarks

メッセージボックスを開くためにこのメンバー関数を呼び出さないでください。代わりに`AfxMessageBox`を使用してください。

アプリケーション全体の呼び出しの`AfxMessageBox`処理をカスタマイズするには、このメンバー関数をオーバーライドします。

##  <a name="dowaitcursor"></a>CWinApp::D oWaitCursor

このメンバー関数は、 [CWaitCursor](../../mfc/reference/cwaitcursor-class.md)、 [Ccmdtarget:: BeginWaitCursor](../../mfc/reference/ccmdtarget-class.md#beginwaitcursor)、 [ccmdtarget:: EndWaitCursor](../../mfc/reference/ccmdtarget-class.md#endwaitcursor)、および[ccmdtarget:: RestoreWaitCursor](../../mfc/reference/ccmdtarget-class.md#restorewaitcursor)を実装するためにフレームワークによって呼び出されます。

```
virtual void DoWaitCursor(int nCode);
```

### <a name="parameters"></a>パラメーター

*nCode*<br/>
このパラメーターが1の場合、待機カーソルが表示されます。 0の場合、参照カウントをインクリメントせずに待機カーソルが復元されます。 -1 の場合、待機カーソルは終了します。

### <a name="remarks"></a>Remarks

既定では、砂時計カーソルが実装されます。 `DoWaitCursor`参照カウントを保持します。 正の場合、砂時計カーソルが表示されます。

通常は直接を呼び出す`DoWaitCursor`ことはできませんが、このメンバー関数をオーバーライドして待機カーソルを変更したり、待機カーソルが表示されている間に追加の処理を行ったりすることもできます。

待機カーソルを実装するためのより簡単で効率的な方法に`CWaitCursor`ついては、を使用してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#37](../../mfc/reference/codesnippet/cpp/cwinapp-class_3.cpp)]

##  <a name="enabled2dsupport"></a>  CWinApp::EnableD2DSupport

Visual Studio 2010 SP1 が必要です。

Application D2D のサポートを有効にします。 このメソッドは、メイン ウィンドウが初期化される前に呼び出します。

```
BOOL EnableD2DSupport(
    D2D1_FACTORY_TYPE d2dFactoryType = D2D1_FACTORY_TYPE_SINGLE_THREADED,
    DWRITE_FACTORY_TYPE writeFactoryType = DWRITE_FACTORY_TYPE_SHARED);
```

### <a name="parameters"></a>パラメーター

*d2dFactoryType*<br/>
D2D ファクトリとそれによって作成されるリソースのスレッドモデル。

*writeFactoryType*<br/>
書き込みファクトリオブジェクトを共有するか分離するかを指定する値。

### <a name="return-value"></a>戻り値

D2D のサポートが有効になっている場合は TRUE、それ以外の場合は FALSE を返します。

##  <a name="enablehtmlhelp"></a>  CWinApp::EnableHtmlHelp

アプリケーションのヘルプに html ヘルプを使用するに`CWinApp`は、派生クラスのコンストラクター内からこのメンバー関数を呼び出します。

```
void EnableHtmlHelp();
```

### <a name="remarks"></a>Remarks

##  <a name="enableshellopen"></a>CWinApp:: EnableShellOpen

アプリケーションのユーザーが Windows ファイルマネージャー `InitInstance`内からファイルをダブルクリックしてデータファイルを開けるようにするには、通常はオーバーライドからこの関数を呼び出します。

```
void EnableShellOpen();
```

### <a name="remarks"></a>Remarks

この関数と共にメンバー関数を呼び出すか、を指定します。`RegisterShellFileTypes`ドキュメントの種類を手動で登録するためのアプリケーションを含む REG ファイル。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#38](../../mfc/reference/codesnippet/cpp/cwinapp-class_4.cpp)]

##  <a name="enabletaskbarinteraction"></a>CWinApp:: EnableTaskbarInteraction

タスクバーとの対話を有効にします。

```
BOOL EnableTaskbarInteraction(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
Windows 7 タスクバーとの対話を有効にするか (TRUE)、無効 (FALSE) にするかを指定します。

### <a name="return-value"></a>戻り値

タスクバーの操作を有効または無効にすることができる場合は TRUE を返します。

### <a name="remarks"></a>Remarks

メインウィンドウを作成する前にこのメソッドを呼び出す必要があります。それ以外の場合は、アサートして FALSE を返します。

##  <a name="exitinstance"></a>CWinApp:: ExitInstance

アプリケーションのこのインスタンスを終了する`Run`ために、メンバー関数内からフレームワークによって呼び出されます。

```
virtual int ExitInstance();
```

### <a name="return-value"></a>戻り値

アプリケーションの終了コード。0はエラーがないことを示し、0より大きい値はエラーを示します。 この値は、からの`WinMain`戻り値として使用されます。

### <a name="remarks"></a>Remarks

このメンバー関数は、 `Run`メンバー関数内のどこからでも呼び出すことはできません。

この関数の既定の実装では、アプリケーションのにフレームワークオプションを書き込みます。INI ファイル。 アプリケーションの終了時にクリーンアップするには、この関数をオーバーライドします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#39](../../mfc/reference/codesnippet/cpp/cwinapp-class_5.cpp)]

##  <a name="getapplicationrecoveryparameter"></a>  CWinApp::GetApplicationRecoveryParameter

アプリケーションの回復方法の入力パラメーターを取得します。

```
virtual LPVOID GetApplicationRecoveryParameter();
```

### <a name="return-value"></a>戻り値

アプリケーションの回復方法の既定の入力パラメーター。

### <a name="remarks"></a>Remarks

この関数の既定の動作では、NULL が返されます。

詳細については、「 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)」を参照してください。

##  <a name="getapplicationrecoverypinginterval"></a>  CWinApp::GetApplicationRecoveryPingInterval

再開マネージャーが復旧コールバック関数から戻るまで待機する時間を返します。

```
virtual DWORD GetApplicationRecoveryPingInterval();
```

### <a name="return-value"></a>戻り値

ミリ秒単位の時間の長さ。

### <a name="remarks"></a>Remarks

再起動マネージャーに登録されているアプリケーションが予期せず終了した場合、アプリケーションは開いているドキュメントを保存し、回復コールバック関数を呼び出します。 既定の回復コールバック関数は、 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)です。

復旧コールバック関数が返されるのをフレームワークが待機する時間の長さは、ping の間隔です。 Ping 間隔をカスタマイズするには、 `CWinApp::GetApplicationRecoveryPingInterval`をオーバーライドするか、に`RegisterWithRestartManager`カスタム値を指定します。

##  <a name="getapplicationrestartflags"></a>CWinApp:: GetApplicationRestartFlags

再起動マネージャーのフラグを返します。

```
virtual DWORD GetApplicationRestartFlags();
```

### <a name="return-value"></a>戻り値

再起動マネージャーのフラグ。 既定の実装では、0が返されます。

### <a name="remarks"></a>Remarks

再起動マネージャーのフラグは、既定の実装には影響しません。 これらは将来使用するために提供されています。

このフラグは、アプリケーションを再起動マネージャーに登録するときに、 [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)を使用して設定します。

Restart manager フラグに指定できる値は次のとおりです。

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="getappregistrykey"></a>  CWinApp::GetAppRegistryKey

HKEY_CURRENT_USER\\"Software" \RegistryKey\ProfileName. のキーを返します。

```
HKEY GetAppRegistryKey(CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*pTM*<br/>
オブジェクトへの`CAtlTransactionManager`ポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合はアプリケーションキー。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="getdatarecoveryhandler"></a>CWinApp:: GetDataRecoveryHandler

アプリケーションのこのインスタンスのデータ回復ハンドラーを取得します。

```
virtual CDataRecoveryHandler *GetDataRecoveryHandler();
```

### <a name="return-value"></a>戻り値

アプリケーションのこのインスタンスのデータ回復ハンドラー。

### <a name="remarks"></a>Remarks

再起動マネージャーを使用する各アプリケーションは、 [CDataRecoveryHandler クラス](../../mfc/reference/cdatarecoveryhandler-class.md)のインスタンスを1つ持つ必要があります。 このクラスは、開いているドキュメントとワークファイルの監視を行います。 の動作は、 `CDataRecoveryHandler`再起動マネージャーの構成によって異なります。 詳細については、「 [CDataRecoveryHandler クラス](../../mfc/reference/cdatarecoveryhandler-class.md)」を参照してください。

このメソッドは、Windows Vista より前のオペレーティングシステムでは NULL を返します。 再起動マネージャーは、Windows Vista より前のオペレーティングシステムではサポートされていません。

アプリケーションに現在データ復旧ハンドラーがない場合、このメソッドは1つを作成し、ポインターを返します。

##  <a name="getfirstdoctemplateposition"></a>CWinApp:: GetFirstDocTemplatePosition

アプリケーション内の最初のドキュメントテンプレートの位置を取得します。

```
POSITION GetFirstDocTemplatePosition() const;
```

### <a name="return-value"></a>戻り値

反復またはオブジェクトポインターの取得に使用できる位置の値。リストが空の場合は NULL です。

### <a name="remarks"></a>Remarks

[GetNextDocTemplate](#getnextdoctemplate)の呼び出しで返される位置の値を使用して、最初の[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)オブジェクトを取得します。

##  <a name="gethelpmode"></a>CWinApp:: Ge@ Pmode

アプリケーションによって使用されるヘルプの種類を取得します。

```
AFX_HELP_TYPE GetHelpMode();
```

### <a name="return-value"></a>戻り値

アプリケーションによって使用されるヘルプの種類。 詳細については、「 [CWinApp:: m_eHelpType](#m_ehelptype) 」を参照してください。

##  <a name="getnextdoctemplate"></a>CWinApp:: GetNextDocTemplate

*Pos*によって識別されるドキュメントテンプレートを取得し、 *pos*を POSITION 値に設定します。

```
CDocTemplate* GetNextDocTemplate(POSITION& pos) const;
```

### <a name="parameters"></a>パラメーター

*po*<br/>
または`GetNextDocTemplate` [getfirstdoctemplateposition](#getfirstdoctemplateposition)への前回の呼び出しによって返された位置の値への参照。 値は、この呼び出しによって次の位置に更新されます。

### <a name="return-value"></a>戻り値

[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

`GetNextDocTemplate` を`GetFirstDocTemplatePosition`呼び出して最初の位置を設定する場合は、前方反復ループでを使用できます。

位置の値が有効であることを確認する必要があります。 無効な場合は、Microsoft Foundation Class ライブラリのデバッグバージョンがアサートされます。

取得したドキュメントテンプレートが最後に使用可能な場合は、 *pos*の新しい値が NULL に設定されます。

##  <a name="getprinterdevicedefaults"></a>CWinApp:: Getプリンター Devicedefaults

印刷用のプリンターデバイスコンテキストを準備するには、このメンバー関数を呼び出します。

```
BOOL GetPrinterDeviceDefaults(struct tagPDA* pPrintDlg);
```

### <a name="parameters"></a>パラメーター

*pPrintDlg*<br/>
[PRINTDLG](/windows/win32/api/commdlg/ns-commdlg-printdlga)構造体へのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

Windows から現在のプリンターの既定値を取得します。必要に応じて INI ファイルを使用するか、印刷設定でユーザーによって設定された最後のプリンター構成を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#40](../../mfc/reference/codesnippet/cpp/cwinapp-class_6.cpp)]

##  <a name="getprofilebinary"></a>CWinApp:: GetProfileBinary

アプリケーションのレジストリまたはの指定したセクション内のエントリからバイナリデータを取得するには、このメンバー関数を呼び出します。INI ファイル。

```
BOOL GetProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE* ppData,
    UINT* pBytes);
```

### <a name="parameters"></a>パラメーター

*lpszSection*<br/>
エントリがあるセクションを指定する NULL で終わる文字列へのポインター。

*lpszEntry*<br/>
値を取得するエントリを指定する NULL で終わる文字列へのポインター。

*ppData*<br/>
データのアドレスを受け取るポインターをポイントします。

*pBytes*<br/>
データのサイズ (バイト単位) を受け取る UINT を指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数は大文字と小文字が区別されないので、場合によっては、 *Lpszsection*および*lpszEntry*パラメーター内の文字列が異なる場合があります。

> [!NOTE]
> `GetProfileBinary`バッファーを割り当て、そのアドレスを\* *ppdata*に返します。 呼び出し元は、 **delete []** を使用してバッファーを解放します。

> [!IMPORTANT]
> この関数が返すデータは、NULL で終わるデータとは限らないため、呼び出し元で検証を行う必要があります。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#41](../../mfc/reference/codesnippet/cpp/cwinapp-class_7.cpp)]

その他の例については、「 [CWinApp:: WriteProfileBinary](#writeprofilebinary)」を参照してください。

##  <a name="getprofileint"></a>CWinApp:: GetProfileInt

アプリケーションのレジストリまたは .INI ファイルの指定のセクション内のエントリから整数値を取得します。

```
UINT GetProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nDefault);
```

### <a name="parameters"></a>パラメーター

*lpszSection*<br/>
エントリがあるセクションを指定する NULL で終わる文字列へのポインター。

*lpszEntry*<br/>
値を取得するエントリを指定する NULL で終わる文字列へのポインター。

*nDefault*<br/>
フレームワークがエントリを見つけられなかったときのために指定する既定値。

### <a name="return-value"></a>戻り値

正常終了した場合は、指定されたエントリに続く文字列の整数値を返します。 関数がエントリを見つけられない場合、戻り値は*Ndefault*パラメーターの値になります。 指定されたエントリに対応する値が整数でない場合は、0 を返します。

このメンバー関数は .INI ファイル内の値として 16 進表記をサポートします。 符号付き整数を取得する場合は、値を**int**にキャストする必要があります。

### <a name="remarks"></a>Remarks

このメンバー関数は大文字と小文字が区別されないので、場合によっては、 *Lpszsection*および*lpszEntry*パラメーター内の文字列が異なる場合があります。

> [!IMPORTANT]
> この関数が返すデータは、NULL で終わるデータとは限らないため、呼び出し元で検証を行う必要があります。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#42](../../mfc/reference/codesnippet/cpp/cwinapp-class_8.cpp)]

その他の例については、「 [CWinApp:: WriteProfileInt](#writeprofileint)」を参照してください。

##  <a name="getprofilestring"></a>  CWinApp::GetProfileString

このメンバー関数を呼び出して、アプリケーションのレジストリまたはの指定したセクション内のエントリに関連付けられている文字列を取得します。INI ファイル。

```
CString GetProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszDefault = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszSection*<br/>
エントリがあるセクションを指定する NULL で終わる文字列へのポインター。

*lpszEntry*<br/>
文字列を取得するエントリを含む、null で終わる文字列を指します。 この値を NULL にすることはできません。

*lpszDefault*<br/>
初期化ファイルにエントリが見つからない場合は、指定されたエントリの既定の文字列値をポイントします。

### <a name="return-value"></a>戻り値

戻り値は、アプリケーションのの文字列です。INI ファイルまたは*Lpszdefault* (文字列が見つからない場合)。 フレームワークでサポートされる文字列の最大長は _MAX_PATH です。 *Lpszdefault*が NULL の場合、戻り値は空の文字列になります。

### <a name="remarks"></a>Remarks

> [!IMPORTANT]
> この関数が返すデータは、NULL で終わるデータとは限らないため、呼び出し元で検証を行う必要があります。 詳しくは、「 [バッファー オーバーランの回避](/windows/win32/SecBP/avoiding-buffer-overruns)」をご覧ください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

別の例については、「 [CWinApp:: GetProfileInt](#getprofileint)」の例を参照してください。

##  <a name="getsectionkey"></a>  CWinApp::GetSectionKey

HKEY_CURRENT_USER\\"software" \ registrykey\ appname lpszsectionのキーを返します。

```
HKEY GetSectionKey(
    LPCTSTR lpszSection,
    CAtlTransactionManager* pTM = NULL);
```

### <a name="parameters"></a>パラメーター

*lpszSection*<br/>
取得するキーの名前。

*pTM*<br/>
オブジェクトへの`CAtlTransactionManager`ポインター。

### <a name="return-value"></a>戻り値

関数が成功した場合はセクションキー。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

##  <a name="hideapplication"></a>  CWinApp::HideApplication

開いているドキュメントを閉じる前に、アプリケーションを非表示にするには、このメンバー関数を呼び出します。

```
void HideApplication();
```

##  <a name="htmlhelp"></a>  CWinApp::HtmlHelp

このメンバー関数を呼び出して、Html ヘルプアプリケーションを呼び出します。

```
virtual void HtmlHelp(
    DWORD_PTR dwData,
    UINT nCmd = 0x000F);
```

### <a name="parameters"></a>パラメーター

*dwData*<br/>
追加データを指定します。 使用される値は、 *Ncmd*パラメーターの値によって異なります。 既定値`0x000F`は[HH_HELP_CONTEXT](/previous-versions/windows/desktop/htmlhelp/hh-help-context-command)を意味します。

*nCmd*<br/>
要求されるヘルプの種類を指定します。 使用可能な値の一覧と*Dwdata*パラメーターへの影響については、Windows SDK の[htmlhelpw](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpw)または[htmlhelpw](/windows/win32/api/htmlhelp/nf-htmlhelp-htmlhelpa) API 関数に記述されている*ucommand*パラメーターを参照してください。 

### <a name="remarks"></a>Remarks

フレームワークは、この関数を呼び出して、Html ヘルプアプリケーションを呼び出します。

アプリケーションが終了すると、フレームワークは自動的に Html ヘルプアプリケーションを終了します。

##  <a name="initinstance"></a>  CWinApp::InitInstance

Windows では、同じプログラムの複数のコピーを同時に実行できます。

```
virtual BOOL InitInstance();
```

### <a name="return-value"></a>戻り値

初期化が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

アプリケーションの初期化は、概念的には、プログラムの初回実行時に実行される1回限りのアプリケーションの初期化と、プログラムのコピーが実行されるたびに実行されるインスタンスの初期化の2つのセクションに分けられます。 フレームワークのの`WinMain`実装では、この関数を呼び出します。

を`InitInstance`オーバーライドして、Windows で実行されているアプリケーションの新しい各インスタンスを初期化します。 通常は、を`InitInstance`オーバーライドしてメインウィンドウオブジェクトを構築し`CWinThread::m_pMainWnd` 、そのウィンドウを指すようにデータメンバーを設定します。 このメンバー関数をオーバーライドする方法の詳細に[ついては、「CWinApp:アプリケーションクラス](../../mfc/cwinapp-the-application-class.md)。

> [!NOTE]
> MFC アプリケーションは、シングルスレッド アパートメント (STA) として初期化する必要があります。 `InitInstance`オーバーライドで[CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex)を呼び出した場合は、COINIT_APARTMENTTHREADED (COINIT_MULTITHREADED ではなく) を指定します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCListView#9](../../atl/reference/codesnippet/cpp/cwinapp-class_10.cpp)]

##  <a name="istaskbarinteractionenabled"></a>CWinApp:: IsTaskbarInteractionEnabled

Windows 7 タスクバーの対話が有効かどうかを示します。

```
virtual BOOL IsTaskbarInteractionEnabled();
```

### <a name="return-value"></a>戻り値

が呼び出され`EnableTaskbarInteraction`ていて、オペレーティングシステムが Windows 7 以降である場合に TRUE を返します。

### <a name="remarks"></a>Remarks

タスクバーの相互作用とは、MDI アプリケーションが、アプリケーションのタスクバーボタンの上にマウスポインターを置いたときに表示される別のタブ付きサムネイルに MDI 子のコンテンツを表示することを意味します。

##  <a name="loadcursor"></a>  CWinApp::LoadCursor

現在の実行可能ファイルから、 *nIDResource*によって指定された、 *lpszresourcename*持つという名前のカーソルリソースを読み込みます。

```
HCURSOR LoadCursor(LPCTSTR lpszResourceName) const;  HCURSOR LoadCursor(UINT nIDResource) const;
```

### <a name="parameters"></a>パラメーター

*lpszResourceName*<br/>
カーソルリソースの名前を含む null で終わる文字列を指します。 この引数には`CString` 、を使用できます。

*nIDResource*<br/>
カーソルリソースの ID。 リソースの一覧については、Windows SDK の「 [Loadcursor](/windows/win32/api/winuser/nf-winuser-loadcursorw) 」を参照してください。

### <a name="return-value"></a>戻り値

成功した場合はカーソルを処理するハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

`LoadCursor`まだ読み込まれていない場合にのみ、カーソルをメモリに読み込みます。それ以外の場合は、既存のリソースのハンドルを取得します。

定義済みの Windows カーソルにアクセスするには、 [Loadstandardcursor](#loadstandardcursor)または[loadstandardcursor](#loadoemcursor)メンバー関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#44](../../mfc/reference/codesnippet/cpp/cwinapp-class_11.cpp)]

##  <a name="loadicon"></a>  CWinApp::LoadIcon

実行可能ファイルから、 *nIDResource*によって指定された、 *lpszresourcename*またはという名前のアイコンリソースを読み込みます。

```
HICON LoadIcon(LPCTSTR lpszResourceName) const;  HICON LoadIcon(UINT nIDResource) const;
```

### <a name="parameters"></a>パラメーター

*lpszResourceName*<br/>
アイコンリソースの名前を含む null で終わる文字列を指します。 この引数には、 `CString`を使用することもできます。

*nIDResource*<br/>
アイコンリソースの ID 番号。

### <a name="return-value"></a>戻り値

成功した場合はアイコンを示すハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

`LoadIcon`まだ読み込まれていない場合にのみ、アイコンを読み込みます。それ以外の場合は、既存のリソースのハンドルを取得します。

定義済みの Windows アイコンにアクセスするには、 [LoadStandardIcon](#loadstandardicon)または[loadoemicon](#loadoemicon)メンバー関数を使用します。

> [!NOTE]
> このメンバー関数は Win32 API 関数[Loadicon](/windows/win32/api/winuser/nf-winuser-loadiconw)を呼び出します。このアイコンは、SM_CXICON および SM_CYICON システムメトリック値に対応するサイズのアイコンのみを読み込むことができます。

##  <a name="loadoemcursor"></a>  CWinApp::LoadOEMCursor

*NIDCursor*によって指定された Windows の定義済みカーソルリソースを読み込みます。

```
HCURSOR LoadOEMCursor(UINT nIDCursor) const;
```

### <a name="parameters"></a>パラメーター

*nIDCursor*<br/>
定義済みの Windows カーソルを指定する**OCR_** manifest 定数識別子。 WINDOWS の**OCR_** 定数`#include \<afxwin.h>`にアクセスするには、の前にが`#define OEMRESOURCE`必要です。始め.

### <a name="return-value"></a>戻り値

成功した場合はカーソルを処理するハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

定義済み`LoadOEMCursor`の Windows カーソルにアクセスするには、または[loadstandardcursor](#loadstandardcursor)メンバー関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#45](../../mfc/reference/codesnippet/cpp/cwinapp-class_12.h)]

[!code-cpp[NVC_MFCWindowing#46](../../mfc/reference/codesnippet/cpp/cwinapp-class_13.cpp)]

##  <a name="loadoemicon"></a>CWinApp:: LoadOEMIcon

*NIDIcon*によって指定された Windows の定義済みアイコンリソースを読み込みます。

```
HICON LoadOEMIcon(UINT nIDIcon) const;
```

### <a name="parameters"></a>パラメーター

*nIDIcon*<br/>
定義済みの Windows アイコンを指定する**OIC_** manifest 定数識別子。 WINDOWS の**OIC_** 定数`#include \<afxwin.h>`にアクセスするには、の前にが`#define OEMRESOURCE`必要です。始め.

### <a name="return-value"></a>戻り値

成功した場合はアイコンを示すハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

定義済みの Windows アイコンにアクセスするには、`LoadOEMIcon` または [LoadStandardIcon](#loadstandardicon) メンバー関数を使用します。

##  <a name="loadstandardcursor"></a>CWinApp:: LoadStandardCursor

*Lpszcursor name*によって指定された Windows 定義済みのカーソルリソースを読み込みます。

```
HCURSOR LoadStandardCursor(LPCTSTR lpszCursorName) const;
```

### <a name="parameters"></a>パラメーター

*Lpszカーソル名*<br/>
定義済みの Windows カーソルを指定する**IDC_** manifest 定数識別子。 これらの識別子は WINDOWS で定義されています。始め. 次の一覧に、 *Lpszカーソル名*に使用できる定義済みの値と意味を示します。

- IDC_ARROW 標準の矢印カーソル

- IDC_IBEAM 標準のテキスト挿入カーソル

- Windows が時間のかかるタスクを実行するときに使用される IDC_WAIT 砂時計カーソル

- IDC_CROSS クロスヘアカーソルを選択します

- IDC_UPARROW をポイントする矢印

- IDC_SIZE は廃止され、サポートされていません。IDC_SIZEALL を使用する

- IDC_SIZEALL 4 つの矢印を指します。 ウィンドウのサイズを変更するために使用するカーソル。

- IDC_ICON Obsolete およびサポートされていません。 IDC_ARROW を使用します。

- 左上と右下で両端を持つ2方向矢印を IDC_SIZENWSE します。

- IDC_SIZENESW の右上隅と左下にある双方向矢印

- IDC_SIZEWE 横方向双方向矢印

- IDC_SIZENS Vertical 双方向矢印

### <a name="return-value"></a>戻り値

成功した場合はカーソルを処理するハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

定義済み`LoadStandardCursor`の Windows カーソルにアクセスするには、または[loadoemcursor](#loadoemcursor)メンバー関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#47](../../mfc/reference/codesnippet/cpp/cwinapp-class_14.cpp)]

##  <a name="loadstandardicon"></a>  CWinApp::LoadStandardIcon

*Lpsziconname*によって指定された Windows 定義済みのアイコンリソースを読み込みます。

```
HICON LoadStandardIcon(LPCTSTR lpszIconName) const;
```

### <a name="parameters"></a>パラメーター

*lpszIconName*<br/>
定義済みの Windows アイコンを指定するマニフェスト定数識別子。 これらの識別子は WINDOWS で定義されています。始め. 定義可能な定義済みの値とその説明の一覧については、Windows SDK の[Loadicon](/windows/win32/api/winuser/nf-winuser-loadiconw)の*Lsee onname*パラメーターを参照してください。

### <a name="return-value"></a>戻り値

成功した場合はアイコンを示すハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

定義済み`LoadStandardIcon`の Windows アイコンにアクセスするには、または[loadoemicon](#loadoemicon)メンバー関数を使用します。

##  <a name="loadstdprofilesettings"></a>  CWinApp::LoadStdProfileSettings

このメンバー関数を[InitInstance](#initinstance)メンバー関数内から呼び出して、最近使用した (MRU) ファイルと最後のプレビュー状態の一覧を有効にし、読み込みます。

```
void LoadStdProfileSettings(UINT nMaxMRU = _AFX_MRU_COUNT);
```

### <a name="parameters"></a>パラメーター

*nMaxMRU*<br/>
追跡する最近使用したファイルの数。

### <a name="remarks"></a>Remarks

*Nmaxmru*が0の場合、mru リストは保持されません。

##  <a name="m_bhelpmode"></a>CWinApp:: m_bHelpMode

アプリケーションがヘルプコンテキストモードである場合は TRUE (従来は SHIFT + F1 キーを使用して呼び出されます)。それ以外の場合は FALSE。

```
BOOL m_bHelpMode;
```

### <a name="remarks"></a>Remarks

ヘルプコンテキストモードでは、カーソルは疑問符になり、ユーザーは画面に移動できます。 ヘルプモードでの特別な処理を実装する場合は、このフラグを調べます。 `m_bHelpMode`は、BOOL 型のパブリック変数です。

##  <a name="m_dwrestartmanagersupportflags"></a>CWinApp:: m_dwRestartManagerSupportFlags

再起動マネージャーの動作を決定するフラグ。

```
DWORD m_dwRestartManagerSupportFlags;
```

### <a name="remarks"></a>Remarks

再起動マネージャーを有効にする`m_dwRestartManagerSupportFlags`には、を目的の動作に設定します。 次の表は、使用可能なフラグを示しています。

|||
|-|-|
|フラグ|説明|
|AFX_RESTART_MANAGER_SUPPORT_RESTART|アプリケーションは、 [CWinApp:: RegisterWithRestartManager](#registerwithrestartmanager)を使用して登録されます。 再起動マネージャーは、予期せず終了した場合に、アプリケーションを再起動する役割を担います。|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY|アプリケーションは再起動マネージャーに登録され、再起動マネージャーはアプリケーションを再起動するときに、回復コールバック関数を呼び出します。 既定の回復コールバック関数は、 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)です。|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART|自動保存が有効になり、再起動マネージャーによって、アプリケーションの再起動時に開いているすべてのドキュメントが自動保存されます。|
|- AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL|自動保存が有効になり、再起動マネージャーは開いているドキュメントを一定の間隔で自動保存します。 間隔は、 [CWinApp:: m_nAutosaveInterval](#m_nautosaveinterval)で定義されます。|
|- AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES|再起動マネージャーは、予期しない終了からアプリケーションを再起動した後、以前に開いていたドキュメントを開きます。 [CDataRecoveryHandler クラス](../../mfc/reference/cdatarecoveryhandler-class.md)は、開いているドキュメントの一覧を格納し、それらを復元します。|
|- AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES|再起動マネージャーは、アプリケーションの再起動後に、自動保存されたファイルを復元するようにユーザーに要求します。 クラス`CDataRecoveryHandler`は、ユーザーに対してクエリを行います。|
|- AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE|AFX_RESTART_MANAGER_SUPPORT_RESTART、AFX_RESTART_MANAGER_SUPPORT_RECOVER、および AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES の和集合。|
|- AFX_RESTART_MANAGER_SUPPORT_ALL_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_NO_AUTOSAVE、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL、および AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES の和集合。|
|- AFX_RESTART_MANAGER_SUPPORT_RESTART_ASPECTS|AFX_RESTART_MANAGER_SUPPORT_RESTART、AFX_RESTART_MANAGER_AUTOSAVE_AT_RESTART、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES、および AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES の和集合。|
|- AFX_RESTART_MANAGER_SUPPORT_RECOVERY_ASPECTS|Union ofAFX_RESTART_MANAGER_SUPPORT_RECOVERY、AFX_RESTART_MANAGER_AUTOSAVE_AT_INTERVAL、AFX_RESTART_MANAGER_REOPEN_PREVIOUS_FILES、および AFX_RESTART_MANAGER_RESTORE_AUTOSAVED_FILES。|

##  <a name="m_ehelptype"></a>CWinApp:: m_eHelpType

このデータメンバーの型は、 `CWinApp`クラス内で定義されている列挙型 AFX_HELP_TYPE です。

```
AFX_HELP_TYPE m_eHelpType;
```

### <a name="remarks"></a>Remarks

AFX_HELP_TYPE 列挙体は次のように定義されています。

```
enum AFX_HELP_TYPE {
    afxWinHelp = 0,
    afxHTMLHelp = 1
    };
```

- アプリケーションのヘルプを HTML ヘルプに設定するには、 [Sei pmode](#sethelpmode)を`afxHTMLHelp`呼び出し、を指定します。

- アプリケーションのヘルプを WinHelp に設定するには`SetHelpMode` 、を`afxWinHelp`呼び出し、を指定します。

##  <a name="m_hinstance"></a>  CWinApp::m_hInstance

Windows によってに`WinMain`渡される hInstance パラメーターに対応します。

```
HINSTANCE m_hInstance;
```

### <a name="remarks"></a>Remarks

`m_hInstance`データメンバーは、Windows で実行されているアプリケーションの現在のインスタンスへのハンドルです。 これは、グローバル関数[AfxGetInstanceHandle](application-information-and-management.md#afxgetinstancehandle)によって返されます。 `m_hInstance`は、HINSTANCE 型のパブリック変数です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#55](../../mfc/reference/codesnippet/cpp/cwinapp-class_15.cpp)]

##  <a name="m_lpcmdline"></a>CWinApp:: m_lpCmdLine

Windows によってに`WinMain`渡される lpCmdLine パラメーターに対応します。

```
LPTSTR m_lpCmdLine;
```

### <a name="remarks"></a>Remarks

アプリケーションのコマンドラインを指定する null で終わる文字列を指します。 アプリケーション`m_lpCmdLine`の起動時にユーザーが入力したコマンドライン引数にアクセスするには、を使用します。 `m_lpCmdLine`は、LPTSTR 型のパブリック変数です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="m_nautosaveinterval"></a>CWinApp:: m_nAutosaveInterval

自動保存の時間の長さ (ミリ秒単位)。

```
int m_nAutosaveInterval;
```

### <a name="remarks"></a>Remarks

開いているドキュメントを設定した間隔で自動保存するように再起動マネージャーを構成できます。 アプリケーションがファイルを自動保存しない場合、このパラメーターは無効です。

##  <a name="m_ncmdshow"></a>  CWinApp::m_nCmdShow

Windows によってに`WinMain`渡される*ncmdshow*パラメーターに対応します。

```
int m_nCmdShow;
```

### <a name="remarks"></a>Remarks

アプリケーションのメイン`m_nCmdShow`ウィンドウに対して[CWnd:: ShowWindow](../../mfc/reference/cwnd-class.md#showwindow)を呼び出す場合は、を引数として渡す必要があります。 `m_nCmdShow`**int**型のパブリック変数です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#56](../../mfc/reference/codesnippet/cpp/cwinapp-class_17.cpp)]

##  <a name="m_pactivewnd"></a>CWinApp:: m_pActiveWnd

OLE サーバーアプリケーションが埋め込み先でアクティブになっている OLE コンテナーアプリケーションのメインウィンドウへのポインターを格納するには、このデータメンバーを使用します。

### <a name="remarks"></a>Remarks

このデータメンバーが NULL の場合、アプリケーションはアクティブな状態ではありません。

フレームワークは、フレームウィンドウが OLE コンテナーアプリケーションによって埋め込み先に配置されている場合に、このメンバー変数を設定します。

##  <a name="m_pdatarecoveryhandler"></a>  CWinApp::m_pDataRecoveryHandler

アプリケーションのデータ復旧ハンドラーへのポインター。

```
CDataRecoveryHandler* m_pDataRecoveryHandler;
```

### <a name="remarks"></a>Remarks

アプリケーションのデータ回復ハンドラーは、開いているドキュメントを監視し、それらを自動保存します。 フレームワークは、予期せずに終了した後にアプリケーションが再起動したときに、データ回復ハンドラーを使用して自動保存されたファイルを復元します。 詳細については、「 [CDataRecoveryHandler クラス](../../mfc/reference/cdatarecoveryhandler-class.md)」を参照してください。

##  <a name="m_pszappname"></a>  CWinApp::m_pszAppName

アプリケーション名を示します。

```
LPCTSTR m_pszAppName;
```

### <a name="remarks"></a>Remarks

アプリケーション名は、 [CWinApp](#cwinapp)コンストラクターに渡されたパラメーターから取得できます。または、指定されていない場合は、ID が AFX_IDS_APP_TITLE のリソース文字列になります。 アプリケーション名がリソース内に見つからない場合は、プログラムのから取得されます。EXE ファイル名。

グローバル関数[AfxGetAppName](application-information-and-management.md#afxgetappname)によって返されます。 `m_pszAppName`**const char**<strong>\*</strong>型のパブリック変数です。

> [!NOTE]
> に`m_pszAppName`値を割り当てた場合は、ヒープに動的に割り当てられる必要があります。 デストラクター `CWinApp`は、このポインターを使用して**free**() を呼び出します。 多くの`_tcsdup`場合、() ランタイムライブラリ関数を使用して割り当てを実行します。 また、新しい値を割り当てる前に、現在のポインターに関連付けられているメモリを解放します。 例:

[!code-cpp[NVC_MFCWindowing#57](../../mfc/reference/codesnippet/cpp/cwinapp-class_18.cpp)]

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#65](../../mfc/reference/codesnippet/cpp/cwinapp-class_19.cpp)]

##  <a name="m_pszexename"></a>  CWinApp::m_pszExeName

拡張子のないアプリケーションの実行可能ファイルの名前を格納します。

```
LPCTSTR m_pszExeName;
```

### <a name="remarks"></a>Remarks

[M_pszAppName](#m_pszappname)とは異なり、この名前に空白を含めることはできません。 `m_pszExeName`**const char**<strong>\*</strong>型のパブリック変数です。

> [!NOTE]
> に`m_pszExeName`値を割り当てた場合は、ヒープに動的に割り当てられる必要があります。 デストラクター `CWinApp`は、このポインターを使用して**free**() を呼び出します。 多くの`_tcsdup`場合、() ランタイムライブラリ関数を使用して割り当てを実行します。 また、新しい値を割り当てる前に、現在のポインターに関連付けられているメモリを解放します。 例:

[!code-cpp[NVC_MFCWindowing#58](../../mfc/reference/codesnippet/cpp/cwinapp-class_20.cpp)]

##  <a name="m_pszhelpfilepath"></a>CWinApp:: m_pszHelpFilePath

アプリケーションのヘルプファイルへのパスが含まれます。

```
LPCTSTR m_pszHelpFilePath;
```

### <a name="remarks"></a>Remarks

既定では、フレームワークは`m_pszHelpFilePath` 、アプリケーションの名前に "" を指定して初期化します。HLP "が追加されています。 ヘルプファイルの名前を変更するには、 `m_pszHelpFilePath`をに設定して、目的のヘルプファイルの完全な名前を含む文字列を指定します。 これを行うための便利な場所は、アプリケーションの[InitInstance](#initinstance)関数です。 `m_pszHelpFilePath`**const char**<strong>\*</strong>型のパブリック変数です。

> [!NOTE]
> に`m_pszHelpFilePath`値を割り当てた場合は、ヒープに動的に割り当てられる必要があります。 デストラクター `CWinApp`は、このポインターを使用して**free**() を呼び出します。 多くの`_tcsdup`場合、() ランタイムライブラリ関数を使用して割り当てを実行します。 また、新しい値を割り当てる前に、現在のポインターに関連付けられているメモリを解放します。 例:

[!code-cpp[NVC_MFCWindowing#59](../../mfc/reference/codesnippet/cpp/cwinapp-class_21.cpp)]

##  <a name="m_pszprofilename"></a>  CWinApp::m_pszProfileName

アプリケーションのの名前を格納します。INI ファイル。

```
LPCTSTR m_pszProfileName;
```

### <a name="remarks"></a>Remarks

`m_pszProfileName`**const char**<strong>\*</strong>型のパブリック変数です。

> [!NOTE]
> に`m_pszProfileName`値を割り当てた場合は、ヒープに動的に割り当てられる必要があります。 デストラクター `CWinApp`は、このポインターを使用して**free**() を呼び出します。 多くの`_tcsdup`場合、() ランタイムライブラリ関数を使用して割り当てを実行します。 また、新しい値を割り当てる前に、現在のポインターに関連付けられているメモリを解放します。 例:

[!code-cpp[NVC_MFCWindowing#60](../../mfc/reference/codesnippet/cpp/cwinapp-class_22.cpp)]

##  <a name="m_pszregistrykey"></a>CWinApp:: m_pszRegistryKey

レジストリまたは INI ファイル内のアプリケーションプロファイル設定が格納されている場所を決定するために使用されます。

```
LPCTSTR m_pszRegistryKey;
```

### <a name="remarks"></a>Remarks

通常、このデータメンバーは読み取り専用として扱われます。

- 値はレジストリキーに格納されます。 アプリケーションプロファイル設定の名前は、次のレジストリキーに追加されます。HKEY_CURRENT_USER/Software/LocalAppWizard-Generated/。

に`m_pszRegistryKey`値を割り当てた場合は、ヒープに動的に割り当てられる必要があります。 デストラクター `CWinApp`は、このポインターを使用して**free**() を呼び出します。 多くの`_tcsdup`場合、() ランタイムライブラリ関数を使用して割り当てを実行します。 また、新しい値を割り当てる前に、現在のポインターに関連付けられているメモリを解放します。 例:

[!code-cpp[NVC_MFCWindowing#61](../../mfc/reference/codesnippet/cpp/cwinapp-class_23.cpp)]

##  <a name="m_pszappid"></a>  CWinApp::m_pszAppID

アプリケーションユーザーモデル ID。

```
LPCTSTR m_pszAppID;
```

### <a name="remarks"></a>Remarks

##  <a name="oncontexthelp"></a>  CWinApp::OnContextHelp

アプリケーション内の SHIFT + F1 ヘルプを処理します。

```
afx_msg void OnContextHelp();
```

### <a name="remarks"></a>Remarks

このメンバー関数を`ON_COMMAND( ID_CONTEXT_HELP, OnContextHelp )`有効にする`CWinApp`には、クラスメッセージマップにステートメントを追加し、アクセラレータテーブルエントリ (通常は SHIFT + F1 キー) も追加する必要があります。

`OnContextHelp`アプリケーションをヘルプモードにします。 カーソルが矢印と疑問符に変わり、ユーザーはマウスポインターを移動し、マウスの左ボタンを押して、ダイアログボックス、ウィンドウ、メニュー、またはコマンドボタンを選択できます。 このメンバー関数は、カーソルの下にあるオブジェクトのヘルプコンテキストを取得し、そのヘルプコンテキストを使用して Windows 関数 WinHelp を呼び出します。

##  <a name="onddecommand"></a>  CWinApp::OnDDECommand

メインフレームウィンドウが DDE 実行メッセージを受信すると、フレームワークによって呼び出されます。

```
virtual BOOL OnDDECommand(LPTSTR lpszCommand);
```

### <a name="parameters"></a>パラメーター

*lpszCommand*<br/>
アプリケーションによって受信された DDE コマンド文字列を指します。

### <a name="return-value"></a>戻り値

コマンドが処理される場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

既定の実装は、コマンドがドキュメントを開く要求であるかどうかを確認し、存在する場合は、指定されたドキュメントを開きます。 通常、Windows ファイルマネージャーは、ユーザーがデータファイルをダブルクリックしたときに、このような DDE コマンド文字列を送信します。 この関数をオーバーライドして、他の DDE 実行コマンド (印刷するコマンドなど) を処理します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#48](../../mfc/reference/codesnippet/cpp/cwinapp-class_24.cpp)]

##  <a name="onfilenew"></a>  CWinApp::OnFileNew

ID_FILE_NEW コマンドを実装します。

```
afx_msg void OnFileNew();
```

### <a name="remarks"></a>Remarks

このメンバー関数を`ON_COMMAND( ID_FILE_NEW, OnFileNew )`有効にする`CWinApp`には、ステートメントをクラスメッセージマップに追加する必要があります。 有効になっている場合、この関数は File New コマンドの実行を処理します。

既定の動作とこのメンバー関数をオーバーライドする方法については、「[テクニカルノート 22](../../mfc/tn022-standard-commands-implementation.md) 」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileopen"></a>  CWinApp::OnFileOpen

ID_FILE_OPEN コマンドを実装します。

```
afx_msg void OnFileOpen();
```

### <a name="remarks"></a>Remarks

このメンバー関数を`ON_COMMAND( ID_FILE_OPEN, OnFileOpen )`有効にする`CWinApp`には、ステートメントをクラスメッセージマップに追加する必要があります。 有効になっている場合、この関数は File Open コマンドの実行を処理します。

既定の動作と、このメンバー関数をオーバーライドする方法に関するガイダンスについては、「[テクニカルノート 22](../../mfc/tn022-standard-commands-implementation.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onfileprintsetup"></a>  CWinApp::OnFilePrintSetup

ID_FILE_PRINT_SETUP コマンドを実装します。

```
afx_msg void OnFilePrintSetup();
```

### <a name="remarks"></a>Remarks

このメンバー関数を`ON_COMMAND( ID_FILE_PRINT_SETUP, OnFilePrintSetup )`有効にする`CWinApp`には、ステートメントをクラスメッセージマップに追加する必要があります。 有効になっている場合、この関数は、ファイル印刷コマンドの実行を処理します。

既定の動作と、このメンバー関数をオーバーライドする方法に関するガイダンスについては、「[テクニカルノート 22](../../mfc/tn022-standard-commands-implementation.md)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#49](../../mfc/reference/codesnippet/cpp/cwinapp-class_25.cpp)]

[!code-cpp[NVC_MFCWindowing#50](../../mfc/reference/codesnippet/cpp/cwinapp-class_26.cpp)]

##  <a name="onhelp"></a>  CWinApp::OnHelp

アプリケーション内で F1 ヘルプを (現在のコンテキストを使って) 処理します。

```
afx_msg void OnHelp();
```

### <a name="remarks"></a>Remarks

通常は、F1 キーのアクセラレータキーのエントリも追加します。 F1 キーを有効にすることは、必須条件ではなく、規則にすぎません。

このメンバー関数を`ON_COMMAND( ID_HELP, OnHelp )`有効にする`CWinApp`には、ステートメントをクラスメッセージマップに追加する必要があります。 有効な場合は、ユーザーが F1 キーを押したときにフレームワークによって呼び出されます。

このメッセージハンドラー関数の既定の実装では、現在のウィンドウ、ダイアログボックス、またはメニュー項目に対応するヘルプコンテキストが決定され、WINHELP が呼び出されます。EXCEL.EXE. コンテキストが現在使用できない場合、関数は既定のコンテキストを使用します。

このメンバー関数をオーバーライドして、現在フォーカスがあるウィンドウ、ダイアログボックス、メニュー項目、またはツールバーボタン以外にヘルプコンテキストを設定します。 目的`WinHelp`のヘルプコンテキスト ID を指定してを呼び出します。

##  <a name="onhelpfinder"></a>CWinApp:: OnHelpFinder

ID_HELP_FINDER コマンドと ID_DEFAULT_HELP コマンドを処理します。

```
afx_msg void OnHelpFinder();
```

### <a name="remarks"></a>Remarks

このメンバー関数を`ON_COMMAND( ID_HELP_FINDER, OnHelpFinder )`有効にする`CWinApp`には、ステートメントをクラスメッセージマップに追加する必要があります。 有効にした場合、フレームワークは、アプリケーションのユーザーが Help Finder コマンドを選択して標準の**HELP_FINDER**トピック`WinHelp`で呼び出すヘルプファインダーコマンドを選択すると、このメッセージハンドラー関数を呼び出します。

##  <a name="onhelpindex"></a>  CWinApp::OnHelpIndex

ID_HELP_INDEX コマンドを処理し、既定のヘルプトピックを提供します。

```
afx_msg void OnHelpIndex();
```

### <a name="remarks"></a>Remarks

このメンバー関数を`ON_COMMAND( ID_HELP_INDEX, OnHelpIndex )`有効にする`CWinApp`には、ステートメントをクラスメッセージマップに追加する必要があります。 有効にした場合、フレームワークは、アプリケーションのユーザーが標準の`WinHelp` **HELP_INDEX**トピックで呼び出される Help Index コマンドを選択したときに、このメッセージハンドラー関数を呼び出します。

##  <a name="onhelpusing"></a>  CWinApp::OnHelpUsing

ID_HELP_USING コマンドを処理します。

```
afx_msg void OnHelpUsing();
```

### <a name="remarks"></a>Remarks

このメンバー関数を`ON_COMMAND( ID_HELP_USING, OnHelpUsing )`有効にする`CWinApp`には、ステートメントをクラスメッセージマップに追加する必要があります。 フレームワークは、アプリケーションのユーザーが [Help Using] コマンドを選択して標準の`WinHelp` **HELP_HELPONHELP**トピックでアプリケーションを呼び出すときに、このメッセージハンドラー関数を呼び出します。

##  <a name="onidle"></a>  CWinApp::OnIdle

アイドル時間の処理を実行するには、このメンバー関数をオーバーライドします。

```
virtual BOOL OnIdle(LONG lCount);
```

### <a name="parameters"></a>パラメーター

*lCount*<br/>
アプリケーションのメッセージキューが`OnIdle`空のときにが呼び出されるたびに、カウンターがインクリメントされます。 このカウントは、新しいメッセージが処理されるたびに0にリセットされます。 *LCount*パラメーターを使用すると、メッセージを処理せずにアプリケーションがアイドル状態になっている時間の相対的な長さを確認できます。

### <a name="return-value"></a>戻り値

アイドル状態の処理時間を増やすには0以外。アイドル時間がこれ以上必要ない場合は0。

### <a name="remarks"></a>Remarks

`OnIdle`は、アプリケーションのメッセージキューが空のときに、既定のメッセージループで呼び出されます。 オーバーライドを使用して、独自のバックグラウンドアイドルハンドラータスクを呼び出します。

`OnIdle`は、アイドル処理時間が不要であることを示すために0を返す必要があります。 *LCount*パラメーターは、メッセージキューが`OnIdle`空のときにが呼び出されるたびに増分され、新しいメッセージが処理されるたびに0にリセットされます。 この数に基づいて、異なるアイドルルーチンを呼び出すことができます。

次に、アイドルループ処理の概要を示します。

1. Microsoft Foundation Class ライブラリ内のメッセージループがメッセージキューを確認し、保留中のメッセージが検出さ`OnIdle`れなかった場合は、アプリケーションオブジェクトを呼び出し、 *lCount*引数として0を指定します。

2. `OnIdle`処理を実行し、0以外の値を返して、さらに処理を行うために再度呼び出す必要があることを示します。

3. メッセージループは、メッセージキューを再度確認します。 保留中のメッセージがない場合は`OnIdle` 、を再度呼び出して、 *lCount*引数をインクリメントします。

4. 最終的に`OnIdle`は、はすべてのアイドルタスクの処理を終了し、0を返します。 これにより、メッセージキューから次`OnIdle`のメッセージが受信されるまで呼び出しを停止するようメッセージループに指示します。この時点で、引数が0に設定された状態で、アイドルサイクルが再開されます。

アプリケーションがを返すまで`OnIdle` `OnIdle`ユーザー入力を処理できないため、時間のかかるタスクを実行しないでください。

> [!NOTE]
> 更新プログラムの既定`OnIdle`の実装では、メニュー項目やツールバーボタンなどのユーザーインターフェイスオブジェクトが実行され、内部データ構造のクリーンアップが実行されます。 したがって、をオーバーライド`OnIdle`する場合は、 `CWinApp::OnIdle`オーバーライドさ`lCount`れたバージョンのを使用してを呼び出す必要があります。 最初に、すべての基本クラスのアイドル処理を呼び出します (つまり、 `OnIdle`基底クラスが0を返すまで)。 基本クラスの処理が完了する前に作業を実行する必要がある場合は、基本クラスの実装を確認して、作業を行うための適切な*lCount*を選択します。

メッセージキューからメッセージが取得されるたびに `OnIdle` を呼び出さない場合は、[CWinThreadIsIdleMessage](../../mfc/reference/cwinthread-class.md#isidlemessage) をオーバーライドできます。 アプリケーションで非常に短いタイマーが設定されている場合、またはシステムが WM_SYSTIMER メッセージを`OnIdle`送信している場合は、が繰り返し呼び出され、パフォーマンスが低下します。

### <a name="example"></a>例

次の2つの例は、 `OnIdle`の使用方法を示しています。 最初の例では、 *lCount*引数を使用して2つのアイドルタスクを処理し、タスクの優先順位を設定します。 最初のタスクは優先度が高く、可能な場合はいつでも実行する必要があります。 2番目のタスクは重要度が低いため、ユーザー入力に長い待ち時間がある場合にのみ実行してください。 の`OnIdle`基本クラスバージョンへの呼び出しに注意してください。 2番目の例では、優先順位の異なるアイドルタスクのグループを管理します。

[!code-cpp[NVC_MFCWindowing#51](../../mfc/reference/codesnippet/cpp/cwinapp-class_27.cpp)]

##  <a name="opendocumentfile"></a>  CWinApp::OpenDocumentFile

フレームワークは、このメソッドを呼び出して、アプリケーションの名前付きの[CDocument](../../mfc/reference/cdocument-class.md)ファイルを開きます。

```
virtual CDocument* OpenDocumentFile(
    LPCTSTR lpszFileName
    BOOL bAddToMRU = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszFileName*<br/>
から開くファイルの名前。

*bAddToMRU*<br/>
からTRUE は、ドキュメントが最新のファイルの1つであることを示します。FALSE は、ドキュメントが最新のファイルの1つではないことを示します。

### <a name="return-value"></a>戻り値

成功し`CDocument`た場合はへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

その名前を持つドキュメントが既に開いている場合、そのドキュメントを含む最初のフレームウィンドウにフォーカスが移動します。 アプリケーションが複数のドキュメントテンプレートをサポートしている場合、フレームワークはファイル名拡張子を使用して、ドキュメントの読み込みを試みる適切なドキュメントテンプレートを検索します。 成功した場合は、ドキュメントテンプレートによって、ドキュメントのフレームウィンドウとビューが作成されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#52](../../mfc/reference/codesnippet/cpp/cwinapp-class_16.cpp)]

##  <a name="parsecommandline"></a>  CWinApp::ParseCommandLine

このメンバー関数を呼び出してコマンドラインを解析し、パラメーターを一度に1つずつ[CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)に送信します。

```
void ParseCommandLine(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>パラメーター

*rCmdInfo*<br/>
[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)オブジェクトへの参照。

### <a name="remarks"></a>Remarks

アプリケーションウィザードを使用して新しい MFC プロジェクトを開始すると、アプリケーションウィザードによっ`CCommandLineInfo`てのローカルインスタンスが作成され、 [InitInstance](#initinstance)メンバー関数でと`ParseCommandLine`が呼び出さ`ProcessShellCommand`れます。 コマンドラインは、次に示すルートに従います。

1. で`InitInstance`作成された`CCommandLineInfo`オブジェクトは、に`ParseCommandLine`渡されます。

2. `ParseCommandLine`次に`CCommandLineInfo::ParseParam` 、パラメーターごとに1回、を繰り返し呼び出します。

3. `ParseParam` が `CCommandLineInfo` オブジェクトを塗りつぶし、[ProcessShellCommand](#processshellcommand) に渡します。

4. `ProcessShellCommand`コマンドライン引数とフラグを処理します。

必要に応じてを`ParseCommandLine`直接呼び出すことができることに注意してください。

コマンドラインフラグの詳細については、「 [CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)」を参照してください。

##  <a name="pretranslatemessage"></a>  CWinApp::PreTranslateMessage

Windows 関数[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)にディスパッチされる前にウィンドウメッセージをフィルター処理するには、この関数をオーバーライドします。既定の実装では、アクセラレータキー変換が実行されるため`CWinApp::PreTranslateMessage`、オーバーライドされたバージョンのメンバー関数。

```
virtual BOOL PreTranslateMessage(MSG* pMsg);
```

### <a name="parameters"></a>パラメーター

*pMsg*<br/>
処理するメッセージを含む[MSG](/windows/win32/api/winuser/ns-winuser-msg)構造体へのポインター。

### <a name="return-value"></a>戻り値

メッセージがで完全に処理され`PreTranslateMessage` 、それ以上処理されない場合は0以外の。 メッセージを通常の方法で処理する必要がある場合は0。

##  <a name="processmessagefilter"></a>  CWinApp::ProcessMessageFilter

フレームワークのフック関数は、このメンバー関数を呼び出して、特定の Windows メッセージをフィルター処理して応答します。

```
virtual BOOL ProcessMessageFilter(
    int code,
    LPMSG lpMsg);
```

### <a name="parameters"></a>パラメーター

*code*<br/>
フックコードを指定します。 このメンバー関数は、コードを使用して、 *Lpmsg*の処理方法を決定します。

*lpMsg*<br/>
Windows[メッセージ](/windows/win32/api/winuser/ns-winuser-msg)structure へのポインター。

### <a name="return-value"></a>戻り値

メッセージが処理される場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

フック関数は、アプリケーションの通常のメッセージ処理に送信される前に、イベントを処理します。

この高度な機能をオーバーライドする場合は、フレームワークのフック処理を維持するために、基本クラスのバージョンを必ず呼び出してください。

##  <a name="processshellcommand"></a>  CWinApp::ProcessShellCommand

このメンバー関数は、 *rcmdinfo*によって識別される`CCommandLineInfo`オブジェクトから渡されたパラメーターを受け入れ、指定されたアクションを実行するために、 [InitInstance](#initinstance)によって呼び出されます。

```
BOOL ProcessShellCommand(CCommandLineInfo& rCmdInfo);
```

### <a name="parameters"></a>パラメーター

*rCmdInfo*<br/>
[CCommandLineInfo](../../mfc/reference/ccommandlineinfo-class.md)オブジェクトへの参照。

### <a name="return-value"></a>戻り値

シェルコマンドが正常に処理された場合は0以外の。 0の場合は、 [InitInstance](#initinstance)から FALSE を返します。

### <a name="remarks"></a>Remarks

アプリケーションウィザードを使用して新しい MFC プロジェクトを開始すると、アプリケーションウィザード`CCommandLineInfo`によってのローカルインスタンスが作成され、 `InitInstance`メンバー関数でと[ParseCommandLine](#parsecommandline)が呼び出さ`ProcessShellCommand`れます。 コマンドラインは、次に示すルートに従います。

1. で`InitInstance`作成された`CCommandLineInfo`オブジェクトは、に`ParseCommandLine`渡されます。

2. `ParseCommandLine`次に、パラメーターごとに1回、 [CCommandLineInfo::P arseparam](../../mfc/reference/ccommandlineinfo-class.md#parseparam)を繰り返し呼び出します。

3. `ParseParam`オブジェクトを`CCommandLineInfo`いっぱいにして、に`ProcessShellCommand`渡します。

4. `ProcessShellCommand`コマンドライン引数とフラグを処理します。

[CCommandLineInfo:: m_nShellCommand](../../mfc/reference/ccommandlineinfo-class.md#m_nshellcommand)で`CCommandLineInfo`識別されるオブジェクトのデータメンバーは、 `CCommandLineInfo`クラス内で定義されている次の列挙型です。

```
enum {
    FileNew,
    FileOpen,
    FilePrint,
    FilePrintTo,
    FileDDE
    };
```

これらの各値の簡単な説明について`CCommandLineInfo::m_nShellCommand`は、「」を参照してください。

##  <a name="processwndprocexception"></a>  CWinApp::ProcessWndProcException

このメンバー関数は、アプリケーションのメッセージハンドラーまたはコマンドハンドラーの1つでスローされた例外をハンドラーがキャッチしない場合は常に、フレームワークによって呼び出されます。

```
virtual LRESULT ProcessWndProcException(
    CException* e,
    const MSG* pMsg);
```

### <a name="parameters"></a>パラメーター

*e*<br/>
キャッチされていない例外へのポインター。

*pMsg*<br/>
フレームワークが例外をスローする原因となった windows メッセージに関する情報を含む[MSG](/windows/win32/api/winuser/ns-winuser-msg)structure。

### <a name="return-value"></a>戻り値

Windows に返される値。 通常、これは windows メッセージの場合は0L、コマンドメッセージの場合は 1L (TRUE) になります。

### <a name="remarks"></a>Remarks

このメンバー関数を直接呼び出さないでください。

このメンバー関数の既定の実装では、メッセージボックスが作成されます。 キャッチされていない例外がメニュー、ツールバー、またはアクセラレータコマンドのエラーによって発生した場合、メッセージボックスに "Command failed" というメッセージが表示されます。それ以外の場合は、"内部アプリケーションエラー" メッセージが表示されます。

このメンバー関数をオーバーライドして、例外のグローバルな処理を提供します。 メッセージボックスを表示する場合にのみ、基本機能を呼び出します。

##  <a name="register"></a>  CWinApp::Register

によって処理されない`RegisterShellFileTypes`すべての登録タスクを実行します。

```
virtual BOOL Register();
```

### <a name="return-value"></a>戻り値

正常に完了した場合はゼロ以外、それ以外の場合は 0 です。

### <a name="remarks"></a>Remarks

既定の実装では、単に TRUE が返されます。 カスタマイズされた登録手順を提供するには、この関数をオーバーライドします。

##  <a name="registershellfiletypes"></a>  CWinApp::RegisterShellFileTypes

このメンバー関数を呼び出して、すべてのアプリケーションのドキュメントの種類を Windows ファイルマネージャーに登録します。

```
void RegisterShellFileTypes(BOOL bCompat = FALSE);
```

### <a name="parameters"></a>パラメーター

*bCompat*<br/>
からTRUE を使用すると、シェルコマンドの登録エントリが Print および Print に追加され、ユーザーはシェルから直接ファイルを印刷したり、ファイルをプリンターオブジェクトにドラッグしたりできます。 また、DefaultIcon キーも追加します。 既定では、旧バージョンとの互換性のために、このパラメーターは FALSE です。

### <a name="remarks"></a>Remarks

これにより、ユーザーは、アプリケーションで作成されたデータファイルをファイルマネージャー内でダブルクリックして開くことができます。 アプリケーション`RegisterShellFileTypes`の各ドキュメントテンプレートに対して[、adddoctemplate](#adddoctemplate)を呼び出した後、を呼び出します。 また、`RegisterShellFileTypes` を呼び出すと、[EnableShellOpen](#enableshellopen) メンバー関数も呼び出されます。

`RegisterShellFileTypes`アプリケーションが保持する[CDocTemplate](../../mfc/reference/cdoctemplate-class.md)オブジェクトの一覧を反復処理し、各ドキュメントテンプレートについて、Windows がファイルの関連付けのために保持する登録データベースにエントリを追加します。 ファイルマネージャーは、ユーザーがダブルクリックしたときに、これらのエントリを使用してデータファイルを開きます。 これにより、を出荷する必要がなくなります。アプリケーションと共に REG ファイルを作成します。

> [!NOTE]
> `RegisterShellFileTypes`は、ユーザーが管理者権限でプログラムを実行した場合にのみ機能します。 プログラムに管理者権限がない場合、レジストリキーを変更することはできません。

指定したファイル名拡張子が登録データベースによって既に別の種類のファイルに関連付けられている場合、新しい関連付けは作成されません。 この情報`CDocTemplate`を登録するために必要な文字列の形式については、クラスを参照してください。

##  <a name="registerwithrestartmanager"></a>  CWinApp::RegisterWithRestartManager

アプリケーションを再起動マネージャーに登録します。

```
virtual HRESULT RegisterWithRestartManager(
    BOOL bRegisterRecoveryCallback,
    const CString& strRestartIdentifier);

virtual HRESULT RegisterWithRestartManager(
    LPCWSTR pwzCommandLineArgs,
    DWORD dwRestartFlags,
    APPLICATION_RECOVERY_CALLBACK pRecoveryCallback,
    LPVOID lpvParam,
    DWORD dwPingInterval,
    DWORD dwCallbackFlags);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*bRegisterRecoveryCallback*|からTRUE は、アプリケーションのこのインスタンスが復旧コールバック関数を使用することを示します。FALSE は、そうでないことを示します。 アプリケーションが予期せず終了した場合、フレームワークは回復コールバック関数を呼び出します。 詳細については、「 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)」を参照してください。|
|*strRestartIdentifier*|から再起動マネージャーのこのインスタンスを識別する一意の文字列。 Restart manager id は、アプリケーションの各インスタンスに対して一意です。|
|*pwzCommandLineArgs*|からコマンドラインからの追加の引数を含む文字列。|
|*dwRestartFlags*|から再起動マネージャーのオプションフラグ。 詳細については、「解説」を参照してください。|
|*Preco・コールバック*|から回復コールバック関数。 この関数は、LPVOID パラメーターを入力として受け取り、DWORD を返す必要があります。 既定の回復コールバック関数`CWinApp::ApplicationRecoveryCallback`はです。|
|*lpvParam*|から復旧コールバック関数の入力パラメーター。 詳細については、「 [CWinApp:: ApplicationRecoveryCallback](#applicationrecoverycallback)」を参照してください。|
|*dwPingInterval*|から再起動マネージャーが復旧コールバック関数から戻るまで待機する時間の長さ。 このパラメーターは、ミリ秒単位で指定します。|
|*Dwのフラグ*|から復旧コールバック関数に渡されるフラグ。 将来使用するために予約されています。|

### <a name="return-value"></a>戻り値

メソッドが成功した場合は S_OK。それ以外の場合は、エラーコード。

### <a name="remarks"></a>Remarks

アプリケーションでワークファイルに既定の MFC 実装を使用する場合は、の`RegisterWithRestartManager`単純なバージョンを使用する必要があります。 アプリケーションの自動保存動作`RegisterWithRestartManager`をカスタマイズする場合は、の複合バージョンを使用します。

*StrRestartIdentifier*に空の文字列を指定してこのメソッドを`RegisterWithRestartManager`呼び出すと、によって、再起動マネージャーのこのインスタンスの一意の識別子文字列が作成されます。

アプリケーションが予期せず終了すると、再起動マネージャーによってアプリケーションがコマンドラインから再起動され、一意の再起動識別子がオプションの引数として提供されます。 このシナリオでは、フレームワークは`RegisterWithRestartManager` 2 回を呼び出します。 最初の呼び出しは、文字列識別子に対して空の文字列を使用して、 [CWinApp:: InitInstance](#initinstance)から取得されます。 次に、メソッド[CWinApp::P rocessshellcommand](#processshellcommand)は`RegisterWithRestartManager` 、一意の再起動識別子を使用してを呼び出します。

アプリケーションを再起動マネージャーに登録すると、再起動マネージャーによってアプリケーションが監視されます。 アプリケーションが予期せず終了した場合、再起動マネージャーは、シャットダウンプロセス中に復旧コールバック関数を呼び出します。 再起動マネージャーは、回復コールバック関数からの応答に対して*Dwpinginterval*を待機します。 復旧コールバック関数がこの時間内に応答しない場合、アプリケーションは復旧コールバック関数を実行せずに終了します。

既定では、dwRestartFlags はサポートされていませんが、将来使用するために提供されています。 *DwRestartFlags*に指定できる値は次のとおりです。

- RESTART_NO_CRASH

- RESTART_NO_HANG

- RESTART_NO_PATCH

- RESTART_NO_REBOOT

##  <a name="reopenpreviousfilesatrestart"></a>  CWinApp::ReopenPreviousFilesAtRestart

アプリケーションが予期せず終了したときに開いたファイルを再起動マネージャーが再度開くかどうかを指定します。

```
virtual BOOL ReopenPreviousFilesAtRestart() const;
```

### <a name="return-value"></a>戻り値

[TRUE] を指定すると、再起動マネージャーによって以前に開いたファイルが再度開かれます。FALSE は、再起動マネージャーではないことを示します。

##  <a name="restartinstance"></a>  CWinApp::RestartInstance

再起動マネージャーによって開始されたアプリケーションの再起動を処理します。

```
virtual BOOL CWinApp::RestartInstance();
```

### <a name="return-value"></a>戻り値

データ復旧ハンドラーが以前に開いたドキュメントを開く場合は TRUE。データ回復ハンドラーにエラーがある場合、または以前に開いていたドキュメントがない場合は FALSE。

### <a name="remarks"></a>Remarks

再起動マネージャーによってアプリケーションが再起動されると、フレームワークはこのメソッドを呼び出します。 このメソッドは、データ復旧ハンドラーを取得し、自動保存されたファイルを復元します。 このメソッドは、 [CDataRecoveryHandler:: RestoreAutosavedDocuments](../../mfc/reference/cdatarecoveryhandler-class.md#restoreautosaveddocuments)を呼び出して、ユーザーが自動保存されたファイルを復元する必要があるかどうかを判断します。

[CDataRecoveryHandler](../../mfc/reference/cdatarecoveryhandler-class.md)が開いているドキュメントがないと判断した場合、このメソッドは FALSE を返します。 開いているドキュメントがない場合は、通常、アプリケーションが起動します。

##  <a name="restoreautosavedfilesatrestart"></a>  CWinApp::RestoreAutosavedFilesAtRestart

再起動マネージャーが、アプリケーションの再起動時に自動保存されたファイルを復元するかどうかを指定します。

```
virtual BOOL RestoreAutosavedFilesAtRestart() const;
```

### <a name="return-value"></a>戻り値

TRUE は、再起動マネージャーが自動保存されたファイルを復元することを示します。FALSE は、再起動マネージャーではないことを示します。

##  <a name="run"></a>  CWinApp::Run

既定のメッセージループを提供します。

```
virtual int Run();
```

### <a name="return-value"></a>戻り値

によって`WinMain`返される int 値。

### <a name="remarks"></a>Remarks

`Run`アプリケーションが WM_QUIT メッセージを受信するまで、Windows メッセージを取得してディスパッチします。 アプリケーションのメッセージキューに現在メッセージが含まれていない場合、`Run` は [OnIdle](#onidle) を呼び出して、アイドル時の処理を実行します。 受信メッセージは、特別な処理のために[PreTranslateMessage](#pretranslatemessage)メンバー関数に移動し、 `TranslateMessage`標準キーボード翻訳の windows 関数に移動`DispatchMessage`します。最後に、windows 関数が呼び出されます。

`Run`がオーバーライドされることはほとんどありませんが、これをオーバーライドして特殊な動作を提供することができます。

##  <a name="runautomated"></a>CWinApp:: RunAutomated

この関数を呼び出して、サーバーアプリケーションがクライアントアプリケーションによって起動されたかどうかを示す " **/Automation**" または " **-Automation**" オプションが存在するかどうかを確認します。

```
BOOL RunAutomated();
```

### <a name="return-value"></a>戻り値

オプションが見つかった場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このオプションが指定されている場合、コマンドラインからオプションが削除されます。 OLE オートメーションの詳細については、「[オートメーションサーバー](../../mfc/automation-servers.md)」を参照してください。

##  <a name="runembedded"></a>  CWinApp::RunEmbedded

この関数を呼び出して、サーバーアプリケーションがクライアントアプリケーションによって起動されたかどうかを示す " **/Embedding**" または " **-埋め込み**" オプションが存在するかどうかを確認します。

```
BOOL RunEmbedded();
```

### <a name="return-value"></a>戻り値

オプションが見つかった場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

このオプションが指定されている場合、コマンドラインからオプションが削除されます。 埋め込みの詳細については、 [「サーバー:サーバー](../../mfc/servers-implementing-a-server.md)の実装。

##  <a name="saveallmodified"></a>CWinApp:: SaveAllModified

アプリケーションのメインフレームウィンドウを閉じるとき、または WM_QUERYENDSESSION メッセージを使用して、すべてのドキュメントを保存するためにフレームワークによって呼び出されます。

```
virtual BOOL SaveAllModified();
```

### <a name="return-value"></a>戻り値

アプリケーションを安全に終了する場合は0以外。アプリケーションを安全に終了できない場合は0。

### <a name="remarks"></a>Remarks

このメンバー関数の既定の実装では、アプリケーション内の変更されたすべてのドキュメントに対して、 [CDocument:: SaveModified](../../mfc/reference/cdocument-class.md#savemodified)メンバー関数が順に呼び出されます。

##  <a name="selectprinter"></a>CWinApp:: SelectPrinter

このメンバー関数を呼び出して特定のプリンターを選択し、[印刷] ダイアログボックスで以前に選択したプリンターを解放します。

```
void SelectPrinter(
    HANDLE hDevNames,
    HANDLE hDevMode,
    BOOL bFreeOld = TRUE);
```

### <a name="parameters"></a>パラメーター

*hDevNames*<br/>
特定のプリンターのドライバー、デバイス、および出力ポート名を識別する[DEVNAMES](/windows/win32/api/commdlg/ns-commdlg-devnames)structure へのハンドル。

*hDevMode*<br/>
プリンターのデバイスの初期化と環境に関する情報を指定する[DEVMODE](/windows/win32/api/wingdi/ns-wingdi-devmodea)構造体を示すハンドル。

*bFreeOld*<br/>
以前に選択されたプリンターを解放します。

### <a name="remarks"></a>Remarks

*Hdevmode*と*hDevNames*の両方が NULL の`SelectPrinter`場合、では現在の既定のプリンターが使用されます。

##  <a name="sethelpmode"></a>CWinApp:: Se@ Pmode

アプリケーションのヘルプの種類を設定します。

```
void SetHelpMode(AFX_HELP_TYPE eHelpType);
```

### <a name="parameters"></a>パラメーター

*eHelpType*<br/>
使用するヘルプの種類を指定します。 詳細については、「 [CWinApp:: m_eHelpType](#m_ehelptype) 」を参照してください。

### <a name="remarks"></a>Remarks

アプリケーションのヘルプの種類を設定します。

アプリケーションのヘルプの種類を Html ヘルプに設定するには、 [Enablehtmlhelp](#enablehtmlhelp)を呼び出します。 を呼び出し`EnableHTMLHelp`た後、アプリケーションはヘルプアプリケーションとして html を使用する必要があります。 WinHelp を使用するようにを変更する場合は、 `SetHelpMode`を呼び出して、 *ehelptype*をに`afxWinHelp`設定します。

##  <a name="setregistrykey"></a>CWinApp:: SetRegistryKey

アプリケーション設定を INI ファイルではなくレジストリに格納します。

```
void SetRegistryKey(LPCTSTR lpszRegistryKey);
void SetRegistryKey(UINT nIDRegistryKey);
```

### <a name="parameters"></a>パラメーター

*lpszRegistryKey*<br/>
キーの名前を格納している文字列へのポインター。

*nIDRegistryKey*<br/>
レジストリキーの名前を含む文字列リソースの ID。

### <a name="remarks"></a>Remarks

この関数は *、m_pszRegistryKey*を設定します。この`GetProfileInt`関数`GetProfileString`は`WriteProfileInt` `WriteProfileString` 、の、、、 `CWinApp`の各メンバー関数によって使用されます。 この関数が呼び出された場合は、最近使用した (MRU) ファイルの一覧もレジストリに格納されます。 通常、レジストリキーは会社の名前です。 次の形式のキーに格納されています。HKEY_CURRENT_USER\Software\\< 会社名\>\\< アプリケーション名\><セクション名\><値\>の名前。\\\\

##  <a name="supportsapplicationrecovery"></a>  CWinApp::SupportsApplicationRecovery

予期せずに終了したアプリケーションを再起動マネージャーが回復するかどうかを指定します。

```
virtual BOOL SupportsApplicationRecovery() const;
```

### <a name="return-value"></a>戻り値

TRUE を指定すると、再起動マネージャーによってアプリケーションが復旧されます。FALSE は、再起動マネージャーではないことを示します。

##  <a name="supportsautosaveatinterval"></a>CWinApp:: SupportsAutosaveAtInterval

再起動マネージャーが開いているドキュメントを一定の間隔で自動保存するかどうかを指定します。

```
virtual BOOL SupportsAutosaveAtInterval() const;
```

### <a name="return-value"></a>戻り値

TRUE は、再起動マネージャーが開いているドキュメントを自動保存することを示します。FALSE は、再起動マネージャーではないことを示します。

##  <a name="supportsautosaveatrestart"></a>CWinApp:: SupportsAutosaveAtRestart

アプリケーションの再起動時に、再起動マネージャーが開いているドキュメントを自動保存するかどうかを指定します。

```
virtual BOOL SupportsAutosaveAtRestart() const;
```

### <a name="return-value"></a>戻り値

TRUE は、アプリケーションの再起動時に、再起動マネージャーが開いているドキュメントを自動保存することを示します。FALSE は、再起動マネージャーではないことを示します。

##  <a name="supportsrestartmanager"></a>CWinApp:: SupportsRestartManager

アプリケーションが再起動マネージャーをサポートしているかどうかを判断します。

```
virtual BOOL SupportsRestartManager() const;
```

### <a name="return-value"></a>戻り値

TRUE は、アプリケーションが再起動マネージャーをサポートしていることを示します。FALSE は、アプリケーションがそうでないことを示します。

##  <a name="unregister"></a>  CWinApp::Unregister

アプリケーションオブジェクトによって登録されたすべてのファイルの登録を解除します。

```
virtual BOOL Unregister();
```

### <a name="return-value"></a>戻り値

正常に完了した場合はゼロ以外、それ以外の場合は 0 です。

### <a name="remarks"></a>Remarks

関数`Unregister`は、アプリケーションオブジェクトと[Register](#register)関数によって実行される登録を元に戻します。 通常、どちらの関数も MFC によって暗黙的に呼び出されるため、コードには表示されません。

この関数をオーバーライドして、カスタム登録解除手順を実行します。

##  <a name="unregistershellfiletypes"></a>  CWinApp::UnregisterShellFileTypes

このメンバー関数を呼び出して、すべてのアプリケーションのドキュメントの種類を Windows ファイルマネージャーで登録解除します。

```
void UnregisterShellFileTypes();
```

##  <a name="winhelp"></a>CWinApp:: WinHelp

このメンバー関数を呼び出して、WinHelp アプリケーションを呼び出します。

```
virtual void WinHelp(
    DWORD_PTR dwData,
    UINT nCmd = HELP_CONTEXT);
```

### <a name="parameters"></a>パラメーター

*dwData*<br/>
追加データを指定します。 使用される値は、 *Ncmd*パラメーターの値によって異なります。

*nCmd*<br/>
要求されるヘルプの種類を指定します。 使用可能な値の一覧と*Dwdata*パラメーターへの影響については、「 [WinHelp](/windows/win32/api/winuser/nf-winuser-winhelpw) Windows 関数」を参照してください。

### <a name="remarks"></a>Remarks

フレームワークは、この関数を呼び出して WinHelp アプリケーションを起動することもできます。

アプリケーションが終了すると、フレームワークによって WinHelp アプリケーションが自動的に閉じられます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#53](../../mfc/reference/codesnippet/cpp/cwinapp-class_28.cpp)]

##  <a name="writeprofilebinary"></a>CWinApp:: WriteProfileBinary

アプリケーションのレジストリまたはの指定したセクションにバイナリデータを書き込むには、このメンバー関数を呼び出します。INI ファイル。

```
BOOL WriteProfileBinary(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPBYTE pData,
    UINT nBytes);
```

### <a name="parameters"></a>パラメーター

*lpszSection*<br/>
エントリがあるセクションを指定する NULL で終わる文字列へのポインター。 セクションが存在しない場合は、作成されます。 セクションの名前は大文字と小文字が区別されません。文字列には、大文字と小文字の任意の組み合わせを使用できます。

*lpszEntry*<br/>
は、値の書き込み先のエントリを含む、null で終わる文字列を指します。 指定したセクションにエントリが存在しない場合は、作成されます。

*pData*<br/>
書き込まれるデータを指します。

*nBytes*<br/>
書き込まれるバイト数を格納します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

この例で`CWinApp* pApp = AfxGetApp();`は、を使用して、MFC アプリケーションの`WriteProfileBinary`任意`GetProfileBinary`の関数からとを使用する方法を示す CWinApp クラスを取得します。

[!code-cpp[NVC_MFCWindowing#54](../../mfc/reference/codesnippet/cpp/cwinapp-class_29.cpp)]

別の例については、「 [CWinApp:: GetProfileBinary](#getprofilebinary)」の例を参照してください。

##  <a name="writeprofileint"></a>CWinApp:: WriteProfileInt

このメンバー関数を呼び出して、指定した値をアプリケーションのレジストリまたはの指定したセクションに書き込みます。INI ファイル。

```
BOOL WriteProfileInt(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    int nValue);
```

### <a name="parameters"></a>パラメーター

*lpszSection*<br/>
エントリがあるセクションを指定する NULL で終わる文字列へのポインター。 セクションが存在しない場合は、作成されます。 セクションの名前は大文字と小文字が区別されません。文字列には、大文字と小文字の任意の組み合わせを使用できます。

*lpszEntry*<br/>
は、値の書き込み先のエントリを含む、null で終わる文字列を指します。 指定したセクションにエントリが存在しない場合は、作成されます。

*nValue*<br/>
書き込む値を格納します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

この例で`CWinApp* pApp = AfxGetApp();`は、を使用して、MFC アプリケーションの任意の`GetProfileString`関数から`GetProfileInt` 、、、およびを使用できる方法を`WriteProfileInt`示す`WriteProfileString`CWinApp クラスを取得します。

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

別の例については、「 [CWinApp:: GetProfileInt](#getprofileint)」の例を参照してください。

##  <a name="writeprofilestring"></a>  CWinApp::WriteProfileString

このメンバー関数を呼び出して、指定した文字列をアプリケーションのレジストリまたはの指定したセクションに書き込みます。INI ファイル。

```
BOOL WriteProfileString(
    LPCTSTR lpszSection,
    LPCTSTR lpszEntry,
    LPCTSTR lpszValue);
```

### <a name="parameters"></a>パラメーター

*lpszSection*<br/>
エントリがあるセクションを指定する NULL で終わる文字列へのポインター。 セクションが存在しない場合は、作成されます。 セクションの名前は大文字と小文字が区別されません。文字列には、大文字と小文字の任意の組み合わせを使用できます。

*lpszEntry*<br/>
は、値の書き込み先のエントリを含む、null で終わる文字列を指します。 指定したセクションにエントリが存在しない場合は、作成されます。 このパラメーターが NULL の場合、 *lpszsection*によって指定されたセクションが削除されます。

*lpszValue*<br/>
書き込まれる文字列を指します。 このパラメーターが NULL の場合、 *lpszEntry*パラメーターによって指定されたエントリは削除されます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCWindowing#43](../../mfc/reference/codesnippet/cpp/cwinapp-class_9.cpp)]

別の例については、「 [CWinApp:: GetProfileInt](#getprofileint)」の例を参照してください。

##  <a name="setappid"></a>CWinApp:: SetAppID

アプリケーションのアプリケーションユーザーモデル ID を明示的に設定します。 ユーザーインターフェイスをユーザーに提示する前に、このメソッドを呼び出す必要があります (最適な場所はアプリケーションコンストラクターです)。

```
void SetAppID(LPCTSTR lpcszAppID);
```

### <a name="parameters"></a>パラメーター

*lpcszAppID*<br/>
アプリケーションユーザーモデル ID を指定します。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[CWinThread クラス](../../mfc/reference/cwinthread-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[方法: 再起動マネージャーのサポートを追加する](../../mfc/how-to-add-restart-manager-support.md)
