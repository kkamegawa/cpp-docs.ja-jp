---
title: CSnapInItemImpl クラス
ms.date: 11/04/2016
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: ff7336d393ca4680b4d448b9c775888063125b86
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893614"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl クラス

このクラスは、スナップインからノード オブジェクトを実装するためのメソッドを提供します。

> [!IMPORTANT]
>  このクラスとそのメンバーは、Windows ランタイムで実行するアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>パラメーター

*T*<br/>
派生したクラス、`CSnapInItemImpl`します。

*bIsExtension*<br/>
オブジェクトがスナップイン拡張機能である場合は TRUE。それ以外の場合は FALSE です。

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|コンテキスト メニューにメニュー項目を追加します。|
|[CSnapInItemImpl::Command](#command)|カスタム メニュー項目が選択されているときに、コンソールによって呼び出されます。|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|スナップインのプロパティ シートにページを追加します。|
|[CSnapInItemImpl::FillData](#filldata)|スナップイン オブジェクトで情報を指定したストリームにコピーします。|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|取得、`RESULTDATAITEM`スナップインの構造体。|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|結果ウィンドウで使用されたビューの種類を決定します。|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|取得、`SCOPEDATAITEM`スナップインの構造体。|
|[CSnapInItemImpl::Notify](#notify)|ユーザーが行ったアクションのスナップインに通知するコンソールによって呼び出されます。|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|スナップインでノードのプロパティ ページでサポートされているかどうかに呼び出されます。|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|スナップイン オブジェクトのメニューの挿入のフラグを変更します。|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|指定したツール バー ボタンの情報を設定します。|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|コンテキスト メニュー項目の状態を更新します。|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|指定したツール バー ボタンの状態を更新します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|スナップイン オブジェクトの名前。|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows`RESULTDATAITEM`構造で使用される、`CSnapInItemImpl`オブジェクト。|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows`SCOPEDATAITEM`構造で使用される、`CSnapInItemImpl`オブジェクト。|

## <a name="remarks"></a>Remarks

`CSnapInItemImpl` メニュー項目やツールバーを追加して、適切なハンドラー関数にスナップイン ノード用のコマンドの転送などのスナップインでノード オブジェクトの基本的な実装を提供します。 これらの機能は、複数のインターフェイスを使用して実装し、型をマップします。 既定の実装は、派生クラスの適切なインスタンスを確認し、適切なインスタンスにメッセージを転送し、ノードのオブジェクトに送信される通知を処理します。

## <a name="inheritance-hierarchy"></a>継承階層

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>必要条件

**ヘッダー:** atlsnap.h

##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems

このメソッドは、Win32 関数を実装します。 [IExtendContextMenu::AddMenuItems](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems)します。

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>パラメーター

*piCallback*<br/>
[in]ポインター、`IContextMenuCallback`コンテキスト メニューに項目を追加することができます。

*pInsertionAllowed*<br/>
[入力、出力]識別する Microsoft 管理コンソール MMC 定義メニュー項目の挿入ポイントことができます。 次のフラグの組み合わせを指定できます。

- コンテキスト メニューの上部にある CCM_INSERTIONALLOWED_TOP 項目を挿入することができます。

- 新規作成 サブメニューで CCM_INSERTIONALLOWED_NEW 項目を挿入できます。

- CCM_INSERTIONALLOWED_TASK 項目は、タスク サブメニューに挿入することができます。

- ツールバーの表示 メニューまたはサブメニューの表示、結果ウィンドウのコンテキスト メニューの CCM_INSERTIONALLOWED_VIEW 項目を挿入することができます。

*type*<br/>
[in]オブジェクトの種類を指定します。 次の値のいずれかのことができます。

- スコープ ウィンドウのコンテキストの CCT_SCOPE データ オブジェクト。

- 結果ウィンドウのコンテキストの CCT_RESULT データ オブジェクト。

- マネージャー スナップインでコンテキストの CCT_SNAPIN_MANAGER データ オブジェクト。

- CCT_UNINITIALIZED データ オブジェクトには、無効な型があります。

##  <a name="command"></a>  CSnapInItemImpl::Command

このメソッドは、Win32 関数を実装します。 [IExtendContextMenu::Command](/windows/desktop/api/mmc/nf-mmc-iextendcontextmenu-command)します。

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>パラメーター

*lCommandID*<br/>
[in]メニュー項目のコマンド識別子を指定します。

*type*<br/>
[in]オブジェクトの種類を指定します。 次の値のいずれかのことができます。

- スコープ ウィンドウのコンテキストの CCT_SCOPE データ オブジェクト。

- 結果ウィンドウのコンテキストの CCT_RESULT データ オブジェクト。

- マネージャー スナップインでコンテキストの CCT_SNAPIN_MANAGER データ オブジェクト。

- CCT_UNINITIALIZED データ オブジェクトには、無効な型があります。

##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages

このメソッドは、Win32 関数を実装します。 [IExtendPropertySheet::CreatePropertyPages](/windows/desktop/api/mmc/nn-mmc-iextendpropertysheet2)します。

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>パラメーター

*lpProvider*<br/>
[in]ポインター、`IPropertySheetCallback`インターフェイス。

*handle*<br/>
[in]適切なデータ クラスを MMCN_PROPERTY_CHANGE 通知メッセージをルーティングするためのハンドルを指定します。

*pUnk*<br/>
[in]ポインター、`IExtendPropertySheet`ノードに関するコンテキスト情報を格納しているオブジェクトのインターフェイス。

*type*<br/>
[in]オブジェクトの種類を指定します。 次の値のいずれかのことができます。

- スコープ ウィンドウのコンテキストの CCT_SCOPE データ オブジェクト。

- 結果ウィンドウのコンテキストの CCT_RESULT データ オブジェクト。

- マネージャー スナップインでコンテキストの CCT_SNAPIN_MANAGER データ オブジェクト。

- CCT_UNINITIALIZED データ オブジェクトには、無効な型があります。

##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl

`CSnapInItemImpl` オブジェクトを構築します。

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>  CSnapInItemImpl::FillData

この関数は、項目に関する情報を取得します。

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>パラメーター

*cf*<br/>
[in]クリップボードの形式 (テキスト、リッチ テキスト、または OLE 項目を含むリッチ テキスト)。

*pStream*<br/>
[in]オブジェクトのデータを格納しているストリームへのポインター。

### <a name="remarks"></a>Remarks

この関数を正しく実装するには、ストリームに正しい情報をコピー (*pStream*) で示されるクリップボード形式に応じて、 *cf*します。

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

スナップイン オブジェクトの結果ペインのビューの種類を取得するには、この関数を呼び出します。

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>パラメーター

*ppViewType*<br/>
[out]返されるビューの種類のアドレスへのポインター。

*pViewOptions*<br/>
[out]所有している、スナップインで指定されたオプションを使用して、コンソールを提供する MMC_VIEW_OPTIONS 列挙型へのポインター。 この値には、次のいずれかを指定できます。

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 で標準のリスト ビューの選択肢を表示しないようにコンソールに指示、**ビュー**メニュー。 結果ビュー ペインでのみ、独自のカスタム ビューを表示するスナップインを使用できます。 これは、この時点で定義されている唯一のオプション フラグです。

- MMC_VIEW_OPTIONS_NONE 0 が既定のビューのオプションを = です。

##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo

取得するには、この関数を呼び出す、`SCOPEDATAITEM`スナップインの構造体。

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>パラメーター

*pScopeDataItem*<br/>
[out]ポインター、`SCOPEDATAITEM`の構造、`CSnapInItemImpl`オブジェクト。

##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo

取得するには、この関数を呼び出す、`RESULTDATAITEM`スナップインの構造体。

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>パラメーター

*pResultDataItem*<br/>
[out]ポインター、`RESULTDATAITEM`の構造、`CSnapInItemImpl`オブジェクト。

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

ノード項目に対して表示文字列が含まれています。

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM`スナップイン データ オブジェクトの構造体。

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem

[RESULTDATAITEM](/windows/desktop/api/mmc/ns-mmc-resultdataitem)スナップイン データ オブジェクトの構造体。

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>  CSnapInItemImpl::Notify

スナップイン オブジェクトは、ユーザーが機能しているときに呼び出されます。

```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```

### <a name="parameters"></a>パラメーター

*event*<br/>
[in]ユーザーが実行する操作を識別します。 次の通知が考えられます。

- MMCN_ACTIVATE 送信ウィンドウがされているときにアクティブ化され、非アクティブ化します。

- 結果ウィンドウにイメージを追加する MMCN_ADD_IMAGES が送信されます。

- MMCN_BTN_CLICK は、ユーザーがツール バー ボタンのいずれかをクリックしたときに送信されます。

- ユーザーがリスト ビュー アイテムを上でマウス ボタンをクリックすると、MMCN_CLICK が送信されます。

- ユーザーがリスト ビュー アイテムを上でマウス ボタンをダブルクリックすると、MMCN_DBLCLICK が送信されます。

- オブジェクトにする必要があるスナップインに通知するために送信される MMCN_DELETE を削除します。

- フォルダーを展開または縮小する必要がある場合、MMCN_EXPAND が送信されます。

- MMCN_MINIMIZED 送信ウィンドウがされているときに最小化または最大化します。

- 変更する、スナップイン オブジェクトのビューは、スナップイン オブジェクトに通知する MMCN_PROPERTY_CHANGE が送信されます。

- MMCN_REMOVE_CHILDREN 送信、スナップインのサブツリー全体を指定したノードの下に追加と削除する必要があります。

- MMCN_RENAME は、名前の変更のクエリを最初に、名前の変更を行う 2 回目に送信されます。

- MMCN_SELECT は、スコープまたは結果ビュー ペイン内の項目が選択されているときに送信されます。

- スコープ項目が選択されているまたはを初めて選択解除されたときに、MMCN_SHOW が送信されます。

- MMCN_VIEW_CHANGE には、スナップインですべてのビューを更新、変更が発生した場合とが送信されます。

*arg*<br/>
[in]通知の種類によって異なります。

*param*<br/>
[in]通知の種類によって異なります。

*pComponentData*<br/>
[out]実装するオブジェクトへのポインター`IComponentData`します。 通知が転送しない場合、このパラメーターが NULL`IComponentData::Notify`します。

*pComponent*<br/>
[out]実装するオブジェクトへのポインター`IComponent`します。 通知が転送しない場合、このパラメーターが NULL`IComponent::Notify`します。

*type*<br/>
[in]オブジェクトの種類を指定します。 次の値のいずれかのことができます。

- スコープ ウィンドウのコンテキストの CCT_SCOPE データ オブジェクト。

- 結果ウィンドウのコンテキストの CCT_RESULT データ オブジェクト。

- マネージャー スナップインでコンテキストの CCT_SNAPIN_MANAGER データ オブジェクト。

- CCT_UNINITIALIZED データ オブジェクトには、無効な型があります。

##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor

スナップインでノードのプロパティ ページでサポートされているかどうかに呼び出されます。

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags

指定された、メニューの挿入フラグを変更するには、この関数を呼び出す*pInsertionAllowed*、スナップイン オブジェクト。

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>パラメーター

*bBeforeInsertion*<br/>
[in]コンテキスト メニューに項目を追加する前に、関数を呼び出す必要がある場合は 0 以外それ以外の場合 0 を返します。

*pInsertionAllowed*<br/>
[入力、出力]識別する Microsoft 管理コンソール MMC 定義メニュー項目の挿入ポイントことができます。 次のフラグの組み合わせを指定できます。

- コンテキスト メニューの上部にある CCM_INSERTIONALLOWED_TOP 項目を挿入することができます。

- 新規作成 サブメニューで CCM_INSERTIONALLOWED_NEW 項目を挿入できます。

- CCM_INSERTIONALLOWED_TASK 項目は、タスク サブメニューに挿入することができます。

- ツールバーの表示 メニューまたはサブメニューの表示、結果ウィンドウのコンテキスト メニューの CCM_INSERTIONALLOWED_VIEW 項目を挿入することができます。

### <a name="remarks"></a>Remarks

プライマリのスナップインを開発している場合は、サード パーティ製の拡張機能を追加するメニュー項目の種類を制限する方法として挿入フラグのいずれかをリセットできます。 たとえば、プライマリ スナップインでは、拡張機能が、独自の新規作成 メニュー項目を追加するを防ぐために CCM_INSERTIONALLOWED_NEW フラグをクリアできます。

のビットを設定しないで*pInsertionAllowed*最初をクリアします。 MMC の将来のバージョンが現在定義されていない bits が変わらないようにするために定義されていないビットを使用できます。

##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo

ツールバーを作成する前に、スナップイン オブジェクトのツール バー ボタンのスタイルを変更するには、この関数を呼び出します。

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
[in]設定するツール バー ボタンの ID。

*fsState*<br/>
[in]ボタンの状態フラグ。 次の 1 つ以上を指定できます。

- TBSTATE_CHECKED ボタンは、スタイルのスタイルを備えが押されました。

- ボタン、ボタンは、ユーザーの入力を受け入れます。 この状態がないボタンは、ユーザー入力が受け付けられません、淡色表示にします。

- TBSTATE_HIDDEN ボタンが表示されていないと、ユーザー入力を受け取ることはできません。

- TBSTATE_INDETERMINATE ボタンは淡色表示にします。

- ボタンが押された TBSTATE_PRESSED します。

- TBSTATE_WRAP A 改行では、ボタンに従います。 ボタンも、ボタンがあります。

*fsType*<br/>
[in]ボタンの状態フラグ。 次の 1 つ以上を指定できます。

- TBSTYLE_BUTTON は、標準的なプッシュ ボタンを作成します。

- ユーザーを毎回押された状態および not 押された状態の間を切り替えるボタンは TBSTYLE_CHECK を作成、それをクリックします。 押された状態にあるときに、別の背景色がボタンには、します。

- グループ内の別のボタンが押されるまで保持されるチェック ボタンが押された TBSTYLE_CHECKGROUP を作成します。

- グループ内の別のボタンが押されるまで保持されるボタンが押された TBSTYLE_GROUP を作成します。

- TBSTYLE_SEP は、ボタンのグループ間で小規模のギャップを提供する、区切り記号を作成します。 このスタイルがボタンでは、ユーザー入力を受信しません。

##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState

スナップイン オブジェクトのコンテキスト メニューに挿入される前に、メニュー項目を変更するには、この関数を呼び出します。

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
[in]設定するメニュー項目の ID。

*pBuf*<br/>
[in]更新するメニュー項目の文字列へのポインター。

*flags*<br/>
[in]新しい状態フラグを指定します。 次のフラグの組み合わせを指定できます。

- ならばでは、これは、コンテキスト メニューのサブメニューであることを指定します。 このサブメニューを使用するメニュー項目、挿入ポイント、およびさらに、サブメニューを追加することがあります、`lCommandID`としてその`IInsertionPointID`します。

- MF_BITMAP と MF_OWNERDRAW これらのフラグが許可されておらず、E_INVALIDARG の戻り値になります。

- MF_SEPARATOR では、水平方向の境界線を描画します。 のみ`IContextMenuProvider`は MF_SEPARATOR セットでのメニュー項目の追加を許可します。

- は、メニュー項目の横にあるチェック マークを配置します。

- MF_DISABLED を無効にしますが、メニュー項目選択できないため、フラグは灰色ではないこと。

- MF_ENABLED 選択できるように、灰色表示の状態から復元するメニュー項目を実現します。

- MF_GRAYED には、選択できないように灰色表示にするメニュー項目が無効にします。

- メニュー バーのフラグ、MF_MENUBREAK と同じ MF_MENUBARBREAK 関数です。 ドロップダウン メニューのサブメニュー、またはショートカット メニューの新しい列は、垂直線で、古い列から区切られます。

- MF_MENUBREAK (メニュー バー) の新しい行に項目を配置または列を分離することがなく新しい列 (のドロップダウン メニューのサブメニュー、またはショートカット メニュー)。

- (既定値) の項目の横にチェック マークは配置 MF_UNCHECKED されません。

次のフラグのグループを一緒に使用できません。

- MF_DISABLED、MF_ENABLED、および MF_GRAYED です。

- MF_MENUBARBREAK MF_MENUBREAK.

- MF_UNCHECKED.

##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton

表示する前に、スナップイン オブジェクトのツールバーのボタンを変更するには、この関数を呼び出します。

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
更新するツール バー ボタンのボタンの ID を指定します。

*fsState*<br/>
ツール バー ボタンの状態を指定します。 この状態を設定する場合は、TRUE を返します。 次のフラグの組み合わせを指定できます。

- 有効、ボタンは、ユーザー入力を受け入れます。 この状態がないボタンは、ユーザー入力が受け付けられません、淡色表示にします。

- ボタンのスタイルがチェックされているとが押されたチェックされます。

- 非表示ボタンは表示されず、ユーザー入力を受け取ることはできません。

- 不確定なボタンは淡色表示にします。

- ボタンが押された BUTTONPRESSED します。

## <a name="see-also"></a>関連項目

[クラスの概要](../../atl/atl-class-overview.md)
