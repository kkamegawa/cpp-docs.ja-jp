---
title: CMFCFontInfo クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::GetFullName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nCharSet
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nPitchAndFamily
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_nType
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strName
- AFXTOOLBARFONTCOMBOBOX/CMFCFontInfo::m_strScript
helpviewer_keywords:
- CMFCFontInfo [MFC], GetFullName
- CMFCFontInfo [MFC], m_nCharSet
- CMFCFontInfo [MFC], m_nPitchAndFamily
- CMFCFontInfo [MFC], m_nType
- CMFCFontInfo [MFC], m_strName
- CMFCFontInfo [MFC], m_strScript
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
ms.openlocfilehash: a27606b494b13cd7b50f01b38fa95a918bacc7aa
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505272"
---
# <a name="cmfcfontinfo-class"></a>CMFCFontInfo クラス

クラス`CMFCFontInfo`は、フォントの名前とその他の属性を記述します。

## <a name="syntax"></a>構文

```
class CMFCFontInfo : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCFontInfo`|`CMFCFontInfo` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCFontInfo::GetFullName](#getfullname)|フォントとその文字セット (スクリプト) の連結された名前を取得します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCFontInfo::m_nCharSet](#m_ncharset)|フォントに関連付けられている文字セット (スクリプト) を示す値です。|
|[CMFCFontInfo::m_nPitchAndFamily](#m_npitchandfamily)|フォントのピッチとファミリを指定する値。|
|[CMFCFontInfo::m_nType](#m_ntype)|フォントの種類を指定する値。|
|[CMFCFontInfo::m_strName](#m_strname)|フォントの名前。たとえば、 **Arial**のようにします。|
|[CMFCFontInfo::m_strScript](#m_strscript)|フォントに関連付けられている文字セット (スクリプト) の名前。|

## <a name="remarks"></a>Remarks

オブジェクトは`CMFCFontInfo` 、 [cmfctoolbarfontcombobox クラス](../../mfc/reference/cmfctoolbarfontcombobox-class.md)クラスの項目にアタッチできます。 [Cmfctoolbarfontcombobox:: GetFontDesc](../../mfc/reference/cmfctoolbarfontcombobox-class.md#getfontdesc)メソッドを呼び出して、 `CMFCFontInfo`オブジェクトへのポインターを取得します。

## <a name="example"></a>例

`CMFCFontInfo`クラスのさまざまなメンバーを使用する方法を次の例に示します。 この例では、 `CMFCFontInfo` `CMFCRibbonFontComboBox`からオブジェクトを取得する方法と、そのローカル変数にアクセスする方法を示します。 この例は、 [MSOffice 2007 Demo サンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/cpp/cmfcfontinfo-class_1.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbarfontcombobox

##  <a name="cmfcfontinfo"></a>  CMFCFontInfo::CMFCFontInfo

`CMFCFontInfo` オブジェクトを構築します。

```
CMFCFontInfo(
    LPCTSTR lpszName,
    LPCTSTR lpszScript,
    BYTE nCharSet,
    BYTE nPitchAndFamily,
    int nType);

CMFCFontInfo(const CMFCFontInfo& src);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
からフォントの名前。 詳細については、 `lfFaceName` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)構造体のメンバーを参照してください。

*lpszScript*<br/>
からフォントのスクリプト (文字セット) の名前。

*nCharSet*<br/>
からフォントの文字セット (スクリプト) を指定する値。 詳細については、 `lfCharSet` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)構造体のメンバーを参照してください。

*nPitchAndFamily*<br/>
からフォントのピッチとファミリを指定する値。 詳細については、 `lfPitchAndFamily` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)構造体のメンバーを参照してください。

*nType*<br/>
からフォントの種類を示す値です。 このパラメーターには、DEVICE_FONTTYPE、RASTER_FONTTYPE、および TRUETYPE_FONTTYPE のビットごとの組み合わせ (or) を指定できます。

*src*<br/>
から`CMFCFontInfo` この`CMFCFontInfo`オブジェクトを構築するために使用されるメンバーを持つ既存のオブジェクト。

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

このドキュメントでは、*文字セット*と*スクリプト*を同義に使用します。 *スクリプト*は、書記体系とも呼ばれ、1つ以上の言語でこれらの文字を書き込むための文字とルールのコレクションです。 文字のコレクションには、そのスクリプトで使用されるアルファベットと句読点が含まれます。 たとえば、Latin スクリプトは米国で話される英語に使用され、アルファベットに A ~ Z の文字が含まれます。[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) `lfCharSet`構造体のメンバーは、文字セットを指定します。 たとえば、UI GOTHIC という値は、ラテン語スクリプトのアルファベットを含む ANSI 文字セットを指定します。

##  <a name="getfullname"></a>  CMFCFontInfo::GetFullName

フォントとその文字セット (スクリプト) の連結された名前を取得します。

```
CString GetFullName() const;
```

### <a name="return-value"></a>戻り値

フォント名とスクリプトを含む文字列。

### <a name="remarks"></a>Remarks

このメソッドを使用して、フォントの完全な名前を取得します。 たとえば、フォント名が**arial**で、フォントスクリプトが**キリル文字**の場合、このメソッドは "arial (キリル)" を返します。

##  <a name="m_ncharset"></a>CMFCFontInfo::m_nCharSet

フォントに関連付けられている文字セット (スクリプト) を示す値です。

```
const BYTE m_nCharSet;
```

### <a name="remarks"></a>Remarks

詳細については、 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)コンストラクターの*ncharset*パラメーターを参照してください。

##  <a name="m_npitchandfamily"></a>CMFCFontInfo::m_nPitchAndFamily

フォントのピッチ (ポイントサイズ) とファミリ (セリフ、sans serif、および等幅) を指定する値。

```
const BYTE m_nPitchAndFamily;
```

### <a name="remarks"></a>Remarks

詳細については、 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)コンストラクターの*nPitchAndFamily*パラメーターを参照してください。

##  <a name="m_ntype"></a>  CMFCFontInfo::m_nType

フォントの種類を指定する値。

```
const int m_nType;
```

### <a name="remarks"></a>Remarks

詳細については、 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)コンストラクターの*nType*パラメーターを参照してください。

##  <a name="m_strname"></a>  CMFCFontInfo::m_strName

フォントの名前。たとえば、 **Arial**です。

```
const CString m_strName;
```

### <a name="remarks"></a>Remarks

詳細については、 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)コンストラクターの*lpszname*パラメーターを参照してください。

##  <a name="m_strscript"></a>  CMFCFontInfo::m_strScript

フォントに関連付けられている文字セット (スクリプト) の名前。

```
const CString m_strScript;
```

### <a name="remarks"></a>Remarks

詳細については、 [CMFCFontInfo:: CMFCFontInfo](#cmfcfontinfo)コンストラクターの*lpszscript*パラメーターを参照してください。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox クラス](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCToolBarFontSizeComboBox クラス](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)
