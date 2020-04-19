---
title: CMFCPropertyGridColorProperty クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableAutomaticButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::EnableOtherButton
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetColumnsNumber
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridColorProperty::SetOriginalValue
helpviewer_keywords:
- CMFCPropertyGridColorProperty [MFC], CMFCPropertyGridColorProperty
- CMFCPropertyGridColorProperty [MFC], EnableAutomaticButton
- CMFCPropertyGridColorProperty [MFC], EnableOtherButton
- CMFCPropertyGridColorProperty [MFC], GetColor
- CMFCPropertyGridColorProperty [MFC], SetColor
- CMFCPropertyGridColorProperty [MFC], SetColumnsNumber
- CMFCPropertyGridColorProperty [MFC], SetOriginalValue
ms.assetid: af37be93-a91e-40a2-9a65-0f3412c6f0f8
ms.openlocfilehash: 95dcbbc2b445e2ff67979b90816daed0fb0c0fba
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403608"
---
# <a name="cmfcpropertygridcolorproperty-class"></a>CMFCPropertyGridColorProperty クラス

`CMFCPropertyGridColorProperty` クラスは、色の選択用のダイアログ ボックスを開くプロパティ リスト コントロール項目をサポートします。

## <a name="syntax"></a>構文

```
class CMFCPropertyGridColorProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty](#cmfcpropertygridcolorproperty)|`CMFCPropertyGridColorProperty` オブジェクトを構築します。|
|`CMFCPropertyGridColorProperty::~CMFCPropertyGridColorProperty`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCPropertyGridColorProperty::EnableAutomaticButton](#enableautomaticbutton)|により、*自動*色の選択 ダイアログ ボックスのボタンをクリックします。 (標準の自動ボタンのラベルは**自動**)。|
|[CMFCPropertyGridColorProperty::EnableOtherButton](#enableotherbutton)|により、*他*色の選択 ダイアログ ボックスのボタン。 (標準の他のボタンのラベルは**その他の色**)。|
|`CMFCPropertyGridColorProperty::FormatProperty`|プロパティ値のテキスト表現の書式を設定します  (上書き[cmfcpropertygridproperty::formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty))。|
|[CMFCPropertyGridColorProperty::GetColor](#getcolor)|プロパティの現在の色を取得します。|
|`CMFCPropertyGridColorProperty::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|
|`CMFCPropertyGridColorProperty::OnClickButton`|プロパティに含まれているボタンをユーザーがクリックすると、フレームワークによって呼び出されます  (上書き[cmfcpropertygridproperty::onclickbutton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton))。|
|`CMFCPropertyGridColorProperty::OnDrawValue`|プロパティ値を表示するためにフレームワークによって呼び出されます  (上書き[cmfcpropertygridproperty::ondrawvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#ondrawvalue))。|
|`CMFCPropertyGridColorProperty::OnEdit`|ユーザーがプロパティ値を変更しようとすると、フレームワークによって呼び出されます  (上書き[cmfcpropertygridproperty::onedit](../../mfc/reference/cmfcpropertygridproperty-class.md#onedit))。|
|`CMFCPropertyGridColorProperty::OnUpdateValue`|編集可能なプロパティの値が変更されると、フレームワークによって呼び出されます  (上書き[cmfcpropertygridproperty::onupdatevalue](../../mfc/reference/cmfcpropertygridproperty-class.md#onupdatevalue))。|
|[CMFCPropertyGridColorProperty::SetColor](#setcolor)|プロパティの新しい色を設定します。|
|[CMFCPropertyGridColorProperty::SetColumnsNumber](#setcolumnsnumber)|現在のカラー プロパティ グリッド内の列の数を指定します。|
|[CMFCPropertyGridColorProperty::SetOriginalValue](#setoriginalvalue)|編集可能なプロパティの元の値を設定します。|

## <a name="remarks"></a>Remarks

`CMFCPropertyGridColorProperty` クラスは、プロパティ リスト コントロールに追加できるカラー プロパティをサポートします。 詳細については、次を参照してください。、 [CMFCPropertyGridCtrl クラス](../../mfc/reference/cmfcpropertygridctrl-class.md)します。

## <a name="example"></a>例

`CMFCPropertyGridColorProperty` クラスのオブジェクトを構築する方法、および `CMFCPropertyGridColorProperty` クラスの各種メソッドを使用してこのオブジェクトを構成する方法を次の例に示します。 このコードでは、自動ボタンとその他ボタンを有効にする方法、および色と列番号を設定する方法を示しています。 この例は、[新しいコントロール サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_NewControls#13](../../mfc/reference/codesnippet/cpp/cmfcpropertygridcolorproperty-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridColorProperty](../../mfc/reference/cmfcpropertygridcolorproperty-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpropertygridctrl.h

##  <a name="cmfcpropertygridcolorproperty"></a>  CMFCPropertyGridColorProperty::CMFCPropertyGridColorProperty

`CMFCPropertyGridColorProperty` オブジェクトを構築します。

```
CMFCPropertyGridColorProperty(
    const CString& strName,
    const COLORREF& color,
    CPalette* pPalette = NULL,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0);
```

### <a name="parameters"></a>パラメーター

*strName*<br/>
[in]プロパティの名前。

*色*<br/>
[in]プロパティの色の値。

*pPalette*<br/>
[in]色のパレットへのポインター。 既定値は、NULL です。

*lpszDescr*<br/>
[in]プロパティの説明。 既定値は、NULL です。

*dwData*<br/>
[in]整数プロパティに関連付けられているその他のデータへのポインターなどのアプリケーションに固有のデータ。 既定値は 0 です。

##  <a name="enableautomaticbutton"></a>  CMFCPropertyGridColorProperty::EnableAutomaticButton

により、*自動*色の選択 ダイアログ ボックスのボタンをクリックします。 (標準の自動ボタンのラベルは**自動**)。

```
void EnableAutomaticButton(
    LPCTSTR lpszLabel,
    COLORREF colorAutomatic,
    BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]自動ボタンのラベル テキスト。

*colorAutomatic*<br/>
[in]自動 (既定値) の色の RGB カラー値。

*bEnable*<br/>
[in]自動ボタンを有効にする場合は TRUEそれ以外の場合、FALSE です。 既定値は TRUE です。

### <a name="remarks"></a>Remarks

##  <a name="enableotherbutton"></a>  CMFCPropertyGridColorProperty::EnableOtherButton

により、*他*色の選択 ダイアログ ボックスのボタン。 (標準の他のボタンのラベルは**その他の色**)。

```
void EnableOtherButton(
    LPCTSTR lpszLabel,
    BOOL bAltColorDlg = TRUE,
    BOOL bEnable = TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
[in]その他のボタンのラベル テキスト。

*bAltColorDlg*<br/>
[in]表示する場合は True、 `CMFCColorDialog` ; ダイアログ ボックス標準の色の選択 ダイアログ ボックスを表示する場合は FALSE。 既定値は TRUE です。

*bEnable*<br/>
[in]その他のボタンを表示する場合は TRUEそれ以外の場合、FALSE です。  既定値は TRUE です。

### <a name="remarks"></a>Remarks

##  <a name="getcolor"></a>  CMFCPropertyGridColorProperty::GetColor

プロパティの現在の色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

RGB 色の値。

### <a name="remarks"></a>Remarks

##  <a name="setcolor"></a>  CMFCPropertyGridColorProperty::SetColor

プロパティの新しい色を設定します。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

*色*<br/>
[in]RGB 色の値。

### <a name="remarks"></a>Remarks

##  <a name="setcolumnsnumber"></a>  CMFCPropertyGridColorProperty::SetColumnsNumber

現在のカラー プロパティ グリッド内の列の数を指定します。

```
void SetColumnsNumber(int nColumnsNumber);
```

### <a name="parameters"></a>パラメーター

*nColumnsNumber*<br/>
[in]推奨される色のプロパティ グリッドで列数。

### <a name="remarks"></a>Remarks

このメソッドの値を設定、`m_nColumnsNumber`データ メンバーを保護します。

##  <a name="setoriginalvalue"></a>  CMFCPropertyGridColorProperty::SetOriginalValue

編集可能なプロパティの元の値を設定します。

```
virtual void SetOriginalValue(const COleVariant& varValue);
```

### <a name="parameters"></a>パラメーター

*varValue*<br/>
[in]値。

### <a name="remarks"></a>Remarks

使用して、 [cmfcpropertygridproperty::resetoriginalvalue](../../mfc/reference/cmfcpropertygridproperty-class.md#resetoriginalvalue)編集済みのプロパティの元の値をリセットするメソッド。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl クラス](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty クラス](../../mfc/reference/cmfcpropertygridproperty-class.md)
