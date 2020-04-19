---
title: CMFCFontComboBox クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::CMFCFontComboBox
- AFXFONTCOMBOBOX/CMFCFontComboBox::GetSelFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::SelectFont
- AFXFONTCOMBOBOX/CMFCFontComboBox::Setup
- AFXFONTCOMBOBOX/CMFCFontComboBox::m_bDrawUsingFont
helpviewer_keywords:
- CMFCFontComboBox [MFC], CMFCFontComboBox
- CMFCFontComboBox [MFC], GetSelFont
- CMFCFontComboBox [MFC], SelectFont
- CMFCFontComboBox [MFC], Setup
- CMFCFontComboBox [MFC], m_bDrawUsingFont
ms.assetid: 9a53fb0c-7b45-486d-8187-2a4c723d9fbb
ms.openlocfilehash: 69e8f81e7e01d0610f3cbf88ac1725a21d59838f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505299"
---
# <a name="cmfcfontcombobox-class"></a>CMFCFontComboBox クラス

クラス`CMFCFontComboBox`は、フォントの一覧を含むコンボボックスコントロールを作成します。

## <a name="syntax"></a>構文

```
class CMFCFontComboBox : public CComboBox
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCFontComboBox::CMFCFontComboBox](#cmfcfontcombobox)|`CMFCFontComboBox` オブジェクトを構築します。|
|`CMFCFontComboBox::~CMFCFontComboBox`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCFontComboBox::CompareItem`|現在のフォントコンボボックスコントロールの並べ替えられたリストボックス内の新しい項目の相対位置を決定するために、フレームワークによって呼び出されます。 ( [CComboBox:: CompareItem](../../mfc/reference/ccombobox-class.md#compareitem)をオーバーライドします)。|
|`CMFCFontComboBox::DrawItem`|現在のフォントコンボボックスコントロール内の指定された項目を描画するために、フレームワークによって呼び出されます。 ( [CComboBox::D rawItem](../../mfc/reference/ccombobox-class.md#drawitem)をオーバーライドします)。|
|[CMFCFontComboBox::GetSelFont](#getselfont)|現在選択されているフォントに関する情報を取得します。|
|`CMFCFontComboBox::MeasureItem`|現在のフォントコンボボックスコントロールのリストボックスのサイズをウィンドウに通知するために、フレームワークによって呼び出されます。 ( [CComboBox:: MeasureItem](../../mfc/reference/ccombobox-class.md#measureitem)をオーバーライドします)。|
|`CMFCFontComboBox::PreTranslateMessage`|[TranslateMessage](/windows/win32/api/winuser/nf-winuser-translatemessage)および[DispatchMessage](/windows/win32/api/winuser/nf-winuser-dispatchmessage)の Windows 関数にディスパッチされる前に、ウィンドウメッセージを変換します。 ( [CWnd::PreTranslateMessage](../../mfc/reference/cwnd-class.md#pretranslatemessage)をオーバーライドします)。|
|[CMFCFontComboBox::SelectFont](#selectfont)|指定した条件に一致するフォントを [フォント] コンボボックスから選択します。|
|[CMFCFontComboBox:: セットアップ](#setup)|フォントコンボボックス内の項目のリストを初期化します。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCFontComboBox:: m_bDrawUsingFont](#m_bdrawusingfont)|現在のフォントコンボボックスに項目ラベルを描画するために使用するフォントをフレームワークに指示します。|

## <a name="remarks"></a>Remarks

ダイアログボックスで`CMFCFontComboBox`オブジェクトを使用するには、ダイアログ`CMFCFontComboBox`ボックスクラスに変数を追加します。 次に、 `OnInitDialog`ダイアログボックスクラスのメソッドで、 [cmfcfontcombobox:: Setup](#setup)メソッドを呼び出して、コンボボックスコントロール内の項目のリストを初期化します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CComboBox](../../mfc/reference/ccombobox-class.md)

[CMFCFontComboBox](../../mfc/reference/cmfcfontcombobox-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxfontcombobox

##  <a name="cmfcfontcombobox"></a>  CMFCFontComboBox::CMFCFontComboBox

`CMFCFontComboBox` オブジェクトを構築します。

```
CMFCFontComboBox();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getselfont"></a>  CMFCFontComboBox::GetSelFont

現在選択されているフォントに関する情報を取得します。

```
CMFCFontInfo* GetSelFont() const;
```

### <a name="return-value"></a>戻り値

フォントを記述する[CMFCFontInfo Class](../../mfc/reference/cmfcfontinfo-class.md)オブジェクトへのポインター。 コンボボックスでフォントが選択されていない場合、NULL になることがあります。

### <a name="remarks"></a>Remarks

##  <a name="m_bdrawusingfont"></a>CMFCFontComboBox:: m_bDrawUsingFont

現在のフォントコンボボックスに項目ラベルを描画するために使用するフォントをフレームワークに指示します。

```
static BOOL m_bDrawUsingFont;
```

### <a name="remarks"></a>Remarks

このメンバーを TRUE に設定すると、フレームワークは、各項目ラベルを描画するために同じフォントを使用するように指示されます。 このメンバーを FALSE に設定すると、名前がラベルと同じフォントで各項目ラベルを描画するようにフレームワークに指示します。 このメンバーの既定値は FALSE です。

##  <a name="selectfont"></a>  CMFCFontComboBox::SelectFont

指定した条件に一致するフォントを [フォント] コンボボックスから選択します。

```
BOOL SelectFont(CMFCFontInfo* pDesc);

BOOL SelectFont(
    LPCTSTR lpszName,
    BYTE nCharSet=DEFAULT_CHARSET);
```

### <a name="parameters"></a>パラメーター

*pDesc*<br/>
からフォント記述オブジェクトをポイントします。

*lpszName*<br/>
からフォント名を指定します。

*nCharSet*<br/>
から文字セットを指定します。 既定値は DEFAULT_CHARSET です。 詳細については、 `lfCharSet` [LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)構造体のメンバーを参照してください。

### <a name="return-value"></a>戻り値

フォントコンボボックスの項目が、指定したフォントの説明オブジェクトまたはフォント名と文字セットと一致する場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドを使用して、指定したフォントに対応するフォントコンボボックス内の項目を選択してスクロールします。

### <a name="example"></a>例

`CMFCFontComboBox`クラスの`SelectFont`メソッドを使用する方法を次の例に示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#35](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_2.cpp)]

##  <a name="setup"></a>  CMFCFontComboBox::Setup

フォントコンボボックス内の項目のリストを初期化します。

```
BOOL Setup(
    int nFontType=DEVICE_FONTTYPE|RASTER_FONTTYPE|TRUETYPE_FONTTYPE,
    BYTE nCharSet=DEFAULT_CHARSET,
    BYTE nPitchAndFamily=DEFAULT_PITCH);
```

### <a name="parameters"></a>パラメーター

*nFontType*<br/>
からフォントの種類を指定します。 既定値は、DEVICE_FONTTYPE、RASTER_FONTTYPE、および TRUETYPE_FONTTYPE のビットごとの組み合わせ (or) です。

*nCharSet*<br/>
からフォント文字セットを指定します。 既定値は DEFAULT_CHARSET です。

*nPitchAndFamily*<br/>
からフォントのピッチとファミリを指定します。 既定値は DEFAULT_PITCH です。

### <a name="return-value"></a>戻り値

フォントコンボボックスが正常に初期化された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、指定されたパラメーターに一致する現在インストールされているフォントを列挙し、それらのフォント名を [フォント] コンボボックスに挿入することにより、フォントコンボボックスを初期化します。

### <a name="example"></a>例

`CMFCFontComboBox`クラスの`Setup`メソッドを使用する方法を次の例に示します。 この例は、「[新しいコントロールのサンプル](../../overview/visual-cpp-samples.md)」の一部です。

[!code-cpp[NVC_MFC_NewControls#34](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_1.h)]
[!code-cpp[NVC_MFC_NewControls#36](../../mfc/reference/codesnippet/cpp/cmfcfontcombobox-class_3.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBarFontComboBox クラス](../../mfc/reference/cmfctoolbarfontcombobox-class.md)<br/>
[CMFCFontInfo クラス](../../mfc/reference/cmfcfontinfo-class.md)
