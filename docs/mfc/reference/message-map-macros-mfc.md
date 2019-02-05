---
title: メッセージ マップ マクロ (MFC)
ms.date: 11/04/2016
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
ms.openlocfilehash: 6c6364dcf5d558bcdd25a2957721df1863d1f73f
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893666"
---
# <a name="message-map-macros-mfc"></a>メッセージ マップ マクロ (MFC)

メッセージ マップをサポートするには、mfc は、次のマクロを使用します。

### <a name="message-map-declaration-and-demarcation-macros"></a>メッセージ マップの宣言と定義用マクロ

|||
|-|-|
|[DECLARE_MESSAGE_MAP](#declare_message_map)|メッセージ マップがクラスで関数 (クラス宣言で使用する必要があります) にメッセージをマップに使用されることを宣言します。|
|[BEGIN_MESSAGE_MAP](#begin_message_map)|メッセージ マップ (クラスの実装で使用する必要があります) の定義を開始します。|
|[BEGIN_TEMPLATE_MESSAGE_MAP](#begin_template_interface_map)|1 つのテンプレート引数を格納しているクラス型のメッセージ マップの定義を開始します。 |
|[END_MESSAGE_MAP](#end_message_map)|メッセージ マップ (クラスの実装で使用する必要があります) の定義を終了します。|

### <a name="message-mapping-macros"></a>メッセージ マップ マクロ

|||
|-|-|
|[ON_COMMAND](#on_command)|指定されたコマンド メッセージを処理する関数を示します。|
|[ON_COMMAND_EX](#on_command_ex)|指定されたコマンド メッセージを処理する関数を示します。|
|[ON_CONTROL](#on_control)|指定されたコントロール通知メッセージを処理する関数を示します。|
|[ON_MESSAGE](#on_message)|ユーザー定義のメッセージを処理する関数を示します。|
|[ON_OLECMD](#on_olecmd)|DocObject またはそのコンテナーからのメニュー コマンドを処理する関数を示します。|
|[ON_REGISTERED_MESSAGE](#on_registered_message)|登録済みのユーザー定義メッセージを処理する関数を示します。|
|[ON_REGISTERED_THREAD_MESSAGE](#on_registered_thread_message)|ある場合、関数は、登録済みのユーザー定義メッセージを処理することを示します、`CWinThread`クラス。|
|[ON_THREAD_MESSAGE](#on_thread_message)|ある場合、関数は、ユーザー定義メッセージを処理することを示します、`CWinThread`クラス。|
|[ON_UPDATE_COMMAND_UI](#on_update_command_ui)|指定されたユーザー インターフェイスの更新コマンド メッセージを処理する関数を示します。|

### <a name="message-map-range-macros"></a>範囲のメッセージ マップ マクロ

|||
|-|-|
|[ON_COMMAND_RANGE](#on_command_range)|マクロに最初の 2 つのパラメーターで指定されたコマンド Id の範囲を処理する関数を示します。|
|[ON_UPDATE_COMMAND_UI_RANGE](#on_update_command_ui_range)|どの更新ハンドラーが最初の 2 つの pa で指定されたコマンド Id の範囲を処理することを示します] rameters マクロにします。|
|[ON_CONTROL_RANGE](#on_control_range)|コントロールのマクロに 2 番目と 3 番目のパラメーターで指定された Id の範囲からの通知を処理する関数を示します。 最初のパラメーターは、コントロールの通知メッセージ、BN_CLICKED などです。|

メッセージ マップ、メッセージ マップの宣言と定義用のマクロとメッセージ マップ マクロの詳細については、次を参照してください。[メッセージ マップ](../../mfc/reference/message-maps-mfc.md)と[メッセージの処理とのマッピング」](../../mfc/message-handling-and-mapping.md)します。 メッセージ マップの範囲の詳細については、次を参照してください。[メッセージ マップの範囲内のハンドラー](../../mfc/handlers-for-message-map-ranges.md)します。

## <a name="begin_message_map"></a> BEGIN_MESSAGE_MAP

メッセージ マップの定義を開始します。

### <a name="syntax"></a>構文

```
BEGIN_MESSAGE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
マップを持つメッセージ クラスの名前を指定します。

*baseClass*<br/>
基本クラスの名前を示す*クラス*します。

### <a name="remarks"></a>Remarks

クラスのメンバー関数を定義する、実装 (.cpp) ファイルで、BEGIN_MESSAGE_MAP マクロをメッセージ マップを開始し、メッセージ ハンドラー関数ごとのマクロのエントリを追加し、END_MESSAGE_MAP とメッセージ マップを完了マクロ。

メッセージ マップの詳細については、次を参照してください[メッセージ マップ。](message-maps-mfc.md)

### <a name="example"></a>例

```cpp
BEGIN_MESSAGE_MAP(CMainFrame, CMDIFrameWnd)
   ON_WM_CREATE()
END_MESSAGE_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="begin_template_message_map"></a>BEGIN_TEMPLATE_MESSAGE_MAP

1 つのテンプレート引数を格納しているクラス型のメッセージ マップの定義を開始します。

### <a name="syntax"></a>構文

```
BEGIN_TEMPLATE_MESSAGE_MAP( theClass, type_name, baseClass )
```

### <a name="parameters"></a>パラメーター

*クラス*<br/>
マップを持つメッセージ クラスの名前を指定します。

*type_name*<br/>
指定されたクラス テンプレート パラメーターの名前。

*baseClass*<br/>
基本クラスの名前を示す*クラス*します。

### <a name="remarks"></a>Remarks

このマクロは、 [BEGIN_MESSAGE_MAP](message-map-macros-mfc.md#begin_message_map)マクロです。 ただし、このマクロは 1 つのテンプレート引数を含むクラスのものです。

クラスのメソッドの実装のセクションで、同じようマクロ; メッセージ マップを開始します標準のメッセージ マップの場合とは、各メッセージ ハンドラー メソッドのマクロのエントリを追加します。 BEGIN_MESSAGE_MAP マクロでは、テンプレート メッセージ マップを完了すると、 [END_MESSAGE_MAP](message-map-macros-mfc.md#end_message_map)マクロ。

メッセージ マップのテンプレート クラスの実装の詳細についてを参照してください[方法。テンプレート クラスのメッセージ マップを作成する](../how-to-create-a-message-map-for-a-template-class.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="declare_message_map"></a>  DECLARE_MESSAGE_MAP

クラスがメッセージ マップを定義することを宣言します。 各`CCmdTarget`-プログラム内の派生クラスは、メッセージを処理するメッセージ マップを提供する必要があります。

### <a name="syntax"></a>構文

```
DECLARE_MESSAGE_MAP( )
```

### <a name="remarks"></a>Remarks

クラスの宣言の最後に DECLARE_MESSAGE_MAP マクロを使用します。 次に、クラスのメンバー関数を定義する .cpp ファイルでを使用して、BEGIN_MESSAGE_MAP マクロ、マクロのエントリの各種メッセージ ハンドラー関数、および END_MESSAGE_MAP マクロ。

> [!NOTE]
>  DECLARE_MESSAGE_MAP 後に任意のメンバーを宣言する場合は、新しいアクセスの種類を指定する必要があります (**パブリック**、**プライベート**、または**保護**) にします。

メッセージ マップおよび DECLARE_MESSAGE_MAP マクロの詳細については、次を参照してください。[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)します。

### <a name="example"></a>例

```cpp
class CMainFrame : public CMDIFrameWnd
{
   DECLARE_MESSAGE_MAP()

   // Remainder of class declaration omitted.
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="end_message_map"></a>  END_MESSAGE_MAP

メッセージ マップの定義を終了します。

### <a name="syntax"></a>構文

```
END_MESSAGE_MAP( )
```

### <a name="remarks"></a>Remarks

メッセージ マップおよび END_MESSAGE_MAP マクロの詳細については、次を参照してください。[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="on_command"></a>  ON_COMMAND

このマクロは、コマンド メッセージをメンバー関数にマップします。

### <a name="syntax"></a>構文

```
ON_COMMAND( id, memberFxn )
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
コマンド ID。

*memberFxn*<br/>
コマンドがマップされているメッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

メニュー項目またはツール バー ボタンなどのコマンドのユーザー インターフェイス オブジェクトからコマンド メッセージを処理する関数を示します。

ON_COMMAND が、メンバー関数を呼び出して、コマンド ターゲット オブジェクトは、指定の ID を持つ Windows WM_COMMAND メッセージを受信したときに`memberFxn`メッセージを処理します。

ON_COMMAND を使用して、1 つのコマンドをメンバー関数にマップします。 使用[ON_COMMAND_RANGE](#on_command_range)コマンド id の範囲を 1 つのメンバー関数にマップします。 1 つだけのメッセージ マップ エントリは、指定したコマンド id と一致できます。つまり、1 つ以上のハンドラーにコマンドを割り当てることはできません。 詳細と例については、次を参照してください。[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)します。

### <a name="example"></a>例

```cpp
BEGIN_MESSAGE_MAP(CMFCListViewDoc, CDocument)
   ON_COMMAND(ID_MYCOMMAND, &CMFCListViewDoc::OnMycommand)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_.h

## <a name="on_command_ex"></a>  ON_COMMAND_EX

コマンド ハンドラー メンバー関数を拡張します。

### <a name="syntax"></a>構文

```
ON_COMMAND_EX(id, memberFxn);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
コマンド ID。

*memberFxn*<br/>
コマンドがマップされているメッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

コマンド メッセージ ハンドラーの拡張の形式は高度な用途のために使用できます。 ON_COMMAND_EX マクロは、このようなメッセージ ハンドラーを使用してのスーパー セットを提供します、 [ON_COMMAND](message-map-macros-mfc.md#on_command)機能します。 拡張のコマンド ハンドラー メンバー関数では、コマンド ID を含む UINT、1 つのパラメーターを受け取るし、ブール値を返します。 戻り値が、コマンドが処理されたことを指定する場合は TRUE にする必要があります。それ以外の場合、ルーティングは、その他のコマンド ターゲット オブジェクトを続けます。

詳細については、テクニカル ノートを参照してください [TN006:。メッセージ マップ] tm006-メッセージ-maps.md)。

### <a name="requirements"></a>必要条件

ヘッダー ファイル: afxmsg_.h

### <a name="see-also"></a>関連項目

[ON_COMMAND](message-map-macros-mfc.md#on_command)<br/>
[TN006:メッセージ マップ](../tn006-message-maps.md)

## <a name="on_control"></a>  ON_CONTROL

カスタム コントロールの通知メッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_CONTROL( wNotifyCode, id, memberFxn )
```

### <a name="parameters"></a>パラメーター

*wNotifyCode*<br/>
コントロールの通知コード。

*ID*<br/>
コマンド ID。

*memberFxn*<br/>
コマンドがマップされているメッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

コントロールの通知メッセージを使用して、コントロールから親ウィンドウに送信されます。

メッセージ ハンドラー関数にマップする必要がありますすべてのコントロールの通知メッセージのメッセージ マップに ON_CONTROL マクロ ステートメントは 1 つだけ必要があります。

詳細と例については、次を参照してください。[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_.h

## <a name="on_message"></a>  ON_MESSAGE

ユーザー定義のメッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>パラメーター

*message*<br/>
メッセージ ID。

*memberFxn*<br/>
メッセージがマップされているメッセージ ハンドラー関数の名前。

関数の型である必要があります`afx_msg LRESULT (CWnd::*)(WPARAM, LPARAM)`します。

### <a name="remarks"></a>Remarks

ユーザー定義メッセージは、標準の Windows WM_MESSAGE メッセージではない任意のメッセージです。 メッセージ ID を選択すると、0x7FFF または WM_APP (0x8000) 0xBFFF に範囲の WM_USER (0x0400) 内の値を使用する必要があります。 メッセージ Id の詳細については、次を参照してください。 [WM_APP](/windows/desktop/winmsg/wm-app)します。

メッセージ ハンドラー関数にマップする必要がありますすべてのユーザー定義メッセージのメッセージ マップに ON_MESSAGE マクロ ステートメントは 1 つだけ必要があります。

> [!NOTE]
>  ユーザー定義のメッセージだけでなく ON_MESSAGE はあまり一般的な Windows メッセージを処理します。 詳細については、次を参照してください。[メッセージ マップ](../../mfc/tn006-message-maps.md)します。

詳細と例については、次を参照してください[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)と[ユーザー定義のハンドラー。](user-defined-handlers.md)

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

**ヘッダー:** afxmsg_.h

## <a name="on_olecmd"></a>  ON_OLECMD

コマンドをコマンドのディスパッチ インターフェイスを介してルーティング`IOleCommandTarget`します。

### <a name="syntax"></a>構文

```
ON_OLECMD( pguid, olecmdid, id )
```

### <a name="parameters"></a>パラメーター

*pguid*<br/>
コマンドが所属するコマンド グループの識別子。 標準のグループには、NULL を使用します。

*olecmdid*<br/>
OLE コマンドの識別子。

*ID*<br/>
メニュー ID、ツールバー ID、ボタン ID、またはその他の ID のリソースまたはオブジェクトのコマンドを実行します。

### <a name="remarks"></a>Remarks

`IOleCommandTarget` DocObject のユーザー インターフェイスでは、コマンドを受信するためのコンテナーを使用でき、同じコマンドを送信するコンテナー (新規、オープン、名前を付けて保存、および [ファイル] メニューの; 印刷など、コピー、貼り付け、元に戻したり、[編集] メニュー) DocObject にします。

`IOleCommandTarget` OLE オートメーションのよりも簡単です`IDispatch`します。 `IOleCommandTarget` コマンドの標準セットを完全に依存の引数を持つことはほとんどありませんし、型情報は必要ありません (タイプ セーフはコマンドの引数も低下)。 引数を持つコマンドをディスパッチする場合を使用して、 [COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)します。

`IOleCommandTarget`標準メニュー コマンドは、次のマクロに MFC によって実装されています。

**ON_OLECMD_CLEARSELECTION( )**

クリア編集コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_CLEARSELECTION, ID_EDIT_CLEAR)`

**ON_OLECMD_COPY( )**

コピーして編集コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_COPY, ID_EDIT_COPY)`

**ON_OLECMD_CUT( )**

編集 [切り取り] コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_CUT, ID_EDIT_CUT)`

**ON_OLECMD_NEW( )**

ファイルの新しいコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_NEW, ID_FILE_NEW)`

**ON_OLECMD_OPEN( )**

ファイルを開くコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_OPEN, ID_FILE_OPEN)`

**ON_OLECMD_PAGESETUP( )**

ファイルのページ設定 コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_PAGESETUP, ID_FILE_PAGE_SETUP)`

**ON_OLECMD_PASTE( )**

貼り付けコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_PASTE, ID_EDIT_PASTE)`

**ON_OLECMD_PASTESPECIAL( )**

編集貼り付けコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_PASTESPECIAL, ID_EDIT_PASTE_SPECIAL)`

**ON_OLECMD_PRINT( )**

ファイルの印刷 コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_PRINT, ID_FILE_PRINT)`

**ON_OLECMD_PRINTPREVIEW( )**

ファイルの印刷プレビュー コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_PRINTPREVIEW, ID_FILE_PRINT_PREVIEW)`

**ON_OLECMD_REDO( )**

やり直しコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_REDO, ID_EDIT_REDO)`

**ON_OLECMD_SAVE( )**

ファイルの保存のコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_SAVE, ID_FILE_SAVE)`

**ON_OLECMD_SAVE_AS( )**

ファイル名を付けてコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_SAVEAS, ID_FILE_SAVE_AS)`

**ON_OLECMD_SAVE_COPY_AS( )**

ファイルのコピーを付けて保存コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_SAVECOPYAS, ID_FILE_SAVE_COPY_AS)`

**ON_OLECMD_SELECTALL( )**

すべての編集コマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_SELECTALL, ID_EDIT_SELECT_ALL)`

**ON_OLECMD_UNDO( )**

編集を元に戻すコマンドをディスパッチします。 として実装されます。

`ON_OLECMD(NULL, OLECMDID_UNDO, ID_EDIT_UNDO)`

### <a name="requirements"></a>必要条件

**ヘッダー:** afxdocob.h

### <a name="see-also"></a>関連項目

[COleCmdUI クラス](colecmdui-class.md)<br/>
[COleServerDoc::OnExecOleCmd](coleserverdoc-class.md#onexecolecmd)

## <a name="on_registered_message"></a>  ON_REGISTERED_MESSAGE

Windows`RegisterWindowMessage`関数は、システム全体で一意であることが保証される、新しいウィンドウ メッセージを定義するために使用します。

### <a name="syntax"></a>構文

```
ON_REGISTERED_MESSAGE( nMessageVariable, memberFxn )
```

### <a name="parameters"></a>パラメーター

*nMessageVariable*<br/>
登録されたウィンドウ メッセージ ID の変数です。

*memberFxn*<br/>
メッセージがマップされているメッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

このマクロは、登録済みのメッセージを処理する関数を示します。

詳細と例については、次を参照してください。[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)します。

### <a name="example"></a>例

```cpp
static UINT NEAR WM_FIND = RegisterWindowMessage(_T("COMMDLG_FIND"));

BEGIN_MESSAGE_MAP(CMyWnd3, CWnd)
   ON_REGISTERED_MESSAGE(WM_FIND, OnFind)
END_MESSAGE_MAP()
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_.h

### <a name="see-also"></a>関連項目

[を通じて](/windows/desktop/api/winuser/nf-winuser-registerwindowmessagea)<br/>
[ユーザー定義によるハンドラー](user-defined-handlers.md)

## <a name="on_registered_thread_message"></a>  ON_REGISTERED_THREAD_MESSAGE

Windows を通じて関数によって登録されたメッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_REGISTERED_THREAD_MESSAGE(nMessageVariable, memberFxn )
```

### <a name="parameters"></a>パラメーター

*nMessageVariable*<br/>
登録されたウィンドウ メッセージ ID の変数です。

*memberFxn*<br/>
メッセージがマップされている CWinThread メッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

を通じてを使用して、システム全体で一意であることが保証される、新しいウィンドウ メッセージを定義します。 CWinThread クラスがある場合、システムではなく ON_REGISTERED_THREAD_MESSAGE を使用する必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_.h

## <a name="on_thread_message"></a>  ON_THREAD_MESSAGE

ユーザー定義のメッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_THREAD_MESSAGE( message, memberFxn )
```

### <a name="parameters"></a>パラメーター

*message*<br/>
メッセージ ID。

*memberFxn*<br/>
名前、 `CWinThread`-メッセージのメッセージがマップされているハンドラー関数。

### <a name="remarks"></a>Remarks

ある場合に、ON_MESSAGE ではなく ON_THREAD_MESSAGE を使用する必要があります、`CWinThread`クラス。 ユーザー定義メッセージは、標準の Windows WM_MESSAGE メッセージではない任意のメッセージです。 メッセージ ハンドラー関数にマップする必要がありますすべてのユーザー定義メッセージのメッセージ マップに ON_THREAD_MESSAGE マクロ ステートメントは 1 つだけ必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxole.h

## <a name="on_update_command_ui"></a>  ON_UPDATE_COMMAND_UI

このマクロは、ユーザー インターフェイスの更新コマンド メッセージを処理する関数を示します。

### <a name="syntax"></a>構文

```
ON_UPDATE_COMMAND_UI( id, memberFxn )
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
メッセージ ID。

*memberFxn*<br/>
メッセージがマップされているメッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

メッセージ ハンドラー関数にマップする必要がありますすべてのユーザー インターフェイス更新コマンドに対して、メッセージ マップに ON_UPDATE_COMMAND_UI マクロ ステートメントは 1 つだけ必要があります。

詳細と例については、次を参照してください。[メッセージの処理とマップ」](../../mfc/message-handling-and-mapping.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxole.h

### <a name="see-also"></a>関連項目

[CCmdUI クラス](ccmdui-class.md)

## <a name="on_command_range"></a>  ON_COMMAND_RANGE

コマンド Id の連続する範囲を 1 つのメッセージ ハンドラー関数にマップするのにには、このマクロを使用します。

### <a name="syntax"></a>構文

```
ON_COMMAND_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>パラメーター

*id1*<br/>
コマンド Id の連続する範囲の先頭のコマンド ID。

*id2*<br/>
コマンド Id の連続する範囲の最後のコマンド ID。

*memberFxn*<br/>
コマンドがマップされているメッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

Id の範囲の始まり*id1*で終わります*id2*します。

ON_COMMAND_RANGE を使用して、コマンド Id の範囲を 1 つのメンバー関数にマップします。 使用[ON_COMMAND](#on_command)に 1 つのコマンドをメンバー関数にマップします。 1 つだけのメッセージ マップ エントリが指定されたコマンド ID と一致できます。 つまり、1 つ以上のハンドラーにコマンドを割り当てることはできません。 メッセージの範囲のマッピングの詳細については、次を参照してください。[メッセージ マップの範囲内のハンドラー](../../mfc/handlers-for-message-map-ranges.md)します。

自分でマクロを配置する必要がありますので、メッセージ マップの範囲の自動サポートはありません。

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

**ヘッダー:** afxmsg_.h

## <a name="on_update_command_ui_range"></a>  ON_UPDATE_COMMAND_UI_RANGE

コマンド Id の連続する範囲を 1 つの更新メッセージ ハンドラー関数にマップします。

### <a name="syntax"></a>構文

```
ON_UPDATE_COMMAND_UI_RANGE( id1, id2, memberFxn )
```

### <a name="parameters"></a>パラメーター

*id1*<br/>
コマンド Id の連続する範囲の先頭のコマンド ID。

*id2*<br/>
コマンド Id の連続する範囲の最後のコマンド ID。

*memberFxn*<br/>
コマンドがマップされている更新メッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

更新メッセージ ハンドラーでは、メニュー項目と、コマンドに関連付けられたツール バー ボタンの状態を更新します。 Id の範囲の始まり*id1*で終わります*id2*します。

自分でマクロを配置する必要がありますので、メッセージ マップの範囲の自動サポートはありません。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_.h

## <a name="on_control_range"></a>  ON_CONTROL_RANGE

コントロール Id の連続する範囲を BN_CLICKED などの指定された Windows 通知メッセージの 1 つのメッセージ ハンドラー関数にマップするのにには、このマクロを使用します。

### <a name="syntax"></a>構文

```
ON_CONTROL_RANGE( wNotifyCode, id1, id2, memberFxn )
```

### <a name="parameters"></a>パラメーター

*wNotifyCode*<br/>
ハンドラーが応答する通知コード。

*id1*<br/>
コントロール Id の連続する範囲の先頭のコマンド ID。

*id2*<br/>
コントロール Id の連続する範囲の最後のコマンド ID。

*memberFxn*<br/>
コントロールがマップされているメッセージ ハンドラー関数の名前。

### <a name="remarks"></a>Remarks

Id の範囲の始まり*id1*で終わります*id2*します。 マップ コントロールのいずれかから指定された通知のハンドラーが呼び出されます。

自分でマクロを配置する必要がありますので、メッセージ マップの範囲の自動サポートはありません。

コントロール Id の範囲のハンドラー関数の実装の詳細についてを参照してください[メッセージ マップの範囲内のハンドラー](../../mfc/handlers-for-message-map-ranges.md)します。

### <a name="requirements"></a>必要条件

**ヘッダー:** afxmsg_.h
