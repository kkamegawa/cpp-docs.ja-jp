---
title: CMFCPropertyGridFileProperty クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty
- AFXPROPERTYGRIDCTRL/CMFCPropertyGridFileProperty::CMFCPropertyGridFileProperty
helpviewer_keywords:
- CMFCPropertyGridFileProperty [MFC], CMFCPropertyGridFileProperty
ms.assetid: 2bb8b8b4-47fc-4798-bd5e-dc8ea0b4cd9d
ms.openlocfilehash: 4b64d18a67ea499c202b81481684227200846483
ms.sourcegitcommit: c3bf94210bdb73be80527166264d49e33784152c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/06/2019
ms.locfileid: "68821283"
---
# <a name="cmfcpropertygridfileproperty-class"></a>CMFCPropertyGridFileProperty クラス

クラス`CMFCPropertyGridFileProperty`は、[ファイルの選択] ダイアログボックスを開くプロパティリストコントロール項目をサポートしています。

## <a name="syntax"></a>構文

```
class CMFCPropertyGridFileProperty : public CMFCPropertyGridProperty
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCPropertyGridFileProperty:: CMFCPropertyGridFileProperty](#cmfcpropertygridfileproperty)|`CMFCPropertyGridFileProperty` オブジェクトを構築します。|
|`CMFCPropertyGridFileProperty::~CMFCPropertyGridFileProperty`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCPropertyGridFileProperty::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|`CMFCPropertyGridFileProperty::OnClickButton`|( [Cmfcpropertygridproperty:: OnClickButton](../../mfc/reference/cmfcpropertygridproperty-class.md#onclickbutton)をオーバーライドします)。|

### <a name="remarks"></a>Remarks

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCPropertyGridProperty](../../mfc/reference/cmfcpropertygridproperty-class.md)

[CMFCPropertyGridFileProperty](../../mfc/reference/cmfcpropertygridfileproperty-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxpropertygridctrl

##  <a name="cmfcpropertygridfileproperty"></a>CMFCPropertyGridFileProperty:: CMFCPropertyGridFileProperty

`CMFCPropertyGridFileProperty` オブジェクトを構築します。

```
CMFCPropertyGridFileProperty(
    const CString& strName,
    BOOL bOpenFileDialog,
    const CString& strFileName,
    LPCTSTR lpszDefExt=NULL,
    DWORD dwFlags=OFN_HIDEREADONLY|OFN_OVERWRITEPROMPT,
    LPCTSTR lpszFilter=NULL,
    LPCTSTR lpszDescr=NULL,
    DWORD_PTR dwData=0);
```

### <a name="parameters"></a>パラメーター

*strName*<br/>
からプロパティ名。

*Boペン Filedialog*<br/>
から **[ファイルを開く**] ダイアログボックスを開く場合は TRUE です。FALSE を選択すると、 **[ファイルの保存]** ダイアログボックスが開きます。

*strFileName*<br/>
から初期ファイル名。

*lpszDefExt*<br/>
から1つ以上のファイル名拡張子からなる文字列。 既定値は NULL です。

*dwFlags*<br/>
からダイアログボックスフラグ。 既定値は OFN_HIDEREADONLY と OFN_OVERWRITEPROMPT のビットごとの組み合わせ (OR) です。

*lpszFilter*<br/>
から1つ以上のファイルフィルターからなる文字列。 既定値は NULL です。

*lpszDescr*<br/>
からプロパティ項目の説明。 既定値は NULL です。

*dwData*<br/>
からプロパティ項目に関連付けられているアプリケーション固有のデータ。 たとえば、32 ビット整数またはその他のデータへのポインター。 既定値は 0 です。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

使用可能なフラグの完全な一覧については、「 [Openfilename 構造体](/windows/win32/api/commdlg/ns-commdlg-openfilenamew)」を参照してください。

### <a name="example"></a>例

次の例では、`CMFCPropertyGridFileProperty` クラスのコンストラクターを使用してオブジェクトを作成する方法を示します。 この例は、 [Visual Studio のデモサンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_VisualStudioDemo#22](../../mfc/codesnippet/cpp/cmfcpropertygridfileproperty-class_1.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCPropertyGridCtrl クラス](../../mfc/reference/cmfcpropertygridctrl-class.md)<br/>
[CMFCPropertyGridProperty クラス](../../mfc/reference/cmfcpropertygridproperty-class.md)
