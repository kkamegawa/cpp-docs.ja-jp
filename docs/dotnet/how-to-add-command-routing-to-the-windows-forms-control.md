---
title: '方法: コマンドの追加フォーム コントロールを Windows へのルーティング'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- command routing [C++], adding to Windows Forms controls
- Windows Forms controls [C++], command routing
ms.assetid: bf138ece-b463-442a-b0a0-de7063a760c0
ms.openlocfilehash: 8f633cf744314833409a3ffeacf8c850429e099c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222911"
---
# <a name="how-to-add-command-routing-to-the-windows-forms-control"></a>方法: コマンドの追加フォーム コントロールを Windows へのルーティング

[CWinFormsView](../mfc/reference/cwinformsview-class.md)を MFC のコマンド (たとえば、フレームのメニュー項目やツールバーのボタン) を処理できるようにするユーザー コントロールにコマンドおよび更新コマンド UI メッセージをルーティングします。

ユーザー コントロールを使用して[ICommandTarget::Initialize](../mfc/reference/icommandtarget-interface.md#initialize)コマンド ソース オブジェクトへの参照を格納する`m_CmdSrc`次の例のようにします。 `ICommandTarget` を使用するには、mfcmifc80.dll への参照を追加する必要があります。

`CWinFormsView` は、共通の MFC ビューの通知をマネージ ユーザー コントロールに転送することによって処理します。 これらの通知が含まれる、 [OnInitialUpdate](../mfc/reference/iview-interface.md#oninitialupdate)、 [OnUpdate](../mfc/reference/iview-interface.md#onupdate)と[OnActivateView](../mfc/reference/iview-interface.md#onactivateview)メソッド。

このトピックでは、完了していた前提としています。[方法。ユーザー コントロールおよびホストを作成 ダイアログ ボックスで](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)と[方法。ユーザー コントロールおよびホスト MDI ビューを作成する](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)します。

### <a name="to-create-the-mfc-host-application"></a>MFC ホスト アプリケーションを作成するには

1. 作成した Windows フォーム コントロール ライブラリを開く[方法。ユーザー コントロールおよびホストを作成 ダイアログ ボックスで](../dotnet/how-to-create-the-user-control-and-host-in-a-dialog-box.md)します。

1. プロジェクト ノードを右クリックして行うことができますが、mfcmifc80.dll への参照を追加**ソリューション エクスプ ローラー**選択**追加**、**参照**を参照しながら、Microsoft Visual Studio 10.0\VC\atlmfc\lib します。

1. UserControl1.Designer.cs を開いて、次の using ステートメントを追加します。

    ```
    using Microsoft.VisualC.MFC;
    ```

1. また、UserControl1.Designer.cs の次の行を変更します。

    ```
    partial class UserControl1
    ```

   変更後は次のようになります。

    ```
    partial class UserControl1 : System.Windows.Forms.UserControl, ICommandTarget
    ```

1. `UserControl1` のクラス定義の最初の行として次の行を追加します。

    ```
    private ICommandSource m_CmdSrc;
    ```

1. 次のメソッドの定義を `UserControl1` に追加します (次の手順で、MFC コントロールの ID を作成します)。

    ```
    public void Initialize (ICommandSource cmdSrc)
    {
       m_CmdSrc = cmdSrc;
       // need ID of control in MFC dialog and callback function
       m_CmdSrc.AddCommandHandler(32771, new CommandHandler (singleMenuHandler));
    }

    private void singleMenuHandler (uint cmdUI)
    {
       // User command handler code
       System.Windows.Forms.MessageBox.Show("Custom menu option was clicked.");
    }
    ```

1. 作成した MFC アプリケーションを開く[方法。ユーザー コントロールおよびホスト MDI ビューを作成する](../dotnet/how-to-create-the-user-control-and-host-mdi-view.md)します。

1. `singleMenuHandler` を呼び出すメニュー オプションを追加します。

   移動して**リソース ビュー** (Ctrl + Shift + E)、展開、**メニュー**フォルダー、およびダブルクリック**IDR_MFC02TYPE**します。 これにより、メニュー エディターが表示されます。

   下部のメニュー オプションを追加、**ビュー**メニュー。 メニュー オプションの ID に注意してください、**プロパティ**ウィンドウ。 ファイルを保存します。

   **ソリューション エクスプ ローラー**、Resource.h ファイルを開き、追加したメニュー オプションの ID 値をコピーおよび最初のパラメーターとしてその値を貼り付けます、 `m_CmdSrc.AddCommandHandler` c# プロジェクトの呼び出す`Initialize`(置換メソッド`32771`必要な場合)。

9. プロジェクトをビルドして実行します。

   **[ビルド]** メニューの **[ソリューションのビルド]** をクリックします。

   **デバッグ** メニューのをクリックして**デバッグなしで開始**します。

   追加したメニュー オプションを選択します。 .dll 内のメソッドが呼び出されます。

## <a name="see-also"></a>関連項目

[MFC ビューとしての Windows フォーム ユーザー コントロールのホスト](../dotnet/hosting-a-windows-forms-user-control-as-an-mfc-view.md)<br/>
[ICommandSource インターフェイス](../mfc/reference/icommandsource-interface.md)<br/>
[ICommandTarget インターフェイス](../mfc/reference/icommandtarget-interface.md)
