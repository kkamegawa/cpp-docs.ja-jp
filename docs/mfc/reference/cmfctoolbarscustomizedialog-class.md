---
title: CMFCToolBarsCustomizeDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillAllCommandsList
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesComboBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::FillCategoriesListBox
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCommandName
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetCountInCategory
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::GetFlags
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::OnInitDialog
- AFXTOOLBARSCUSTOMIZEDIALOG/CMFCToolBarsCustomizeDialog::PostNcDestroy
helpviewer_keywords:
- CMFCToolBarsCustomizeDialog [MFC], CMFCToolBarsCustomizeDialog
- CMFCToolBarsCustomizeDialog [MFC], FillAllCommandsList
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesComboBox
- CMFCToolBarsCustomizeDialog [MFC], FillCategoriesListBox
- CMFCToolBarsCustomizeDialog [MFC], GetCommandName
- CMFCToolBarsCustomizeDialog [MFC], GetCountInCategory
- CMFCToolBarsCustomizeDialog [MFC], GetFlags
- CMFCToolBarsCustomizeDialog [MFC], OnInitDialog
- CMFCToolBarsCustomizeDialog [MFC], PostNcDestroy
ms.assetid: 78e2cddd-4f13-4097-afc3-1ad646a113f1
ms.openlocfilehash: 4e6bdef10d5747abd344750c888cf6726c47d99e
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929931"
---
# <a name="cmfctoolbarscustomizedialog-class"></a>CMFCToolBarsCustomizeDialog クラス

モードレスタブダイアログボックス ( [CPropertySheet クラス](../../mfc/reference/cpropertysheet-class.md))。ユーザーは、アプリケーションのツールバー、メニュー、キーボードショートカット、ユーザー定義ツール、および視覚スタイルをカスタマイズできます。 通常、このダイアログ ボックスを表示するには、 **[ツール]** メニューの **[ユーザー設定]** をクリックします。

**[ユーザー設定]** ダイアログボックスには、次の6つのタブがあります。**コマンド**、ツール**バー**、**ツール**、**キーボード**、**メニュー**、および**オプション**。

## <a name="syntax"></a>構文

```
class CMFCToolBarsCustomizeDialog : public CPropertySheet
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: CMFCToolBarsCustomizeDialog](#cmfctoolbarscustomizedialog)|`CMFCToolBarsCustomizeDialog` オブジェクトを構築します。|
|`CMFCToolBarsCustomizeDialog::~CMFCToolBarsCustomizeDialog`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: AddButton](#addbutton)|**[コマンド]** ページのコマンド一覧にツールバーボタンを挿入します。|
|[CMFCToolBarsCustomizeDialog:: AddMenu](#addmenu)|リソースからメニューを読み込み、 [Cmfctoolbarscustomizedialog:: AddMenuCommands](#addmenucommands)を呼び出して、**コマンド**ページのコマンド一覧にそのメニューを追加します。|
|[CMFCToolBarsCustomizeDialog:: AddMenuCommands](#addmenucommands)|リソースからメニューを読み込み、 [Cmfctoolbarscustomizedialog:: AddMenuCommands](#addmenucommands)を呼び出して、**コマンド**ページのコマンド一覧にそのメニューを追加します。|
|[CMFCToolBarsCustomizeDialog:: AddToolBar](#addtoolbar)|リソースからツールバーを読み込みます。 次に、メニューの各コマンドについて、 [Cmfctoolbarscustomizedialog:: AddButton](#addbutton)メソッドを呼び出して、指定されたカテゴリの下**にあるコマンドページの**コマンドの一覧にボタンを挿入します。|
|[CMFCToolBarsCustomizeDialog:: Create](#create)|**[カスタマイズ]** ダイアログボックスを表示します。|
|`CMFCToolBarsCustomizeDialog::EnableTools`|将来使用するために予約されています。|
|[CMFCToolBarsCustomizeDialog:: Enableuserdefinedtoolbarツールバー](#enableuserdefinedtoolbars)|**[ユーザー設定]** ダイアログボックスを使用して、新しいツールバーの作成を有効または無効にします。|
|[CMFCToolBarsCustomizeDialog::FillAllCommandsList](#fillallcommandslist)|指定さ`CListBox`れたオブジェクトに、 **[すべてのコマンド]** カテゴリのコマンドを設定します。|
|[CMFCToolBarsCustomizeDialog:: Fillカテゴリ Combobox](#fillcategoriescombobox)|指定さ`CComboBox`れたオブジェクトに、[カスタマイズ] ダイアログボックスの各コマンドカテゴリの名前を**設定**します。|
|[CMFCToolBarsCustomizeDialog:: Fillカテゴリリストボックス](#fillcategorieslistbox)|指定さ`CListBox`れたオブジェクトに、[カスタマイズ] ダイアログボックスの各コマンドカテゴリの名前を**設定**します。|
|[CMFCToolBarsCustomizeDialog::GetCommandName](#getcommandname)|指定したコマンド ID に関連付けられている名前を取得します。|
|[CMFCToolBarsCustomizeDialog:: GetCountInCategory](#getcountincategory)|指定されたリストに含まれる、特定のテキストラベルを持つ項目の数を取得します。|
|[CMFCToolBarsCustomizeDialog:: GetFlags](#getflags)|ダイアログボックスの動作に影響を与えるフラグのセットを取得します。|
|`CMFCToolBarsCustomizeDialog::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCToolBarsCustomizeDialog:: OnEditToolbarMenuImage](#onedittoolbarmenuimage)|ユーザーがツールバーボタンまたはメニュー項目アイコンをカスタマイズできるように、イメージエディターを起動します。|
|[CMFCToolBarsCustomizeDialog::OnInitDialog](#oninitdialog)|をオーバーライドして、プロパティシートの初期化を強化します。 ( [CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)をオーバーライドします。)|
|[CMFCToolBarsCustomizeDialog::P ostNcDestroy](#postncdestroy)|ウィンドウが破棄された後にフレームワークによって呼び出されます。 ( `CPropertySheet::PostNcDestroy`をオーバーライドします)。|
|[CMFCToolBarsCustomizeDialog:: RemoveButton](#removebutton)|指定したカテゴリまたはすべてのカテゴリから、指定したコマンド ID を持つボタンを削除します。|
|[CMFCToolBarsCustomizeDialog:: RenameCategory](#renamecategory)|**[コマンド]** タブのカテゴリのリストボックスで、カテゴリの名前を変更します。|
|[CMFCToolBarsCustomizeDialog:: ReplaceButton](#replacebutton)|**[コマンド]** タブのコマンド一覧のボタンを新しいツールバーボタンオブジェクトに置き換えます。|
|[CMFCToolBarsCustomizeDialog:: SetUserCategory](#setusercategory)|**[コマンド]** タブに表示されるカテゴリの一覧にカテゴリを追加します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolBarsCustomizeDialog:: CheckToolsValidity 有効性](#checktoolsvalidity)|ユーザー定義ツールのリストが有効かどうかを判断するために、フレームワークによって呼び出されます。|
|[CMFCToolBarsCustomizeDialog:: OnAfterChangeTool](#onafterchangetool)|ユーザー定義ツールのプロパティが変更されたときにフレームワークによって呼び出されます。|
|[CMFCToolBarsCustomizeDialog:: On割り当てキー](#onassignkey)|指定したショートカットキーをアクションに割り当てることができるかどうかを判断します。|
|[CMFCToolBarsCustomizeDialog:: OnBeforeChangeTool](#onbeforechangetool)|ユーザー定義ツールを変更できるかどうかを判断します。|
|[CMFCToolBarsCustomizeDialog:: OnInitToolsPage](#oninittoolspage)|ユーザーが **[ツール]** タブを選択したときにフレームワークによって呼び出されます。|

## <a name="remarks"></a>Remarks

**[ユーザー設定]** ダイアログボックスを表示する`CMFCToolBarsCustomizeDialog`には、オブジェクトを作成し、 [cmfctoolbarscustomizedialog:: create](#create)メソッドを呼び出します。

**[カスタマイズ]** ダイアログボックスがアクティブになっている間、アプリケーションは、ユーザーをカスタマイズタスクに限定する特別なモードで動作します。

## <a name="example"></a>例

`CMFCToolBarsCustomizeDialog` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例は、 **[コマンド]** ページのコマンドのリストボックスでツールバーボタンを置き換える方法を示しています。また、 **[ユーザー設定]** ダイアログボックスを使用して新しいツールバーの作成を有効にし、 **[カスタマイズ]** ダイアログボックスを表示します。 このコードスニペットは、 [IE デモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_IEDemo#4](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

`CMFCToolBarsCustomizeDialog`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxToolBarsCustomizeDialog

##  <a name="addbutton"></a>  CMFCToolBarsCustomizeDialog::AddButton

**コマンド**ページのコマンドの一覧にツールバーボタンを挿入します。

```
void AddButton(
    UINT uiCategoryId,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);

void AddButton(
    LPCTSTR lpszCategory,
    const CMFCToolBarButton& button,
    int iInsertBefore=-1);
```

### <a name="parameters"></a>パラメーター

*uiCategoryId*<br/>
からボタンを挿入するカテゴリ ID を指定します。

*;*<br/>
から挿入するボタンを指定します。

*iInsertBefore*<br/>
からボタンが挿入される前のツールバーボタンの0から始まるインデックスを指定します。

*lpszCategory*<br/>
からボタンを挿入するカテゴリ文字列を指定します。

### <a name="remarks"></a>Remarks

メソッド`AddButton`は、標準のコマンド id (ID_FILE_MRU_FILE1 など) を持つボタン、許可されていないコマンド ( [cmfctoolbar:: iscommandpermitted](../../mfc/reference/cmfctoolbar-class.md#iscommandpermitted))、およびダミーボタンを無視します。

このメソッドは、ボタンのランタイムクラスを使用し`button`て、(通常は[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)) と同じ型の新しいオブジェクトを作成します。 次に、 [CMFCToolBarButton:: CopyFrom](../../mfc/reference/cmfctoolbarbutton-class.md#copyfrom)を呼び出して、ボタンのデータメンバーをコピーし、指定したカテゴリにコピーを挿入します。

新しいボタンが挿入されると、 `OnAddToCustomizePage`通知を受信します。

が`iInsertBefore` -1 の場合、カテゴリの一覧にボタンが追加されます。それ以外の場合は、指定したインデックスを持つ項目の前に挿入されます。

### <a name="example"></a>例

クラスのメソッド`AddButton`を使用する方法を次の例に示します。 `CMFCToolBarsCustomizeDialog` このコードスニペットは、[スライダーサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_Slider#1](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_2.cpp)]

##  <a name="addmenu"></a>CMFCToolBarsCustomizeDialog:: AddMenu

リソースからメニューを読み込み、 [Cmfctoolbarscustomizedialog:: AddMenuCommands](#addmenucommands)を呼び出して、**コマンド**ページのコマンド一覧にそのメニューを追加します。

```
BOOL AddMenu(UINT uiMenuResId);
```

### <a name="parameters"></a>パラメーター

*uiMenuResId*<br/>
から読み込むメニューのリソース ID を指定します。

### <a name="return-value"></a>戻り値

メニューが正常に追加された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

の呼び出し`AddMenuCommands`では、 *bpopup*は FALSE です。 そのため、このメソッドは、サブメニューを含むメニュー項目をコマンドの一覧に追加しません。 このメソッドは、サブメニューのメニュー項目をコマンドの一覧に追加します。

##  <a name="addmenucommands"></a>CMFCToolBarsCustomizeDialog:: AddMenuCommands

**コマンド**ページのコマンド一覧に項目を追加して、指定したメニュー内のすべての項目を表示します。

```
void AddMenuCommands(
    const CMenu* pMenu,
    BOOL bPopup,
    LPCTSTR lpszCategory=NULL,
    LPCTSTR lpszMenuPath=NULL);
```

### <a name="parameters"></a>パラメーター

*pMenu*<br/>
から追加する CMenu オブジェクトへのポインター。

*bPopup*<br/>
からコマンドの一覧にポップアップメニュー項目を挿入するかどうかを指定します。

*lpszCategory*<br/>
からメニューを挿入するカテゴリの名前。

*lpszMenuPath*<br/>
から **[すべてのカテゴリ]** の一覧にコマンドが表示されたときに名前に追加されるプレフィックス。

### <a name="remarks"></a>Remarks

メソッド`AddMenuCommands`は、 *pmenu*のすべてのメニュー項目をループします。 サブメニューが含まれていない各メニュー項目に対して、このメソッドは[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)オブジェクトを作成し、 [Cmfctoolbarscustomizedialog:: addbutton](#addbutton)メソッドを呼び出して、メニュー項目をツールバーボタンとして、**のコマンド一覧に追加します。コマンド**ページ。 このプロセスでは、区切り記号は無視されます。

*Bpopup*が TRUE の場合、サブメニューを含む各メニュー項目に対して、このメソッドは[Cmfctoolbarmenubutton クラス](../../mfc/reference/cmfctoolbarmenubutton-class.md)オブジェクトを作成し、を呼び出し`AddButton`てコマンドのリストに挿入します。 それ以外の場合、サブメニューを含むメニュー項目は、コマンドの一覧に表示されません。 どちらの場合も、 `AddMenuCommands`でメニュー項目がサブメニューによって検出されたときに、それ自体を再帰的に呼び出し、 *pmenu*パラメーターとしてサブメニューへのポインターを渡し、サブメニューのラベルを*lpszMenuPath*に追加します。

##  <a name="addtoolbar"></a>CMFCToolBarsCustomizeDialog:: AddToolBar

リソースからツールバーを読み込みます。 次に、メニューの各コマンドについて、 [Cmfctoolbarscustomizedialog:: AddButton](#addbutton)メソッドを呼び出して、指定されたカテゴリの下**にあるコマンドページの**コマンドの一覧にボタンを挿入します。

```
BOOL AddToolBar(
    UINT uiCategoryId,
    UINT uiToolbarResId);

BOOL AddToolBar(
    LPCTSTR lpszCategory,
    UINT uiToolbarResId);
```

### <a name="parameters"></a>パラメーター

*uiCategoryId*<br/>
からツールバーを追加するカテゴリのリソース ID を指定します。

*uiToolbarResId*<br/>
からコマンドの一覧にコマンドが挿入されるツールバーのリソース ID を指定します。

*lpszCategory*<br/>
からツールバーを追加するカテゴリの名前を指定します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="example"></a>例

`CMFCToolBarsCustomizeDialog`クラスの`AddToolBar`メソッドを使用する方法を次の例に示します。 このコード スニペットは、 [Word パッド サンプル](../../overview/visual-cpp-samples.md)の一部です。

[!code-cpp[NVC_MFC_WordPad#11](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_3.cpp)]

### <a name="remarks"></a>Remarks

各コマンドを表すために使用されるコントロールは、 [CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)オブジェクトです。 ツールバーを追加した後、 [Cmfctoolbarscustomizedialog:: ReplaceButton](#replacebutton)を呼び出すことによって、ボタンを派生型のコントロールに置き換えることができます。

##  <a name="checktoolsvalidity"></a>CMFCToolBarsCustomizeDialog:: CheckToolsValidity 有効性

ユーザーツールの一覧が有効かどうかを確認します。

```
virtual BOOL CheckToolsValidity(const CObList& lstTools);
```

### <a name="parameters"></a>パラメーター

*lstTools*<br/>
から確認するユーザー定義ツールの一覧。

### <a name="return-value"></a>戻り値

ユーザー定義ツールの一覧が有効な場合は TRUE を返します。それ以外の場合は FALSE。 既定の実装では、常に TRUE が返されます。

### <a name="remarks"></a>Remarks

フレームワークは、このメソッドを呼び出して、 [Cmfctoolbarscustomizedialog:: CheckToolsValidity](#checktoolsvalidity)によって返されたユーザー定義ツールを表すオブジェクトの有効性を検証します。

ユーザーがダイアログボックスを閉じる前に`CMFCToolBarsCustomizeDialog`ユーザーツールを検証する場合は、から派生したクラスのメソッドをオーバーライドします。`CheckToolsValidity` ユーザーがダイアログボックスの右上隅にある **[閉じる]** ボタンをクリックしたとき、またはダイアログボックスの右下隅にある **[閉じる]** ボタンをクリックしたときに、このメソッドが FALSE を返す場合、ダイアログボックスには、 **[ツール]** タブが表示されます。右山. ユーザーがタブをクリックして **[ツール]** タブから移動したときに、このメソッドが FALSE を返す場合、ナビゲーションは実行されません。 検証が失敗する原因となった問題をユーザーに通知するために、適切なメッセージボックスを表示する必要があります。

##  <a name="cmfctoolbarscustomizedialog"></a>  CMFCToolBarsCustomizeDialog::CMFCToolBarsCustomizeDialog

`CMFCToolBarsCustomizeDialog` オブジェクトを構築します。

```
CMFCToolBarsCustomizeDialog(
    CFrameWnd* pWndParentFrame,
    BOOL bAutoSetFromMenus = FALSE,
    UINT uiFlags = (AFX_CUSTOMIZE_MENU_SHADOWS | AFX_CUSTOMIZE_TEXT_LABELS | AFX_CUSTOMIZE_MENU_ANIMATIONS | AFX_CUSTOMIZE_NOHELP),
    CList <CRuntimeClass*, CRuntimeClass*>* p listCustomPages = NULL);
```

### <a name="parameters"></a>パラメーター

*pWndParentFrame*<br/>
から親フレームへのポインター。 このパラメーターを NULL にすることはできません。

*bAutoSetFromMenus*<br/>
からメニューコマンドを**すべてのメニューからコマンドページの**コマンド一覧に追加するかどうかを指定するブール値です。 このパラメーターが TRUE の場合、メニューコマンドが追加されます。 そうしないと、メニューコマンドは追加されません。

*uiFlags*<br/>
からダイアログボックスの動作に影響を与えるフラグの組み合わせ。 このパラメーターには、次の値を1つ以上指定できます。

- AFX_CUSTOMIZE_MENU_SHADOWS

- AFX_CUSTOMIZE_TEXT_LABELS

- AFX_CUSTOMIZE_MENU_ANIMATIONS

- AFX_CUSTOMIZE_NOHELP

- AFX_CUSTOMIZE_CONTEXT_HELP

- AFX_CUSTOMIZE_NOTOOLS

- AFX_CUSTOMIZE_MENUAMPERS

- AFX_CUSTOMIZE_NO_LARGE_ICONS

*plistCustomPages*<br/>
から追加のカスタムページを指定`CRuntimeClass`するオブジェクトのリストへのポインター。

### <a name="remarks"></a>Remarks

*PlistCustomPages*パラメーターは、追加のカスタムページ`CRuntimeClass`を指定するオブジェクトの一覧を参照します。 コンストラクターは、 [CRuntimeClass:: CreateObject](../../mfc/reference/cruntimeclass-structure.md#createobject)メソッドを使用して、ダイアログボックスにページを追加します。 **[カスタマイズ]** ダイアログボックスにページを追加する例については、custompages サンプルを参照してください。

*Uiflags*パラメーターで渡すことができる値の詳細については、「 [Cmfctoolbarscustomizedialog:: getflags](#getflags)」を参照してください。

### <a name="example"></a>例

`CMFCToolBarsCustomizeDialog`クラスのオブジェクトを構築する方法を次の例に示します。 このコードスニペットは、[カスタムページサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_CustomPages#3](../../mfc/reference/codesnippet/cpp/cmfctoolbarscustomizedialog-class_4.cpp)]

##  <a name="create"></a>CMFCToolBarsCustomizeDialog:: Create

**[カスタマイズ]** ダイアログボックスを表示します。

```
virtual BOOL Create();
```

### <a name="return-value"></a>戻り値

カスタマイズプロパティシートが正常に作成された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

クラスを`Create`完全に初期化した後にのみ、メソッドを呼び出します。

##  <a name="enableuserdefinedtoolbars"></a>  CMFCToolBarsCustomizeDialog::EnableUserDefinedToolbars

**[ユーザー設定]** ダイアログボックスを使用して、新しいツールバーの作成を有効または無効にします。

```
void EnableUserDefinedToolbars(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からユーザー定義のツールバーを有効にする場合は TRUE。FALSE の場合は、ツールバーを無効にします。

### <a name="remarks"></a>Remarks

*Benable*が TRUE の場合、 **[ツールバー]** ページに **[新規]** 、 **[名前の変更]** 、 **[削除]** の各ボタンが表示されます。

既定では、または*Benable*が FALSE の場合、これらのボタンは表示されず、ユーザーは新しいツールバーを定義できません。

##  <a name="fillallcommandslist"></a>  CMFCToolBarsCustomizeDialog::FillAllCommandsList

指定さ`CListBox`れたオブジェクトに、 **[すべてのコマンド]** カテゴリのコマンドを設定します。

```
virtual void FillAllCommandsList(CListBox& wndListOfCommands) const;
```

### <a name="parameters"></a>パラメーター

*wndListOfCommands*<br/>
入出力設定する`CListBox`オブジェクトへの参照。

### <a name="remarks"></a>Remarks

**[すべてのコマンド]** カテゴリには、すべてのカテゴリのコマンドが含まれています。 [Cmfctoolbarscustomizedialog:: addbutton](#addbutton)メソッドは、指定されたボタンに関連付けられているコマンドを **[すべてのコマンド]** カテゴリに追加します。

このメソッドは、指定さ`CListBox`れたオブジェクトの内容を消去してから、[すべての**コマンド**] カテゴリのコマンドで設定します。

クラス`CMFCMousePropertyPage`は、このメソッドを使用して、ダブルクリックイベント一覧ボックスを設定します。

##  <a name="fillcategoriescombobox"></a>CMFCToolBarsCustomizeDialog:: Fillカテゴリ Combobox

指定さ`CComboBox`れたオブジェクトに、[カスタマイズ] ダイアログボックスの各コマンドカテゴリの名前を**設定**します。

```
void FillCategoriesComboBox(
    CComboBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>パラメーター

*wndCategory*<br/>
入出力設定する`CComboBox`オブジェクトへの参照。

*bAddEmpty*<br/>
からコマンドを持たないコンボボックスにカテゴリを追加するかどうかを指定するブール値です。 このパラメーターが TRUE の場合、空のカテゴリがコンボボックスに追加されます。 それ以外の場合、空のカテゴリは追加されません。

### <a name="remarks"></a>Remarks

このメソッドは[cmfctoolbarscustomizedialog:: fillカテゴリリスト](#fillcategorieslistbox)メソッドに似ていますが、このメソッド`CComboBox`はオブジェクトで動作する点が異なります。

このメソッドは、 `CComboBox`オブジェクトを設定する前に、その内容をクリアしません。 **[すべてのコマンド]** カテゴリが、コンボボックスの最後の項目であることが保証されます。

[Cmfctoolbarscustomizedialog:: AddButton](#addbutton)メソッドを使用して、新しいコマンドカテゴリを追加できます。 [Cmfctoolbarscustomizedialog:: RenameCategory](#renamecategory)メソッドを使用して、既存のカテゴリの名前を変更できます。

クラス`CMFCToolBarsKeyboardPropertyPage` と`CMFCKeyMapDialog`クラスは、このメソッドを使用して、キーボードマップを分類します。

##  <a name="fillcategorieslistbox"></a>CMFCToolBarsCustomizeDialog:: Fillカテゴリリストボックス

指定さ`CListBox`れたオブジェクトに、[カスタマイズ] ダイアログボックスの各コマンドカテゴリの名前を**設定**します。

```
void FillCategoriesListBox(
    CListBox& wndCategory,
    BOOL bAddEmpty = TRUE) const;
```

### <a name="parameters"></a>パラメーター

*wndCategory*<br/>
入出力設定する`CListBox`オブジェクトへの参照。

*bAddEmpty*<br/>
からコマンドを持たないリストボックスにカテゴリを追加するかどうかを指定するブール値です。 このパラメーターが TRUE の場合、リストボックスに空のカテゴリが追加されます。 それ以外の場合、空のカテゴリは追加されません。

### <a name="remarks"></a>Remarks

このメソッドは[cmfctoolbarscustomizedialog:: fillカテゴリ combobox](#fillcategoriescombobox)メソッドに似ていますが、このメソッド`CListBox`はオブジェクトで動作する点が異なります。

このメソッドは、 `CListBox`オブジェクトを設定する前に、その内容をクリアしません。 **[すべてのコマンド]** カテゴリがリストボックスの最後の項目であることが保証されます。

[Cmfctoolbarscustomizedialog:: AddButton](#addbutton)メソッドを使用して、新しいコマンドカテゴリを追加できます。 [Cmfctoolbarscustomizedialog:: RenameCategory](#renamecategory)メソッドを使用して、既存のカテゴリの名前を変更できます。

クラス`CMFCToolBarsCommandsPropertyPage`は、このメソッドを使用して、各コマンドカテゴリに関連付けられているコマンドの一覧を表示します。

##  <a name="getcommandname"></a>  CMFCToolBarsCustomizeDialog::GetCommandName

指定したコマンド ID に関連付けられている名前を取得します。

```
LPCTSTR GetCommandName(UINT uiCmd) const;
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
から取得するコマンドの ID。

### <a name="return-value"></a>戻り値

指定したコマンド ID に関連付けられている名前。コマンドが存在しない場合は NULL。

##  <a name="getcountincategory"></a>CMFCToolBarsCustomizeDialog:: GetCountInCategory

指定されたリストに含まれる、特定のテキストラベルを持つ項目の数を取得します。

```
int GetCountInCategory(
    LPCTSTR lpszItemName,
    const CObList& lstCommands) const;
```

### <a name="parameters"></a>パラメーター

*lpszItemName*<br/>
から照合するテキストラベル。

*lstCommands*<br/>
からオブジェクトを格納して`CMFCToolBarButton`いるリストへの参照。

### <a name="return-value"></a>戻り値

指定されたリストに含まれる、テキストラベルが*Lpszitemname*と等しい項目の数。

### <a name="remarks"></a>Remarks

指定されたオブジェクトリストの各要素は型`CMFCToolBarButton`である必要があります。 このメソッドは、 *Lpszitemname*と[CMFCToolBarButton:: m_strText](../../mfc/reference/cmfctoolbarbutton-class.md#m_strtext)データメンバーを比較します。

##  <a name="getflags"></a>CMFCToolBarsCustomizeDialog:: GetFlags

ダイアログボックスの動作に影響を与えるフラグのセットを取得します。

```
UINT GetFlags() const;
```

### <a name="return-value"></a>戻り値

ダイアログボックスの動作に影響を与えるフラグのセット。

### <a name="remarks"></a>Remarks

このメソッドは、コンストラクターに渡される*Uiflags*パラメーターの値を取得します。 戻り値には、次の値を1つ以上指定できます。

|||
|-|-|
|AFX_CUSTOMIZE_MENU_SHADOWS|メニューの影の外観をユーザーが指定できるようにします。  |
|AFX_CUSTOMIZE_TEXT_LABELS|テキストラベルをツールバーボタンのイメージの下に表示するかどうかをユーザーが指定できるようにします。  |
|AFX_CUSTOMIZE_MENU_ANIMATIONS|メニューのアニメーションスタイルをユーザーが指定できるようにします。  |
|AFX_CUSTOMIZE_NOHELP|[カスタマイズ] ダイアログボックスから [ヘルプ] ボタンを削除します。  |
|AFX_CUSTOMIZE_CONTEXT_HELP|WS_EX_CONTEXTHELP の視覚スタイルを有効にします。  |
|AFX_CUSTOMIZE_NOTOOLS|カスタマイズ ダイアログボックスから **ツール** ページを削除します。 このフラグは、アプリケーションでクラスを`CUserToolsManager`使用している場合に有効です。  |
|AFX_CUSTOMIZE_MENUAMPERS|ボタンのキャプションにアンパサンド ( **&** ) 文字を含めることができるようにします。  |
|AFX_CUSTOMIZE_NO_LARGE_ICONS|カスタマイズ ダイアログボックスから **大きいアイコン** オプションを削除します。  |

WS_EX_CONTEXTHELP visual スタイルの詳細については、「[拡張ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#extended-window-styles)」を参照してください。

##  <a name="onafterchangetool"></a>  CMFCToolBarsCustomizeDialog::OnAfterChangeTool

ユーザーツールが発生した直後の変更に応答します。

```
virtual void OnAfterChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>パラメーター

*pSelTool*<br/>
[入力、出力]変更されたユーザーツールオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、ユーザーがユーザー定義ツールのプロパティを変更したときにフレームワークによって呼び出されます。 既定の実装では、何も行われません。 ユーザーツールの変更後に処理を`CMFCToolBarsCustomizeDialog`実行するには、から派生したクラスでこのメソッドをオーバーライドします。

##  <a name="onassignkey"></a>CMFCToolBarsCustomizeDialog:: On割り当てキー

キーボードショートカットをユーザーが定義するときに検証します。

```
virtual BOOL OnAssignKey(ACCEL* pAccel);
```

### <a name="parameters"></a>パラメーター

*pAccel*<br/>
[入力、出力][ACCEL](/windows/win32/api/winuser/ns-winuser-accel)構造体として表される、提案されたキーボード割り当てへのポインター。

### <a name="return-value"></a>戻り値

キーを割り当てることができる場合は TRUE、キーを割り当てることができない場合は FALSE。 既定の実装では、常に TRUE が返されます。

### <a name="remarks"></a>Remarks

派生クラスでこのメソッドをオーバーライドして、ユーザーが新しいショートカットキーを割り当てたときに追加の処理を実行したり、ユーザーがキーボードショートカットを定義したときにキーボードショートカットを検証したりします。 ショートカットが割り当てられないようにするには、FALSE を返します。 また、メッセージボックスを表示したり、キーボードショートカットが拒否された理由をユーザーに知らせたりする必要があります。

##  <a name="onbeforechangetool"></a>  CMFCToolBarsCustomizeDialog::OnBeforeChangeTool

ユーザーが変更を適用しようとしているときにユーザーツールが変更されたときに、カスタム処理を実行します。

```
virtual void OnBeforeChangeTool(CUserTool* pSelTool);
```

### <a name="parameters"></a>パラメーター

*pSelTool*<br/>
[入力、出力]置き換えようとしているユーザーツールオブジェクトへのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、ユーザー定義ツールのプロパティを変更しようとしているときに、フレームワークによって呼び出されます。 既定の実装では、何も行われません。 ユーザーツールに対する変更 ( *pseltool*が使用するリソースの解放など) が発生する前に処理を実行する場合は、から`CMFCToolBarsCustomizeDialog`派生したクラスのメソッドをオーバーライドします。`OnBeforeChangeTool`

##  <a name="onedittoolbarmenuimage"></a>CMFCToolBarsCustomizeDialog:: OnEditToolbarMenuImage

ユーザーがツールバーボタンまたはメニュー項目アイコンをカスタマイズできるように、イメージエディターを起動します。

```
virtual BOOL OnEditToolbarMenuImage(
    CWnd* pWndParent,
    CBitmap& bitmap,
    int nBitsPerPixel);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から親ウィンドウへのポインター。

*マップ*<br/>
から編集するビットマップオブジェクトへの参照。

*nBitsPerPixel*<br/>
からビットマップの色解像度 (ピクセルあたりのビット数)。

### <a name="return-value"></a>戻り値

変更がコミットされている場合は TRUE。それ以外の場合は FALSE。 既定の実装では、ダイアログボックスが表示され、ユーザーが **[OK]** をクリックした場合は TRUE、ユーザーが **[キャンセル**] または **[閉じる]** ボタンをクリックした場合は FALSE が返されます。

### <a name="remarks"></a>Remarks

このメソッドは、ユーザーがイメージエディターを実行したときにフレームワークによって呼び出されます。 既定の実装では、[ [Cmfcimageeditordialog クラス](../../mfc/reference/cmfcimageeditordialog-class.md)] ダイアログボックスが表示されます。 カスタム`OnEditToolbarMenuImage`イメージエディターを使用するには、派生クラスでをオーバーライドします。

##  <a name="oninitdialog"></a>  CMFCToolBarsCustomizeDialog::OnInitDialog

をオーバーライドして、プロパティシートの初期化を強化します。

```
virtual BOOL OnInitDialog();
```

### <a name="return-value"></a>戻り値

[CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)メソッドを呼び出した結果。

### <a name="remarks"></a>Remarks

このメソッドは、 **[閉じる]** ボタンを表示して、基本クラスの実装である[CPropertySheet:: OnInitDialog](../../mfc/reference/cpropertysheet-class.md#oninitdialog)を拡張します。ダイアログボックスが現在の画面のサイズに合わせて表示されるようにし、 **[ヘルプ]** ボタンを左下隅に移動します。ダイアログボックスの。

##  <a name="oninittoolspage"></a>  CMFCToolBarsCustomizeDialog::OnInitToolsPage

**ツール**ページが初期化されようとしていることをフレームワークからの通知を処理します。

```
virtual void OnInitToolsPage();
```

### <a name="remarks"></a>Remarks

既定の実装では、何も行われません。 この通知を処理するには、派生クラスでこのメソッドをオーバーライドします。

##  <a name="postncdestroy"></a>CMFCToolBarsCustomizeDialog::P ostNcDestroy

ウィンドウが破棄された後にフレームワークによって呼び出されます。

```
virtual void PostNcDestroy();
```

### <a name="remarks"></a>Remarks

このメソッドは、アプリケーションを前の`CPropertySheet::PostNcDestroy`モードに復元することによって、基本クラスの実装を拡張します。

[Cmfctoolbarscustomizedialog:: Create](#create)メソッドを実行すると、ユーザーをカスタマイズタスクに限定する特別なモードでアプリケーションが作成されます。

##  <a name="removebutton"></a>  CMFCToolBarsCustomizeDialog::RemoveButton

指定したカテゴリまたはすべてのカテゴリから、指定したコマンド ID を持つボタンを削除します。

```
int RemoveButton(
    UINT uiCategoryId,
    UINT uiCmdId);

int RemoveButton(
    LPCTSTR lpszCategory,
    UINT uiCmdId);
```

### <a name="parameters"></a>パラメーター

*uiCategoryId*<br/>
からボタンを削除するカテゴリ ID を指定します。

*uiCmdId*<br/>
からボタンのコマンド ID を指定します。

*lpszCategory*<br/>
からボタンを削除するカテゴリの名前を指定します。

### <a name="return-value"></a>戻り値

削除されたボタンの0から始まるインデックス。指定したカテゴリに指定されたコマンド ID が見つからなかった場合は-1。 *UiCategoryId*が-1 の場合、戻り値は0です。

### <a name="remarks"></a>Remarks

すべてのカテゴリからボタンを削除するには、このメソッドの最初のオーバーロードを呼び出し、 *uiCategoryId*を-1 に設定します。

##  <a name="renamecategory"></a>  CMFCToolBarsCustomizeDialog::RenameCategory

**[コマンド]** ページのカテゴリのリストボックスで、カテゴリの名前を変更します。

```
BOOL RenameCategory(
    LPCTSTR lpszCategoryOld,
    LPCTSTR lpszCategoryNew);
```

### <a name="parameters"></a>パラメーター

*Lpszカテゴリ Old*<br/>
から変更するカテゴリ名。

*Lpszカテゴリの新規作成*<br/>
から新しいカテゴリ名。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

カテゴリ名は一意である必要があります。

##  <a name="replacebutton"></a>  CMFCToolBarsCustomizeDialog::ReplaceButton

**コマンド**ページのコマンドのリストボックスにあるツールバーボタンを置き換えます。

```
void ReplaceButton(
    UINT uiCmd,
    const CMFCToolBarButton& button);
```

### <a name="parameters"></a>パラメーター

*uiCmd*<br/>
[in]置き換えられるボタンのコマンドを指定します。

*;*<br/>
から古いボタンを置き換えるツールバーボタンオブジェクトへの**定数**参照。

### <a name="remarks"></a>Remarks

[Cmfctoolbarscustomizedialog:: AddMenu](#addmenu)、 [Cmfctoolbarscustomizedialog:: addmenucommands](#addmenucommands)、または[Cmfctoolbarscustomizedialog:: addtoolbar](#addtoolbar) **がコマンドページに**コマンドを追加すると、そのコマンドは次の[形式になります。CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)オブジェクト (または、によって`AddMenuCommands`追加されたサブメニューを含むメニュー項目の[cmfctoolbarmenubutton クラス](../../mfc/reference/cmfctoolbarmenubutton-class.md)オブジェクト)。 また、この3つのメソッドを呼び出して、コマンドを自動的に追加します。 代わりに、派生型でコマンドを表す場合は、を呼び出し`ReplaceButton` 、派生型のボタンを渡します。

### <a name="example"></a>例

`CMFCToolBarsCustomizeDialog`クラスの`ReplaceButton`メソッドを使用する方法を次の例に示します。 このコードスニペットは、 [Visual Studio のデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_VisualStudioDemo#34](../../mfc/codesnippet/cpp/cmfctoolbarscustomizedialog-class_5.cpp)]

##  <a name="setusercategory"></a>CMFCToolBarsCustomizeDialog:: SetUserCategory

**[コマンド]** ページのカテゴリの一覧で、ユーザーカテゴリを指定します。 [Cmfctoolbarscustomizedialog:: Create](#create)を呼び出す前に、この関数を呼び出す必要があります。

```
BOOL SetUserCategory(LPCTSTR lpszCategory);
```

### <a name="parameters"></a>パラメーター

*lpszCategory*<br/>
からカテゴリの名前。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ユーザーカテゴリの設定は、現在フレームワークでは使用されていません。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CPropertySheet クラス](../../mfc/reference/cpropertysheet-class.md)
