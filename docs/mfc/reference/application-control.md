---
title: アプリケーションの制御
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 934cb53fa4cb59fea611bfeb9db110d8d6f7d165
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/14/2019
ms.locfileid: "65612298"
---
# <a name="application-control"></a>アプリケーションの制御

OLE には、アプリケーションとそれらのオブジェクトを十分に制御が必要です。 OLE システム Dll を起動し、アプリケーションを自動的にリリースし、運用環境と、オブジェクトの変更を調整、具合できる必要があります。 このトピック内の関数は、その要件を満たしています。 、OLE システム Dll によって呼び出されるだけでなくこれらの関数をアプリケーションにもから呼び出すことがありますする必要があります。

### <a name="application-control"></a>アプリケーションの制御

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|アプリケーションが終了できるかどうかを示します。|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|アプリケーションの現在のメッセージ フィルターを取得します。|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|現在のユーザー制御フラグを取得します。|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|設定またはユーザー コントロール フラグをクリアします。|
|[AfxOleLockApp](#afxolelockapp)|アプリケーションのアクティブなオブジェクトの数のフレームワークのグローバルなカウントをインクリメントします。|
|[AfxOleLockControl](#afxolelockcontrol)| 指定したコントロールのクラス ファクトリをロックします。 |
|[AfxOleUnlockApp](#afxoleunlockapp)|デクリメントするアプリケーションのアクティブなオブジェクトの数のフレームワークの数。|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| 指定したコントロールのクラス ファクトリのロックを解除します。 |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|OLE システム レジストリでサーバーを登録します。|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|ユーザー インターフェイスを実装、 *typename*オブジェクト コマンド。|

##  <a name="afxolecanexitapp"></a>  AfxOleCanExitApp

アプリケーションが終了できるかどうかを示します。

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>戻り値

以外の場合は、アプリケーションを終了できます。それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

アプリケーションでは、そのオブジェクトに未解決の参照がある場合は終了する必要があります。 グローバル関数`AfxOleLockApp`と`AfxOleUnlockApp`にインクリメントされ、それぞれ、アプリケーションのオブジェクトへの参照カウンターをデクリメントします。 このカウンターは、0 以外の場合、アプリケーションは終了できません。 カウンターが 0 以外の場合は、アプリケーションのメイン ウィンドウが非表示 (破棄されずに) ユーザーが システム メニューまたは ファイル メニューからの終了時から終了します。 フレームワークこの関数を呼び出す`CFrameWnd::OnClose`します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー**: afxdisp.h

##  <a name="afxolegetmessagefilter"></a>  AfxOleGetMessageFilter

アプリケーションの現在のメッセージ フィルターを取得します。

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>戻り値

現在のメッセージ フィルターへのポインター。

### <a name="remarks"></a>Remarks

現在にアクセスするには、この関数を呼び出す`COleMessageFilter`-呼び出す場合と同じように、オブジェクトを派生`AfxGetApp`現在のアプリケーション オブジェクトにアクセスします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー**: afxwin.h

##  <a name="afxolegetuserctrl"></a>  AfxOleGetUserCtrl

現在のユーザー制御フラグを取得します。

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>戻り値

以外の場合は、ユーザーがアプリケーションの管理それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

ユーザーが明示的に開くか、新しいドキュメントを作成すると、ユーザーがアプリケーションの管理です。 ユーザーはコントロールにも、OLE システム Dll によって、アプリケーションを起動しなかった場合、つまり、ユーザーがシステムのシェルを使用してアプリケーションを起動した場合。

### <a name="requirements"></a>必要条件

**ヘッダー**: afxdisp.h

##  <a name="afxolesetuserctrl"></a>  AfxOleSetUserCtrl

設定のリファレンスで説明するユーザー制御フラグをクリアまたは`AfxOleGetUserCtrl`します。

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>パラメーター

*bUserCtrl*<br/>
ユーザー制御フラグを設定またはクリアするかどうかを指定します。

### <a name="remarks"></a>Remarks

フレームワークが呼び出しますが、ユーザーを作成またはドキュメントを読み込みますドキュメントが読み込まれたまたは、コンテナーのアプリケーションからの埋め込みオブジェクトの読み込みなどの間接のアクションを使って作成されたときではなく。

この関数を呼び出す場合は、アプリケーションでは、その他のアクションは、アプリケーションのコントロールでユーザーを配置する必要があります。

### <a name="requirements"></a>必要条件

**ヘッダー**: afxdisp.h

##  <a name="afxolelockapp"></a>  AfxOleLockApp

アプリケーションのアクティブなオブジェクトの数のフレームワークのグローバルなカウントをインクリメントします。

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Remarks

フレームワークは、アプリケーションでアクティブなオブジェクトの数のカウントを保持します。 `AfxOleLockApp`と`AfxOleUnlockApp`関数はそれぞれ、インクリメントし、このカウントをデクリメントします。

ユーザーがアクティブなオブジェクトを持つアプリケーションを終了しようとしたときに: アクティブなオブジェクトの数が 0 以外のアプリケーション-フレームワークは、完全にシャット ダウンではなく、ユーザーのビューからアプリケーションを非表示にします。 `AfxOleCanExitApp`関数は、アプリケーションを終了できるかどうかを示します。

呼び出す`AfxOleLockApp`できなくなるクライアント アプリケーションによってまだ使用されているときに破棄するには、そのオブジェクトのことが望ましい場合、OLE インターフェイスを公開する任意のオブジェクトからです。 呼び出すことも`AfxOleUnlockApp`を呼び出す任意のオブジェクトのデストラクターで`AfxOleLockApp`コンス トラクターでします。 既定では、 `COleDocument` (と派生クラス) を自動的にロックして、アプリケーションのロックを解除します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー**: afxdisp.h

##  <a name="afxoleunlockapp"></a>  AfxOleUnlockApp

デクリメント、アプリケーションのアクティブなオブジェクトのフレームワークの数。

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Remarks

参照してください`AfxOleLockApp`についてさらにします。

アクティブなオブジェクトの数がゼロになるとき`AfxOleOnReleaseAllObjects`が呼び出されます。

### <a name="example"></a>例

例をご覧ください[AfxOleLockApp](#afxolelockapp)します。

### <a name="requirements"></a>必要条件

**ヘッダー**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

指定したコントロールのクラス ファクトリをロックするは、コントロールに関連付けられている動的に作成されたデータはメモリに残りますようにします。

### <a name="syntax"></a>構文

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
コントロールの一意のクラス ID。

*lpszProgID*<br/>
コントロールの一意のプログラム ID。

### <a name="return-value"></a>戻り値

コントロールのクラス ファクトリが正常にロックされている場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

コントロールの表示これが大幅に短縮できます。 たとえば、1 回 ダイアログ ボックスのコントロールを作成してコントロールをロック`AfxOleLockControl`を作成し、もう一度ダイアログを表示するか破棄するたびに、強制終了する必要はありません。 場合は、ユーザーは、開くし、繰り返しダイアログ ボックスを閉じ、コントロールをロックできます著しくパフォーマンスが向上します。 コントロールを破棄する準備ができたら、呼び出す`AfxOleUnlockControl`します。

### <a name="example"></a>例

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="afxoleregisterserverclass"></a>  AfxOleRegisterServerClass

この関数では、OLE システム レジストリにサーバーを登録できます。

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
サーバーの OLE クラスの ID への参照

*lpszClassName*<br/>
サーバーのオブジェクトのクラス名を含む文字列へのポインター。

*lpszShortTypeName*<br/>
「グラフです」など、サーバーのオブジェクトの種類の短い名前を含む文字列へのポインター

*lpszLongTypeName*<br/>
サーバーのオブジェクトの種類、「Microsoft Excel 5.0 グラフです」などの長い名前を含む文字列へのポインター

*nAppType*<br/>
OLE アプリケーションの種類を指定する、OLE_APPTYPE 列挙から取得された値。 使用可能な値以下のとおりです。

- OAT_INPLACE_SERVER Server では、サーバー全体のユーザー インターフェイスがあります。

- OAT_SERVER サーバーは、埋め込みのみをサポートします。

- OAT_CONTAINER コンテナーは、埋め込みアイテムへのリンクをサポートします。

- OAT_DISPATCH_OBJECT `IDispatch`-対応するオブジェクト。

*rglpszRegister*<br/>
キーとキーの既存の値が見つからない場合、OLE システム レジストリに追加する値を表す文字列へのポインターの配列。

*rglpszOverwrite*<br/>
キーとレジストリに指定されたキーの既存の値が含まれている場合、OLE システム レジストリに追加する値を表す文字列へのポインターの配列。

### <a name="return-value"></a>戻り値

サーバー クラスが正常に登録されている場合は 0 以外それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

ほとんどのアプリケーションが使用できる`COleTemplateServer::Register`アプリケーションのドキュメントの種類を登録します。 アプリケーションのシステム レジストリ形式では、一般的なパターンに適合しない場合は使用できます`AfxOleRegisterServerClass`詳細に制御します。

レジストリ キーと値のセットで構成されます。 *RglpszRegister*と*rglpszOverwrite*引数が文字列へのポインターの配列、文字列から構成される、キーと値で区切られた、 **NULL**文字 ( `'\0'`). 置き換え可能パラメーターの文字シーケンスで可能な次の各文字列は *%1*を通じて *%5*します。

シンボルはように入力されます。

|シンボル|[値]|
|------------|-----------|
|%1|クラス ID を文字列として書式設定|
|%2|クラス名|
|%3|実行可能ファイルへのパス|
|%4|短い型名|
|%5|Long 型の名前|

### <a name="requirements"></a>必要条件

**ヘッダー**: afxdisp.h

##  <a name="afxoleseteditmenu"></a>  AfxOleSetEditMenu

ユーザー インターフェイスを実装、 *typename*オブジェクト コマンド。

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>パラメーター

*pClient*<br/>
クライアントの OLE アイテムへのポインター。

*pMenu*<br/>
更新メニュー オブジェクトへのポインター。

*iMenuItem*<br/>
更新するメニュー項目のインデックス。

*nIDVerbMin*<br/>
主動詞に対応するコマンド ID。

*nIDVerbMax*<br/>
最後の動詞に対応するコマンド ID。

*nIDConvert*<br/>
変換のメニュー項目の ID。

### <a name="remarks"></a>Remarks

サーバーがプライマリの動詞のみを認識しない場合、メニュー項目は次のようになります。"動詞*typename*オブジェクト"と*nIDVerbMin*コマンドが送信されるのは、ユーザーがコマンドを選択するとします。 かどうかには、いくつかの動詞をサーバーが認識し、メニュー項目が" *typename*オブジェクト"と、ユーザーがコマンドを選択すると、サブメニュー、すべての動詞の一覧が表示されます。 ユーザーが、サブメニューから 動詞*nIDVerbMin*最初の動詞を選択したかどうかは送信*nIDVerbMin* + 1 が 2 つ目の動詞は、選択した場合に送信されます。 既定の`COleDocument`実装は、この機能を自動的に処理します。

クライアントのアプリケーション リソースのスクリプトでは、次のステートメントをいる必要があります (します。RC) のファイル:

**#include \<afxolecl.rc>**

### <a name="requirements"></a>必要条件

**ヘッダー**: afxole.h

## <a name="afxoleunlockcontrol"></a> AfxOleUnlockControl

指定したコントロールのクラス ファクトリのロックを解除します。

### <a name="syntax"></a>構文

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>パラメーター

*clsid*<br/>
コントロールの一意のクラス ID。

*lpszProgID*<br/>
コントロールの一意のプログラム ID。

### <a name="return-value"></a>戻り値

コントロールのクラス ファクトリが正常にロックできなかった場合、0 以外の場合それ以外の場合 0 を返します。

### <a name="remarks"></a>Remarks

コントロールがロックされて`AfxOleLockControl`コントロールに関連付けられている動的に作成されたデータはメモリに残ります。 これが大幅に高速化できますコントロールの表示コントロール必要がありますいない作成および破棄するたびに表示されているためです。 コントロールを破棄する準備ができたら、呼び出す`AfxOleUnlockControl`します。

### <a name="example"></a>例

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](mfc-macros-and-globals.md)<br/>
