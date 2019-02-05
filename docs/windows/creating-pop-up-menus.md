---
title: ショートカット メニュー (C++) の作成
ms.date: 11/04/2016
helpviewer_keywords:
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
ms.assetid: dff4dddf-2e8d-4c34-b755-90baae426b58
ms.openlocfilehash: cf2e3578f49cb6b4af8797052273211f699a6b4f
ms.sourcegitcommit: e98671a4f741b69d6277da02e6b4c9b1fd3c0ae5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/04/2019
ms.locfileid: "55702831"
---
# <a name="creating-pop-up-menus-c"></a>ショートカット メニュー (C++) の作成

[ポップアップ メニュー](../mfc/menus-mfc.md) には、頻繁に使用するコマンドが表示されます。 これらは状況依存となっていて、マウス ポインターの場所に応じて表示できます。 アプリケーションでポップアップ メニューを使用には、メニュー自体をビルドし、アプリケーション コードに接続する必要があります。

アプリケーション コードがメニュー リソースをロードして使用する必要があるメニュー リソースを作成したら、 [TrackPopupMenu](/windows/desktop/api/winuser/nf-winuser-trackpopupmenu)がメニューを表示します。 外部を選択して、ポップアップ メニューが閉じるか、コマンドが選択すると、その関数を返します。 ユーザーがコマンドを選択した場合は、そのコマンドのメッセージが、ハンドルが渡されたウィンドウに送信されます。

## <a name="to-create-a-pop-up-menu"></a>ポップアップ メニューを作成するには

1. 空のタイトルで[メニューを作成](../windows/creating-a-menu.md) します ( **キャプション**は指定しません)。

1. [新しいメニューにメニュー コマンドを追加](../windows/adding-commands-to-a-menu.md)します。 最初のメニュー コマンド、空のメニュー タイトルの下に移動 (一時的なキャプションという`Type Here`)。 **キャプション** とその他の情報を入力します。

   ポップアップ メニューのその他のメニュー コマンドに対して、この手順を繰り返します。

1. メニュー リソースを保存します。

## <a name="to-connect-a-pop-up-menu-to-your-application"></a>ショートカット メニューをアプリケーションに関連付けるには

1. (たとえば) WM_CONTEXTMENU のメッセージ ハンドラーを追加します。 詳細については、次を参照してください。[関数へのメッセージの割り当て](../mfc/reference/mapping-messages-to-functions.md)します。

1. 次のコードをメッセージ ハンドラーに追加します。

    ```cpp
    CMenu menu;
    VERIFY(menu.LoadMenu(IDR_MENU1));
    CMenu* pPopup = menu.GetSubMenu(0);
    ASSERT(pPopup != NULL);
    pPopup->TrackPopupMenu(TPM_LEFTALIGN | TPM_RIGHTBUTTON, point.x, point.y, AfxGetMainWnd());
    ```

   > [!NOTE]
   > [CPoint](../atl-mfc-shared/reference/cpoint-class.md)渡されたハンドラーが画面座標では、メッセージによって。

   > [!NOTE]
   > ポップアップ メニューをアプリケーションに接続するには、MFC が必要です。

## <a name="to-view-a-menu-resource-as-a-pop-up-menu"></a>メニュー リソースをポップアップ メニューとして表示するには

通常、作業するとき、**メニュー**エディター、メニュー バーでメニュー リソースが表示されます。 ただし、プログラムの実行中にアプリケーションのメニュー バーにメニュー リソースが追加されている場合もあります。

メニューを右クリックし、**ポップアップ表示**ショートカット メニューから。

   このオプションは、単なる表示設定で、メニューは変更されません。

   > [!NOTE]
   > メニュー バーの表示に戻すに、次のようにクリックします。**ポップアップ表示**もう一度 (チェック マークが削除と、メニュー バーの表示を返します)。

## <a name="requirements"></a>必要条件

Win32

## <a name="see-also"></a>関連項目

[メニュー エディター](../windows/menu-editor.md)
