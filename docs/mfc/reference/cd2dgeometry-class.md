---
title: CD2DGeometry クラス
ms.date: 11/04/2016
f1_keywords:
- CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::CD2DGeometry
- AFXRENDERTARGET/CD2DGeometry::Attach
- AFXRENDERTARGET/CD2DGeometry::CombineWithGeometry
- AFXRENDERTARGET/CD2DGeometry::CompareWithGeometry
- AFXRENDERTARGET/CD2DGeometry::ComputeArea
- AFXRENDERTARGET/CD2DGeometry::ComputeLength
- AFXRENDERTARGET/CD2DGeometry::ComputePointAtLength
- AFXRENDERTARGET/CD2DGeometry::Destroy
- AFXRENDERTARGET/CD2DGeometry::Detach
- AFXRENDERTARGET/CD2DGeometry::FillContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Get
- AFXRENDERTARGET/CD2DGeometry::GetBounds
- AFXRENDERTARGET/CD2DGeometry::GetWidenedBounds
- AFXRENDERTARGET/CD2DGeometry::IsValid
- AFXRENDERTARGET/CD2DGeometry::Outline
- AFXRENDERTARGET/CD2DGeometry::Simplify
- AFXRENDERTARGET/CD2DGeometry::StrokeContainsPoint
- AFXRENDERTARGET/CD2DGeometry::Tessellate
- AFXRENDERTARGET/CD2DGeometry::Widen
- AFXRENDERTARGET/CD2DGeometry::m_pGeometry
helpviewer_keywords:
- CD2DGeometry [MFC], CD2DGeometry
- CD2DGeometry [MFC], Attach
- CD2DGeometry [MFC], CombineWithGeometry
- CD2DGeometry [MFC], CompareWithGeometry
- CD2DGeometry [MFC], ComputeArea
- CD2DGeometry [MFC], ComputeLength
- CD2DGeometry [MFC], ComputePointAtLength
- CD2DGeometry [MFC], Destroy
- CD2DGeometry [MFC], Detach
- CD2DGeometry [MFC], FillContainsPoint
- CD2DGeometry [MFC], Get
- CD2DGeometry [MFC], GetBounds
- CD2DGeometry [MFC], GetWidenedBounds
- CD2DGeometry [MFC], IsValid
- CD2DGeometry [MFC], Outline
- CD2DGeometry [MFC], Simplify
- CD2DGeometry [MFC], StrokeContainsPoint
- CD2DGeometry [MFC], Tessellate
- CD2DGeometry [MFC], Widen
- CD2DGeometry [MFC], m_pGeometry
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
ms.openlocfilehash: 4549b2e7981d5f8493ddf9f24477e75a94ddde8b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405730"
---
# <a name="cd2dgeometry-class"></a>CD2DGeometry クラス

ID2D1Geometry のラッパーです。

## <a name="syntax"></a>構文

```
class CD2DGeometry : public CD2DResource;
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CD2DGeometry::CD2DGeometry](#cd2dgeometry)|CD2DGeometry オブジェクトを構築します。|
|[CD2DGeometry:: ~ CD2DGeometry](#_dtorcd2dgeometry)|デストラクターです。 D2D ジオメトリ オブジェクトが破棄されるときに呼び出されます。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CD2DGeometry::Attach](#attach)|既存のリソース インターフェイス オブジェクトにアタッチします|
|[CD2DGeometry::CombineWithGeometry](#combinewithgeometry)|このジオメトリと指定したジオメトリを結合し、その結果、ID2D1SimplifiedGeometrySink に格納します。|
|[CD2DGeometry::CompareWithGeometry](#comparewithgeometry)|このジオメトリと指定したジオメトリの交差部分をについて説明します。 比較がフラット化の指定した許容範囲を使用して実行されます。|
|[CD2DGeometry::ComputeArea](#computearea)|ジオメトリの領域が計算された後に指定した行列によって変換され、指定した許容範囲を使用してフラット化します。|
|[CD2DGeometry::ComputeLength](#computelength)|各セグメントは直線にロールバックされた場合と同様に、ジオメトリの長さを計算します。|
|[CD2DGeometry::ComputePointAtLength](#computepointatlength)|ジオメトリに指定された距離にある点と接線ベクターが計算された後に指定した行列によって変換され、指定した許容範囲を使用してフラット化します。|
|[CD2DGeometry::Destroy](#destroy)|CD2DGeometry オブジェクトを破棄します。 (上書き[CD2DResource::Destroy](../../mfc/reference/cd2dresource-class.md#destroy))。|
|[CD2DGeometry::Detach](#detach)|オブジェクトからリソースのインターフェイスをデタッチします。|
|[CD2DGeometry::FillContainsPoint](#fillcontainspoint)|ジオメトリで塗りつぶす領域はフラット化の指定した許容範囲を指定した指定したポイントを含めるかどうかを示します。|
|[CD2DGeometry::Get](#get)|返します ID2D1Geometry インターフェイス|
|[CD2DGeometry::GetBounds](#getbounds)||
|[CD2DGeometry::GetWidenedBounds](#getwidenedbounds)|指定したストロークの幅とスタイルによって拡大され、指定した行列によって変換された後は、ジオメトリの境界を取得します。|
|[CD2DGeometry::IsValid](#isvalid)|リソースの有効性を確認します (上書き[CD2DResource::IsValid](../../mfc/reference/cd2dresource-class.md#isvalid))。|
|[CD2DGeometry::Outline](#outline)|Geometry の輪郭を計算し、結果を ID2D1SimplifiedGeometrySink に書き込みます。|
|[CD2DGeometry::Simplify](#simplify)|ジオメトリを行と (必要に応じて) 3 次ベジエ曲線のみを含み、ID2D1SimplifiedGeometrySink に結果を書き出すの簡略化されたバージョンを作成します。|
|[CD2DGeometry::StrokeContainsPoint](#strokecontainspoint)|ジオメトリのストロークが指定したストロークの太さ、スタイル、および変換を指定した指定したポイントを含むかどうかを判断します。|
|[CD2DGeometry::Tessellate](#tessellate)|指定した行列を使用して変換された後に、geometry をカバーし、指定した許容範囲を使用してフラット化する時計回りの三角形のセットを作成します。|
|[CD2DGeometry::Widen](#widen)|指定したストロークでジオメトリを拡大し、された後に、ID2D1SimplifiedGeometrySink に結果を書き出すと指定の行列変換し、指定した許容範囲を使用してフラット化します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CD2DGeometry::operator ID2D1Geometry *](#operator_id2d1geometry_star)|返します ID2D1Geometry インターフェイス|

### <a name="protected-data-members"></a>プロテクト データ メンバー

|名前|説明|
|----------|-----------------|
|[CD2DGeometry::m_pGeometry](#m_pgeometry)|ID2D1Geometry へのポインター。|

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CD2DResource](../../mfc/reference/cd2dresource-class.md)

`CD2DGeometry`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxrendertarget.h

##  <a name="_dtorcd2dgeometry"></a>  CD2DGeometry:: ~ CD2DGeometry

デストラクターです。 D2D ジオメトリ オブジェクトが破棄されるときに呼び出されます。

```
virtual ~CD2DGeometry();
```

##  <a name="attach"></a>  CD2DGeometry::Attach

既存のリソース インターフェイス オブジェクトにアタッチします

```
void Attach(ID2D1Geometry* pResource);
```

### <a name="parameters"></a>パラメーター

*pResource*<br/>
既存のリソース インターフェイスです。 NULL にすることはできません。

##  <a name="cd2dgeometry"></a>  CD2DGeometry::CD2DGeometry

CD2DGeometry オブジェクトを構築します。

```
CD2DGeometry(
    CRenderTarget* pParentTarget,
    BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>パラメーター

*pParentTarget*<br/>
レンダー ターゲットへのポインター。

*bAutoDestroy*<br/>
所有者 (pParentTarget) によって、オブジェクトが破棄されることを示します。

##  <a name="combinewithgeometry"></a>  CD2DGeometry::CombineWithGeometry

このジオメトリと指定したジオメトリを結合し、その結果、ID2D1SimplifiedGeometrySink に格納します。

```
BOOL CombineWithGeometry(
    CD2DGeometry& inputGeometry,
    D2D1_COMBINE_MODE combineMode,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*inputGeometry*<br/>
このインスタンスと結合するジオメトリ。

*combineMode*<br/>
実行する結合操作の種類。

*inputGeometryTransform*<br/>
結合する前に inputGeometry に適用する変換。

*geometrySink*<br/>
結合操作の結果。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="comparewithgeometry"></a>  CD2DGeometry::CompareWithGeometry

このジオメトリと指定したジオメトリの交差部分をについて説明します。 比較がフラット化の指定した許容範囲を使用して実行されます。

```
D2D1_GEOMETRY_RELATION CompareWithGeometry(
    CD2DGeometry& inputGeometry,
    const D2D1_MATRIX_3X2_F& inputGeometryTransform,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*inputGeometry*<br/>
テストするジオメトリ。

*inputGeometryTransform*<br/>
InputGeometry に適用する変換。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="computearea"></a>  CD2DGeometry::ComputeArea

ジオメトリの領域が計算された後に指定した行列によって変換され、指定した許容範囲を使用してフラット化します。

```
BOOL ComputeArea(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& area,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*worldTransform*<br/>
その領域を計算する前に、このジオメトリに適用する変換。

*領域*<br/>
このメソッドが戻るときに、このジオメトリの変換、フラット化されたバージョンの領域へのポインターが含まれています。 このパラメーターは、記憶域を割り当てる必要があります。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="computelength"></a>  CD2DGeometry::ComputeLength

各セグメントは直線にロールバックされた場合と同様に、ジオメトリの長さを計算します。

```
BOOL ComputeLength(
    const D2D1_MATRIX_3X2_F& worldTransform,
    FLOAT& length,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*worldTransform*<br/>
その長さを計算する前に、ジオメトリに適用する変換。

*length*<br/>
このメソッドが戻るときに、ジオメトリの長さへのポインターが含まれています。 閉じられた場合は、長さには、暗黙的な終了セグメントが含まれています。 このパラメーターは、記憶域を割り当てる必要があります。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="computepointatlength"></a>  CD2DGeometry::ComputePointAtLength

ジオメトリに指定された距離にある点と接線ベクターが計算された後に指定した行列によって変換され、指定した許容範囲を使用してフラット化します。

```
BOOL ComputePointAtLength(
    FLOAT length,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DPointF& point,
    CD2DPointF& unitTangentVector,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*length*<br/>
ジオメトリのポイントと検索に接するに沿った距離。 この距離が小さいし 0 の場合、このメソッドは、ジオメトリの最初の点を計算します。 この距離がジオメトリの長さより大きい場合は、このメソッドは、ジオメトリの最後の点を計算します。

*worldTransform*<br/>
指定したポイントとタンジェントを計算する前に、ジオメトリに適用する変換。

*ポイント*<br/>
ジオメトリに指定された距離にある場所です。 このポイントにはで、x および y として NaN が含まれています、ジオメトリが空の場合の値。

*unitTangentVector*<br/>
このメソッドが戻るときに、ジオメトリに指定された距離にある接線ベクターへのポインターが含まれています。 このベクターにはで、x および y として NaN が含まれています、ジオメトリが空の場合の値。 このパラメーターは、記憶域を割り当てる必要があります。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="destroy"></a>  CD2DGeometry::Destroy

CD2DGeometry オブジェクトを破棄します。

```
virtual void Destroy();
```

##  <a name="detach"></a>  CD2DGeometry::Detach

オブジェクトからリソースのインターフェイスをデタッチします。

```
ID2D1Geometry* Detach();
```

### <a name="return-value"></a>戻り値

インターフェイスのデタッチされたリソースへのポインター。

##  <a name="fillcontainspoint"></a>  CD2DGeometry::FillContainsPoint

ジオメトリで塗りつぶす領域はフラット化の指定した許容範囲を指定した指定したポイントを含めるかどうかを示します。

```
BOOL FillContainsPoint(
    CD2DPointF point,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
テストする点です。

*worldTransform*<br/>
包含をテストする前に、ジオメトリに適用する変換。

*contains*<br/>
このメソッドが戻るときに、geometry で塗りつぶす領域には、ポイントが含まれている場合は TRUE であるブール値が含まれていますそれ以外の場合、FALSE です。 このパラメーターは、記憶域を割り当てる必要があります。

*flatteningTolerance*<br/>
これを使用した数値の精度、正確なジオメトリック パスとパスの交差部分が計算されます。 内で、許容範囲より小さいして塗りつぶしを見つからないポイントと見なされます。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="get"></a>  CD2DGeometry::Get

返します ID2D1Geometry インターフェイス

```
ID2D1Geometry* Get();
```

### <a name="return-value"></a>戻り値

ID2D1Geometry インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="getbounds"></a>  CD2DGeometry::GetBounds

```
BOOL GetBounds(
const D2D1_MATRIX_3X2_F& worldTransform,
CD2DRectF& bounds) const;
```

### <a name="parameters"></a>パラメーター

*worldTransform*<br/>
*境界*

### <a name="return-value"></a>戻り値

##  <a name="getwidenedbounds"></a>  CD2DGeometry::GetWidenedBounds

指定したストロークの幅とスタイルによって拡大され、指定した行列によって変換された後は、ジオメトリの境界を取得します。

```
BOOL GetWidenedBounds(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    CD2DRectF& bounds,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*strokeWidth*<br/>
アウトラインを描画してジオメトリを拡大する量。

*strokeStyle*<br/>
ジオメトリを拡大する線のスタイル。

*worldTransform*<br/>
ジオメトリを変換し、ジオメトリの線を付ける後に、ジオメトリに適用する変換。

*境界*<br/>
このメソッドが戻るときに、拡張の geometry の境界が含まれています。 このパラメーターは、記憶域を割り当てる必要があります。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="isvalid"></a>  CD2DGeometry::IsValid

リソースの有効性のチェック

```
virtual BOOL IsValid() const;
```

### <a name="return-value"></a>戻り値

リソースが有効な場合は TRUE。それ以外の場合は FALSE です。

##  <a name="m_pgeometry"></a>  CD2DGeometry::m_pGeometry

ID2D1Geometry へのポインター。

```
ID2D1Geometry* m_pGeometry;
```

##  <a name="operator_id2d1geometry_star"></a>  CD2DGeometry::operator ID2D1Geometry*

返します ID2D1Geometry インターフェイス

```
operator ID2D1Geometry*();
```

### <a name="return-value"></a>戻り値

ID2D1Geometry インターフェイスまたはオブジェクトはまだ初期化されていない場合は NULL へのポインター。

##  <a name="outline"></a>  CD2DGeometry::Outline

Geometry の輪郭を計算し、結果を ID2D1SimplifiedGeometrySink に書き込みます。

```
BOOL Outline(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*worldTransform*<br/>
ジオメトリのアウトラインに適用する変換。

*geometrySink*<br/>
ジオメトリのアウトラインの変換先 ID2D1SimplifiedGeometrySink が追加されます。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="simplify"></a>  CD2DGeometry::Simplify

ジオメトリを行と (必要に応じて) 3 次ベジエ曲線のみを含み、ID2D1SimplifiedGeometrySink に結果を書き出すの簡略化されたバージョンを作成します。

```
BOOL Simplify(
    D2D1_GEOMETRY_SIMPLIFICATION_OPTION simplificationOption,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*simplificationOption*<br/>
簡略化されたジオメトリのカーブを含めるかどうかを指定する値。

*worldTransform*<br/>
簡略化されたジオメトリに適用する変換。

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink 簡略化されたジオメトリが追加されます。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="strokecontainspoint"></a>  CD2DGeometry::StrokeContainsPoint

ジオメトリのストロークが指定したストロークの太さ、スタイル、および変換を指定した指定したポイントを含むかどうかを判断します。

```
BOOL StrokeContainsPoint(
    CD2DPointF point,
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    BOOL* contains,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*ポイント*<br/>
コンテインメントのテスト ポイント。

*strokeWidth*<br/>
適用するストロークの太さです。

*strokeStyle*<br/>
適用する線のスタイル。

*worldTransform*<br/>
線のジオメトリに適用する変換。

*contains*<br/>
このメソッドが戻るときに指定した点がジオメトリのストロークに含まれている場合に TRUE に設定するブール値が含まれていますそれ以外の場合、FALSE です。 このパラメーターは、記憶域を割り当てる必要があります。

*flatteningTolerance*<br/>
これを使用した数値の精度、正確なジオメトリック パスとパスの交差部分が計算されます。 内でポイントして、許容範囲より小さい、ストロークを見つからないと見なされます。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="tessellate"></a>  CD2DGeometry::Tessellate

指定した行列を使用して変換された後に、geometry をカバーし、指定した許容範囲を使用してフラット化する時計回りの三角形のセットを作成します。

```
BOOL Tessellate(
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1TessellationSink* tessellationSink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*worldTransform*<br/>
この geometry の場合、または NULL に適用する変換。

*tessellationSink*<br/>
テセレーションされた追加 ID2D1TessellationSink します。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

##  <a name="widen"></a>  CD2DGeometry::Widen

指定したストロークでジオメトリを拡大し、された後に、ID2D1SimplifiedGeometrySink に結果を書き出すと指定の行列変換し、指定した許容範囲を使用してフラット化します。

```
BOOL Widen(
    FLOAT strokeWidth,
    ID2D1StrokeStyle* strokeStyle,
    const D2D1_MATRIX_3X2_F& worldTransform,
    ID2D1SimplifiedGeometrySink* geometrySink,
    FLOAT flatteningTolerance = D2D1_DEFAULT_FLATTENING_TOLERANCE) const;
```

### <a name="parameters"></a>パラメーター

*strokeWidth*<br/>
ジオメトリの拡大変換する量。

*strokeStyle*<br/>
Geometry、または NULL に適用する線のスタイル。

*worldTransform*<br/>
これを拡大した後、ジオメトリに適用する変換。

*geometrySink*<br/>
ID2D1SimplifiedGeometrySink 拡張 geometry が追加されます。

*flatteningTolerance*<br/>
ジオメトリの多角形近似における点の間の距離の上限。 小さい値はより正確な結果を生成しますが、実行速度が低下します。

### <a name="return-value"></a>戻り値

メソッドが成功した場合は、TRUE を返します。 それ以外の場合、FALSE を返します。

## <a name="see-also"></a>関連項目

[クラス](../../mfc/reference/mfc-classes.md)
