---
title: CMFCRibbonProgressBar クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::CMFCRibbonProgressBar
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMax
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRangeMin
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::GetRegularSize
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::IsInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::OnDraw
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetInfiniteMode
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetPos
- AFXRIBBONPROGRESSBAR/CMFCRibbonProgressBar::SetRange
helpviewer_keywords:
- CMFCRibbonProgressBar [MFC], CMFCRibbonProgressBar
- CMFCRibbonProgressBar [MFC], GetPos
- CMFCRibbonProgressBar [MFC], GetRangeMax
- CMFCRibbonProgressBar [MFC], GetRangeMin
- CMFCRibbonProgressBar [MFC], GetRegularSize
- CMFCRibbonProgressBar [MFC], IsInfiniteMode
- CMFCRibbonProgressBar [MFC], OnDraw
- CMFCRibbonProgressBar [MFC], SetInfiniteMode
- CMFCRibbonProgressBar [MFC], SetPos
- CMFCRibbonProgressBar [MFC], SetRange
ms.assetid: de3d9f2e-ed59-480e-aa7d-08a33ab36c67
ms.openlocfilehash: 7c16217378cb8825ca4605687770de177e720c1d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391115"
---
# <a name="cmfcribbonprogressbar-class"></a>CMFCRibbonProgressBar クラス

時間のかかる操作の進行状況を視覚的に示すコントロールを実装します。

## <a name="syntax"></a>構文

```
class CMFCRibbonProgressBar : public CMFCRibbonBaseElement
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonProgressBar::CMFCRibbonProgressBar](#cmfcribbonprogressbar)|`CMFCRibbonProgressBar` オブジェクトを構築して初期化します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CMFCRibbonProgressBar::GetPos](#getpos)|現在の進行状況を返します。|
|[CMFCRibbonProgressBar::GetRangeMax](#getrangemax)|現在の範囲の最大値を返します。|
|[CMFCRibbonProgressBar::GetRangeMin](#getrangemin)|現在の範囲の最小値を返します。|
|[CMFCRibbonProgressBar::GetRegularSize](#getregularsize)|リボン要素の標準サイズを返します。 (上書き[cmfcribbonbaseelement::getregularsize](../../mfc/reference/cmfcribbonbaseelement-class.md#getregularsize))。|
|[CMFCRibbonProgressBar::IsInfiniteMode](#isinfinitemode)|進行状況バーが無限のモードで動作しているかどうかを指定します。|
|[CMFCRibbonProgressBar::OnDraw](#ondraw)|リボン要素を描画するために、フレームワークによって呼び出されます。 (上書き[cmfcribbonbaseelement::ondraw](../../mfc/reference/cmfcribbonbaseelement-class.md#ondraw))。|
|[CMFCRibbonProgressBar::SetInfiniteMode](#setinfinitemode)|無限のモードで動作する進行状況バーを設定します。|
|[CMFCRibbonProgressBar::SetPos](#setpos)|現在の進行状況を設定します。|
|[CMFCRibbonProgressBar::SetRange](#setrange)|最小値と最大値を設定します。|

## <a name="remarks"></a>Remarks

A`CMFCRibbonProgressBar`は 2 つのモードで動作します。 正規表現と無限。 通常モードで進行状況バーが左から右に入力され、最大値に達すると停止します。 無限のモードでは、進行状況バーが繰り返し最小値から最大値に入力されます。 無限のモードを使用して、操作が進行中であるが、完了時間が不明である可能性があります。

## <a name="example"></a>例

`CMFCRibbonProgressBar` クラスのさまざまなメソッドの使用方法を次の例に示します。 例は、進行状況バーの最小値と最大値を設定し、進行状況バーの現在の位置を設定 (操作の完了時間はない既知) 無限のモードで動作する進行状況バーを設定する方法を示します。 このコード スニペットの一部、 [MS Office 2007 のデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_MSOffice2007Demo#11](../../mfc/reference/codesnippet/cpp/cmfcribbonprogressbar-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CMFCRibbonBaseElement](../../mfc/reference/cmfcribbonbaseelement-class.md)

[CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxRibbonProgressBar.h

##  <a name="cmfcribbonprogressbar"></a>  CMFCRibbonProgressBar::CMFCRibbonProgressBar

構築し、初期化、 [CMFCRibbonProgressBar](../../mfc/reference/cmfcribbonprogressbar-class.md)オブジェクト。

```
CMFCRibbonProgressBar();

CMFCRibbonProgressBar(
    UINT nID,
    int nWidth = 90,
    int nHeight = 22);
```

### <a name="parameters"></a>パラメーター

*nID*<br/>
[in]リボンの進行状況バーのコマンド ID を指定します。

*nWidth*<br/>
[in]リボンの進行状況バーのピクセル単位の幅を指定します。

*nHeight*<br/>
[in]リボンの進行状況バーのピクセル、高さを指定します。

##  <a name="getpos"></a>  CMFCRibbonProgressBar::GetPos

進行状況バーの現在位置を返します。

```
int GetPos () const;
```

### <a name="return-value"></a>戻り値

進行状況バーの現在の位置を表す値。

### <a name="remarks"></a>Remarks

指定された範囲内で、範囲が設定されている必要があります、 [CMFCRibbonProgressBar::SetRange](#setrange)メソッド。

##  <a name="getrangemax"></a>  CMFCRibbonProgressBar::GetRangeMax

返します、進行状況バーの現在の最大値。

```
int GetRangeMax() const;
```

### <a name="return-value"></a>戻り値

現在の範囲の最大値。

### <a name="remarks"></a>Remarks

##  <a name="getrangemin"></a>  CMFCRibbonProgressBar::GetRangeMin

進行状況バーの現在の返します範囲の最小値。

```
int GetRangeMin() const;
```

### <a name="return-value"></a>戻り値

現在の範囲の最小値。

##  <a name="getregularsize"></a>  CMFCRibbonProgressBar::GetRegularSize

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual CSize GetRegularSize(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

[in]*pDC*<br/>

### <a name="return-value"></a>戻り値

### <a name="remarks"></a>Remarks

##  <a name="isinfinitemode"></a>  CMFCRibbonProgressBar::IsInfiniteMode

進行状況バーが無限のモードで動作しているかどうかを指定します。

```
BOOL IsInfiniteMode() const;
```

### <a name="return-value"></a>戻り値

進行状況バーが無限モードでは、TRUE を返します。それ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

無限のモードでは、進行状況バーは最小値から最大値に繰り返し塗りつぶされます。 無限のモードを使用して、操作が進行中であるが、完了時間が不明である可能性があります。

##  <a name="ondraw"></a>  CMFCRibbonProgressBar::OnDraw

詳細についてにあるソース コードを参照してください、 **VC\\atlmfc\\src\\mfc** Visual Studio のインストールのフォルダー。

```
virtual void OnDraw(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

[in]*pDC*<br/>

### <a name="remarks"></a>Remarks

##  <a name="setinfinitemode"></a>  CMFCRibbonProgressBar::SetInfiniteMode

無限のモードで動作する進行状況バーを設定します。

```
void SetInfiniteMode(BOOL bSet = TRUE);
```

### <a name="parameters"></a>パラメーター

*bSet*<br/>
[in]進行状況バーが、無限モードを指定する場合は TRUEそれ以外の場合、FALSE です。

### <a name="remarks"></a>Remarks

通常は、進行状況バーが無限のモードである場合は、それをユーザーに通知操作が進行中であるが、完了時間が不明であります。 したがって、進行状況バー繰り返し塗りつぶさ最小値から最大値にします。

##  <a name="setpos"></a>  CMFCRibbonProgressBar::SetPos

進行状況バーの現在の位置を設定します。

```
void SetPos(
    int nPos,
    BOOL bRedraw = TRUE);
```

### <a name="parameters"></a>パラメーター

*nPos*<br/>
[in]進行状況バーを設定する位置を指定します。

*bRedraw*<br/>
[in]進行状況バーが再描画が必要かどうかを指定します。

### <a name="remarks"></a>Remarks

指定された範囲内で、範囲が設定されている必要があります、 [CMFCRibbonProgressBar::SetRange](#setrange)メソッド。

##  <a name="setrange"></a>  CMFCRibbonProgressBar::SetRange

進行状況バーの最小値と最大値を設定します。

```
void SetRange(
    int nMin,
    int nMax);
```

### <a name="parameters"></a>パラメーター

*nMin*<br/>
[in]範囲の最小値を指定します。

*nMax*<br/>
[in]範囲の最大値を指定します。

### <a name="remarks"></a>Remarks

最小値と最大値を設定して、進行状況バーの範囲を定義するのにには、このメソッドを使用します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCRibbonBaseElement クラス](../../mfc/reference/cmfcribbonbaseelement-class.md)<br/>
[CMFCRibbonBar クラス](../../mfc/reference/cmfcribbonbar-class.md)
