---
title: メッセージ マップ マクロ (MFC)
ms.date: 03/27/2019
f1_keywords:
- AFXWIN/DECLARE_MESSAGE_MAP
- AFXWIN/BEGIN_MESSAGE_MAP
- AFXWIN/BEGIN_TEMPLATE_MESSAGE_MAP
- AFXWIN/END_MESSAGE_MAP
- AFXWIN/ON_COMMAND
- AFXWIN/ON_COMMAND_EX
- AFXWIN/ON_CONTROL
- AFXWIN/ON_MESSAGE
- AFXWIN/ON_OLECMD
- AFXWIN/ON_REGISTERED_MESSAGE
- AFXWIN/ON_REGISTERED_THREAD_MESSAGE
- AFXWIN/ON_THREAD_MESSAGE
- AFXWIN/ON_UPDATE_COMMAND_UI
- AFXWIN/ON_COMMAND_RANGE
- AFXWIN/ON_UPDATE_COMMAND_UI_RANGE
- AFXWIN/ON_CONTROL_RANGE
helpviewer_keywords:
- message map macros
- Windows messages [MFC], declaration
- demarcating Windows messages
- message maps [MFC], macros
- message maps [MFC], declaration and demarcation
- message mapping macros
- ranges, message map
- message map ranges
ms.assetid: 531b15ce-32b5-4ca0-a849-bb519616c731
ms.openlocfilehash: b88b745e3b70cf030f77f247ab03cd69d910109f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502084"
---
# <a name="message-map-macros-mfc"></a>メッセージ マップ マクロ (MFC)

メッセージマップをサポートするために、MFC には次のマクロが用意されています。

### <a name="message-map-declaration-and-demarcation-macros"></a>メッセージマップの宣言と境界のマクロ

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|メッセージを関数にマップするために、メッセージマップがクラスで使用されることを宣言します (クラス宣言で使用する必要があります)。|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|メッセージマップの定義を開始します (クラスの実装で使用する必要があります)。|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_message_map)|単一のテンプレート引数を含むクラス型のメッセージマップの定義を開始します。 |
|[END_MESSAGE_MAP](#end_message_map)|メッセージマップの定義を終了します (クラスの実装で使用する必要があります)。|

### <a name="message-mapping-macros"></a>メッセージマッピングマクロ

|||
|-|-|
|[ON_COMMAND](#on_command)|指定されたコマンドメッセージを処理する関数を示します。|
|[ON_COMMAND_EX](#on_command_ex)|指定されたコマンドメッセージを処理する関数を示します。|
|[ON_CONTROL](#on_control)|指定したコントロール通知メッセージを処理する関数を示します。|
|[ON_MESSAGE](#on_message)|ユーザー定義メッセージを処理する関数を示します。|
|[ON_OLECMD](#on_olecmd)|DocObject またはそのコンテナーからメニューコマンドを処理する関数を示します。|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|登録されているユーザー定義メッセージを処理する関数を示します。|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|`CWinThread`クラスがある場合に、登録されているユーザー定義メッセージを処理する関数を示します。|
|[ON_THREAD_MESSAGE](#on_thread_message)|`CWinThread`クラスがある場合に、ユーザー定義のメッセージを処理する関数を示します。|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|指定されたユーザーインターフェイスの更新コマンドメッセージを処理する関数を示します。|

### <a name="message-map-range-macros"></a>メッセージマップ範囲マクロ

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|マクロの最初の2つのパラメーターに指定されたコマンド Id の範囲を処理する関数を示します。|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|マクロの最初の2つのパラメーターに指定されたコマンド Id の範囲を処理する更新ハンドラーを示します。|
|[ON_CONTROL_RANGE](#on_control_range)|マクロの2番目と3番目のパラメーターで指定されたコントロール Id の範囲からの通知を処理する関数を示します。 最初のパラメーターは、BN_CLICKED などの制御通知メッセージです。|

メッセージマップ、メッセージマップの宣言マクロ、およびメッセージマップマクロの詳細については、「[メッセージマップ](../../mfc/reference/message-maps-mfc.md)と[メッセージの処理とマッピングに関するトピック](../../mfc/message-handling-and-mapping.md)」を参照してください。 メッセージマップの範囲の詳細については、「[メッセージマップの範囲のハンドラー](../../mfc/handlers-for-message-map-ranges.md)」を参照してください。

## <a name="begin_message_map"></a>BEGIN_MESSAGE_MAP

メッセージマップの定義を開始します。

### <a name="syntax"></a>構文

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
メッセージをマップするクラスの名前を指定します。

*baseClass*<br/>
*クラス*の基底クラスの名前を指定します。

### <a name="remarks"></a>Remarks

クラスのメンバー関数を定義する実装 (.cpp) ファイルで、BEGIN_MESSAGE_MAP マクロを使用してメッセージマップを開始し、各メッセージハンドラー関数にマクロエントリを追加して、END_MESSAGE_MAP を使用してメッセージマップを完了します。マクロ.

メッセージマップの詳細については、「[メッセージマップ](message-maps-mfc.md)」を参照してください。

### <a name="example"></a>例

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

単一のテンプレート引数を含むクラス型のメッセージマップの定義を開始します。

### <a name="syntax"></a>構文

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
メッセージをマップするクラスの名前を指定します。

*type_name*<br/>
クラスに対して指定されたテンプレートパラメーターの名前。

*baseClass*<br/>
*クラス*の基底クラスの名前を指定します。

### <a name="remarks"></a>Remarks

このマクロは、 [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map)マクロに似ています。ただし、このマクロは、1つのテンプレート引数を含むクラスを対象としています。

クラスのメソッドの実装セクションで、BEGIN_TEMPLATE_MESSAGE_MAP マクロを使用してメッセージマップを開始します。次に、標準のメッセージマップの場合と同じように、メッセージハンドラーの各メソッドにマクロエントリを追加します。 BEGIN_MESSAGE_MAP マクロと同様に、 [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map)マクロを使用して、テンプレートメッセージマップを完成させます。

テンプレートクラスのメッセージマップの実装の詳細について[は、「方法:テンプレートクラス](../how-to-create-a-message-map-for-a-template-class.md)のメッセージマップを作成します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="declare_message_map"></a>  DECLARE_MESSAGE_MAP

クラスがメッセージマップを定義することを宣言します。 プログラム`CCmdTarget`内の各派生クラスは、メッセージを処理するためのメッセージマップを提供する必要があります。

### <a name="syntax"></a>構文

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Remarks

クラス宣言の最後に DECLARE_MESSAGE_MAP マクロを使用します。 次に、クラスのメンバー関数を定義する .cpp ファイルで、BEGIN_MESSAGE_MAP マクロ、各メッセージハンドラー関数のマクロエントリ、および END_MESSAGE_MAP マクロを使用します。

> [!NOTE]
>  DECLARE_MESSAGE_MAP の後にメンバーを宣言する場合は、そのメンバーに対して新しいアクセスの種類 (**パブリック**、**プライベート**、または**保護**) を指定する必要があります。

メッセージマップと DECLARE_MESSAGE_MAP マクロの詳細については、「[メッセージの処理とマッピング](../../mfc/message-handling-and-mapping.md)に関するトピック」を参照してください。

### <a name="example"></a>例

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="end_message_map"></a>END_MESSAGE_MAP

メッセージマップの定義を終了します。

### <a name="syntax"></a>構文

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Remarks

メッセージマップと END_MESSAGE_MAP マクロの詳細については、「[メッセージの処理とマッピング](../../mfc/message-handling-and-mapping.md)に関するトピック」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="on_command"></a>ON_COMMAND

このマクロは、コマンドメッセージをメンバー関数にマップします。

### <a name="syntax"></a>構文

```
ON_COMMAND( commandId, memberFxn )
```

### <a name="parameters"></a>パラメーター

*commandId*<br/>
コマンド ID。

*memberFxn*<br/>
コマンドのマップ先となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

これは、メニュー項目やツールバーボタンなどのコマンドユーザーインターフェイスオブジェクトからコマンドメッセージを処理する関数を示します。

コマンドターゲットオブジェクトが、指定された ID を持つ Windows WM_COMMAND メッセージを受信すると、ON_COMMAND は`memberFxn`そのメッセージを処理するためにメンバー関数を呼び出します。

ON_COMMAND を使用して、1つのコマンドをメンバー関数にマップします。 [ON_COMMAND_RANGE](#on_command_range)を使用して、コマンド id の範囲を1つのメンバー関数にマップします。 指定されたコマンド ID に一致できるメッセージマップエントリは1つだけです。 つまり、1つのコマンドを複数のハンドラーにマップすることはできません。 詳細と例については、「[メッセージの処理とマッピングに関するトピック](../../mfc/message-handling-and-mapping.md)」を参照してください。

### <a name="example"></a>例

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="on_command_ex"></a>  ON_COMMAND_EX

拡張コマンドハンドラーメンバー関数。

### <a name="syntax"></a>構文

```
ON_COMMAND_EX(commandId, memberFxn);
```

### <a name="parameters"></a>パラメーター

*commandId*<br/>
コマンド ID。

*memberFxn*<br/>
コマンドのマップ先となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

高度な用途では、拡張された形式のコマンドメッセージハンドラーを使用できます。 ON_COMMAND_EX マクロは、このようなメッセージハンドラーに使用され、 [ON_COMMAND](message-map-macros-mfc.md#on_command)機能のスーパーセットを提供します。 拡張コマンドハンドラーのメンバー関数は、1つのパラメーター (コマンド ID を含む UINT) を受け取り、ブール値を返します。 コマンドが処理されたことを示すには、戻り値が TRUE である必要があります。それ以外の場合、ルーティングは他のコマンドターゲットオブジェクトに進みます。

詳細については、「テクニカルノート [テクニカルノート 6:メッセージマップ] tm006-maps.md)。

### <a name="requirements"></a>必要条件

ヘッダーファイル: afxmsg_

## <a name="on_control"></a>ON_CONTROL

カスタムコントロールの通知メッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_CONTROL( wNotifyCode, commandId, memberFxn )
```

### <a name="parameters"></a>パラメーター

*wNotifyCode*<br/>
コントロールの通知コード。

*commandId*<br/>
コマンド ID。

*memberFxn*<br/>
コマンドのマップ先となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

コントロール通知メッセージは、コントロールから親ウィンドウに送信されます。

メッセージハンドラー関数にマップする必要があるすべてのコントロール通知メッセージに対して、メッセージマップには ON_CONTROL マクロステートメントが1つだけ必要です。

詳細と例については、「[メッセージの処理とマッピングに関するトピック](../../mfc/message-handling-and-mapping.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="on_message"></a>ON_MESSAGE

ユーザー定義メッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>パラメーター

*message*<br/>
メッセージ ID。

*memberFxn*<br/>
メッセージのマップ先となるメッセージハンドラー関数の名前。

関数の型はで`afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`ある必要があります。

### <a name="remarks"></a>Remarks

ユーザー定義メッセージは、標準の Windows WM_MESSAGE メッセージではないメッセージです。 メッセージ ID を選択する場合は、WM_USER (0x0400) の範囲内の値を、WM_APP (0x8000) から0xBFFF までの範囲内で使用する必要があります。 メッセージ Id の詳細については、「 [WM_APP](/windows/win32/winmsg/wm-app)」を参照してください。

メッセージハンドラー関数にマップする必要があるすべてのユーザー定義メッセージについて、メッセージマップには ON_MESSAGE マクロステートメントが1つだけ必要です。

> [!NOTE]
>  ON_MESSAGE は、ユーザー定義メッセージに加えて、あまり一般的でない Windows メッセージを処理します。 詳細については、「[メッセージマップ](../../mfc/tn006-message-maps.md)」を参照してください。

詳細と例については、「[メッセージの処理とマッピングに関するトピック](../../mfc/message-handling-and-mapping.md)」および「[ユーザー定義のハンドラー](user-defined-handlers.md) 」を参照してください。

### <a name="example"></a>例

```cpp
#define WM_MYMESSAGE (WM_USER + 100)

BEGIN_MESSAGE_MAP(CMyWnd2, CWnd)
   ON_MESSAGE(WM_MYMESSAGE, OnMyMessage)
END_MESSAGE_MAP()

// inside the class declaration
afx_msg LRESULT OnMyMessage(WPARAM wParam, LPARAM lParam);

LRESULT CMyWnd2::OnMyMessage(WPARAM wParam, LPARAM lParam)
{
   UNREFERENCED_PARAMETER(wParam);
   UNREFERENCED_PARAMETER(lParam);

   // Handle message here.

   return 0;
}
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="on_olecmd"></a>  ON_OLECMD

コマンドディスパッチインターフェイス`IOleCommandTarget`を使用してコマンドをルーティングします。

### <a name="syntax"></a>構文

```
ON_OLECMD( pguid, olecmdid, commandId )
```

### <a name="parameters"></a>パラメーター

*pguid*<br/>
コマンドが属するコマンドグループの識別子。 標準のグループには NULL を使用します。

*olecmdid*<br/>
OLE コマンドの識別子。

*commandId*<br/>
コマンドを発行するリソースまたはオブジェクトのメニュー ID、ツールバー ID、ボタン ID、またはその他の ID。

### <a name="remarks"></a>Remarks

`IOleCommandTarget`コンテナーが DocObject のユーザーインターフェイスで開始されたコマンドを受信できるようにし、コンテナーが同じコマンド ([ファイル] メニューの [新規]、[開く]、[保存]、[印刷] など) を送信できるようにします。また、[編集] メニューでは、コピー、貼り付け、元に戻すなどの操作を実行できます。

`IOleCommandTarget`は、OLE オートメーションの`IDispatch`よりも簡単です。 `IOleCommandTarget`は、ほとんどの場合、引数を持たない標準のコマンドセットに依存しており、型情報は含まれていません (コマンド引数に対してタイプセーフも低下します)。 引数を指定してコマンドをディスパッチする必要がある場合は、 [COleServerDoc:: OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)を使用します。

標準`IOleCommandTarget`のメニューコマンドは、次のマクロで MFC によって実装されています。

**ON_OLECMD_CLEARSELECTION( )**

Edit Clear コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

Edit Copy コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

Edit Cut コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

File New コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

File Open コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

ファイルページのセットアップコマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

Edit Paste コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

Edit Paste Special コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

ファイル印刷コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

ファイル印刷プレビューコマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

[やり直し] コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

ファイル保存コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

ファイルの名前を付けて保存コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

ファイルの [名前を付けて保存] コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

Edit Select All コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

[元に戻す] コマンドをディスパッチします。 次のように実装されます。

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdocob

## <a name="on_registered_message"></a>  ON_REGISTERED_MESSAGE

Windows `RegisterWindowMessage`関数は、システム全体で一意であることが保証される新しいウィンドウメッセージを定義するために使用されます。

### <a name="syntax"></a>構文

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>パラメーター

*nMessageVariable*<br/>
登録されたウィンドウメッセージ ID 変数。

*memberFxn*<br/>
メッセージのマップ先となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

このマクロは、登録されたメッセージを処理する関数を示します。

詳細と例については、「[メッセージの処理とマッピングに関するトピック](../../mfc/message-handling-and-mapping.md)」を参照してください。

### <a name="example"></a>例

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="on_registered_thread_message"></a>ON_REGISTERED_THREAD_MESSAGE

Windows RegisterWindowMessage 関数によって登録されたメッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>パラメーター

*nMessageVariable*<br/>
登録されたウィンドウメッセージ ID 変数。

*memberFxn*<br/>
メッセージがマップされる CWinThread メッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

RegisterWindowMessage は、システム全体で一意であることが保証される新しいウィンドウメッセージを定義するために使用されます。 CWinThread クラスがある場合は、ON_REGISTERED_MESSAGE の代わりに ON_REGISTERED_THREAD_MESSAGE を使用する必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="on_thread_message"></a>ON_THREAD_MESSAGE

ユーザー定義メッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>パラメーター

*message*<br/>
メッセージ ID。

*memberFxn*<br/>
メッセージのマップ先`CWinThread`となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

クラスがある場合は、 `CWinThread` ON_MESSAGE の代わりに ON_THREAD_MESSAGE を使用する必要があります。 ユーザー定義メッセージは、標準の Windows WM_MESSAGE メッセージではないメッセージです。 メッセージハンドラー関数にマップする必要があるすべてのユーザー定義メッセージについて、メッセージマップには ON_THREAD_MESSAGE マクロステートメントが1つだけ必要です。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxole

## <a name="on_update_command_ui"></a>ON_UPDATE_COMMAND_UI

このマクロは、ユーザーインターフェイスの更新コマンドメッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_UPDATE_COMMAND_UI( messageId, memberFxn )
```

### <a name="parameters"></a>パラメーター

*Id*<br/>
メッセージ ID。

*memberFxn*<br/>
メッセージのマップ先となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

メッセージハンドラー関数にマップする必要があるすべてのユーザーインターフェイス更新コマンドに対して、メッセージマップには ON_UPDATE_COMMAND_UI マクロステートメントが1つだけ必要です。

詳細と例については、「[メッセージの処理とマッピングに関するトピック](../../mfc/message-handling-and-mapping.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxole

## <a name="on_command_range"></a>  ON_COMMAND_RANGE

このマクロを使用して、連続したコマンド Id の範囲を1つのメッセージハンドラー関数にマップします。

### <a name="syntax"></a>構文

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>パラメーター

*id1*<br/>
コマンド ID の連続した範囲の先頭にあるコマンド ID。

*id2*<br/>
コマンド ID の連続する範囲の末尾にあるコマンド ID。

*memberFxn*<br/>
コマンドのマップ先となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

Id の範囲は*id1*で始まり、 *id2*で終わります。

ON_COMMAND_RANGE を使用して、コマンド Id の範囲を1つのメンバー関数にマップします。 [ON_COMMAND](#on_command)を使用して、1つのコマンドをメンバー関数にマップします。 指定されたコマンド ID に一致できるメッセージマップエントリは1つだけです。 つまり、1つのコマンドを複数のハンドラーにマップすることはできません。 メッセージ範囲のマッピングの詳細については、「[メッセージマップの範囲のハンドラー](../../mfc/handlers-for-message-map-ranges.md)」を参照してください。

メッセージマップの範囲は自動でサポートされないため、自分でマクロを配置する必要があります。

### <a name="example"></a>例

```cpp
// The code fragment below shows how to use ON_COMMAND_RANGE macro
// to map a contiguous range of command IDs to a single message
// handler function (i.e. OnRangeCmds() in the sample below). In
// addition, it also shows how to use CheckMenuRadioItem() to check a
// selected menu item and makes it a radio item.

BEGIN_MESSAGE_MAP(CChildFrame, CMDIChildWnd)
   ON_COMMAND_RANGE(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3, &CChildFrame::OnRangeCmds)
END_MESSAGE_MAP()

void CChildFrame::OnRangeCmds(UINT nID)
{
   CMenu* mmenu = AfxGetMainWnd()->GetMenu();
   CMenu* submenu = mmenu->GetSubMenu(5);
   submenu->CheckMenuRadioItem(ID_COMMAND_RANGECMD1, ID_COMMAND_RANGECMD3,
      nID, MF_BYCOMMAND);
}
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="on_update_command_ui_range"></a>ON_UPDATE_COMMAND_UI_RANGE

連続したコマンド Id の範囲を1つの更新メッセージハンドラー関数にマップします。

### <a name="syntax"></a>構文

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>パラメーター

*id1*<br/>
コマンド ID の連続した範囲の先頭にあるコマンド ID。

*id2*<br/>
コマンド ID の連続する範囲の末尾にあるコマンド ID。

*memberFxn*<br/>
コマンドのマップ先となる更新メッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

更新メッセージハンドラーは、コマンドに関連付けられているメニュー項目とツールバーボタンの状態を更新します。 Id の範囲は*id1*で始まり、 *id2*で終わります。

メッセージマップの範囲は自動でサポートされないため、自分でマクロを配置する必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="on_control_range"></a>ON_CONTROL_RANGE

このマクロを使用して、指定した Windows 通知メッセージ (BN_CLICKED など) に対して、連続した範囲のコントロール Id を1つのメッセージハンドラー関数にマップします。

### <a name="syntax"></a>構文

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>パラメーター

*wNotifyCode*<br/>
ハンドラーが応答する通知コード。

*id1*<br/>
連続した範囲のコントロール Id の先頭にあるコマンド ID。

*id2*<br/>
コントロール Id の連続した範囲の末尾にあるコマンド ID。

*memberFxn*<br/>
コントロールのマップ先となるメッセージハンドラー関数の名前。

### <a name="remarks"></a>Remarks

Id の範囲は*id1*で始まり、 *id2*で終わります。 ハンドラーは、マップされたコントロールのいずれかから送られた指定の通知に対して呼び出されます。

メッセージマップの範囲は自動でサポートされないため、自分でマクロを配置する必要があります。

コントロール Id の範囲に対するハンドラー関数の実装の詳細については、「[メッセージマップの範囲のハンドラー](../../mfc/handlers-for-message-map-ranges.md)」を参照してください。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_

## <a name="see-also"></a>関連項目

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[テクニカル ノート 6: メッセージ マップ](../tn006-message-maps.md)<br/>
[COleCmdUI クラス](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)<br/>
[RegisterWindowMessage](/windows/win32/api/winuser/nf-winuser-registerwindowmessagew)<br/>
[ユーザー定義によるハンドラー](user-defined-handlers.md)<br/>
[CCmdUI クラス](ccmdui-class.md)
