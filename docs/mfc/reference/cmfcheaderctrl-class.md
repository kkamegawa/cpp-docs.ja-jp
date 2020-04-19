---
title: CMFCHeaderCtrl Class
ms.date: 11/04/2016
f1_keywords:
- CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::CMFCHeaderCtrl
- AFXHEADERCTRL/CMFCHeaderCtrl::EnableMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::GetColumnState
- AFXHEADERCTRL/CMFCHeaderCtrl::GetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::IsAscending
- AFXHEADERCTRL/CMFCHeaderCtrl::IsDialogControl
- AFXHEADERCTRL/CMFCHeaderCtrl::IsMultipleSort
- AFXHEADERCTRL/CMFCHeaderCtrl::RemoveSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::SetSortColumn
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawItem
- AFXHEADERCTRL/CMFCHeaderCtrl::OnDrawSortArrow
- AFXHEADERCTRL/CMFCHeaderCtrl::OnFillBackground
helpviewer_keywords:
- CMFCHeaderCtrl [MFC], CMFCHeaderCtrl
- CMFCHeaderCtrl [MFC], EnableMultipleSort
- CMFCHeaderCtrl [MFC], GetColumnState
- CMFCHeaderCtrl [MFC], GetSortColumn
- CMFCHeaderCtrl [MFC], IsAscending
- CMFCHeaderCtrl [MFC], IsDialogControl
- CMFCHeaderCtrl [MFC], IsMultipleSort
- CMFCHeaderCtrl [MFC], RemoveSortColumn
- CMFCHeaderCtrl [MFC], SetSortColumn
- CMFCHeaderCtrl [MFC], OnDrawItem
- CMFCHeaderCtrl [MFC], OnDrawSortArrow
- CMFCHeaderCtrl [MFC], OnFillBackground
ms.assetid: 2f5fbf7b-5c75-42db-9216-640b1628f777
ms.openlocfilehash: 86674e086da482e59b2711f5ba9154848ff05a6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218386"
---
# <a name="cmfcheaderctrl-class"></a>CMFCHeaderCtrl Class

`CMFCHeaderCtrl`クラスは、ヘッダー コントロールの複数の列の並べ替えをサポートしています。

## <a name="syntax"></a>構文

```
class CMFCHeaderCtrl : public CHeaderCtrl
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCHeaderCtrl::CMFCHeaderCtrl](#cmfcheaderctrl)|`CMFCHeaderCtrl` オブジェクトを構築します。|
|`CMFCHeaderCtrl::~CMFCHeaderCtrl`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)|有効または無効に*複数列の並べ替え*の現在のヘッダー コントロールのモード。|
|[CMFCHeaderCtrl::GetColumnState](#getcolumnstate)|列が並べ替えられていないかを昇順または降順で並べ替えるかどうかを示します。|
|[CMFCHeaderCtrl::GetSortColumn](#getsortcolumn)|ヘッダー コントロールの最初の並べ替えられた列の 0 から始まるインデックスを取得します。|
|`CMFCHeaderCtrl::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|[CMFCHeaderCtrl::IsAscending](#isascending)|ヘッダー コントロールの任意の列を昇順で並べ替えるかどうかを示します。|
|[CMFCHeaderCtrl::IsDialogControl](#isdialogcontrol)|現在のヘッダー コントロールの親ウィンドウがダイアログ ボックスであるかどうかを示します。|
|[CMFCHeaderCtrl::IsMultipleSort](#ismultiplesort)|現在のヘッダー コントロールがかどうかを示す*複数列の並べ替え*モード。|
|[CMFCHeaderCtrl::RemoveSortColumn](#removesortcolumn)|並べ替え列の一覧から、指定された列を削除します。|
|[CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)|ヘッダー コントロールの指定された列の並べ替え順序を設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCHeaderCtrl::OnDrawItem](#ondrawitem)|ヘッダー コントロールの列を描画するためにフレームワークによって呼び出されます。|
|[CMFCHeaderCtrl::OnDrawSortArrow](#ondrawsortarrow)|並べ替え矢印を描画するためにフレームワークによって呼び出されます。|
|[CMFCHeaderCtrl::OnFillBackground](#onfillbackground)|ヘッダー コントロールの列の背景を塗りつぶすために、フレームワークによって呼び出されます。|

## <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCHeaderCtrl`クラス、および有効にする方法*複数列の並べ替え*の現在のヘッダー コントロールのモード。

[!code-cpp[NVC_MFC_RibbonApp#24](../../mfc/reference/codesnippet/cpp/cmfcheaderctrl-class_1.cpp)]

## <a name="remarks"></a>Remarks

`CMFCHeaderCtrl`クラスを示す列が並べ替えられているヘッダー コントロールの列の並べ替え矢印を描画します。 使用*複数列の並べ替え*モードの場合、親リスト コントロール内の列のセット ( [CMFCListCtrl クラス](../../mfc/reference/cmfclistctrl-class.md)) と同時に並べ替えることができます。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CHeaderCtrl](../../mfc/reference/cheaderctrl-class.md)

[CMFCHeaderCtrl](../../mfc/reference/cmfcheaderctrl-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxheaderctrl.h

##  <a name="cmfcheaderctrl"></a>  CMFCHeaderCtrl::CMFCHeaderCtrl

`CMFCHeaderCtrl` オブジェクトを構築します。

```
CMFCHeaderCtrl::CMFCHeaderCtrl()
```

### <a name="remarks"></a>Remarks

このコンス トラクターでは、指定した値には、次のメンバー変数を初期化します。

|メンバー変数|[値]|
|---------------------|-----------|
|`m_bIsMousePressed`|false|
|`m_bMultipleSort`|false|
|`m_bAscending`|true|
|`m_nHighlightedItem`|-1|
|`m_bTracked`|false|
|`m_bIsDlgControl`|false|
|`m_hFont`|NULL|

##  <a name="enablemultiplesort"></a>  CMFCHeaderCtrl::EnableMultipleSort

有効または無効に*複数列の並べ替え*の現在のヘッダー コントロールのモード。

```
void EnableMultipleSort(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]複数列の並べ替えモードを有効にする場合は TRUE複数の列の並べ替えモードを無効にして、並べ替えられた列の一覧から列を削除する場合は FALSE。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

有効または複数の列の並べ替えモードを無効にするには、このメソッドを使用します。 ヘッダー コントロールが複数の列の並べ替えモードの場合、2 つ以上の列が並べ替えで参加できます。

##  <a name="getcolumnstate"></a>  CMFCHeaderCtrl::GetColumnState

列がない並べ替えられた、またはを昇順または降順で並べ替えるかどうかを示します。

```
int GetColumnState(int iColumn) const;
```

### <a name="parameters"></a>パラメーター

*iColumn*<br/>
[in]列の 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

指定された列の並べ替え状態を示す値。 次の表では、使用可能な値を示します。

|[値]|説明|
|-----------|-----------------|
|-1|降順で並べ替えられます。|
|0|並べ替えられません。|
|1|昇順に並べ替えられます。|

### <a name="remarks"></a>Remarks

##  <a name="getsortcolumn"></a>  CMFCHeaderCtrl::GetSortColumn

ヘッダー コントロールの最初の並べ替えられた列の 0 から始まるインデックスを取得します。

```
int GetSortColumn() const;
```

### <a name="return-value"></a>戻り値

並べ替えられた列で並べ替えられた列が見つからない場合は-1 のインデックス。

### <a name="remarks"></a>Remarks

ヘッダー コントロールが場合*複数列の並べ替え*モードとするこのメソッドは、アサートを使用するように勧めるデバッグ モードでアプリケーションをコンパイル、 [CMFCHeaderCtrl::GetColumnState](#getcolumnstate)メソッド代わりにします。 ヘッダー コントロールは、複数の列の並べ替えモードでは、小売モードでアプリケーションをコンパイルする場合は、このメソッドは-1 を返します。

##  <a name="isascending"></a>  CMFCHeaderCtrl::IsAscending

ヘッダー コントロールの任意の列を昇順で並べ替えるかどうかを示します。

```
BOOL IsAscending() const;
```

### <a name="return-value"></a>戻り値

ヘッダー コントロールの任意の列が昇順に並べ替えられている場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

このメソッドから返される値は、ヘッダー コントロールの項目に適切な並べ替え矢印を表示する使用されます。 使用して、 [CMFCHeaderCtrl::SetSortColumn](#setsortcolumn)並べ替え順序を設定します。

##  <a name="isdialogcontrol"></a>  CMFCHeaderCtrl::IsDialogControl

現在のヘッダー コントロールの親ウィンドウがダイアログ ボックスであるかどうかを示します。

```
BOOL IsDialogControl() const;
```

### <a name="return-value"></a>戻り値

現在のヘッダー コントロールの親ウィンドウがダイアログ ボックスがある場合は TRUE。それ以外の場合、FALSE です。

##  <a name="ismultiplesort"></a>  CMFCHeaderCtrl::IsMultipleSort

現在のヘッダー コントロールがかどうかを示す*複数列の並べ替え*モード。

```
BOOL IsMultipleSort() const;
```

### <a name="return-value"></a>戻り値

は複数の列の並べ替えモードが有効な場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

使用して、 [CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)メソッドを有効または複数の列の並べ替えモードを無効にします。 ヘッダー コントロールが複数の列の並べ替えモードの場合、2 つ以上の列が並べ替えで参加できます。

##  <a name="ondrawitem"></a>  CMFCHeaderCtrl::OnDrawItem

ヘッダー コントロールの列を描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawItem(
    CDC* pDC,
    int iItem,
    CRect rect,
    BOOL bIsPressed,
    BOOL bIsHighlighted);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*iItem*<br/>
[in]描画するために、項目の 0 から始まるインデックス。

*rect*<br/>
[in]描画する項目の外接する四角形。

*bIsPressed*<br/>
[in]押された状態で項目を描画する場合は TRUEそれ以外の場合、FALSE です。

*bIsHighlighted*<br/>
[in]強調表示された状態で項目を描画する場合は TRUEそれ以外の場合、FALSE です。

##  <a name="ondrawsortarrow"></a>  CMFCHeaderCtrl::OnDrawSortArrow

並べ替え矢印を描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawSortArrow(
    CDC* pDC,
    CRect rectArrow);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

*rectArrow*<br/>
[in]並べ替え矢印の外接する四角形。

##  <a name="onfillbackground"></a>  CMFCHeaderCtrl::OnFillBackground

ヘッダー コントロールの列の背景を塗りつぶすために、フレームワークによって呼び出されます。

```
virtual void OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]デバイス コンテキストへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="removesortcolumn"></a>  CMFCHeaderCtrl::RemoveSortColumn

並べ替え列の一覧から、指定された列を削除します。

```
void RemoveSortColumn(int iColumn);
```

### <a name="parameters"></a>パラメーター

*iColumn*<br/>
[in]削除する列の 0 から始まるインデックス。

##  <a name="setsortcolumn"></a>  CMFCHeaderCtrl::SetSortColumn

ヘッダー コントロールの指定された列の並べ替え順序を設定します。

```
void SetSortColumn(
    int iColumn,
    BOOL bAscending=TRUE,
    BOOL bAdd=FALSE);
```

### <a name="parameters"></a>パラメーター

*iColumn*<br/>
[in]ヘッダー コントロールの列の 0 から始まるインデックス。 このパラメーターが 0 より小さい場合、このメソッドは、並べ替え列の一覧からすべての列を削除します。

*bAscending*<br/>
[in]列の並べ替え順序を指定する、 *iColumn*パラメーターを指定します。 昇順を設定する場合は TRUE降順の順序を設定する場合は FALSE。 既定値は TRUE です。

*bAdd*<br/>
[in]True を列の並べ替え順序の設定、 *iColumn*パラメーターを指定します。

現在のヘッダー コントロールの場合*複数列の並べ替え*モードでは、このメソッドは、並べ替え列の一覧に指定された列を追加します。 使用[CMFCHeaderCtrl::EnableMultipleSort](#enablemultiplesort)を複数の列の並べ替えモードを設定します。

かどうかは、複数の列の並べ替えモードが設定されていないと、このメソッドは、デバッグ モードでコンパイルされている、このメソッドをアサートします。 複数列の並べ替えモードが設定されていない、このメソッドは、小売モードでコンパイルされている場合は、このメソッドは最初並べ替え列の一覧からすべての列を削除し、リストに指定された列を追加します。

最初の列の並べ替え、一覧からすべての列を削除し、一覧に指定された列を追加する場合は FALSE。 既定値は FALSE です。

### <a name="remarks"></a>Remarks

列の並べ替え順序を設定するのにには、このメソッドを使用します。 必要に応じて、このメソッドは、列を並べ替え列の一覧に追加します。 ヘッダー コントロールでは、並べ替え順序を使用して、上向きまたは下向きの矢印を描画します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCListCtrl クラス](../../mfc/reference/cmfclistctrl-class.md)
