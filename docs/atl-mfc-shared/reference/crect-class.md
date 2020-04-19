---
title: CRect クラス
ms.date: 11/06/2018
f1_keywords:
- CRect
- ATLTYPES/ATL::CRect
- ATLTYPES/ATL::CRect::CRect
- ATLTYPES/ATL::CRect::BottomRight
- ATLTYPES/ATL::CRect::CenterPoint
- ATLTYPES/ATL::CRect::CopyRect
- ATLTYPES/ATL::CRect::DeflateRect
- ATLTYPES/ATL::CRect::EqualRect
- ATLTYPES/ATL::CRect::Height
- ATLTYPES/ATL::CRect::InflateRect
- ATLTYPES/ATL::CRect::IntersectRect
- ATLTYPES/ATL::CRect::IsRectEmpty
- ATLTYPES/ATL::CRect::IsRectNull
- ATLTYPES/ATL::CRect::MoveToX
- ATLTYPES/ATL::CRect::MoveToXY
- ATLTYPES/ATL::CRect::MoveToY
- ATLTYPES/ATL::CRect::NormalizeRect
- ATLTYPES/ATL::CRect::OffsetRect
- ATLTYPES/ATL::CRect::PtInRect
- ATLTYPES/ATL::CRect::SetRect
- ATLTYPES/ATL::CRect::SetRectEmpty
- ATLTYPES/ATL::CRect::Size
- ATLTYPES/ATL::CRect::SubtractRect
- ATLTYPES/ATL::CRect::TopLeft
- ATLTYPES/ATL::CRect::UnionRect
- ATLTYPES/ATL::CRect::Width
helpviewer_keywords:
- LPCRECT data type
- CRect class
- LPRECT operator
- RECT structure
ms.assetid: dee4e752-15d6-4db4-b68f-1ad65b2ed6ca
ms.openlocfilehash: 13f86c411cca98f5817d1b3b2d9162ae8af8b734
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/06/2020
ms.locfileid: "78866533"
---
# <a name="crect-class"></a>CRect クラス

Windows の[RECT](/windows/win32/api/windef/ns-windef-rect)構造体に似ています。

## <a name="syntax"></a>構文

```
class CRect : public tagRECT
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|Name|Description|
|----------|-----------------|
|[CRect:: CRect](#crect)|`CRect` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|Name|Description|
|----------|-----------------|
|[CRect:: 右下](#bottomright)|`CRect`の右下の点を返します。|
|[CRect:: 小惑星](#centerpoint)|`CRect`の小惑星を返します。|
|[CRect:: CopyRect](#copyrect)|コピー元の四角形の寸法を `CRect`にコピーします。|
|[CRect::D eflateRect](#deflaterect)|`CRect`の幅と高さを小さくします。|
|[CRect:: EqualRect](#equalrect)|`CRect` が、指定された四角形と等しいかどうかを判断します。|
|[CRect:: Height](#height)|`CRect`の高さを計算します。|
|[CRect:: InflateRect](#inflaterect)|`CRect`の幅と高さを大きくします。|
|[CRect:: IntersectRect](#intersectrect)|2つの四角形の交差部分に等しい `CRect` を設定します。|
|[CRect:: IsRectEmpty](#isrectempty)|`CRect` が空かどうかを判断します。 幅と高さのどちらかまたは両方が0の場合、`CRect` は空になります。|
|[CRect:: IsRectNull](#isrectnull)|`top`、`bottom`、`left`、および `right` のメンバー変数がすべて0に等しいかどうかを判断します。|
|[CRect:: MoveToX](#movetox)|`CRect` を指定した x 座標に移動します。|
|[CRect:: MoveToXY](#movetoxy)|指定した x 座標と y 座標に `CRect` を移動します。|
|[CRect:: MoveToY](#movetoy)|`CRect` を指定した y 座標に移動します。|
|[CRect:: NormalizeRect](#normalizerect)|`CRect`の高さと幅を標準化します。|
|[CRect:: OffsetRect](#offsetrect)|指定したオフセットだけ `CRect` を移動します。|
|[CRect::P の実行](#ptinrect)|指定したポイントが `CRect`内にあるかどうかを判断します。|
|[CRect:: SetRect](#setrect)|`CRect`の大きさを設定します。|
|[CRect:: SetRectEmpty](#setrectempty)|`CRect` を空の四角形 (すべての座標が0に等しい) に設定します。|
|[CRect:: Size](#size)|`CRect`のサイズを計算します。|
|[CRect:: SubtractRect](#subtractrect)|ある四角形を別の四角形から減算します。|
|[CRect:: TopLeft](#topleft)|`CRect`の左上の点を返します。|
|[CRect:: UnionRect](#unionrect)|2つの四角形の和集合に等しい `CRect` を設定します。|
|[CRect:: Width](#width)|`CRect`の幅を計算します。|

### <a name="public-operators"></a>パブリック演算子

|Name|Description|
|----------|-----------------|
|[CRect:: operator-](#operator_-)|`CRect` または縮小 `CRect` から指定されたオフセットを減算し、結果として得られる `CRect`を返します。|
|[CRect:: operator LPCRECT](#operator_lpcrect)|`CRect` を `LPCRECT` に変換します。|
|[CRect:: operator LPRECT](#operator_lprect)|`CRect` を `LPRECT` に変換します。|
|[CRect:: operator! =](#operator_neq)|`CRect` が四角形と等しくないかどうかを判断します。|
|[CRect:: operator &amp;](#operator_amp)|`CRect` と四角形の交差部分を作成し、結果として得られる `CRect`を返します。|
|[CRect:: operator &amp;=](#operator_amp_eq)|`CRect` と四角形の交差部分に等しい `CRect` 設定します。|
|[CRect:: operator&#124;](#operator_or)|`CRect` と四角形の和集合を作成し、結果として得られる `CRect`を返します。|
|[CRect:: operator &#124;=](#operator_or_eq)|`CRect` と四角形の和集合に等しい `CRect` 設定します。|
|[CRect:: operator +](#operator_add)|指定されたオフセットを `CRect` または増え `CRect` に追加し、結果として得られる `CRect`を返します。|
|[CRect:: operator + =](#operator_add_eq)|`CRect` または増え `CRect`に指定されたオフセットを追加します。|
|[CRect:: operator =](#operator_eq)|四角形の寸法を `CRect`にコピーします。|
|[CRect:: operator-=](#operator_-_eq)|`CRect` または縮小 `CRect`から指定されたオフセットを減算します。|
|[CRect:: operator = =](#operator_eq_eq)|`CRect` が四角形と等しいかどうかを判断します。|

## <a name="remarks"></a>解説

`CRect` には、`CRect` オブジェクトと Windows `RECT` 構造体を操作するためのメンバー関数も含まれています。

`CRect` オブジェクトは、`RECT` 構造体、`LPCRECT`、または `LPRECT` を渡すことができる場所であれば、関数パラメーターとして渡すことができます。

> [!NOTE]
> このクラスは `tagRECT` 構造体から派生します。 (名前 `tagRECT` は、`RECT` 構造体に使用頻度の低い名前です)。これは、`RECT` 構造体のデータメンバー (`left`、`top`、`right`、および `bottom`) が `CRect`のアクセス可能なデータメンバーであることを意味します。

`CRect` には、四角形の左上および右下の点を定義するメンバー変数が含まれています。

`CRect`を指定するときは、その値が正規化されるように注意する必要があります。つまり、左の座標の値が右側より小さく、上の値が下部よりも小さくなるようにします。 たとえば、の左上 (10, 10) と右下 (20, 20) は正規化された四角形を定義しますが、(10, 10) の左上 (20, 20) と右下 (10, 10) は正規化されていない四角形を定義します。 四角形が正規化されていない場合、多くの `CRect` メンバー関数が正しくない結果を返す可能性があります。 (これらの関数の一覧については、「 [CRect:: NormalizeRect](#normalizerect) 」を参照してください)。正規化された四角形を必要とする関数を呼び出す前に、`NormalizeRect` 関数を呼び出すことにより、正規化されていない四角形を正規化できます。

[Cdc::D PtoLP](../../mfc/reference/cdc-class.md#dptolp)および[Cdc:: lptodp](../../mfc/reference/cdc-class.md#lptodp)メンバー関数を使用して `CRect` を操作する場合は注意が必要です。 `MM_LOENGLISH`のように、表示コンテキストのマッピングモードが y 範囲に負の値になるような場合、`CDC::DPtoLP` によって `CRect` が変換され、その上部が下部よりも大きくなります。 `Height` や `Size` などの関数は、変換された `CRect`の高さに対して負の値を返し、四角形は非正規化になります。

オーバーロードされた `CRect` 演算子を使用する場合、最初のオペランドは `CRect`である必要があります。2つ目は、 [RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトのいずれかです。

## <a name="inheritance-hierarchy"></a>継承階層

`tagRECT`

`CRect`

## <a name="requirements"></a>必要条件

**ヘッダー:** atltypes. h

##  <a name="bottomright"></a>CRect:: 右下

座標は、`CRect`に含まれる[CPoint](cpoint-class.md)オブジェクトへの参照として返されます。

```
CPoint& BottomRight() throw();
const CPoint& BottomRight() const throw();
```

### <a name="return-value"></a>戻り値

四角形の右下隅の座標です。

### <a name="remarks"></a>解説

この関数を使用すると、四角形の右下隅を取得または設定できます。 代入演算子の左側にあるこの関数を使用して、コーナーを設定します。

### <a name="example"></a>例

```cpp
// use BottomRight() to retrieve the bottom
// right POINT
CRect rect(210, 150, 350, 900);
CPoint ptDown;

ptDown = rect.BottomRight();

// ptDown is now set to (350, 900)
ASSERT(ptDown == CPoint(350, 900));

// or, use BottomRight() to set the bottom
// right POINT
CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);

CRect rect2(10, 10, 350, 350);
CPoint ptLow(180, 180);
rect2.BottomRight() = ptLow;

// rect2 is now (10, 10, 180, 180)
ASSERT(rect2 == CRect(10, 10, 180, 180));
```

##  <a name="centerpoint"></a>CRect:: 小惑星

左右の値を加算して2で割ることによって `CRect` の小惑星を計算し、上と下の値を加算して2で除算します。

```
CPoint CenterPoint() const throw();
```

### <a name="return-value"></a>戻り値

`CRect`の小惑星である `CPoint` オブジェクト。

### <a name="example"></a>例

```cpp
// Code from this OnPaint() implementation can be pasted into your own application
// to draw lines that would look like a letter "Y" within your dialog.
void CMyDlg::OnPaint()
{
    CPaintDC dc(this);

    // device context for painting

    // get the size and position of the client area of
    // your window

    CRect rect;
    GetClientRect(&rect);

    // Move the current pen to the top left of the window. We call the
    // TopLeft() member of CRect here and it returns a CPoint object we
    // pass to the override of CDC::MoveTo() that accepts a CPoint.

    dc.MoveTo(rect.TopLeft());

    // Draw a line from the top left to the center of the window.
    // CenterPoint() gives us the middle point of the window as a
    // CPoint, and since CDC::LineTo() has an override that accepts a
    // CPoint, we can just pass it along.

    dc.LineTo(rect.CenterPoint());

    // Now, draw a line to the top right of the window. There's no
    // CRect member which returns a CPoint for the top right of the
    // window, so we'll reference the CPoint members directly and call
    // the CDC::LineTo() override which takes two integers.

    dc.LineTo(rect.right, rect.top);

    // The top part of the "Y" is drawn. Now, we'll draw the stem. We
    // start from the center point.

    dc.MoveTo(rect.CenterPoint());

    // and then draw to the middle of the bottom edge of the window.
    // We'll get the x-coordinate from the x member of the CPOINT
    // returned by CenterPoint(), and the y value comes directly from
    // the rect.

    dc.LineTo(rect.CenterPoint().x, rect.bottom);
}
```

##  <a name="copyrect"></a>CRect:: CopyRect

`CRect`に `lpSrcRect` 四角形をコピーします。

```
void CopyRect(LPCRECT lpSrcRect) throw();
```

### <a name="parameters"></a>パラメーター

*lpSrcRect*<br/>
コピーする[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトをポイントします。

### <a name="example"></a>例

```cpp
CRect rectSource(35, 10, 125, 10);
CRect rectDest;

rectDest.CopyRect(&rectSource);

// rectDest is now set to (35, 10, 125, 10)

RECT rectSource2;
rectSource2.left = 0;
rectSource2.top = 0;
rectSource2.bottom = 480;
rectSource2.right = 640;

rectDest.CopyRect(&rectSource2);

// works against RECT structures, too!
// rectDest is now set to (0, 0, 640, 480)
```

##  <a name="crect"></a>CRect:: CRect

`CRect` オブジェクトを構築します。

```
CRect() throw();
CRect(int l, int t, int r, int b) throw();
CRect(const RECT& srcRect) throw();
CRect(LPCRECT lpSrcRect) throw();
CRect(POINT point, SIZE size) throw();
CRect(POINT topLeft, POINT bottomRight) throw();
```

### <a name="parameters"></a>パラメーター

*l*<br/>
`CRect`の左の位置を指定します。

*t*<br/>
`CRect`の先頭を指定します。

*r*<br/>
`CRect`の適切な位置を指定します。

*b*<br/>
`CRect`の下部を指定します。

*srcRect*<br/>
`CRect`の座標を使用して、 [RECT](/windows/win32/api/windef/ns-windef-rect)構造体を参照します。

*lpSrcRect*<br/>
`CRect`の座標を使用して `RECT` 構造体をポイントします。

*視点*<br/>
構築する四角形の始点を指定します。 左上隅に相当します。

*size*<br/>
構築する四角形の左上隅から右下隅までの移動を指定します。

*topLeft*<br/>
`CRect`の左上の位置を指定します。

*右下*<br/>
`CRect`の右下の位置を指定します。

### <a name="remarks"></a>解説

引数が指定されていない場合、`left`、`top`、`right`、および `bottom` のメンバーは初期化されません。

`CRect`(`const RECT&`) コンストラクターと `CRect`(`LPCRECT`) コンストラクターは、 [Copyrect](#copyrect)を実行します。 その他のコンストラクターは、オブジェクトのメンバー変数を直接初期化します。

### <a name="example"></a>例

```cpp
// default constructor doesn't initialize!
CRect rectUnknown;

// four-integers are left, top, right, and bottom
CRect rect(0, 0, 100, 50);
ASSERT(rect.Width() == 100);
ASSERT(rect.Height() == 50);

// Initialize from RECT structure
RECT sdkRect;
sdkRect.left = 0;
sdkRect.top = 0;
sdkRect.right = 100;
sdkRect.bottom = 50;

CRect rect2(sdkRect);
// by reference
CRect rect3(&sdkRect);

// by address
ASSERT(rect2 == rect);
ASSERT(rect3 == rect);

// from a point and a size
CPoint pt(0, 0);
CSize sz(100, 50);
CRect rect4(pt, sz);
ASSERT(rect4 == rect2);

// from two points
CPoint ptBottomRight(100, 50);
CRect rect5(pt, ptBottomRight);
ASSERT(rect5 == rect4);
```

##  <a name="deflaterect"></a>CRect::D eflateRect

縮小 `CRect` を `DeflateRect` するには、中心に向かって移動します。

```
void DeflateRect(int x, int y) throw();
void DeflateRect(SIZE size) throw();
void DeflateRect(LPCRECT lpRect) throw();
void DeflateRect(int l, int t, int r, int b) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
`CRect`の左右の辺を収縮する単位数を指定します。

*y*<br/>
`CRect`の上下を収縮する単位数を指定します。

*size*<br/>
`CRect`deflate する単位の数を指定する[サイズ](/windows/win32/api/windef/ns-windef-size)または[CSize](csize-class.md) 。 `cx` の値は、左右の単位を縮小する単位の数を指定し、`cy` の値は、上と下を収縮する単位の数を指定します。

*lpRect*<br/>
各辺を収縮する単位の数を指定する[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` を指します。

*l*<br/>
`CRect`の左側を収縮する単位数を指定します。

*t*<br/>
`CRect`の上部を deflate する単位数を指定します。

*r*<br/>
`CRect`の右側を縮小する単位数を指定します。

*b*<br/>
`CRect`の下部を deflate する単位数を指定します。

### <a name="remarks"></a>解説

これを行うには、`DeflateRect`、左右に単位を追加し、右と下から単位を減算します。 `DeflateRect` のパラメーターは符号付きの値です。正の値は `CRect` を deflate し、負の値はそれを拡大します。

最初の2つのオーバーロードは、`CRect` の反対側の両方のペアを縮小して、合計幅が*x* (または `cx`) の2倍に減少し、合計の高さが*y* (または `cy`) の2倍に減少するようにします。 他の2つのオーバーロードは、`CRect` の両側を他のオーバーロードとは別に deflate します。

### <a name="example"></a>例

```cpp
CRect rect(10, 10, 50, 50);
rect.DeflateRect(1, 2);
ASSERT(rect.left == 11 && rect.right == 49);
ASSERT(rect.top == 12 && rect.bottom == 48);

CRect rect2(10, 10, 50, 50);
CRect rectDeflate(1, 2, 3, 4);
rect2.DeflateRect(&rectDeflate);
ASSERT(rect2.left == 11 && rect2.right == 47);
ASSERT(rect2.top == 12 && rect2.bottom == 46);
```

##  <a name="equalrect"></a>CRect:: EqualRect

`CRect` が、指定された四角形と等しいかどうかを判断します。

```
BOOL EqualRect(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
四角形の左上隅と右下隅の座標を格納している[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトをポイントします。

### <a name="return-value"></a>戻り値

2つの四角形の上、左、下、および右の値が同じ場合は0以外の値。それ以外の場合は0です。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1.EqualRect(rect2));
ASSERT(!rect1.EqualRect(rect3));
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1.EqualRect(&test));
```

##  <a name="height"></a>CRect:: Height

下の値から上位の値を減算することによって、`CRect` の高さを計算します。

```
int Height() const throw();
```

### <a name="return-value"></a>戻り値

`CRect`の高さ。

### <a name="remarks"></a>解説

結果の値には負の値を指定できます。

> [!NOTE]
>  四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rect(20, 30, 80, 70);
int nHt = rect.Height();

// nHt is now 40
ASSERT(nHt == 40);
```

##  <a name="inflaterect"></a>CRect:: InflateRect

`InflateRect` の側を中央から移動して `CRect` をします。

```
void InflateRect(int x, int y) throw();
void InflateRect(SIZE size) throw();
void InflateRect(LPCRECT lpRect) throw();
void InflateRect(int l, int t, int r,  int b) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
`CRect`の左右の辺を拡大する単位の数を指定します。

*y*<br/>
`CRect`の上と下を拡大する単位数を指定します。

*size*<br/>
`CRect`を展開する単位の数を指定する[サイズ](/windows/win32/api/windef/ns-windef-size)または[CSize](csize-class.md) 。 `cx` 値には、左右に拡大する単位の数を指定し、`cy` の値では、上と下に膨張する単位の数を指定します。

*lpRect*<br/>
各辺を膨張させる単位数を指定する[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` を指します。

*l*<br/>
`CRect`の左側を拡大する単位数を指定します。

*t*<br/>
`CRect`の先頭を拡大する単位数を指定します。

*r*<br/>
`CRect`の右側に膨張する単位数を指定します。

*b*<br/>
`CRect`の下部を拡大する単位数を指定します。

### <a name="remarks"></a>解説

これを行うには、`InflateRect` 左および上から単位を減算し、単位を右と下に追加します。 `InflateRect` のパラメーターは符号付きの値です。正の値は `CRect` を膨張させ、負の値を収縮します。

最初の2つのオーバーロードは、`CRect` の反対側の両方のペアを膨張させて、合計幅が*x* (または `cx`) の2倍に増加し、合計の高さが*y* (または `cy`) の2倍増加するようにします。 他の2つのオーバーロードは、`CRect` の各側を他のオーバーロードとは別に膨張させます。

### <a name="example"></a>例

```cpp
CRect rect(0, 0, 300, 300);
rect.InflateRect(50, 200);

// rect is now (-50, -200, 350, 500)
ASSERT(rect == CRect(-50, -200, 350, 500));
```

##  <a name="intersectrect"></a>CRect:: IntersectRect

2つの既存の四角形の積集合と等しい `CRect` を作成します。

```
BOOL IntersectRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>パラメーター

*lpRect1*<br/>
ソース四角形を含む[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトを指します。

*lpRect2*<br/>
ソース四角形を含む `RECT` 構造体または `CRect` オブジェクトを指します。

### <a name="return-value"></a>戻り値

積集合が空でない場合は0以外の。積集合が空の場合は0。

### <a name="remarks"></a>解説

共通部分は、両方の既存の四角形に含まれる最大の四角形です。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rectOne(125,  0, 150, 200);
CRect rectTwo(0, 75, 350, 95);
CRect rectInter;

rectInter.IntersectRect(rectOne, rectTwo);
ASSERT(rectInter == CRect(125, 75, 150, 95));
// operator &= can do the same task:

CRect rectInter2 = rectOne;
rectInter2 &= rectTwo;
ASSERT(rectInter2 == CRect(125, 75, 150, 95));
```

##  <a name="isrectempty"></a>CRect:: IsRectEmpty

`CRect` が空かどうかを判断します。

```
BOOL IsRectEmpty() const throw();
```

### <a name="return-value"></a>戻り値

`CRect` が空の場合は0以外の。`CRect` が空でない場合は0。

### <a name="remarks"></a>解説

幅と高さのどちらかまたは両方が0または負の場合、四角形は空になります。 `IsRectNull`とは異なり、四角形のすべての座標がゼロであるかどうかを判断します。

> [!NOTE]
>  四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectEmpty());
ASSERT(!rectSome.IsRectEmpty());
CRect rectEmpty(35, 35, 35, 35);
ASSERT(rectEmpty.IsRectEmpty());
```

##  <a name="isrectnull"></a>CRect:: IsRectNull

`CRect` の上、左、下、右側の値がすべて0に等しいかどうかを判断します。

```
BOOL IsRectNull() const throw();
```

### <a name="return-value"></a>戻り値

`CRect`の top、left、bottom、および right の各値がすべて0に等しい場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>解説

`IsRectEmpty`とは異なり、四角形が空かどうかを判断します。

### <a name="example"></a>例

```cpp
CRect rectNone(0, 0, 0, 0);
CRect rectSome(35, 50, 135, 150);
ASSERT(rectNone.IsRectNull());
ASSERT(!rectSome.IsRectNull());
// note that null means _all_ zeros

CRect rectNotNull(0, 0, 35, 50);
ASSERT(!rectNotNull.IsRectNull());
```

##  <a name="movetox"></a>CRect:: MoveToX

四角形を*x*で指定された絶対 x 座標に移動します。

```
void MoveToX(int x) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
四角形の左上隅の絶対値の x 座標。

### <a name="example"></a>例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToX(10);

// rect is now (10, 0, 110, 100);
ASSERT(rect == CRect(10, 0, 110, 100));
```

##  <a name="movetoxy"></a>CRect:: MoveToXY

この関数を呼び出して、指定した絶対値の x 座標と y 座標に四角形を移動します。

```
void MoveToXY(int x, int y) throw();
void MoveToXY(POINT point) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
四角形の左上隅の絶対値の x 座標。

*y*<br/>
四角形の左上隅の絶対値の y 座標。

*視点*<br/>
四角形の左上隅を指定する `POINT` 構造体。

### <a name="example"></a>例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToXY(10, 10);
// rect is now (10, 10, 110, 110);
ASSERT(rect == CRect(10, 10, 110, 110));
```

##  <a name="movetoy"></a>CRect:: MoveToY

四角形を*y*によって指定された絶対 y 座標に移動するには、この関数を呼び出します。

```
void MoveToY(int y) throw();
```

### <a name="parameters"></a>パラメーター

*y*<br/>
四角形の左上隅の絶対値の y 座標。

### <a name="example"></a>例

```cpp
CRect rect(0, 0, 100, 100);
rect.MoveToY(10);
// rect is now (0, 10, 100, 110);
ASSERT(rect == CRect(0, 10, 100, 110));
```

##  <a name="normalizerect"></a>CRect:: NormalizeRect

高さと幅の両方が正であるように、`CRect` を正規化します。

```
void NormalizeRect() throw();
```

### <a name="remarks"></a>解説

四角形は、Windows が座標に通常使用する4番目のクアドラントの配置に対して正規化されます。 `NormalizeRect` では、上と下の値が比較され、上の方が下部より大きい場合はそれらを交換します。 同様に、左側の値が右側よりも大きい場合は、左辺と右辺の値が入れ替えられます。 この関数は、さまざまなマッピングモードおよび反転された四角形を処理する場合に便利です。

> [!NOTE]
> 次の `CRect` メンバー関数は、適切に機能するために正規化された四角形が必要です。 [Height](#height)、 [Width](#width)、 [Size](#size)、 [isrectempty](#isrectempty)、 [ptinrect](#ptinrect)、 [EqualRect](#equalrect)、 [UnionRect](#unionrect)、 [IntersectRect](#intersectrect)、 [SubtractRect](#subtractrect)、 [operator = =](#operator_eq_eq)、 [operator! =](#operator_neq)、 [operator &#124; ](#operator_or)、 [operator &#124;=](#operator_or_eq)、operator [&](#operator_amp)、 [operator & =](#operator_amp_eq)。

### <a name="example"></a>例

```cpp
CRect rect1(110, 100, 250, 310);
CRect rect2(250, 310, 110, 100);
rect1.NormalizeRect();
rect2.NormalizeRect();
ASSERT(rect1 == rect2);
```

##  <a name="offsetrect"></a>CRect:: OffsetRect

指定したオフセットだけ `CRect` を移動します。

```
void OffsetRect(int x, int y) throw();
void OffsetRect(POINT point) throw();
void OffsetRect(SIZE size) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
左または右に移動する量を指定します。 左に移動するには、負の値にする必要があります。

*y*<br/>
上または下に移動する量を指定します。 上に移動するには、負の値である必要があります。

*視点*<br/>
移動する次元の両方を指定する[POINT](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](cpoint-class.md)オブジェクトを格納します。

*size*<br/>
移動する次元の両方を指定する[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](csize-class.md)オブジェクトを格納します。

### <a name="remarks"></a>解説

X 軸と*y*単位の `CRect`*x*単位を y 軸に沿って移動します。 *X*および*y*パラメーターは符号付きの値であるため、`CRect` を左または右に移動できます。

### <a name="example"></a>例

```cpp
CRect rect(0, 0, 35, 35);
rect.OffsetRect(230, 230);

// rect is now (230, 230, 265, 265)
ASSERT(rect == CRect(230, 230, 265, 265));
```

##  <a name="operator_lpcrect"></a>CRect:: operator LPCRECT `CRect` を[lpcrect](../../mfc/reference/data-types-mfc.md)に変換します。

```
operator LPCRECT() const throw();
```

### <a name="remarks"></a>解説

この関数を使用する場合、アドレスの ( **&** ) 演算子は必要ありません。 この演算子は、`LPCRECT`を予期している関数に `CRect` オブジェクトを渡すときに自動的に使用されます。

##  <a name="operator_lprect"></a>CRect:: operator LPRECT

`CRect` を[LPRECT](../../mfc/reference/data-types-mfc.md)に変換します。

```
operator LPRECT() throw();
```

### <a name="remarks"></a>解説

この関数を使用する場合、アドレスの ( **&** ) 演算子は必要ありません。 この演算子は、`LPRECT`を予期している関数に `CRect` オブジェクトを渡すときに自動的に使用されます。

### <a name="example"></a>例

「 [CRect:: operator LPCRECT](#operator_lpcrect)」の例を参照してください。

##  <a name="operator_eq"></a>CRect:: operator =

*Srcrect*を `CRect`に割り当てます。

```
void operator=(const RECT& srcRect) throw();
```

### <a name="parameters"></a>パラメーター

*srcRect*<br/>
ソースの四角形を参照します。 には、 [RECT](/windows/win32/api/windef/ns-windef-rect)または `CRect`を指定できます。

### <a name="example"></a>例

```cpp
CRect rect(0, 0, 127, 168);
CRect rect2;

rect2 = rect;
ASSERT(rect2 == CRect(0, 0, 127, 168));
```

##  <a name="operator_eq_eq"></a>CRect:: operator = =

左上隅と右下隅の座標を比較することによって、`rect` が `CRect` と等しいかどうかを判断します。

```
BOOL operator==(const RECT& rect) const throw();
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
ソースの四角形を参照します。 には、 [RECT](/windows/win32/api/windef/ns-windef-rect)または `CRect`を指定できます。

### <a name="return-value"></a>戻り値

等しい場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>解説

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999, 6, 3);
ASSERT(rect1 == rect2);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect1 == test);
```

##  <a name="operator_neq"></a>CRect:: operator! =

左上隅と右下隅の座標を比較することによって、 *rect*が `CRect` と等しくないかどうかを判断します。

```
BOOL operator!=(const RECT& rect) const throw();
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
ソースの四角形を参照します。 には、 [RECT](/windows/win32/api/windef/ns-windef-rect)または `CRect`を指定できます。

### <a name="return-value"></a>戻り値

等しくない場合は0以外の値。それ以外の場合は0です。

### <a name="remarks"></a>解説

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rect1(35, 150, 10, 25);
CRect rect2(35, 150, 10, 25);
CRect rect3(98, 999,  6,  3);
ASSERT(rect1 != rect3);
// works just fine against RECTs, as well

RECT test;
test.left = 35;
test.top = 150;
test.right = 10;
test.bottom = 25;

ASSERT(rect3 != test);
```

##  <a name="operator_add_eq"></a>CRect:: operator + =

最初の2つのオーバーロードは、指定されたオフセットによって `CRect` を移動します。

```
void operator+=(POINT point) throw();
void operator+=(SIZE size) throw();
void operator+=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
四角形を移動する単位の数を指定する[ポイント](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](cpoint-class.md)オブジェクト。

*size*<br/>
四角形を移動する単位の数を指定する[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](csize-class.md)オブジェクト。

*lpRect*<br/>
`CRect`の各辺を拡大する単位数を格納している[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトを指します。

### <a name="remarks"></a>解説

パラメーターの*x*と*y* (または `cx` と `cy`) の値が `CRect`に追加されます。

3番目のオーバーロード増えは、パラメーターの各メンバーで指定された単位数によって `CRect` ます。

### <a name="example"></a>例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint  pt(35, 65);
CRect   rect2(135, 300, 235, 400);

rect1 += pt;
ASSERT(rect1 == rect2);
```

##  <a name="operator_-_eq"></a>CRect:: operator-=

最初の2つのオーバーロードは、指定されたオフセットによって `CRect` を移動します。

```
void operator-=(POINT point) throw();
void operator-=(SIZE size) throw();
void operator-=(LPCRECT lpRect) throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
四角形を移動する単位の数を指定する[ポイント](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](cpoint-class.md)オブジェクト。

*size*<br/>
四角形を移動する単位の数を指定する[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](csize-class.md)オブジェクト。

*lpRect*<br/>
`CRect`の各辺を縮小する単位数を格納している[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトを指します。

### <a name="remarks"></a>解説

パラメーターの*x*と*y* (または `cx` と `cy`) の値は `CRect`から減算されます。

3番目のオーバーロード縮小は、パラメーターの各メンバーで指定された単位数によって `CRect` ます。 このオーバーロードは[DeflateRect](#deflaterect)のように機能することに注意してください。

### <a name="example"></a>例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);

rect1 -= pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect1 == rectResult);
```

##  <a name="operator_amp_eq"></a>CRect:: operator &amp;=

`CRect` と `rect`の交差部分に等しい `CRect` を設定します。

```
void operator&=(const RECT& rect) throw();
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
に[RECT](/windows/win32/api/windef/ns-windef-rect)または `CRect`が含まれています。

### <a name="remarks"></a>解説

交差部分は、両方の四角形に含まれる最大の四角形です。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

「 [CRect:: IntersectRect](#intersectrect)」の例を参照してください。

##  <a name="operator_or_eq"></a>CRect:: operator &#124;=

`CRect` と `rect`の和集合に等しい `CRect` を設定します。

```
void operator|=(const RECT& rect) throw();
```

### <a name="parameters"></a>パラメーター

*rect*<br/>
`CRect` または[四角形](/windows/win32/api/windef/ns-windef-rect)が含まれています。

### <a name="remarks"></a>解説

共用体は、両方のソース四角形を含む最小の四角形です。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);

rect1 |= rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect1);
```

##  <a name="operator_add"></a>CRect:: operator +

最初の2つのオーバーロードは、指定されたオフセットによって置き換えら `CRect` と等しい `CRect` オブジェクトを返します。

```
CRect operator+(POINT point) const throw();
CRect operator+(LPCRECT lpRect) const throw();
CRect operator+(SIZE size) const throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
戻り値を移動する単位の数を指定する[ポイント](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](cpoint-class.md)オブジェクト。

*size*<br/>
戻り値を移動する単位の数を指定する[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](csize-class.md)オブジェクト。

*lpRect*<br/>
戻り値の各辺を拡大する単位数を格納する[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトをポイントします。

### <a name="return-value"></a>戻り値

`CRect` を移動または拡大した結果の `CRect`、パラメーターで指定された単位数だけです。

### <a name="remarks"></a>解説

パラメーターの*x*と*y* (または `cx` と `cy`) のパラメーターが `CRect`の位置に追加されます。

3番目のオーバーロードは、パラメーターの各メンバーで指定された単位数によって大きく `CRect` に等しい新しい `CRect` を返します。

### <a name="example"></a>例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 + pt;
CRect   rectResult(135, 300, 235, 400);
ASSERT(rectResult == rect2);
```

##  <a name="operator_-"></a>CRect:: operator-

最初の2つのオーバーロードは、指定されたオフセットによって置き換えら `CRect` と等しい `CRect` オブジェクトを返します。

```
CRect operator-(POINT point) const throw();
CRect operator-(SIZE size) const throw();
CRect operator-(LPCRECT lpRect) const throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
戻り値を移動する単位の数を指定する[ポイント](/windows/win32/api/windef/ns-windef-point)構造または `CPoint` オブジェクト。

*size*<br/>
戻り値を移動する単位の数を指定する[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または `CSize` オブジェクト。

*lpRect*<br/>
戻り値の各辺を収縮する単位数を格納する[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトをポイントします。

### <a name="return-value"></a>戻り値

`CRect` を移動または deflating した結果の `CRect`、パラメーターで指定された単位数だけです。

### <a name="remarks"></a>解説

パラメーターの*x*および*y* (または `cx` および `cy`) パラメーターは `CRect`の位置から減算されます。

3番目のオーバーロードは、パラメーターの各メンバーで指定された単位数で `CRect` deflated に等しい新しい `CRect` を返します。 このオーバーロードは、 [SubtractRect](#subtractrect)ではなく[DeflateRect](#deflaterect)のように機能することに注意してください。

### <a name="example"></a>例

```cpp
CRect   rect1(100, 235, 200, 335);
CPoint pt(35, 65);
CRect   rect2;

rect2 = rect1 - pt;
CRect   rectResult(65, 170, 165, 270);
ASSERT(rect2 == rectResult);
```

##  <a name="operator_amp"></a>CRect:: operator &amp;

`CRect` と*rect2*の積集合である `CRect` を返します。

```
CRect operator&(const RECT& rect2) const throw();
```

### <a name="parameters"></a>パラメーター

*rect2*<br/>
に[RECT](/windows/win32/api/windef/ns-windef-rect)または `CRect`が含まれています。

### <a name="return-value"></a>戻り値

`CRect` と*rect2*の積集合である `CRect`。

### <a name="remarks"></a>解説

交差部分は、両方の四角形に含まれる最大の四角形です。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 & rect2;
CRect   rectResult(100, 100, 200, 200);
ASSERT(rectResult == rect3);
```

##  <a name="operator_or"></a>CRect:: operator&#124;

`CRect` と*rect2*の和集合である `CRect` を返します。

```
CRect operator|(const RECT&
rect2) const throw();
```

### <a name="parameters"></a>パラメーター

*rect2*<br/>
に[RECT](/windows/win32/api/windef/ns-windef-rect)または `CRect`が含まれています。

### <a name="return-value"></a>戻り値

`CRect` と*rect2*の和集合である `CRect`。

### <a name="remarks"></a>解説

共用体は、両方の四角形を含む最小の四角形です。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3 = rect1 | rect2;
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="ptinrect"></a>CRect::P の実行

指定したポイントが `CRect`内にあるかどうかを判断します。

```
BOOL PtInRect(POINT point) const throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](cpoint-class.md)オブジェクトが含まれています。

### <a name="return-value"></a>戻り値

ポイントが `CRect`内にある場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>解説

点は、左側または上側にある場合、または4辺のいずれかにある場合、`CRect` 内にあります。 右または下の点が `CRect`の外側にあります。

> [!NOTE]
>  四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rect(5, 5, 100, 100);
CPoint pt1(35, 50);
CPoint pt2(125, 298);

// this is true, because pt1 is inside the rectangle
ASSERT(rect.PtInRect(pt1));

// this is NOT true, because pt2 is outside the rectangle
ASSERT(!rect.PtInRect(pt2));

// note that the right and the bottom aren't inside
ASSERT(!rect.PtInRect(CPoint(35, 100)));
ASSERT(!rect.PtInRect(CPoint(100, 98)));

// but the top and the left are inside
ASSERT(rect.PtInRect(CPoint(5, 65)));
ASSERT(rect.PtInRect(CPoint(88, 5)));

// and that PtInRect() works against a POINT, too
POINT pt;
pt.x = 35;
pt.y = 50;
ASSERT(rect.PtInRect(pt));
```

##  <a name="setrect"></a>CRect:: SetRect

`CRect` の大きさを指定した座標に設定します。

```
void SetRect(int x1, int y1, int x2, int y2) throw();
```

### <a name="parameters"></a>パラメーター

*x1*<br/>
左上隅の x 座標を指定します。

*y1*<br/>
左上隅の y 座標を指定します。

*×*<br/>
右下隅の x 座標を指定します。

*y2*<br/>
右下隅の y 座標を指定します。

### <a name="example"></a>例

```cpp
CRect rect;
rect.SetRect(256, 256, 512, 512);
ASSERT(rect == CRect(256, 256, 512, 512));
```

##  <a name="setrectempty"></a>CRect:: SetRectEmpty

すべての座標を0に設定することにより、`CRect` を null の四角形にします。

```
void SetRectEmpty() throw();
```

### <a name="example"></a>例

```cpp
CRect rect;
rect.SetRectEmpty();

// rect is now (0, 0, 0, 0)
ASSERT(rect.IsRectEmpty());
```

##  <a name="size"></a>CRect:: SIZE

戻り値の `cx` メンバーと `cy` メンバーには、`CRect`の高さと幅が含まれています。

```
CSize Size() const throw();
```

### <a name="return-value"></a>戻り値

`CRect`のサイズを格納している[CSize](csize-class.md)オブジェクト。

### <a name="remarks"></a>解説

高さまたは幅は負の値にすることができます。

> [!NOTE]
>  四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rect(10, 10, 50, 50);
CSize sz = rect.Size();
ASSERT(sz.cx == 40 && sz.cy == 40);
```

##  <a name="subtractrect"></a>CRect:: SubtractRect

`CRect` の次元を `lpRectSrc1`からの `lpRectSrc2` の減算と同じにします。

```
BOOL SubtractRect(LPCRECT lpRectSrc1, LPCRECT lpRectSrc2) throw();
```

### <a name="parameters"></a>パラメーター

*lpRectSrc1*<br/>
四角形を減算する[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または `CRect` オブジェクトをポイントします。

*lpRectSrc2*<br/>
*LpRectSrc1*パラメーターによって示される四角形から減算される `RECT` 構造体または `CRect` オブジェクトを指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>解説

減算は、 *lpRectScr1*と*lpRectScr2*が交差していない、 *lpRectScr1*内のすべての点を含む最小の四角形です。

*LpRectSrc1*で指定された四角形は、 *lpRectSrc2*によって指定された四角形が、x または y 方向の少なくとも1つの*lpRectSrc1*によって指定された四角形と完全に重ならない場合、変更されません。

たとえば、 *lpRectSrc1*が (10, 10, 100100) で、 *lpRectSrc2*が (50, 50, 150150) であった場合、 *lpRectSrc1*が指す四角形は、関数が返されたときに変更されません。 *LpRectSrc1*が (10, 10, 100100) で、 *lpRectSrc2*が (50, 10, 150150) である場合、 *lpRectSrc1*が指す四角形には、関数が返されたときの座標 (10, 10, 50100) が格納されます。

`SubtractRect` は[演算子](#operator_-)と[演算子-=](#operator_-_eq)と同じではありません。 これらの演算子はいずれも `SubtractRect`を呼び出しません。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
RECT   rectOne;
RECT   rectTwo;

rectOne.left = 10;
rectOne.top = 10;
rectOne.bottom = 100;
rectOne.right = 100;

rectTwo.left = 50;
rectTwo.top = 10;
rectTwo.bottom = 150;
rectTwo.right = 150;

CRect   rectDiff;

rectDiff.SubtractRect(&rectOne, &rectTwo);
CRect   rectResult(10, 10, 50, 100);

ASSERT(rectDiff == rectResult);

// works for CRect, too, since there is
// implicit CRect -> LPCRECT conversion

CRect rect1(10, 10, 100, 100);
CRect rect2(50, 10, 150, 150);
CRect rectOut;

rectOut.SubtractRect(rect1, rect2);
ASSERT(rectResult == rectOut);
```

##  <a name="topleft"></a>CRect:: TopLeft

座標は、`CRect`に含まれる[CPoint](cpoint-class.md)オブジェクトへの参照として返されます。

```
CPoint& TopLeft() throw();
const CPoint& TopLeft() const throw();
```

### <a name="return-value"></a>戻り値

四角形の左上隅の座標です。

### <a name="remarks"></a>解説

この関数を使用すると、四角形の左上隅を取得または設定できます。 代入演算子の左側にあるこの関数を使用して、コーナーを設定します。

### <a name="example"></a>例

「 [CRect:: 小惑星](#centerpoint)」の例を参照してください。

##  <a name="unionrect"></a>CRect:: UnionRect

`CRect` の大きさを、2つのソース四角形の和集合と等しくなるようにします。

```
BOOL UnionRect(LPCRECT lpRect1, LPCRECT lpRect2) throw();
```

### <a name="parameters"></a>パラメーター

*lpRect1*<br/>
ソース四角形を含む[RECT](/windows/win32/api/windef/ns-windef-rect)または `CRect` を指します。

*lpRect2*<br/>
コピー元の四角形を格納している `RECT` または `CRect` を指します。

### <a name="return-value"></a>戻り値

共用体が空でない場合は0以外の。共用体が空の場合は0。

### <a name="remarks"></a>解説

共用体は、両方のソース四角形を含む最小の四角形です。

空の四角形の大きさは無視されます。つまり、高さのない四角形や幅のない四角形です。

> [!NOTE]
>  両方の四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect   rect1(100,  0, 200, 300);
CRect   rect2(0, 100, 300, 200);
CRect   rect3;

rect3.UnionRect(&rect1, &rect2);
CRect   rectResult(0, 0, 300, 300);
ASSERT(rectResult == rect3);
```

##  <a name="width"></a>CRect:: Width

右側の値から左の値を減算することによって、`CRect` の幅を計算します。

```
int Width() const throw();
```

### <a name="return-value"></a>戻り値

`CRect`の幅。

### <a name="remarks"></a>解説

幅には負の値を指定できます。

> [!NOTE]
>  四角形が正規化されているか、この関数が失敗する可能性があります。 [NormalizeRect](#normalizerect)を呼び出して、この関数を呼び出す前に四角形を正規化することができます。

### <a name="example"></a>例

```cpp
CRect rect(20, 30, 80, 70);
int nWid = rect.Width();
// nWid is now 60
ASSERT(nWid == 60);
```

## <a name="see-also"></a>参照

[CPoint クラス](cpoint-class.md)<br/>
[CSize クラス](csize-class.md)<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect)
