---
title: CBrush クラス
ms.date: 11/04/2016
f1_keywords:
- CBrush
- AFXWIN/CBrush
- AFXWIN/CBrush::CBrush
- AFXWIN/CBrush::CreateBrushIndirect
- AFXWIN/CBrush::CreateDIBPatternBrush
- AFXWIN/CBrush::CreateHatchBrush
- AFXWIN/CBrush::CreatePatternBrush
- AFXWIN/CBrush::CreateSolidBrush
- AFXWIN/CBrush::CreateSysColorBrush
- AFXWIN/CBrush::FromHandle
- AFXWIN/CBrush::GetLogBrush
helpviewer_keywords:
- CBrush [MFC], CBrush
- CBrush [MFC], CreateBrushIndirect
- CBrush [MFC], CreateDIBPatternBrush
- CBrush [MFC], CreateHatchBrush
- CBrush [MFC], CreatePatternBrush
- CBrush [MFC], CreateSolidBrush
- CBrush [MFC], CreateSysColorBrush
- CBrush [MFC], FromHandle
- CBrush [MFC], GetLogBrush
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
ms.openlocfilehash: a99d8c8022d23f627320b66c3f376be803c9c839
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507435"
---
# <a name="cbrush-class"></a>CBrush クラス

Windows のグラフィック デバイス インターフェイス (GDI) のブラシをカプセル化します。

## <a name="syntax"></a>構文

```
class CBrush : public CGdiObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CBrush:: CBrush](#cbrush)|`CBrush` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CBrush::CreateBrushIndirect](#createbrushindirect)|[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush)構造体で指定されたスタイル、色、およびパターンを使用してブラシを初期化します。|
|[CBrush:: Createdibpattern ブラシ](#createdibpatternbrush)|デバイスに依存しないビットマップ (DIB) によって指定されたパターンでブラシを初期化します。|
|[CBrush::CreateHatchBrush](#createhatchbrush)|指定したハッチパターンと色でブラシを初期化します。|
|[CBrush::CreatePatternBrush](#createpatternbrush)|ビットマップによって指定されたパターンでブラシを初期化します。|
|[CBrush:: CreateSolidBrush](#createsolidbrush)|指定した純色でブラシを初期化します。|
|[CBrush::CreateSysColorBrush](#createsyscolorbrush)|既定のシステムカラーであるブラシを作成します。|
|[CBrush:: FromHandle](#fromhandle)|`CBrush` Windows`HBRUSH`オブジェクトへのハンドルが指定された場合に、オブジェクトへのポインターを返します。|
|[CBrush::GetLogBrush](#getlogbrush)|[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush)構造体を取得します。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CBrush:: operator HBRUSH](#operator_hbrush)|`CBrush`オブジェクトにアタッチされている Windows ハンドルを返します。|

## <a name="remarks"></a>Remarks

`CBrush`オブジェクトを使用するには、 `CBrush`オブジェクトを構築し、その`CDC`オブジェクトを、ブラシを必要とする任意のメンバー関数に渡します。

ブラシには、ソリッド、ハッチ、またはパターンを使用できます。

`CBrush`の詳細については[グラフィック オブジェクト](../../mfc/graphic-objects.md)を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CGdiObject](../../mfc/reference/cgdiobject-class.md)

`CBrush`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="cbrush"></a>CBrush:: CBrush

`CBrush` オブジェクトを構築します。

```
CBrush();
CBrush(COLORREF crColor);
CBrush(int nIndex, COLORREF crColor);
explicit CBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>パラメーター

*crColor*<br/>
ブラシの前景色を RGB 色として指定します。 ブラシがハッチの場合、このパラメーターは陰影の色を指定します。

*nIndex*<br/>
ブラシのハッチスタイルを指定します。 次のいずれかの値を指定できます。

- HS_BDIAGONAL 下ハッチ (左から右) を45度で右に移動

- 水平および垂直のハッチングを HS_CROSS

- 45度の HS_DIAGCROSS のハッチング

- 45度に上方ハッチ (左から右) を HS_FDIAGONAL

- HS_HORIZONTAL 水平ハッチ

- HS_VERTICAL 垂直ハッチ

*pBitmap*<br/>
ブラシが描画`CBitmap`するビットマップを指定するオブジェクトをポイントします。

### <a name="remarks"></a>Remarks

`CBrush`には、4つのオーバーロードされたコンストラクターがあります。引数を持たないコンストラクターは、初期`CBrush`化されていないオブジェクトを構築してから使用する必要があります。

引数を指定せずにコンストラクターを`CBrush`使用する場合は、結果として得られるオブジェクトを [CreateSolidBrush](#createsolidbrush)、[CreateHatchBrush](#createhatchbrush)、[CreateBrushIndirect](#createbrushindirect)、[CreatePatternBrush](#createpatternbrush)、または [CreateDIBPatternBrush](#createdibpatternbrush) で初期化する必要があります。 引数を受け取るコンストラクターのいずれかを使用する場合、それ以上の初期化は必要ありません。 引数を持つコンストラクターは、エラーが発生した場合は例外をスローできますが、引数を持たないコンストラクターは常に成功します。

1つの[COLORREF](/windows/win32/gdi/colorref)パラメーターを持つコンストラクターは、指定された色でソリッドブラシを構築します。 色は RGB 値を指定し、WINDOWS の RGB マクロを使用して作成できます。始め.

2つのパラメーターを持つコンストラクターは、ハッチブラシを構築します。 *NIndex*パラメーターは、ハッチパターンのインデックスを指定します。 *CrColor*パラメーターは、色を指定します。

パラメーターを`CBitmap`持つコンストラクターは、パターン化されたブラシを構築します。 パラメーターはビットマップを識別します。 ビットマップは、 [CBitmap:: CreateBitmap](../../mfc/reference/cbitmap-class.md#createbitmap)、 [CBitmap:: createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)、 [CBitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)、または[CBitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)を使用して作成されたものと見なされます。 塗りつぶしパターンで使用するビットマップの最小サイズは8ピクセル x 8 ピクセルです。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#21](../../mfc/codesnippet/cpp/cbrush-class_1.cpp)]

##  <a name="createbrushindirect"></a>CBrush:: CreateBrushIndirect

[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush)構造体で指定されたスタイル、色、およびパターンを使用してブラシを初期化します。

```
BOOL CreateBrushIndirect(const LOGBRUSH* lpLogBrush);
```

### <a name="parameters"></a>パラメーター

*lpLogBrush*<br/>
ブラシに関する情報を格納している[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush)構造体を指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このブラシは、その後、任意のデバイスコンテキストの現在のブラシとして選択できます。

モノクロ (1 平面、1ビット/ピクセル) ビットマップを使用して作成されたブラシは、現在のテキストと背景色を使用して描画されます。 0に設定されたビットによって表されるピクセルは、現在のテキストの色で描画されます。 1に設定されたビットによって表されるピクセルは、現在の背景色で描画されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#22](../../mfc/codesnippet/cpp/cbrush-class_2.cpp)]

##  <a name="createdibpatternbrush"></a>  CBrush::CreateDIBPatternBrush

デバイスに依存しないビットマップ (DIB) によって指定されたパターンでブラシを初期化します。

```
BOOL CreateDIBPatternBrush(
    HGLOBAL hPackedDIB,
    UINT nUsage);

BOOL CreateDIBPatternBrush(
    const void* lpPackedDIB,
    UINT nUsage);
```

### <a name="parameters"></a>パラメーター

*hPackedDIB*<br/>
圧縮デバイスに依存しないビットマップ (DIB) を含むグローバルメモリオブジェクトを識別します。

*nUsage*<br/>
[BITMAPINFO](/windows/win32/api/wingdi/ns-wingdi-bitmapinfo) データ構造`bmiColors[]` ("パックされた DIB" の一部) のフィールドに、現在認識されている論理パレットへの明示的な RGB 値またはインデックスが含まれるかどうかを指定します。 パラメーターには、次のいずれかの値を指定する必要があります。

- DIB_PAL_COLORS カラーテーブルは、16ビットのインデックスの配列で構成されています。

- DIB_RGB_COLORS color テーブルには、リテラルの RGB 値が含まれています。

*lpPackedDIB*<br/>
`BITMAPINFO`構造体の直後にビットマップのピクセルを定義するバイト配列で構成される、パックされた DIB を指します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

その後、ラスター操作をサポートする任意のデバイスコンテキストに対して、ブラシを選択できます。

次の2つのバージョンは、DIB の処理方法が異なります。

- 最初のバージョンでは、DIB へのハンドルを取得するために、 `GlobalAlloc` Windows の関数を呼び出してグローバルメモリのブロックを割り当ててから、メモリにパックされた DIB を格納します。

- 2番目のバージョンでは、を呼び出し`GlobalAlloc`て、パックされた DIB にメモリを割り当てる必要はありません。

パックされた DIB は`BITMAPINFO` 、データ構造の直後に、ビットマップのピクセルを定義するバイト配列で構成されます。 塗りつぶしパターンとして使用されるビットマップは8ピクセル x 8 ピクセルである必要があります。 ビットマップが大きい場合、Windows は、ビットマップの左上隅にある最初の8行と8列のピクセルに対応するビットのみを使用して、塗りつぶしパターンを作成します。

アプリケーションが2色の DIB パターンブラシをモノクロデバイスコンテキストに選択すると、DIB に指定されている色が無視され、代わりに、デバイスコンテキストの現在のテキストと背景色を使用してパターンブラシが表示されます。 DIB の最初の色 (DIB カラーテーブルのオフセット 0) にマップされたピクセルは、テキストの色を使用して表示されます。 2番目の色にマップされたピクセル (カラーテーブルのオフセット 1) は、背景色を使用して表示されます。

次の Windows 関数の使用方法の詳細については、Windows SDK を参照してください。

- [Createdibpattern ブラシ](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrush)(この関数は、 `CreateDIBPatternBrushPt` 3.0 より前のバージョンの Windows 用に記述されたアプリケーションとの互換性のためだけに用意されています。関数を使用してください)。

- [CreateDIBPatternBrushPt](/windows/win32/api/wingdi/nf-wingdi-createdibpatternbrushpt)(この関数は、Win32 ベースのアプリケーションで使用する必要があります)。

- [GlobalAlloc](/windows/win32/api/winbase/nf-winbase-globalalloc)

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#23](../../mfc/codesnippet/cpp/cbrush-class_3.cpp)]

##  <a name="createhatchbrush"></a>  CBrush::CreateHatchBrush

指定したハッチパターンと色でブラシを初期化します。

```
BOOL CreateHatchBrush(
    int nIndex,
    COLORREF crColor);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
ブラシのハッチスタイルを指定します。 次のいずれかの値を指定できます。

- HS_BDIAGONAL 下ハッチ (左から右) を45度で右に移動

- 水平および垂直のハッチングを HS_CROSS

- 45度の HS_DIAGCROSS のハッチング

- 45度に上方ハッチ (左から右) を HS_FDIAGONAL

- HS_HORIZONTAL 水平ハッチ

- HS_VERTICAL 垂直ハッチ

*crColor*<br/>
ブラシの前景色を RGB 色 (陰影の色) として指定します。 詳細については、Windows SDK の「 [COLORREF](/windows/win32/gdi/colorref) 」を参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このブラシは、その後、任意のデバイスコンテキストの現在のブラシとして選択できます。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#24](../../mfc/codesnippet/cpp/cbrush-class_4.cpp)]

##  <a name="createpatternbrush"></a>  CBrush::CreatePatternBrush

ビットマップによって指定されたパターンでブラシを初期化します。

```
BOOL CreatePatternBrush(CBitmap* pBitmap);
```

### <a name="parameters"></a>パラメーター

*pBitmap*<br/>
ビットマップを識別します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

その後、ラスター操作をサポートする任意のデバイスコンテキストに対して、ブラシを選択できます。 *Pbitmap*によって識別されるビットマップは、通常、 [CBitmap:: createbitmap](../../mfc/reference/cbitmap-class.md#createbitmap)、 [CBitmap:: Createbitmapindirect](../../mfc/reference/cbitmap-class.md#createbitmapindirect)、 [CBitmap:: Loadbitmap](../../mfc/reference/cbitmap-class.md#loadbitmap)、または[CBitmap:: CreateCompatibleBitmap](../../mfc/reference/cbitmap-class.md#createcompatiblebitmap)関数を使用して初期化されます。

塗りつぶしパターンとして使用されるビットマップは8ピクセル x 8 ピクセルである必要があります。 ビットマップが大きい場合、Windows では、ビットマップの左上隅にある最初の8行とピクセルの列に対応するビットのみが使用されます。

パターンブラシは、関連付けられているビットマップに影響を与えずに削除できます。 これは、ビットマップを使用して任意の数のパターンブラシを作成できることを意味します。

モノクロビットマップを使用して作成されたブラシ (1 つのカラープレーン、1ピクセルあたり1ビット) は、現在のテキストと背景色を使用して描画されます。 0に設定されたビットによって表されるピクセルは、現在のテキストの色で描画されます。 1に設定されたビットによって表されるピクセルは、現在の背景色で描画されます。

Windows 関数の[Createpattern ブラシ](/windows/win32/api/wingdi/nf-wingdi-createpatternbrush)の使用方法の詳細については、「Windows SDK」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#25](../../mfc/codesnippet/cpp/cbrush-class_5.cpp)]

##  <a name="createsolidbrush"></a>CBrush:: CreateSolidBrush

指定した純色でブラシを初期化します。

```
BOOL CreateSolidBrush(COLORREF crColor);
```

### <a name="parameters"></a>パラメーター

*crColor*<br/>
ブラシの色を指定する[COLORREF](/windows/win32/gdi/colorref)構造体。 色は RGB 値を指定し、WINDOWS の RGB マクロを使用して作成できます。始め.

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このブラシは、その後、任意のデバイスコンテキストの現在のブラシとして選択できます。

によっ`CreateSolidBrush`て作成されたブラシを使用してアプリケーションが終了したら、デバイスコンテキストからブラシを選択する必要があります。

### <a name="example"></a>例

  [Cbrush:: cbrush](#cbrush)の例を参照してください。

##  <a name="createsyscolorbrush"></a>  CBrush::CreateSysColorBrush

ブラシの色を初期化します。

```
BOOL CreateSysColorBrush(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
色のインデックスを指定します。 この値は、21のウィンドウ要素のいずれかの塗りつぶしに使用される色に対応します。 値の一覧については、Windows SDK の[Getsyscolor](/windows/win32/api/winuser/nf-winuser-getsyscolor)を参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このブラシは、その後、任意のデバイスコンテキストの現在のブラシとして選択できます。

によっ`CreateSysColorBrush`て作成されたブラシを使用してアプリケーションが終了したら、デバイスコンテキストからブラシを選択する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#26](../../mfc/codesnippet/cpp/cbrush-class_6.cpp)]

##  <a name="fromhandle"></a>CBrush:: FromHandle

Windows [hbrush](#operator_hbrush)オブジェクトへ`CBrush`のハンドルが指定された場合に、オブジェクトへのポインターを返します。

```
static CBrush* PASCAL FromHandle(HBRUSH hBrush);
```

### <a name="parameters"></a>パラメーター

*hBrush*<br/>
Windows GDI ブラシを処理します。

### <a name="return-value"></a>戻り値

成功した場合`CBrush`はオブジェクトへのポインター、それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

オブジェクトがハンドルにまだアタッチされていない場合は`CBrush` 、一時オブジェクトが作成され、アタッチされます。 `CBrush` この一時`CBrush`オブジェクトは、アプリケーションが次にそのイベントループ内でアイドル状態になるまで有効です。 この時点で、すべての一時グラフィックオブジェクトが削除されます。 つまり、一時オブジェクトは、1つのウィンドウメッセージの処理中にのみ有効です。

グラフィックオブジェクトの使用方法の詳細については、「Windows SDK の[グラフィックオブジェクト](/windows/win32/gdi/graphic-objects)」を参照してください。

### <a name="example"></a>例

  [Cbrush:: cbrush](#cbrush)の例を参照してください。

##  <a name="getlogbrush"></a>  CBrush::GetLogBrush

このメンバー関数を呼び出して、 `LOGBRUSH`構造体を取得します。

```
int GetLogBrush(LOGBRUSH* pLogBrush);
```

### <a name="parameters"></a>パラメーター

*pLogBrush*<br/>
ブラシに関する情報を格納している[Logbrush](/windows/win32/api/wingdi/ns-wingdi-logbrush)構造体を指します。

### <a name="return-value"></a>戻り値

関数が成功し、 *pLogBrush*が有効なポインターの場合、戻り値はバッファーに格納されているバイト数です。

関数が成功し、 *pLogBrush*が NULL の場合、戻り値は、関数がバッファーに格納する情報を保持するために必要なバイト数になります。

関数が失敗した場合、戻り値は0になります。

### <a name="remarks"></a>Remarks

構造`LOGBRUSH`体は、ブラシのスタイル、色、およびパターンを定義します。

たとえば、ビットマップの`GetLogBrush`特定の色またはパターンに一致するを呼び出します。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#27](../../mfc/codesnippet/cpp/cbrush-class_7.cpp)]

##  <a name="operator_hbrush"></a>CBrush:: operator HBRUSH

`CBrush`オブジェクトのアタッチされた Windows GDI ハンドルを取得するには、この演算子を使用します。

```
operator HBRUSH() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、 `CBrush`オブジェクトによって表される Windows GDI オブジェクトへのハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

この演算子は、HBRUSH オブジェクトの直接使用をサポートするキャスト演算子です。

グラフィックオブジェクトの使用方法の詳細については、「Windows SDK の[グラフィックオブジェクト](/windows/win32/gdi/graphic-objects)」を参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#28](../../mfc/codesnippet/cpp/cbrush-class_8.cpp)]

## <a name="see-also"></a>関連項目

[MFC のサンプル PROPDLG](../../overview/visual-cpp-samples.md)<br/>
[CGdiObject クラス](../../mfc/reference/cgdiobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CBitmap クラス](../../mfc/reference/cbitmap-class.md)<br/>
[CDC クラス](../../mfc/reference/cdc-class.md)
