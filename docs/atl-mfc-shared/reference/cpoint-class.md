---
title: CPoint クラス
ms.date: 11/04/2016
f1_keywords:
- CPoint
- ATLTYPES/ATL::CPoint
- ATLTYPES/ATL::CPoint::CPoint
- ATLTYPES/ATL::CPoint::Offset
helpviewer_keywords:
- LPPOINT structure
- POINT structure
- CPoint class
ms.assetid: a6d4db93-35cc-444d-9221-c3e160f6edaa
ms.openlocfilehash: b7c13ef8b9656c5c2fa6a90fefca0d9babbe1c84
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69491223"
---
# <a name="cpoint-class"></a>CPoint クラス

Windows の `POINT` 構造体と同様のものです。

## <a name="syntax"></a>構文

```
class CPoint : public tagPOINT
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CPoint:: CPoint](#cpoint)|`CPoint` を構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CPoint:: Offset](#offset)|の`x` `y`メンバーとメンバーに値を追加します。`CPoint`|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CPoint:: operator-](#operator_-)|`CPoint`とのサイズ、または点の否定、または2つの点のサイズの差、または負のサイズによるオフセットの差を返します。|
|[CPoint:: operator! =](#operator_neq)|2つの点が等しくないかどうかをチェックします。|
|[CPoint:: operator +](#operator_add)|`CPoint`とサイズまたはポイントの合計、 `CRect`またはサイズによるオフセットを返します。|
|[CPoint:: operator + =](#operator_add_eq)|サイズ`CPoint`またはポイントを追加してオフセットします。|
|[CPoint:: operator-=](#operator_-_eq)|サイズ`CPoint`またはポイントを減算してオフセットします。|
|[CPoint:: operator = =](#operator_eq_eq)|2つの点が等しいかどうかをチェックします。|

## <a name="remarks"></a>Remarks

[また、構造体](/windows/win32/api/windef/ns-windef-point)を操作`CPoint`するためのメンバー関数も含まれています。

オブジェクト`CPoint`は、 `POINT`構造体が使用されているすべての場所で使用できます。 "サイズ" と対話するこのクラスの演算子は、2つの型が交換可能であるため、 [CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクトまたは[サイズ](/windows/win32/api/windef/ns-windef-size)構造体のいずれかを受け入れます。

> [!NOTE]
>  このクラスは、 `tagPOINT`構造体から派生します。 (この`tagPOINT`名前は、 `POINT`構造体で使用頻度の低い名前です)。これ`POINT`は、 `x`構造体のデータメンバー、および`y`は、の`CPoint`アクセス可能なデータメンバーであることを意味します。

> [!NOTE]
>  共有ユーティリティクラス (など`CPoint`) の詳細については、「[共有クラス](../../atl-mfc-shared/atl-mfc-shared-classes.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

`tagPOINT`

`CPoint`

## <a name="requirements"></a>必要条件

**ヘッダー:** atltypes. h

##  <a name="cpoint"></a>CPoint:: CPoint

`CPoint` オブジェクトを構築します。

```
CPoint() throw();
CPoint(int initX, int initY) throw();
CPoint(POINT initPt) throw();
CPoint(SIZE initSize) throw();
CPoint(LPARAM dwPoint) throw();
```

### <a name="parameters"></a>パラメーター

*initX*<br/>
`x` の `CPoint` メンバーの値を指定します。

*initY*<br/>
`y` の `CPoint` メンバーの値を指定します。

*initPt*<br/>
初期`CPoint` 化`CPoint`に使用する値を指定する [POINT](/windows/win32/api/windef/ns-windef-point) 構造体または。

*initSize*<br/>
初期化`CPoint`に使用する値を指定する [SIZE](/windows/win32/api/windef/ns-windef-size) 構造体または [CSize](../../atl-mfc-shared/reference/csize-class.md) 。

*dwPoint*<br/>
メンバーを*dwpoint*の下位ワードに設定し、メンバーをdwpointの上位ワードに設定し`y`ます。 `x`

### <a name="remarks"></a>Remarks

引数を指定しない場合、`x` メンバーおよび `y` メンバーは 0 に設定されます。

### <a name="example"></a>例

```cpp
CPoint   ptTopLeft(0, 0);
// works from a POINT, too

POINT   ptHere;
ptHere.x = 35;
ptHere.y = 95;

CPoint   ptMFCHere(ptHere);

// works from a SIZE
SIZE   sHowBig;
sHowBig.cx = 300;
sHowBig.cy = 10;

CPoint ptMFCBig(sHowBig);
// or from a DWORD

DWORD   dwSize;
dwSize = MAKELONG(35, 95);

CPoint ptFromDouble(dwSize);
ASSERT(ptFromDouble == ptMFCHere);
```

##  <a name="offset"></a>CPoint:: Offset

の`x` `y`メンバーとメンバーに値を追加します。`CPoint`

```
void Offset(int xOffset, int yOffset) throw();
void Offset(POINT point) throw();
void Offset(SIZE size) throw();
```

### <a name="parameters"></a>パラメーター

*xOffset*<br/>
のメンバー`x`をオフセットする量を指定します。`CPoint`

*yOffset*<br/>
のメンバー`y`をオフセットする量を指定します。`CPoint`

*視点*<br/>
をオフセットする量 ([POINT](/windows/win32/api/windef/ns-windef-point) `CPoint`または`CPoint`) を指定します。

*size*<br/>
をオフセット`CPoint`する量 ([SIZE](/windows/win32/api/windef/ns-windef-size) または [CSize](../../atl-mfc-shared/reference/csize-class.md)) を指定します。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#28](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_1.cpp)]

##  <a name="operator_eq_eq"></a>CPoint:: operator = =

2つの点が等しいかどうかをチェックします。

```
BOOL operator==(POINT point) const throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)構造体または`CPoint`オブジェクトが含まれています。

### <a name="return-value"></a>戻り値

点が等しい場合は0以外の値。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#29](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_2.cpp)]

##  <a name="operator_neq"></a>CPoint:: operator! =

2つの点が等しくないかどうかをチェックします。

```
BOOL operator!=(POINT point) const throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)構造体または`CPoint`オブジェクトが含まれています。

### <a name="return-value"></a>戻り値

点が等しくない場合は0以外の値。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#30](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_3.cpp)]

##  <a name="operator_add_eq"></a>CPoint:: operator + =

最初のオーバーロードは、 `CPoint`にサイズを追加します。

```
void operator+=(SIZE size) throw();
void operator+=(POINT point) throw();
```

### <a name="parameters"></a>パラメーター

*size*<br/>
[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクトを格納します。

*視点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)オブジェクトが含まれています。

### <a name="remarks"></a>Remarks

2番目のオーバーロードは、 `CPoint`に点を追加します。

どちらの場合も、右側のオペランドの`x` (または`cx`) メンバー `CPoint`をの`x`メンバーに追加し、右側のオペランドの`y` (または`cy`) メンバーをに追加することで、加算が行われます。`y` の`CPoint`メンバー。

たとえば、を含む`CPoint(5, -7)`変数にを追加する`CPoint(30, 40)`と、変数が`CPoint(35, 33)`に変更されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#31](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_4.cpp)]

##  <a name="operator_-_eq"></a>CPoint:: operator-=

最初のオーバーロードは、 `CPoint`からサイズを減算します。

```
void operator-=(SIZE size) throw();
void operator-=(POINT point) throw();
```

### <a name="parameters"></a>パラメーター

*size*<br/>
[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクトを格納します。

*視点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)オブジェクトが含まれています。

### <a name="remarks"></a>Remarks

2番目のオーバーロードは、 `CPoint`から点を減算します。

どちらの場合も、減算`x`は、 `x` `CPoint`のメンバーから右側`cx`のオペランドの (または) メンバーを減算し、右側の`y` (または`cy`) メンバーを減算することによって行われます。のメンバー`y`からのオペランド。 `CPoint`

たとえば、を含む`CPoint(5, -7)`変数からを減算する`CPoint(30, 40)`と、変数が`CPoint(25, 47)`に変更されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#32](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_5.cpp)]

##  <a name="operator_add"></a>CPoint:: operator +

この演算子は、 `CPoint` `CSize` `CPoint` オブジェクトまた`CRect`はオブジェクトによるオフセット、またはによるのオフセットに使用します。`CPoint`

```
CPoint operator+(SIZE size) const throw();
CPoint operator+(POINT point) const throw();
CRect operator+(const RECT* lpRect) const throw();
```

### <a name="parameters"></a>パラメーター

*size*<br/>
[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクトを格納します。

*視点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)オブジェクトが含まれています。

*lpRect*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトへのポインターを格納します。

### <a name="return-value"></a>戻り値

サイズでオフセットされる、ポイントでオフセットさ`CRect` `CPoint` れる、または点による`CPoint`オフセットを表す。

### <a name="remarks"></a>Remarks

たとえば、最初の2つのオーバーロードのいずれかを使用し`CPoint(25, -19)`てポイントを`CPoint(15, 5)`ポイントまた`CSize(15, 5)`はサイズで`CPoint(40, -14)`オフセットすると、値が返されます。

点に四角形を追加すると、ポイントに指定された`x`および`y`の値によってオフセットされた後、四角形が返されます。 たとえば、最後のオーバーロードを使用して、ある`CRect(125, 219, 325, 419)`点`CPoint(25, -19)`によって`CRect(150, 200, 350, 400)`四角形をオフセットすると、が返されます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#33](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_6.cpp)]

##  <a name="operator_-"></a>CPoint:: operator-

最初の2つのオーバーロードのいずれかを`CPoint`使用`CSize`して`CPoint`、またはオブジェクトをから減算します。

```
CSize operator-(POINT point) const throw();
CPoint operator-(SIZE size) const throw();
CRect operator-(const RECT* lpRect) const throw();
CPoint operator-() const throw();
```

### <a name="parameters"></a>パラメーター

*視点*<br/>
[POINT](/windows/win32/api/windef/ns-windef-point)構造体または[CPoint](../../atl-mfc-shared/reference/cpoint-class.md)オブジェクト。

*size*<br/>
[サイズ](/windows/win32/api/windef/ns-windef-size)構造体または[CSize](../../atl-mfc-shared/reference/csize-class.md)オブジェクト。

*lpRect*<br/>
[RECT](/windows/win32/api/windef/ns-windef-rect)構造体または[CRect](../../atl-mfc-shared/reference/crect-class.md)オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

2つの点`CPoint`の差である、サイズ`CRect`の否定によってオフセットされる、点の否定によってオフセットされる、また`CPoint`は点の否定である。 `CSize`

### <a name="remarks"></a>Remarks

3番目のオーバーロード`CRect`は、の`CPoint`否定によってをオフセットします。 最後に、単項演算子を使用`CPoint`してを否定します。

たとえば、最初のオーバーロードを使用して2つの点`CPoint(25, -19)` `CPoint(15, 5)`の差を`CSize(10, -24)`検出し、を返します。

から`CSize` `CPoint` `CSize`を減算すると、上記と同じ計算が行われますが、オブジェクトではなくオブジェクトが返されます。 `CPoint` たとえば、2番目のオーバーロードを使用して、ポイント`CPoint(25, -19)`と`CPoint(10, -24)`サイズ`CSize(15, 5)`の差を求めます。

点から四角形を減算する`x`と、ポイントで指定された値と`y`値の否定によって四角形のオフセットが返されます。 たとえば、最後のオーバーロードを使用して、四角形`CRect(125, 200, 325, 400)`をポイント`CPoint(25, -19)`でオフセット`CRect(100, 219, 300, 419)`すると、が返されます。

単項演算子を使用して、点を否定します。 たとえば、単項演算子をポイント`CPoint(25, -19)`と共に使用すると、が返さ`CPoint(-25, 19)`れます。

### <a name="example"></a>例

[!code-cpp[NVC_ATLMFC_Utilities#34](../../atl-mfc-shared/codesnippet/cpp/cpoint-class_7.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル MDI](../../overview/visual-cpp-samples.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[POINT 構造体](/windows/win32/api/windef/ns-windef-point)<br/>
[CRect クラス](../../atl-mfc-shared/reference/crect-class.md)<br/>
[CSize クラス](../../atl-mfc-shared/reference/csize-class.md)
