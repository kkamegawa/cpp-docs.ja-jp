---
title: 淡色表示 (灰色) ビットマップ関数とディザリングされたビットマップ関数
ms.date: 11/19/2018
f1_keywords:
- AFXWIN/AfxDrawGrayBitmap
- AFXWIN/AfxGetGrayBitmap
- AFXWIN/AfxDrawDitheredBitmap
- AFXWIN/AfxGetDitheredBitmap
helpviewer_keywords:
- gray and dithered bitmap functions [MFC]
ms.assetid: cb139a77-b85e-4504-9d93-24156ad77a41
ms.openlocfilehash: fb764dbd71d89ae3317816df3539c2881b9695b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62322321"
---
# <a name="gray-and-dithered-bitmap-functions"></a>淡色表示 (灰色) ビットマップ関数とディザリングされたビットマップ関数

**淡色表示 (灰色) ビットマップ関数**

MFC には、ビットマップのコントロールが無効になっていることを示すための 2 つの関数が用意されています。

![灰色と元のアイコンの比較](../../mfc/reference/media/vcgraybitmap.gif "灰色と元のアイコンの比較")

|||
|-|-|
|[AfxDrawGrayBitmap](#afxdrawgraybitmap)|灰色のバージョンのビットマップを描画します。|
|[AfxGetGrayBitmap](#afxgetgraybitmap)|灰色のバージョンのビットマップをコピーします。|

**淡色表示 (灰色) ビットマップ関数**

MFC には、ビットマップの背景をディザリングされたパターンに置き換える 2 つの関数も用意されています。

![ディザリングされたと元のアイコンの比較](../../mfc/reference/media/vcditheredbitmap.gif "ディザリングされたと元のアイコンの比較")

|||
|-|-|
|[AfxDrawDitheredBitmap](#afxdrawditheredbitmap)|背景がディザリングされたビットマップを描画します。|
|[AfxGetDitheredBitmap](#afxgetditheredbitmap)|背景がディザリングされたビットマップをコピーします。|

##  <a name="afxdrawgraybitmap"></a>  AfxDrawGrayBitmap

灰色のバージョンのビットマップを描画します。

```
void AFXAPI AfxDrawGrayBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF crBackground);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
宛先 DC を示します。

*x*<br/>
宛先の x 座標。

*y*<br/>
宛先の y 座標。

*rSrc*<br/>
元のビットマップ。

*crBackground*<br/>
新しい背景色 (通常は COLOR_MENU などの灰色)。

### <a name="remarks"></a>Remarks

`AfxDrawGrayBitmap` で描画されるビットマップの外観は、無効なコントロールになります。

![灰色と元のアイコンの比較](../../mfc/reference/media/vcgraybitmap.gif "灰色と元のアイコンの比較")

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#191](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_1.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="afxgetgraybitmap"></a>  AfxGetGrayBitmap

灰色のバージョンのビットマップをコピーします。

```
void AFXAPI AfxGetGrayBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF crBackground);
```

### <a name="parameters"></a>パラメーター

*rSrc*<br/>
元のビットマップ。

*pDest*<br/>
コピー先のビットマップ。

*crBackground*<br/>
新しい背景色 (通常は COLOR_MENU などの灰色)。

### <a name="remarks"></a>Remarks

`AfxGetGrayBitmap` でコピーされるビットマップの外観は、無効なコントロールのようになります。

![灰色と元のアイコンの比較](../../mfc/reference/media/vcgraybitmap.gif "灰色と元のアイコンの比較")

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#193](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_2.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="afxdrawditheredbitmap"></a>  AfxDrawDitheredBitmap

その背景をディザリングされた (チェッカー) パターンに置き換えて、ビットマップを描画します。

```
void AFXAPI AfxDrawDitheredBitmap(
    CDC* pDC,
    int x,
    int y,
    const CBitmap& rSrc,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
宛先 DC を示します。

*x*<br/>
宛先の x 座標。

*y*<br/>
宛先の y 座標。

*rSrc*<br/>
元のビットマップ。

*cr1*<br/>
2 つのディザー カラーのいずれかの通常白します。

*cr2*<br/>
その他のディザー色、通常は明るい灰色 (COLOR_MENU)。

### <a name="remarks"></a>Remarks

2 色でレプリケート先 DC に元のビットマップが描画されます (*cr1*と*cr2*) 格子模様のパターン ビットマップの背景を置換します。 ソース ビットマップの背景は、その白いピクセル、左上隅にあるビットマップのピクセルの色と一致するすべてのピクセルとして定義されます。

![ディザリングされたと元のアイコンの比較](../../mfc/reference/media/vcditheredbitmap.gif "ディザリングされたと元のアイコンの比較")

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#190](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_3.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="afxgetditheredbitmap"></a>  AfxGetDitheredBitmap

その背景をディザリングされた (チェッカー) パターンに置き換えて、ビットマップをコピーします。

```
void AFXAPI AfxGetDitheredBitmap(
    const CBitmap& rSrc,
    CBitmap* pDest,
    COLORREF cr1  ,
    COLORREF cr2);
```

### <a name="parameters"></a>パラメーター

*rSrc*<br/>
元のビットマップ。

*pDest*<br/>
コピー先のビットマップ。

*cr1*<br/>
2 つのディザー カラーのいずれかの通常白します。

*cr2*<br/>
その他のディザー色、通常は明るい灰色 (COLOR_MENU)。

### <a name="remarks"></a>Remarks

ソース ビットマップは 2 色でコピー先ビットマップにコピー (*cr1*と*cr2*) ソース ビットマップの背景を置き換える格子模様のパターン。 ソース ビットマップの背景は、その白いピクセル、左上隅にあるビットマップのピクセルの色と一致するすべてのピクセルとして定義されます。

![ディザリングされたと元のアイコンの比較](../../mfc/reference/media/vcditheredbitmap.gif "vcditheredbitmap")

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#192](../../mfc/codesnippet/cpp/gray-and-dithered-bitmap-functions_4.cpp)]

### <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)
