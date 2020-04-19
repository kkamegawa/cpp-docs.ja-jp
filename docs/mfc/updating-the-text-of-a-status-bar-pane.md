---
title: ステータス バー ペインのテキストの更新
ms.date: 11/04/2016
helpviewer_keywords:
- updating user interface objects [MFC]
- ON_UPDATE_COMMAND_UI macro [MFC]
- user interface objects [MFC], updating
- text, status bar
- CStatusBar class [MFC], updating
- SetText method [MFC]
- panes, status bar
- status bars [MFC], updating
ms.assetid: 4984a3f4-9905-4d8c-a927-dca19781053b
ms.openlocfilehash: 20cd519f15fa9b218bca3dd1348659cfd0d5e473
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907639"
---
# <a name="updating-the-text-of-a-status-bar-pane"></a>ステータス バー ペインのテキストの更新

この記事では、MFC ステータスバーペインに表示されるテキストを変更する方法について説明します。 ステータスバー ( [CStatusBar](../mfc/reference/cstatusbar-class.md)クラスのウィンドウオブジェクト) には、いくつかの "ペイン" が含まれています。 各ペインは、ステータスバーの四角形の領域で、情報を表示するために使用できます。 たとえば、多くのアプリケーションでは、右端のウィンドウの CAPS LOCK、NUM LOCK、およびその他のキーの状態が表示されます。 また、多くの場合、アプリケーションでは、左端のウィンドウ (ペイン 0) に情報のテキストが表示されます ("メッセージウィンドウ" と呼ばれることもあります)。 たとえば、既定の MFC ステータスバーでは、メッセージペインを使用して、現在選択されているメニュー項目またはツールバーボタンを説明する文字列を表示します。 [ステータスバー](../mfc/status-bar-implementation-in-mfc.md)の図は、アプリケーションウィザードで作成された MFC アプリケーションのステータスバーを示しています。

既定では、ペインの作成時`CStatusBar`に、MFC はペインを有効にしません。 ペインをアクティブにするには、ステータスバーの各ペインに ON_UPDATE_COMMAND_UI マクロを使用して、ペインを更新する必要があります。 ペインは WM_COMMAND メッセージを送信しないため (ツールバーボタンのようなものではありません)、手動でコードを入力する必要があります。

たとえば、1つのペインに`ID_INDICATOR_PAGE`コマンド識別子があり、ドキュメント内の現在のページ番号が含まれているとします。 次の手順では、ステータスバーに新しいウィンドウを作成する方法について説明します。

### <a name="to-make-a-new-pane"></a>新しいウィンドウを作成するには

1. ペインのコマンド ID を定義します。

   **[表示]** メニューの **[リソースビュー]** をクリックします。 プロジェクトリソースを右クリックし、 **[リソースシンボル]** をクリックします。 [リソースシンボル] ダイアログボックスで、 `New`をクリックします。 コマンド ID 名を入力します (例`ID_INDICATOR_PAGE`:)。 ID の値を指定するか、[リソースシンボル] ダイアログボックスで提示された値をそのまま使用します。 たとえば、の`ID_INDICATOR_PAGE`場合は、既定値をそのまま使用します。 [リソースシンボル] ダイアログボックスを閉じます。

1. ペインに表示する既定の文字列を定義します。

   リソースビュー開いた状態で、アプリケーションのリソースの種類を一覧表示するウィンドウの **[文字列テーブル]** をダブルクリックします。 **文字列テーブル**エディターを開いた状態で、 **[挿入]** メニューの **[新しい文字列]** をクリックします。 ペインのコマンド ID (たとえば`ID_INDICATOR_PAGE`) を選択し、"Page" などの既定の文字列値を入力します。 文字列エディターを閉じます。 (コンパイラエラーを回避するには、既定の文字列が必要です)。

1. *インジケーター*配列にペインを追加します。

   ファイル MAINFRM.CPP にあります。CPP で、*インジケーター*の配列を探します。 この配列は、ステータスバーのすべてのインジケーターのコマンド Id を左から右へ順に一覧表示します。 配列内の適切な位置に、次に`ID_INDICATOR_PAGE`示すように、ペインのコマンド ID を入力します。

   [!code-cpp[NVC_MFCDocView#10](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_1.cpp)]

ペインにテキストを表示するには、ペインの更新ハンドラー `SetText`関数でクラス`CCmdUI`のメンバー関数を呼び出すことをお勧めします。 たとえば、現在のページ番号を含む整数変数*m_nPage*を設定し、を使用`SetText`して、その数値の文字列バージョンにペインのテキストを設定することができます。

> [!NOTE]
>  この`SetText`方法をお勧めします。 `CStatusBar`メンバー関数`SetPaneText`を呼び出すことによって、このタスクを少し低いレベルで実行することができます。 それでも、更新ハンドラーが必要です。 ペインのハンドラーがないと、MFC はウィンドウを自動的に無効にし、その内容を消去します。

次の手順は、更新ハンドラー関数を使用してテキストをペインに表示する方法を示しています。

#### <a name="to-make-a-pane-display-text"></a>ペインにテキストを表示するには

1. コマンドのコマンド更新ハンドラーを追加します。

   (Mainfrm.cpp の) の`ID_INDICATOR_PAGE`ように、ハンドラーのプロトタイプを手動で追加します。H):

   [!code-cpp[NVC_MFCDocView#11](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_2.h)]

1. 適切なで。CPP ファイルで、(mainfrm.cpp の) の`ID_INDICATOR_PAGE`ように、ハンドラーの定義を追加します。CPP):

   [!code-cpp[NVC_MFCDocView#12](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_3.cpp)]

   このハンドラーの最後の3行は、テキストを表示するコードです。

1. 適切なメッセージマップで、(mainfrm.cpp の) の`ID_INDICATOR_PAGE`ように、ON_UPDATE_COMMAND_UI マクロを追加します。CPP):

   [!code-cpp[NVC_MFCDocView#13](../mfc/codesnippet/cpp/updating-the-text-of-a-status-bar-pane_4.cpp)]

*M_nPage*メンバー変数 (クラス`CMainFrame`) の値を定義すると、この手法により、アプリケーションが他のインジケーターを更新するのと同じ方法で、アイドル処理中にページ番号がウィンドウに表示されます。 *M_nPage*が変更されると、次のアイドルループ中に表示が変更されます。

### <a name="what-do-you-want-to-know-more-about"></a>詳細については、次を参照してください。

- [ユーザーインターフェイスオブジェクトの更新 (プログラムの条件の変更に応じてツールバーのボタンとメニュー項目を更新する方法)](../mfc/how-to-update-user-interface-objects.md)

## <a name="see-also"></a>関連項目

[MFC でのステータス バーの実装](../mfc/status-bar-implementation-in-mfc.md)<br/>
[CStatusBar クラス](../mfc/reference/cstatusbar-class.md)
