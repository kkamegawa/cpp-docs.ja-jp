---
title: CImage クラス
ms.date: 08/19/2019
f1_keywords:
- CImage
- ATLIMAGE/ATL::CImage
- ATLIMAGE/ATL::CImage::CImage
- ATLIMAGE/ATL::CImage::AlphaBlend
- ATLIMAGE/ATL::CImage::Attach
- ATLIMAGE/ATL::CImage::BitBlt
- ATLIMAGE/ATL::CImage::Create
- ATLIMAGE/ATL::CImage::CreateEx
- ATLIMAGE/ATL::CImage::Destroy
- ATLIMAGE/ATL::CImage::Detach
- ATLIMAGE/ATL::CImage::Draw
- ATLIMAGE/ATL::CImage::GetBits
- ATLIMAGE/ATL::CImage::GetBPP
- ATLIMAGE/ATL::CImage::GetColorTable
- ATLIMAGE/ATL::CImage::GetDC
- ATLIMAGE/ATL::CImage::GetExporterFilterString
- ATLIMAGE/ATL::CImage::GetHeight
- ATLIMAGE/ATL::CImage::GetImporterFilterString
- ATLIMAGE/ATL::CImage::GetMaxColorTableEntries
- ATLIMAGE/ATL::CImage::GetPitch
- ATLIMAGE/ATL::CImage::GetPixel
- ATLIMAGE/ATL::CImage::GetPixelAddress
- ATLIMAGE/ATL::CImage::GetTransparentColor
- ATLIMAGE/ATL::CImage::GetWidth
- ATLIMAGE/ATL::CImage::IsDIBSection
- ATLIMAGE/ATL::CImage::IsIndexed
- ATLIMAGE/ATL::CImage::IsNull
- ATLIMAGE/ATL::CImage::IsTransparencySupported
- ATLIMAGE/ATL::CImage::Load
- ATLIMAGE/ATL::CImage::LoadFromResource
- ATLIMAGE/ATL::CImage::MaskBlt
- ATLIMAGE/ATL::CImage::PlgBlt
- ATLIMAGE/ATL::CImage::ReleaseDC
- ATLIMAGE/ATL::CImage::ReleaseGDIPlus
- ATLIMAGE/ATL::CImage::Save
- ATLIMAGE/ATL::CImage::SetColorTable
- ATLIMAGE/ATL::CImage::SetPixel
- ATLIMAGE/ATL::CImage::SetPixelIndexed
- ATLIMAGE/ATL::CImage::SetPixelRGB
- ATLIMAGE/ATL::CImage::SetTransparentColor
- ATLIMAGE/ATL::CImage::StretchBlt
- ATLIMAGE/ATL::CImage::TransparentBlt
helpviewer_keywords:
- jpeg files
- bitmaps [C++], ATL and MFC support for
- images [C++], ATL and MFC support for
- gif files, ATL and MFC support
- .gif files, ATL and MFC support
- PNG files, ATL and MFC support
- CImage class
- transparent color
ms.assetid: 52861e3d-bf7e-481f-a240-90e88f76c490
ms.openlocfilehash: 3b278f37bbcbe2ee879d9c3d2837267fe31e57e2
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/20/2019
ms.locfileid: "69630713"
---
# <a name="cimage-class"></a>CImage クラス

`CImage`では、JPEG、GIF、BMP、およびポータブルネットワークグラフィックス (PNG) 形式のイメージを読み込んで保存する機能など、ビットマップのサポートが強化されています。

> [!IMPORTANT]
> このクラスとそのメンバーは、Windows ランタイムで実行されるアプリケーションでは使用できません。

## <a name="syntax"></a>構文

```
class CImage
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CImage::CImage](#cimage)|コンストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CImage::AlphaBlend](#alphablend)|透明または半透明のピクセルを持つビットマップを表示します。|
|[CImage::Attach](#attach)|HBITMAP を`CImage`オブジェクトにアタッチします。 DIB 以外のセクションビットマップまたは DIB セクションビットマップと共に使用できます。|
|[CImage::BitBlt](#bitblt)|ソースデバイスコンテキストからこの現在のデバイスコンテキストにビットマップをコピーします。|
|[CImage::Create](#create)|DIB セクションビットマップを作成し、それを以前に構築`CImage`されたオブジェクトにアタッチします。|
|[CImage::CreateEx](#createex)|追加のパラメーターを使用して DIB セクションビットマップを作成し、それを以前`CImage`に構築されたオブジェクトにアタッチします。|
|[CImage::Destroy](#destroy)|ビットマップを`CImage`オブジェクトからデタッチし、ビットマップを破棄します。|
|[CImage::Detach](#detach)|ビットマップを`CImage`オブジェクトからデタッチします。|
|[CImage::Draw](#draw)|コピー元の四角形からコピー先の四角形にビットマップをコピーします。 `Draw`必要に応じて、コピー先の四角形の大きさに合わせてビットマップを拡大または縮小し、アルファブレンドと透明色を処理します。|
|[CImage::GetBits](#getbits)|ビットマップの実際のピクセル値へのポインターを取得します。|
|[CImage::GetBPP](#getbpp)|ピクセルあたりのビット数を取得します。|
|[CImage::GetColorTable](#getcolortable)|色テーブルのエントリの範囲から赤、緑、青 (RGB) の色の値を取得します。|
|[CImage::GetDC](#getdc)|現在のビットマップが選択されているデバイスコンテキストを取得します。|
|[CImage::GetExporterFilterString](#getexporterfilterstring)|使用可能なイメージ形式とその説明を検索します。|
|[CImage::GetHeight](#getheight)|現在のイメージの高さ (ピクセル単位) を取得します。|
|[CImage::GetImporterFilterString](#getimporterfilterstring)|使用可能なイメージ形式とその説明を検索します。|
|[CImage::GetMaxColorTableEntries](#getmaxcolortableentries)|カラーテーブル内のエントリの最大数を取得します。|
|[CImage::GetPitch](#getpitch)|現在のイメージのピッチ (バイト単位) を取得します。|
|[CImage::GetPixel](#getpixel)|*X*および*y*によって指定されたピクセルの色を取得します。|
|[CImage::GetPixelAddress](#getpixeladdress)|指定されたピクセルのアドレスを取得します。|
|[CImage::GetTransparentColor](#gettransparentcolor)|カラーテーブル内の透明色の位置を取得します。|
|[CImage::GetWidth](#getwidth)|現在のイメージの幅 (ピクセル単位) を取得します。|
|[CImage::IsDIBSection](#isdibsection)|添付ビットマップが DIB セクションかどうかを判断します。|
|[CImage::IsIndexed](#isindexed)|ビットマップの色がインデックス付きパレットにマップされることを示します。|
|[CImage::IsNull](#isnull)|ソースビットマップが現在読み込まれているかどうかを示します。|
|[CImage::IsTransparencySupported](#istransparencysupported)|アプリケーションが透明なビットマップをサポートするかどうかを示します。|
|[CImage::Load](#load)|指定されたファイルからイメージを読み込みます。|
|[CImage::LoadFromResource](#loadfromresource)|指定したリソースからイメージを読み込みます。|
|[CImage::MaskBlt](#maskblt)|指定したマスクおよびラスター操作を使用して、コピー元とコピー先のビットマップのカラーデータを結合します。|
|[CImage::PlgBlt](#plgblt)|ソースデバイスコンテキストの四角形から、変換先デバイスコンテキストの平行四辺形へのビットブロック転送を実行します。|
|[CImage::ReleaseDC](#releasedc)|[CImage:: GetDC](#getdc)を使用して取得されたデバイスコンテキストを解放します。|
|[CImage::ReleaseGDIPlus](#releasegdiplus)|GDI + によって使用されるリソースを解放します。 グローバル`CImage`オブジェクトによって作成されたリソースを解放するには、を呼び出す必要があります。|
|[CImage::Save](#save)|指定した種類のイメージを保存します。 `Save`イメージオプションを指定することはできません。|
|[CImage::SetColorTable](#setcolortable)|DIB セクションの色テーブルのエントリ範囲に、赤、緑、青の RGB) の色の値を設定します。|
|[CImage::SetPixel](#setpixel)|指定した座標にあるピクセルを、指定した色に設定します。|
|[CImage::SetPixelIndexed](#setpixelindexed)|指定した座標にあるピクセルを、パレットの指定したインデックス位置の色に設定します。|
|[CImage::SetPixelRGB](#setpixelrgb)|指定した座標にあるピクセルを、指定した赤、緑、青 (RGB) の値に設定します。|
|[CImage::SetTransparentColor](#settransparentcolor)|透明として扱う色のインデックスを設定します。 透明にできるのは、パレット内の1色だけです。|
|[CImage::StretchBlt](#stretchblt)|コピー元の四角形からコピー先の四角形にビットマップをコピーし、必要に応じて、コピー先の四角形のサイズに合うようにビットマップを拡大または縮小します。|
|[CImage::TransparentBlt](#transparentblt)|ソースデバイスコンテキストからこの現在のデバイスコンテキストに透明色のビットマップをコピーします。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CImage:: operator HBITMAP](#operator_hbitmap)|`CImage`オブジェクトにアタッチされている Windows ハンドルを返します。|

## <a name="remarks"></a>Remarks

`CImage`デバイスに依存しないビットマップ (DIB) のセクションであるかどうかを問わず、ビットマップを取得します。ただし、DIB セクションだけを使用して、 [Create](#create)または[CImage:: Load](#load)を使用できます。 `CImage` [Attach](#attach)を使用してオブジェクトに dib 以外のセクションビットマップをアタッチすることはできますが、次`CImage`のメソッドは使用できません。これらのメソッドでは、dib セクションビットマップのみがサポートされます。

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

添付されたビットマップが DIB セクションであるかどうかを確認するには、 [IsDibSection](#isdibsection)を呼び出します。

> [!NOTE]
> Visual Studio .net 2003 では、このクラスは作成された`CImage`オブジェクト数のカウントを保持します。 カウントが0になると、gdi + `GdiplusShutdown`によって使用されるリソースを解放するために、関数が自動的に呼び出されます。 これにより`CImage` 、dll によって直接または間接的に作成されたオブジェクトは常`DllMain`に正常に破棄され`GdiplusShutdown` 、からは呼び出されません。

> [!NOTE]
> DLL で`CImage`グローバルオブジェクトを使用することはお勧めできません。 DLL でグローバル`CImage`オブジェクトを使用する必要がある場合は、 [CImage:: ReleaseGDIPlus](#releasegdiplus)を呼び出して、gdi + によって使用されるリソースを明示的に解放します。

`CImage`を新しい[CDC](../../mfc/reference/cdc-class.md)に選択することはできません。 `CImage`イメージの固有の HDC を作成します。 HBITMAP は一度に1つの hdc にしか選択できないため、に関連付けら`CImage`れている HBITMAP を別の hdc に選択することはできません。 Cdc が必要な場合は、 `CImage`から HDC を取得し、 [cdc:: FromHandle](../../mfc/reference/cdc-class.md#fromhandle)に渡します。

## <a name="example"></a>例

```cpp
// Get a CDC for the image
CDC* pDC = CDC::FromHandle(m_myImage.GetDC());

// Use pDC here
pDC->Rectangle(0, 40, 100, 50);
m_myImage.ReleaseDC();
```

MFC プロジェクトで`CImage`を使用する場合は、プロジェクト内のどのメンバー関数が[CBitmap](../../mfc/reference/cbitmap-class.md)オブジェクトへのポインターを必要とするかを確認してください。 このような関数と`CImage`共にを使用する場合は ( [CMenu:: appendmenu](../../mfc/reference/cmenu-class.md#appendmenu)など)、 `CImage` [CBitmap:: FromHandle](../../mfc/reference/cbitmap-class.md#fromhandle)を使用し、HBITMAP に渡し`CBitmap*`、返されたを使用します。

## <a name="example"></a>例

```cpp
void CMyDlg::OnRButtonDown(UINT nFlags, CPoint point)
{
    UNREFERENCED_PARAMETER(nFlags);

    CBitmap* pBitmap = CBitmap::FromHandle(m_myImage);
    m_pmenuPop->AppendMenu(0, ID_BMPCOMMAND, pBitmap);
    ClientToScreen(&point);
    m_pmenuPop->TrackPopupMenu(TPM_RIGHTBUTTON | TPM_LEFTALIGN, point.x,
    point.y, this);
}
```

で`CImage`は、DIB セクションの実際のビットにアクセスできます。 以前に Win32 HBITMAP `CImage`または DIB セクションを使用した場所であればどこでもオブジェクトを使用できます。

は、MFC `CImage`または ATL から使用できます。

> [!NOTE]
> を使用して`CImage`プロジェクトを作成する場合は、 *atlimage*を含める前にを定義`CString`する必要があります。 プロジェクトで MFC を使用せずに ATL を使用する場合は、 *atlimage*を含める前に*atlstr. h*を含めます。 プロジェクトで MFC を使用している場合 (または、MFC がサポートされている ATL プロジェクトの場合) は、 *atlimage*を含める前に*afxstr*を含めてください。<br/>
> <br/>
> 同様に、 *atlimpl .cpp*を含める前に*atlimage*を含める必要があります。 これを簡単に行うには、atlimage (Visual Studio 2017 以前の*stdafx.h* ) にを含めます。

## <a name="requirements"></a>必要条件

**ヘッダー:** atlimage

##  <a name="alphablend"></a>CImage:: AlphaBlend

透明または半透明のピクセルを持つビットマップを表示します。

```
BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    const POINT& pointDest,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER) const throw();

BOOL AlphaBlend(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);

BOOL AlphaBlend(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    BYTE bSrcAlpha = 0xff,
    BYTE bBlendOp = AC_SRC_OVER);
```

### <a name="parameters"></a>パラメーター

*hDestDC*<br/>
宛先デバイスコンテキストを処理します。

*xDest*<br/>
コピー先の四角形の左上隅の x 座標 (論理単位)。

*yDest*<br/>
コピー先の四角形の左上隅の y 座標 (論理単位)。

*bSrcAlpha*<br/>
ソースビットマップ全体で使用されるアルファ透明度値。 既定値 0xff (255) は、イメージが不透明であること、およびピクセル単位のアルファ値のみを使用することを前提としています。

*bBlendOp*<br/>
コピー元とコピー先のビットマップのアルファブレンド関数、ソースビットマップ全体に適用されるグローバルアルファ値、およびソースビットマップの書式情報。 現在、変換元と変換先の blend 関数は AC_SRC_OVER に制限されています。

*pointDest*<br/>
コピー先の四角形の左上隅 (論理単位) を識別する[ポイント](/previous-versions/dd162805\(v=vs.85\))構造への参照。

*nDestWidth*<br/>
コピー先の四角形の幅 (論理単位)。

*nDestHeight*<br/>
コピー先の四角形の高さ (論理単位)。

*xSrc*<br/>
ソース四角形の左上隅の論理 x 座標。

*ySrc*<br/>
ソース四角形の左上隅の論理 y 座標。

*nSrcWidth*<br/>
コピー元の四角形の幅 (論理単位)。

*Nsr、*<br/>
コピー元の四角形の高さ (論理単位)。

*rectDest*<br/>
ターゲットを識別する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*rectSrc*<br/>
ソースを識別する`RECT`構造体への参照。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

アルファブレンドビットマップでは、ピクセル単位での色のブレンドがサポートされます。

*Bblendop*が既定値の AC_SRC_OVER に設定されている場合、ソースビットマップは、ソースピクセルのアルファ値に基づいて、コピー先ビットマップに配置されます。

##  <a name="attach"></a>CImage:: Attach

*HBitmap*を`CImage`オブジェクトにアタッチします。

```
void Attach(HBITMAP hBitmap, DIBOrientation eOrientation = DIBOR_DEFAULT) throw();
```

### <a name="parameters"></a>パラメーター

*hBitmap*<br/>
HBITMAP を処理するハンドル。

*eOrientation*<br/>
ビットマップの向きを指定します。 次のいずれかの値を指定します。

- DIBOR_DEFAULT ビットマップの向きは、オペレーティングシステムによって決まります。

- DIBOR_BOTTOMUP ビットマップの行は逆順になっています。 これにより、 [cimage:: GetBits](#getbits)がビットマップバッファーの末尾付近にポインターを返し、 [Cimage:: getbits](#getpitch)が負の数を返すようになります。

- DIBOR_TOPDOWN ビットマップの行は、上から下の順に並んでいます。 これにより、 [cimage:: GetBits](#getbits)はビットマップバッファーの最初のバイトへのポインターを返し、 [Cimage:: getbits](#getpitch)は正の数値を返すようにします。

### <a name="remarks"></a>Remarks

ビットマップは、DIB 以外のセクションビットマップまたは DIB セクションビットマップにすることができます。 DIB セクションビットマップでのみ使用できるメソッドの一覧については、「 [IsDIBSection](#isdibsection) 」を参照してください。

##  <a name="bitblt"></a>CImage:: BitBlt

ソースデバイスコンテキストからこの現在のデバイスコンテキストにビットマップをコピーします。

```
BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const POINT& pointDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    DWORD dwROP = SRCCOPY) const throw();

BOOL BitBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>パラメーター

*hDestDC*<br/>
コピー先の HDC。

*xDest*<br/>
コピー先の四角形の左上隅の論理 x 座標。

*yDest*<br/>
コピー先の四角形の左上隅の論理 y 座標。

*dwROP*<br/>
実行するラスター操作。 ラスター操作コードでは、変換元、変換先、および (現在選択されているブラシで定義されている) パターンのビットを組み合わせることによって、変換先を形成する方法を正確に定義します。 その他のラスター操作コードとその説明の一覧については、Windows SDK の「 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 」を参照してください。

*pointDest*<br/>
コピー先の四角形の左上隅を示す[ポイント](/previous-versions/dd162805\(v=vs.85\))構造体。

*nDestWidth*<br/>
コピー先の四角形の幅 (論理単位)。

*nDestHeight*<br/>
コピー先の四角形の高さ (論理単位)。

*xSrc*<br/>
ソース四角形の左上隅の論理 x 座標。

*ySrc*<br/>
ソース四角形の左上隅の論理 y 座標。

*rectDest*<br/>
コピー先の四角形を示す[RECT](/previous-versions/dd162897\(v=vs.85\))構造体。

*pointSrc*<br/>
コピー元の四角形の左上隅を示す構造体。`POINT`

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 」を参照してください。

##  <a name="cimage"></a>CImage:: CImage

`CImage` オブジェクトを構築します。

```
CImage() throw();
```

### <a name="remarks"></a>Remarks

オブジェクトを構築したら、 [Create](#create)、 [Load](#load)、 [LoadFromResource](#loadfromresource)、または[attach](#attach)を呼び出して、オブジェクトにビットマップをアタッチします。

**メモ**Visual Studio では、このクラスは作成された`CImage`オブジェクト数のカウントを保持します。 カウントが0になると、gdi + `GdiplusShutdown`によって使用されるリソースを解放するために、関数が自動的に呼び出されます。 これにより`CImage` 、dll によって直接または間接的に作成され`GdiplusShutdown`たオブジェクトは常に正常に破棄され、DllMain からは呼び出されません。

DLL で`CImage`グローバルオブジェクトを使用することはお勧めできません。 DLL でグローバル`CImage`オブジェクトを使用する必要がある場合は、 [CImage:: ReleaseGDIPlus](#releasegdiplus)を呼び出して、gdi + によって使用されるリソースを明示的に解放します。

##  <a name="create"></a>  CImage::Create

ビットマップを`CImage`作成し、それを以前に構築`CImage`されたオブジェクトにアタッチします。

```
BOOL Create(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>パラメーター

*nWidth*<br/>
`CImage`ビットマップの幅 (ピクセル単位)。

*nHeight*<br/>
`CImage`ビットマップの高さ (ピクセル単位)。 *NHeight*が正の値の場合、ビットマップは下位の DIB で、その原点は左下隅になります。 *NHeight*が負の場合、ビットマップはトップダウン DIB で、原点は左上隅になります。

*nBPP*<br/>
ビットマップ内のピクセルあたりのビット数。 通常、4、8、16、24、または32。 モノクロビットマップまたはマスクの場合は1にすることができます。

*dwFlags*<br/>
ビットマップオブジェクトにアルファチャネルがあるかどうかを指定します。 には、次の値を0個以上組み合わせて指定できます。

- *createAlphaChannel* *Nbpp*が32で、 *eCompression*が BI_RGB の場合にのみ使用できます。 指定されている場合、作成されたイメージは、各ピクセルの4番目のバイトに格納され、各ピクセルのアルファ (透明度) 値を持ちます (アルファ以外の32ビットイメージでは使用されません)。 このアルファチャネルは、 [CImage:: AlphaBlend](#alphablend)を呼び出すときに自動的に使用されます。

> [!NOTE]
> [CImage の呼び出し[::D raw](#draw)] では、アルファチャネルを含むイメージは、自動的に変換先に対してアルファブレンドされます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

##  <a name="createex"></a>  CImage::CreateEx

ビットマップを`CImage`作成し、それを以前に構築`CImage`されたオブジェクトにアタッチします。

```
BOOL CreateEx(
    int nWidth,
    int nHeight,
    int nBPP,
    DWORD eCompression,
    const DWORD* pdwBitmasks = NULL,
    DWORD dwFlags = 0) throw();
```

### <a name="parameters"></a>パラメーター

*nWidth*<br/>
`CImage`ビットマップの幅 (ピクセル単位)。

*nHeight*<br/>
`CImage`ビットマップの高さ (ピクセル単位)。 *NHeight*が正の値の場合、ビットマップは下位の DIB で、その原点は左下隅になります。 *NHeight*が負の場合、ビットマップはトップダウン DIB で、原点は左上隅になります。

*nBPP*<br/>
ビットマップ内のピクセルあたりのビット数。 通常、4、8、16、24、または32。 モノクロビットマップまたはマスクの場合は1にすることができます。

*eCompression*<br/>
圧縮された下位ビットマップの圧縮の種類を指定します (上から下の Dib を圧縮することはできません)。 次のいずれかの値になります。

- BI_RGB 形式は圧縮されていません。 を呼び出すとき`CImage::CreateEx`にこの値を指定する`CImage::Create`ことは、を呼び出すことと同じです。

- BI_BITFIELDS の形式は圧縮されず、カラーテーブルは、それぞれピクセルの赤、緑、および青のコンポーネントを指定する3つの DWORD カラーマスクで構成されます。 これは、16ビットと 32 bpp のビットマップで使用する場合に有効です。

*pdwBitfields*<br/>
*ECompression*が BI_BITFIELDS に設定されている場合にのみ使用されます。それ以外の場合は、NULL にする必要があります。 3つの DWORD ビットマスクの配列へのポインター。色の赤、緑、および青のコンポーネントにそれぞれ使用されるビットを指定します。 ビットフィールドの制限については、Windows SDK の「 [Bitmapinfoheader](/previous-versions//dd183376\(v=vs.85\)) 」を参照してください。

*dwFlags*<br/>
ビットマップオブジェクトにアルファチャネルがあるかどうかを指定します。 には、次の値を0個以上組み合わせて指定できます。

- *createAlphaChannel* *Nbpp*が32で、 *eCompression*が BI_RGB の場合にのみ使用できます。 指定されている場合、作成されたイメージは、各ピクセルの4番目のバイトに格納され、各ピクセルのアルファ (透明度) 値を持ちます (アルファ以外の32ビットイメージでは使用されません)。 このアルファチャネルは、 [CImage:: AlphaBlend](#alphablend)を呼び出すときに自動的に使用されます。

   > [!NOTE]
   > [CImage の呼び出し[::D raw](#draw)] では、アルファチャネルを含むイメージは、自動的に変換先に対してアルファブレンドされます。

### <a name="return-value"></a>戻り値

成功した場合は TRUE。 それ以外の場合は FALSE。

### <a name="example"></a>例

次の例では、各ピクセルをエンコードするために16ビットを使用して、100ピクセルのビットマップを作成します。 指定された16ビットピクセルでは、ビット0-3 は赤成分、ビット4-7 エンコード緑、およびビット8-11 エンコード blue をエンコードします。 残りの4ビットは使用されません。

```cpp
DWORD adwBitmasks[3] = { 0x0000000f, 0x000000f0, 0x00000f00 };
m_myImage.CreateEx(100, 100, 16, BI_BITFIELDS, adwBitmasks, 0);
```

##  <a name="destroy"></a>CImage::D estroy

ビットマップを`CImage`オブジェクトからデタッチし、ビットマップを破棄します。

```
void Destroy() throw();
```

##  <a name="detach"></a>CImage::D します。

ビットマップを`CImage`オブジェクトからデタッチします。

```
HBITMAP Detach() throw();
```

### <a name="return-value"></a>戻り値

デタッチされたビットマップへのハンドル。ビットマップがアタッチされていない場合は NULL。

##  <a name="draw"></a>CImage::D raw

ソースデバイスコンテキストから現在のデバイスコンテキストにビットマップをコピーします。

```
BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest) const throw();

BOOL Draw(
    HDC hDestDC,
    const POINT& pointDest) const throw();

BOOL Draw(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight) const throw();

BOOL Draw(
    HDC hDestDC,
    const RECT& rectDest) const throw();
```

### <a name="parameters"></a>パラメーター

*hDestDC*<br/>
宛先デバイスコンテキストへのハンドル。

*xDest*<br/>
コピー先の四角形の左上隅の x 座標 (論理単位)。

*yDest*<br/>
コピー先の四角形の左上隅の y 座標 (論理単位)。

*nDestWidth*<br/>
コピー先の四角形の幅 (論理単位)。

*nDestHeight*<br/>
コピー先の四角形の高さ (論理単位)。

*xSrc*<br/>
コピー元の四角形の左上隅の x 座標 (論理単位)。

*ySrc*<br/>
コピー元の四角形の左上隅の y 座標 (論理単位)。

*nSrcWidth*<br/>
コピー元の四角形の幅 (論理単位)。

*Nsr、*<br/>
コピー元の四角形の高さ (論理単位)。

*rectDest*<br/>
ターゲットを識別する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*rectSrc*<br/>
ソースを識別する`RECT`構造体への参照。

*pointDest*<br/>
コピー先の四角形の左上隅 (論理単位) を識別する[ポイント](/previous-versions/dd162805\(v=vs.85\))構造への参照。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

`Draw`イメージに透明色またはアルファチャネルが含まれていない限り、 [StretchBlt](#stretchblt)と同じ操作を実行します。 この場合、は`Draw` 、必要に応じて、 [TransparentBlt](#transparentblt)または[AlphaBlend](#alphablend)のいずれかと同じ操作を実行します。

ソースの四角形`Draw`を指定していないのバージョンでは、ソースイメージ全体が既定値になります。 コピー先の四角形`Draw`のサイズが指定されていないのバージョンでは、ソースイメージのサイズが既定値であり、拡大または縮小は行われません。

##  <a name="getbits"></a>CImage:: GetBits

ビットマップ内の特定のピクセルの実際のビット値へのポインターを取得します。

```
void* GetBits() throw();
```

### <a name="return-value"></a>戻り値

ビットマップバッファーへのポインター。 ビットマップが下位の DIB の場合、ポインターはバッファーの末尾付近を指します。 ビットマップが上から下の DIB の場合、ポインターはバッファーの最初のバイトを指します。

### <a name="remarks"></a>Remarks

このポインターを[Getpitch](#getpitch)によって返される値と共に使用すると、イメージ内の個々のピクセルを見つけて変更できます。

> [!NOTE]
> このメソッドは、DIB セクションビットマップのみをサポートしています。そのため`CImage` 、DIB セクションのピクセルと同じように、オブジェクトのピクセルにアクセスします。 返されたポインターは、位置 (0, 0) のピクセルを指します。

##  <a name="getbpp"></a>  CImage::GetBPP

ピクセルあたりのビット数の値を取得します。

```
int GetBPP() const throw();
```

### <a name="return-value"></a>戻り値

ピクセルあたりのビット数。

### <a name="remarks"></a>Remarks

この値によって、各ピクセルを定義するビット数とビットマップ内の色の最大数が決まります。

ピクセルあたりのビット数は、通常、1、4、8、16、24、または32です。 この値の詳細については、Windows SDK の[bitmapinfoheader](/previous-versions//dd183376\(v=vs.85\))のメンバーを参照してください。`biBitCount`

##  <a name="getcolortable"></a>  CImage::GetColorTable

DIB セクションのパレット内のエントリの範囲から赤、緑、青 (RGB) の色の値を取得します。

```
void GetColorTable(
    UINT iFirstColor,
    UINT nColors,
    RGBQUAD* prgbColors) const throw();
```

### <a name="parameters"></a>パラメーター

*iFirstColor*<br/>
取得する最初のエントリのカラーテーブルインデックス。

*n 色*<br/>
取得するカラーテーブルエントリの数。

*prgbColors*<br/>
カラーテーブルエントリを取得する[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)構造体の配列へのポインター。

##  <a name="getdc"></a>  CImage::GetDC

現在選択されているイメージが含まれているデバイスコンテキストを取得します。

```
HDC GetDC() const throw();
```

### <a name="return-value"></a>戻り値

デバイス コンテキストを識別するハンドル。

### <a name="remarks"></a>Remarks

を`GetDC`呼び出すたびに、 [ReleaseDC](#releasedc)を呼び出す必要があります。

##  <a name="getexporterfilterstring"></a>  CImage::GetExporterFilterString

画像の保存に使用できるイメージ形式を検索します。

```
static HRESULT GetExporterFilterString(
    CSimpleString& strExporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultSave,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>パラメーター

*strExporters*<br/>
`CSimpleString` オブジェクトへの参照。 詳細については、「**解説**」を参照してください。

*aguidFileTypes*<br/>
Guid の配列。文字列内のいずれかのファイルの種類に対応する各要素が含まれます。 以下の*Pszallfilesdescription*の例では、 *aguidFileTypes*[0] は GUID_NULL で、残りの配列値は現在のオペレーティングシステムでサポートされているイメージファイル形式です。

> [!NOTE]
> 定数の完全な一覧については、「Windows SDK 内の**イメージファイル形式定数**」を参照してください。

*pszAllFilesDescription*<br/>
このパラメーターが NULL でない場合、フィルター文字列にはリストの先頭に追加のフィルターが1つ追加されます。 このフィルターには、その説明に対して*Pszallfilesdescription*の現在の値が設定されます。また、リスト内の他のエクスポーターでサポートされている任意の拡張機能のファイルを受け入れます。

例えば:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any exporter.
CImage::GetExporterFilterString(
    strExporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
一覧から除外するファイルの種類を指定するビットフラグのセット。 使用できるフラグは次のとおりです。

- `excludeGIF`= 0x01 は、GIF ファイルを除外します。

- `excludeBMP`= 0x02 は、BMP (Windows ビットマップ) ファイルを除外します。

- `excludeEMF`= 0x04 は、EMF (拡張メタファイル) ファイルを除外します。

- `excludeWMF`= 0x08 は、WMF (Windows メタファイル) ファイルを除外します。

- `excludeJPEG`= 0x10 は、JPEG ファイルを除外します。

- `excludePNG`= 0x20 は PNG ファイルを除外します。

- `excludeTIFF`= 0x40 は、TIFF ファイルを除外します。

- `excludeIcon`= 0x80 は .ICO (Windows アイコン) ファイルを除外します。

- `excludeOther`= 0x80000000 上に記載されていない他の種類のファイルは除外されます。

- `excludeDefaultLoad`= 0 の場合、既定ではすべてのファイルの種類が含まれます。

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`保存する場合、これらのファイルは通常、特別な要件を持つため、既定では除外されます。

*chSeparator*<br/>
イメージ形式の間で使用される区切り記号。 詳細については、「**解説**」を参照してください。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

生成された書式指定文字列を MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)オブジェクトに渡すことで、[ファイル名を付けて保存] ダイアログボックスで使用可能なイメージ形式のファイル拡張子を公開できます。

パラメーター *strExporter*の形式は次のとおりです。

ファイル description0&#124;\*. ext0&#124;&#124;filedescription1\*...&#124;ファイルの説明*n*&#124;\*. ext *n*&#124;&#124;

ここで&#124;、' ' はで`chSeparator`指定された区切り記号です。 例えば:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

この文字列を MFC&#124; `CFileDialog`オブジェクトに渡す場合は、既定の区切り記号 ' ' を使用します。 共通の [ファイルの保存] ダイアログボックスにこの文字列を渡す場合は、null 区切り文字 ' \ 0 ' を使用します。

##  <a name="getheight"></a>  CImage::GetHeight

イメージの高さ (ピクセル単位) を取得します。

```
int GetHeight() const throw();
```

### <a name="return-value"></a>戻り値

イメージの高さ (ピクセル単位)。

##  <a name="getimporterfilterstring"></a>  CImage::GetImporterFilterString

イメージの読み込みに使用できるイメージ形式を検索します。

```
static HRESULT GetImporterFilterString(
    CSimpleString& strImporters,
    CSimpleArray<GUID>& aguidFileTypes,
    LPCTSTR pszAllFilesDescription = NULL,
    DWORD dwExclude = excludeDefaultLoad,
    TCHAR chSeparator = _T('|'));
```

### <a name="parameters"></a>パラメーター

*strImporters*<br/>
`CSimpleString` オブジェクトへの参照。 詳細については、「**解説**」を参照してください。

*aguidFileTypes*<br/>
Guid の配列。文字列内のいずれかのファイルの種類に対応する各要素が含まれます。 以下の*Pszallfilesdescription*の例では、 *aguidFileTypes*[0] は GUID_NULL で、残りの配列値は、現在のオペレーティングシステムでサポートされているイメージファイル形式です。

> [!NOTE]
> 定数の完全な一覧については、「Windows SDK 内の**イメージファイル形式定数**」を参照してください。

*pszAllFilesDescription*<br/>
このパラメーターが NULL でない場合、フィルター文字列にはリストの先頭に追加のフィルターが1つ追加されます。 このフィルターには、その説明に対して*Pszallfilesdescription*の現在の値が設定されます。また、リスト内の他のエクスポーターでサポートされている任意の拡張機能のファイルを受け入れます。

例えば:

```cpp
//First filter in the list will be titled "All Image Files", and
//will accept files with any extension supported by any importer.
CImage::GetImporterFilterString(
    strImporters, aguidFileTypes,
_T("All Image Files"));
```

*dwExclude*<br/>
一覧から除外するファイルの種類を指定するビットフラグのセット。 使用できるフラグは次のとおりです。

- `excludeGIF`= 0x01 は、GIF ファイルを除外します。

- `excludeBMP`= 0x02 は、BMP (Windows ビットマップ) ファイルを除外します。

- `excludeEMF`= 0x04 は、EMF (拡張メタファイル) ファイルを除外します。

- `excludeWMF`= 0x08 は、WMF (Windows メタファイル) ファイルを除外します。

- `excludeJPEG`= 0x10 は、JPEG ファイルを除外します。

- `excludePNG`= 0x20 は PNG ファイルを除外します。

- `excludeTIFF`= 0x40 は、TIFF ファイルを除外します。

- `excludeIcon`= 0x80 は .ICO (Windows アイコン) ファイルを除外します。

- `excludeOther`= 0x80000000 上に記載されていない他の種類のファイルは除外されます。

- `excludeDefaultLoad`= 0 の場合、既定ではすべてのファイルの種類が含まれます。

- `excludeDefaultSave` = `excludeIcon &#124; excludeEMF &#124; excludeWMF`保存する場合、これらのファイルは通常、特別な要件を持つため、既定では除外されます。

*chSeparator*<br/>
イメージ形式の間で使用される区切り記号。 詳細については、「**解説**」を参照してください。

### <a name="remarks"></a>Remarks

生成された書式指定文字列を MFC [CFileDialog](../../mfc/reference/cfiledialog-class.md)オブジェクトに渡すことで、 **[ファイルを開く]** ダイアログボックスで使用可能なイメージ形式のファイル拡張子を公開できます。

パラメーター *strImporter*の形式は次のとおりです。

ファイル description0&#124;\*. ext0&#124;&#124;filedescription1\*...&#124;ファイルの説明*n*&#124;\*. ext *n*&#124;&#124;

ここで&#124;、' ' は*chseparator*によって指定された区切り記号です。 例えば:

`"Bitmap format|*.bmp|JPEG format|*.jpg|GIF format|*.gif|PNG format|*.png||"`

この文字列を MFC&#124; `CFileDialog`オブジェクトに渡す場合は、既定の区切り記号 ' ' を使用します。 一般的な **[ファイルを開く**] ダイアログボックスにこの文字列を渡す場合は、null 区切り文字 ' \ 0 ' を使用します。

##  <a name="getmaxcolortableentries"></a>  CImage::GetMaxColorTableEntries

カラーテーブル内のエントリの最大数を取得します。

```
int GetMaxColorTableEntries() const throw();
```

### <a name="return-value"></a>戻り値

カラーテーブル内のエントリの数。

### <a name="remarks"></a>Remarks

このメソッドは、DIB セクションビットマップだけをサポートします。

##  <a name="getpitch"></a>CImage:: GetPitch

イメージのピッチを取得します。

```
int GetPitch() const throw();
```

### <a name="return-value"></a>戻り値

イメージのピッチ。 戻り値が負の場合、ビットマップは下位の DIB で、その原点は左下隅になります。 戻り値が正の場合、ビットマップはトップダウン DIB で、原点は左上隅になります。

### <a name="remarks"></a>Remarks

ピッチは、1つのビットマップ線の先頭と次のビットマップ線の先頭を表す2つのメモリアドレス間の距離 (バイト単位) です。 ピッチはバイト単位で測定されるため、イメージのピッチはピクセル形式を決定するのに役立ちます。 ピッチには、ビットマップ用に予約されている追加のメモリを含めることもできます。

イメージ`GetPitch`の個々のピクセルを検索するには、 [getbits](#getbits)と共に使用します。

> [!NOTE]
> このメソッドは、DIB セクションビットマップだけをサポートします。

##  <a name="getpixel"></a>  CImage::GetPixel

*X*と*y*によって指定された位置にあるピクセルの色を取得します。

```
COLORREF GetPixel(int x, int y) const throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
ピクセルの x 座標。

*y*<br/>
ピクセルの y 座標。

### <a name="return-value"></a>戻り値

ピクセルの赤、緑、青 (RGB) の値。 ピクセルが現在のクリッピング領域の外側にある場合、戻り値は CLR_INVALID です。

##  <a name="getpixeladdress"></a>  CImage::GetPixelAddress

ピクセルの正確なアドレスを取得します。

```
void* GetPixelAddress(int x, int y) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
ピクセルの x 座標。

*y*<br/>
ピクセルの y 座標。

### <a name="remarks"></a>Remarks

アドレスは、ピクセルの座標、ビットマップのピッチ、およびピクセルあたりのビット数に基づいて決定されます。

1ピクセルあたり8ビット未満の形式の場合、このメソッドはピクセルを格納しているバイトのアドレスを返します。 たとえば、イメージ形式が1ピクセル`GetPixelAddress`あたり4ビットの場合、はバイトの最初のピクセルのアドレスを返し、1バイトあたり2ピクセルの場合はを計算する必要があります。

> [!NOTE]
> このメソッドは、DIB セクションビットマップだけをサポートします。

##  <a name="gettransparentcolor"></a>  CImage::GetTransparentColor

カラーパレット内の透明色のインデックス位置を取得します。

```
LONG GetTransparentColor() const throw();
```

### <a name="return-value"></a>戻り値

透明色のインデックス。

##  <a name="getwidth"></a>  CImage::GetWidth

イメージの幅 (ピクセル単位) を取得します。

```
int GetWidth() const throw();
```

### <a name="return-value"></a>戻り値

ビットマップの幅 (ピクセル単位)。

##  <a name="isdibsection"></a>CImage:: IsDIBSection

添付ビットマップが DIB セクションかどうかを判断します。

```
bool IsDIBSection() const throw();
```

### <a name="return-value"></a>戻り値

添付ビットマップが DIB セクションの場合は TRUE。 それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

ビットマップが dib セクションでない場合、次`CImage`のメソッドは使用できません。これらのメソッドでは、dib セクションビットマップのみがサポートされます。

- [GetBits](#getbits)

- [GetColorTable](#getcolortable)

- [GetMaxColorTableEntries](#getmaxcolortableentries)

- [GetPitch](#getpitch)

- [GetPixelAddress](#getpixeladdress)

- [IsIndexed](#isindexed)

- [SetColorTable](#setcolortable)

##  <a name="isindexed"></a>  CImage::IsIndexed

ビットマップのピクセルがカラーパレットにマップされるかどうかを判断します。

```
bool IsIndexed() const throw();
```

### <a name="return-value"></a>戻り値

インデックスが作成されている場合は TRUE です。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

このメソッドは、ビットマップが8ビット (256 色) 以下の場合にのみ TRUE を返します。

> [!NOTE]
> このメソッドは、DIB セクションビットマップだけをサポートします。

##  <a name="isnull"></a>  CImage::IsNull

ビットマップが現在読み込まれているかどうかを判断します。

```
bool IsNull() const throw();
```

### <a name="remarks"></a>Remarks

このメソッドは、ビットマップが現在読み込まれていない場合に TRUE を返します。それ以外の場合は FALSE。

##  <a name="istransparencysupported"></a>  CImage::IsTransparencySupported

アプリケーションが透明なビットマップをサポートするかどうかを示します。

```
static BOOL IsTransparencySupported() throw();
```

### <a name="return-value"></a>戻り値

現在のプラットフォームが透明度をサポートしている場合は0以外の。 それ以外の場合は0です。

### <a name="remarks"></a>Remarks

戻り値が0以外で、透明度がサポートされている場合、 [AlphaBlend](#alphablend)、 [TransparentBlt](#transparentblt)、または[Draw](#draw)を呼び出すと透明色が処理されます。

##  <a name="load"></a>CImage:: Load

イメージを読み込みます。

```
HRESULT Load(LPCTSTR pszFileName) throw();
HRESULT Load(IStream* pStream) throw();
```

### <a name="parameters"></a>パラメーター

*pszFileName*<br/>
読み込むイメージファイルの名前を格納している文字列へのポインター。

*pStream*<br/>
読み込むイメージファイルの名前を格納しているストリームへのポインター。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

*Pszfilename*または*pstream*によって指定されたイメージを読み込みます。

有効なイメージの種類は、BMP、GIF、JPEG、PNG、および TIFF です。

##  <a name="loadfromresource"></a>  CImage::LoadFromResource

ビットマップリソースからイメージを読み込みます。

```
void LoadFromResource(
    HINSTANCE hInstance,
    LPCTSTR pszResourceName) throw();

void LoadFromResource(
    HINSTANCE hInstance,
    UINT nIDResource) throw();
```

### <a name="parameters"></a>パラメーター

*hInstance*<br/>
読み込むイメージを含むモジュールのインスタンスを処理します。

*pszResourceName*<br/>
読み込むイメージを格納しているリソースの名前を格納している文字列へのポインター。

*nIDResource*<br/>
読み込むリソースの ID。

### <a name="remarks"></a>Remarks

リソースの種類は BITMAP である必要があります。

##  <a name="maskblt"></a>CImage:: MaskBlt

指定したマスクおよびラスター操作を使用して、コピー元とコピー先のビットマップのカラーデータを結合します。

```
BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    HBITMAP hbmMask,
    int xMask,
    int yMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const POINT& pointSrc,
    HBITMAP hbmMask,
    const POINT& pointMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();

BOOL MaskBlt(
    HDC hDestDC,
    const POINT& pointDest,
    HBITMAP hbmMask,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>パラメーター

*hDestDC*<br/>
実行可能ファイルにリソースが格納されているモジュールへのハンドル。

*xDest*<br/>
コピー先の四角形の左上隅の x 座標 (論理単位)。

*yDest*<br/>
コピー先の四角形の左上隅の y 座標 (論理単位)。

*nDestWidth*<br/>
コピー先の四角形とソースビットマップの幅 (論理単位)。

*nDestHeight*<br/>
コピー先の四角形とコピー元のビットマップの高さ (論理単位)。

*xSrc*<br/>
ソースビットマップの左上隅の論理 x 座標。

*ySrc*<br/>
ソースビットマップの左上隅の論理 y 座標。

*hbmMask*<br/>
ソースデバイスコンテキストのカラービットマップと組み合わせた、モノクロマスクビットマップへのハンドル。

*xMask*<br/>
*Hbmmask*パラメーターによって指定されたマスクビットマップの水平方向のピクセルオフセット。

*yMask*<br/>
*Hbmmask*パラメーターによって指定されたマスクビットマップの垂直ピクセルオフセット。

*dwROP*<br/>
ソースとターゲットのデータの組み合わせを制御するためにメソッドが使用する、前景色と背景の3項ラスター操作コードの両方を指定します。 バックグラウンドラスター操作コードは、この値の上位ワードの上位バイトに格納されます。前景ラスター操作コードは、この値の上位ワードの下位バイトに格納されます。この値の下位ワードは無視され、0にする必要があります。 このメソッドのコンテキストにおけるフォアグラウンドとバックグラウンドの詳細については`MaskBlt` 、Windows SDK の「」を参照してください。 一般的なラスター操作コードの一覧について`BitBlt`は、Windows SDK の「」を参照してください。

*rectDest*<br/>
変換先を識別`RECT`する構造体への参照。

*pointSrc*<br/>
コピー元の四角形の左上隅を示す構造体。`POINT`

*pointMask*<br/>
マスクビットマップの左上隅を示す構造体。`POINT`

*pointDest*<br/>
コピー先の四角形`POINT`の左上隅 (論理単位) を識別する構造体への参照。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

この方法は、Windows NT バージョン4.0 以降にのみ適用されます。

##  <a name="operator_hbitmap"></a>CImage:: operator HBITMAP

`CImage`オブジェクトのアタッチされた Windows GDI ハンドルを取得するには、この演算子を使用します。 この演算子は、HBITMAP オブジェクトの直接使用をサポートするキャスト演算子です。

##  <a name="plgblt"></a>  CImage::PlgBlt

ソースデバイスコンテキストの四角形から、変換先デバイスコンテキストの平行四辺形へのビットブロック転送を実行します。

```
BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    HBITMAP hbmMask = NULL) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    HBITMAP hbmMask = NULL,
    int xMask = 0,
    int yMask = 0) const throw();

BOOL PlgBlt(
    HDC hDestDC,
    const POINT* pPoints,
    const RECT& rectSrc,
    HBITMAP hbmMask = NULL,
    const POINT& pointMask = CPoint(0, 0)) const throw();
```

### <a name="parameters"></a>パラメーター

*hDestDC*<br/>
宛先デバイスコンテキストへのハンドル。

*pPoints*<br/>
コピー先の平行四辺形の3つの角を識別する論理空間内の3つの点の配列へのポインター。 コピー元の四角形の左上隅は、この配列の最初の点、この配列の2番目の点の右上隅、および3番目の点の左下隅にマップされます。 ソースの四角形の右下隅は、平行四辺形の4番目の点にマップされます。

*hbmMask*<br/>
コピー元の四角形の色をマスクするために使用されるオプションのモノクロビットマップを指定するハンドル。

*xSrc*<br/>
コピー元の四角形の左上隅の x 座標 (論理単位)。

*ySrc*<br/>
コピー元の四角形の左上隅の y 座標 (論理単位)。

*nSrcWidth*<br/>
コピー元の四角形の幅 (論理単位)。

*Nsr、*<br/>
コピー元の四角形の高さ (論理単位)。

*xMask*<br/>
モノクロビットマップの左上隅の x 座標。

*yMask*<br/>
モノクロビットマップの左上隅の y 座標。

*rectSrc*<br/>
ソース四角形の座標を指定する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*pointMask*<br/>
マスクビットマップの左上隅を示す[ポイント](/previous-versions/dd162805\(v=vs.85\))構造体。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

*Hbmmask*が有効なモノクロビットマップを識別`PlgBit`する場合、はこのビットマップを使用して、ソースの四角形の色データのビットをマスクします。

この方法は、Windows NT バージョン4.0 以降にのみ適用されます。 詳細については、Windows SDK の「 [PlgBlt](/windows/win32/api/wingdi/nf-wingdi-plgblt) 」を参照してください。

##  <a name="releasedc"></a>  CImage::ReleaseDC

デバイスコンテキストを解放します。

```
void ReleaseDC() const throw();
```

### <a name="remarks"></a>Remarks

一度に1つのデバイスコンテキストに選択できるビットマップは1つだけなので`ReleaseDC` 、 [GetDC](#getdc)を呼び出すたびにを呼び出す必要があります。

##  <a name="releasegdiplus"></a>  CImage::ReleaseGDIPlus

GDI + によって使用されるリソースを解放します。

```
void ReleaseGDIPlus() throw();
```

### <a name="remarks"></a>Remarks

グローバル`CImage`オブジェクトによって割り当てられたリソースを解放するには、このメソッドを呼び出す必要があります。 「 [Cimage:: cimage](#cimage)」を参照してください。

##  <a name="save"></a>CImage:: 保存

ディスク上の指定したストリームまたはファイルにイメージを保存します。

```
HRESULT Save(
    IStream* pStream,
    REFGUID guidFileType) const throw();

HRESULT Save(
    LPCTSTR pszFileName,
    REFGUID guidFileType = GUID_NULL) const throw();
```

### <a name="parameters"></a>パラメーター

*pStream*<br/>
ファイルイメージデータを格納している COM IStream オブジェクトへのポインター。

*pszFileName*<br/>
イメージのファイル名へのポインター。

*guidFileType*<br/>
イメージを保存するファイルの種類。 次のいずれかの値を指定します。

- `ImageFormatBMP`非圧縮ビットマップイメージ。

- `ImageFormatPNG`ポータブルネットワークグラフィック (PNG) の圧縮されたイメージ。

- `ImageFormatJPEG`JPEG 圧縮イメージ。

- `ImageFormatGIF`GIF 圧縮画像。

> [!NOTE]
> 定数の完全な一覧については、「Windows SDK 内の**イメージファイル形式定数**」を参照してください。

### <a name="return-value"></a>戻り値

標準の HRESULT です。

### <a name="remarks"></a>Remarks

指定した名前と型を使用してイメージを保存します。 *Guidfiletype*パラメーターが指定されていない場合は、ファイル名のファイル拡張子を使用してイメージ形式が決定されます。 拡張子が指定されていない場合、イメージは BMP 形式で保存されます。

##  <a name="setcolortable"></a>  CImage::SetColorTable

DIB セクションのパレット内のエントリの範囲に対して、赤、緑、青 (RGB) の色の値を設定します。

```
void SetColorTable(
    UINT iFirstColor,
    UINT nColors,
    const RGBQUAD* prgbColors) throw();
```

### <a name="parameters"></a>パラメーター

*iFirstColor*<br/>
設定する最初のエントリのカラーテーブルインデックス。

*n 色*<br/>
設定するカラーテーブルエントリの数。

*prgbColors*<br/>
カラーテーブルエントリを設定する[RGBQUAD](/windows/win32/api/wingdi/ns-wingdi-rgbquad)構造体の配列へのポインター。

### <a name="remarks"></a>Remarks

このメソッドは、DIB セクションビットマップだけをサポートします。

##  <a name="setpixel"></a>  CImage::SetPixel

ビットマップ内の特定の位置にあるピクセルの色を設定します。

```
void SetPixel(int x, int y, COLORREF color) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
設定するピクセルの水平位置。

*y*<br/>
設定するピクセルの垂直位置。

*色*<br/>
ピクセルの設定に使用する色。

### <a name="remarks"></a>Remarks

ピクセル座標が選択されたクリッピング領域の外側にある場合、このメソッドは失敗します。

##  <a name="setpixelindexed"></a>  CImage::SetPixelIndexed

カラーパレットの*iIndex*にある色にピクセルの色を設定します。

```
void SetPixelIndexed(int x, int y, int iIndex) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
設定するピクセルの水平位置。

*y*<br/>
設定するピクセルの垂直位置。

*iIndex*<br/>
カラーパレット内の色のインデックス。

##  <a name="setpixelrgb"></a>  CImage::SetPixelRGB

*X*と*y*によって指定された位置にあるピクセルを、 *r*、 *g*、および*b*によって示される色を、赤、緑、青 (RGB) のイメージで設定します。

```
void SetPixelRGB(
    int x,
    int y,
    BYTE r,
    BYTE g,
    BYTE b) throw();
```

### <a name="parameters"></a>パラメーター

*x*<br/>
設定するピクセルの水平位置。

*y*<br/>
設定するピクセルの垂直位置。

*r*<br/>
赤の色の濃度。

*g*<br/>
緑の色の濃度。

*b*<br/>
青の色の輝度。

### <a name="remarks"></a>Remarks

赤、緑、および青の各パラメーターは、それぞれ 0 ~ 255 の数値で表されます。 3つのパラメーターをすべて0に設定すると、結果として得られる色は黒になります。 3つのパラメーターをすべて255に設定した場合、結果として得られる色は白になります。

##  <a name="settransparentcolor"></a>  CImage::SetTransparentColor

指定されたインデックス位置にある色を透明として設定します。

```
LONG SetTransparentColor(LONG iTransparentColor) throw();
```

### <a name="parameters"></a>パラメーター

*iTransparentColor*<br/>
透明に設定する色のカラーパレット内のインデックス。 -1 の場合、色は透明に設定されません。

### <a name="return-value"></a>戻り値

以前に透明として設定された色のインデックス。

##  <a name="stretchblt"></a>CImage:: StretchBlt

ソースデバイスコンテキストからこの現在のデバイスコンテキストにビットマップをコピーします。

```
BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    DWORD dwROP = SRCCOPY) const throw();

BOOL StretchBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    DWORD dwROP = SRCCOPY) const throw();
```

### <a name="parameters"></a>パラメーター

*hDestDC*<br/>
宛先デバイスコンテキストへのハンドル。

*xDest*<br/>
コピー先の四角形の左上隅の x 座標 (論理単位)。

*yDest*<br/>
コピー先の四角形の左上隅の y 座標 (論理単位)。

*nDestWidth*<br/>
コピー先の四角形の幅 (論理単位)。

*nDestHeight*<br/>
コピー先の四角形の高さ (論理単位)。

*dwROP*<br/>
実行するラスター操作。 ラスター操作コードでは、変換元、変換先、および (現在選択されているブラシで定義されている) パターンのビットを組み合わせることによって、変換先を形成する方法を正確に定義します。 その他のラスター操作コードとその説明の一覧については、Windows SDK の「 [BitBlt](/windows/win32/api/wingdi/nf-wingdi-bitblt) 」を参照してください。

*rectDest*<br/>
ターゲットを識別する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*xSrc*<br/>
コピー元の四角形の左上隅の x 座標 (論理単位)。

*ySrc*<br/>
コピー元の四角形の左上隅の y 座標 (論理単位)。

*nSrcWidth*<br/>
コピー元の四角形の幅 (論理単位)。

*Nsr、*<br/>
コピー元の四角形の高さ (論理単位)。

*rectSrc*<br/>
ソースを識別する`RECT`構造体への参照。

### <a name="return-value"></a>戻り値

成功した場合は0以外の。それ以外の場合は0。

### <a name="remarks"></a>Remarks

詳細については、Windows SDK の「 [StretchBlt](/windows/win32/api/wingdi/nf-wingdi-stretchblt) 」を参照してください。

##  <a name="transparentblt"></a>  CImage::TransparentBlt

ソースデバイスコンテキストからこの現在のデバイスコンテキストにビットマップをコピーします。

```
BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    int xDest,
    int yDest,
    int nDestWidth,
    int nDestHeight,
    int xSrc,
    int ySrc,
    int nSrcWidth,
    int nSrcHeight,
    UINT crTransparent = CLR_INVALID) const throw();

BOOL TransparentBlt(
    HDC hDestDC,
    const RECT& rectDest,
    const RECT& rectSrc,
    UINT crTransparent = CLR_INVALID) const throw();
```

### <a name="parameters"></a>パラメーター

*hDestDC*<br/>
宛先デバイスコンテキストへのハンドル。

*xDest*<br/>
コピー先の四角形の左上隅の x 座標 (論理単位)。

*yDest*<br/>
コピー先の四角形の左上隅の y 座標 (論理単位)。

*nDestWidth*<br/>
コピー先の四角形の幅 (論理単位)。

*nDestHeight*<br/>
コピー先の四角形の高さ (論理単位)。

*crTransparent*<br/>
透明として扱うソースビットマップの色。 既定では、CLR_INVALID は、イメージの透明色として現在設定されている色を使用することを示します。

*rectDest*<br/>
ターゲットを識別する[RECT](/previous-versions/dd162897\(v=vs.85\))構造体への参照。

*xSrc*<br/>
コピー元の四角形の左上隅の x 座標 (論理単位)。

*ySrc*<br/>
コピー元の四角形の左上隅の y 座標 (論理単位)。

*nSrcWidth*<br/>
コピー元の四角形の幅 (論理単位)。

*Nsr、*<br/>
コピー元の四角形の高さ (論理単位)。

*rectSrc*<br/>
ソースを識別する`RECT`構造体への参照。

### <a name="return-value"></a>戻り値

成功した場合は TRUE、それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

`TransparentBlt`は、1ピクセルあたり4ビット、1ピクセルあたり8ビットのソースビットマップでサポートされています。 [AlphaBlend](#alphablend)を使用して、透明度の32ビット/ピクセルのビットマップを指定します。

### <a name="example"></a>例

```cpp
// Performs a transparent blit from the source image to the destination
// image using the images' current transparency settings
BOOL TransparentBlt(CImage* pSrcImage, CImage* pDstImage,
       int xDest, int yDest, int nDestWidth, int nDestHeight)
{
    HDC hDstDC = NULL;
    BOOL bResult;

    if(pSrcImage == NULL || pDstImage == NULL)
    {
        // Invalid parameter
        return FALSE;
    }

    // Obtain a DC to the destination image
    hDstDC = pDstImage->GetDC();
    // Perform the blit
    bResult = pSrcImage->TransparentBlt(hDstDC, xDest, yDest, nDestWidth, nDestHeight);

    // Release the destination DC
    pDstImage->ReleaseDC();

    return bResult;
}
```

## <a name="see-also"></a>関連項目

[MMXSwarm サンプル](../../overview/visual-cpp-samples.md)<br/>
[SimpleImage サンプル](../../overview/visual-cpp-samples.md)<br/>
[デバイスに依存しないビットマップ](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)<br/>
[ATL COM デスクトップ コンポーネント](../../atl/atl-com-desktop-components.md)<br/>
[デバイスに依存しないビットマップ](/windows/win32/gdi/device-independent-bitmaps)<br/>
[CreateDIBSection](/windows/win32/api/wingdi/nf-wingdi-createdibsection)
