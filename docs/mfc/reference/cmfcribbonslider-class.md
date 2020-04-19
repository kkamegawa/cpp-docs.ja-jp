---
title: CMFCRibbonSlider クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::CMFCRibbonSlider
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMax
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRangeMin
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetRegularSize
- AFXRIBBONSLIDER/CMFCRibbonSlider::GetZoomIncrement
- AFXRIBBONSLIDER/CMFCRibbonSlider::HasZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::OnDraw
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetPos
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetRange
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomButtons
- AFXRIBBONSLIDER/CMFCRibbonSlider::SetZoomIncrement
helpviewer_keywords:
- CMFCRibbonSlider [MFC], CMFCRibbonSlider
- CMFCRibbonSlider [MFC], GetPos
- CMFCRibbonSlider [MFC], GetRangeMax
- CMFCRibbonSlider [MFC], GetRangeMin
- CMFCRibbonSlider [MFC], GetRegularSize
- CMFCRibbonSlider [MFC], GetZoomIncrement
- CMFCRibbonSlider [MFC], HasZoomButtons
- CMFCRibbonSlider [MFC], OnDraw
- CMFCRibbonSlider [MFC], SetPos
- CMFCRibbonSlider [MFC], SetRange
- CMFCRibbonSlider [MFC], SetZoomButtons
- CMFCRibbonSlider [MFC], SetZoomIncrement
ms.assetid: 9351ac34-f234-4e42-91e2-763f1989c8ff
ms.openlocfilehash: 85c646e2fa524268e4559b587f90c5e06971b765
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374078"
---
# <a name="cmfcribbonslider-class"></a>CMFCRibbonSlider クラス

`CMFCRibbonSlider`クラスは、リボン バーまたはリボン ステータス バーに追加できるスライダー コントロールを実装します。 リボン スライダー コントロールは、Office 2007 アプリケーションに表示されるズーム スライダーに似ています。

## <a name="syntax"></a>構文

```
class CMFCRibbonSlider : public CMFCRibbonBaseElement
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonSlider::CMFCRibbonSlider](#cmfcribbonslider)|構築し、リボンのスライダー コントロールを初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonSlider::GetPos](#getpos)|スライダー コントロールの現在位置を返します。|
|[CMFCRibbonSlider::GetRangeMax](#getrangemax)|スライダーの最大値を返します。|
|[CMFCRibbonSlider::GetRangeMin](#getrangemin)|スライダーの最小値を返します。|
|[CMFCRibbonSlider::GetRegularSize](#getregularsize)|リボン要素の標準サイズを返します。 (上書き[cmfcribbonbaseelement::getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize))。|
|[CMFCRibbonSlider::GetZoomIncrement](#getzoomincrement)|スライダー コントロールのズーム インクリメントのサイズを返します。|
|[CMFCRibbonSlider::HasZoomButtons](#haszoombuttons)|スライダーがズーム ボタンを持つかどうかを指定します。|
|[CMFCRibbonSlider::OnDraw](#ondraw)|リボン要素を描画するために、フレームワークによって呼び出されます。 (上書き[cmfcribbonbaseelement::ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw))。|
|[CMFCRibbonSlider::SetPos](#setpos)|スライダー コントロールの現在の位置を設定します。|
|[CMFCRibbonSlider::SetRange](#setrange)|スライダー コントロールの範囲を指定するには、最小値と最大値を設定します。|
|[CMFCRibbonSlider::SetZoomButtons](#setzoombuttons)|表示とズーム ボタンを非表示します。|
|[CMFCRibbonSlider::SetZoomIncrement](#setzoomincrement)|スライダー コントロールのズーム インクリメントのサイズを設定します。|

## <a name="remarks"></a>Remarks

使用することができます、`SetRange`スライダーのズーム インクリメントの範囲を構成する方法。 使用して、スライダーの現在の位置を設定することができます、`SetPos`メソッド。

使用して、左側と右側にあるスライダー コントロールの循環のズーム ボタンを表示することができます、`SetZoomButtons`メソッド。 既定では、スライダーは水平方向、左のズーム ボタンにマイナス記号を表示および右のズーム ボタンは、プラス記号を表示します。

`SetZoomIncrement`メソッドに追加したり、ユーザーがズーム ボタンをクリックすると、現在の位置から減算する単位を定義します。

## <a name="example"></a>例

次の例では、さまざまなメソッドを使用する方法、`CMFCRibbonSlider`スライダーのプロパティを設定するクラス。 例では、作成する方法を示しています、`CMFCRibbonSlider`オブジェクトでズーム ボタンを表示、スライダー コントロールの現在の位置を設定し、スライダー コントロールの値の範囲を設定します。

[!code-cpp[NVC_MFC_RibbonApp#12](../../mfc/reference/codesnippet/cpp/cmfcribbonslider-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonSlider](../../mfc/reference/cmfcribbonslider-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribbonslider.h

##  <a name="cmfcribbonslider"></a>  CMFCRibbonSlider::CMFCRibbonSlider

リボン スライダーを構築します。

```
CMFCRibbonSlider(
    UINT nID,
    int nWidth=100);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
[in]スライダーの id。

[in]。 *nWidth*スライダーの幅 (ピクセル単位)。

### <a name="remarks"></a>Remarks

リボン スライダーを構築します*nWidth*スライダーの追加パネルのカテゴリの幅はピクセル。 既定では、スライダーは水平方向です。

##  <a name="getpos"></a>  CMFCRibbonSlider::GetPos

スライダー コントロールの現在位置を返します。

```
int GetPos() const;
```

### <a name="return-value"></a>戻り値

スライダーの先頭からの相対位置であるスライダー コントロールの現在の位置。

##  <a name="getrangemax"></a>  CMFCRibbonSlider::GetRangeMax

スライダー コントロールのスライダーを移動できるスライダーの最大の増分値を取得します。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>戻り値

スライダー コントロールのスライダーを移動できるスライダーの最大の増分値。

##  <a name="getrangemin"></a>  CMFCRibbonSlider::GetRangeMin

スライダー コントロールのスライダーを移動できる最小の増分値を返します。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>戻り値

スライダー コントロールのスライダーを移動できる最小の増分値。

##  <a name="getregularsize"></a>  CMFCRibbonSlider::GetRegularSize

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

[in]*pDC*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="getzoomincrement"></a>  CMFCRibbonSlider::GetZoomIncrement

スライダー コントロールのズーム インクリメントを取得します。

```
int GetZoomIncrement() const;
```

### <a name="return-value"></a>戻り値

スライダー コントロールのズーム インクリメントします。

##  <a name="haszoombuttons"></a>  CMFCRibbonSlider::HasZoomButtons

スライダーがズーム ボタンを持つかどうかを指定します。

```
BOOL HasZoomButtons() const;
```

### <a name="return-value"></a>戻り値

TRUE の場合は、スライダーがあるズーム ボタンFALSE それ以外の場合。

##  <a name="ondraw"></a>  CMFCRibbonSlider::OnDraw

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

[in]*pDC*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setpos"></a>  CMFCRibbonSlider::SetPos

スライダー コントロールの現在の位置を設定します。

```
void SetPos(
    int nPos,
    BOOL bRedraw=TRUE);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
[in]スライダーに設定する位置を指定します。 位置では、スライダーの開始位置を基準です。

*bRedraw*<br/>
[in]TRUE の場合、スライダーが再描画されます。

##  <a name="setrange"></a>  CMFCRibbonSlider::SetRange

スライダー コントロールの値の範囲を設定します。

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>パラメーター

*nMin*<br/>
[in]スライダー コントロールの最小値を指定します。

*nMax*<br/>
[in]スライダー コントロールの最大値を指定します。

### <a name="remarks"></a>Remarks

スライダー コントロールの値の範囲を指定するには、最小値と最大値を設定します。

##  <a name="setzoombuttons"></a>  CMFCRibbonSlider::SetZoomButtons

表示またはズーム ボタンを非表示にします。

```
void SetZoomButtons(BOOL bSet=TRUE);
```

### <a name="parameters"></a>パラメーター

[in]。 *bSet*ズーム ボタンを表示する以外の場合は true非表示にする場合は FALSE。

##  <a name="setzoomincrement"></a>  CMFCRibbonSlider::SetZoomIncrement

スライダー コントロールのズーム インクリメントを設定します。

```
void SetZoomIncrement(int nZoomIncrement);
```

### <a name="parameters"></a>パラメーター

*nZoomIncrement*<br/>
[in]スライダー コントロールのズーム インクリメントを指定します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement クラス](../../mfc/reference/cmfcribbonbaseelement-class.md)
