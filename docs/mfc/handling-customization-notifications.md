---
title: カスタマイズ通知の処理
ms.date: 11/04/2016
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
ms.openlocfilehash: dc34f3eaa4b085b9d8acbaf47b21cf1825627100
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240688"
---
# <a name="handling-customization-notifications"></a>カスタマイズ通知の処理

Windows ツール バー コモン コントロールには、システム定義のカスタマイズ ダイアログ ボックスなどのカスタマイズ機能が組み込まれています。この機能を使用して、ユーザーはツール バー ボタンを挿入、削除、または再配置できます。 アプリケーションは、カスタマイズ機能が使用できるかどうかを判断し、ユーザーがツール バーをどの程度までカスタマイズできるかを制御します。

利用できるこれらのカスタマイズ機能をユーザーに、ツールバーを指定して、**ツール**スタイル。 カスタマイズ機能を使用すると、ユーザーはボタンを新しい位置にドラッグしたり、ボタンをツール バーの外にドラッグして削除したりできます。 さらに、ユーザーはツール バーをダブルクリックして **[ツール バーのカスタマイズ]** ダイアログ ボックスを表示し、このダイアログ ボックスから、ツール バー ボタンを追加、削除、再配置できます。 アプリケーションでは、 [Customize](../mfc/reference/ctoolbarctrl-class.md#customize) メンバー関数を使用することでこのダイアログ ボックスを表示できます。

ツール バー コントロールは、カスタマイズ処理の各手順で通知メッセージを親ウィンドウに送信します。 ユーザーが Shift キーを押しながらボタンのドラッグを開始すると、ツール バーは自動的にドラッグ操作を処理します。 ツール バーは **TBN_QUERYDELETE** 通知メッセージを親ウィンドウに送信し、ボタンを削除できるかどうかを判断します。 親ウィンドウが **FALSE**を返すと、ドラッグ操作は終了します。 それ以外の場合、ツール バーはマウス入力をキャプチャし、ユーザーがマウス ボタンを離すのを待機します。

ユーザーがマウス ボタンを離すと、ツール バー コントロールはマウス カーソルの場所を確認します。 カーソルがツール バーの外側にある場合、ボタンは削除されます。 カーソルが別のツール バー ボタン上にある場合、ツール バーは **TBN_QUERYINSERT** 通知メッセージを親ウィンドウに送信し、指定したボタンの左側にボタンを挿入できるかどうかを判断します。 親ウィンドウが **TRUE**を返すと、ボタンは挿入されます。それ以外の場合は、挿入されません。 ツール バーは **TBN_TOOLBARCHANGE** 通知メッセージを送信し、ドラッグ操作の終了を知らせます。

ユーザーが Shift キーを押さずにドラッグ操作を開始すると、ツール バー コントロールは **TBN_BEGINDRAG** 通知メッセージをオーナー ウィンドウに送信します。 独自のボタン ドラッグ コードを実装しているアプリケーションでは、ドラッグ操作を開始するシグナルとしてこのメッセージを使用できます。 ツール バーは **TBN_ENDDRAG** 通知メッセージを送信し、ドラッグ操作の終了を知らせます。

ユーザーが **[ツール バーのカスタマイズ]** ダイアログ ボックスを使用してツール バーをカスタマイズすると、ツール バー コントロールは通知メッセージを送信します。 ユーザーがツール バーをダブルクリックすると、ダイアログ ボックスが作成される前に、ツール バーは **TBN_BEGINADJUST** 通知メッセージを送信します。 次に、ツール バーは一連の **TBN_QUERYINSERT** 通知メッセージの送信を開始し、ツール バーにボタンを挿入できるかどうかを判断します。 親ウィンドウが **TRUE**を返すと、ツール バーは **TBN_QUERYINSERT** 通知メッセージの送信を終了します。 親ウィンドウが、どのボタンに対しても **TRUE** を返さない場合、ツール バーはダイアログ ボックスを破棄します。

次に、ツール バー コントロールは、ツール バーのボタンごとに **TBN_QUERYDELETE** 通知メッセージを送り、ツール バーからボタンを削除できるかどうかを判断します。 ボタンを削除できる場合、親ウィンドウは **TRUE** を返します。それ以外の場合は **FALSE**を返します。 ツール バーはすべてのツール バー ボタンをダイアログ ボックスに追加しますが、削除できないボタンは淡色表示します。

ツール バー コントロールは、[ツール バーのカスタマイズ] ダイアログ ボックスのボタンに関する情報が必要になると、 **TBN_GETBUTTONINFO** 通知メッセージを送り、情報が必要なボタンのインデックスと **TBNOTIFY** 構造体のアドレスを指定します。 親ウィンドウは構造体に適切な情報を格納する必要があります。

**[ツール バーのカスタマイズ]** ダイアログ ボックスには、[ヘルプ] ボタンと [リセット] ボタンがあります。 ユーザーが [ヘルプ] ボタンを選ぶと、ツール バー コントロールは **TBN_CUSTHELP** 通知メッセージを送信します。 親ウィンドウは、ヘルプ情報を表示して応答する必要があります。 ユーザーが [リセット] ボタンを選ぶと、ダイアログ ボックスは **TBN_RESET** 通知メッセージを送信します。 このメッセージは、ツール バーがダイアログ ボックスを再初期化しようとしていることを示します。

これらのメッセージはすべて **WM_NOTIFY** メッセージです。メッセージをオーナー ウィンドウで処理するには、オーナー ウィンドウのメッセージ マップに次のような形式でメッセージ マップのエントリを追加します。

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   通知メッセージの識別子コード。 **TBN_BEGINADJUST**など。

- **idControl**

   通知を送信するコントロールの識別子。

- **memberFxn**

   この通知を受信したときに呼び出されるメンバー関数。

メンバー関数は次のプロトタイプで宣言されます。

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

通知メッセージ ハンドラーが値を返す場合は、その値を **result** が指す *LRESULT*に格納する必要があります。

各メッセージに対して、 `pNotifyStruct` は **NMHDR** 構造体か **TBNOTIFY** 構造体のいずれかを指します。 これらの構造体は次のとおりです。

**NMHDR** 構造体には次のメンバーが含まれます。

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   通知を送信するコントロールのウィンドウ ハンドル。 このハンドルを `CWnd` ポインターに変換するには、 [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle)を使用します。

- **idFrom**

   通知を送信するコントロールの識別子。

- **code**

   通知コード。 このメンバーは、 **TBN_BEGINADJUST** や **TTN_NEEDTEXT**などのコントロールの種類に固有の値になるか、以下に示す通知に共通の値のいずれかになります。

   - **NM_CLICK** ユーザーがコントロール内でマウスの左ボタンをクリックしました。

   - **NM_DBLCLK** ユーザーがコントロール内でマウスの左ボタンをダブルクリックしました。

   - **NM_KILLFOCUS** コントロールは入力フォーカスを失いました。

   - **NM_OUTOFMEMORY** メモリ不足のために、コントロールは操作を完了できませんでした。

   - **NM_RCLICK** ユーザーがコントロール内でマウスの右ボタンをクリックしました。

   - **NM_RDBLCLK** ユーザーがコントロール内でマウスの右ボタンをダブルクリックしました。

   - **NM_RETURN** コントロールに入力フォーカスがあり、ユーザーが Enter キーを押しました。

   - **NM_SETFOCUS** コントロールは入力フォーカスを受け取りました。

**TBNOTIFY** 構造体には次のメンバーが含まれます。

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   すべての **WM_NOTIFY** メッセージに共通の情報。

- **iItem**

   通知に関連付けられたボタンのインデックス。

- **tbButton**

   **TBBUTTON**通知に関連付けられているツール バー ボタンに関する情報を含む構造体。

- **cchText**

   ボタンのテキスト文字の数。

- **lpszText**

   ボタンのテキストへのポインター。

ツール バーが送信する通知は、次のとおりです。

- **TBN_BEGINADJUST**

   ユーザーがツール バー コントロールのカスタマイズを開始するときに送信します。 ポインターは、通知についての情報を格納する **NMHDR** 構造体を指します。 ハンドラーが特定の値を返す必要はありません。

- **TBN_BEGINDRAG**

   ユーザーがツール バー コントロールに、ボタンのドラッグを開始するときに送信します。 ポインターは **TBNOTIFY** 構造体を指します。 **iItem** メンバーには、ドラッグされているボタンの 0 から始まるインデックスが含まれます。 ハンドラーが特定の値を返す必要はありません。

- **TBN_CUSTHELP**

   ユーザーがツールバーのカスタマイズ ダイアログ ボックスで ヘルプ ボタンを選択したときに送信されます。 戻り値はありません。 ポインターは、この通知メッセージについての情報を格納する **NMHDR** 構造体を指します。 ハンドラーが特定の値を返す必要はありません。

- **TBN_ENDADJUST**

   ユーザーがツール バー コントロールのカスタマイズと送信されます。 ポインターは、この通知メッセージについての情報を格納する **NMHDR** 構造体を指します。 ハンドラーが特定の値を返す必要はありません。

- **TBN_ENDDRAG**

   ユーザーがツール バー コントロールに、ボタンのドラッグを停止するときに送信します。 ポインターは **TBNOTIFY** 構造体を指します。 **iItem** メンバーには、ドラッグされているボタンの 0 から始まるインデックスが含まれます。 ハンドラーが特定の値を返す必要はありません。

- **TBN_GETBUTTONINFO**

   ユーザーがツール バー コントロールをカスタマイズするときに送信されます。 ツール バーは、この通知メッセージを使用して [ツール バーのカスタマイズ] ダイアログ ボックスで必要になる情報を取得します。 ポインターは **TBNOTIFY** 構造体を指します。 **iItem** メンバーは、ボタンの 0 から始まるインデックスを指定します。 **pszText** メンバーと **cchText** メンバーは、現在のボタンのテキストのアドレスと長さ (文字数) で指定します。 アプリケーションでは、ボタンに関する情報をこの構造体に格納する必要があります。 ボタンの情報が構造体にコピーされた場合は **TRUE** を返し、それ以外の場合は **FALSE** を返します。

- **TBN_QUERYDELETE**

   ユーザーがツール バー コントロールからボタンを削除するかどうかを判断するツールバーをカスタマイズ中に送信されます。 ポインターは **TBNOTIFY** 構造体を指します。 **iItem** メンバーには、削除するボタンの 0 から始まるインデックスが含まれます。 ボタンの削除を許可する場合は **TRUE** を返し、ボタンの削除を禁止する場合は **FALSE** を返します。

- **TBN_QUERYINSERT**

   ユーザーが、指定したボタンの左側にボタンを挿入するかどうかを判断するツール バー コントロールをカスタマイズするときに送信されます。 ポインターは **TBNOTIFY** 構造体を指します。 **iItem** メンバーには、挿入するボタンの 0 から始まるインデックスが含まれます。 指定したボタンの前にボタンの挿入を許可する場合は **TRUE** を返し、ボタンの挿入を禁止する場合は **FALSE** を返します。

- **TBN_RESET**

   ユーザーがツールバーのカスタマイズ ダイアログ ボックスのコンテンツをリセットしたときに送信されます。 ポインターは、この通知メッセージについての情報を格納する **NMHDR** 構造体を指します。 ハンドラーが特定の値を返す必要はありません。

- **TBN_TOOLBARCHANGE**

   ユーザーがツール バー コントロールをカスタマイズした後に送信されます。 ポインターは、この通知メッセージについての情報を格納する **NMHDR** 構造体を指します。 ハンドラーが特定の値を返す必要はありません。

## <a name="see-also"></a>関連項目

[CToolBarCtrl の使い方](../mfc/using-ctoolbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
