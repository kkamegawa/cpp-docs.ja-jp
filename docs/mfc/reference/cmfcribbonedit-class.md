---
title: CMFCRibbonEdit クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CMFCRibbonEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::CanBeStretched
- AFXRIBBONEDIT/CMFCRibbonEdit::CopyFrom
- AFXRIBBONEDIT/CMFCRibbonEdit::CreateEdit
- AFXRIBBONEDIT/CMFCRibbonEdit::DestroyCtrl
- AFXRIBBONEDIT/CMFCRibbonEdit::DropDownList
- AFXRIBBONEDIT/CMFCRibbonEdit::EnableSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::GetCompactSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::GetIntermediateSize
- AFXRIBBONEDIT/CMFCRibbonEdit::GetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::GetWidth
- AFXRIBBONEDIT/CMFCRibbonEdit::HasCompactMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasFocus
- AFXRIBBONEDIT/CMFCRibbonEdit::HasLargeMode
- AFXRIBBONEDIT/CMFCRibbonEdit::HasSpinButtons
- AFXRIBBONEDIT/CMFCRibbonEdit::IsHighlighted
- AFXRIBBONEDIT/CMFCRibbonEdit::OnAfterChangeRect
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDraw
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawLabelAndImage
- AFXRIBBONEDIT/CMFCRibbonEdit::OnDrawOnList
- AFXRIBBONEDIT/CMFCRibbonEdit::OnEnable
- AFXRIBBONEDIT/CMFCRibbonEdit::OnHighlight
- AFXRIBBONEDIT/CMFCRibbonEdit::OnKey
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonDown
- AFXRIBBONEDIT/CMFCRibbonEdit::OnLButtonUp
- AFXRIBBONEDIT/CMFCRibbonEdit::OnRTLChanged
- AFXRIBBONEDIT/CMFCRibbonEdit::OnShow
- AFXRIBBONEDIT/CMFCRibbonEdit::Redraw
- AFXRIBBONEDIT/CMFCRibbonEdit::SetACCData
- AFXRIBBONEDIT/CMFCRibbonEdit::SetEditText
- AFXRIBBONEDIT/CMFCRibbonEdit::SetTextAlign
- AFXRIBBONEDIT/CMFCRibbonEdit::SetWidth
helpviewer_keywords:
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CanBeStretched
- CMFCRibbonEdit [MFC], CMFCRibbonEdit
- CMFCRibbonEdit [MFC], CopyFrom
- CMFCRibbonEdit [MFC], CreateEdit
- CMFCRibbonEdit [MFC], DestroyCtrl
- CMFCRibbonEdit [MFC], DropDownList
- CMFCRibbonEdit [MFC], EnableSpinButtons
- CMFCRibbonEdit [MFC], GetCompactSize
- CMFCRibbonEdit [MFC], GetEditText
- CMFCRibbonEdit [MFC], GetIntermediateSize
- CMFCRibbonEdit [MFC], GetTextAlign
- CMFCRibbonEdit [MFC], GetWidth
- CMFCRibbonEdit [MFC], HasCompactMode
- CMFCRibbonEdit [MFC], HasFocus
- CMFCRibbonEdit [MFC], HasLargeMode
- CMFCRibbonEdit [MFC], HasSpinButtons
- CMFCRibbonEdit [MFC], IsHighlighted
- CMFCRibbonEdit [MFC], OnAfterChangeRect
- CMFCRibbonEdit [MFC], OnDraw
- CMFCRibbonEdit [MFC], OnDrawLabelAndImage
- CMFCRibbonEdit [MFC], OnDrawOnList
- CMFCRibbonEdit [MFC], OnEnable
- CMFCRibbonEdit [MFC], OnHighlight
- CMFCRibbonEdit [MFC], OnKey
- CMFCRibbonEdit [MFC], OnLButtonDown
- CMFCRibbonEdit [MFC], OnLButtonUp
- CMFCRibbonEdit [MFC], OnRTLChanged
- CMFCRibbonEdit [MFC], OnShow
- CMFCRibbonEdit [MFC], Redraw
- CMFCRibbonEdit [MFC], SetACCData
- CMFCRibbonEdit [MFC], SetEditText
- CMFCRibbonEdit [MFC], SetTextAlign
- CMFCRibbonEdit [MFC], SetWidth
ms.assetid: 9b85f1f2-446b-454e-9af9-104fdad8a897
ms.openlocfilehash: 4f973074fbec3d04b1c1a74852b02ff2564217c1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504949"
---
# <a name="cmfcribbonedit-class"></a>CMFCRibbonEdit クラス

リボンバーに配置されるエディットコントロールを実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonEdit : public CMFCRibbonButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|`CMFCRibbonEdit` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonEdit:: CanBeStretched](#canbestretched)|`CMFCRibbonEdit`コントロールの高さをリボン行の高さに垂直方向に拡大できるかどうかを示します。|
|[CMFCRibbonEdit::CMFCRibbonEdit](#cmfcribbonedit)|`CMFCRibbonEdit` オブジェクトを構築します。|
|[CMFCRibbonEdit:: CopyFrom](#copyfrom)|指定した`CMFCRibbonEdit`オブジェクトの状態を現在`CMFCRibbonEdit`のオブジェクトにコピーします。|
|[CMFCRibbonEdit:: CreateEdit](#createedit)|`CMFCRibbonEdit`オブジェクトの新しいテキストボックスを作成します。|
|[CMFCRibbonEdit::D estroyCtrl](#destroyctrl)|`CMFCRibbonEdit` オブジェクトを破棄します。|
|[CMFCRibbonEdit::D ropDownList](#dropdownlist)|リストボックスを下にドロップします。|
|[CMFCRibbonEdit::EnableSpinButtons](#enablespinbuttons)|テキストボックスのスピンボタンの範囲を有効にして設定します。|
|[CMFCRibbonEdit:: GetCompactSize](#getcompactsize)|`CFMCRibbonEdit`オブジェクトのコンパクトなサイズを取得します。|
|[CMFCRibbonEdit::GetEditText](#getedittext)|テキストボックス内のテキストを取得します。|
|[CMFCRibbonEdit:: GetIntermediateSize](#getintermediatesize)|`CMFCRibbonEdit`オブジェクトの中間サイズを取得します。|
|[CMFCRibbonEdit:: GetTextAlign](#gettextalign)|テキストボックス内のテキストの配置を取得します。|
|[CMFCRibbonEdit:: GetWidth](#getwidth)|`CMFCRibbonEdit`コントロールの幅 (ピクセル単位) を取得します。|
|[CMFCRibbonEdit::HasCompactMode](#hascompactmode)|`CMFCRibbonEdit`コントロールの表示サイズをコンパクトにできるかどうかを示します。|
|[CMFCRibbonEdit:: HasFocus](#hasfocus)|コントロールに`CMFCRIbbonEdit`フォーカスがあるかどうかを示します。|
|[CMFCRibbonEdit::HasLargeMode](#haslargemode)|`CMFCRibbonEdit`コントロールの表示サイズが大きくなる可能性があるかどうかを示します。|
|[CMFCRibbonEdit::HasSpinButtons](#hasspinbuttons)|テキストボックスにスピンボタンがあるかどうかを示します。|
|[CMFCRibbonEdit::IsHighlighted](#ishighlighted)|コントロールが強調`CMFCRibbonEdit`表示されているかどうかを示します。|
|[CMFCRibbonEdit::OnAfterChangeRect](#onafterchangerect)|`CMFCRibbonEdit`コントロールの表示四角形の大きさが変更されたときにフレームワークによって呼び出されます。|
|[CMFCRibbonEdit:: OnDraw](#ondraw)|`CMFCRibbonEdit`コントロールを描画するためにフレームワークによって呼び出されます。|
|[CMFCRibbonEdit::OnDrawLabelAndImage](#ondrawlabelandimage)|`CMFCRibbonEdit`コントロールのラベルとイメージを描画するためにフレームワークによって呼び出されます。|
|[CMFCRibbonEdit::OnDrawOnList](#ondrawonlist)|コマンドリストボックスに`CMFCRibbonEdit`コントロールを描画するために、フレームワークによって呼び出されます。|
|[CMFCRibbonEdit:: OnEnable](#onenable)|`CMFCRibbonEdit`コントロールを有効または無効にするためにフレームワークによって呼び出されます。|
|[CMFCRibbonEdit:: OnHighlight 表示](#onhighlight)|ポインターが`CMFCRibbonEdit`コントロールの境界内を出入りするときに、フレームワークによって呼び出されます。|
|[CMFCRibbonEdit::OnKey](#onkey)|ユーザーが keytip `CMFCRibbonEdit`を押し、コントロールにフォーカスがあるときにフレームワークによって呼び出されます。|
|[CMFCRibbonEdit::OnLButtonDown](#onlbuttondown)|ユーザーがコントロール上でマウスの`CMFCRibbonEdit`左ボタンを押したときにコントロールを更新するために、フレームワークによって呼び出されます。|
|[CMFCRibbonEdit::OnLButtonUp](#onlbuttonup)|ユーザーがマウスの左ボタンを離したときにフレームワークによって呼び出されます。|
|[CMFCRibbonEdit:: OnRTLChanged](#onrtlchanged)|レイアウトの方向が変更され`CMFCRibbonEdit`たときにコントロールを更新するために、フレームワークによって呼び出されます。|
|[CMFCRibbonEdit:: OnShow](#onshow)|`CMFCRibbonEdit`コントロールを表示または非表示にするためにフレームワークによって呼び出されます。|
|[CMFCRibbonEdit::Redraw](#redraw)|`CMFCRibbonEdit`コントロールの表示を更新します。|
|[CMFCRibbonEdit:: Setのデータ](#setaccdata)|`CMFCRibbonEdit`オブジェクトのアクセシビリティデータを設定します。|
|[CMFCRibbonEdit::SetEditText](#setedittext)|テキストボックス内のテキストを設定します。|
|[CMFCRibbonEdit:: SetTextAlign](#settextalign)|テキストボックスのテキストの配置を設定します。|
|[CMFCRibbonEdit:: SetWidth](#setwidth)|`CMFCRibbonEdit`コントロールのテキストボックスの幅を設定します。|

## <a name="remarks"></a>Remarks

## <a name="example"></a>例

次の例では、 `CMFCRibbonEdit`オブジェクトを構築し、エディットコントロールの横にスピンボタンを表示し、エディットコントロールのテキストを設定する方法を示します。 このコードスニペットは、 [MS Office 2007 Demo サンプル](../../overview/visual-cpp-samples.md)に含まれています。

[!code-cpp[NVC_MFC_MSOffice2007Demo#7](../../mfc/reference/codesnippet/cpp/cmfcribbonedit-class_1.cpp)]

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonEdit

##  <a name="canbestretched"></a>CMFCRibbonEdit:: CanBeStretched

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールの高さをリボン行の高さに垂直方向に拡大できるかどうかを示します。

```
virtual BOOL CanBeStretched();
```

### <a name="return-value"></a>戻り値

常に FALSE を返します。

### <a name="remarks"></a>Remarks

##  <a name="cmfcribbonedit"></a>CMFCRibbonEdit::CMFCRibbonEdit

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトを構築します。

```
CMFCRibbonEdit(
    UINT nID,
    int nWidth,
    LPCTSTR lpszLabel = NULL,
    int nImage = -1);

CMFCRibbonEdit();
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
から`CMFCRibbonEdit`コントロールのコマンド ID。

*nWidth*<br/>
から`CMFCRibbonEdit`コントロールのテキストボックスの幅 (ピクセル単位)。

*lpszLabel*<br/>
から`CMFCRibbonEdit`コントロールのラベル。

*nImage*<br/>
から`CMFCRibbonEdit`コントロールに使用する小さいイメージのインデックス。 小さい画像のコレクションは、親のリボンカテゴリによって維持されます。

### <a name="remarks"></a>Remarks

この`CMFCRibbonEdit`コントロールでは、大きなイメージは使用されません。

##  <a name="copyfrom"></a>  CMFCRibbonEdit::CopyFrom

指定した[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトの状態を現在の[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトにコピーします。

```
virtual void CopyFrom(const CMFCRibbonBaseElement& src);
```

### <a name="parameters"></a>パラメーター

*src*<br/>
からソース`CMFCRibbonEdit`オブジェクト。

### <a name="remarks"></a>Remarks

*Src*パラメーターの型`CMFCRibbonEdit`はである必要があります。

##  <a name="createedit"></a>CMFCRibbonEdit:: CreateEdit

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトの新しいテキストボックスを作成します。

```
virtual CMFCRibbonRichEditCtrl* CreateEdit(
    CWnd* pWndParent,
    DWORD dwEditStyle);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
から`CMFCRibbonEdit`オブジェクトの親ウィンドウへのポインター。

*dwEditStyle*<br/>
からテキストボックスのスタイルを指定します。 「解説」に記載されているウィンドウスタイルと、Windows SDK で説明されている[編集コントロールスタイル](/windows/win32/Controls/edit-control-styles)を組み合わせることができます。

### <a name="return-value"></a>戻り値

メソッドが正常に終了した場合は、新しいテキストボックスへのポインター。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

カスタムテキストボックスを作成するには、派生クラスでこのメソッドをオーバーライドします。

テキストボックスには、次の[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)を適用できます。

- **WS_CHILD**

- **WS_VISIBLE**

- **WS_DISABLED**

- **WS_GROUP**

- **WS_TABSTOP**

##  <a name="destroyctrl"></a>CMFCRibbonEdit::D estroyCtrl

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトを破棄します。

```
virtual void DestroyCtrl();
```

### <a name="remarks"></a>Remarks

##  <a name="dropdownlist"></a>CMFCRibbonEdit::D ropDownList

リストボックスを下にドロップします。

```
virtual void DropDownList();
```

### <a name="remarks"></a>Remarks

既定では、このメソッドは何も行いません。 リストボックスをドロップダウンするには、このメソッドをオーバーライドします。

##  <a name="enablespinbuttons"></a>  CMFCRibbonEdit::EnableSpinButtons

テキストボックスのスピンボタンの範囲を有効にして設定します。

```
void EnableSpinButtons(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>パラメーター

*N1 日*<br/>
からスピンボタンの最小値。

*N1 日*<br/>
からスピンボタンの最大値。

### <a name="remarks"></a>Remarks

スピンボタンを使用すると、上下の矢印が表示され、ユーザーは固定された値のセット内を移動できます。

##  <a name="getcompactsize"></a>CMFCRibbonEdit:: GetCompactSize

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトのコンパクトサイズを取得します。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から`CMFCRibbonEdit`オブジェクトのデバイスコンテキストへのポインター。

### <a name="return-value"></a>戻り値

`CMFCRibbonEdit`オブジェクトのコンパクトサイズ。

### <a name="remarks"></a>Remarks

##  <a name="getedittext"></a>  CMFCRibbonEdit::GetEditText

テキストボックス内のテキストを取得します。

```
CString GetEditText() const;
```

### <a name="return-value"></a>戻り値

テキストボックス内のテキスト。

### <a name="remarks"></a>Remarks

##  <a name="getintermediatesize"></a>CMFCRibbonEdit:: GetIntermediateSize

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトの中間サイズを取得します。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から`CMFCRibbonEdit`オブジェクトのデバイスコンテキストへのポインター。

### <a name="return-value"></a>戻り値

`CMFCRibbonEdit`オブジェクトの中間サイズ。

### <a name="remarks"></a>Remarks

##  <a name="gettextalign"></a>CMFCRibbonEdit:: GetTextAlign

テキストボックス内のテキストの配置を取得します。

```
int GetTextAlign() const;
```

### <a name="return-value"></a>戻り値

テキストの配置の列挙値。 使用可能な値については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

返される値は、次のいずれかの編集コントロールスタイルです。

- 左揃えの場合は**ES_LEFT**

- CENTER の配置のための**ES_CENTER**

- 右揃えの**ES_RIGHT**

これらのスタイルの詳細については、「[コントロールスタイルの編集](/windows/win32/Controls/edit-control-styles)」を参照してください。

##  <a name="getwidth"></a>  CMFCRibbonEdit::GetWidth

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールの幅 (ピクセル単位) を取得します。

```
int GetWidth(BOOL bInFloatyMode = FALSE) const;
```

### <a name="parameters"></a>パラメーター

*bInFloatyMode*<br/>
から`CMFCRibbonEdit`コントロールが浮動モードの場合は TRUE、それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

`CMFCRibbonEdit`コントロールの幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

##  <a name="hascompactmode"></a>CMFCRibbonEdit::HasCompactMode

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールの表示サイズをコンパクトにできるかどうかを示します。

```
virtual BOOL HasCompactMode() const;
```

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

既定では、このメソッドは常に TRUE を返します。 このメソッドをオーバーライドして、表示サイズをコンパクトにできるかどうかを示します。

##  <a name="hasfocus"></a>CMFCRibbonEdit:: HasFocus

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールにフォーカスがあるかどうかを示します。

```
virtual BOOL HasFocus() const;
```

### <a name="return-value"></a>戻り値

コントロールに`CMFCRibbonEdit`フォーカスがある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="haslargemode"></a>CMFCRibbonEdit::HasLargeMode

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールの表示サイズが大きくなる可能性があるかどうかを示します。

```
virtual BOOL HasLargeMode() const;
```

### <a name="return-value"></a>戻り値

常に FALSE を返します。

### <a name="remarks"></a>Remarks

既定では、このメソッドは常に FALSE を返します。 このメソッドをオーバーライドして、表示サイズが大きい可能性があるかどうかを示します。

##  <a name="hasspinbuttons"></a>  CMFCRibbonEdit::HasSpinButtons

テキストボックスにスピンボタンがあるかどうかを示します。

```
virtual BOOL HasSpinButtons() const;
```

### <a name="return-value"></a>戻り値

テキストボックスにスピンボタンがある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="ishighlighted"></a>CMFCRibbonEdit::IsHighlighted

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールが強調表示されているかどうかを示します。

```
virtual BOOL IsHighlighted() const;
```

### <a name="return-value"></a>戻り値

コントロールが強調`CMFCRibbonEdit`表示されている場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="onafterchangerect"></a>CMFCRibbonEdit::OnAfterChangeRect

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールの表示四角形の大きさが変更されたときにフレームワークによって呼び出されます。

```
virtual void OnAfterChangeRect(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から`CMFCRibbonEdit`コントロールのデバイスコンテキストへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="ondraw"></a>CMFCRibbonEdit:: OnDraw

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から`CMFCRibbonEdit`コントロールのデバイスコンテキストへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="ondrawlabelandimage"></a>CMFCRibbonEdit::OnDrawLabelAndImage

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールのラベルとイメージを描画するために、フレームワークによって呼び出されます。

```
virtual void OnDrawLabelAndImage(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から`CMFCRibbonEdit`コントロールのデバイスコンテキストへのポインター。

### <a name="remarks"></a>Remarks

##  <a name="ondrawonlist"></a>CMFCRibbonEdit::OnDrawOnList

コマンドリストボックスに[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールを描画するために、フレームワークによって呼び出されます。

```
virtual void OnDrawOnList(
    CDC* pDC,
    CString strText,
    int nTextOffset,
    CRect rect,
    BOOL bIsSelected,
    BOOL bHighlighted);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
から`CMFCRibbonEdit`コントロールのデバイスコンテキストへのポインター。

*strText*<br/>
から表示テキスト[](../../mfc/reference/cmfcribbonedit-class.md "cmfcribbonedit クラス")。

*nTextOffset*<br/>
からリストボックスの左側から表示テキストまでの距離 (ピクセル単位)。

*rect*<br/>
から`CMFCRibbonEdit`コントロールの表示四角形。

*bIsSelected*<br/>
からこのパラメーターは使用されません。

*bHighlighted 表示*<br/>
からこのパラメーターは使用されません。

### <a name="remarks"></a>Remarks

[コマンド] ボックスの一覧には、ユーザーがクイックアクセスツールバーをカスタマイズできるようにするためのリボンコントロールが表示されます。

##  <a name="onenable"></a>CMFCRibbonEdit:: OnEnable

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールを有効または無効にするためにフレームワークによって呼び出されます。

```
virtual void OnEnable(BOOL bEnable);
```

### <a name="parameters"></a>パラメーター

*bEnable*<br/>
からコントロールを有効にする場合は TRUE。コントロールを無効にする場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="onhighlight"></a>  CMFCRibbonEdit::OnHighlight

ポインターが[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールの境界内に出入りするときに、フレームワークによって呼び出されます。

```
virtual void OnHighlight(BOOL bHighlight);
```

### <a name="parameters"></a>パラメーター

*bHighlight 表示*<br/>
からポインターが`CMFCRibbonEdit`コントロールの境界内にある場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="onkey"></a>  CMFCRibbonEdit::OnKey

ユーザーが keytip を押し、 [CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールにフォーカスがあるときにフレームワークによって呼び出されます。

```
virtual BOOL OnKey(BOOL bIsMenuKey);
```

### <a name="parameters"></a>パラメーター

*bIsMenuKey*<br/>
からKeytip にポップアップメニューが表示される場合は TRUE。それ以外の場合は FALSE。

### <a name="return-value"></a>戻り値

イベントが処理された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="onlbuttondown"></a>  CMFCRibbonEdit::OnLButtonDown

ユーザーがコントロール上でマウスの左ボタンを押したときに[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールを更新するために、フレームワークによって呼び出されます。

```
virtual void OnLButtonDown(CPoint point);
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
からこのパラメーターは使用されません。

### <a name="remarks"></a>Remarks

##  <a name="onlbuttonup"></a>CMFCRibbonEdit::OnLButtonUp

ユーザーがマウスの左ボタンを離したときにフレームワークによって呼び出されます。

```
virtual void OnLButtonUp(CPoint point);
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
からこのパラメーターは使用されません。

### <a name="remarks"></a>Remarks

##  <a name="onrtlchanged"></a>CMFCRibbonEdit:: OnRTLChanged

レイアウトの方向が変更されたときに[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールを更新するために、フレームワークによって呼び出されます。

```
virtual void OnRTLChanged(BOOL bIsRTL);
```

### <a name="parameters"></a>パラメーター

*bIsRTL*<br/>
からレイアウトが右から左の場合は TRUE。レイアウトが左から右への場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="onshow"></a>CMFCRibbonEdit:: OnShow

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールを表示または非表示にするためにフレームワークによって呼び出されます。

```
virtual void OnShow(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
からコントロールを表示する場合は TRUE。コントロールを非表示にする場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="redraw"></a>  CMFCRibbonEdit::Redraw

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールの表示を更新します。

```
virtual void Redraw();
```

### <a name="remarks"></a>Remarks

このメソッドは、RDW_INVALIDATE、RDW_ERASE、 `CMFCRibbonEdit`および RDW_UPDATENOW の各フラグが設定された状態で[CWnd:: redrawwindow](/windows/win32/api/winuser/nf-winuser-redrawwindow)を間接的に呼び出すことによって、オブジェクトの表示四角形を再描画します。

##  <a name="setaccdata"></a>CMFCRibbonEdit:: Setのデータ

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)オブジェクトのアクセシビリティデータを設定します。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
`CMFCRibbonEdit`オブジェクトの親ウィンドウへのポインター。

*data*<br/>
`CMFCRibbonEdit`オブジェクトのアクセシビリティデータ。

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

##  <a name="setedittext"></a>CMFCRibbonEdit::SetEditText

テキストボックス内のテキストを設定します。

```
void SetEditText(CString strText);
```

### <a name="parameters"></a>パラメーター

*strText*<br/>
からテキストボックスのテキスト。

##  <a name="settextalign"></a>CMFCRibbonEdit:: SetTextAlign

テキストボックスのテキストの配置を設定します。

```
void SetTextAlign(int nAlign);
```

### <a name="parameters"></a>パラメーター

*n Align*<br/>
からテキストの配置の列挙値。 使用可能な値については、「解説」を参照してください。

### <a name="remarks"></a>Remarks

パラメーター *n align*は、次のいずれかの編集コントロールスタイルです。

- 左揃えの場合は ES_LEFT

- CENTER の配置のための ES_CENTER

- 右揃えの ES_RIGHT

これらのスタイルの詳細については、「[コントロールスタイルの編集](/windows/win32/Controls/edit-control-styles)」を参照してください。

##  <a name="setwidth"></a>CMFCRibbonEdit:: SetWidth

[CMFCRibbonEdit](../../mfc/reference/cmfcribbonedit-class.md)コントロールのテキストボックスの幅を設定します。

```
void SetWidth(
    int nWidth,
    BOOL bInFloatyMode = FALSE);
```

### <a name="parameters"></a>パラメーター

*nWidth*<br/>
からテキストボックスの幅 (ピクセル単位)。

*bInFloatyMode*<br/>
フローティングモードの幅を設定する場合は TRUE。標準モードの幅を設定する場合は FALSE。

### <a name="remarks"></a>Remarks

`CMFCRibbonEdit`コントロールには、表示モード (フローティングモードと通常モード) に応じて2つの幅があります。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonButton クラス](../../mfc/reference/cmfcribbonbutton-class.md)<br/>
[CMFCRibbonBar クラス](../../mfc/reference/cmfcribbonbar-class.md)
