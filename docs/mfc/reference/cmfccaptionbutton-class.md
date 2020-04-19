---
title: CMFCCaptionButton クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::CMFCCaptionButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetHit
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetIconID
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetRect
- AFXCAPTIONBUTTON/CMFCCaptionButton::GetSize
- AFXCAPTIONBUTTON/CMFCCaptionButton::IsMiniFrameButton
- AFXCAPTIONBUTTON/CMFCCaptionButton::Move
- AFXCAPTIONBUTTON/CMFCCaptionButton::OnDraw
- AFXCAPTIONBUTTON/CMFCCaptionButton::SetMiniFrameButton
helpviewer_keywords:
- CMFCCaptionButton [MFC], CMFCCaptionButton
- CMFCCaptionButton [MFC], GetHit
- CMFCCaptionButton [MFC], GetIconID
- CMFCCaptionButton [MFC], GetRect
- CMFCCaptionButton [MFC], GetSize
- CMFCCaptionButton [MFC], IsMiniFrameButton
- CMFCCaptionButton [MFC], Move
- CMFCCaptionButton [MFC], OnDraw
- CMFCCaptionButton [MFC], SetMiniFrameButton
ms.assetid: c5774b38-c0dd-414a-9ede-3b2f78f233ec
ms.openlocfilehash: 2020f6cb2f0feec28996f69791899c648600b600
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403816"
---
# <a name="cmfccaptionbutton-class"></a>CMFCCaptionButton クラス

`CMFCCaptionButton`クラスは、ドッキング ペインまたはミニフレーム ウィンドウのキャプション バーに表示されるボタンを実装します。 通常は、フレームワークがキャプション ボタンを自動的に作成します。

## <a name="syntax"></a>構文

```
class CMFCCaptionButton : public CObject
```

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCCaptionButton::CMFCCaptionButton](#cmfccaptionbutton)|CMFCCaptionButton オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCCaptionButton::GetHit](#gethit)|ボタンで表されるコマンドを返します。|
|[CMFCCaptionButton::GetIconID](#geticonid)|ボタンに関連付けられているイメージ ID を返します。|
|[CMFCCaptionButton::GetRect](#getrect)|ボタンによって占有されている四角形を返します。|
|[CMFCCaptionButton::GetSize](#getsize)|ボタンの高さと幅を返します。|
|[CMFCCaptionButton::IsMiniFrameButton](#isminiframebutton)|タイトル バーの高さはミニ サイズに設定されているかどうかを示します。|
|[CMFCCaptionButton::Move](#move)|ウィンドウの表示状態のボタンの描画位置を設定します。|
|[CMFCCaptionButton::OnDraw](#ondraw)|キャプション ボタンを描画します。|
|[CMFCCaptionButton::SetMiniFrameButton](#setminiframebutton)|ミニ タイトル バーのサイズを設定します。|

## <a name="remarks"></a>Remarks

クラスを派生させる[CPaneFrameWnd クラス](../../mfc/reference/cpaneframewnd-class.md)保護対象のメソッドを使用して`AddButton`、ミニフレーム ウィンドウにキャプション ボタンを追加します。

CPaneFrameWnd.h は、キャプション ボタンの 2 種類のコマンド Id を定義します。

- AFX_CAPTION_BTN_PIN ドッキング ペインが自動的に隠すモードをサポートしている場合は、ピン留めする ボタンを表示します。

- AFX_CAPTION_BTN_CLOSE で、表示、**閉じる**ボタン、ウィンドウの終了または非表示にできます。

## <a name="example"></a>例

次の例は、構築する方法を示します、`CMFCCaptionButton`オブジェクトし、ミニ タイトル バーのサイズを設定します。

[!code-cpp[NVC_MFC_RibbonApp#43](../../mfc/reference/codesnippet/cpp/cmfccaptionbutton-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCCaptionButton](../../mfc/reference/cmfccaptionbutton-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcaptionbutton.h

##  <a name="cmfccaptionbutton"></a>  CMFCCaptionButton::CMFCCaptionButton

`CMFCCaptionButton` オブジェクトを構築します。

```
CMFCCaptionButton();

CMFCCaptionButton(
    UINT nHit,
    BOOL bLeftAlign = FALSE);
```

### <a name="parameters"></a>パラメーター

*nHit*<br/>
[in]ボタンに関連付けられているコマンド。

*bLeftAlign*<br/>
[in]ボタンは、左に配置されているかどうかを指定します。

次の表に指定できる値の一覧、 *nHit*パラメーター。

|[値]|コマンド|
|-----------|-------------|
|AFX_HTCLOSE|閉じるボタンをクリックします。|
|HTMINBUTTON|最小化ボタン。|
|HTMAXBUTTON|最大化ボタン。|
|AFX_HTLEFTBUTTON|左矢印ボタンをクリックします。|
|AFX_HTRIGHTBUTTON|右矢印ボタンをクリックします。|
|AFX_HTMENU|下向きの矢印のメニュー ボタン。|
|HTNOWHERE|既定値です。コマンドを表すありません。|

### <a name="remarks"></a>Remarks

既定では、キャプション ボタンは、コマンドに関連付けられていません。

キャプション ボタンは、いずれかで、右または左に揃えて配置されます。

##  <a name="gethit"></a>  CMFCCaptionButton::GetHit

ボタンで表されるコマンドを返します。

```
UINT GetHit() const;
```

### <a name="return-value"></a>戻り値

ボタンで表されるコマンド。

次の表では、有効な戻り値を示します。

|[値]|コマンド|
|-----------|-------------|
|AFX_HTCLOSE|閉じるボタンをクリックします。|
|HTMINBUTTON|最小化ボタン。|
|HTMAXBUTTON|最大化ボタン。|
|AFX_HTLEFTBUTTON|左矢印ボタンをクリックします。|
|AFX_HTRIGHTBUTTON|右矢印ボタンをクリックします。|
|AFX_HTMENU|下向きの矢印のメニュー ボタン。|
|HTNOWHERE|既定値です。コマンドを表すありません。|

##  <a name="geticonid"></a>  CMFCCaptionButton::GetIconID

ボタンに関連付けられているイメージ ID を返します。

```
virtual CMenuImages::IMAGES_IDS GetIconID(
    BOOL bHorz,
    BOOL bMaximized = FALSE) const;
```

### <a name="parameters"></a>パラメーター

*bHorz*<br/>
[in]左側または右側の矢印のイメージ Id の場合は TRUE。FALSE を上下の矢印のイメージ Id。

*bMaximized*<br/>
[in]TRUE の最大化イメージ ID。最小化イメージ ID の場合は FALSE。

### <a name="return-value"></a>戻り値

イメージ id。

### <a name="remarks"></a>Remarks

パラメーターでは、最小化にイメージ Id を指定またはキャプション ボタンを最大化します。

##  <a name="getrect"></a>  CMFCCaptionButton::GetRect

ボタンによって占有されている四角形を返します。

```
virtual CRect GetRect() const;
```

### <a name="return-value"></a>戻り値

ボタンの位置を表す四角形。

### <a name="remarks"></a>Remarks

ボタンが表示できない場合、返されるサイズは 0 です。

##  <a name="getsize"></a>  CMFCCaptionButton::GetSize

ボタンの高さと幅を返します。

```
static CSize GetSize();
```

### <a name="return-value"></a>戻り値

ボタンの外部の大きさ。

### <a name="remarks"></a>Remarks

返されるサイズには、ボタンの余白と境界線が含まれています。

##  <a name="isminiframebutton"></a>  CMFCCaptionButton::IsMiniFrameButton

タイトル バーの高さはミニ サイズに設定されているかどうかを示します。

```
BOOL IsMiniFrameButton() const;
```

### <a name="return-value"></a>戻り値

キャプションが小さなサイズに設定されている場合は TRUE。それ以外の場合は FALSE です。

### <a name="remarks"></a>Remarks

##  <a name="move"></a>  CMFCCaptionButton::Move

ウィンドウの表示状態のボタンの描画位置を設定します。

```
void Move(
    const CPoint& ptTo,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>パラメーター

*ptTo*<br/>
[in]新しい場所です。

*bHide*<br/>
[in]ボタンを表示するかどうか。

##  <a name="ondraw"></a>  CMFCCaptionButton::OnDraw

キャプション ボタンを描画します。

```
virtual void OnDraw(
    CDC* pDC,
    BOOL bActive,
    BOOL bHorz = TRUE,
    BOOL bMaximized = TRUE,
    BOOL bDisabled = FALSE);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]ボタンのデバイス コンテキストへのポインター。

*描画*<br/>
[in]アクティブなボタン イメージを描画するかどうか。

*bHorz*<br/>
[in]派生クラスで使用するために予約されています。

*bMaximized*<br/>
[in]最大化ボタンのイメージを描画するかどうか。

*bDisabled*<br/>
[in]ボタンが有効なイメージを描画するかどうか。

### <a name="remarks"></a>Remarks

*BMaximized*パラメーターは、ボタンは、最大にする場合に使用または最小化ボタン。

##  <a name="setminiframebutton"></a>  CMFCCaptionButton::SetMiniFrameButton

ミニ タイトル バーのサイズを設定します。

```
void SetMiniFramebutton(BOOL bSet = TRUE);
```

### <a name="parameters"></a>パラメーター

*bSet*<br/>
[in]TRUE のミニのタイトル バーの高さ。既定のタイトル バーの高さの場合は FALSE。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CPaneFrameWnd クラス](../../mfc/reference/cpaneframewnd-class.md)<br/>
[CDockablePane クラス](../../mfc/reference/cdockablepane-class.md)
