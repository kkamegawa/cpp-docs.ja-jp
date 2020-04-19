---
title: CMFCListCtrl クラス
ms.date: 07/30/2019
f1_keywords:
- CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl
- AFXLISTCTRL/CMFCListCtrl::EnableMarkSortedColumn
- AFXLISTCTRL/CMFCListCtrl::EnableMultipleSort
- AFXLISTCTRL/CMFCListCtrl::GetHeaderCtrl
- AFXLISTCTRL/CMFCListCtrl::IsMultipleSort
- AFXLISTCTRL/CMFCListCtrl::OnCompareItems
- AFXLISTCTRL/CMFCListCtrl::OnGetCellBkColor
- AFXLISTCTRL/CMFCListCtrl::OnGetCellFont
- AFXLISTCTRL/CMFCListCtrl::OnGetCellTextColor
- AFXLISTCTRL/CMFCListCtrl::RemoveSortColumn
- AFXLISTCTRL/CMFCListCtrl::SetSortColumn
- AFXLISTCTRL/CMFCListCtrl::Sort
helpviewer_keywords:
- CMFCListCtrl [MFC], EnableMarkSortedColumn
- CMFCListCtrl [MFC], EnableMultipleSort
- CMFCListCtrl [MFC], GetHeaderCtrl
- CMFCListCtrl [MFC], IsMultipleSort
- CMFCListCtrl [MFC], OnCompareItems
- CMFCListCtrl [MFC], OnGetCellBkColor
- CMFCListCtrl [MFC], OnGetCellFont
- CMFCListCtrl [MFC], OnGetCellTextColor
- CMFCListCtrl [MFC], RemoveSortColumn
- CMFCListCtrl [MFC], SetSortColumn
- CMFCListCtrl [MFC], Sort
ms.assetid: 50d16aee-138c-4f34-8690-cb75d544ef2e
ms.openlocfilehash: 599a00af28ee5b8effbabbe5b334022ceb49f91a
ms.sourcegitcommit: 725e86dabe2901175ecc63261c3bf05802dddff4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/31/2019
ms.locfileid: "68682346"
---
# <a name="cmfclistctrl-class"></a>CMFCListCtrl クラス

クラス`CMFCListCtrl`は、 [CMFCHeaderCtrl クラス](../../mfc/reference/cmfcheaderctrl-class.md)の高度なヘッダーコントロール機能をサポートすることによって、 [CListCtrl クラス](../../mfc/reference/clistctrl-class.md)クラスの機能を拡張します。

## <a name="syntax"></a>構文

```
class CMFCListCtrl : public CListCtrl
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCListCtrl::EnableMarkSortedColumn](#enablemarksortedcolumn)|並べ替えられた列を別の背景色でマークする機能を有効にします。|
|[CMFCListCtrl::EnableMultipleSort](#enablemultiplesort)|複数の並べ替えモードを有効にします。|
|[CMFCListCtrl::GetHeaderCtrl](#getheaderctrl)|下線付きヘッダーコントロールへの参照を返します。|
|[CMFCListCtrl:: Is乗数 Esort](#ismultiplesort)|リストコントロールが複数の並べ替えモードであるかどうかを確認します。|
|[CMFCListCtrl:: OnCompareItems](#oncompareitems)|2つのリストコントロール項目を比較する必要があるときに、フレームワークによって呼び出されます。|
|[CMFCListCtrl::OnGetCellBkColor](#ongetcellbkcolor)|個々のセルの背景色を決定する必要があるときに、フレームワークによって呼び出されます。|
|[CMFCListCtrl::OnGetCellFont](#ongetcellfont)|描画されるセルのフォントを取得する必要があるときに、フレームワークによって呼び出されます。|
|[CMFCListCtrl::OnGetCellTextColor](#ongetcelltextcolor)|個々のセルのテキストの色を決定する必要があるときに、フレームワークによって呼び出されます。|
|[CMFCListCtrl::RemoveSortColumn](#removesortcolumn)|並べ替えられた列の一覧から並べ替え列を削除します。|
|[CMFCListCtrl:: SetSortColumn](#setsortcolumn)|現在の並べ替えられた列と並べ替え順序を設定します。|
|[CMFCListCtrl:: Sort](#sort)|リストコントロールを並べ替えます。|

## <a name="remarks"></a>Remarks

`CMFCListCtrl`では、 [CListCtrl クラス](../../mfc/reference/clistctrl-class.md)クラスに2つの拡張機能が用意されています。 まず、ヘッダーに自動的に並べ替え矢印を描画して、列の並べ替えが使用可能なオプションであることを示します。 2つ目は、同時に複数の列のデータの並べ替えをサポートすることです。

## <a name="example"></a>例

`CMFCListCtrl` クラスのさまざまなメソッドの使用方法を次の例に示します。 この例では、リストコントロールを作成する方法、列を挿入する方法、項目を挿入する方法、項目のテキストを設定する方法、およびリストコントロールのフォントを設定する方法を示します。 このコードスニペットは、 [Visual Studio のデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_VisualStudioDemo#25](../../mfc/codesnippet/cpp/cmfclistctrl-class_1.h)]
[!code-cpp[NVC_MFC_VisualStudioDemo#26](../../mfc/codesnippet/cpp/cmfclistctrl-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListCtrl](../../mfc/reference/clistctrl-class.md)

[CMFCListCtrl](../../mfc/reference/cmfclistctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxlistctrl

##  <a name="enablemarksortedcolumn"></a>  CMFCListCtrl::EnableMarkSortedColumn

並べ替えられた列を別の背景色でマークします。

```
void EnableMarkSortedColumn(
    BOOL bMark = TRUE,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*bMark*<br/>
から別の背景色を有効にするかどうかを決定するブール型パラメーターです。

*より描画*<br/>
からコントロールをすぐに再描画するかどうかを決定するブール型パラメーターです。

### <a name="remarks"></a>Remarks

`EnableMarkSortedColumn`メソッド`CDrawingManager::PixelAlpha`を使用して、並べ替えられた列に使用する色を計算します。 選択された色は、通常の背景色に基づいています。

##  <a name="enablemultiplesort"></a>CMFCListCtrl::EnableMultipleSort

リストコントロール内のデータ行を複数の列で並べ替えることができるようにします。

```
void EnableMultipleSort(BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
から複数の列の並べ替えモードを有効にするかどうかを指定するブール値です。

### <a name="remarks"></a>Remarks

複数の列に基づいて並べ替えを有効にすると、列に階層が設定されます。 最初に、データの行がプライマリ列で並べ替えられます。 同等の値は、その後、優先度に基づいて後続の各列によって並べ替えられます。

##  <a name="getheaderctrl"></a>CMFCListCtrl::GetHeaderCtrl

ヘッダーコントロールへの参照を返します。

```
virtual CMFCHeaderCtrl& GetHeaderCtrl();
```

### <a name="return-value"></a>戻り値

基になる[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)オブジェクトへの参照。

### <a name="remarks"></a>Remarks

リストコントロールのヘッダーコントロールは、列のタイトルを含むウィンドウです。 通常は、列のすぐ上に配置されます。

##  <a name="ismultiplesort"></a>CMFCListCtrl:: Is乗数 Esort

リストコントロールが複数の列での並べ替えを現在サポートしているかどうかを確認します。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>戻り値

リストコントロールが複数の並べ替えをサポートしている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

[CMFCListCtrl クラス](../../mfc/reference/cmfclistctrl-class.md)で複数の並べ替えがサポートされている場合、ユーザーはリストコントロール内のデータを複数の列で並べ替えることができます。 複数の並べ替えを有効にするには、 [CMFCListCtrl:: EnableMultipleSort](#enablemultiplesort)を呼び出します。

##  <a name="oncompareitems"></a>CMFCListCtrl:: OnCompareItems

フレームワークは、2つの項目を比較するときにこのメソッドを呼び出します。

```
virtual int OnCompareItems(
    LPARAM lParam1,
    LPARAM lParam2,
    int iColumn);
```

### <a name="parameters"></a>パラメーター

*lParam1*<br/>
から比較する最初の項目。

*lParam2*<br/>
から比較する2番目の項目。

*iColumn*<br/>
からこのメソッドが並べ替えている列のインデックス。

### <a name="return-value"></a>戻り値

2つの項目の相対位置を示す整数。 負の値は、最初の項目が2番目の項目の前にある必要があることを示し、正の値は最初の項目が2番目の項目の後に続くことを示し、0は2つの項目が等しいことを示します。

### <a name="remarks"></a>Remarks

既定の実装では、常に0が返されます。 独自の並べ替えアルゴリズムを提供するには、この関数をオーバーライドします。

##  <a name="ongetcellbkcolor"></a>  CMFCListCtrl::OnGetCellBkColor

フレームワークは、個々のセルの背景色を決定する必要がある場合に、このメソッドを呼び出します。

```
virtual COLORREF OnGetCellBkColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>パラメーター

*nRow*<br/>
から問題のセルの行。

*n 列*<br/>
から問題のセルの列。

### <a name="return-value"></a>戻り値

セルの背景色を指定する COLOREF 値。

### <a name="remarks"></a>Remarks

の既定の`OnGetCellBkColor`実装では、指定された入力パラメーターを使用`GetBkColor`せず、代わりにを呼び出します。 したがって、既定では、リストコントロール全体の背景色は同じになります。 派生クラスで`OnGetCellBkColor`をオーバーライドして、個々のセルを個別の背景色でマークすることができます。

##  <a name="ongetcellfont"></a>  CMFCListCtrl::OnGetCellFont

フレームワークは、個々のセルのフォントを取得するときに、このメソッドを呼び出します。

```
virtual HFONT OnGetCellFont(
    int nRow,
    int nColumn,
    DWORD dwData = 0);
```

### <a name="parameters"></a>パラメーター

*nRow*<br/>
から問題のセルの行。

*n 列*<br/>
から問題のセルの列。

*dwData*<br/>
からユーザー定義データ。 既定の実装では、このパラメーターは使用されません。

### <a name="return-value"></a>戻り値

現在のセルに使用されるフォントを示すハンドル。

### <a name="remarks"></a>Remarks

既定では、このメソッドは NULL を返します。 リストコントロール内のすべてのセルのフォントは同じです。 異なるセルに異なるフォントを提供するには、このメソッドをオーバーライドします。

##  <a name="ongetcelltextcolor"></a>  CMFCListCtrl::OnGetCellTextColor

フレームワークは、個々のセルのテキストの色を決定する必要がある場合に、このメソッドを呼び出します。

```
virtual COLORREF OnGetCellTextColor(
    int nRow,
    int nColumn);
```

### <a name="parameters"></a>パラメーター

*nRow*<br/>
から問題のセルの行。

*n 列*<br/>
から問題のセルの列。

### <a name="return-value"></a>戻り値

セルのテキストの色を指定する COLOREF 値。

### <a name="remarks"></a>Remarks

既定では、このメソッド`GetTextColor`は入力パラメーターに関係なく、を呼び出します。 リストコントロール全体のテキストの色は同じになります。 派生クラスで`OnGetCellTextColor`をオーバーライドして、個別のセルにテキストの色を付けることができます。

##  <a name="removesortcolumn"></a>  CMFCListCtrl::RemoveSortColumn

並べ替えられた列の一覧から並べ替え列を削除します。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>パラメーター

*iColumn*<br/>
から削除する列。

### <a name="remarks"></a>Remarks

このメソッドは、ヘッダーコントロールから並べ替え列を削除します。 [CMFCHeaderCtrl:: RemoveSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#removesortcolumn)を呼び出します。

##  <a name="setsortcolumn"></a>CMFCListCtrl:: SetSortColumn

現在の並べ替えられた列と並べ替え順序を設定します。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>パラメーター

*iColumn*<br/>
から並べ替える列。

*bAscending*<br/>
から並べ替え順序を指定するブール値。

*bAdd*<br/>
から*IColumn*によって示される列を並べ替え列のリストに追加するかどうかを指定するブール値です。

### <a name="remarks"></a>Remarks

このメソッドは、 [CMFCHeaderCtrl:: SetSortColumn](../../mfc/reference/cmfcheaderctrl-class.md#setsortcolumn)メソッドを使用して、ヘッダーコントロールに入力パラメーターを渡します。

##  <a name="sort"></a>CMFCListCtrl:: Sort

リストコントロールを並べ替えます。

```
virtual void Sort(
    int iColumn,
    BOOL bAscending = TRUE,
    BOOL bAdd = FALSE);
```

### <a name="parameters"></a>パラメーター

*iColumn*<br/>
から並べ替える列。

*bAscending*<br/>
から並べ替え順序を指定するブール値。

*bAdd*<br/>
からこのメソッドが、 *iColumn*によって示される列を並べ替え列のリストに追加するかどうかを指定するブール値です。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CListCtrl クラス](../../mfc/reference/clistctrl-class.md)
