---
title: CMFCDesktopAlertWnd Class
ms.date: 10/18/2018
f1_keywords:
- CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::Create
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetCaptionHeight
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetDialogSize
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetLastPos
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::GetTransparency
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::HasSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnBeforeShow
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnClickLinkButton
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::OnDraw
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::ProcessCommand
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationSpeed
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAnimationType
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetAutoCloseTime
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetSmallCaption
- AFXDESKTOPALERTWND/CMFCDesktopAlertWnd::SetTransparency
helpviewer_keywords:
- CMFCDesktopAlertWnd [MFC], Create
- CMFCDesktopAlertWnd [MFC], GetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], GetAnimationType
- CMFCDesktopAlertWnd [MFC], GetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], GetCaptionHeight
- CMFCDesktopAlertWnd [MFC], GetDialogSize
- CMFCDesktopAlertWnd [MFC], GetLastPos
- CMFCDesktopAlertWnd [MFC], GetTransparency
- CMFCDesktopAlertWnd [MFC], HasSmallCaption
- CMFCDesktopAlertWnd [MFC], OnBeforeShow
- CMFCDesktopAlertWnd [MFC], OnClickLinkButton
- CMFCDesktopAlertWnd [MFC], OnCommand
- CMFCDesktopAlertWnd [MFC], OnDraw
- CMFCDesktopAlertWnd [MFC], ProcessCommand
- CMFCDesktopAlertWnd [MFC], SetAnimationSpeed
- CMFCDesktopAlertWnd [MFC], SetAnimationType
- CMFCDesktopAlertWnd [MFC], SetAutoCloseTime
- CMFCDesktopAlertWnd [MFC], SetSmallCaption
- CMFCDesktopAlertWnd [MFC], SetTransparency
ms.assetid: 73a2dd7b-ea84-4ae2-9830-7cf6e8dd2425
ms.openlocfilehash: 3ff74f5025d888077b51f8191f043237597dfdbe
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403673"
---
# <a name="cmfcdesktopalertwnd-class"></a>CMFCDesktopAlertWnd Class

`CMFCDesktopAlertWnd`クラスは、イベントについてユーザーに通知する画面に表示されるモードレス ダイアログ ボックスの機能を実装します。

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。
## <a name="syntax"></a>構文

```
class CMFCDesktopAlertWnd : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCDesktopAlertWnd::Create](#create)|作成して、デスクトップの通知ウィンドウを初期化します。|
|[CMFCDesktopAlertWnd::GetAnimationSpeed](#getanimationspeed)|アニメーションの速度を返します。|
|[CMFCDesktopAlertWnd::GetAnimationType](#getanimationtype)|アニメーションの種類を返します。|
|[CMFCDesktopAlertWnd::GetAutoCloseTime](#getautoclosetime)|自動終了時間帯を返します。|
|[CMFCDesktopAlertWnd::GetCaptionHeight](#getcaptionheight)|キャプションの高さを返します。|
|[CMFCDesktopAlertWnd::GetDialogSize](#getdialogsize)||
|[CMFCDesktopAlertWnd::GetLastPos](#getlastpos)|画面のデスクトップ通知ウィンドウの最後の有効な位置を返します。|
|[CMFCDesktopAlertWnd::GetTransparency](#gettransparency)|透過性レベルを返します。|
|[CMFCDesktopAlertWnd::HasSmallCaption](#hassmallcaption)|デスクトップ通知ウィンドウが小規模のキャプションで表示されるかどうかを判断します。|
|[CMFCDesktopAlertWnd::OnBeforeShow](#onbeforeshow)||
|[CMFCDesktopAlertWnd::OnClickLinkButton](#onclicklinkbutton)|ユーザーがデスクトップのアラート メニューにあるリンク ボタンをクリックすると、フレームワークによって呼び出されます。|
|[CMFCDesktopAlertWnd::OnCommand](#oncommand)|フレームワークは、ユーザーは、子コントロールは、通知メッセージを送信するとき、またはアクセラレータのキーストロークを変換するとき、メニューから項目を選択すると、このメンバー関数を呼び出します。 (上書き[CWnd::OnCommand](../../mfc/reference/cwnd-class.md#oncommand))。|
|[CMFCDesktopAlertWnd::OnDraw](#ondraw)||
|[CMFCDesktopAlertWnd::ProcessCommand](#processcommand)||
|[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)|新しいアニメーション速度を設定します。|
|[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)|アニメーションの種類を設定します。|
|[CMFCDesktopAlertWnd::SetAutoCloseTime](#setautoclosetime)|自動終了時間帯を設定します。|
|[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)|小規模で、通常のキャプションを切り替えます。|
|[CMFCDesktopAlertWnd::SetTransparency](#settransparency)|透過性レベルを設定します。|

## <a name="remarks"></a>Remarks

デスクトップ通知ウィンドウを透明にすることができます、アニメーションの効果が表示されます (指定された遅延の後または閉じるボタンをクリックして、ユーザーが閉じるときに) が表示されなくなることができます。

デスクトップ通知ウィンドウは、アイコン、メッセージ テキスト (ラベル)、およびリンクを含む既定 ダイアログ ボックスを含めることもできます。 また、アプリケーションのリソースからのカスタム ダイアログ ボックスがデスクトップ通知ウィンドウに含めることができます。

2 つの手順では、デスクトップの通知ウィンドウを作成します。 最初に、構築するコンス トラクターを呼び出し、`CMFCDesktopAlertWnd`オブジェクト。 次に、呼び出し、 [cmfcdesktopalertwnd::create](#create)メンバー関数は、ウィンドウを作成し、アタッチ先、`CMFCDesktopAlertWnd`オブジェクト。

`CMFCDesktopAlertWnd`オブジェクトがデスクトップ通知ウィンドウのクライアント領域を塗りつぶす特殊な子ダイアログ ボックスを作成します。 ダイアログ ボックスでは、それに位置しているすべてのコントロールを所有します。

カスタム ダイアログ ボックスをポップアップ ウィンドウに表示するには、次の手順に従います。

1. `CMFCDesktopAlertDialog` の派生クラスを作成します。

1. リソースに子ダイアログ ボックスのテンプレートを作成します。

1. 呼び出す[cmfcdesktopalertwnd::create](#create)  ダイアログ ボックスのテンプレートと、派生クラスのランタイム クラス情報へのポインターのリソース ID を使用します。

1. ホスト型のコントロールから送信されるすべての通知を処理するためにカスタム ダイアログ ボックスをプログラムするか、これらの通知を直接処理するためにホストされるコントロールをプログラムします。

デスクトップ通知ウィンドウの動作を制御するのにには、次の関数を使用します。

- アニメーションの種類を呼び出すことによって設定[CMFCDesktopAlertWnd::SetAnimationType](#setanimationtype)します。 有効なオプションに広げて、スライド、およびフェードインします。

- アニメーション フレームの速度を呼び出すことによって設定[CMFCDesktopAlertWnd::SetAnimationSpeed](#setanimationspeed)します。

- 呼び出すことによって、透過性レベルを設定[CMFCDesktopAlertWnd::SetTransparency](#settransparency)します。

- 小規模に呼び出すことによって、キャプションのサイズを変更[CMFCDesktopAlertWnd::SetSmallCaption](#setsmallcaption)します。 小さいキャプションは、高 7 ピクセルです。

## <a name="example"></a>例

次の例では、さまざまなメソッドを使用する方法を示しています、`CMFCDesktopAlertWnd`を構成するクラス、`CMFCDesktopAlertWnd`オブジェクト。 この例では、アニメーションの種類の設定、ポップアップ ウィンドウの透明度を設定、通知ウィンドウが小さいキャプションを表示することを指定、および通知ウィンドウを自動的に終了する前に経過した時間を設定する方法を示します。 例では、作成し、デスクトップの通知ウィンドウを初期化する方法も示します。 このコード スニペットの一部、[デスクトップ アラート デモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_DesktopAlertDemo#1](../../mfc/reference/codesnippet/cpp/cmfcdesktopalertwnd-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CMFCDesktopAlertWnd](../../mfc/reference/cmfcdesktopalertwnd-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxDesktopAlertWnd.h

##  <a name="create"></a>  CMFCDesktopAlertWnd::Create

作成して、デスクトップの通知ウィンドウを初期化します。

```
virtual BOOL Create(
    CWnd* pWndOwner,
    UINT uiDlgResID,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1),
    CRuntimeClass* pRTIDlgBar = RUNTIME_CLASS(CMFCDesktopAlertDialog));

virtual BOOL Create(
    CWnd* pWndOwner,
    CMFCDesktopAlertWndInfo& params,
    HMENU hMenu = NULL,
    CPoint ptPos = CPoint(-1,-1));
```

### <a name="parameters"></a>パラメーター

*pWndOwner*<br/>
[入力、出力]通知ウィンドウの所有者を指定します。 その所有者しデスクトップ通知ウィンドウのすべての通知を受け取ります。 この値は NULL をすることはできません。

*uiDlgResID*<br/>
[in]通知ウィンドウのリソース ID を指定します。

*hMenu*<br/>
[in]ユーザーがメニュー ボタンをクリックしたときに表示されるメニューを指定します。 NULL の場合、メニュー ボタンは表示されません。

*ptPos*<br/>
[in]通知ウィンドウが表示される初期位置を指定、画面座標を使用します。 このパラメーターは、(-1,-1) には、画面の右下隅で、[アラート] ウィンドウが表示されます。

*pRTIDlgBar*<br/>
[in]アラートのウィンドウのクライアント領域を網羅するカスタム ダイアログ ボックス クラスのランタイム クラス情報。

*params*<br/>
[in]通知ウィンドウの作成に使用されるパラメーターを指定します。

### <a name="return-value"></a>戻り値

通知ウィンドウが正常に作成された場合は TRUE。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

通知ウィンドウを作成するには、このメソッドを呼び出します。 アラートのウィンドウのクライアント領域には、ユーザーに表示されるすべてのコントロールをホストする子ダイアログ ボックスが含まれています。

最初のメソッドのオーバー ロードは、アプリケーションのリソースから読み込まれた子ダイアログ ボックスを含むアラート ウィンドウを作成します。 最初のメソッドのオーバー ロードでは、カスタム ダイアログ ボックスのクラスのランタイム クラス情報も指定できます。

2 番目のメソッドのオーバー ロードは、既定のコントロールを含むアラート ウィンドウを作成します。 変更することで表示するコントロールを指定することができます、 [CMFCDesktopAlertWndInfo クラス](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)します。

##  <a name="getanimationspeed"></a>  CMFCDesktopAlertWnd::GetAnimationSpeed

アニメーションの速度を返します。

```
UINT GetAnimationSpeed() const;
```

### <a name="return-value"></a>戻り値

ミリ秒単位での通知ウィンドウのアニメーションの速度。

### <a name="remarks"></a>Remarks

アニメーションの速度は、アラートのウィンドウが開き、終了する速度について説明します。

##  <a name="getanimationtype"></a>  CMFCDesktopAlertWnd::GetAnimationType

アニメーションの種類を返します。

```
CMFCPopupMenu::ANIMATION_TYPE GetAnimationType();
```

### <a name="return-value"></a>戻り値

次のアニメーションの種類のいずれか:

- NO_ANIMATION

- 展開します。

- スライド

- フェード

- SYSTEM_DEFAULT_ANIMATION

##  <a name="getautoclosetime"></a>  CMFCDesktopAlertWnd::GetAutoCloseTime

自動終了時間帯を返します。

```
int GetAutoCloseTime() const;
```

### <a name="return-value"></a>戻り値

時間 (ミリ秒)、その後、[アラート] ウィンドウを自動的に閉じます。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、特定のアラート ウィンドウは自動的に閉じる前にどれ時間だけが経過する必要があります。

##  <a name="getcaptionheight"></a>  CMFCDesktopAlertWnd::GetCaptionHeight

キャプションの高さを返します。

```
virtual int GetCaptionHeight();
```

### <a name="return-value"></a>戻り値

キャプションのピクセル単位の高さ。

### <a name="remarks"></a>Remarks

このメソッドは、派生クラスでオーバーライドできます。 既定の実装で、いずれか: ポップアップ ウィンドウには、小さいキャプション、または Windows API 関数から取得した値を表示する場合は、小さいキャプションの高さの値 (7 ピクセル単位) を返します`GetSystemMetrics(SM_CYSMCAPTION)`します。

##  <a name="getlastpos"></a>  CMFCDesktopAlertWnd::GetLastPos

画面のデスクトップ通知ウィンドウの最後の位置を返します。

```
CPoint GetLastPos() const;
```

### <a name="return-value"></a>戻り値

画面座標にポイントします。

### <a name="remarks"></a>Remarks

このメソッドは、画面の通知ウィンドウの最後の有効な位置を返します。

##  <a name="gettransparency"></a>  CMFCDesktopAlertWnd::GetTransparency

透過性レベルを返します。

```
BYTE GetTransparency() const;
```

### <a name="return-value"></a>戻り値

0 ~ 255 の範囲の透明度レベル。 この値が大きい、不透明度を高くウィンドウ。

### <a name="remarks"></a>Remarks

このメソッドを使用すると、アラートのウィンドウの現在の透明度を取得できます。

##  <a name="hassmallcaption"></a>  CMFCDesktopAlertWnd::HasSmallCaption

デスクトップ通知ウィンドウが小さいキャプションまたは標準サイズのキャプションにあるかどうかを判断します。

```
BOOL HasSmallCaption() const;
```

### <a name="return-value"></a>戻り値

小さいキャプションのポップアップ ウィンドウが表示されている場合は TRUE。通常のサイズのキャプションを含むポップアップ ウィンドウが表示されている場合は FALSE です。

### <a name="remarks"></a>Remarks

小さいキャプションまたは標準サイズのキャプション、ポップアップ ウィンドウがあるかどうかを確認するのにには、このメソッドを使用します。 既定では、小さいキャプションは、高 7 ピクセルです。 標準サイズのキャプションの高さを取得するには、Windows API 関数を呼び出すことによって`GetSystemMetrics(SM_CYCAPTION)`します。

##  <a name="onbeforeshow"></a>  CMFCDesktopAlertWnd::OnBeforeShow

```
virtual BOOL OnBeforeShow(CPoint&);
```

### <a name="parameters"></a>パラメーター

[in]*CPoint (& a)*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="onclicklinkbutton"></a>  CMFCDesktopAlertWnd::OnClickLinkButton

ユーザーがデスクトップのアラート メニューにあるリンク ボタンをクリックすると、フレームワークによって呼び出されます。

```
virtual BOOL OnClickLinkButton(UINT uiCmdID);
```

### <a name="parameters"></a>パラメーター

*uiCmdID*<br/>
[in]このパラメーターは使用されません。

### <a name="return-value"></a>戻り値

常に FALSE です。

### <a name="remarks"></a>Remarks

ユーザーが通知ウィンドウのリンクをクリックしたときに通知する場合は、派生クラスでこのメソッドをオーバーライドします。

##  <a name="oncommand"></a>  CMFCDesktopAlertWnd::OnCommand

```
virtual BOOL OnCommand(
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>パラメーター

[in] *wParam*<br/>

[in] *lParam*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="ondraw"></a>  CMFCDesktopAlertWnd::OnDraw

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

[in]*pDC*<br/>

### <a name="remarks"></a>Remarks

##  <a name="processcommand"></a>  CMFCDesktopAlertWnd::ProcessCommand

```
BOOL ProcessCommand(HWND hwnd);
```

### <a name="parameters"></a>パラメーター

[in]*hwnd*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="setanimationspeed"></a>  CMFCDesktopAlertWnd::SetAnimationSpeed

新しいアニメーション速度を設定します。

```
void SetAnimationSpeed(UINT nSpeed);
```

### <a name="parameters"></a>パラメーター

*nSpeed*<br/>
[in]新しいアニメーションの速度をミリ秒単位で指定します。

### <a name="remarks"></a>Remarks

アラートのウィンドウのアニメーションの速度を設定するには、このメソッドを呼び出します。 既定のアニメーションの速度は、30 ミリ秒です。

##  <a name="setanimationtype"></a>  CMFCDesktopAlertWnd::SetAnimationType

アニメーションの種類を設定します。

```
void SetAnimationType(CMFCPopupMenu::ANIMATION_TYPE type);
```

### <a name="parameters"></a>パラメーター

*type*<br/>
[in]アニメーションの種類を指定します。

### <a name="remarks"></a>Remarks

アニメーションの種類を設定するには、このメソッドを呼び出します。 次のいずれかの値を指定できます。

- NO_ANIMATION

- 展開します。

- スライド

- フェード

- SYSTEM_DEFAULT_ANIMATION

##  <a name="setautoclosetime"></a>  CMFCDesktopAlertWnd::SetAutoCloseTime

自動終了時間帯を設定します。

```
void SetAutoCloseTime(int nTime);
```

### <a name="parameters"></a>パラメーター

*nTime*<br/>
[in]通知ウィンドウが自動的に閉じるまでの経過する時間 (ミリ秒単位)。

### <a name="remarks"></a>Remarks

ユーザーは、ウィンドウと対話しない場合、指定時間後に、[アラート] ウィンドウが自動的に閉じます。

##  <a name="setsmallcaption"></a>  CMFCDesktopAlertWnd::SetSmallCaption

および標準サイズの小さいキャプションを切り替えます。

```
void SetSmallCaption(BOOL bSmallCaption = TRUE);
```

### <a name="parameters"></a>パラメーター

*bSmallCaption*<br/>
[in]通知ウィンドウが小さいキャプションを表示することを指定する場合は TRUEそれ以外の場合、通知ウィンドウが標準サイズのキャプションを表示することを指定する場合は FALSE。

### <a name="remarks"></a>Remarks

小規模または標準サイズのキャプションを表示するには、このメソッドを呼び出します。 既定では、小さいキャプションは、高 7 ピクセルです。 通常のキャプションのサイズを取得するには、Windows API 関数を呼び出すことによって`GetSystemMetrics(SM_CYCAPTION)`します。

##  <a name="settransparency"></a>  CMFCDesktopAlertWnd::SetTransparency

ポップアップ ウィンドウの透明度を設定します。

```
void SetTransparency(BYTE nTransparency);
```

### <a name="parameters"></a>パラメーター

*nTransparency*<br/>
[in]透過性レベルを指定します。 この値は、0 から 255 までの間である必要があります。 この値が大きい、不透明度を高くウィンドウ。

### <a name="remarks"></a>Remarks

ポップアップ ウィンドウの透明度レベルを設定するには、この関数を呼び出します。

##  <a name="getdialogsize"></a>  CMFCDesktopAlertWnd::GetDialogSize

```
virtual CSize GetDialogSize();
```

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCDesktopAlertWndInfo クラス](../../mfc/reference/cmfcdesktopalertwndinfo-class.md)<br/>
[CMFCDesktopAlertDialog クラス](../../mfc/reference/cmfcdesktopalertdialog-class.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)
