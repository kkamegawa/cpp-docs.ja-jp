---
title: CMFCCaptionBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar
- AFXCAPTIONBAR/CMFCCaptionBar::Create
- AFXCAPTIONBAR/CMFCCaptionBar::DoesAllowDynInsertBefore
- AFXCAPTIONBAR/CMFCCaptionBar::EnableButton
- AFXCAPTIONBAR/CMFCCaptionBar::GetAlignment
- AFXCAPTIONBAR/CMFCCaptionBar::GetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::GetButtonRect
- AFXCAPTIONBAR/CMFCCaptionBar::GetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::IsMessageBarMode
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveButton
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveIcon
- AFXCAPTIONBAR/CMFCCaptionBar::RemoveText
- AFXCAPTIONBAR/CMFCCaptionBar::SetBitmap
- AFXCAPTIONBAR/CMFCCaptionBar::SetBorderSize
- AFXCAPTIONBAR/CMFCCaptionBar::SetButton
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonPressed
- AFXCAPTIONBAR/CMFCCaptionBar::SetButtonToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetFlatBorder
- AFXCAPTIONBAR/CMFCCaptionBar::SetIcon
- AFXCAPTIONBAR/CMFCCaptionBar::SetImageToolTip
- AFXCAPTIONBAR/CMFCCaptionBar::SetMargin
- AFXCAPTIONBAR/CMFCCaptionBar::SetText
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBackground
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawBorder
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawButton
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawImage
- AFXCAPTIONBAR/CMFCCaptionBar::OnDrawText
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBackground
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarBorder
- AFXCAPTIONBAR/CMFCCaptionBar::m_clrBarText
helpviewer_keywords:
- CMFCCaptionBar [MFC], Create
- CMFCCaptionBar [MFC], DoesAllowDynInsertBefore
- CMFCCaptionBar [MFC], EnableButton
- CMFCCaptionBar [MFC], GetAlignment
- CMFCCaptionBar [MFC], GetBorderSize
- CMFCCaptionBar [MFC], GetButtonRect
- CMFCCaptionBar [MFC], GetMargin
- CMFCCaptionBar [MFC], IsMessageBarMode
- CMFCCaptionBar [MFC], RemoveBitmap
- CMFCCaptionBar [MFC], RemoveButton
- CMFCCaptionBar [MFC], RemoveIcon
- CMFCCaptionBar [MFC], RemoveText
- CMFCCaptionBar [MFC], SetBitmap
- CMFCCaptionBar [MFC], SetBorderSize
- CMFCCaptionBar [MFC], SetButton
- CMFCCaptionBar [MFC], SetButtonPressed
- CMFCCaptionBar [MFC], SetButtonToolTip
- CMFCCaptionBar [MFC], SetFlatBorder
- CMFCCaptionBar [MFC], SetIcon
- CMFCCaptionBar [MFC], SetImageToolTip
- CMFCCaptionBar [MFC], SetMargin
- CMFCCaptionBar [MFC], SetText
- CMFCCaptionBar [MFC], OnDrawBackground
- CMFCCaptionBar [MFC], OnDrawBorder
- CMFCCaptionBar [MFC], OnDrawButton
- CMFCCaptionBar [MFC], OnDrawImage
- CMFCCaptionBar [MFC], OnDrawText
- CMFCCaptionBar [MFC], m_clrBarBackground
- CMFCCaptionBar [MFC], m_clrBarBorder
- CMFCCaptionBar [MFC], m_clrBarText
ms.assetid: acb54d5f-14ff-4c96-aeb3-7717cf566d9a
ms.openlocfilehash: c6385cb6bd3eec3ce5fefe0475d771c774777820
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403842"
---
# <a name="cmfccaptionbar-class"></a>CMFCCaptionBar クラス

A`CMFCCaptionBar`オブジェクトは 3 つの要素を表示できるコントロール バー: ボタン、テキスト ラベル、およびビットマップ。 表示できる各要素の数は 1 つずつです。 各要素は、コントロールの左端、右端、または中央に揃えて配置できます。 また、キャプション バーの上部または下部の境界線にフラット スタイルまたは 3D スタイルを適用することもできます。

## <a name="syntax"></a>構文

```
class CMFCCaptionBar : public CPane
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCCaptionBar::Create](#create)|キャプション バー コントロールを作成しにアタッチします、`CMFCCaptionBar`オブジェクト。|
|[CMFCCaptionBar::DoesAllowDynInsertBefore](#doesallowdyninsertbefore)|キャプション バーとその親フレームの間の別のウィンドウを動的に挿入するかどうかを示します。 (上書き[cbasepane::doesallowdyninsertbefore](../../mfc/reference/cbasepane-class.md#doesallowdyninsertbefore))。|
|[CMFCCaptionBar::EnableButton](#enablebutton)|有効またはキャプション バーにあるボタンを無効にします。|
|[CMFCCaptionBar::GetAlignment](#getalignment)|指定した要素の配置を返します。|
|[CMFCCaptionBar::GetBorderSize](#getbordersize)|キャプション バーの境界線のサイズを返します。|
|[CMFCCaptionBar::GetButtonRect](#getbuttonrect)|キャプション バーのボタンの外接する四角形を取得します。|
|[CMFCCaptionBar::GetMargin](#getmargin)|キャプション バーの要素の端とキャプション バー コントロールの端との間の距離を返します。|
|[CMFCCaptionBar::IsMessageBarMode](#ismessagebarmode)|キャプション バーが、メッセージ バー モードかどうかを指定します。|
|[CMFCCaptionBar::RemoveBitmap](#removebitmap)|キャプション バーからビットマップ イメージを削除します。|
|[CMFCCaptionBar::RemoveButton](#removebutton)|キャプション バーから、ボタンを削除します。|
|[CMFCCaptionBar::RemoveIcon](#removeicon)|キャプション バーからアイコンを削除します。|
|[CMFCCaptionBar::RemoveText](#removetext)|キャプション バーからテキスト ラベルを削除します。|
|[CMFCCaptionBar::SetBitmap](#setbitmap)|キャプション バーのビットマップ イメージを設定します。|
|[CMFCCaptionBar::SetBorderSize](#setbordersize)|キャプション バーの境界線のサイズを設定します。|
|[CMFCCaptionBar::SetButton](#setbutton)|キャプション バーのボタンを設定します。|
|[CMFCCaptionBar::SetButtonPressed](#setbuttonpressed)|ボタンが押された状態のままになるかどうかを指定します。|
|[CMFCCaptionBar::SetButtonToolTip](#setbuttontooltip)|ボタンのツールヒントを設定します。|
|[CMFCCaptionBar::SetFlatBorder](#setflatborder)|キャプション バーの境界線スタイルを設定します。|
|[CMFCCaptionBar::SetIcon](#seticon)|キャプション バーのアイコンを設定します。|
|[CMFCCaptionBar::SetImageToolTip](#setimagetooltip)|キャプション バーのイメージのツールヒントを設定します。|
|[CMFCCaptionBar::SetMargin](#setmargin)|キャプション バーの要素の端とキャプション バー コントロールの端との間の距離を設定します。|
|[CMFCCaptionBar::SetText](#settext)|キャプション バーのテキスト ラベルを設定します。|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCCaptionBar::OnDrawBackground](#ondrawbackground)|キャプション バーの背景を塗りつぶすために、フレームワークによって呼び出されます。|
|[CMFCCaptionBar::OnDrawBorder](#ondrawborder)|キャプション バーの境界線を描画するためにフレームワークによって呼び出されます。|
|[CMFCCaptionBar::OnDrawButton](#ondrawbutton)|キャプション バーのボタンを描画するためにフレームワークによって呼び出されます。|
|[CMFCCaptionBar::OnDrawImage](#ondrawimage)|キャプション バーの画像を描画するためにフレームワークによって呼び出されます。|
|[CMFCCaptionBar::OnDrawText](#ondrawtext)|キャプション バーのテキストを描画するためにフレームワークによって呼び出されます。|

### <a name="data-members"></a>データ メンバー

|名前|説明|
|----------|-----------------|
|[CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)|キャプション バーの背景色。|
|[CMFCCaptionBar::m_clrBarBorder](#m_clrbarborder)|キャプション バーの境界線の色。|
|[CMFCCaptionBar::m_clrBarText](#m_clrbartext)|キャプション バーのテキストの色。|

## <a name="remarks"></a>Remarks

キャプション バーを作成するには、次の手順を実行します。

1. 構築、`CMFCCaptionBar`オブジェクト。 通常、キャプション バーをフレーム ウィンドウ クラスに追加します。

1. 呼び出す、 [CMFCCaptionBar::Create](#create)キャプション バー コントロールを作成し、アタッチ先メソッドを`CMFCCaptionBar`オブジェクト。

1. 呼び出す[CMFCCaptionBar::SetButton](#setbutton)、 [CMFCCaptionBar::SetText](#settext)、 [CMFCCaptionBar::SetIcon](#seticon)、および[CMFCCaptionBar::SetBitmap](#setbitmap)キャプション バーの要素を設定します。

ボタンの要素を設定すると、ボタンをコマンド ID を割り当てる必要があります。 ユーザーは、ボタンをクリックすると、キャプション バーを親フレーム ウィンドウにこの ID を持つ WM_COMMAND メッセージをルーティングします。

キャプション バーは、Microsoft Office 2007 アプリケーションで表示されるメッセージ バーにエミュレートするメッセージ バー モードで操作もできます。 ビットマップ、メッセージ、およびボタン (通常は、ダイアログ ボックスが開きます。) メッセージ バー モード、キャプション バーに表示されます。ビットマップにツールヒントを割り当てることができます。

メッセージ バー モードを有効にするのには、呼び出す[CMFCCaptionBar::Create](#create) (bIsMessageBarMode) の 4 番目のパラメーターを TRUE に設定します。

## <a name="example"></a>例

`CMFCCaptionBar` クラスのさまざまなメソッドの使用方法を次の例に示します。 キャプション バー コントロールを作成、キャプション バーの 3D 境界線を設定、キャプション バーの要素の端とキャプション バー コントロールの端の間隔をピクセル単位で距離を設定、キャプション バーのボタンを設定する方法を示します、、ボタンのツールヒントを設定、キャプション バーのテキスト ラベルを設定、ビットマップ イメージのキャプション バーの設定、およびキャプション バーにイメージのツールヒントを設定します。 このコード スニペットの一部、 [MS Office 2007 のデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_MSOffice2007Demo#1](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_1.h)]
[!code-cpp[NVC_MFC_MSOffice2007Demo#2](../../mfc/reference/codesnippet/cpp/cmfccaptionbar-class_2.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CMFCCaptionBar](../../mfc/reference/cmfccaptionbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcaptionbar.h

##  <a name="create"></a>  CMFCCaptionBar::Create

キャプション バー コントロールを作成しにアタッチします、`CMFCCaptionBar`オブジェクト。

```
BOOL Create(
    DWORD dwStyle,
    CWnd* pParentWnd,
    UINT uID,
    int nHeight=-1,
    BOOL bIsMessageBarMode=FALSE);
```

### <a name="parameters"></a>パラメーター

*dwStyle*<br/>
キャプション バーのスタイルの論理 OR の組み合わせ。

*pParentWnd*<br/>
キャプション バー コントロールの親ウィンドウ。

*uID*<br/>
キャプション バー コントロールの ID。

*nHeight*<br/>
キャプション バー コントロールのピクセル単位の高さ。 -1 の場合は、高さが、アイコン、テキスト、キャプション バー コントロールを表示するボタンの高さに基づいて計算されます。

*bIsMessageBarMode*<br/>
キャプション バーが、メッセージ バー モードでは、TRUE を返します。FALSE それ以外の場合。

### <a name="return-value"></a>戻り値

キャプション バー コントロールが正常に作成された場合は TRUE。FALSE それ以外の場合。

### <a name="remarks"></a>Remarks

構築する、 `CMFCCaptionBar` 2 つのステップ内のオブジェクト。 最初に、コンス トラクターを呼び出すしを呼び出して、`Create`メソッドでは、Windows コントロールを作成しにアタッチします、`CMFCCaptionBar`オブジェクト。

##  <a name="doesallowdyninsertbefore"></a>  CMFCCaptionBar::DoesAllowDynInsertBefore

キャプション バーとその親フレームの間の別のウィンドウを動的に挿入するかどうかを示します。

```
virtual BOOL DoesAllowDynInsertBefore() const;
```

### <a name="return-value"></a>戻り値

オーバーライドされない限り、FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="enablebutton"></a>  CMFCCaptionBar::EnableButton

有効またはキャプション バーにあるボタンを無効にします。

```
void EnableButton(BOOL bEnable=TRUE);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
[in]ボタンを無効に false の場合、ボタンを有効にする場合は TRUE。

##  <a name="getalignment"></a>  CMFCCaptionBar::GetAlignment

指定した要素の配置を返します。

```
BarElementAlignment GetAlignment(BarElement elem);
```

### <a name="parameters"></a>パラメーター

*elem*<br/>
[in]キャプション バーには、配置を取得するための要素が表示されます。

### <a name="return-value"></a>戻り値

ボタン、ビットマップ、テキスト、アイコンなどの要素の配置です。

### <a name="remarks"></a>Remarks

要素の配置には、次の値のいずれかを指定できます。

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="getbordersize"></a>  CMFCCaptionBar::GetBorderSize

キャプション バーの境界線のサイズを返します。

```
int GetBorderSize() const;
```

### <a name="return-value"></a>戻り値

枠線のピクセル単位のサイズ。

##  <a name="getbuttonrect"></a>  CMFCCaptionBar::GetButtonRect

キャプション バーのボタンの外接する四角形を取得します。

```
CRect GetButtonRect() const;
```

### <a name="return-value"></a>戻り値

A`CRect`キャプション バーのボタンの外接する四角形の座標を格納しているオブジェクト。

##  <a name="getmargin"></a>  CMFCCaptionBar::GetMargin

キャプション バーの要素の端とキャプション バー コントロールの端との間の距離を返します。

```
int GetMargin() const;
```

### <a name="return-value"></a>戻り値

キャプション バーの要素の端とキャプション バー コントロールの端の間隔をピクセル単位で距離です。

##  <a name="ismessagebarmode"></a>  CMFCCaptionBar::IsMessageBarMode

キャプション バーが、メッセージ バー モードかどうかを指定します。

```
BOOL IsMessageBarMode() const;
```

### <a name="return-value"></a>戻り値

キャプション バーが、メッセージ バー モードでは、TRUE を返します。FALSE それ以外の場合。

### <a name="remarks"></a>Remarks

メッセージ バー モードでは、キャプション バーには、ツールヒント、メッセージ テキスト、ボタンの画像が表示されます。

##  <a name="m_clrbarbackground"></a>  CMFCCaptionBar::m_clrBarBackground

キャプション バーの背景色。

```
COLORREF m_clrBarBackground
```

##  <a name="m_clrbarborder"></a>  CMFCCaptionBar::m_clrBarBorder

キャプション バーの境界線の色。

```
COLORREF m_clrBarBorder
```

##  <a name="m_clrbartext"></a>  CMFCCaptionBar::m_clrBarText

キャプション バーのテキストの色。

```
COLORREF m_clrBarText
```

##  <a name="ondrawbackground"></a>  CMFCCaptionBar::OnDrawBackground

キャプション バーの背景を塗りつぶすために、フレームワークによって呼び出されます。

```
virtual void OnDrawBackground(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]キャプション バーのデバイス コンテキストへのポインター。

*rect*<br/>
[in]外接する四角形を入力します。

### <a name="remarks"></a>Remarks

`OnDrawBackground`キャプション バーの背景が入力するときに、メソッドが呼び出されます。 既定の実装を使用して背景を塗りつぶす、 [CMFCCaptionBar::m_clrBarBackground](#m_clrbarbackground)色。

このメソッドをオーバーライドする`CMFCCaptionBar`キャプション バーの外観をカスタマイズするクラスを派生します。

##  <a name="ondrawborder"></a>  CMFCCaptionBar::OnDrawBorder

キャプション バーの境界線を描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawBorder(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]枠線の表示に使用されるデバイス コンテキストを指定します。

*rect*<br/>
[in]外接する四角形。

### <a name="remarks"></a>Remarks

既定では、罫線には、フラット スタイルが設定されています。

このメソッドをオーバーライドする`CMFCCaptionBar`キャプション バーの境界線の外観をカスタマイズするクラスを派生します。

##  <a name="ondrawbutton"></a>  CMFCCaptionBar::OnDrawButton

キャプション バーのボタンを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawButton(
    CDC* pDC,
    CRect rect,
    const CString& strButton,
    BOOL bEnabled);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]ボタンを表示するために使用しているデバイス コンテキストへのポインター。

*rect*<br/>
[in]ボタンの外接する四角形。

*strButton*<br/>
[in]ボタンのテキスト ラベル。

*bEnabled*<br/>
[in]は、ボタンが有効な場合は TRUE。FALSE それ以外の場合。

### <a name="remarks"></a>Remarks

このメソッドをオーバーライドする`CMFCCaptionBar`キャプション バーのボタンの外観をカスタマイズするクラスを派生します。

##  <a name="ondrawimage"></a>  CMFCCaptionBar::OnDrawImage

キャプション バーの画像を描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawImage(
    CDC* pDC,
    CRect rect);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]イメージを表示するために使用しているデバイス コンテキストへのポインター。

*rect*<br/>
[in]イメージの外接する四角形を指定します。

### <a name="remarks"></a>Remarks

このメソッドをオーバーライドする`CMFCCaptionBar`イメージの外観をカスタマイズするクラスを派生します。

##  <a name="ondrawtext"></a>  CMFCCaptionBar::OnDrawText

キャプション バーのテキストを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDrawText(
    CDC* pDC,
    CRect rect,
    const CString& strText);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]ボタンを表示するために使用しているデバイス コンテキストへのポインター。

*rect*<br/>
[in]テキストの外接する四角形。

*strText*<br/>
[in]表示するテキスト文字列。

### <a name="remarks"></a>Remarks

既定の実装を使用して、テキストを表示する`CDC::DrawText`と[CMFCCaptionBar::m_clrBarText](#m_clrbartext)色。

このメソッドをオーバーライドする`CMFCCaptionBar`キャプション バーのテキストの外観をカスタマイズするクラスを派生します。

##  <a name="removebitmap"></a>  CMFCCaptionBar::RemoveBitmap

キャプション バーからビットマップ イメージを削除します。

```
void RemoveBitmap();
```

##  <a name="removebutton"></a>  CMFCCaptionBar::RemoveButton

キャプション バーから、ボタンを削除します。

```
void RemoveButton();
```

### <a name="remarks"></a>Remarks

キャプション バーの要素のレイアウトは自動的に調整されます。

##  <a name="removeicon"></a>  CMFCCaptionBar::RemoveIcon

キャプション バーからアイコンを削除します。

```
void RemoveIcon();
```

##  <a name="removetext"></a>  CMFCCaptionBar::RemoveText

キャプション バーからテキスト ラベルを削除します。

```
void RemoveText();
```

##  <a name="setbitmap"></a>  CMFCCaptionBar::SetBitmap

キャプション バーのビットマップ イメージを設定します。

```
void SetBitmap(
    HBITMAP hBitmap,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);

void SetBitmap(
    UINT uiBmpResID,
    COLORREF clrTransparent,
    BOOL bStretch=FALSE,
    BarElementAlignment bmpAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>パラメーター

*hBitmap*<br/>
[in]設定するビットマップ ハンドル。

*clrTransparent*<br/>
[in]ビットマップの透明色を指定する RGB 値。

*bStretch*<br/>
[in]TRUE の場合、イメージの外接する四角形に収まらない場合、ビットマップが拡大します。 それ以外の場合、ビットマップは引き伸ばされません。

*bmpAlignment*<br/>
[in]ビットマップの配置です。

### <a name="remarks"></a>Remarks

キャプション バーにビットマップを設定するのにには、このメソッドを使用します。

前のビットマップは自動的に破棄されます。 キャプション バーにアイコンが表示されますを呼び出したためかどうか、 [CMFCCaptionBar::SetIcon](#seticon)メソッドを呼び出すことで、アイコンを削除しない限り、ビットマップは表示されません[CMFCCaptionBar::RemoveIcon](#removeicon)します。

ビットマップの配置の指定に従って、 *bmpAlignment*パラメーター。  このパラメーターには、次の `BarElementAlignment` 値のいずれかを指定できます。

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setbordersize"></a>  CMFCCaptionBar::SetBorderSize

キャプション バーの境界線のサイズを設定します。

```
void SetBorderSize(int nSize);
```

### <a name="parameters"></a>パラメーター

*nSize*<br/>
[in]新しいサイズ (ピクセル)、キャプション バーの境界線。

##  <a name="setbutton"></a>  CMFCCaptionBar::SetButton

キャプション バーのボタンを設定します。

```
void SetButton(
    LPCTSTR lpszLabel,
    UINT uiCmdUI,
    BarElementAlignment btnAlignmnet=ALIGN_LEFT,
    BOOL bHasDropDownArrow=TRUE);
```

### <a name="parameters"></a>パラメーター

*lpszLabel*<br/>
ボタンのコマンドのラベル。

*uiCmdUI*<br/>
ボタンのコマンド id。

*btnAlignmnet*<br/>
ボタンの配置。

*bHasDropDownArrow*<br/>
TRUE の場合、ボタンを表示するドロップダウン矢印を FALSE それ以外の場合。

##  <a name="setbuttonpressed"></a>  CMFCCaptionBar::SetButtonPressed

ボタンが押された状態のままになるかどうかを指定します。

```
void SetButtonPressed(BOOL bPresed=TRUE);
```

### <a name="parameters"></a>パラメーター

*bPresed*<br/>
ボタンがそれ以外の場合、押された状態、FALSE を保持した場合は TRUE。

##  <a name="setbuttontooltip"></a>  CMFCCaptionBar::SetButtonToolTip

ボタンのツールヒントを設定します。

```
void SetButtonToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszToolTip*<br/>
[in]ツールヒントのキャプション。

*lpszDescription*<br/>
[in]ツールヒントの説明。

##  <a name="setflatborder"></a>  CMFCCaptionBar::SetFlatBorder

キャプション バーの境界線スタイルを設定します。

```
void SetFlatBorder(BOOL bFlat=TRUE);
```

### <a name="parameters"></a>パラメーター

*bFlat*<br/>
[in]キャプション バーの境界線がフラットな場合は TRUE。 境界線が 3D である場合は FALSE。

##  <a name="seticon"></a>  CMFCCaptionBar::SetIcon

キャプション バーのアイコンを設定します。

```
void SetIcon(
    HICON hIcon,
    BarElementAlignment iconAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>パラメーター

*hIcon*<br/>
[in]設定アイコンのハンドルです。

*iconAlignment*<br/>
[in]アイコンの配置です。

### <a name="remarks"></a>Remarks

キャプション バーには、アイコンまたはビットマップのいずれかを表示できます。 参照してください[CMFCCaptionBar::SetBitmap](#setbitmap)ビットマップを表示する方法を説明します。 アイコンとビットマップの両方を設定した場合、アイコンが常に表示されます。 呼び出す[CMFCCaptionBar::RemoveIcon](#removeicon)キャプション バーからアイコンを削除します。

に従って配置されたが、アイコン、 *iconAlignment*パラメーター。 次のいずれか`BarElementAlignment`値。

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

##  <a name="setimagetooltip"></a>  CMFCCaptionBar::SetImageToolTip

キャプション バーには、イメージのツールヒントを設定します。

```
void SetImageToolTip(
    LPCTSTR lpszToolTip,
    LPCTSTR lpszDescription=NULL);
```

### <a name="parameters"></a>パラメーター

*lpszToolTip*<br/>
[in]ツールヒントのテキスト。

*lpszDescription*<br/>
[in]ツールヒントの説明。

##  <a name="setmargin"></a>  CMFCCaptionBar::SetMargin

キャプション バーの要素の端とキャプション バー コントロールの端との間の距離を設定します。

```
void SetMargin(int nMargin);
```

### <a name="parameters"></a>パラメーター

*nMargin*<br/>
[in]キャプション バーの要素の端とキャプション バー コントロールの端の間隔をピクセル単位で距離です。

##  <a name="settext"></a>  CMFCCaptionBar::SetText

キャプション バーのテキスト ラベルを設定します。

```
void SetText(
    const CString& strText,
    BarElementAlignment textAlignment=ALIGN_RIGHT);
```

### <a name="parameters"></a>パラメーター

*strText*<br/>
[in]設定するテキスト文字列。

*textalignment それから*<br/>
[in]テキストの配置。

### <a name="remarks"></a>Remarks

テキスト ラベルを配置の指定に従って、 *textalignment それから*パラメーター。 次のいずれか`BarElementAlignment`値。

- ALIGN_INVALID

- ALIGN_LEFT

- ALIGN_RIGHT

- ALIGN_CENTER

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
