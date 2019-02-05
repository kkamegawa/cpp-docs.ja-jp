---
title: TN006:メッセージ マップ
ms.date: 06/25/2018
f1_keywords:
- vc.messages.maps
helpviewer_keywords:
- ON_UPDATE_COMMAND_UI macro [MFC]
- ON_NOTIFY_RANGE macro [MFC]
- ON_COMMAND macro [MFC]
- ON_CONTROL_RANGE macro [MFC]
- ON_REGISTERED_MESSAGE macro [MFC]
- ON_NOTIFY message [MFC]
- ON_COMMAND_RANGE_EX macro [MFC]
- ON_MESSAGE macro [MFC]
- Windows messages [MFC], message maps
- ON_COMMAND_RANGE macro [MFC]
- TN006
- ON_CONTROL macro [MFC]
- ON_COMMAND_EX macro [MFC]
- message maps [MFC], Windows messaging
ms.assetid: af4b6794-4b40-4f1e-ad41-603c3b7409bb
ms.openlocfilehash: 3536cb215da04fb7114853d3fa5d764585cbb58e
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54894082"
---
# <a name="tn006-message-maps"></a>TN006:メッセージ マップ

ここでは、MFC メッセージ マップ機能について説明します。

## <a name="the-problem"></a>問題を

Microsoft Windows では、メッセージングの機能を使用して、ウィンドウ クラスの仮想関数を実装します。 多いのため、関連するメッセージの Windows メッセージごとに個別の仮想関数を提供する非常に大規模な vtable を作成します。

時間の経過と共に Windows メッセージのシステム定義の数を変更し、メッセージがマップするため、アプリケーションが独自の Windows メッセージを定義するためのインターフェイスの変更が既存のコードを中断するを防ぎます間接レベルを提供します。

## <a name="overview"></a>概要

MFC には、代わりに、ウィンドウに送信されるメッセージを処理するために従来の Windows ベースのプログラムで使用されていた switch ステートメントが用意されています。 ウィンドウで、メッセージが受信したときに、適切なメソッドが自動的に呼び出されるように、メッセージからメソッドへのマッピングを定義できます。 このメッセージ マップ機能は仮想関数と同じように設計されていますが、仮想関数の C++ では実現できません利点もあります。

## <a name="defining-a-message-map"></a>メッセージ マップを定義します。

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map)マクロ クラスの 3 つのメンバーを宣言します。

- AFX_MSGMAP_ENTRY エントリのプライベート配列と呼ばれる *_messageEntries*します。

- 保護された AFX_MSGMAP 構造体と呼ばれる*messageMap*を指す、 *_messageEntries*配列。

- プロテクト仮想関数が呼び出されます`GetMessageMap`のアドレスを返す*messageMap*します。

メッセージ マップを使用して任意のクラスの宣言では、このマクロを含める必要があります。 慣例により、クラス宣言の最後になります。 例:

```cpp
class CMyWnd : public CMyParentWndClass
{
    // my stuff...

protected:
    //{{AFX_MSG(CMyWnd)
    afx_msg void OnPaint();
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};
```

これは、新しいクラスを作成するときに、AppWizard と ClassWizard で生成された形式です。 //{{と//}} ClassWizard 角かっこが必要です。

メッセージ マップのテーブルは、メッセージ マップ エントリに展開されるマクロのセットを使用して定義されます。 テーブルが始まり、 [BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)マクロの呼び出しは、このメッセージ マップによって処理されるクラスとする未処理のメッセージが渡された親クラスを定義します。 テーブルが終わる、 [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)マクロの呼び出し。

これら 2 つのマクロ呼び出しの間、このメッセージ マップによって処理されるメッセージごとにエントリです。 すべての標準 Windows メッセージがフォーム ON_WM のマクロ*MESSAGE_NAME*そのメッセージのエントリを生成します。

標準の関数のシグネチャは、各 Windows メッセージのパラメーターをアンパックし、タイプ セーフを提供するために定義されています。 これらの署名 Afxwin.h、宣言内のファイルで見つかるの[CWnd](../mfc/reference/cwnd-class.md)します。 それぞれが、キーワードでマークされた**afx_msg**を簡単に識別します。

> [!NOTE]
> ClassWizard では、使用することが必要です、 **afx_msg**メッセージ マップのハンドラーの宣言でキーワード。

これらの関数シグネチャは、単純な規則を使用して取得しました。 関数の名前は常に始まる`"On`"。 大文字で入力の各単語の最初の文字を削除「wm _」の Windows メッセージの名前は、この後にします。 パラメーターの順序付けは*wParam*続けて`LOWORD`(*lParam*) し、 `HIWORD`(*lParam*)。 使用されていないパラメーターは渡されません。 MFC クラスによってラップされているすべてのハンドルは、適切な MFC オブジェクトへのポインターに変換されます。 次の例では、WM_PAINT メッセージを処理し、発生する方法を示しています、`CMyWnd::OnPaint`に呼び出される関数。

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

任意の関数またはクラス定義のスコープ外メッセージ マップのテーブルを定義する必要があります。 Extern"C"ブロックで配置する必要があります。

> [!NOTE]
> ClassWizard の間に発生するメッセージ マップ エントリを変更、//{{と//}} コメントの角かっこです。

## <a name="user-defined-windows-messages"></a>ユーザー定義の Windows メッセージ

使用して、メッセージ マップでユーザー定義メッセージを含めることができます、 [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)マクロ。 このマクロは、メッセージ数と、フォームのメソッドを受け取ります。

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

この例では、ユーザー定義メッセージの標準 WM_USER 基本クラスから派生した、Windows メッセージ ID を持つカスタム メッセージのハンドラーを確立します。 次の例では、このハンドラーを呼び出す方法を示します。

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

このアプローチを使用するユーザー定義メッセージの範囲は、WM_USER 0x7fff の範囲内で指定する必要があります。

> [!NOTE]
> ClassWizard は ClassWizard のユーザー インターフェイスからの入力の ON_MESSAGE ハンドラー ルーチンをサポートしていません。 Visual C エディターから手動で入力する必要があります。 ClassWizard では、これらのエントリが解析され、その他のすべてのメッセージ マップ エントリと同じように参照できます。

## <a name="registered-windows-messages"></a>登録済みの Windows メッセージ

[を通じて](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)関数は、システム全体で一意であることが保証される、新しいウィンドウ メッセージを定義するために使用します。 ON_REGISTERED_MESSAGE マクロは、これらのメッセージを処理するために使用されます。 このマクロの名前を受け入れる、 *UINT 近く*登録済みの windows メッセージの ID を含む変数 次に例を示します。

```cpp
class CMyWnd : public CMyParentWndClass
{
public:
    CMyWnd();

    //{{AFX_MSG(CMyWnd)
    afx_msg LRESULT OnFind(WPARAM wParam, LPARAM lParam);
    //}}AFX_MSG

    DECLARE_MESSAGE_MAP()
};

static UINT NEAR WM_FIND = RegisterWindowMessage("COMMDLG_FIND");

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

登録済みの Windows メッセージ ID 変数 (この例では WM_FIND) である必要があります、 *NEAR* ON_REGISTERED_MESSAGE の実装方法により変数。

このアプローチを使用するユーザー定義メッセージの範囲は、0xC000 に 0 xffff の範囲内になります。

> [!NOTE]
> ClassWizard は ClassWizard のユーザー インターフェイスからの入力の ON_REGISTERED_MESSAGE ハンドラー ルーチンをサポートしていません。 テキスト エディターから手動で入力する必要があります。 ClassWizard では、これらのエントリが解析され、その他のすべてのメッセージ マップ エントリと同じように参照できます。

## <a name="command-messages"></a>コマンド メッセージ

メニューとアクセラレータからコマンド メッセージは、ON_COMMAND マクロをメッセージ マップで処理されます。 このマクロは、コマンド ID とメソッドを受け取ります。 持つ特定の WM_COMMAND メッセージのみを*wParam*と等しい、指定したコマンドの ID は、メッセージ マップ エントリで指定されたメソッドによって処理されます。 コマンド ハンドラー メンバー関数は、パラメーターを受け取らないし、返す**void**します。 マクロでは、次の形式があります。

```cpp
ON_COMMAND(id, memberFxn)
```

コマンド更新メッセージは、同じメカニズムを介してルーティングされますが、ON_UPDATE_COMMAND_UI マクロを代わりに使用します。 コマンド更新ハンドラー メンバー関数は、1 つのパラメーターへのポインターを受け取る、 [CCmdUI](../mfc/reference/ccmdui-class.md)オブジェクト、戻って**void**します。 マクロは、フォーム

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

高度なユーザーは、コマンド メッセージ ハンドラーの拡張の形式である ON_COMMAND_EX マクロを使用できます。 マクロは、ON_COMMAND 機能のスーパー セットを提供します。 拡張コマンド ハンドラー メンバー関数が、1 つのパラメーターを受け取る、 **UINT**コマンド ID を表すを返します、 **BOOL**します。 戻り値にする必要があります**TRUE**をコマンドが処理されていることを示します。 それ以外の場合、ルーティングは、その他のコマンド ターゲット オブジェクトを続けます。

これらの形式の例:

- 内側の Resource.h (通常は、Visual C で生成する)

    ```cpp
    #define    ID_MYCMD      100
    #define    ID_COMPLEX    101
    ```

- クラス宣言内

    ```cpp
    afx_msg void OnMyCommand();
    afx_msg void OnUpdateMyCommand(CCmdUI* pCmdUI);
    afx_msg BOOL OnComplexCommand(UINT nID);
    ```

- メッセージ マップの定義の内部

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- 実装ファイル

    ```cpp
    void CMyClass::OnMyCommand()
    {
        // handle the command
    }

    void CMyClass::OnUpdateMyCommand(CCmdUI* pCmdUI)
    {
        // set the UI state with pCmdUI
    }

    BOOL CMyClass::OnComplexCommand(UINT nID)
    {
        // handle the command
        return TRUE;
    }
    ```

上級ユーザーは、1 つのコマンド ハンドラーを使用して、さまざまなコマンドを処理できます。[ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)または ON_COMMAND_RANGE_EX します。 これらのマクロの詳細については、製品ドキュメントを参照してください。

> [!NOTE]
> ClassWizard ON_COMMAND とハンドラーの作成をサポートしていますが、ON_COMMAND_EX または割り当てるにはハンドラーの作成をサポートしていません。 ただし、クラス ウィザードが解析され、4 つのコマンド ハンドラーのすべてのバリエーションを参照することができます。

## <a name="control-notification-messages"></a>コントロールの通知メッセージ

子コントロールから、ウィンドウには、余分なビット情報がメッセージの送信されるメッセージ マップ エントリ: コントロールの id。 次の条件に該当する場合にのみ、メッセージ マップ エントリで指定されたメッセージのハンドラーが呼び出されます。

- コントロールの通知コード (の上位ワード*lParam*)、BN_CLICKED など、メッセージ マップ エントリで指定された通知のコードに一致します。

- コントロールの ID (*wParam*) メッセージ マップ エントリで指定されたコントロールの ID と一致します。

カスタム コントロールの通知メッセージを使用して、可能性があります、 [ON_CONTROL](reference/message-map-macros-mfc.md#on_control)マクロをカスタム通知コードとメッセージ マップ エントリを定義します。 このマクロには、フォーム

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

高度な使用状況の[ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)同じハンドラーを持つコントロールの範囲から特定のコントロールの通知を処理するために使用できます。

> [!NOTE]
> ClassWizard では、ユーザー インターフェイスで ON_CONTROL または ON_CONTROL_RANGE ハンドラーを作成することはできません。 テキスト エディターで手動で入力する必要があります。 ClassWizard では、これらのエントリが解析され、その他のメッセージ マップ エントリと同じように参照できます。

Windows コモン コントロールを使用して、強力な[WM_NOTIFY](/windows/desktop/controls/wm-notify)の複雑なコントロールの通知。 このバージョンの MFC ON_NOTIFY メッセージと ON_NOTIFY_RANGE マクロを使用してこの新しいメッセージの直接サポートしています。 これらのマクロの詳細については、製品ドキュメントを参照してください。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
