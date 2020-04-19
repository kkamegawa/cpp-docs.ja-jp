---
title: テクニカル ノート 6:メッセージ マップ
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
ms.openlocfilehash: 489db046910cc4b44e381b3f9056cfe8f8b7ccfa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69511106"
---
# <a name="tn006-message-maps"></a>テクニカル ノート 6:メッセージ マップ

このメモでは、MFC メッセージマップ機能について説明します。

## <a name="the-problem"></a>問題を

Microsoft Windows では、メッセージング機能を使用するウィンドウクラスに仮想関数を実装しています。 大量のメッセージが含まれているため、Windows メッセージごとに個別の仮想関数を指定すると、非常に大きな vtable が作成されます。

システム定義の Windows メッセージの数は時間の経過と共に変化するため、アプリケーションは独自の Windows メッセージを定義できるため、メッセージマップでは、インターフェイスの変更が既存のコードに影響を与えないようにする間接的なレベルが提供されます。

## <a name="overview"></a>概要

MFC には、ウィンドウに送信されたメッセージを処理するために従来の Windows ベースのプログラムで使用されていた switch ステートメントの代わりとして、が用意されています。 メッセージからメソッドへのマッピングを定義して、メッセージがウィンドウによって受信されたときに、適切なメソッドが自動的に呼び出されるようにすることができます。 このメッセージマップ機能は、仮想機能と似ていますが、仮想関数でC++は実現できない追加の利点があります。

## <a name="defining-a-message-map"></a>メッセージマップの定義

[DECLARE_MESSAGE_MAP](reference/message-map-macros-mfc.md#declare_message_map)マクロは、クラスの3つのメンバーを宣言します。

- AFX_MSGMAP_ENTRY エントリのプライベート配列 (" *messageentries")* 。

- *MessageMap*と呼ばれる protected AFX_MSGMAP 構造体。これは、 *messageentries*配列を指します。

- MessageMap のアドレスを返す`GetMessageMap` 、と呼ばれるプロテクト仮想関数。

このマクロは、メッセージマップを使用して、任意のクラスの宣言に配置する必要があります。 慣例により、これはクラス宣言の最後にあります。 例えば:

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

これは、AppWizard および ClassWizard で新しいクラスを作成するときに生成される形式です。 ClassWizard には、//{{および//}} かっこが必要です。

メッセージマップのテーブルは、メッセージマップエントリに展開されるマクロのセットを使用して定義されます。 テーブルは[BEGIN_MESSAGE_MAP](reference/message-map-macros-mfc.md#begin_message_map)マクロ呼び出しで始まります。このマクロ呼び出しでは、このメッセージマップによって処理されるクラスと、未処理のメッセージが渡される親クラスが定義されます。 テーブルは、 [END_MESSAGE_MAP](reference/message-map-macros-mfc.md#end_message_map)マクロ呼び出しで終了します。

これら2つのマクロ呼び出しの間には、このメッセージマップによって処理される各メッセージのエントリがあります。 すべての標準 Windows メッセージには、そのメッセージのエントリを生成する ON_WM_*MESSAGE_NAME*という形式のマクロがあります。

各 Windows メッセージのパラメーターをアンパックし、タイプセーフを提供するために、標準の関数シグネチャが定義されています。 これらの署名は、 [CWnd](../mfc/reference/cwnd-class.md)の宣言の afxwin.h ファイルにあります。 識別を容易にするために、それぞれにキーワード**afx_msg**が設定されています。

> [!NOTE]
> ClassWizard では、メッセージマップハンドラーの宣言で**afx_msg**キーワードを使用する必要があります。

これらの関数シグネチャは、単純な規約を使用して派生されています。 関数の名前は常に "で`"On`始まります。 この後に、"WM_" が削除された Windows メッセージの名前と、各単語の最初の文字が大文字になります。 パラメーターの順序は、 *wParam*の後に`LOWORD`(*lparam*) then `HIWORD`(*lparam*) となります。 未使用のパラメーターは渡されません。 MFC クラスによってラップされたハンドルは、適切な MFC オブジェクトへのポインターに変換されます。 次の例では、WM_PAINT メッセージを処理し`CMyWnd::OnPaint` 、関数を呼び出す方法を示します。

```cpp
BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    //{{AFX_MSG_MAP(CMyWnd)
    ON_WM_PAINT()
    //}}AFX_MSG_MAP
END_MESSAGE_MAP()
```

メッセージマップテーブルは、関数またはクラス定義のスコープ外で定義する必要があります。 Extern "C" ブロックには含めないでください。

> [!NOTE]
> ClassWizard は、//{{と//}} のコメントのかっこの間に出現するメッセージマップエントリを変更します。

## <a name="user-defined-windows-messages"></a>ユーザー定義の Windows メッセージ

ユーザー定義メッセージは、 [ON_MESSAGE](reference/message-map-macros-mfc.md#on_message)マクロを使用してメッセージマップに含めることができます。 このマクロは、次の形式のメッセージ番号とメソッドを受け入れます。

```cpp
    // inside the class declaration
    afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

    #define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd, CMyParentWndClass)
    ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()
```

この例では、ユーザー定義メッセージの標準 WM_USER base から派生した Windows メッセージ ID を持つカスタムメッセージのハンドラーを設定します。 次の例は、このハンドラーを呼び出す方法を示しています。

```cpp
CWnd* pWnd = ...;
pWnd->SendMessage(WM_MYMESSAGE);
```

この方法を使用するユーザー定義メッセージの範囲は、WM_USER ~ の範囲内である必要があります。

> [!NOTE]
> ClassWizard は、ClassWizard ユーザーインターフェイスからの ON_MESSAGE handler ルーチンの入力をサポートしていません。 ビジュアルC++エディターから手動で入力する必要があります。 ClassWizard は、これらのエントリを解析し、他のメッセージマップエントリと同じように参照できるようにします。

## <a name="registered-windows-messages"></a>登録済みの Windows メッセージ

[Registerwindowmessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)関数は、システム全体で一意であることが保証される新しいウィンドウメッセージを定義するために使用されます。 マクロ ON_REGISTERED_MESSAGE は、これらのメッセージを処理するために使用されます。 このマクロは、登録されている windows メッセージ ID を含む*UINT NEAR*変数の名前を受け入れます。 次に例を示します。

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

登録されている Windows メッセージ ID 変数 (この例では WM_FIND) は、ON_REGISTERED_MESSAGE の実装方法により、 *NEAR*変数である必要があります。

この方法を使用するユーザー定義メッセージの範囲は、0xC000 ~ 0xFFFF の範囲になります。

> [!NOTE]
> ClassWizard は、ClassWizard ユーザーインターフェイスからの ON_REGISTERED_MESSAGE handler ルーチンの入力をサポートしていません。 テキストエディターから手動で入力する必要があります。 ClassWizard は、これらのエントリを解析し、他のメッセージマップエントリと同じように参照できるようにします。

## <a name="command-messages"></a>コマンド メッセージ

メニューおよびアクセラレータからのコマンドメッセージは、ON_COMMAND マクロを使用してメッセージマップで処理されます。 このマクロは、コマンド ID とメソッドを受け入れます。 指定されたコマンド ID と等しい*wParam*を持つ特定の WM_COMMAND メッセージのみが、メッセージマップエントリに指定されたメソッドによって処理されます。 コマンドハンドラーのメンバー関数は、パラメーターを取らず、 **void**を返します。 マクロには、次の形式があります。

```cpp
ON_COMMAND(id, memberFxn)
```

コマンド更新メッセージは同じメカニズムを通じてルーティングされますが、代わりに ON_UPDATE_COMMAND_UI マクロを使用します。 コマンド更新ハンドラーのメンバー関数は、単一のパラメーター、 [CCmdUI](../mfc/reference/ccmdui-class.md)オブジェクトへのポインターを受け取り、 **void**を返します。 マクロの形式は、

```cpp
ON_UPDATE_COMMAND_UI(id, memberFxn)
```

上級ユーザーは、コマンドメッセージハンドラーの拡張形式である ON_COMMAND_EX マクロを使用できます。 マクロは、ON_COMMAND 機能のスーパーセットを提供します。 拡張コマンドハンドラーのメンバー関数は、1つのパラメーターを受け取り、コマンド ID を含む**UINT**を返し、**ブール**値を返します。 コマンドが処理されたことを示すには、戻り値が**TRUE**である必要があります。 それ以外の場合、ルーティングは他のコマンドターゲットオブジェクトに進みます。

これらの形式の例を次に示します。

- (通常は、Visual C++によって生成される) resource.h 内

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

- メッセージマップ定義内

    ```cpp
    ON_COMMAND(ID_MYCMD, OnMyCommand)
    ON_UPDATE_COMMAND_UI(ID_MYCMD, OnUpdateMyCommand)
    ON_COMMAND_EX(ID_MYCMD, OnComplexCommand)
    ```

- 実装ファイル内

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

上級ユーザーは、1つのコマンドハンドラーを使用して、さまざまなコマンドを処理できます。[ON_COMMAND_RANGE](reference/message-map-macros-mfc.md#on_command_range)または ON_COMMAND_RANGE_EX。 これらのマクロの詳細については、製品のドキュメントを参照してください。

> [!NOTE]
> ClassWizard では、ON_COMMAND ハンドラーと ON_UPDATE_COMMAND_UI ハンドラーの作成がサポートされていますが、ON_COMMAND_EX ハンドラーまたは ON_COMMAND_RANGE ハンドラーの作成はサポートしていません。 ただし、クラスウィザードは解析を行い、4つのコマンドハンドラーのすべてのバリアントを参照できるようにします。

## <a name="control-notification-messages"></a>通知メッセージの制御

子コントロールからウィンドウに送信されるメッセージには、そのコントロールの ID であるメッセージマップエントリに追加の情報が含まれます。 メッセージマップエントリに指定されたメッセージハンドラーは、次の条件に該当する場合にのみ呼び出されます。

- メッセージマップエントリに指定されている通知コードは、コントロール通知コード ( *lParam*の上位ワード) と一致します。

- コントロール ID (*wParam*) は、メッセージマップエントリで指定されたコントロール id と一致します。

カスタムコントロール通知メッセージでは、 [ON_CONTROL](reference/message-map-macros-mfc.md#on_control)マクロを使用して、カスタム通知コードを含むメッセージマップエントリを定義できます。 このマクロの形式は次のようになります。

```cpp
ON_CONTROL(wNotificationCode, id, memberFxn)
```

[ON_CONTROL_RANGE](reference/message-map-macros-mfc.md#on_control_range)を使用すると、同じハンドラーを持つさまざまなコントロールから特定のコントロール通知を処理できます。

> [!NOTE]
> ClassWizard では、ユーザーインターフェイスでの ON_CONTROL または ON_CONTROL_RANGE ハンドラーの作成はサポートされていません。 テキストエディターを使用して手動で入力する必要があります。 ClassWizard は、これらのエントリを解析し、他のメッセージマップエントリと同じように参照できるようにします。

Windows コモンコントロールでは、複雑なコントロール通知により強力な[WM_NOTIFY](/windows/win32/controls/wm-notify)が使用されます。 このバージョンの MFC では、ON_NOTIFY マクロと ON_NOTIFY_RANGE マクロを使用して、この新しいメッセージを直接サポートしています。 これらのマクロの詳細については、製品のドキュメントを参照してください。

## <a name="see-also"></a>関連項目

[番号順テクニカル ノート](../mfc/technical-notes-by-number.md)<br/>
[カテゴリ別テクニカル ノート](../mfc/technical-notes-by-category.md)
