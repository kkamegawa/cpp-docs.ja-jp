---
title: CGdiObject クラス
ms.date: 11/04/2016
f1_keywords:
- CGdiObject
- AFXWIN/CGdiObject
- AFXWIN/CGdiObject::CGdiObject
- AFXWIN/CGdiObject::Attach
- AFXWIN/CGdiObject::CreateStockObject
- AFXWIN/CGdiObject::DeleteObject
- AFXWIN/CGdiObject::DeleteTempMap
- AFXWIN/CGdiObject::Detach
- AFXWIN/CGdiObject::FromHandle
- AFXWIN/CGdiObject::GetObject
- AFXWIN/CGdiObject::GetObjectType
- AFXWIN/CGdiObject::GetSafeHandle
- AFXWIN/CGdiObject::UnrealizeObject
- AFXWIN/CGdiObject::m_hObject
helpviewer_keywords:
- CGdiObject [MFC], CGdiObject
- CGdiObject [MFC], Attach
- CGdiObject [MFC], CreateStockObject
- CGdiObject [MFC], DeleteObject
- CGdiObject [MFC], DeleteTempMap
- CGdiObject [MFC], Detach
- CGdiObject [MFC], FromHandle
- CGdiObject [MFC], GetObject
- CGdiObject [MFC], GetObjectType
- CGdiObject [MFC], GetSafeHandle
- CGdiObject [MFC], UnrealizeObject
- CGdiObject [MFC], m_hObject
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
ms.openlocfilehash: ea82e2c667dcbd476d22ed23085d409b448b27ed
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69506258"
---
# <a name="cgdiobject-class"></a>CGdiObject クラス

ビットマップ、領域、ブラシ、ペン、パレット、フォントなどの Windows のさまざまな種類のグラフィックス デバイス インターフェイス (GDI) の基底クラスを提供します。

## <a name="syntax"></a>構文

```
class CGdiObject : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CGdiObject::CGdiObject](#cgdiobject)|`CGdiObject` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CGdiObject:: Attach](#attach)|Windows GDI オブジェクトを`CGdiObject`オブジェクトにアタッチします。|
|[CGdiObject::CreateStockObject](#createstockobject)|Windows の定義済みのストックペン、ブラシ、またはフォントの1つへのハンドルを取得します。|
|[CGdiObject::DeleteObject](#deleteobject)|オブジェクトに関連付けられている`CGdiObject`すべてのシステムストレージを解放することによって、オブジェクトにアタッチされている Windows GDI オブジェクトをメモリから削除します。|
|[CGdiObject::DeleteTempMap](#deletetempmap)|によって`CGdiObject`作成され`FromHandle`た一時オブジェクトを削除します。|
|[CGdiObject::D etach](#detach)|Windows gdi オブジェクトを`CGdiObject`オブジェクトからデタッチし、windows gdi オブジェクトへのハンドルを返します。|
|[CGdiObject:: FromHandle](#fromhandle)|Windows GDI オブジェクトへの`CGdiObject`ハンドルを指定して、オブジェクトへのポインターを返します。|
|[CGdiObject:: GetObject](#getobject)|`CGdiObject`オブジェクトにアタッチされている Windows GDI オブジェクトを記述するデータをバッファーに格納します。|
|[CGdiObject::GetObjectType](#getobjecttype)|GDI オブジェクトの型を取得します。|
|[CGdiObject:: GetSafeHandle](#getsafehandle)|Null `m_hObject`の場合を返します。 null の場合、null が返されます。|
|[CGdiObject::UnrealizeObject](#unrealizeobject)|ブラシの原点をリセットするか、論理パレットをリセットします。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CGdiObject:: operator! =](#operator_neq)|2つの GDI オブジェクトが論理的に等しくないかどうかを判断します。|
|[CGdiObject:: operator = =](#operator_eq_eq)|2つの GDI オブジェクトが論理的に等しいかどうかを判断します。|
|[CGdiObject:: operator HGDIOBJ](#operator_hgdiobj)|アタッチされた Windows GDI オブジェクトへのハンドルを取得します。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CGdiObject::m_hObject](#m_hobject)|このオブジェクトにアタッチされている HBITMAP、HPALETTE、HRGN、HPALETTE、HPALETTE、または HPALETTE を含むハンドル。|

## <a name="remarks"></a>Remarks

を`CGdiObject`直接作成することはありません。 代わりに、または`CPen` `CBrush`などの派生クラスのいずれかからオブジェクトを作成します。

`CGdiObject`の詳細については[グラフィック オブジェクト](../../mfc/graphic-objects.md)を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CGdiObject`

## <a name="requirements"></a>要件

**ヘッダー:** afxwin.h

##  <a name="attach"></a>CGdiObject:: Attach

Windows GDI オブジェクトを`CGdiObject`オブジェクトにアタッチします。

```
BOOL Attach(HGDIOBJ hObject);
```

### <a name="parameters"></a>パラメーター

*hObject*<br/>
Windows GDI オブジェクト (HPEN や HPEN など) へのハンドル。

### <a name="return-value"></a>戻り値

添付ファイルが成功した場合は0以外の。それ以外の場合は0です。

##  <a name="cgdiobject"></a>CGdiObject::CGdiObject

`CGdiObject` オブジェクトを構築します。

```
CGdiObject();
```

### <a name="remarks"></a>Remarks

を`CGdiObject`直接作成することはありません。 代わりに、または`CPen` `Cbrush`などの派生クラスのいずれかからオブジェクトを作成します。

##  <a name="createstockobject"></a>  CGdiObject::CreateStockObject

定義済みのストック Windows GDI ペン、ブラシ、またはフォントの1つへのハンドルを取得し、GDI オブジェクト`CGdiObject`をオブジェクトにアタッチします。

```
BOOL CreateStockObject(int nIndex);
```

### <a name="parameters"></a>パラメーター

*nIndex*<br/>
必要なストックオブジェクトの種類を指定する定数。 適切な値の説明については、Windows SDK にある[Getstockobject](/windows/win32/api/wingdi/nf-wingdi-getstockobject)のパラメーター *fnobject*を参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

この関数を、ストックペンなど、 `CPen` Windows GDI オブジェクト型に対応する派生クラスの1つと共に呼び出します。

##  <a name="deleteobject"></a>  CGdiObject::DeleteObject

Windows GDI オブジェクトに関連付けられているすべてのシステム記憶域を解放することによって、アタッチされた Windows GDI オブジェクトをメモリから削除します。

```
BOOL DeleteObject();
```

### <a name="return-value"></a>戻り値

GDI オブジェクトが正常に削除された場合は0以外の。それ以外の場合は0です。

### <a name="remarks"></a>Remarks

`CGdiObject`オブジェクトに関連付けられているストレージは、この呼び出しの影響を受けません。 アプリケーションは、デバイスコンテキスト`DeleteObject`に現在`CGdiObject`選択されているオブジェクトでを呼び出すことはできません。

パターンブラシが削除されても、ブラシに関連付けられているビットマップは削除されません。 ビットマップは、個別に削除する必要があります。

##  <a name="deletetempmap"></a>  CGdiObject::DeleteTempMap

`CWinApp`アイドルタイムハンドラーによって自動的に呼び出さ`DeleteTempMap`れ、に`CGdiObject`よって`FromHandle`作成された一時オブジェクトを削除します。

```
static void PASCAL DeleteTempMap();
```

### <a name="remarks"></a>Remarks

`DeleteTempMap`オブジェクト`CGdiObject`を削除する前に、一時`CGdiObject`オブジェクトにアタッチされている Windows GDI オブジェクトをデタッチします。

### <a name="example"></a>例

[!code-cpp[NVC_MFCDocView#175](../../mfc/codesnippet/cpp/cgdiobject-class_1.cpp)]

##  <a name="detach"></a>CGdiObject::D etach

Windows gdi オブジェクトを`CGdiObject`オブジェクトからデタッチし、windows gdi オブジェクトへのハンドルを返します。

```
HGDIOBJ Detach();
```

### <a name="return-value"></a>戻り値

デタッチ`HANDLE`された Windows gdi オブジェクトへの。 gdi オブジェクトがアタッチされていない場合は NULL。

##  <a name="fromhandle"></a>CGdiObject:: FromHandle

Windows GDI オブジェクトへの`CGdiObject`ハンドルを指定して、オブジェクトへのポインターを返します。

```
static CGdiObject* PASCAL FromHandle(HGDIOBJ hObject);
```

### <a name="parameters"></a>パラメーター

*hObject*<br/>
Windows GDI オブジェクトを表すハンドルです。

### <a name="return-value"></a>戻り値

一時的または永続的`CGdiObject`なへのポインター。

### <a name="remarks"></a>Remarks

オブジェクトが Windows GDI オブジェクトにまだアタッチされていない場合は`CGdiObject` 、一時オブジェクトが作成され、アタッチされます。 `CGdiObject`

この一時`CGdiObject`オブジェクトは、アプリケーションが次にそのイベントループ内でアイドル状態になるまで有効です。その時点で、すべての一時グラフィックオブジェクトが削除されます。 別の方法として、一時オブジェクトは1つのウィンドウメッセージの処理中にのみ有効であるということもあります。

##  <a name="getobject"></a>  CGdiObject::GetObject

指定されたオブジェクトを定義するデータをバッファーに格納します。

```
int GetObject(
    int nCount,
    LPVOID lpObject) const;
```

### <a name="parameters"></a>パラメーター

*nCount*<br/>
*LpObject*バッファーにコピーするバイト数を指定します。

*lpObject*<br/>
情報を受け取るユーザー指定のバッファーを指します。

### <a name="return-value"></a>戻り値

取得されたバイト数。それ以外の場合は、エラーが発生した場合は0です。

### <a name="remarks"></a>Remarks

関数は、次の一覧に示すように、グラフィックオブジェクトの型に依存する型を持つデータ構造を取得します。

|オブジェクト|バッファーの種類|
|------------|-----------------|
|`CPen`|[LOGPEN](/windows/win32/api/Wingdi/ns-wingdi-logpen)|
|`CBrush`|[LOGBRUSH](/windows/win32/api/wingdi/ns-wingdi-logbrush)|
|`CFont`|[LOGFONT](/windows/win32/api/wingdi/ns-wingdi-logfontw)|
|`CBitmap`|[マップ](/windows/win32/api/wingdi/ns-wingdi-bitmap)|
|`CPalette`|WORD|
|`CRgn`|サポートなし|

オブジェクトが`CBitmap`オブジェクトの場合は、 `GetObject`ビットマップの幅、高さ、および色の書式情報のみを返します。 実際のビットは、 [CBitmap:: GetBitmapBits](../../mfc/reference/cbitmap-class.md#getbitmapbits)を使用して取得できます。

オブジェクトが`CPalette`オブジェクトの場合は、 `GetObject`パレット内のエントリの数を指定する単語を取得します。 関数は、パレットを定義する[Logpalette](/windows/win32/api/wingdi/ns-wingdi-logpalette)構造体を取得しません。 アプリケーションでは、 [CPalette:: getpalette エントリ](../../mfc/reference/cpalette-class.md#getpaletteentries)を呼び出すことによって、パレットエントリに関する情報を取得できます。

##  <a name="getobjecttype"></a>  CGdiObject::GetObjectType

GDI オブジェクトの型を取得します。

```
UINT GetObjectType() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、オブジェクトの型。それ以外の場合は0です。 値は次のいずれかになります。

- OBJ_BITMAP ビットマップ

- OBJ_BRUSH Brush

- OBJ_FONT フォント

- OBJ_PAL パレット

- OBJ_PEN ペン

- OBJ_EXTPEN 拡張ペン

- OBJ_REGION リージョン

- OBJ_DC デバイスコンテキスト

- OBJ_MEMDC Memory デバイスコンテキスト

- OBJ_METAFILE メタファイル

- OBJ_METADC メタファイルデバイスコンテキスト

- OBJ_ENHMETAFILE 拡張メタファイル

- OBJ_ENHMETADC 拡張メタファイルデバイスコンテキスト

##  <a name="getsafehandle"></a>CGdiObject:: GetSafeHandle

Null `m_hObject`の場合を返します。 null の場合、null が返されます。

```
HGDIOBJ GetSafeHandle() const;
```

### <a name="return-value"></a>戻り値

アタッチされた Windows GDI オブジェクトへのハンドル。それ以外の場合は、オブジェクトがアタッチされていない場合は NULL です。

### <a name="remarks"></a>Remarks

これは一般的なハンドルインターフェイスパラダイムの一部であり、NULL がハンドルに対して有効な値または特殊な値である場合に便利です。

### <a name="example"></a>例

  [CWnd:: IsWindowEnabled](../../mfc/reference/cwnd-class.md#iswindowenabled)の例を参照してください。

##  <a name="m_hobject"></a>  CGdiObject::m_hObject

このオブジェクトにアタッチされている HBITMAP、HRGN、HBRUSH、HBRUSH、HBRUSH、または HBRUSH を含むハンドル。

```
HGDIOBJ m_hObject;
```

##  <a name="operator_neq"></a>CGdiObject:: operator! =

2つの GDI オブジェクトが論理的に等しくないかどうかを判断します。

```
BOOL operator!=(const CGdiObject& obj) const;
```

### <a name="parameters"></a>パラメーター

*obj*<br/>
既存`CGdiObject`のへのポインター。

### <a name="remarks"></a>Remarks

左辺の GDI オブジェクトが右辺の GDI オブジェクトと等しくないかどうかを判断します。

##  <a name="operator_eq_eq"></a>CGdiObject:: operator = =

2つの GDI オブジェクトが論理的に等しいかどうかを判断します。

```
BOOL operator==(const CGdiObject& obj) const;
```

### <a name="parameters"></a>パラメーター

*obj*<br/>
既存`CGdiObject`のへの参照。

### <a name="remarks"></a>Remarks

左辺の GDI オブジェクトが右辺の GDI オブジェクトと等しいかどうかを判断します。

##  <a name="operator_hgdiobj"></a>CGdiObject:: operator HGDIOBJ

アタッチされた Windows GDI オブジェクトへのハンドルを取得します。それ以外の場合は、オブジェクトがアタッチされていない場合は NULL です。

```
operator HGDIOBJ() const;
```

##  <a name="unrealizeobject"></a>CGdiObject::UnrealizeObject

ブラシの原点をリセットするか、論理パレットをリセットします。

```
BOOL UnrealizeObject();
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

はクラスのメンバー関数ですが、または`CPalette`オブジェクトで`CBrush`のみ呼び出す必要があります。 `CGdiObject` `UnrealizeObject`

オブジェクト`CBrush`の場合`UnrealizeObject` 、は、次にデバイスコンテキストに選択されたときに、指定されたブラシの原点をリセットするようにシステムに指示します。 オブジェクトが`CPalette`オブジェクトの場合、は`UnrealizeObject` 、以前は認識されていなかったかのように、パレットを認識するようにシステムに指示します。 次に、指定したパレットの[CDC:: RealizePalette](../../mfc/reference/cdc-class.md#realizepalette)関数をアプリケーションが呼び出すときに、システムは論理パレットをシステムパレットに完全に再マップします。

関数`UnrealizeObject`は、stock オブジェクトと共に使用することはできません。 関数`UnrealizeObject`は、新しいブラシの原点が設定されるたびに ( [CDC:: SetBrushOrg](../../mfc/reference/cdc-class.md#setbrushorg)関数によって) 呼び出される必要があります。 現在選択されているブラシまたは表示コンテキストの現在選択されているパレットに対して関数を呼び出すことはできません。`UnrealizeObject`

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[CBitmap クラス](../../mfc/reference/cbitmap-class.md)<br/>
[CBrush クラス](../../mfc/reference/cbrush-class.md)<br/>
[CFont クラス](../../mfc/reference/cfont-class.md)<br/>
[CPalette クラス](../../mfc/reference/cpalette-class.md)<br/>
[CPen クラス](../../mfc/reference/cpen-class.md)<br/>
[CRgn クラス](../../mfc/reference/crgn-class.md)
