---
title: COleDocObjectItem クラス
ms.date: 11/04/2016
f1_keywords:
- COleDocObjectItem
- AFXOLE/COleDocObjectItem
- AFXOLE/COleDocObjectItem::COleDocObjectItem
- AFXOLE/COleDocObjectItem::DoDefaultPrinting
- AFXOLE/COleDocObjectItem::ExecCommand
- AFXOLE/COleDocObjectItem::GetActiveView
- AFXOLE/COleDocObjectItem::GetPageCount
- AFXOLE/COleDocObjectItem::OnPreparePrinting
- AFXOLE/COleDocObjectItem::OnPrint
- AFXOLE/COleDocObjectItem::QueryCommand
- AFXOLE/COleDocObjectItem::Release
helpviewer_keywords:
- COleDocObjectItem [MFC], COleDocObjectItem
- COleDocObjectItem [MFC], DoDefaultPrinting
- COleDocObjectItem [MFC], ExecCommand
- COleDocObjectItem [MFC], GetActiveView
- COleDocObjectItem [MFC], GetPageCount
- COleDocObjectItem [MFC], OnPreparePrinting
- COleDocObjectItem [MFC], OnPrint
- COleDocObjectItem [MFC], QueryCommand
- COleDocObjectItem [MFC], Release
ms.assetid: d150d306-8fd3-4831-b06d-afbe71d8fc9b
ms.openlocfilehash: c6e00bf42cf20b46c949c218efe1820cc7ce0f9b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504006"
---
# <a name="coledocobjectitem-class"></a>COleDocObjectItem クラス

Active ドキュメント コンテインメントを実装します。

## <a name="syntax"></a>構文

```
class COleDocObjectItem : public COleClientItem
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[COleDocObjectItem:: COleDocObjectItem](#coledocobjectitem)|項目を`COleDocObject`構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[COleDocObjectItem::D oDefaultPrinting](#dodefaultprinting)|既定のプリンター設定を使用して、コンテナーアプリケーションのドキュメントを印刷します。|
|[COleDocObjectItem:: ExecCommand](#execcommand)|ユーザーによって指定されたコマンドを実行します。|
|[COleDocObjectItem:: GetActiveView](#getactiveview)|ドキュメントのアクティブなビューを取得します。|
|[COleDocObjectItem:: GetPageCount](#getpagecount)|コンテナーアプリケーションのドキュメント内のページ数を取得します。|
|[COleDocObjectItem:: OnPreparePrinting](#onprepareprinting)|コンテナーアプリケーションのドキュメントの印刷を準備します。|
|[COleDocObjectItem:: OnPrint](#onprint)|コンテナーアプリケーションのドキュメントを印刷します。|
|[COleDocObjectItem::QueryCommand](#querycommand)|ユーザー インターフェイスのイベントによって生成された 1 つ以上のコマンドの状態を調べるためにクエリを実行します。|
|[COleDocObjectItem::Release](#release)|OLE リンクアイテムへの接続を解放し、開いている場合は閉じます。 は、クライアント項目を破棄しません。|

## <a name="remarks"></a>Remarks

MFC では、アクティブなドキュメントは通常の埋め込み先編集可能な埋め込みと同様に処理されますが、次の点が異なります。

- 派生`COleDocument`クラスは、現在埋め込まれている項目のリストを保持しますが、これら`COleDocObjectItem`の項目は派生した項目である場合もあります。

- アクティブなドキュメントがアクティブな場合は、ビューのクライアント領域全体がアクティブな状態で表示されます。

- アクティブなドキュメントコンテナーには、 **[ヘルプ]** メニューのフルコントロールがあります。

- **[ヘルプ]** メニューには、アクティブなドキュメントコンテナーとサーバーの両方のメニュー項目が表示されます。

アクティブなドキュメントコンテナーは **[ヘルプ]** メニューを所有しているので、サーバーの**ヘルプ**メニューメッセージをサーバーに転送する役割があります。 この統合は、に`COleDocObjectItem`よって処理されます。

メニューのマージとアクティブドキュメントのアクティブ化の詳細については、「 [Active ドキュメントコンテインメント](../../mfc/active-document-containment.md)の概要」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CDocItem](../../mfc/reference/cdocitem-class.md)

[COleClientItem](../../mfc/reference/coleclientitem-class.md)

`COleDocObjectItem`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxole

##  <a name="coledocobjectitem"></a>COleDocObjectItem:: COleDocObjectItem

オブジェクトを初期化するには、 `COleDocObjectItem`このメンバー関数を呼び出します。

```
COleDocObjectItem(COleDocument* pContainerDoc = NULL);
```

### <a name="parameters"></a>パラメーター

*pContainerDoc*<br/>
アクティブなドキュメントコンテナー `COleDocument`として機能するオブジェクトへのポインター。 IMPLEMENT_SERIALIZE を有効にするには、このパラメーターに NULL を指定する必要があります。 通常、OLE 項目は NULL 以外のドキュメントポインターを使用して構築されます。

##  <a name="dodefaultprinting"></a>COleDocObjectItem::D oDefaultPrinting

フレームワークによって、既定の設定を使用してドキュメントに対して呼び出されます。

```
static HRESULT DoDefaultPrinting(
    CView* pCaller,
    CPrintInfo* pInfo);
```

### <a name="parameters"></a>パラメーター

*pCaller*<br/>
Print コマンドを送信する[CView](../../mfc/reference/cview-class.md)オブジェクトへのポインター。

*pInfo*<br/>
印刷するジョブを記述する[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)オブジェクトへのポインター。

##  <a name="execcommand"></a>COleDocObjectItem:: ExecCommand

このメンバー関数を呼び出して、ユーザーによって指定されたコマンドを実行します。

```
HRESULT ExecCommand(
    DWORD nCmdID,
    DWORD nCmdExecOpt = OLECMDEXECOPT_DONTPROMPTUSER,
    const GUID* pguidCmdGroup = NULL);
```

### <a name="parameters"></a>パラメーター

*nCmdID*<br/>
実行するコマンドの識別子。 *Pguidcmdgroup*によって識別されるグループに存在する必要があります。

*nCmdExecOpt*<br/>
コマンド実行オプションを指定します。 既定では、ユーザーにプロンプトを表示せずにコマンドを実行するように設定します。 値の一覧については、「 [OLECMDEXECOPT](/windows/win32/api/docobj/ne-docobj-olecmdexecopt) 」を参照してください。

*pguidCmdGroup*<br/>
コマンドグループの一意識別子。 既定では、NULL は標準のグループを指定します。 *Ncmdid*で渡されるコマンドは、グループに属している必要があります。

### <a name="return-value"></a>戻り値

成功した場合は S_OK を返します。それ以外の場合は、次のいずれかのエラーコードが返されます。

|[値]|説明|
|-----------|-----------------|
|E_UNEXPECTED|予期しないエラーが発生しました。|
|E_FAIL|エラーが発生しました。|
|E_NOTIMPL|MFC 自体がコマンドの変換とディスパッチを試みる必要があることを示します。|
|OLECMDERR_E_UNKNOWNGROUP|*Pguidcmdgroup*は NULL 以外ですが、認識されているコマンドグループを指定していません。|
|OLECMDERR_E_NOTSUPPORTED|*Ncmdid*は、グループ pgroup の有効なコマンドとして認識されません。|
|OLECMDERR_DISABLED|*Ncmdid*で識別されたコマンドは無効になっているため、実行できません。|
|OLECMDERR_NOHELP|呼び出し元は*Ncmdid*で識別されたコマンドに関するヘルプを要求しましたが、ヘルプはありません。|
|OLECMDERR_CANCELLED|ユーザーが実行を取り消しました。|

### <a name="remarks"></a>Remarks

*Pguidcmdgroup*と*ncmdid*パラメーターを一緒に実行すると、呼び出すコマンドが一意に識別されます。 *Ncmdexecopt*パラメーターは、実行する正確なアクションを指定します。

##  <a name="getactiveview"></a>COleDocObjectItem:: GetActiveView

現在アクティブなビューの`IOleDocumentView`インターフェイスへのポインターを取得するには、このメンバー関数を呼び出します。

```
LPOLEDOCUMENTVIEW GetActiveView() const;
```

### <a name="return-value"></a>戻り値

現在アクティブなビューの[IOleDocumentView](/windows/win32/api/docobj/nn-docobj-ioledocumentview)インターフェイスへのポインター。 現在のビューがない場合は、NULL を返します。

### <a name="remarks"></a>Remarks

返さ`IOleDocumentView`れたポインターの参照カウントは、この関数によって返される前にインクリメントされません。

##  <a name="getpagecount"></a>COleDocObjectItem:: GetPageCount

ドキュメント内のページ数を取得するには、このメンバー関数を呼び出します。

```
BOOL GetPageCount(
    LPLONG pnFirstPage,
    LPLONG pcPages);
```

### <a name="parameters"></a>パラメーター

*[pnFirstPage]*<br/>
ドキュメントの最初のページの番号へのポインター。 NULL にすることができます。これは、呼び出し元がこの番号を必要としないことを示します。

*pcPages*<br/>
ドキュメント内のページの合計数へのポインター。 NULL にすることができます。これは、呼び出し元がこの番号を必要としないことを示します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="onprepareprinting"></a>COleDocObjectItem:: OnPreparePrinting

このメンバー関数は、印刷用のドキュメントを準備するためにフレームワークによって呼び出されます。

```
static BOOL OnPreparePrinting(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>パラメーター

*pCaller*<br/>
Print コマンドを送信する[CView](../../mfc/reference/cview-class.md)オブジェクトへのポインター。

*pInfo*<br/>
印刷するジョブを記述する[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)オブジェクトへのポインター。

*bPrintAll*<br/>
ドキュメント全体を印刷するかどうかを指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="onprint"></a>  COleDocObjectItem::OnPrint

このメンバー関数は、ドキュメントを印刷するためにフレームワークによって呼び出されます。

```
static void OnPrint(
    CView* pCaller,
    CPrintInfo* pInfo,
    BOOL bPrintAll = TRUE);
```

### <a name="parameters"></a>パラメーター

*pCaller*<br/>
Print コマンドを送信する CView オブジェクトへのポインター。

*pInfo*<br/>
印刷するジョブを記述する[CPrintInfo](../../mfc/reference/cprintinfo-structure.md)オブジェクトへのポインター。

*bPrintAll*<br/>
ドキュメント全体を印刷するかどうかを指定します。

##  <a name="querycommand"></a>  COleDocObjectItem::QueryCommand

ユーザー インターフェイスのイベントによって生成された 1 つ以上のコマンドの状態を調べるためにクエリを実行します。

```
HRESULT QueryCommand(
    ULONG nCmdID,
    DWORD* pdwStatus,
    OLECMDTEXT* pCmdText =NULL,
    const GUID* pguidCmdGroup =NULL);
```

### <a name="parameters"></a>パラメーター

*nCmdID*<br/>
クエリ対象のコマンドの識別子。

*pdwStatus*<br/>
クエリの結果として返されるフラグへのポインター。 使用可能な値の一覧については、「 [OLECMDF](/windows/win32/api/docobj/ne-docobj-olecmdf)」を参照してください。

*pCmdText*<br/>
1つのコマンドの名前と状態の情報を返す[OLECMDTEXT](/windows/win32/api/docobj/ns-docobj-olecmdtext)構造体へのポインター。 NULL にすると、呼び出し元がこの情報を必要としないことを示すことができます。

*pguidCmdGroup*<br/>
コマンドグループの一意識別子。標準のグループを指定する場合は NULL を指定できます。

### <a name="return-value"></a>戻り値

戻り値の完全な一覧については、Windows SDK の「 [IOleCommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus) 」を参照してください。

### <a name="remarks"></a>Remarks

このメンバー関数は、Windows SDK で説明されているように、 [IOleCommandTarget:: QueryStatus](/windows/win32/api/docobj/nf-docobj-iolecommandtarget-querystatus)メソッドの機能をエミュレートします。

##  <a name="release"></a>  COleDocObjectItem::Release

OLE リンクアイテムへの接続を解放し、開いている場合は閉じます。 は、クライアント項目を破棄しません。

```
virtual void Release(OLECLOSE dwCloseOption = OLECLOSE_NOSAVE);
```

### <a name="parameters"></a>パラメーター

*dwCloseOption*<br/>
OLE 項目が読み込まれた状態に戻ったときに、どのような状況で OLE 項目を保存するかを指定するフラグ。 使用可能な値の一覧については、「 [COleClientItem:: Close](../../mfc/reference/coleclientitem-class.md#close)」を参照してください。

### <a name="remarks"></a>Remarks

は、クライアント項目を破棄しません。

## <a name="see-also"></a>関連項目

[MFC サンプル MFCBIND](../../overview/visual-cpp-samples.md)<br/>
[COleClientItem クラス](../../mfc/reference/coleclientitem-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[COleClientItem クラス](../../mfc/reference/coleclientitem-class.md)<br/>
[CDocObjectServerItem クラス](../../mfc/reference/cdocobjectserveritem-class.md)
