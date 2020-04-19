---
title: メニューエディター (C++)
ms.date: 02/15/2019
f1_keywords:
- vc.editors.menu.F1
- vc.editors.menu
helpviewer_keywords:
- resource editors [C++], Menu editor
- editors, menus
- Menu editor
- menus [C++], Menu editor
- mnemonics [C++], associating menu items
- menus [C++], associating commands with mnemonic keys
- menus [C++], creating
- menus [C++], adding items
- commands [C++], adding to menus
- menu items, adding to menus
- submenus
- submenus [C++], creating
- menus [C++], creating
- context menus [C++], Menu Editor
- pop-up menus [C++], creating
- menus [C++], pop-up
- menus [C++], creating
- shortcut menus [C++], creating
- pop-up menus [C++], displaying
- pop-up menus [C++], connecting to applications
- context menus [C++], connecting to applications
- shortcut menus [C++], connecting to applications
- pop-up menus
- menu commands [C++], selecting
- menus [C++], selecting
- commands [C++], menu commands
- commands [C++], copying on menus
- menu items, moving
- commands [C++], moving on menus
- menu items, copying
- menu items, deleting
- commands [C++], deleting from menus
- menus [C++], deleting
ms.assetid: 421fb215-6e12-4ec9-a3af-82d77f87bfa6
ms.openlocfilehash: a21ff3ba736bd345e4b8399a761b5a8d9db531ac
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444989"
---
# <a name="menu-editor-c"></a>メニューエディター (C++)

メニューを使用すると、論理的かつ見つけやすい方法でコマンドを配置できます。 **メニューエディター**を使用すると、完成したアプリケーションのメニューバーによく似たメニューバーを直接操作して、メニューを作成および編集できます。

> [!TIP]
> **メニューエディター**を使用しているときに、多くの場合、右クリックすると、頻繁に使用するコマンドのポップアップメニューを表示できます。 使用できるコマンドは、ポインターの位置によって異なります。

## <a name="how-to"></a>方法

**メニューエディター**では、次のことが可能です。

### <a name="to-create-a-standard-menu"></a>標準メニューを作成するには

1. メニュー**ビュー** > **つの他のウィンドウ** > **リソースビュー**にアクセスし、**メニュー**見出しを右クリックします。 **[リソースの追加]** 、[**メニュー]** の順に選択します。

1. メニューバーで、 **[新しい項目]** ボックス (*ここでは型*を含む四角形) を選択します。

   ![メニューエディターの新しい項目ボックス](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")<br/>
   **新しい項目**ボックス

1. 新しいメニューの名前 ([*ファイル*] など) を入力します。

   入力したテキストは、**メニューエディター**と [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)の **[キャプション]** ボックスの両方に表示されます。 新しいメニューのプロパティはこのどちらからでも編集できます。

   メニュー バーで新しいメニューの名前を指定すると、さらに別のメニューを追加できるように [新しい項目] ボックスが右に移動し、最初のメニューの下に新しい [新しい項目] ボックスが表示されます。この新しいボックスでメニュー コマンドを追加できます。

   ![展開された新しい項目ボックス](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")<br/>
   メニュー名を入力した後にフォーカスが移動される**新しい項目**ボックス

   > [!NOTE]
   > メニューバーに単一項目のメニューを作成するには、 **Popup**プロパティを**False**に設定します。

### <a name="to-create-a-submenu"></a>サブメニューを作成するには

1. サブメニューを作成するメニューコマンドを選択します。

1. 右側に表示される **[新しいアイテム]** ボックスに、新しいメニュー コマンドの名前を入力します。 サブメニューのメニューには、この新しいコマンドが最初に表示されます。

1. サブメニューのメニューにメニュー コマンドを追加します。

### <a name="to-insert-a-new-menu-between-existing-menus"></a>既存のメニュー間に新規メニューを挿入するには

既存のメニュー名を選択して**挿入**キーを押すか、メニューバーを右クリックして **[新規挿入]** を選択します。

   選択した項目の前に **[新しい項目]** ボックスが挿入されます。

### <a name="to-add-commands-to-a-menu"></a>メニューにコマンドを追加するには

1. メニューを作成します。 次に、 **[ファイル]** などのメニュー名を選択します。

   各メニューが展開され、コマンド用の新しい項目ボックスが表示されます。 たとえば、 **[新規]** 、 **[開く**]、 **[閉じる]** の各コマンドを **[ファイル]** メニューに追加できます。

1. [新しい項目] ボックスに新しいメニュー コマンドの名前を入力します。

   > [!NOTE]
   > 入力したテキストは、**メニューエディター**と [[プロパティ] ウィンドウ](/visualstudio/ide/reference/properties-window)の **[キャプション]** ボックスの両方に表示されます。 新しいメニューのプロパティはこのどちらからでも編集できます。

   > [!TIP]
   > ユーザーがメニュー コマンドを選択できるようにするニーモニック キー (ホット キー) を定義することができます。 文字の前にアンパサンド (`&`) を入力して、ニーモニックとして指定します。 この文字を入力することで、ユーザーはメニュー コマンドを選択できます。

1. **[プロパティ]** ウィンドウで、適用するメニューコマンドのプロパティを選択します。 詳細については、「[メニューコマンドのプロパティ](../windows/menu-command-properties.md)」を参照してください。

1. **[プロパティ]** ウィンドウの **[プロンプト]** ボックスに、アプリケーションのステータスバーに表示するプロンプト文字列を入力します。

   この手順では、作成したメニューコマンドと同じリソース識別子を使用して、文字列テーブルにエントリを作成します。

   > [!NOTE]
   > プロンプトは、 **Popup**プロパティが**True**のメニュー項目にのみ適用できます。 たとえば、トップレベルのメニュー項目にサブメニュー項目がある場合、プロンプトを適用できます。 **プロンプト**の目的は、ユーザーがメニュー項目を選択した場合に何が起こるかを示すことです。

1. **Enter**キーを押して、メニューコマンドを完了します。

   新しい項目ボックスが選択され、追加のメニュー コマンドを作成できるようになります。

### <a name="to-select-multiple-menu-commands-to-run-bulk-operations-such-as-deleting-or-changing-properties"></a>複数のメニューコマンドを選択して、プロパティの削除や変更などの一括操作を実行するには

**Ctrl**キーを押しながら、目的のメニューまたはサブメニューのコマンドを選択します。

### <a name="to-move-and-copy-menus-and-menu-commands"></a>メニューとメニューコマンドを移動およびコピーするには

- ドラッグアンドドロップの方法を使用します。

   1. 移動する項目を次の場所にドラッグまたはコピーします。

      - 現在のメニュー上の新しい場所。

      - 別のメニュー 他のメニューに移動するには、そのメニューの上にマウスポインターをドラッグします。

   1. 挿入ガイドで目的の位置が示されたら、メニュー コマンドをドロップします。

- ショートカットメニューのコマンドを使用します。

   1. 1つ以上のメニューまたはメニューコマンドを右クリックし、 **[切り取り]** (移動する場合) または **[コピー]** を選択します。

   1. 項目を別のメニューリソースまたはリソーススクリプトファイルに移動している場合は、[別のウィンドウで開き](/visualstudio/ide/customizing-window-layouts-in-visual-studio)ます。

   1. メニューやメニュー コマンドを移動またはコピーする位置を選択します。

   1. ショートカット メニューの **[貼り付け]** を選択します。 移動またはコピーする項目は、選択した項目の前に配置されます。

> [!NOTE]
> ドラッグでコピーした項目を別のメニュー ウィンドウの別のメニューに貼り付けることもできます。

### <a name="to-delete-a-menu-or-menu-command"></a>メニューまたはメニュー コマンドを削除するには

メニュー名またはコマンドを右クリックし、 **[削除]** を選択します。

> [!NOTE]
> 同様に、ショートカット メニューを使用して、コピー、切り取り、貼り付け、新しい項目の挿入、区切り記号の挿入、ID の編集、ポップアップとして表示、ニーモニックの確認などの操作を実行することができます。

## <a name="pop-up-menus"></a>ポップアップメニュー

[ポップアップ メニュー](../mfc/menus-mfc.md) には、頻繁に使用するコマンドが表示されます。 これらは状況依存となっていて、マウス ポインターの場所に応じて表示できます。 アプリケーションでポップアップ メニューを使用には、メニュー自体をビルドし、アプリケーション コードに接続する必要があります。

メニューリソースを作成したら、アプリケーションコードでメニューリソースを読み込み、 [TrackPopupMenu](/windows/win32/api/winuser/nf-winuser-trackpopupmenu)を使用してメニューを表示する必要があります。 [外側] を選択してポップアップメニューを閉じるか、またはコマンドを選択すると、その関数はを返します。 ユーザーがコマンドを選択した場合は、そのコマンドのメッセージが、ハンドルが渡されたウィンドウに送信されます。

> [!NOTE]
> Microsoft Foundation Class (MFC) ライブラリプログラムおよび ATL プログラムの場合は、**コードウィザード**を使用してメニューコマンドをコードにフックします。 詳細については、「[イベントの追加](../ide/adding-an-event-visual-cpp.md)」および「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください。

- ポップアップメニューを作成するには、タイトルを空にして、*キャプション*を指定しないメニューを作成します。 次に、メニューコマンドを新しいメニューに追加し、空白のメニュータイトルの下にある最初のメニューコマンドに移動します。ここには一時的なキャプションの*種類を入力*し、*キャプション*とその他の情報を入力します。

   ポップアップメニューのその他のメニューコマンドについても、この手順を繰り返します。メニューリソースは必ず保存してください。

- たとえば、ポップアップメニューをアプリケーションに接続するには、WM_CONTEXTMENU のメッセージハンドラーを追加してから、メッセージハンドラーに次のコードを追加します。

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > メッセージハンドラーによって渡される[CPoint](../atl-mfc-shared/reference/cpoint-class.md)は、画面座標です。

通常、メニュー**エディター**で作業しているときは、メニューリソースがメニューバーとして表示されます。 ただし、プログラムの実行中にアプリケーションのメニュー バーにメニュー リソースが追加されている場合もあります。

- メニューリソースをポップアップメニューとして表示するには、メニューを右クリックし、 **[ポップアップとして表示]** を選択します。

   このオプションは表示設定にすぎないため、メニューは変更されません。

> [!TIP]
> メニューバービューに戻るには、もう一度 **[ポップアップとして表示]** を選択します。 この操作により、チェックマークが削除され、メニューバービューが返されます。

## <a name="requirements"></a>［要件］

Win32

## <a name="see-also"></a>関連項目

[リソース エディター](../windows/resource-editors.md)<br/>
[メニュー コマンド](../windows/menu-command-properties.md)<br/>
[ユーザー インターフェイス オブジェクトとコマンド ID](../mfc/user-interface-objects-and-command-ids.md)<br/>
[メニュー](../mfc/menus-mfc.md)<br/>
[メニュー](/windows/win32/menurc/menus)