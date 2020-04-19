---
title: TN028:状況依存のヘルプのサポート
ms.date: 11/04/2016
f1_keywords:
- vc.help
helpviewer_keywords:
- context-sensitive Help [MFC], MFC applications
- TN028
- resource identifiers, context-sensitive Help
ms.assetid: 884f1c55-fa27-4d4c-984f-30907d477484
ms.openlocfilehash: 5689e314c2ba94068619a066e5f458e06819b2b7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305984"
---
# <a name="tn028-context-sensitive-help-support"></a>TN028:状況依存のヘルプのサポート

ここでは、ヘルプ コンテキスト Id と MFC の他のヘルプの問題を割り当てるための規則について説明します。 状況依存のヘルプのサポートには、Visual C で使用できるヘルプ コンパイラが必要です。

> [!NOTE]
>  WinHelp を使用して、状況依存のヘルプを実装するだけでなく、HTML ヘルプの使用を MFC もサポートします。 このサポートおよび HTML ヘルプを使用したプログラミングの詳細については、次を参照してください。 [HTML ヘルプ。プログラムの状況依存のヘルプ](../mfc/html-help-context-sensitive-help-for-your-programs.md)します。

## <a name="types-of-help-supported"></a>サポートされているヘルプの種類

Windows アプリケーションで実装される状況依存のヘルプの 2 種類があります。 まずと呼ばれる"F1"WinHelp を現在アクティブなオブジェクトに基づき、適切なコンテキストで起動する必要があります。 2 つ目は、"Shift + F1"モードです。 このモードでは、ヘルプ カーソルにマウス カーソルが変更され、オブジェクトをクリックして、ユーザーが続行されます。 その時点では、ユーザーをクリックしたオブジェクトのヘルプを提供する WinHelp が起動されます。

Microsoft Foundation Classes は、これらの形式のヘルプの両方を実装します。 さらに、フレームワークでは、ヘルプとヘルプを使用して、2 つの簡単なヘルプ コマンドをサポートしています。

## <a name="help-files"></a>ヘルプ ファイル

Microsoft Foundation classes には、1 つのヘルプ ファイルがあるとします。 ヘルプ ファイルは、アプリケーションと同じ名前とパスが必要です。 たとえば、実行可能ファイルが C:\MyApplication\MyHelp.exe 場合ヘルプ ファイルは C:\MyApplication\MyHelp.hlp である必要があります。 使用してパスを設定する、*ポインター*のメンバー変数、 [CWinApp クラス](../mfc/reference/cwinapp-class.md)します。

## <a name="help-context-ranges"></a>ヘルプ コンテキストの範囲

MFC の既定の実装では、プログラムのヘルプ コンテキスト Id の割り当てに関するいくつかの規則に従う必要があります。 これらの規則は、特定のコントロールに割り当てられている Id の範囲です。 さまざまなヘルプに関連するメンバー関数のさまざまな実装を提供することで、これらのルールを上書きできます。

```
0x00000000 - 0x0000FFFF : user defined
0x00010000 - 0x0001FFFF : commands (menus/command buttons)
0x00010000 + ID_
(note: 0x18000-> 0x1FFFF is the practical range since command IDs are>=0x8000)
0x00020000 - 0x0002FFFF : windows and dialogs
0x00020000 + IDR_
(note: 0x20000-> 0x27FFF is the practical range since IDRs are <= 0x7FFF)
0x00030000 - 0x0003FFFF : error messages (based on error string ID)
0x00030000 + IDP_
0x00040000 - 0x0004FFFF : special purpose (non-client areas)
0x00040000 + HitTest area
0x00050000 - 0x0005FFFF : controls (those that are not commands)
0x00040000 + IDW_
```

## <a name="simple-help-commands"></a>単純な"Help"コマンド

これには、Microsoft Foundation Classes によって実装される 2 つの簡単なヘルプ コマンドがあります。

- によって実装される ID_HELP_INDEX [CWinApp::OnHelpIndex](../mfc/reference/cwinapp-class.md#onhelpindex)

- によって実装される ID_HELP_USING [CWinApp::OnHelpUsing](../mfc/reference/cwinapp-class.md#onhelpusing)

最初のコマンドは、アプリケーションのヘルプ インデックスを示しています。 2 つ目は、WinHelp プログラムを使用してユーザー ヘルプを示します。

## <a name="context-sensitive-help-f1-help"></a>状況依存のヘルプ (F1 ヘルプ)

F1 キーは、メイン ウィンドウのアクセラレータ テーブルにアクセラレータでは、通常の ID の ID_HELP コマンドに変換されます。 ID_HELP コマンドは、メイン ウィンドウまたはダイアログ ボックスの ID の ID_HELP いるボタンも生成されます。

ID_HELP コマンドを生成する方法に関係なく、コマンド ハンドラーに到達するまで、通常のコマンドとしてルーティングされます。 MFC コマンド ルーティング アーキテクチャの詳細についてを参照してください[テクニカル ノート 21](../mfc/tn021-command-and-message-routing.md)します。 ID_HELP コマンドによって処理されるアプリケーションにヘルプが有効になっている場合、 [:onhelp](../mfc/reference/cwinapp-class.md#onhelp)します。 アプリケーション オブジェクトは、ヘルプ メッセージを受信し、コマンドを適切にルーティングします。 これは、機能は、既定のコマンド ルーティングが最も具体的なコンテキストを決定するために十分でないため必要です。

`CWinApp::OnHelp` 次の順序で WinHelp を起動しようとしています。

1. アクティブなチェック`AfxMessageBox`ヘルプ ID を呼び出す メッセージ ボックスが現在アクティブな場合は、WinHelp がそのメッセージ ボックスに適切なコンテキストで起動します。

1. アクティブなウィンドウをようメッセージを送信します。 WinHelp を起動することでそのウィンドウが応答しない場合に、メッセージが処理されたか、現在のウィンドウがトップレベル ウィンドウまで、同じメッセージはそのウィンドウの祖先に送信されます。

1. ID_DEFAULT_HELP コマンドは、メイン ウィンドウに送信します。 これは、既定のヘルプを起動します。 このコマンドは通常に`CWinApp::OnHelpIndex`します。

グローバルに既定の ID ベース値 (コマンドの 0x10000 など 0x20000 ダイアログなどのリソースの) を無効にするアプリケーションをオーバーライドする必要があります[cwinapp::winhelp](../mfc/reference/cwinapp-class.md#winhelp)します。

この機能とヘルプ コンテキストが決定される方法を無効にするには、ようメッセージを処理する必要があります。 ルーティングを提供する具体的なヘルプ、framework よりのみ現在の MDI 子ウィンドウとしてディープがたい場合があります。 特定のウィンドウまたはダイアログ ボックスで、そのオブジェクトまたはダイアログ内でアクティブなコントロールの現在の内部状態に基づくなどの特定のヘルプを提供することもできます。

## <a name="wmcommandhelp"></a>よう

```

afx_msg LRESULT CWnd::OnCommandHelp(WPARAM wParam, LPARAM lParam)
```

ようは、ヘルプが要求されたときにアクティブなウィンドウによって受信されるプライベート Windows MFC メッセージです。 呼び出す必要があります、ウィンドウは、このメッセージを受信したときに`CWinApp::WinHelp`ウィンドウの内部状態と一致するコンテキストを使用します。

*lParam*<br/>
現在使用可能なヘルプ コンテキストが含まれています。 *lParam*ヘルプ コンテキストが特定されていない場合は 0。 実装`OnCommandHelp`でコンテキスト ID を使用して*lParam*に異なるコンテキストの決定またはに渡すことができますのみ`CWinApp::WinHelp`します。

*wParam*<br/>
使用されず、0 になります。

場合、`OnCommandHelp`関数呼び出し`CWinApp::WinHelp`が返されます**TRUE**します。 返す**TRUE**他のクラス、および他のウィンドウには、このコマンドのルーティングを停止します。

## <a name="help-mode-shiftf1-help"></a>ヘルプ モード (Shift + F1 ヘルプ)

これは、状況依存のヘルプの 2 番目の形式です。 一般に、このモードは、shift キーを押しながら f1 キーを押すか、メニューとツールバーを使用して入力されます。 コマンド (ID_CONTEXT_HELP) として実装されます。 モーダル ダイアログ ボックスの中にこのコマンドを変換するメッセージ フィルターのフックが設定されていない、またはメニューがアクティブなしたがってこのコマンドはユーザーが利用できる場合にのみアプリケーションのメイン メッセージ ポンプを実行 (`CWinApp::Run`)。

このモードを入力すると、ヘルプのマウス カーソルが場合でも、その領域 (ウィンドウの周囲のサイズ変更境界線) などの独自のカーソルと、アプリケーションは通常表示、アプリケーションのすべての領域に表示されます。 ユーザーは、コマンドを選択するマウスやキーボードを使用することができます。 コマンドを実行するには、代わりにそのコマンドのヘルプが表示されます。 また、ユーザーは、ツールバーのボタンなど、画面に表示可能なオブジェクトをクリックして、そのオブジェクトのヘルプが表示されます。 このモードのヘルプがによって提供される`CWinApp::OnContextHelp`します。

このループの実行中には、すべてのキーボード入力がアクティブで、メニューにアクセス キーを除く。 また、コマンドの翻訳を使用して実行も`PreTranslateMessage`アクセラレータ キーを押すし、そのコマンドのヘルプを表示するユーザーを許可します。

翻訳または実行されているアクションが配置の特定がある場合、`PreTranslateMessage`関数は中に行われる shift キーを押しながら f1 キー ヘルプ モードの場合は、確認する必要があります、 *m_bHelpMode*のメンバー`CWinApp`ものを実行する前に操作です。 `CDialog`の実装`PreTranslateMessage`呼び出す前にこのフラグをチェック`IsDialogMessage`など。 これには、shift キーを押しながら F1 モード中にモードレス ダイアログ ボックスの「ダイアログ ナビゲーション」キーが無効にします。 さらに、`CWinApp::OnIdle`はこのループの中に呼び出されます。

場合は、ユーザーは、メニューからコマンドを選択、そのコマンドのヘルプとして処理されます (よう、を通じて以下参照)。 ユーザーは、アプリケーション ウィンドウの表示領域をクリックするは、については、非クライアントまたはクライアントをクリックするかどうかを決定が行われます。 `OnContextHelp` 非クライアントのハンドルのマッピングを自動的にクライアントをクリックしてクリックします。 クライアントの場合、領域をクリックしたウィンドウに送信します。 そのウィンドウが 0 以外の値を返す場合、その値がヘルプ コンテキストとして使用されます。 0 が返された場合`OnContextHelp`親ウィンドウを試みます (と失敗をその親、およびなど)。 マップされます (通常は)、メイン ウィンドウに ID_DEFAULT_HELP コマンドを送信する既定値は、ヘルプ コンテキストを決定できない場合`CWinApp::OnHelpIndex`します。

## <a name="wmhelphittest"></a>領域

```

afx_msg LRESULT CWnd::OnHelpHitTest(
WPARAM, LPARAM lParam)
```

領域は、shift キーを押しながら f1 キー ヘルプ モードの実行時にアクティブなウィンドウによって受信される MFC プライベート windows メッセージです。 返します、ウィンドウは、このメッセージを受信した場合、 **DWORD** WinHelp で使用するためのヘルプの ID。

LOWORD(lParam) には、ウィンドウのクライアント領域を基準とマウスがクリックしてされた位置の x 軸デバイス座標が含まれています。

HIWORD(lParam) には、y 軸座標が含まれています。

*wParam*<br/>
使用されず、0 になります。 戻り値が 0 以外の場合は、WinHelp はそのコンテキストで呼び出されます。 戻り値が 0 の場合は、親ウィンドウのヘルプが照会されます。

多くの場合は、ヒット テストのコードは既にを活用できます。 実装を参照してください。`CToolBar::OnHelpHitTest`領域メッセージの処理の例については (コードは、ボタンのツールヒントに使用するヒット テストのコードを活用して`CControlBar`)。

## <a name="mfc-application-wizard-support-and-makehm"></a>MFC アプリケーション ウィザードのサポートおよび MAKEHM

MFC アプリケーション ウィザードでは、ヘルプ ファイル (.cnt および .hpj ファイル) をビルドするために必要なファイルを作成します。 Microsoft ヘルプ コンパイラによって受け入れられる事前構築済みの .rtf ファイル数も含まれています。 完了すると、多くのトピックがいくつかは、特定のアプリケーションを変更する必要があります。

「ヘルプ マッピング」ファイルの自動作成は、makehm ユーティリティによってサポートされます。 MAKEHM ユーティリティでは、アプリケーションのリソースを翻訳できます。ヘルプのマッピング ファイルを H ファイルです。 例えば:

```
#define IDD_MY_DIALOG   2000
#define ID_MY_COMMAND   150
```

変換されます。

```
HIDD_MY_DIALOG    0x207d0
HID_MY_COMMAND    0x10096
```

この形式はヘルプ コンパイラの機能は、トピック名 (左側にあるシンボル) のコンテキスト Id (右側にある数値) のマップとの互換性。

MAKEHM のソース コードは、MFC のプログラミングのユーティリティのサンプルで使用できる[MAKEHM](../overview/visual-cpp-samples.md)します。

## <a name="adding-help-support-after-running-the-mfc-application-wizard"></a>MFC アプリケーション ウィザードの実行後のヘルプのサポートを追加します。

アプリケーションにヘルプを追加する最善の方法では、アプリケーションを作成する前に、MFC アプリケーション ウィザードの [高度な機能] ページで、「状況依存のヘルプ」オプションを確認します。 その方法 MFC アプリケーション ウィザードを自動的に追加するために必要なメッセージ マップ エントリ、 `CWinApp`-ヘルプをサポートするクラスを派生します。

## <a name="help-on-message-boxes"></a>メッセージ ボックスをヘルプします。

(アラートとも呼ばれます) のメッセージ ボックスのヘルプは、`AfxMessageBox`関数では、ラッパー、 `MessageBox` Windows API。

2 つのバージョンがある`AfxMessageBox`、文字列へのポインターを使用するための別の文字列 ID と使用のいずれか (`LPCSTR`)。

```
int AFXAPI AfxMessageBox(LPCSTR lpszText,
    UINT nType,
    UINT nIDHelp);

int AFXAPI AfxMessageBox(UINT nIDPrompt,
    UINT nType,
    UINT nIDHelp);
```

どちらの場合である、省略可能なヘルプは ID です。

最初のケースで nIDHelp の既定値は 0 で、このメッセージ ボックスのヘルプを示しません。 ユーザーなど、メッセージ ボックスがアクティブな間、f1 キーを押すと、ユーザーは受け取りませんヘルプ (たとえアプリケーションでは、ヘルプをサポートしています)。 これが望ましくない場合は、nIDHelp のヘルプ ID を指定する必要があります。

2 番目のケースでは、nIDHelp の既定値はヘルプ ID が nIDPrompt と同じことを示す-1 です。 ヘルプはのみ、アプリケーションのヘルプが有効な場合、もちろん)。 メッセージ ボックスにヘルプ サポートされていないことを希望する場合は、nIDHelp の 0 を指定する必要があります。 ヘルプが有効にするが nIDPrompt よりヘルプ ID を必要に応じて、nIDHelp nIDPrompt から別の正の値を単に提供するメッセージをする必要があります。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
