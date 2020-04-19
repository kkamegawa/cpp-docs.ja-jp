---
title: CMFCRibbonStatusBarPane クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::GetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::IsExtended
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnDrawBorder
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFillBackground
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAlmostLargeText
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetAnimationList
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::SetTextAlign
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StartAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::StopAnimation
- AFXRIBBONSTATUSBARPANE/CMFCRibbonStatusBarPane::OnFinishAnimation
helpviewer_keywords:
- CMFCRibbonStatusBarPane [MFC], CMFCRibbonStatusBarPane
- CMFCRibbonStatusBarPane [MFC], GetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], GetTextAlign
- CMFCRibbonStatusBarPane [MFC], IsAnimation
- CMFCRibbonStatusBarPane [MFC], IsExtended
- CMFCRibbonStatusBarPane [MFC], OnDrawBorder
- CMFCRibbonStatusBarPane [MFC], OnFillBackground
- CMFCRibbonStatusBarPane [MFC], SetAlmostLargeText
- CMFCRibbonStatusBarPane [MFC], SetAnimationList
- CMFCRibbonStatusBarPane [MFC], SetTextAlign
- CMFCRibbonStatusBarPane [MFC], StartAnimation
- CMFCRibbonStatusBarPane [MFC], StopAnimation
- CMFCRibbonStatusBarPane [MFC], OnFinishAnimation
ms.assetid: 5d034c3c-ecca-4267-b88c-0f55a2884dd0
ms.openlocfilehash: 9911672ec139ab1598db8005e9b7b909e85dd33d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410077"
---
# <a name="cmfcribbonstatusbarpane-class"></a>CMFCRibbonStatusBarPane クラス

`CMFCRibbonStatusBarPane`クラスは、リボン ステータス バーに追加できるリボン要素を実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonStatusBarPane : public CMFCRibbonButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane](#cmfcribbonstatusbarpane)|`CMFCRibbonStatusBarPane` オブジェクトを構築して初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::GetAlmostLargeText](#getalmostlargetext)|切り捨てることがなく、ウィンドウに表示できる最大長の文字列を定義する文字列を返します。|
|[CMFCRibbonStatusBarPane::GetTextAlign](#gettextalign)|テキストの配置の現在の設定を返します。|
|[CMFCRibbonStatusBarPane::IsAnimation](#isanimation)|アニメーションが進行中かどうかを判断します。|
|[CMFCRibbonStatusBarPane::IsExtended](#isextended)|リボン ステータス バーの拡張領域内のウィンドウにあるかどうかを判断します。|
|[CMFCRibbonStatusBarPane::OnDrawBorder](#ondrawborder)|(上書き[CMFCRibbonButton::OnDrawBorder](../../mfc/reference/cmfcribbonbutton-class.md#ondrawborder))。|
|[CMFCRibbonStatusBarPane::OnFillBackground](#onfillbackground)|(上書き[CMFCRibbonButton::OnFillBackground](../../mfc/reference/cmfcribbonbutton-class.md#onfillbackground))。|
|[CMFCRibbonStatusBarPane::SetAlmostLargeText](#setalmostlargetext)|切り捨てることがなく、ウィンドウに表示できる最大長の文字列を定義します。|
|[CMFCRibbonStatusBarPane::SetAnimationList](#setanimationlist)|アニメーションを使用できるイメージ リストのウィンドウに割り当てられます。|
|[CMFCRibbonStatusBarPane::SetTextAlign](#settextalign)|テキストの配置を設定します。|
|[CMFCRibbonStatusBarPane::StartAnimation](#startanimation)|ウィンドウに割り当てられているアニメーションを開始します。|
|[CMFCRibbonStatusBarPane::StopAnimation](#stopanimation)|ウィンドウに割り当てられているアニメーションを停止します。 .|

### <a name="protected-methods"></a>プロテクト メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonStatusBarPane::OnFinishAnimation](#onfinishanimation)|ウィンドウに割り当てられているアニメーションが停止したときに、フレームワークによって呼び出されます。|

## <a name="example"></a>例

次の例は、`CMFCRibbonStatusBarPane` クラスのさまざまなメソッドの使用方法を説明しています。 例では、作成する方法を示しています、`CMFCRibbonStatusBarPane`オブジェクト、ステータス バー ペインのラベルのテキストの配置の設定、切り捨てることがなく、ステータス バー ペインに表示できますをステータス バー ペインを使用できるイメージ リストに接続する最も長いテキストを定義します。nimation、およびアニメーションを開始します。

[!code-cpp[NVC_MFC_RibbonApp#2](../../mfc/reference/codesnippet/cpp/cmfcribbonstatusbarpane-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonStatusBarPane](../../mfc/reference/cmfcribbonstatusbarpane-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribbonstatusbarpane.h

##  <a name="cmfcribbonstatusbarpane"></a>  CMFCRibbonStatusBarPane::CMFCRibbonStatusBarPane

ステータス バー ペインのオブジェクトを構築します。

```
CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    BOOL bIsStatic=FALSE,
    HICON hIcon=NULL,
    LPCTSTR lpszAlmostLargeText=NULL);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192,192 1,192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);

CMFCRibbonStatusBarPane(
    UINT nCmdID,
    LPCTSTR lpszText,
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTrnsp=RGB(192, 192 1, 192) 1,
    HICON hIcon=NULL,
    BOOL bIsStatic=FALSE);
```

### <a name="parameters"></a>パラメーター

*nCmdID*<br/>
[in]ウィンドウのコマンド ID を指定します。

*lpszText*<br/>
[in]ウィンドウに表示するテキスト文字列を指定します。

*bIsStatic*<br/>
[in]TRUE の場合、ステータス ウィンドウを強調表示されているまたはをクリックして選択されていることはできません。

*hIcon*<br/>
[in]ウィンドウに表示されるアイコンを識別するハンドルを指定します。

*lpszAlmostLargeText*<br/>
[in]ウィンドウが表示可能な最大長の文字列を指定します。

*hBmpAnimationList*<br/>
[in]アニメーションで使用するイメージ リストを識別するハンドルを指定します。

*cxAnimation*<br/>
[in]\(ピクセル単位)、アニメーションで使用するイメージ リストのアイコンの幅を指定します。

*clrTrnsp*<br/>
[in]アニメーションに使用されるイメージの一覧で、イメージの透明色を指定します。

*uiAnimationListResID*<br/>
[in]アニメーションで使用するイメージ リストのリソース ID を指定します。

##  <a name="getalmostlargetext"></a>  CMFCRibbonStatusBarPane::GetAlmostLargeText

ステータス バー ペインを表示できる最大長の文字列を取得します。

```
LPCTSTR GetAlmostLargeText() const;
```

### <a name="return-value"></a>戻り値

ステータス バー ペインを表示できる最も長いテキスト文字列。

##  <a name="gettextalign"></a>  CMFCRibbonStatusBarPane::GetTextAlign

ステータス バー ペインのラベルのテキストの配置の現在の設定を取得します。

```
int GetTextAlign() const;
```

### <a name="return-value"></a>戻り値

次のいずれかの現在のテキスト配置:

- TA_LEFT

- TA_CENTER

- TA_RIGHT します。

##  <a name="isanimation"></a>  CMFCRibbonStatusBarPane::IsAnimation

アニメーションが進行中かどうかを判断します。

```
BOOL IsAnimation() const;
```

### <a name="return-value"></a>戻り値

アニメーションが実行中の場合は TRUE。FALSE それ以外の場合。

##  <a name="isextended"></a>  CMFCRibbonStatusBarPane::IsExtended

リボン ステータス バーの拡張領域内のウィンドウにあるかどうかを決定します。

```
BOOL IsExtended() const;
```

### <a name="return-value"></a>戻り値

ウィンドウがステータス バーの拡張領域にある場合は TRUE。 FALSE それ以外の場合。

##  <a name="ondrawborder"></a>  CMFCRibbonStatusBarPane::OnDrawBorder

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual void OnDrawBorder(CDC*);
```

### <a name="parameters"></a>パラメーター

[in]*CDC&#42;*<br/>

### <a name="remarks"></a>Remarks

##  <a name="onfillbackground"></a>  CMFCRibbonStatusBarPane::OnFillBackground

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual COLORREF OnFillBackground(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

[in]*pDC*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onfinishanimation"></a>  CMFCRibbonStatusBarPane::OnFinishAnimation

フレームワークは、ウィンドウに割り当てられているアニメーションの終了時にこのメソッドを呼び出します。

```
virtual void OnFinishAnimation();
```

### <a name="remarks"></a>Remarks

`StopAnimation` メソッドの呼び出し、`OnFinishAnimation`メソッドで、アニメーションの終了時にデータのクリーンアップに使用することができます。

##  <a name="setalmostlargetext"></a>  CMFCRibbonStatusBarPane::SetAlmostLargeText

切り捨てることがなく、ステータス バー ペインに表示できる最も長いテキストを定義します。

```
void SetAlmostLargeText(LPCTSTR lpszAlmostLargeText);
```

### <a name="parameters"></a>パラメーター

*lpszAlmostLargeText*<br/>
[in]切り捨てることがなく、ステータス バー ペインに表示できる最も長い文字列を指定します。

### <a name="remarks"></a>Remarks

ライブラリは、テキストのサイズを計算する*lpszAlmostLargeText*を指定し、それに応じて、ウィンドウのサイズを変更します。 テキストは、ウィンドウにも適合しない場合は切り捨てられます。

##  <a name="setanimationlist"></a>  CMFCRibbonStatusBarPane::SetAnimationList

アニメーションを使用できるイメージ リストのステータス バー ペインにアタッチします。

```
void SetAnimationList(
    HBITMAP hBmpAnimationList,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);

BOOL SetAnimationList(
    UINT uiAnimationListResID,
    int cxAnimation=16,
    COLORREF clrTransp=RGB(192, 192 1, 192) 1);
```

### <a name="parameters"></a>パラメーター

*hBmpAnimationList*<br/>
[in]イメージ リストを識別するハンドルを指定します。

*cxAnimation*<br/>
[in]イメージ リスト内のフレームのピクセル、幅を指定します。

*clrTransp*<br/>
[in]イメージ リストの透明色を指定します。

*uiAnimationListResID*<br/>
[in]イメージ リストのリソース ID を指定します。

### <a name="return-value"></a>戻り値

イメージ リストが、ステータス バー ペインを正常にアタッチされている場合は TRUE。FALSE それ以外の場合。

##  <a name="settextalign"></a>  CMFCRibbonStatusBarPane::SetTextAlign

ステータス バー ペインのラベルのテキストの配置を設定します。

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>パラメーター

*nAlign*<br/>
[in]テキストの配置を指定します。

### <a name="remarks"></a>Remarks

*nAlign*値は次のいずれかであることができます。

- TA_LEFT: 左揃え

- TA_CENTER: 中央揃え

- TA_RIGHT: 右揃え

##  <a name="startanimation"></a>  CMFCRibbonStatusBarPane::StartAnimation

ウィンドウに割り当てることのアニメーションを開始します。

```
void StartAnimation(
    UINT nFrameDelay=500,
    UINT nDuration=-1);
```

### <a name="parameters"></a>パラメーター

*nFrameDelay*<br/>
[in]アニメーションのフレーム レートをミリ秒単位で指定します。

*nDuration*<br/>
[in]ミリ秒単位で、アニメーションの再生にどのくらいの期間を指定します。 無限ループに-1 を使用します。

### <a name="remarks"></a>Remarks

呼び出す前に、イメージ リストを識別するハンドルを指定する必要があります`StartAnimation`を使用して`SetAnimationList`します。

##  <a name="stopanimation"></a>  CMFCRibbonStatusBarPane::StopAnimation

ステータス バー ペインに割り当てられているアニメーションを停止します。

```
void StopAnimation();
```

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton クラス](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonStatusBar クラス](../../mfc/reference/cmfcribbonstatusbar-class.md)
