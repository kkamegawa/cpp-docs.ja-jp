---
title: 'テクニカル ノート 61: ON_NOTIFY メッセージと WM_NOTIFY メッセージ'
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: aa1efb628ee45be3dfaee320cf64c4b2cbb91f04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302238"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>テクニカル ノート 61: ON_NOTIFY メッセージと WM_NOTIFY メッセージ

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このテクニカルノートでは、新しい WM_NOTIFY メッセージに関する背景情報を提供し、MFC アプリケーションで WM_NOTIFY メッセージを処理するために推奨される (そして最も一般的な) 方法について説明します。

**Windows 3.x の通知メッセージ**

Windows 3.x では、コントロールは、マウスのクリック、コンテンツや選択の変更などのイベントの親に通知し、親にメッセージを送信することによって背景の描画を制御します。 単純な通知は、特殊な WM_COMMAND メッセージとして送信されます。通知コード (BN_CLICKED など) とコントロール ID が*wParam*にパックされ、コントロール ID が*lParam*に組み込まれています。 *WParam*と*lParam*がいっぱいであるため、追加のデータを渡すことはできません。これらのメッセージは単純な通知だけにすることができます。 たとえば、BN_CLICKED 通知では、ボタンがクリックされたときにマウスカーソルの場所に関する情報を送信する方法はありません。

Windows 3.x のコントロールが追加データを含む通知メッセージを送信する必要がある場合は、WM_CTLCOLOR、WM_VSCROLL、WM_HSCROLL、WM_DRAWITEM、WM_MEASUREITEM、WM_COMPAREITEM、WM_DELETEITEM などのさまざまな目的のメッセージを使用し WM_CHARTOITEM、WM_VKEYTOITEM など。 これらのメッセージは、送信元のコントロールに反映されます。 詳細については、「[テクニカルノート 62: Message リフレクション For Windows Controls](../mfc/tn062-message-reflection-for-windows-controls.md)」を参照してください。

**Win32 での通知メッセージ**

Windows 3.1 に存在するコントロールの場合、Win32 API は、Windows 3.x で使用されていたほとんどの通知メッセージを使用します。 ただし、Win32 では、Windows 3.x でサポートされているものに対して、多数の高度な複雑なコントロールも追加します。 多くの場合、これらのコントロールは、通知メッセージと共に追加のデータを送信する必要があります。 追加データを必要とする新しい通知ごとに新しい**WM_** <strong>\*</strong>メッセージを追加するのではなく、Win32 API のデザイナーは、1つのメッセージだけを追加するように選択しました。 WM_NOTIFY は、標準化された方法で任意の量の追加データを渡すことができます。

WM_NOTIFY メッセージには、 *wParam*でメッセージを送信するコントロールの ID と、 *lParam*の構造体へのポインターが含まれます。 この構造体は、 **nmhdr**構造体、または最初のメンバーとして**nmhdr**構造体を持つ、より大きな構造体です。 **Nmhdr**メンバーが最初に使用されるため、この構造体へのポインターは、キャストの方法に応じて、 **nmhdr**へのポインターまたはより大きな構造体へのポインターとして使用できます。

ほとんどの場合、ポインターはより大きな構造体を指し、使用時にキャストする必要があります。 一般的な通知 (名前が**NM_** で始まる)、ツールヒントコントロールの TTN_SHOW と TTN_POP 通知など、いくつかの通知のみが、実際に使用される**NMHDR**構造体です。

**NMHDR**構造体または初期メンバーには、メッセージを送信するコントロールのハンドルと ID と、通知コード (TTN_SHOW など) が含まれます。 次に、 **NMHDR**構造体の形式を示します。

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

TTN_SHOW メッセージの場合、**コード**メンバーは TTN_SHOW に設定されます。

ほとんどの通知では、最初のメンバーとして**NMHDR**構造体を含む大きな構造体へのポインターが渡されます。 たとえば、リストビューコントロールの LVN_KEYDOWN 通知メッセージによって使用される構造を考えてみます。このメッセージは、リストビューコントロールでキーが押されたときに送信されます。 ポインターは**LV_KEYDOWN**構造体を指します。これは次のように定義されています。

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

**Nmhdr**メンバーがこの構造体の最初にあるため、通知メッセージで渡されるポインターは、 **nmhdr**へのポインターまたは**LV_KEYDOWN**へのポインターにキャストできます。

**すべての新しい Windows コントロールに共通の通知**

一部の通知は、すべての新しい Windows コントロールに共通です。 これらの通知は、 **NMHDR**構造体へのポインターを渡します。

|通知コード|送信の理由|
|-----------------------|------------------|
|NM_CLICK|ユーザーがコントロールでマウスの左ボタンをクリックしました|
|NM_DBLCLK|ユーザーがコントロールでマウスの左ボタンをダブルクリックしました|
|NM_RCLICK|ユーザーがコントロールでマウスの右ボタンをクリックしました|
|NM_RDBLCLK|ユーザーがコントロールでマウスの右ボタンをダブルクリックしました|
|NM_RETURN|コントロールに入力フォーカスがあるときにユーザーが ENTER キーを押しました|
|NM_SETFOCUS|コントロールに入力フォーカスが与えられました|
|NM_KILLFOCUS|コントロールが入力フォーカスを失いました|
|NM_OUTOFMEMORY|使用可能なメモリが不足しているため、コントロールは操作を完了できませんでした|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: MFC アプリケーションでの WM_NOTIFY メッセージの処理

関数 `CWnd::OnNotify` は、通知メッセージを処理します。 既定の実装では、通知ハンドラーがを呼び出すためにメッセージマップがチェックされます。 一般に、`OnNotify`はオーバーライドしません。 代わりに、ハンドラー関数を指定し、そのハンドラーのメッセージマップエントリを所有者ウィンドウのクラスのメッセージマップに追加します。

Classwizard では、ClassWizard プロパティシートを使用して ON_NOTIFY のメッセージマップエントリを作成し、スケルトンハンドラー関数を提供できます。 ClassWizard を使用してこれを簡単にする方法の詳細については、「[関数へのメッセージのマッピング](../mfc/reference/mapping-messages-to-functions.md)」を参照してください。

ON_NOTIFY メッセージマップマクロには、次の構文があります。

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

パラメーターは次のとおりです。

*wNotifyCode*<br/>
処理する通知メッセージのコード (LVN_KEYDOWN など)。

*ID*<br/>
通知を送信するコントロールの子識別子。

*memberFxn*<br/>
この通知が送信されるときに呼び出されるメンバー関数。

メンバー関数は、次のプロトタイプで宣言されている必要があります。

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

パラメーターは次のとおりです。

*pNotifyStruct*<br/>
上のセクションで説明したように、通知構造体へのポインター。

*result*<br/>
を返す前に設定する結果コードへのポインター。

## <a name="example"></a>使用例

ID が `IDC_LIST1`である `CListCtrl` からの LVN_KEYDOWN メッセージをメンバー関数 `OnKeydownList1` で処理するように指定するには、ClassWizard を使用して、メッセージマップに次のコードを追加します。

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

上記の例では、ClassWizard によって提供される関数は次のとおりです。

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

ClassWizard では、適切な型のポインターが自動的に提供されることに注意してください。 通知構造には、 *Pnmhdr*または*plvkeydow*よってアクセスできます。

##  <a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

コントロールのセットに対して同じ WM_NOTIFY メッセージを処理する必要がある場合は、ON_NOTIFY ではなく ON_NOTIFY_RANGE を使用できます。 たとえば、特定の通知メッセージに対して同じ操作を実行するためのボタンのセットがあるとします。

ON_NOTIFY_RANGE を使用する場合は、範囲の開始と終了の子識別子を指定することによって、通知メッセージを処理する連続する範囲の子識別子を指定します。

ClassWizard は ON_NOTIFY_RANGE を処理しません。これを使用するには、自分でメッセージマップを編集する必要があります。

ON_NOTIFY_RANGE のメッセージマップエントリと関数プロトタイプは次のとおりです。

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

パラメーターは次のとおりです。

*wNotifyCode*<br/>
処理する通知メッセージのコード (LVN_KEYDOWN など)。

*ID*<br/>
連続する識別子の範囲内の最初の識別子。

*idLast*<br/>
連続した識別子の範囲の最後の識別子。

*memberFxn*<br/>
この通知が送信されるときに呼び出されるメンバー関数。

メンバー関数は、次のプロトタイプで宣言されている必要があります。

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

パラメーターは次のとおりです。

*ID*<br/>
通知を送信したコントロールの子識別子。

*pNotifyStruct*<br/>
前に説明したように、通知構造へのポインター。

*result*<br/>
を返す前に設定する結果コードへのポインター。

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX、ON_NOTIFY_EX_RANGE

通知ルーティングで1つのメッセージを処理するために複数のオブジェクトが必要な場合は、ON_NOTIFY (または ON_NOTIFY_RANGE) ではなく ON_NOTIFY_EX (または ON_NOTIFY_EX_RANGE) を使用できます。 **Ex**バージョンと標準バージョンの唯一の違いは、 **ex**バージョンに対して呼び出されるメンバー関数が、メッセージ処理を続行するかどうかを示す**ブール**値を返すことです。 この関数から**FALSE**を返すと、複数のオブジェクトで同じメッセージを処理できます。

ClassWizard では、ON_NOTIFY_EX または ON_NOTIFY_EX_RANGE は処理されません。これらのいずれかを使用する場合は、自分でメッセージマップを編集する必要があります。

ON_NOTIFY_EX と ON_NOTIFY_EX_RANGE のメッセージマップエントリと関数プロトタイプは次のとおりです。 パラメーターの意味は、**EX**以外のバージョンの場合と同じです。

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

上記の両方のプロトタイプは同じです。

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

どちらの場合も、 *id*は、通知を送信したコントロールの子識別子を保持します。

関数は、通知メッセージが完全に処理された場合は**TRUE**を返し、コマンドルーティング内の他のオブジェクトがメッセージを処理する可能性がある場合は**FALSE**を返す必要があります。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
