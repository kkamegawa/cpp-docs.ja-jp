---
title: CMFCRibbonCheckBox クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::CMFCRibbonCheckBox
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetCompactSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetIntermediateSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::GetRegularSize
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::IsDrawTooltipImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDraw
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawMenuImage
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::OnDrawOnList
- AFXRIBBONCHECKBOX/CMFCRibbonCheckBox::SetACCData
helpviewer_keywords:
- CMFCRibbonCheckBox [MFC], CMFCRibbonCheckBox
- CMFCRibbonCheckBox [MFC], GetCompactSize
- CMFCRibbonCheckBox [MFC], GetIntermediateSize
- CMFCRibbonCheckBox [MFC], GetRegularSize
- CMFCRibbonCheckBox [MFC], IsDrawTooltipImage
- CMFCRibbonCheckBox [MFC], OnDraw
- CMFCRibbonCheckBox [MFC], OnDrawMenuImage
- CMFCRibbonCheckBox [MFC], OnDrawOnList
- CMFCRibbonCheckBox [MFC], SetACCData
ms.assetid: 3a6c3891-c8d1-4af0-b954-7b9ab048782a
ms.openlocfilehash: 34af1ae818125abd51b9eaf04cd98f9ac24addb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392545"
---
# <a name="cmfcribboncheckbox-class"></a>CMFCRibbonCheckBox クラス

`CMFCRibbonCheckBox` クラスは、リボン パネル、クイック アクセス ツール バー、またはポップアップ メニューに追加できるチェック ボックスを実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonCheckBox : public CMFCRibbonButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonCheckBox::CMFCRibbonCheckBox](#cmfcribboncheckbox)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonCheckBox::GetCompactSize](#getcompactsize)|(上書き[cmfcribbonbutton::getcompactsize](../../mfc/reference/cmfcribbonbutton-class.md#getcompactsize))。|
|[CMFCRibbonCheckBox::GetIntermediateSize](#getintermediatesize)|(上書き[cmfcribbonbutton::getintermediatesize](../../mfc/reference/cmfcribbonbutton-class.md#getintermediatesize))。|
|[CMFCRibbonCheckBox::GetRegularSize](#getregularsize)|(上書き[cmfcribbonbutton::getregularsize](../../mfc/reference/cmfcribbonbutton-class.md#getregularsize))。|
|[CMFCRibbonCheckBox::IsDrawTooltipImage](#isdrawtooltipimage)|( `CMFCRibbonButton::IsDrawTooltipImage`をオーバーライドします)。|
|[CMFCRibbonCheckBox::OnDraw](#ondraw)|(上書き[cmfcribbonbutton::ondraw](../../mfc/reference/cmfcribbonbutton-class.md#ondraw))。|
|[CMFCRibbonCheckBox::OnDrawMenuImage](#ondrawmenuimage)|(上書き[cmfcribbonbaseelement::ondrawmenuimage](../../mfc/reference/cmfcribbonbaseelement-class.md#ondrawmenuimage))。|
|[CMFCRibbonCheckBox::OnDrawOnList](#ondrawonlist)|( `CMFCRibbonButton::OnDrawOnList`をオーバーライドします)。|
|[CMFCRibbonCheckBox::SetACCData](#setaccdata)|(上書き[cmfcribbonbutton::setaccdata](../../mfc/reference/cmfcribbonbutton-class.md#setaccdata))。|

## <a name="remarks"></a>Remarks

`CMFCRibbonCheckBox` をアプリケーションで使用するには、次のコンストラクターをコードに追加します。

```
CMFCRibbonCheckBox (UINT nID, LPCTSTR lpszText)
```
場所*nID*  チェック ボックスのコマンド id と*lpszText*  チェック ボックスのテキスト ラベルします。

チェック ボックスをリボン パネルに追加するにを使用して[cmfcribbonpanel::add](../../mfc/reference/cmfcribbonpanel-class.md#add)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonButton](../../mfc/reference/cmfcribbonbutton-class.md)

[CMFCRibbonCheckBox](../../mfc/reference/cmfcribboncheckbox-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribboncheckbox.h

##  <a name="cmfcribboncheckbox"></a>  CMFCRibbonCheckBox::CMFCRibbonCheckBox

リボンのチェック ボックスをオブジェクトのコンス トラクター

```
CMFCRibbonCheckBox(
    UINT nID,
    LPCTSTR lpszText);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
[in]コマンド ID を指定します

*lpszText*<br/>
[in]テキスト ラベルを指定します。

### <a name="return-value"></a>戻り値

リボンのチェック ボックス オブジェクトを構築します。

### <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCRibbonCheckBox`クラス。

[!code-cpp[NVC_MFC_RibbonApp#17](../../mfc/reference/codesnippet/cpp/cmfcribboncheckbox-class_1.cpp)]

##  <a name="getcompactsize"></a>  CMFCRibbonCheckBox::GetCompactSize

オーバーライドされた場合、チェック ボックスのコンパクト サイズを取得します。

```
virtual CSize GetCompactSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]チェック ボックスに関連付けられている CDC へのポインター。

### <a name="return-value"></a>戻り値

返します、`CSize`チェック ボックスのコンパクト サイズを格納しているオブジェクト。

### <a name="remarks"></a>Remarks

オーバーライドされていない場合は、チェック ボックスの中間のサイズを返します。

##  <a name="getintermediatesize"></a>  CMFCRibbonCheckBox::GetIntermediateSize

チェック ボックスの中間のサイズを取得します。

```
virtual CSize GetIntermediateSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]このチェック ボックスをオンに関連付けられている CDC へのポインター。

### <a name="return-value"></a>戻り値

A`CSize`中間サイズのチェック ボックスを含むオブジェクト。

### <a name="remarks"></a>Remarks

オーバーライドされていない場合は、既定のチェック ボックスのサイズとして中間のサイズを計算 ( `AFX_CHECK_BOX_DEFAULT_SIZE`) さらには、テキストのサイズと余白。

##  <a name="getregularsize"></a>  CMFCRibbonCheckBox::GetRegularSize

チェック ボックスの標準サイズを取得します。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]このチェック ボックスをオンに関連付けられている CDC オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

返します、`CSize`チェック ボックスの標準サイズを格納しているオブジェクト。

### <a name="remarks"></a>Remarks

オーバーライドされていない場合は、チェック ボックスの中間のサイズを返します。

##  <a name="isdrawtooltipimage"></a>  CMFCRibbonCheckBox::IsDrawTooltipImage

チェック ボックスに関連付けられているツールヒント イメージがあるかどうかを示します。

```
virtual BOOL IsDrawTooltipImage() const;
```

### <a name="return-value"></a>戻り値

チェック ボックスを関連付けられているツールヒント イメージがある場合は TRUE または FALSE の場合を返します。

### <a name="remarks"></a>Remarks

##  <a name="ondraw"></a>  CMFCRibbonCheckBox::OnDraw

指定したデバイス コンテキストを使用して、チェック ボックスを描画するためにフレームワークによって呼び出されます。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
[in]チェック ボックスを描画するための CDC へのポインター。

### <a name="remarks"></a>Remarks

##  <a name="ondrawmenuimage"></a>  CMFCRibbonCheckBox::OnDrawMenuImage

チェック ボックスのメニュー画像を描画するためにフレームワークによって呼び出されます。

```
virtual BOOL OnDrawMenuImage(CDC*, CRect);
```

### <a name="parameters"></a>パラメーター

[in]*CDC&#42;*<br/>
チェック ボックスに関連付けられている CDC へのポインター。

*CRect*<br/>
[in]A`CRect`メニュー画像を描画する四角形を指定するオブジェクト。

### <a name="return-value"></a>戻り値

TRUE の場合は、イメージが描画された、またはしない場合は FALSE を返します。

### <a name="remarks"></a>Remarks

オーバーライドされていない場合は、FALSE を返します。

##  <a name="ondrawonlist"></a>  CMFCRibbonCheckBox::OnDrawOnList

コマンドのリスト ボックスで、チェック ボックスを描画するためにフレームワークによって呼び出されます。

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
[in]チェック ボックスを描画するためのデバイス コンテキストへのポインター。

*strText*<br/>
[in]表示テキスト。

*nTextOffset*<br/>
[in]テキストを表示、リスト ボックスの左側からのピクセル単位の距離です。

*rect*<br/>
[in]チェック ボックスを表示する四角形。

*bIsSelected*<br/>
[in]TRUE の場合、チェック ボックスが選択されている、またはしない場合は FALSE。

*bHighlighted*<br/>
[in]TRUE の場合、チェック ボックスが強調表示されている、またはしない場合は FALSE。

### <a name="remarks"></a>Remarks

##  <a name="setaccdata"></a>  CMFCRibbonCheckBox::SetACCData

チェック ボックスのアクセシビリティ データを設定します。

```
virtual BOOL SetACCData(
    CWnd* pParent,
    CAccessibilityData& data);
```

### <a name="parameters"></a>パラメーター

*pParent*<br/>
チェック ボックスの親ウィンドウ。

*data*<br/>
チェック ボックスのユーザー補助データ。

### <a name="return-value"></a>戻り値

常に TRUE を返します。

### <a name="remarks"></a>Remarks

既定では、このメソッドは、チェック ボックスのアクセシビリティ データを設定し、常に TRUE を返します。 アクセシビリティ データを設定し、成功または失敗を示す値を返すようにするには、このメソッドをオーバーライドします。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonPanel クラス](../../mfc/reference/cmfcribbonpanel-class.md)
