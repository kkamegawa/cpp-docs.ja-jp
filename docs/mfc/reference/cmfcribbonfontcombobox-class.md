---
title: CMFCRibbonFontComboBox クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::CMFCRibbonFontComboBox
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::BuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetCharSet
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontDesc
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetFontType
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::GetPitchAndFamily
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::RebuildFonts
- AFXRIBBONCOMBOBOX/CMFCRibbonFontComboBox::SetFont
helpviewer_keywords:
- CMFCRibbonFontComboBox [MFC], CMFCRibbonFontComboBox
- CMFCRibbonFontComboBox [MFC], BuildFonts
- CMFCRibbonFontComboBox [MFC], GetCharSet
- CMFCRibbonFontComboBox [MFC], GetFontDesc
- CMFCRibbonFontComboBox [MFC], GetFontType
- CMFCRibbonFontComboBox [MFC], GetPitchAndFamily
- CMFCRibbonFontComboBox [MFC], RebuildFonts
- CMFCRibbonFontComboBox [MFC], SetFont
ms.assetid: 33b4db50-df4f-45fa-8f05-2e6e73c31435
ms.openlocfilehash: 186c4bc3e1b26529ed0e000d2893e1b2d81c4304
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504967"
---
# <a name="cmfcribbonfontcombobox-class"></a>CMFCRibbonFontComboBox クラス

フォントの一覧を含むコンボ ボックスを実装します。 このコンボ ボックスをリボン パネルに配置できます。

## <a name="syntax"></a>構文

```
class CMFCRibbonFontComboBox : public CMFCRibbonComboBox
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|`CMFCRibbonFontComboBox::~CMFCRibbonFontComboBox`|デストラクターです。|

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonFontComboBox::CMFCRibbonFontComboBox](#cmfcribbonfontcombobox)|`CMFCRibbonFontComboBox` オブジェクトを構築して初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonFontComboBox:: BuildFonts](#buildfonts)|リボンのフォント コンボ ボックスに、指定されたフォントの種類、文字セット、ピッチ、ファミリのフォントを設定します。|
|`CMFCRibbonFontComboBox::CreateObject`|このクラス型の動的インスタンスを作成するために、フレームワークで使用されます。|
|[CMFCRibbonFontComboBox::GetCharSet](#getcharset)|指定された文字セットを返します。|
|[CMFCRibbonFontComboBox::GetFontDesc](#getfontdesc)||
|[CMFCRibbonFontComboBox::GetFontType](#getfonttype)|コンボ ボックスに表示するフォントの種類を返します。 有効なオプションは、DEVICE_FONTTYPE、RASTER_FONTTYPE、TRUETYPE_FONTTYPE、またはそのビットごとの任意の組み合わせです。|
|[CMFCRibbonFontComboBox::GetPitchAndFamily](#getpitchandfamily)|コンボ ボックスに表示されるフォントのピッチとファミリを返します。|
|`CMFCRibbonFontComboBox::GetThisClass`|このクラス型に関連付けられている[CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)オブジェクトへのポインターを取得するために、フレームワークによって使用されます。|
|[CMFCRibbonFontComboBox::RebuildFonts](#rebuildfonts)|リボンのフォント コンボ ボックスに、以前に指定されたフォントの種類、文字セット、ピッチ、ファミリのフォントを設定します。|
|[CMFCRibbonFontComboBox::SetFont](#setfont)|コンボ ボックスで、指定されたフォントを選択します。|

## <a name="remarks"></a>Remarks

オブジェクトを`CMFCRibbonFontComboBox`作成した後、 [CMFCRibbonPanel:: add](../../mfc/reference/cmfcribbonpanel-class.md#add)を呼び出して、オブジェクトをリボンパネルに追加します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)

[CMFCRibbonComboBox](../../mfc/reference/cmfcribboncombobox-class.md)

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonComboBox

##  <a name="buildfonts"></a>  CMFCRibbonFontComboBox::BuildFonts

リボンのコンボボックスにフォントを設定します。

```
void BuildFonts(
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH);
```

### <a name="parameters"></a>パラメーター

*nFontType*<br/>
から追加するフォントのフォントの種類を指定します。

*nCharSet*<br/>
から追加するフォントの文字セットを指定します。

*nPitchAndFamily*<br/>
から追加するフォントのピッチとファミリを指定します。

##  <a name="cmfcribbonfontcombobox"></a>  CMFCRibbonFontComboBox::CMFCRibbonFontComboBox

[CMFCRibbonFontComboBox](../../mfc/reference/cmfcribbonfontcombobox-class.md)オブジェクトを構築し、初期化します。

```
CMFCRibbonFontComboBox(
    UINT nID,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    BYTE nPitchAndFamily = DEFAULT_PITCH,
    int nWidth = -1);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
からユーザーがコンボボックスから項目を選択したときに実行されるコマンドのコマンド ID です。

*nFontType*<br/>
からコンボボックスに表示するフォントの種類を指定します。 有効なオプションは、DEVICE_FONTTYPE、RASTER_FONTTYPE、TRUETYPE_FONTTYPE、またはそのビットごとの任意の組み合わせです。

*nCharSet*<br/>
からコンボボックス内のフォントを、指定した文字セットに属するフォントにフィルター処理します。

*nPitchAndFamily*<br/>
からコンボボックスに表示されるフォントのピッチとファミリを指定します。

*nWidth*<br/>
からコンボボックスの幅をピクセル単位で指定します。

### <a name="remarks"></a>Remarks

使用可能な*Nfonttype*パラメーター値の詳細については、Windows SDK のドキュメントの「 [EnumFontFamProc](/previous-versions/dd162621\(v=vs.85\)) 」を参照してください。

*Ncharset*に割り当てることができる有効な文字セットと、 *nPitchAndFamily*に割り当てることができる有効な値の詳細については、Windows SDK のドキュメントの「 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 」を参照してください。

##  <a name="getfontdesc"></a>  CMFCRibbonFontComboBox::GetFontDesc

詳細については、Visual Studio のインストール**の\\VC atlmfc\\\\src mfc**フォルダーにあるソースコードを参照してください。

```
const CMFCFontInfo* GetFontDesc(int iIndex = -1) const;
```

### <a name="parameters"></a>パラメーター

から*iIndex*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="rebuildfonts"></a>  CMFCRibbonFontComboBox::RebuildFonts

以前に指定したフォントの種類、文字セット、およびピッチとファミリのフォントをリボンのコンボボックスに設定します。

```
void RebuildFonts();
```

### <a name="remarks"></a>Remarks

このクラスの[コンストラクター](#cmfcribbonfontcombobox)の [リボンフォント] コンボボックスに含めるフォントの種類、文字セット、およびピッチとファミリを指定することも、 [CMFCRibbonFontComboBox:: buildfonts](#buildfonts)を呼び出すこともできます。

##  <a name="setfont"></a>  CMFCRibbonFontComboBox::SetFont

コンボ ボックスで、指定されたフォントを選択します。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet = DEFAULT_CHARSET,
    BOOL bExact = FALSE);
```

### <a name="parameters"></a>パラメーター

' lpszName * 選択するフォントの名前を指定します。

*nCharSet*<br/>
選択したフォントの文字セットを指定します。

*bExact*<br/>
フォントを選択するときに文字セットが一致する必要があることを指定する場合は TRUE。フォントを選択するときに文字セットを無視できることを指定する場合は FALSE。

### <a name="return-value"></a>戻り値

指定したフォントが見つかり、選択された場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

##  <a name="getcharset"></a>  CMFCRibbonFontComboBox::GetCharSet

指定された文字セットを返します。

```
BYTE GetCharSet() const;
```

### <a name="return-value"></a>戻り値

文字セット (Windows SDK のドキュメントの「LOGFONT」を参照してください)。

### <a name="remarks"></a>Remarks

##  <a name="getfonttype"></a>  CMFCRibbonFontComboBox::GetFontType

コンボ ボックスに表示するフォントの種類を返します。 有効なオプションは、DEVICE_FONTTYPE、RASTER_FONTTYPE、TRUETYPE_FONTTYPE、またはそのビットごとの任意の組み合わせです。

```
int GetFontType() const;
```

### <a name="return-value"></a>戻り値

フォントの種類 (Windows SDK ドキュメントの「EnumFontFamProc」を参照してください)。

### <a name="remarks"></a>Remarks

##  <a name="getpitchandfamily"></a>  CMFCRibbonFontComboBox::GetPitchAndFamily

コンボ ボックスに表示されるフォントのピッチとファミリを返します。

```
BYTE GetPitchAndFamily() const;
```

### <a name="return-value"></a>戻り値

ピッチとファミリ (Windows SDK のドキュメントの「LOGFONT」を参照してください)。

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonComboBox クラス](../../mfc/reference/cmfcribboncombobox-class.md)
