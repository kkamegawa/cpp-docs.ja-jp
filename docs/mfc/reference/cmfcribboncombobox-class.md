---
title: CMFCRibbonComboBox クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::CMFCRibbonComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::AddItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::DeleteItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::EnableDropDownListResize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::FindItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCount
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetCurSel
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetDropDownHeight
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetIntermediateSize
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::GetItemData
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::HasEditBox
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::IsResizeDropDownList
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::OnSelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::RemoveAllItems
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SelectItem
- AFXRIBBONCOMBOBOX/CMFCRibbonComboBox::SetDropDownHeight
helpviewer_keywords:
- CMFCRibbonComboBox [MFC], CMFCRibbonComboBox
- CMFCRibbonComboBox [MFC], AddItem
- CMFCRibbonComboBox [MFC], DeleteItem
- CMFCRibbonComboBox [MFC], EnableDropDownListResize
- CMFCRibbonComboBox [MFC], FindItem
- CMFCRibbonComboBox [MFC], GetCount
- CMFCRibbonComboBox [MFC], GetCurSel
- CMFCRibbonComboBox [MFC], GetDropDownHeight
- CMFCRibbonComboBox [MFC], GetIntermediateSize
- CMFCRibbonComboBox [MFC], GetItem
- CMFCRibbonComboBox [MFC], GetItemData
- CMFCRibbonComboBox [MFC], HasEditBox
- CMFCRibbonComboBox [MFC], IsResizeDropDownList
- CMFCRibbonComboBox [MFC], OnSelectItem
- CMFCRibbonComboBox [MFC], RemoveAllItems
- CMFCRibbonComboBox [MFC], SelectItem
- CMFCRibbonComboBox [MFC], SetDropDownHeight
ms.assetid: 9b29a6a4-cf17-4152-9b13-0bf90784b30d
ms.openlocfilehash: 89007ea3eb7fd0aef28caadf439195b4090a05d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237336"
---
# <a name="cmfcribboncombobox-class"></a>CMFCRibbonComboBox クラス

`CMFCRibbonComboBox`クラスは、リボン バー、リボン パネル、またはリボン ポップアップ メニューに追加できるコンボ ボックス コントロールを実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonComboBox : public CMFCRibbonEdit
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonComboBox::CMFCRibbonComboBox](#cmfcribboncombobox)|CMFCRibbonComboBox オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonComboBox::AddItem](#additem)|リスト ボックスに一意の項目を追加します。|
|[CMFCRibbonComboBox::DeleteItem](#deleteitem)|リスト ボックスから、指定した項目を削除します。|
|[CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)|リスト ボックスのドロップダウンしたときにサイズを変更できるかどうかを指定します。|
|[CMFCRibbonComboBox::FindItem](#finditem)|指定した文字列と一致するリスト ボックスで、最初の項目のインデックスを返します。|
|[CMFCRibbonComboBox::GetCount](#getcount)|リスト ボックス項目の数を返します。|
|[CMFCRibbonComboBox::GetCurSel](#getcursel)|リスト ボックスで現在選択されている項目のインデックスを取得します。|
|[CMFCRibbonComboBox::GetDropDownHeight](#getdropdownheight)|、リスト ボックスが削除されるときに、リスト ボックスの高さを取得します。|
|[CMFCRibbonComboBox::GetIntermediateSize](#getintermediatesize)|中間モードで表示されるように、コンボ ボックスのサイズを返します。|
|[CMFCRibbonComboBox::GetItem](#getitem)|リスト ボックスで指定したインデックス位置にある項目に関連付けられている文字列を返します。|
|[CMFCRibbonComboBox::GetItemData](#getitemdata)|リスト ボックスで指定したインデックス位置にある項目に関連付けられているデータを返します。|
|[CMFCRibbonComboBox::HasEditBox](#haseditbox)|コントロールが編集ボックスに含まれるかどうかを示します。|
|[CMFCRibbonComboBox::IsResizeDropDownList](#isresizedropdownlist)|リスト ボックスのサイズを変更できるかどうかを示します。|
|[CMFCRibbonComboBox::OnSelectItem](#onselectitem)|ユーザーがリスト ボックスで項目を選択すると、フレームワークによって呼び出されます。|
|[CMFCRibbonComboBox::RemoveAllItems](#removeallitems)|リスト ボックスからすべてのアイテムを削除し、編集ボックスをクリアします。|
|[CMFCRibbonComboBox::SelectItem](#selectitem)|リスト ボックス内の項目を選択します。|
|[CMFCRibbonComboBox::SetDropDownHeight](#setdropdownheight)|にドロップしたときに、リスト ボックスの高さを設定します。|

## <a name="remarks"></a>Remarks

リボンのコンボ ボックスは、ユーザーが編集可能なラベルまたは静的ラベルと組み合わせて、リスト ボックスで構成されます。 リボンのコンボ ボックスを作成するときに種類を指定する必要があります。

## <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCRibbonComboBox`クラス、コンボ ボックスに項目を追加、コンボ ボックスで、項目を選択およびパネルにコンボ ボックスを追加します。

[!code-cpp[NVC_MFC_RibbonApp#11](../../mfc/reference/codesnippet/cpp/cmfcribboncombobox-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribboncombobox.h

##  <a name="additem"></a>  CMFCRibbonComboBox::AddItem

リスト ボックスに一意の項目を追加します。

```
virtual INT_PTR AddItem(
    LPCTSTR lpszItem,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>パラメーター

*lpszItem*<br/>
[in]追加する項目の文字列。

*dwData*<br/>
[in]追加する項目に関連付けられたデータ。

### <a name="return-value"></a>戻り値

追加する項目の 0 から始まるインデックス。

##  <a name="cmfcribboncombobox"></a>  CMFCRibbonComboBox::CMFCRibbonComboBox

`CMFCRibbonComboBox` オブジェクトを構築します。

```
public:
CMFCRibbonComboBox(
    UINT nID,
    BOOL bHasEditBox=TRUE,
    Int nWidth=-1,
    LPCTSTR lpszLabel=NULL,
    Int nImage=-1);

protected:
CMFCRibbonComboBox();
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
[in]コンボ ボックスの ID。

*bHasEditBox*<br/>
[in]コントロール内で、編集ボックスを使用する場合は TRUE。FALSE それ以外の場合。

*nWidth*<br/>
[in]ピクセルのコンボ ボックスの幅または、既定の幅の場合は-1。

*lpszLabel*<br/>
[in]コンボ ボックスのラベルを表示します。

*nImage*<br/>
[in]コンボ ボックスの小さいイメージのインデックス。

### <a name="remarks"></a>Remarks

既定の幅は、108 ピクセルです。

##  <a name="deleteitem"></a>  CMFCRibbonComboBox::DeleteItem

リスト ボックスから、指定した項目を削除します。

```
BOOL DeleteItem(int iIndex);
BOOL DeleteItem(DWORD_PTR dwData);

BOOL DeleteItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
[in]削除する項目の 0 から始まるインデックス。

*dwData*<br/>
[in]削除する項目に関連付けられたデータ。

*lpszText*<br/>
[in]削除する項目の文字列。 同じ文字列のアイテムが複数ある場合は、最初の項目が削除されます。

### <a name="return-value"></a>戻り値

指定した項目が削除された場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="enabledropdownlistresize"></a>  CMFCRibbonComboBox::EnableDropDownListResize

リスト ボックスのドロップダウンしたときにサイズを変更できるかどうかを指定します。

```
void EnableDropDownListResize(BOOL bEnable=FALSE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]有効にするサイズ変更する場合は Trueサイズ変更を無効にする場合は FALSE。

### <a name="remarks"></a>Remarks

サイズ変更を有効にすると、リスト ボックスに表示する項目に合わせてサイズが変わります。

##  <a name="finditem"></a>  CMFCRibbonComboBox::FindItem

指定した文字列と一致するリスト ボックスで、最初の項目のインデックスを返します。

```
int FindItem(LPCTSTR lpszText) const;
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
[in]リスト ボックス内の項目の文字列。

### <a name="return-value"></a>戻り値

項目の 0 から始まるインデックスまたは、項目が見つからない場合は-1。

### <a name="remarks"></a>Remarks

##  <a name="getcount"></a>  CMFCRibbonComboBox::GetCount

リスト ボックス項目の数を返します。

```
INT_PTR GetCount() const;
```

### <a name="return-value"></a>戻り値

リスト ボックスまたはリスト ボックスに項目が含まれていない場合は 0 の項目の数。

### <a name="remarks"></a>Remarks

##  <a name="getcursel"></a>  CMFCRibbonComboBox::GetCurSel

リスト ボックスで現在選択されている項目のインデックスを取得します。

```
int GetCurSel() const;
```

### <a name="return-value"></a>戻り値

リスト ボックスで現在選択されている項目の 0 から始まるインデックスまたは、項目が選択されていない場合は-1。

##  <a name="getdropdownheight"></a>  CMFCRibbonComboBox::GetDropDownHeight

、リスト ボックスが削除されるときに、リスト ボックスの高さを取得します。

```
int GetDropDownHeight();
```

### <a name="return-value"></a>戻り値

リスト ボックスのピクセル単位の高さ。

### <a name="remarks"></a>Remarks

##  <a name="getintermediatesize"></a>  CMFCRibbonComboBox::GetIntermediateSize

中間モードで表示されるように、コンボ ボックスのサイズを返します。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]コンボ ボックスのデバイス コンテキストへのポインター。

### <a name="return-value"></a>戻り値

コンボ ボックスのサイズ。

### <a name="remarks"></a>Remarks

小さいイメージを表示するとき、返されるサイズは、コンボ ボックスのサイズに基づきます。

##  <a name="getitem"></a>  CMFCRibbonComboBox::GetItem

リスト ボックスで指定したインデックス位置にある項目に関連付けられている文字列を返します。

```
LPCTSTR GetItem(int iIndex) const;
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
[in]リスト ボックス内の項目の 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

アイテムに関連付けられている文字列へのポインターそれ以外の場合、インデックス パラメーターが有効でない場合、またはインデックスのパラメーターが-1 とコンボ ボックスで選択した項目がない場合は NULL です。

### <a name="remarks"></a>Remarks

##  <a name="getitemdata"></a>  CMFCRibbonComboBox::GetItemData

リスト ボックスで指定したインデックス位置にある項目に関連付けられているデータを返します。

```
DWORD_PTR GetItemData(int iIndex) const;
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
[in]リスト ボックス内の項目の 0 から始まるインデックス。

### <a name="return-value"></a>戻り値

項目に関連付けられたデータ0 または項目が存在しない場合、またはインデックスのパラメーターが-1 とリスト ボックスで選択した項目がない場合。

##  <a name="haseditbox"></a>  CMFCRibbonComboBox::HasEditBox

コントロールが編集ボックスに含まれるかどうかを示します。

```
BOOL HasEditBox() const;
```

### <a name="return-value"></a>戻り値

コントロールには、編集ボックスが含まれている場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="isresizedropdownlist"></a>  CMFCRibbonComboBox::IsResizeDropDownList

リスト ボックスのサイズを変更できるかどうかを示します。

```
BOOL IsResizeDropDownList() const;
```

### <a name="return-value"></a>戻り値

リスト ボックスのサイズを変更できる場合は TRUE。それ以外の場合は FALSE です。 [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)

### <a name="remarks"></a>Remarks

使用してリスト ボックスのサイズ変更できるように、 [CMFCRibbonComboBox::EnableDropDownListResize](#enabledropdownlistresize)メソッド。

##  <a name="onselectitem"></a>  CMFCRibbonComboBox::OnSelectItem

ユーザーがリスト ボックスで項目を選択すると、フレームワークによって呼び出されます。

```
virtual void OnSelectItem(int nItem);
```

### <a name="parameters"></a>パラメーター

*nItem*<br/>
[in]選択した項目のインデックス。

### <a name="remarks"></a>Remarks

ユーザー入力の選択を処理する場合は、このメソッドをオーバーライドします。

##  <a name="removeallitems"></a>  CMFCRibbonComboBox::RemoveAllItems

リスト ボックスからすべてのアイテムを削除し、編集ボックスをクリアします。

```
void RemoveAllItems();
```

### <a name="remarks"></a>Remarks

##  <a name="selectitem"></a>  CMFCRibbonComboBox::SelectItem

リスト ボックス内の項目を選択します。

```
BOOL SelectItem(int iIndex);
BOOL SelectItem(DWORD_PTR dwData);

BOOL SelectItem(LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
[in]リスト ボックス内の項目の 0 から始まるインデックス。

*dwData*<br/>
[in]リスト ボックス内の項目に関連付けられたデータ。

*lpszText*<br/>
[in]リスト ボックス内の項目の文字列。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="setdropdownheight"></a>  CMFCRibbonComboBox::SetDropDownHeight

にドロップしたときに、リスト ボックスの高さを設定します。

```
void SetDropDownHeight(int nHeight);
```

### <a name="parameters"></a>パラメーター

*nHeight*<br/>
[in]リスト ボックスのピクセル単位の高さ。

### <a name="remarks"></a>Remarks

既定の高さは、150 ピクセルです。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonEdit クラス](../../mfc/reference/cmfcribbonedit-class.md)
