---
title: CD2DGeometrySink クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::CD2DGeometrySink
- AFXRENDERTARGET/CD2DGeometrySink::AddArc
- AFXRENDERTARGET/CD2DGeometrySink::AddBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddBeziers
- AFXRENDERTARGET/CD2DGeometrySink::AddLine
- AFXRENDERTARGET/CD2DGeometrySink::AddLines
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBezier
- AFXRENDERTARGET/CD2DGeometrySink::AddQuadraticBeziers
- AFXRENDERTARGET/CD2DGeometrySink::BeginFigure
- AFXRENDERTARGET/CD2DGeometrySink::Close
- AFXRENDERTARGET/CD2DGeometrySink::EndFigure
- AFXRENDERTARGET/CD2DGeometrySink::Get
- AFXRENDERTARGET/CD2DGeometrySink::IsValid
- AFXRENDERTARGET/CD2DGeometrySink::SetFillMode
- AFXRENDERTARGET/CD2DGeometrySink::SetSegmentFlags
- AFXRENDERTARGET/CD2DGeometrySink::m_pSink
helpviewer_keywords:
- CD2DGeometrySink [MFC], CD2DGeometrySink
- CD2DGeometrySink [MFC], AddArc
- CD2DGeometrySink [MFC], AddBezier
- CD2DGeometrySink [MFC], AddBeziers
- CD2DGeometrySink [MFC], AddLine
- CD2DGeometrySink [MFC], AddLines
- CD2DGeometrySink [MFC], AddQuadraticBezier
- CD2DGeometrySink [MFC], AddQuadraticBeziers
- CD2DGeometrySink [MFC], BeginFigure
- CD2DGeometrySink [MFC], Close
- CD2DGeometrySink [MFC], EndFigure
- CD2DGeometrySink [MFC], Get
- CD2DGeometrySink [MFC], IsValid
- CD2DGeometrySink [MFC], SetFillMode
- CD2DGeometrySink [MFC], SetSegmentFlags
- CD2DGeometrySink [MFC], m_pSink
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
ms.openlocfilehash: 48c88f0b837b2e49e4c87f07a9aa28c16a66c1e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391258"
---
# <a name="cd2dgeometrysink-class"></a>CD2DGeometrySink クラス

ID2D1GeometrySink のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DGeometrySink;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DGeometrySink::CD2DGeometrySink](#cd2dgeometrysink)|CD2DPathGeometry オブジェクトから CD2DGeometrySink オブジェクトを構築します。|
|[CD2DGeometrySink:: ~ CD2DGeometrySink](#_dtorcd2dgeometrysink)|デストラクターです。 D2D geometry シンク オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DGeometrySink::AddArc](#addarc)|パス ジオメトリに 1 つの円弧を追加します。|
|[CD2DGeometrySink::AddBezier](#addbezier)|現在の点と指定された終点の間に 3 次ベジエ曲線を作成します。|
|[CD2DGeometrySink::AddBeziers](#addbeziers)|3 次ベジエ曲線のシーケンスを作成し、geometry シンクに追加します。|
|[CD2DGeometrySink::AddLine](#addline)|現在の点と指定された終点の間の直線セグメントを作成し、geometry シンクに追加します。|
|[CD2DGeometrySink::AddLines](#addlines)|指定されたポイントを使用して行のシーケンスを作成し、geometry シンクに追加します。|
|[CD2DGeometrySink::AddQuadraticBezier](#addquadraticbezier)|現在の点と指定された終点の間に 2 次ベジエ曲線を作成します。|
|[CD2DGeometrySink::AddQuadraticBeziers](#addquadraticbeziers)|1 回の呼び出しでは配列として、2 次ベジエ セグメントのシーケンスを追加します。|
|[CD2DGeometrySink::BeginFigure](#beginfigure)|指定したポイントに新しい図形を開始します。|
|[CD2DGeometrySink::Close](#close)|ジオメトリのシンクを閉じます|
|[CD2DGeometrySink::EndFigure](#endfigure)|現在の図形を終了します。必要に応じて、これを閉じます。|
|[CD2DGeometrySink::Get](#get)|返します ID2D1GeometrySink インターフェイス|
|[CD2DGeometrySink::IsValid](#isvalid)|ジオメトリのシンクの有効性を確認します。|
|[CD2DGeometrySink::SetFillMode](#setfillmode)|この geometry シンクによって説明されている geometry 内のポイントは、の外側にあるポイントを判断するために使用するメソッドを指定します。|
|[CD2DGeometrySink::SetSegmentFlags](#setsegmentflags)|ジオメトリのシンクに追加された新しいセグメントに適用する線と結合オプションを指定します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DGeometrySink::operator ID2D1GeometrySink*](#operator_id2d1geometrysink_star)|返します ID2D1GeometrySink インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DGeometrySink::m_pSink](#m_psink)|ID2D1GeometrySink へのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

`CD2DGeometrySink`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dgeometrysink"></a>  CD2DGeometrySink:: ~ CD2DGeometrySink

デストラクターです。 D2D geometry シンク オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DGeometrySink();
```

##  <a name="addarc"></a>  CD2DGeometrySink::AddArc

パス ジオメトリに 1 つの円弧を追加します。

```
void AddArc(const D2D1_ARC_SEGMENT& arc);
```

### <a name="parameters"></a>パラメーター

*arc*<br/>
円弧のセグメントの図に追加するには

##  <a name="addbezier"></a>  CD2DGeometrySink::AddBezier

現在の点と指定された終点の間に 3 次ベジエ曲線を作成します。

```
void AddBezier(const D2D1_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>パラメーター

*ベジエ*<br/>
制御点と追加するベジエ曲線の終点を表す構造体。

##  <a name="addbeziers"></a>  CD2DGeometrySink::AddBeziers

3 次ベジエ曲線のシーケンスを作成し、geometry シンクに追加します。

```
void AddBeziers(
    const CArray<D2D1_BEZIER_SEGMENT,
    D2D1_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>パラメーター

*ベジエ曲線*<br/>
作成するベジエ曲線を記述するベジエ セグメントの配列。 曲線は、geometry シンクの現在のポイント (最後のセグメントを描画または BeginFigure で指定された位置の終了ポイント) から、配列の最初のベジエ セグメントの終点に描画されます。 配列に追加のベジエ セグメントが含まれている場合、後続の各ベジエ セグメントはその開始点として前のベジエ セグメントの終点を使用します。

##  <a name="addline"></a>  CD2DGeometrySink::AddLine

現在の点と指定された終点の間の直線セグメントを作成し、geometry シンクに追加します。

```
void AddLine(CD2DPointF point);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
描画する線の終点。

##  <a name="addlines"></a>  CD2DGeometrySink::AddLines

指定されたポイントを使用して行のシーケンスを作成し、geometry シンクに追加します。

```
void AddLines(
    const CArray<CD2DPointF,
    CD2DPointF>& points);
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
描画するために行を 1 つまたは複数の点の配列。 行は、geometry シンクの現在のポイント (最後のセグメントを描画または BeginFigure で指定された位置の終了ポイント) から、配列の最初の点に描画されます。 配列に追加の点が含まれている場合と 3 番目のポイントでは、2 つ目の点から、配列の 2 番目の点に、行が最初の点から描画されます。 描画する線の終点のシーケンスの配列。

##  <a name="addquadraticbezier"></a>  CD2DGeometrySink::AddQuadraticBezier

現在の点と指定された終点の間に 2 次ベジエ曲線を作成します。

```
void AddQuadraticBezier(const D2D1_QUADRATIC_BEZIER_SEGMENT& bezier);
```

### <a name="parameters"></a>パラメーター

*ベジエ*<br/>
制御点と追加の 2 次ベジエ曲線の終点を表す構造体。

##  <a name="addquadraticbeziers"></a>  CD2DGeometrySink::AddQuadraticBeziers

1 回の呼び出しでは配列として、2 次ベジエ セグメントのシーケンスを追加します。

```
void AddQuadraticBeziers(
    const CArray<D2D1_QUADRATIC_BEZIER_SEGMENT,
    D2D1_QUADRATIC_BEZIER_SEGMENT>& beziers);
```

### <a name="parameters"></a>パラメーター

*ベジエ曲線*<br/>
2 次ベジエ セグメントのシーケンスの配列。

##  <a name="beginfigure"></a>  CD2DGeometrySink::BeginFigure

指定したポイントに新しい図形を開始します。

```
void BeginFigure(
    CD2DPointF startPoint,
    D2D1_FIGURE_BEGIN figureBegin);
```

### <a name="parameters"></a>パラメーター

*startPoint*<br/>
新しい図形を開始するポイント。

*figureBegin*<br/>
かどうか白抜きまたは塗りつぶされた新しい図になります。

##  <a name="cd2dgeometrysink"></a>  CD2DGeometrySink::CD2DGeometrySink

CD2DPathGeometry オブジェクトから CD2DGeometrySink オブジェクトを構築します。

```
CD2DGeometrySink(CD2DPathGeometry& pathGeometry);
```

### <a name="parameters"></a>パラメーター

*pathGeometry*<br/>
既存の CD2DPathGeometry オブジェクト。

##  <a name="close"></a>  CD2DGeometrySink::Close

ジオメトリのシンクを閉じます

```
BOOL Close();
```

### <a name="return-value"></a>戻り値

成功した場合、0 以外の場合それ以外の場合は FALSE です。

##  <a name="endfigure"></a>  CD2DGeometrySink::EndFigure

現在の図形を終了します。必要に応じて、これを閉じます。

```
void EndFigure(D2D1_FIGURE_END figureEnd);
```

### <a name="parameters"></a>パラメーター

*figureEnd*<br/>
現在の図形を閉じるかどうかを示す値。 図が閉じている場合、現在のポイントと BeginFigure で指定された開始点の間に行を描画します。

##  <a name="get"></a>  CD2DGeometrySink::Get

返します ID2D1GeometrySink インターフェイス

```
ID2D1GeometrySink* Get();
```

### <a name="return-value"></a>戻り値

ID2D1GeometrySink インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="isvalid"></a>  CD2DGeometrySink::IsValid

ジオメトリのシンクの有効性を確認します。

```
BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

Geometry シンクが有効な場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_psink"></a>  CD2DGeometrySink::m_pSink

ID2D1GeometrySink へのポインター。

```
ID2D1GeometrySink* m_pSink;
```

##  <a name="operator_id2d1geometrysink_star"></a>  CD2DGeometrySink::operator ID2D1GeometrySink*

返します ID2D1GeometrySink インターフェイス

```
operator ID2D1GeometrySink*();
```

### <a name="return-value"></a>戻り値

ID2D1GeometrySink インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="setfillmode"></a>  CD2DGeometrySink::SetFillMode

この geometry シンクによって説明されている geometry 内のポイントは、の外側にあるポイントを判断するために使用するメソッドを指定します。

```
void SetFillMode(D2D1_FILL_MODE fillMode);
```

### <a name="parameters"></a>パラメーター

*fillMode*<br/>
指定された点がジオメトリの一部であるかどうかを判断するために使用するメソッド。

##  <a name="setsegmentflags"></a>  CD2DGeometrySink::SetSegmentFlags

ジオメトリのシンクに追加された新しいセグメントに適用する線と結合オプションを指定します。

```
void SetSegmentFlags(D2D1_PATH_SEGMENT vertexFlags);
```

### <a name="parameters"></a>パラメーター

*vertexFlags*<br/>
ジオメトリに追加された新しいセグメントに適用されるストロークと結合のオプションは、次のシンクします。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
