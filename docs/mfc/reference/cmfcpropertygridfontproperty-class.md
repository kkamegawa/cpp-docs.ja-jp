---
title: CMFCPropertyGridFontProperty クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::CMFCPropertyGridFontProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetColor
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFontProperty::GetLogFont
helpviewer_keywords:
- CMFCPropertyGridFontProperty [MFC], CMFCPropertyGridFontProperty
- CMFCPropertyGridFontProperty [MFC], GetColor
- CMFCPropertyGridFontProperty [MFC], GetLogFont
ms.assetid: 83693f33-bbd3-4fcb-a9ad-fa79fcf2ca24
ms.openlocfilehash: a3c5b806482a97d64a9ffab92877781cb8778b6b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505122"
---
# <a name="cmfcpropertygridfontproperty-class"></a>CMFCPropertyGridFontProperty クラス

クラス`CMFCPropertyGridFileProperty`は、[フォントの選択] ダイアログボックスを開くプロパティリストコントロール項目をサポートしています。

## <a name="syntax"></a>構文

```
class CMFCPropertyGridFontProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCPropertyGridFontProperty:: CMFCPropertyGridFontProperty](#cmfcpropertygridfontproperty)|`CMFCPropertyGridFontProperty` オブジェクトを構築します。|
|`CMFCPropertyGridFontProperty::~CMFCPropertyGridFontProperty`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCPropertyGridFontProperty::FormatProperty`|プロパティ値のテキスト表現の書式を設定します ( [Cmfcpropertygridproperty:: formatproperty](../../mfc/reference/cmfcpropertygridproperty-class.md#formatproperty)をオーバーライドします)。|
|[CMFCPropertyGridFontProperty:: GetColor](#getcolor)|ユーザーが [フォント] ダイアログボックスから選択したフォントの色を取得します。|
|[CMFCPropertyGridFontProperty:: GetLogFont](#getlogfont)|ユーザーが [フォント] ダイアログボックスから選択したフォントを取得します。|
|`CMFCPropertyGridFontProperty::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|`CMFCPropertyGridFontProperty::OnClickButton`|プロパティに含まれているボタンをユーザーがクリックすると、フレームワークによって呼び出されます ( [Cmfcpropertygridproperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)をオーバーライドします)。|

## <a name="remarks"></a>Remarks

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFontProperty](../../mfc/reference/cmfcpropertygridfontproperty-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpropertygridctrl

##  <a name="cmfcpropertygridfontproperty"></a>CMFCPropertyGridFontProperty:: CMFCPropertyGridFontProperty

`CMFCPropertyGridFontProperty` オブジェクトを構築します。

```
CMFCPropertyGridFontProperty(
    const CString& strName,
    LOGFONT& lf,
    DWORD dwFontDialogFlags = CF_EFFECTS | CF_SCREENFONTS,
    LPCTSTR lpszDescr = NULL,
    DWORD_PTR dwData = 0,
    COLORREF color = (COLORREF)-1);
```

### <a name="parameters"></a>パラメーター

*strName*<br/>
からプロパティの名前。

*lf*<br/>
からフォントの属性を指定する論理フォント構造。

*Dwfontのフラグ*<br/>
から[プロパティ値] ドロップダウンボタンをクリックしたときに表示される [フォント] ダイアログボックスに適用されるスタイルです。 既定値は、CF_EFFECTS と CF_SCREENFONTS のビットごとの組み合わせ (or) です。 詳細については、[[フォント構造](/windows/win32/api/commdlg/ns-commdlg-choosefontw)の指定] の*Flags*パラメーターを参照してください。

*lpszDescr*<br/>
からフォントプロパティの説明。 既定値は NULL です。

*dwData*<br/>
から整数や、プロパティに関連付けられている他のデータへのポインターなど、アプリケーション固有のデータ。 既定値は 0 です。

*色*<br/>
からフォントの色。 既定値は既定の色です。

### <a name="remarks"></a>Remarks

オブジェクト`CMFCPropertyGridFontProperty`は、プロパティグリッドのフォントコントロールのフォントプロパティを表します。

### <a name="example"></a>例

`CMFCPropertyGridFontProperty`クラスのオブジェクトを構築する方法を次の例に示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#26](../../mfc/reference/codesnippet/cpp/cmfcpropertygridfontproperty-class_1.cpp)]

##  <a name="getcolor"></a>CMFCPropertyGridFontProperty:: GetColor

ユーザーが [フォント] ダイアログボックスから選択したフォントの色を取得します。

```
COLORREF GetColor() const;
```

### <a name="return-value"></a>戻り値

選択したフォントの色を表す RGB カラー値。

### <a name="remarks"></a>Remarks

##  <a name="getlogfont"></a>  CMFCPropertyGridFontProperty::GetLogFont

ユーザーが [フォント] ダイアログボックスから選択したフォントを取得します。

```
LPLOGFONT GetLogFont();
```

### <a name="return-value"></a>戻り値

選択されたフォントを記述する[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)構造体へのポインター。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl クラス](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty クラス](../../mfc/reference/cmfcpropertygridproperty-class.md)
