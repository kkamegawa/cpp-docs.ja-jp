---
title: CCheckListBox クラス
ms.date: 11/04/2016
f1_keywords:
- CCheckListBox
- AFXWIN/CCheckListBox
- AFXWIN/CCheckListBox::CCheckListBox
- AFXWIN/CCheckListBox::Create
- AFXWIN/CCheckListBox::DrawItem
- AFXWIN/CCheckListBox::Enable
- AFXWIN/CCheckListBox::GetCheck
- AFXWIN/CCheckListBox::GetCheckStyle
- AFXWIN/CCheckListBox::IsEnabled
- AFXWIN/CCheckListBox::MeasureItem
- AFXWIN/CCheckListBox::OnGetCheckPosition
- AFXWIN/CCheckListBox::SetCheck
- AFXWIN/CCheckListBox::SetCheckStyle
helpviewer_keywords:
- CCheckListBox [MFC], CCheckListBox
- CCheckListBox [MFC], Create
- CCheckListBox [MFC], DrawItem
- CCheckListBox [MFC], Enable
- CCheckListBox [MFC], GetCheck
- CCheckListBox [MFC], GetCheckStyle
- CCheckListBox [MFC], IsEnabled
- CCheckListBox [MFC], MeasureItem
- CCheckListBox [MFC], OnGetCheckPosition
- CCheckListBox [MFC], SetCheck
- CCheckListBox [MFC], SetCheckStyle
ms.assetid: 1dd78438-00e8-441c-b36f-9c4f9ac0d019
ms.openlocfilehash: cd50711813a3cfc1305cd5558c95e909ddbfc3f2
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215522"
---
# <a name="cchecklistbox-class"></a>CCheckListBox クラス

Windows のチェックリスト ボックスの機能を提供します。

## <a name="syntax"></a>構文

```
class CCheckListBox : public CListBox
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|説明|
|----------|-----------------|
|[CCheckListBox:: CCheckListBox](#cchecklistbox)|`CCheckListBox` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|説明|
|----------|-----------------|
|[CCheckListBox:: Create](#create)|Windows チェックリストボックスを作成し、`CCheckListBox` オブジェクトにアタッチします。|
|[CCheckListBox::D rawItem](#drawitem)|オーナー描画リストボックスの視覚的な側面が変化したときにフレームワークによって呼び出されます。|
|[CCheckListBox:: Enable](#enable)|チェックリストボックスの項目を有効または無効にします。|
|[CCheckListBox:: GetCheck](#getcheck)|項目のチェックボックスの状態を取得します。|
|[CCheckListBox:: GetCheckStyle](#getcheckstyle)|コントロールのチェックボックスのスタイルを取得します。|
|[CCheckListBox:: IsEnabled](#isenabled)|項目が有効かどうかを判断します。|
|[CCheckListBox:: MeasureItem](#measureitem)|オーナー描画スタイルのリストボックスが作成されたときに、フレームワークによって呼び出されます。|
|[CCheckListBox:: OnGetCheckPosition](#ongetcheckposition)|項目のチェックボックスの位置を取得するためにフレームワークによって呼び出されます。|
|[CCheckListBox:: SetCheck](#setcheck)|項目のチェックボックスの状態を設定します。|
|[CCheckListBox:: SetCheckStyle](#setcheckstyle)|コントロールのチェックボックスのスタイルを設定します。|

## <a name="remarks"></a>コメント

[チェックリストボックス] には、ファイル名などの項目の一覧が表示されます。 リスト内の各項目の横には、ユーザーがチェックまたはオフにできるチェックボックスがあります。

リストに含まれているのがテキスト文字列を超えているため、`CCheckListBox` はオーナー描画コントロールに対してのみです。 最も簡単なチェックリストボックスには、テキスト文字列とチェックボックスが含まれていますが、テキストを入力する必要はありません。 たとえば、各項目の横にチェックボックスが付いた小さいビットマップの一覧があるとします。

独自のチェックリストボックスを作成するには、`CCheckListBox`から独自のクラスを派生させる必要があります。 独自のクラスを派生させるには、派生クラスのコンストラクターを記述し、`Create`を呼び出します。

リストボックスから親 (通常は、 [CDialog](../../mfc/reference/cdialog-class.md)から派生したクラス) に送信される Windows 通知メッセージを処理する場合は、各メッセージの親クラスにメッセージマップエントリとメッセージハンドラーメンバー関数を追加します。

各メッセージマップエントリには、次の形式があります。

**\_** _通知_ **(** _id_、 _memberFxn_ **)**

ここで `id` 通知を送信するコントロールの子ウィンドウ ID を指定します。 `memberFxn` は、通知を処理するために記述した親メンバー関数の名前です。

親の関数プロトタイプは次のとおりです。

`afx_msg void memberFxn();`

`CCheckListBox` に特に関連するメッセージマップエントリは1つだけです (ただし、 [CListBox](../../mfc/reference/clistbox-class.md)のメッセージマップエントリも参照してください)。

- ユーザーが項目のチェックボックスの状態を変更した ON_CLBN_CHKCHANGE。

チェックリストボックスが既定のチェックリストボックス (それぞれの左側に既定サイズのチェックボックスが付いた文字列の一覧) である場合は、既定の[Cchecklistbox::D rawItem](#drawitem)を使用してチェックリストボックスを描画できます。 それ以外の場合は、 [CListBox:: compareitem](../../mfc/reference/clistbox-class.md#compareitem)関数と[cchecklistbox::D Rawitem](#drawitem)および[Cchecklistbox:: MeasureItem](#measureitem)関数をオーバーライドする必要があります。

チェックリストボックスを作成するには、ダイアログテンプレートを使用するか、コード内で直接作成します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[から派生しているのではない](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CCheckListBox`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

##  <a name="cchecklistbox"></a>CCheckListBox:: CCheckListBox

`CCheckListBox` オブジェクトを構築します。

```
CCheckListBox();
```

### <a name="remarks"></a>コメント

`CCheckListBox` オブジェクトを作成するには、2つの手順を実行します。 最初に `CCheckListBox`から派生したクラスを定義し、次に `Create`を呼び出します。これにより、Windows チェックリストボックスが初期化され、`CCheckListBox` オブジェクトにアタッチされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCControlLadenDialog#60](../../mfc/codesnippet/cpp/cchecklistbox-class_1.cpp)]

##  <a name="create"></a>CCheckListBox:: Create

Windows チェックリストボックスを作成し、`CCheckListBox` オブジェクトにアタッチします。

```
virtual BOOL Create(
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
チェックリストボックスのスタイルを指定します。 スタイルは LBS_HASSTRINGS であり、LBS_OWNERDRAWFIXED (リスト内のすべての項目が同じ高さ) であるか、または LBS_OWNERDRAWVARIABLE (リスト内の項目の高さが異なる) である必要があります。 このスタイルは、LBS_USETABSTOPS を除く他の[リストボックススタイル](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)と組み合わせることができます。

*rect*<br/>
チェックリストボックスのサイズと位置を指定します。 には、 [CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトまたは[RECT](/windows/win32/api/windef/ns-windef-rect)構造体のいずれかを指定できます。

*pParentWnd*<br/>
チェックリストボックスの親ウィンドウ (通常は `CDialog` オブジェクト) を指定します。 NULL にすることはできません。

*nID*<br/>
チェックリストボックスのコントロール ID を指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>コメント

`CCheckListBox` オブジェクトを作成するには、2つの手順を実行します。 まず、`CcheckListBox` から派生したクラスを定義し、`Create`を呼び出します。これにより、Windows チェックリストボックスが初期化され、`CCheckListBox`にアタッチされます。 サンプルについては、「 [cchecklistbox:: cchecklistbox](#cchecklistbox) 」を参照してください。

`Create` 実行すると、Windows によって[WM_NCCREATE](../../mfc/reference/cwnd-class.md#onnccreate)、 [WM_CREATE](../../mfc/reference/cwnd-class.md#oncreate)、 [WM_NCCALCSIZE](../../mfc/reference/cwnd-class.md#onnccalcsize)、および[WM_GETMINMAXINFO](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)メッセージがチェックリストボックスコントロールに送信されます。

これらのメッセージは、既定では `CWnd` 基本クラスの[OnNcCreate](../../mfc/reference/cwnd-class.md#onnccreate)、 [OnCreate](../../mfc/reference/cwnd-class.md#oncreate)、 [OnNcCalcSize](../../mfc/reference/cwnd-class.md#onnccalcsize)、および[OnGetMinMaxInfo](../../mfc/reference/cwnd-class.md#ongetminmaxinfo)メンバー関数によって処理されます。 既定のメッセージ処理を拡張するには、メッセージマップを派生クラスに追加し、前のメッセージハンドラーメンバー関数をオーバーライドします。 たとえば、新しいクラスに必要な初期化を実行するために、`OnCreate`をオーバーライドします。

チェックリストボックスコントロールに、次の[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)を適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

- 垂直スクロールバーを追加する WS_VSCROLL

- 水平スクロールバーを追加する WS_HSCROLL

- グループコントロールに WS_GROUP

- このコントロールへのタブ移動を許可する WS_TABSTOP

##  <a name="drawitem"></a>CCheckListBox::D rawItem

オーナー描画チェックリストボックスの外観が変化したときにフレームワークによって呼び出されます。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDrawItemStruct*<br/>
必要な描画の種類に関する情報を格納している[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)構造体への long ポインター。

### <a name="remarks"></a>コメント

`DRAWITEMSTRUCT` 構造体の `itemAction` メンバーと `itemState` メンバーは、実行される描画アクションを定義します。

既定では、この関数は既定のチェックボックスリストを描画します。このリストは、左側の既定サイズのチェックボックスを持つ文字列のリストで構成されます。 チェックボックスの一覧のサイズは、[[作成](#create)] で指定したものです。

このメンバー関数をオーバーライドして、既定値ではないオーナー描画チェックリストボックスの描画を実装します。たとえば、文字列ではないリストや、可変高さの項目を含むチェックリストボックス、左側にはないチェックボックスなどがあります。 アプリケーションは、このメンバー関数が終了する前に、 *lpDrawItemStruct*で指定された表示コンテキスト用に選択されたすべてのグラフィックスデバイスインターフェイス (GDI) オブジェクトを復元する必要があります。

チェックリストボックスの項目の高さがすべて同じでない場合は、`Create`で指定されたチェックリストボックスのスタイルが**LBS_OWNERVARIABLE**である必要があります。また、 [MeasureItem](#measureitem)関数をオーバーライドする必要があります。

##  <a name="enable"></a>CCheckListBox:: Enable

チェックリストボックスの項目を有効または無効にするには、この関数を呼び出します。

```
void Enable(
    int nIndex,
    BOOL bEnabled = TRUE);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
有効にするチェックリストボックス項目のインデックス。

*bEnabled*<br/>
項目が有効か無効かを指定します。

##  <a name="getcheck"></a>CCheckListBox:: GetCheck

指定したチェックボックスの状態を取得します。

```
int GetCheck(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックスに格納されているチェックボックスの0から始まるインデックス。

### <a name="return-value"></a>戻り値

指定されたチェックボックスの状態。 次の表に、使用可能な値を示します。

|値|説明|
|-----------|-----------------|
|BST_CHECKED|チェック ボックスはオンです。|
|BST_UNCHECKED|チェックボックスはオフになっています。|
|BST_INDETERMINATE|チェックボックスの状態は不確定です。|

##  <a name="getcheckstyle"></a>CCheckListBox:: GetCheckStyle

チェックリストボックスのスタイルを取得するには、この関数を呼び出します。

```
UINT GetCheckStyle();
```

### <a name="return-value"></a>戻り値

コントロールのチェックボックスのスタイル。

### <a name="remarks"></a>コメント

使用できるスタイルの詳細については、「 [Setcheckstyle](#setcheckstyle)」を参照してください。

##  <a name="isenabled"></a>CCheckListBox:: IsEnabled

項目が有効かどうかを判断するには、この関数を呼び出します。

```
BOOL IsEnabled(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
項目のインデックス。

### <a name="return-value"></a>戻り値

項目が有効な場合は0以外の。それ以外の場合は0です。

##  <a name="measureitem"></a>CCheckListBox:: MeasureItem

既定以外のスタイルを持つチェックリストボックスが作成されたときに、フレームワークによって呼び出されます。

```
virtual void MeasureItem(LPMEASUREITEMSTRUCT lpMeasureItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpMeasureItemStruct*<br/>
[MEASUREITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-measureitemstruct)構造体への long ポインター。

### <a name="remarks"></a>コメント

既定では、このメンバー関数は何も行いません。 このメンバー関数をオーバーライドし、`MEASUREITEMSTRUCT` 構造体を入力して、チェックリストボックス項目の次元をウィンドウに通知します。 チェックリストボックスが[LBS_OWNERDRAWVARIABLE](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)スタイルで作成されている場合、フレームワークはリストボックスの各項目に対してこのメンバー関数を呼び出します。 それ以外の場合、このメンバーは1回だけ呼び出されます。

##  <a name="ongetcheckposition"></a>CCheckListBox:: OnGetCheckPosition

フレームワークは、この関数を呼び出して、項目のチェックボックスの位置とサイズを取得します。

```
virtual CRect OnGetCheckPosition(
    CRect rectItem,
    CRect rectCheckBox);
```

### <a name="parameters"></a>パラメーター

*rectItem*<br/>
リスト項目の位置とサイズ。

*rectCheckBox*<br/>
項目のチェックボックスの既定の位置とサイズ。

### <a name="return-value"></a>戻り値

項目のチェックボックスの位置とサイズ。

### <a name="remarks"></a>コメント

既定の実装では、チェックボックスの既定の位置とサイズ (`rectCheckBox`) のみが返されます。 既定では、チェックボックスは項目の左上隅に揃えられ、標準のチェックボックスのサイズになります。 右側にチェックボックスが必要な場合や、より大きいまたは小さいチェックボックスが必要な場合があります。 このような場合は、`OnGetCheckPosition` をオーバーライドして、項目内のチェックボックスの位置とサイズを変更します。

##  <a name="setcheck"></a>CCheckListBox:: SetCheck

指定したチェックボックスの状態を設定します。

```
void SetCheck(
    int nIndex,
    int nCheck);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
リストボックスに格納されているチェックボックスの0から始まるインデックス。

*n*<br/>
指定したチェックボックスのボタンの状態。 使用可能な値については、「解説」を参照してください。

### <a name="remarks"></a>コメント

次の表に、 *n*パラメーターの使用可能な値を示します。

|値|説明|
|-----------|-----------------|
|BST_CHECKED|指定したチェックボックスをオンにします。|
|BST_UNCHECKED|指定したチェックボックスをオフにします。|
|BST_INDETERMINATE|指定したチェックボックスの状態を [不確定] に設定します。<br /><br /> この状態は、チェックボックスのスタイルが BS_AUTO3STATE または BS_3STATE の場合にのみ使用できます。 詳細については、「[ボタンのスタイル](../../mfc/reference/styles-used-by-mfc.md#button-styles)」を参照してください。|

##  <a name="setcheckstyle"></a>CCheckListBox:: SetCheckStyle

チェックリストボックスのチェックボックスのスタイルを設定するには、この関数を呼び出します。

```
void SetCheckStyle(UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*nStyle*<br/>
チェックリストボックスのチェックボックスのスタイルを決定します。

### <a name="remarks"></a>コメント

有効なスタイルは次のとおりです。

- BS_CHECKBOX

- BS_AUTOCHECKBOX

- BS_AUTO3STATE

- BS_3STATE

これらのスタイルの詳細については、「[ボタンのスタイル](../../mfc/reference/styles-used-by-mfc.md#button-styles)」を参照してください。

## <a name="see-also"></a>参照

[MFC のサンプル TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox クラス](../../mfc/reference/clistbox-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CListBox クラス](../../mfc/reference/clistbox-class.md)
