---
title: CMFCToolBarFontComboBox クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::CMFCToolBarFontComboBox
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::GetFontDesc
- AFXTOOLBARFONTCOMBOBOX/CMFCToolBarFontComboBox::SetFont
helpviewer_keywords:
- CMFCToolBarFontComboBox [MFC], CMFCToolBarFontComboBox
- CMFCToolBarFontComboBox [MFC], GetFontDesc
- CMFCToolBarFontComboBox [MFC], SetFont
ms.assetid: 25f8e08c-aadd-4cb5-9581-a99d49d444b1
ms.openlocfilehash: 7e19fc9257c1fe986ff09a8bbc86bf2fb55af7ee
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504746"
---
# <a name="cmfctoolbarfontcombobox-class"></a>CMFCToolBarFontComboBox クラス

ユーザーがシステムフォントの一覧からフォントを選択できるようにするコンボボックスコントロールを含むツールバーボタン。

## <a name="syntax"></a>構文

```
class CMFCToolBarFontComboBox : public CMFCToolBarComboBoxButton
```

## <a name="members"></a>メンバー

### <a name="protected-constructors"></a>プロテクト コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCToolBarFontComboBox:: CMFCToolBarFontComboBox](#cmfctoolbarfontcombobox)|`CMFCToolBarFontComboBox` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCToolBarFontComboBox::GetFontDesc](#getfontdesc)|コンボボックス内の指定`CMFCFontInfo`したインデックスのオブジェクトへのポインターを返します。|
|[CMFCToolBarFontComboBox::SetFont](#setfont)|フォントの名前、またはフォントのプレフィックスと文字セットに応じて、[フォント] コンボボックス内のフォントを選択します。|

### <a name="data-members"></a>データ メンバー

[CMFCToolBarFontComboBox:: m_nFontHeight](#m_nfontheight)<br/>
フォントコンボボックス内の文字の高さ。

## <a name="remarks"></a>Remarks

ツールバーにフォントコンボボックスボタンを追加するには、次の手順を実行します。

1. 親ツール バー リソースでボタンのダミー リソース ID を予約します。

1. `CMFCToolBarFontComboBox` オブジェクトを構築します。

1. AFX_WM_RESETTOOLBAR メッセージを処理するメッセージハンドラーで、 [Cmfctoolbar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)を使用して、元のボタンを新しいコンボボックスボタンに置き換えます。

1. [Cmfctoolbarfontcombobox:: SetFont](#setfont)メソッドを使用して、コンボボックスで選択されているフォントとドキュメント内のフォントを同期します。

ドキュメントのフォントとコンボボックスで選択したフォントを同期するには、 [Cmfctoolbarfontcombobox:: GetFontDesc](#getfontdesc)メソッドを使用して、選択したフォントの属性を取得し、これらの属性を使用して、 [CFont クラス](../../mfc/reference/cfont-class.md)オブジェクトを作成します。

フォントコンボボックスボタンは、Win32 関数[EnumFontFamiliesEx](/windows/win32/api/wingdi/nf-wingdi-enumfontfamiliesexw)を呼び出して、システムで使用できる画面とプリンターのフォントを決定します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCToolBarButton](../../mfc/reference/cmfctoolbarbutton-class.md)

[CMFCToolBarComboBoxButton](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)

[CMFCToolBarFontComboBox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxtoolbarfontcombobox

##  <a name="cmfctoolbarfontcombobox"></a>  CMFCToolBarFontComboBox::CMFCToolBarFontComboBox

[Cmfctoolbarfontcombobox](../../mfc/reference/cmfctoolbarfontcombobox-class.md)オブジェクトを構築します。

```
public:
CMFCToolBarFontComboBox(
    UINT uiID,
    int iImage,
    int nFontType = DEVICE_FONTTYPE | RASTER_FONTTYPE | TRUETYPE_FONTTYPE,
    BYTE nCharSet = DEFAULT_CHARSET,
    DWORD dwStyle = CBS_DROPDOWN,
    int iWidth = 0,
    BYTE nPitchAndFamily = DEFAULT_PITCH);

protected:
CMFCToolBarFontComboBox(
    CObList* pLstFontsExternal,
    int nFontType,
    BYTE nCharSet,
    BYTE nPitchAndFamily);

CMFCToolBarFontComboBox();
```

### <a name="parameters"></a>パラメーター

*uiID*<br/>
からコンボボックスのコマンド ID。

*iImage*<br/>
からツールバーイメージの0から始まるインデックス。 このイメージは、 [Cmfctoolbar クラス](../../mfc/reference/cmfctoolbar-class.md)クラスが保持する[cmfctoolbarimages クラス](../../mfc/reference/cmfctoolbarimages-class.md)オブジェクトに配置されています。

*nFontType*<br/>
からコンボボックスに含まれるフォントの種類。 このパラメーターは、次の値の組み合わせ (ブール値または) にすることができます。

DEVICE_FONTTYPE

RASTER_FONTTYPE

TRUETYPE_FONTTYPE

*nCharSet*<br/>
からDEFAULT_CHARSET に設定されている場合、コンボボックスにはすべての文字セットの一意の名前付きフォントがすべて含まれます。 (同じ名前のフォントが2つある場合、コンボボックスにはそのうちの1つが含まれます)。有効な文字セット値に設定されている場合、コンボボックスには、指定した文字セット内のフォントのみが表示されます。 使用可能な文字セットの一覧については、「 [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw) 」を参照してください。

*dwStyle*<br/>
からコンボボックスのスタイル。 (「[コンボボックススタイル」を](../../mfc/reference/styles-used-by-mfc.md#combo-box-styles)参照)

*iWidth*<br/>
からエディットコントロールの幅 (ピクセル単位)。

*nPitchAndFamily*<br/>
からDEFAULT_PITCH に設定すると、コンボボックスには、ピッチに関係なくフォントが表示されます。 FIXED_PITCH または VARIABLE_PITCH に設定した場合、コンボボックスには、そのピッチの種類を持つフォントのみが表示されます。 フォントファミリに基づくフィルター処理は現在サポートされていません。

*pLstFontsExternal*<br/>
入出力使用可能なフォントを格納する、 [CObList クラス](../../mfc/reference/coblist-class.md)オブジェクトへのポインター。

### <a name="remarks"></a>Remarks

通常、 `CMFCToolBarFontComboBox`オブジェクトは、使用可能なフォントのリストを 1 `CObList`つの共有オブジェクトに格納します。 コンストラクターの2番目のオーバーロードを使用し、 *pLstFontsExternal*への有効なポインターを`CMFCToolBarFontComboBox`指定すると、その`CObList`オブジェクトは、使用可能なフォントを使用して*pLstFontsExternal*をポイントするようになります。

### <a name="example"></a>例

次の例は、オブジェクトを`CMFCToolBarFontComboBox`構築する方法を示しています。 このコード スニペットは、 [Word パッド サンプル](../../overview/visual-cpp-samples.md)の一部です。

[!code-cpp[NVC_MFC_WordPad#7](../../mfc/reference/codesnippet/cpp/cmfctoolbarfontcombobox-class_1.cpp)]

##  <a name="getfontdesc"></a>  CMFCToolBarFontComboBox::GetFontDesc

コンボボックス内の指定`CMFCFontInfo`したインデックスのオブジェクトへのポインターを返します。

```
const CMFCFontInfo* GetFontDesc(int iIndex=-1) const;
```

### <a name="parameters"></a>パラメーター

*iIndex*<br/>
からコンボボックス項目の0から始まるインデックスを指定します。

### <a name="return-value"></a>戻り値

`CMFCFontInfo` オブジェクトへのポインター。 *IIndex*で有効な項目インデックスが指定されていない場合、戻り値は NULL になります。

##  <a name="m_nfontheight"></a>CMFCToolBarFontComboBox:: m_nFontHeight

コンボボックスにオーナー描画スタイルがある場合に、フォントコンボボックスの文字の高さ (ピクセル単位) を指定します。

```
static int m_nFontHeight
```

### <a name="remarks"></a>Remarks

`m_nFontHeight`変数が0の場合は、コンボボックスの既定のフォントに従って高さが自動的に計算されます。 高さには、ベースラインの上にある文字のアセントと、ベースラインの下にある文字のディセントの両方が含まれます。

##  <a name="setfont"></a>  CMFCToolBarFontComboBox::SetFont

パラメーターで指定したフォント名と文字セットに従って、[フォント] コンボボックス内のフォントを選択します。

```
BOOL SetFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET,
    BOOL bExact=FALSE);
```

### <a name="parameters"></a>パラメーター

*lpszName*<br/>
からフォント名またはプレフィックスを指定します。

*nCharSet*<br/>
から文字セットを指定します。

*bExact*<br/>
から*Lpszname*にフォント名またはフォントプレフィックスを含めるかどうかを指定します。

### <a name="return-value"></a>戻り値

フォントが正常に選択された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

*Bexact*が TRUE の場合、このメソッドは、指定した名前と完全に一致するフォントを*lpszname*として選択します。 *Bexact*が FALSE の場合、このメソッドは、指定されたテキストを*lpszname*として使用し、 *ncharset*として指定した文字セットを使用するフォントを選択します。 *Ncharset*が DEFAULT_CHARSET に設定されている場合、文字セットは無視され、 *lpszname*のみがフォントの選択に使用されます。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)<br/>
[CMFCToolBarButton クラス](../../mfc/reference/cmfctoolbarbutton-class.md)<br/>
[CMFCToolBarComboBoxButton クラス](../../mfc/reference/cmfctoolbarcomboboxbutton-class.md)<br/>
[CMFCFontInfo クラス](../../mfc/reference/cmfcfontinfo-class.md)<br/>
[CMFCToolBar:: ReplaceButton](../../mfc/reference/cmfctoolbar-class.md#replacebutton)<br/>
[チュートリアル: ツール バーへのコントロールの追加](../../mfc/walkthrough-putting-controls-on-toolbars.md)
