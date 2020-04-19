---
title: TN062:Windows のコントロールのメッセージ リフレクション
ms.date: 06/28/2018
f1_keywords:
- vc.controls.messages
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
ms.openlocfilehash: aa189eec430d72bef753fef7ebbe9ad929d76c87
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62351847"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062:Windows のコントロールのメッセージ リフレクション

> [!NOTE]
> 次のテクニカル ノートは、最初にオンライン ドキュメントの一部とされてから更新されていません。 結果として、一部のプロシージャおよびトピックが最新でないか、不正になります。 最新の情報について、オンライン ドキュメントのキーワードで関係のあるトピックを検索することをお勧めします。

このテクニカル ノートでは、メッセージは、MFC 4.0 の新機能について説明します。 メッセージ リフレクションを使用する単純な再利用可能なコントロールを作成する手順も含まれています。

このテクニカル ノートでは、(旧称 OLE コントロール) の ActiveX コントロールに適用されるメッセージ リフレクションは説明しません。 この記事を参照してください[ActiveX コントロール。Windows コントロールをサブクラス化](../mfc/mfc-activex-controls-subclassing-a-windows-control.md)します。

**メッセージ リフレクションとは**

Windows コントロールは、頻繁に親ウィンドウに通知メッセージを送信します。 たとえば、多くのコントロールは、それぞれの親コントロールの背景を描画するブラシを指定する親を許可するコントロールの色の通知メッセージ (WM_CTLCOLOR またはそのバリエーションの 1 つ) を送信します。

Windows および MFC バージョン 4.0 より前に、では、親ウィンドウ、ダイアログ ボックスでは多くの場合がこれらのメッセージを処理します。 つまり、メッセージを処理するコードを親ウィンドウのクラスである必要があることと、そのメッセージを処理する必要があるすべてのクラス内で重複する必要があります。 上記の例でカスタムの背景を持つコントロールを必要なすべてのダイアログ ボックスはコントロールの色の通知メッセージを処理する必要があります。 独自の背景色を処理すると、コントロール クラスが書き込まれる場合は、コードを再利用するはるかに簡単になります。

MFC 4.0 では、従来の機能でも、親ウィンドウは、通知メッセージを処理できます。 さらに、ただし、MFC 4.0 を容易に再利用「メッセージ リフレクション」と呼ばれる機能を提供することでこれらの通知メッセージに子コントロールのウィンドウまたは親ウィンドウのいずれかまたは両方で処理できるようにします。 コントロールの背景色の例で、リフレクション WM_CTLCOLOR メッセージを処理することによって、独自の背景色を設定するコントロール クラスを記述することができますようになりました: 親に頼ることがなくすべて。 (メッセージ リフレクションは、MFC によって実装される、ためいない、Windows によって親ウィンドウ クラスする必要がありますを派生させるから`CWnd`させるメッセージ リフレクション)。

MFC の以前のバージョンでは、オーナー描画リスト ボックス) (WM_DRAWITEM、およびなど) のメッセージなど、いくつかのメッセージの仮想関数を提供することによってメッセージ リフレクションのようなものを行いました。 新しいメッセージ リフレクション メカニズムとは、一般化されたで一貫性のあります。

メッセージ リフレクションは、4.0 より前に、のバージョンの MFC に対して記述されたコードとの下位互換性です。

特定のメッセージのハンドラーを指定するか、さまざまなメッセージは、親ウィンドウのクラスでオーバーライドされる場合は、独自のハンドラーの基本クラスのハンドラー関数を呼び出さない限り、同じメッセージのメッセージ ハンドラーを反映します。 たとえば、WM_CTLCOLOR をダイアログ ボックス クラスを処理する場合、処理は、リフレクション メッセージ ハンドラーをオーバーライドします。

これらのメッセージを送信する子コントロールを使用してリフレクション メッセージ ハンドラーがない場合にのみ、ハンドラーが呼び出されます場合、親ウィンドウ クラス、特定の WM_NOTIFY メッセージまたは範囲の WM_NOTIFY メッセージのハンドラーを指定する、`ON_NOTIFY_REFLECT()`します。 使用する場合`ON_NOTIFY_REFLECT_EX()`メッセージ ハンドラー、メッセージ マップに可能性がありますまたはメッセージを処理するために、親ウィンドウを許可しない場合があります。 ハンドラーが返された場合**FALSE**を返す呼び出し中に、同様に、親によってメッセージが処理される**TRUE**処理し親ことはできません。 通知メッセージの前に反映されたメッセージが処理されることに注意してください。

WM_NOTIFY メッセージが送信されるときに、コントロールにはそれを処理する最初の機会が提供されます。 リフレクションの他のメッセージが送信される場合は、親ウィンドウがそれを処理する最初の機会とコントロールが反映されたメッセージを受け取る。 これを行うには、それにハンドラー関数とコントロールのクラスのメッセージ マップ内の適切なエントリ必要があります。

リフレクション メッセージ用のメッセージ マップ マクロは通常の通知よりも若干異なります。 が *_REFLECT* 、通常の名前に追加されます。 たとえば、親 WM_NOTIFY メッセージを処理するには、親のメッセージ マップ マクロ ON_NOTIFY を使用します。 子コントロールに反映されたメッセージを処理するには、子コントロールのメッセージ マップで ON_NOTIFY_REFLECT マクロを使用します。 場合によっては、パラメーターは、さまざまなも。 ClassWizard のメッセージ マップ エントリを追加および正しいパラメーターを持つ関数の骨組み実装を提供することが通常に注意してください。

参照してください[TN061:ON_NOTIFY メッセージと WM_NOTIFY メッセージ](../mfc/tn061-on-notify-and-wm-notify-messages.md)については、新しい WM_NOTIFY メッセージ。

**メッセージ マップ エントリと返送されたメッセージのハンドラー関数のプロトタイプ**

反映されたコントロールの通知メッセージを処理するために、メッセージ マップ マクロと関数プロトタイプが以下の表を使用します。

ClassWizard は、通常、これらのメッセージ マップ エントリを追加し、スケルトン関数の実装を提供できます。 参照してください[リフレクション メッセージ用のメッセージ ハンドラーを定義する](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)反映されたメッセージのハンドラーを定義する方法についてはします。

メッセージ名から反映されたマクロ名に変換する付加*on _* と追加 *_REFLECT*します。 たとえば、WM_CTLCOLOR ON_WM_CTLCOLOR_REFLECT になります。 (次の表に、マクロのエントリを逆の変換を実行するメッセージを反映して)。

上記のルールには、次の 3 つの例外は次のとおりです。

- WM_COMMAND 通知用のマクロは、ON_CONTROL_REFLECT です。

- WM_NOTIFY 反射のマクロは、ON_NOTIFY_REFLECT です。

- ON_UPDATE_COMMAND_UI 反射のマクロは、ON_UPDATE_COMMAND_UI_REFLECT です。

上記の特殊なケースの各でハンドラー メンバー関数の名前を指定する必要があります。 その他の場合、ハンドラー関数の標準の名前を使用する必要があります。

パラメーターの意味と、関数の戻り値が関数名または関数名の下に記載されている*で*先頭に付加します。 たとえば、`CtlColor`に記載されて`OnCtlColor`します。 リフレクション メッセージ ハンドラーには、親ウィンドウのようなハンドラーよりも少ないパラメーターが必要があります。 ドキュメントの仮パラメーターの名前を持つ次の表の名前に一致だけです。

|マップ エントリ|関数プロトタイプ|
|---------------|------------------------|
|**ON_CONTROL_REFLECT(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( );**|
|**ON_NOTIFY_REFLECT(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **( NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT**<strong>\*</strong> *result* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT(** `memberFxn` **)**|**afx_msg void** `memberFxn` **( CCmdUI**<strong>\*</strong> `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT( )**|**afx_msg HBRUSH CtlColor ( CDC**<strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT( )**|**afx_msg void DrawItem ( LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT( )**|**afx_msg void MeasureItem (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **)。**|
|**ON_WM_DELETEITEM_REFLECT( )**|**afx_msg void DeleteItem ( LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT( )**|**afx_msg int CompareItem ( LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT( )**|**afx_msg int CharToItem (UINT** `nKey` **、UINT** `nIndex` **)。**|
|**ON_WM_VKEYTOITEM_REFLECT( )**|**afx_msg int VKeyToItem ( UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT( )**|**afx_msg void HScroll (UINT** `nSBCode` **、UINT** `nPos` **)。**|
|**ON_WM_VSCROLL_REFLECT( )**|**afx_msg void VScroll (UINT** `nSBCode` **、UINT** `nPos` **)。**|
|**ON_WM_PARENTNOTIFY_REFLECT( )**|**afx_msg void ParentNotify ( UINT** `message` **, LPARAM** `lParam` **);**|

ON_NOTIFY_REFLECT と ON_CONTROL_REFLECT マクロでは、特定のメッセージを処理するために 1 つ以上のオブジェクト (コントロールとその親) などを許可するバリエーションがあります。

|マップ エントリ|関数プロトタイプ|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **( NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT**<strong>\*</strong> *result* **);**|
|**ON_CONTROL_REFLECT_EX(** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **( );**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>反映されたメッセージの処理。再利用可能なコントロールの例

この簡単な例と呼ばれる再利用可能なコントロールを作成する`CYellowEdit`します。 コントロールは、黄色の背景に黒のテキストが表示される点を除いて、通常のエディット コントロールと同じでは機能します。 簡単にできるようにするメンバー関数を追加することが、`CYellowEdit`さまざまな色を表示するコントロール。

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>再利用可能なコントロールを作成する例を試す

1. 既存のアプリケーションでは、新しいダイアログ ボックスを作成します。 詳細については、次を参照してください。、[ダイアログ エディター](../windows/dialog-editor.md)トピック。

   再利用可能なコントロールを開発するためのアプリケーションが必要です。 使用する既存のアプリケーションを持っていない場合は、AppWizard を使用して、ダイアログ ベースのアプリケーションを作成します。

2. Visual C に読み込まれるプロジェクトと ClassWizard を使用してという新しいクラスを作成する`CYellowEdit`に基づいて`CEdit`します。

3. 次の 3 つのメンバー変数を追加して、`CYellowEdit`クラス。 最初の 2 つになります*COLORREF*テキストの色と背景の色を保持する変数。 3 番目になります、`CBrush`背景の描画ブラシを保持するオブジェクト。 `CBrush`オブジェクトを使用するブラシで 1 回だけではその後、参照を作成するときに自動的にブラシを破棄して、`CYellowEdit`コントロールが破棄されます。

4. 次のように、コンス トラクターを記述することで、メンバー変数を初期化します。

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. 反映された WM_CTLCOLOR メッセージのハンドラーを追加、ClassWizard を使用して、`CYellowEdit`クラス。 処理できるメッセージの一覧で、メッセージ名の前に等号 (=) が、メッセージが反映されることを示すことに注意してください。 「[リフレクション メッセージ用のメッセージ ハンドラーを定義する](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md)します。

   ClassWizard では、次のメッセージ マップ マクロとスケルトン関数を追加します。

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. 関数の本体を次のコードに置き換えます。 コードでは、テキストの色、テキストの背景色、およびコントロールの残りの部分の背景色を指定します。

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. ダイアログ ボックスで、編集コントロールを作成し、コントロール キーを押しながら、編集コントロールをダブルクリックして、メンバー変数にアタッチします。 メンバー変数の追加 ダイアログ ボックスでは、変数名を完了し、カテゴリには、"CYellowEdit"変数の型の「コントロール」を選択します。 忘れずに、ダイアログ ボックスで、タブ オーダーを設定します。 また、インクルード ヘッダー ファイルを必ず、 `CYellowEdit`  ダイアログ ボックスのヘッダー ファイル内のコントロール。

8. アプリケーションをビルドして実行します。 エディット コントロールでは、黄色の背景があります。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
