---
title: CRgn クラス
ms.date: 11/04/2016
f1_keywords:
- CRgn
- AFXWIN/CRgn
- AFXWIN/CRgn::CRgn
- AFXWIN/CRgn::CombineRgn
- AFXWIN/CRgn::CopyRgn
- AFXWIN/CRgn::CreateEllipticRgn
- AFXWIN/CRgn::CreateEllipticRgnIndirect
- AFXWIN/CRgn::CreateFromData
- AFXWIN/CRgn::CreateFromPath
- AFXWIN/CRgn::CreatePolygonRgn
- AFXWIN/CRgn::CreatePolyPolygonRgn
- AFXWIN/CRgn::CreateRectRgn
- AFXWIN/CRgn::CreateRectRgnIndirect
- AFXWIN/CRgn::CreateRoundRectRgn
- AFXWIN/CRgn::EqualRgn
- AFXWIN/CRgn::FromHandle
- AFXWIN/CRgn::GetRegionData
- AFXWIN/CRgn::GetRgnBox
- AFXWIN/CRgn::OffsetRgn
- AFXWIN/CRgn::PtInRegion
- AFXWIN/CRgn::RectInRegion
- AFXWIN/CRgn::SetRectRgn
helpviewer_keywords:
- CRgn [MFC], CRgn
- CRgn [MFC], CombineRgn
- CRgn [MFC], CopyRgn
- CRgn [MFC], CreateEllipticRgn
- CRgn [MFC], CreateEllipticRgnIndirect
- CRgn [MFC], CreateFromData
- CRgn [MFC], CreateFromPath
- CRgn [MFC], CreatePolygonRgn
- CRgn [MFC], CreatePolyPolygonRgn
- CRgn [MFC], CreateRectRgn
- CRgn [MFC], CreateRectRgnIndirect
- CRgn [MFC], CreateRoundRectRgn
- CRgn [MFC], EqualRgn
- CRgn [MFC], FromHandle
- CRgn [MFC], GetRegionData
- CRgn [MFC], GetRgnBox
- CRgn [MFC], OffsetRgn
- CRgn [MFC], PtInRegion
- CRgn [MFC], RectInRegion
- CRgn [MFC], SetRectRgn
ms.assetid: d904da84-76aa-481e-8780-b09485f49e64
ms.openlocfilehash: 97266ac9e4f1885149ce521f554ad2f22daee6e0
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741501"
---
# <a name="crgn-class"></a>CRgn クラス

Windows のグラフィック デバイス インターフェイス (GDI) の領域をカプセル化したものです。

## <a name="syntax"></a>構文

```
class CRgn : public CGdiObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CRgn::CRgn](#crgn)|`CRgn` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CRgn::CombineRgn](#combinergn)|指定し`CRgn`た`CRgn` 2 つのオブジェクトの和集合と等価になるようにオブジェクトを設定します。|
|[CRgn::CopyRgn](#copyrgn)|オブジェクトを`CRgn` 、指定した`CRgn`オブジェクトのコピーであるように設定します。|
|[CRgn::CreateEllipticRgn](#createellipticrgn)|楕円領域`CRgn`を使用してオブジェクトを初期化します。|
|[CRgn::CreateEllipticRgnIndirect](#createellipticrgnindirect)|[RECT](/windows/win32/api/windef/ns-windef-rect) 構造体で定義された楕円領域を使用して `CRgn` オブジェクトを初期化します。|
|[CRgn::CreateFromData](#createfromdata)|指定された領域と変換データから領域を作成します。|
|[CRgn::CreateFromPath](#createfrompath)|指定されたデバイスコンテキストに選択されているパスから領域を作成します。|
|[CRgn::CreatePolygonRgn](#createpolygonrgn)|多角形領域`CRgn`を使用してオブジェクトを初期化します。 必要に応じて、最後の頂点から最初の頂点までの線を描画することによって、多角形が自動的に閉じられます。|
|[CRgn::CreatePolyPolygonRgn](#createpolypolygonrgn)|一連の`CRgn`閉じた多角形で構成される領域を使用してオブジェクトを初期化します。 ポリゴンは、結合されていない場合もあれば、重なっている場合もあります。|
|[CRgn::CreateRectRgn](#createrectrgn)|四角形の`CRgn`領域を使用してオブジェクトを初期化します。|
|[CRgn::CreateRectRgnIndirect](#createrectrgnindirect)|[RECT](/windows/win32/api/windef/ns-windef-rect) structure `CRgn`によって定義される四角形領域を使用してオブジェクトを初期化します。|
|[CRgn::CreateRoundRectRgn](#createroundrectrgn)|角が`CRgn`丸い四角形の領域を使用してオブジェクトを初期化します。|
|[CRgn::EqualRgn](#equalrgn)|2つ`CRgn`のオブジェクトが等しいかどうかを確認します。|
|[CRgn:: FromHandle](#fromhandle)|Windows 領域へのハンドル`CRgn`が指定された場合に、オブジェクトへのポインターを返します。|
|[CRgn::GetRegionData](#getregiondata)|指定されたバッファーに、指定された領域を記述するデータを格納します。|
|[CRgn::GetRgnBox](#getrgnbox)|`CRgn`オブジェクトの外接する四角形の座標を取得します。|
|[CRgn::OffsetRgn](#offsetrgn)|指定し`CRgn`たオフセットだけオブジェクトを移動します。|
|[CRgn::PtInRegion](#ptinregion)|指定した点が領域内にあるかどうかを判断します。|
|[CRgn::RectInRegion](#rectinregion)|指定した四角形のいずれかの部分が領域の境界内にあるかどうかを判断します。|
|[CRgn::SetRectRgn](#setrectrgn)|指定された四角形領域にオブジェクトを設定します。`CRgn`|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CRgn:: operator HRGN](#operator_hrgn)|`CRgn`オブジェクトに格納されている Windows ハンドルを返します。|

## <a name="remarks"></a>Remarks

Region は、ウィンドウ内の楕円または多角形の領域です。 領域を使用するには、クラスのメンバー関数`CRgn`を使用して、クラス`CDC`のメンバーとして定義されているクリッピング関数を使用します。

の`CRgn`メンバー関数は、呼び出される region オブジェクトに関する情報を作成、変更、および取得します。

の使用方法`CRgn`の詳細については、「[グラフィックオブジェクト](../../mfc/graphic-objects.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CRgn`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="combinergn"></a>  CRgn::CombineRgn

2つの既存の領域を組み合わせることによって、新しい GDI 領域を作成します。

```
int CombineRgn(
    CRgn* pRgn1,
    CRgn* pRgn2,
    int nCombineMode);
```

### <a name="parameters"></a>パラメーター

*pRgn1*<br/>
既存の領域を識別します。

*pRgn2*<br/>
既存の領域を識別します。

*nCombineMode*<br/>
2つのソースリージョンを結合するときに実行する操作を指定します。 次のいずれかの値を指定できます。

- RGN_AND では、両方のリージョンの重なり合った領域 (共通部分) を使用します。

- RGN_COPY は、 *pRgn1*によって識別される領域1のコピーを作成します。

- RGN_DIFF は、領域 2 ( *pRgn2*によって識別されます) の一部ではない領域 1 ( *pRgn1*によって識別される) の領域で構成される領域を作成します。

- RGN_OR では、両方のリージョンが全体 (共用体) に結合されます。

- RGN_XOR は、両方のリージョンを結合しますが、重複する領域を削除します。

### <a name="return-value"></a>戻り値

結果として得られる領域の種類を指定します。 次のいずれかの値を指定できます。

- COMPLEXREGION の新しい領域に重複する境界線があります。

- 新しいリージョンが作成されていません。

- NULLREGION の新しい領域が空です。

- SIMPLEREGION の新しい領域には、重複する境界線がありません。

### <a name="remarks"></a>Remarks

これらの領域は、 *nCombineMode*によって指定されたとおりに組み合わされます。

2つの指定された領域が結合され、結果とし`CRgn`て得られる領域ハンドルがオブジェクトに格納されます。 したがって、 `CRgn`オブジェクトに格納されているすべての領域が、結合された領域に置き換えられます。

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

1つのリージョンを別のリージョンにコピーするには、 [Copyrgn](#copyrgn)を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#144](../../mfc/codesnippet/cpp/crgn-class_1.cpp)]

##  <a name="copyrgn"></a>  CRgn::CopyRgn

*Prgnsrc*によって定義された`CRgn`領域をオブジェクトにコピーします。

```
int CopyRgn(CRgn* pRgnSrc);
```

### <a name="parameters"></a>パラメーター

*pRgnSrc*<br/>
既存の領域を識別します。

### <a name="return-value"></a>戻り値

結果として得られる領域の種類を指定します。 次のいずれかの値を指定できます。

- COMPLEXREGION の新しい領域に重複する境界線があります。

- 新しいリージョンが作成されていません。

- NULLREGION の新しい領域が空です。

- SIMPLEREGION の新しい領域には、重複する境界線がありません。

### <a name="remarks"></a>Remarks

以前に`CRgn`オブジェクトに格納されていた領域が新しい領域で置き換えられます。 この関数は、 [CombineRgn](#combinergn)メンバー関数の特殊なケースです。

### <a name="example"></a>例

  「 [CRgn:: CreateEllipticRgn](#createellipticrgn)」の例を参照してください。

##  <a name="createellipticrgn"></a>  CRgn::CreateEllipticRgn

楕円領域を作成します。

```
BOOL CreateEllipticRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>パラメーター

*x1*<br/>
楕円の外接する四角形の左上隅の論理 x 座標を指定します。

*y1*<br/>
楕円の外接する四角形の左上隅の論理 y 座標を指定します。

*×*<br/>
楕円の外接する四角形の右下隅の論理 x 座標を指定します。

*y2*<br/>
楕円の外接する四角形の右下隅の論理 y 座標を指定します。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

領域は、 *x1*、 *y1*、 *x2*、および*y2*によって指定された外接する四角形によって定義されます。 領域は`CRgn`オブジェクトに格納されます。

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

`CreateEllipticRgn`関数で作成された領域の使用が完了したら、アプリケーションはデバイスコンテキストからリージョンを選択し、 `DeleteObject`関数を使用してその領域を削除する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#145](../../mfc/codesnippet/cpp/crgn-class_2.cpp)]

##  <a name="createellipticrgnindirect"></a>  CRgn::CreateEllipticRgnIndirect

楕円領域を作成します。

```
BOOL CreateEllipticRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
楕円の外`RECT`接する四角形の`CRect`左上隅と右下隅の論理座標を格納している構造体またはオブジェクトを指します。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

領域は、 *lpRect*が指す構造体またはオブジェクトによって定義され、 `CRgn`オブジェクトに格納されます。

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

`CreateEllipticRgnIndirect`関数で作成された領域の使用が完了したら、アプリケーションはデバイスコンテキストからリージョンを選択し、 `DeleteObject`関数を使用してその領域を削除する必要があります。

### <a name="example"></a>例

  「 [CRgn:: CreateRectRgnIndirect](#createrectrgnindirect)」の例を参照してください。

##  <a name="createfromdata"></a>  CRgn::CreateFromData

指定された領域と変換データから領域を作成します。

```
BOOL CreateFromData(
    const XFORM* lpXForm,
    int nCount,
    const RGNDATA* pRgnData);
```

### <a name="parameters"></a>パラメーター

*lpXForm*<br/>
領域で実行される変換を定義する、 [XFORM](/windows/win32/api/wingdi/ns-wingdi-xform)ata 構造体を指します。 このポインターが NULL の場合、id 変換が使用されます。

*nCount*<br/>
*Prgndata*が指すバイト数を指定します。

*pRgnData*<br/>
領域データを格納する[Rgndata](/windows/win32/api/wingdi/ns-wingdi-rgndata)構造体を指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

アプリケーションは、 `CRgn::GetRegionData`関数を呼び出すことによって、領域のデータを取得できます。

##  <a name="createfrompath"></a>  CRgn::CreateFromPath

指定されたデバイスコンテキストに選択されているパスから領域を作成します。

```
BOOL CreateFromPath(CDC* pDC);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
閉じたパスを含むデバイスコンテキストを識別します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

*PDC*パラメーターで識別されるデバイスコンテキストには、閉じたパスが含まれている必要があります。 が`CreateFromPath`パスを領域に変換した後、Windows はデバイスコンテキストから閉じたパスを破棄します。

##  <a name="createpolygonrgn"></a>  CRgn::CreatePolygonRgn

多角形領域を作成します。

```
BOOL CreatePolygonRgn(
    LPPOINT lpPoints,
    int nCount,
    int nMode);
```

### <a name="parameters"></a>パラメーター

*lpPoints*<br/>
構造体の`POINT`配列、またはオブジェクトの`CPoint`配列を指します。 各構造体は、多角形の1つの頂点の x 座標と y 座標を指定します。 構造`POINT`体の形式は次のとおりです。

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*nCount*<br/>
LpPoints が指す配列`POINT`内の`CPoint`構造体またはオブジェクトの数を指定します。

*Evaluationmode*<br/>
領域の塗りつぶしモードを指定します。 このパラメーターには、代替またはワインディングを使用できます。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

必要に応じて、最後の頂点から最初の頂点までの線を描画することによって、多角形が自動的に閉じられます。 結果として得られる`CRgn`領域は、オブジェクトに格納されます。

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

多角形の塗りつぶしモードが別の場合、システムは各スキャン行の奇数と偶数の多角形の辺の間に領域を塗りつぶします。 つまり、システムによって、最初と2番目の側、3番目と4番目の側の間の領域が塗りつぶされます。

多角形入力モードがワインディングの場合、システムは、図形が描画された方向を使用して、領域を塗りつぶすかどうかを判断します。 多角形の各線分は、時計回りまたは反時計回りの方向に描画されます。 囲まれた領域から図形の外側に描画された虚数線が時計回りの直線セグメントを通過するたびに、カウントがインクリメントされます。 直線が反時計回りに直線セグメントを通過すると、カウントがデクリメントされます。 線が図形の外側に到達したときに、その数が0以外の場合、領域は塗りつぶされます。

`CreatePolygonRgn`関数で作成された領域を使用してアプリケーションが終了したら、デバイスコンテキストからリージョンを選択し、 `DeleteObject`関数を使用してその領域を削除する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#146](../../mfc/codesnippet/cpp/crgn-class_3.cpp)]

##  <a name="createpolypolygonrgn"></a>  CRgn::CreatePolyPolygonRgn

一連の閉じた多角形で構成される領域を作成します。

```
BOOL CreatePolyPolygonRgn(
    LPPOINT lpPoints,
    LPINT lpPolyCounts,
    int nCount,
    int nPolyFillMode);
```

### <a name="parameters"></a>パラメーター

*lpPoints*<br/>
構造体の`POINT`配列、または多角形の頂点`CPoint`を定義するオブジェクトの配列を指します。 各ポリゴンは、システムによって自動的に閉じられないため、明示的に閉じる必要があります。 多角形は連続して指定されます。 構造`POINT`体の形式は次のとおりです。

```cpp
typedef struct tagPOINT {
    int x;
    int y;
} POINT;
```

*lpPolyCounts*<br/>
整数の配列を指します。 最初の整数は、 *lpPoints*配列内の最初の多角形の頂点の数を指定し、2番目の整数は2番目の多角形の頂点の数を指定します。

*nCount*<br/>
*LpPolyCounts*配列内の整数の合計数を指定します。

*nPolyFillMode*<br/>
多角形入力モードを指定します。 この値には、代替またはワインディングを使用できます。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

結果として得られる`CRgn`領域は、オブジェクトに格納されます。

ポリゴンは、結合されていない場合もあれば、重なっている場合もあります。

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

多角形の塗りつぶしモードが別の場合、システムは各スキャン行の奇数と偶数の多角形の辺の間に領域を塗りつぶします。 つまり、システムによって、最初と2番目の側、3番目と4番目の側の間の領域が塗りつぶされます。

多角形入力モードがワインディングの場合、システムは、図形が描画された方向を使用して、領域を塗りつぶすかどうかを判断します。 多角形の各線分は、時計回りまたは反時計回りの方向に描画されます。 囲まれた領域から図形の外側に描画された虚数線が時計回りの直線セグメントを通過するたびに、カウントがインクリメントされます。 直線が反時計回りに直線セグメントを通過すると、カウントがデクリメントされます。 線が図形の外側に到達したときに、その数が0以外の場合、領域は塗りつぶされます。

`CreatePolyPolygonRgn`関数で作成された領域を使用してアプリケーションが終了したら、デバイスコンテキストからリージョンを選択し、 [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)メンバー関数を使用して削除します。

##  <a name="createrectrgn"></a>  CRgn::CreateRectRgn

`CRgn`オブジェクトに格納されている四角形の領域を作成します。

```
BOOL CreateRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);
```

### <a name="parameters"></a>パラメーター

*x1*<br/>
領域の左上隅の論理 x 座標を指定します。

*y1*<br/>
領域の左上隅の論理 y 座標を指定します。

*×*<br/>
領域の右下隅の論理 x 座標を指定します。

*y2*<br/>
領域の右下隅の論理 y 座標を指定します。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

によっ`CreateRectRgn`て作成された領域の使用が完了したら、アプリケーションは[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)メンバー関数を使用して領域を削除する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#147](../../mfc/codesnippet/cpp/crgn-class_4.cpp)]

その他の例については、「 [CRgn:: CombineRgn](#combinergn)」を参照してください。

##  <a name="createrectrgnindirect"></a>  CRgn::CreateRectRgnIndirect

`CRgn`オブジェクトに格納されている四角形の領域を作成します。

```
BOOL CreateRectRgnIndirect(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
領域の左上`RECT`隅と`CRect`右下隅の論理座標を格納している構造体またはオブジェクトを指します。 構造`RECT`体の形式は次のとおりです。

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

によっ`CreateRectRgnIndirect`て作成された領域の使用が完了したら、アプリケーションは[CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)メンバー関数を使用して領域を削除する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#148](../../mfc/codesnippet/cpp/crgn-class_5.cpp)]

##  <a name="createroundrectrgn"></a>  CRgn::CreateRoundRectRgn

`CRgn`オブジェクトに格納されている角が丸い四角形の領域を作成します。

```
BOOL CreateRoundRectRgn(
    int x1,
    int y1,
    int x2,
    int y2,
    int x3,
    int y3);
```

### <a name="parameters"></a>パラメーター

*x1*<br/>
領域の左上隅の論理 x 座標を指定します。

*y1*<br/>
領域の左上隅の論理 y 座標を指定します。

*×*<br/>
領域の右下隅の論理 x 座標を指定します。

*y2*<br/>
領域の右下隅の論理 y 座標を指定します。

*x3*<br/>
丸みのある角を作成するために使用する楕円の幅を指定します。

*y3*<br/>
丸みのある角を作成するために使用する楕円の高さを指定します。

### <a name="return-value"></a>戻り値

操作が成功した場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

領域のサイズは、32767論理ユニットまたは 64 k のメモリのうち、いずれか小さい方の32767に制限されます。

`CreateRoundRectRgn`関数で作成された領域を使用してアプリケーションが終了したら、デバイスコンテキストからリージョンを選択し、 [CGDIObject::D eleteobject](../../mfc/reference/cgdiobject-class.md#deleteobject)メンバー関数を使用して削除します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#149](../../mfc/codesnippet/cpp/crgn-class_6.cpp)]

##  <a name="crgn"></a>  CRgn::CRgn

`CRgn` オブジェクトを構築します。

```
CRgn();
```

### <a name="remarks"></a>Remarks

オブジェクト`m_hObject`が他の`CRgn` 1 つ以上のメンバー関数で初期化されるまで、データメンバーに有効な Windows GDI 領域が含まれていません。

### <a name="example"></a>例

  「 [CRgn:: CreateRoundRectRgn](#createroundrectrgn)」の例を参照してください。

##  <a name="equalrgn"></a>  CRgn::EqualRgn

指定された領域が、 `CRgn`オブジェクトに格納されている領域と等しいかどうかを判断します。

```
BOOL EqualRgn(CRgn* pRgn) const;
```

### <a name="parameters"></a>パラメーター

*pRgn*<br/>
リージョンを識別します。

### <a name="return-value"></a>戻り値

2つの領域が等しい場合は0以外の。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#150](../../mfc/codesnippet/cpp/crgn-class_7.cpp)]

##  <a name="fromhandle"></a>CRgn:: FromHandle

Windows 領域へのハンドル`CRgn`が指定された場合に、オブジェクトへのポインターを返します。

```
static CRgn* PASCAL FromHandle(HRGN hRgn);
```

### <a name="parameters"></a>パラメーター

*hRgn*<br/>
Windows 領域へのハンドルを指定します。

### <a name="return-value"></a>戻り値

`CRgn` オブジェクトへのポインター。 関数が成功しなかった場合、戻り値は NULL になります。

### <a name="remarks"></a>Remarks

オブジェクトがハンドルにまだアタッチされていない場合は`CRgn` 、一時オブジェクトが作成され、アタッチされます。 `CRgn` この一時`CRgn`オブジェクトは、アプリケーションが次にそのイベントループ内でアイドル状態になったときにのみ有効です。その時点で、すべての一時グラフィックオブジェクトが削除されます。 別の方法として、一時オブジェクトは1つのウィンドウメッセージの処理中にのみ有効であるということもあります。

##  <a name="getregiondata"></a>  CRgn::GetRegionData

領域を記述するデータを指定したバッファーに格納します。

```
int GetRegionData(
    LPRGNDATA lpRgnData,
    int nCount) const;
```

### <a name="parameters"></a>パラメーター

*lpRgnData*<br/>
情報を受け取る[Rgndata](/windows/win32/api/wingdi/ns-wingdi-rgndata)構造体を指します。 このパラメーターが NULL の場合、戻り値には、領域データに必要なバイト数が含まれます。

*nCount*<br/>
*LpRgnData*バッファーのサイズ (バイト単位) を指定します。

### <a name="return-value"></a>戻り値

関数が成功し、 *nCount*に適切なバイト数が指定されている場合、戻り値は常に*ncount*になります。 関数が失敗した場合、または*nCount*が適切なバイト数より少ない場合、戻り値は 0 (error) になります。

### <a name="remarks"></a>Remarks

このデータには、領域を構成する四角形の寸法が含まれます。 この関数は、 `CRgn::CreateFromData`関数と組み合わせて使用されます。

##  <a name="getrgnbox"></a>  CRgn::GetRgnBox

`CRgn`オブジェクトの外接する四角形の座標を取得します。

```
int GetRgnBox(LPRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
外接する四角形`RECT`の座標`CRect`を受け取る構造体またはオブジェクトを指します。 構造`RECT`体の形式は次のとおりです。

`typedef struct tagRECT {`

`int left;`

`int top;`

`int right;`

`int bottom;`

`} RECT;`

### <a name="return-value"></a>戻り値

領域の種類を指定します。 次のいずれかの値を指定できます。

- COMPLEXREGION 領域に重複する境界線があります。

- NULLREGION 領域が空です。

- エラー `CRgn`オブジェクトには有効なリージョンが指定されていません。

- SIMPLEREGION Region には重複する境界線がありません。

### <a name="example"></a>例

  「 [CRgn:: CreatePolygonRgn](#createpolygonrgn)」の例を参照してください。

##  <a name="offsetrgn"></a>  CRgn::OffsetRgn

`CRgn`オブジェクトに格納されている領域を、指定したオフセットで移動します。

```
int OffsetRgn(
    int x,
    int y);

int OffsetRgn(POINT point);
```

### <a name="parameters"></a>パラメーター

*x*<br/>
左または右に移動する単位の数を指定します。

*y*<br/>
上または下に移動する単位の数を指定します。

*視点*<br/>
*Point*の x 座標は、左または右に移動する単位の数を指定します。 *ポイント*の y 座標は、上または下に移動する単位の数を指定します。 *Point*パラメーターには、構造体`POINT`また`CPoint`はオブジェクトを指定できます。

### <a name="return-value"></a>戻り値

新しい領域の型。 次のいずれかの値を指定できます。

- COMPLEXREGION 領域に重複する境界線があります。

- エラー領域ハンドルが無効です。

- NULLREGION 領域が空です。

- SIMPLEREGION Region には重複する境界線がありません。

### <a name="remarks"></a>Remarks

関数は、y 軸に沿って x 軸と*y*単位に沿って領域の*x*単位を移動します。

領域の座標値は、32767以下かつ-32768 以上である必要があります。 無効な領域の座標を防ぐために、 *x*および*y*パラメーターを慎重に選択する必要があります。

### <a name="example"></a>例

  「 [CRgn:: CreateEllipticRgn](#createellipticrgn)」の例を参照してください。

##  <a name="operator_hrgn"></a>  CRgn::operator HRGN

`CRgn`オブジェクトのアタッチされた Windows GDI ハンドルを取得するには、この演算子を使用します。

```
operator HRGN() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、 `CRgn`オブジェクトによって表される Windows GDI オブジェクトへのハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

この演算子は、HRGN オブジェクトの直接使用をサポートするキャスト演算子です。

グラフィックオブジェクトの使用方法の詳細については、Windows SDK の「[グラフィックオブジェクト](/windows/win32/gdi/graphic-objects)」を参照してください。

##  <a name="ptinregion"></a>  CRgn::PtInRegion

*X*と*y*によって指定された点が、 `CRgn`オブジェクトに格納されている領域内にあるかどうかを確認します。

```
BOOL PtInRegion(
    int x,
    int y) const;

BOOL PtInRegion(POINT point) const;
```

### <a name="parameters"></a>パラメーター

*x*<br/>
テストする点の論理 x 座標を指定します。

*y*<br/>
テストする点の論理 y 座標を指定します。

*視点*<br/>
*点*の x 座標と y 座標は、値をテストする点の x 座標と y 座標を指定します。 *Point*パラメーターには、 `POINT`構造体また`CPoint`はオブジェクトを指定できます。

### <a name="return-value"></a>戻り値

点が領域内にある場合は0以外の。それ以外の場合は0です。

##  <a name="rectinregion"></a>  CRgn::RectInRegion

*LpRect*によって指定された四角形のいずれかの部分が、 `CRgn`オブジェクトに格納されている領域の境界内にあるかどうかを判断します。

```
BOOL RectInRegion(LPCRECT lpRect) const;
```

### <a name="parameters"></a>パラメーター

*lpRect*<br/>
`RECT`構造体または`CRect`オブジェクトを指します。 構造`RECT`体の形式は次のとおりです。

```cpp
typedef struct tagRECT {
    int left;
    int top;
    int right;
    int bottom;
} RECT;
```

### <a name="return-value"></a>戻り値

指定した四角形のいずれかの部分が領域の境界内にある場合は0以外の。それ以外の場合は0です。

##  <a name="setrectrgn"></a>  CRgn::SetRectRgn

四角形の領域を作成します。

```
void SetRectRgn(
    int x1,
    int y1,
    int x2,
    int y2);

void SetRectRgn(LPCRECT lpRect);
```

### <a name="parameters"></a>パラメーター

*x1*<br/>
四角形領域の左上隅の x 座標を指定します。

*y1*<br/>
四角形領域の左上隅の y 座標を指定します。

*×*<br/>
四角形領域の右下隅の x 座標を指定します。

*y2*<br/>
四角形領域の右下隅の y 座標を指定します。

*lpRect*<br/>
四角形の領域を指定します。 には、 `RECT`構造体`CRect`またはオブジェクトへのポインターを指定できます。

### <a name="remarks"></a>Remarks

ただし、 [CreateRectRgn](#createrectrgn)とは異なり、ローカル Windows アプリケーションヒープから追加のメモリは割り当てられません。 代わりに、 `CRgn`オブジェクトに格納されている領域に割り当てられた領域を使用します。 これは、を`CRgn`呼び出す`SetRectRgn`前に、オブジェクトが有効な Windows 領域を使用して既に初期化されている必要があることを意味します。 *X1*、 *y1*、 *x2*、および*y2*によって指定されるポイントは、割り当てられた領域の最小サイズを指定します。

ローカルメモリマネージャーの呼び出しを`CreateRectRgn`回避するには、メンバー関数の代わりにこの関数を使用します。

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)
