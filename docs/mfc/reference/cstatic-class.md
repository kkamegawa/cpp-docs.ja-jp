---
title: CStatic クラス
ms.date: 11/04/2016
f1_keywords:
- CStatic
- AFXWIN/CStatic
- AFXWIN/CStatic::CStatic
- AFXWIN/CStatic::Create
- AFXWIN/CStatic::DrawItem
- AFXWIN/CStatic::GetBitmap
- AFXWIN/CStatic::GetCursor
- AFXWIN/CStatic::GetEnhMetaFile
- AFXWIN/CStatic::GetIcon
- AFXWIN/CStatic::SetBitmap
- AFXWIN/CStatic::SetCursor
- AFXWIN/CStatic::SetEnhMetaFile
- AFXWIN/CStatic::SetIcon
helpviewer_keywords:
- CStatic [MFC], CStatic
- CStatic [MFC], Create
- CStatic [MFC], DrawItem
- CStatic [MFC], GetBitmap
- CStatic [MFC], GetCursor
- CStatic [MFC], GetEnhMetaFile
- CStatic [MFC], GetIcon
- CStatic [MFC], SetBitmap
- CStatic [MFC], SetCursor
- CStatic [MFC], SetEnhMetaFile
- CStatic [MFC], SetIcon
ms.assetid: e7c94cd9-5ebd-428a-aa30-b3e51f8efb95
ms.openlocfilehash: fd7b6787b372e220a32770e19d54d149f5ba6934
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69502414"
---
# <a name="cstatic-class"></a>CStatic クラス

Windows のスタティック コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CStatic : public CWnd
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CStatic::CStatic](#cstatic)|`CStatic` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CStatic:: Create](#create)|Windows スタティックコントロールを作成し、 `CStatic`オブジェクトにアタッチします。|
|[CStatic::D rawItem](#drawitem)|オーナー描画の静的コントロールを描画するには、をオーバーライドします。|
|[CStatic:: GetBitmap](#getbitmap)|以前に[SetBitmap](#setbitmap)で設定されたビットマップのハンドルを取得します。|
|[CStatic:: GetCursor](#getcursor)|以前に[SetCursor](#setcursor)で設定したカーソルイメージのハンドルを取得します。|
|[CStatic::GetEnhMetaFile](#getenhmetafile)|以前に[SetEnhMetaFile](#setenhmetafile)で設定された拡張メタファイルのハンドルを取得します。|
|[CStatic:: GetIcon](#geticon)|以前に[SetIcon](#seticon)で設定したアイコンのハンドルを取得します。|
|[CStatic::SetBitmap](#setbitmap)|スタティックコントロールに表示されるビットマップを指定します。|
|[CStatic::SetCursor](#setcursor)|静的コントロールに表示されるカーソルイメージを指定します。|
|[CStatic::SetEnhMetaFile](#setenhmetafile)|静的コントロールに表示される拡張メタファイルを指定します。|
|[CStatic::SetIcon](#seticon)|静的コントロールに表示するアイコンを指定します。|

## <a name="remarks"></a>Remarks

静的コントロールは、テキスト文字列、ボックス、四角形、アイコン、カーソル、ビットマップ、または拡張メタファイルを表示します。 これは、他のコントロールのラベル付け、ボックス、または分離に使用できます。 静的コントロールは通常、入力を行わず、出力も行いません。ただし、SS_NOTIFY スタイルを使用して作成されている場合、マウスクリックの親に通知することができます。

静的コントロールを作成するには、次の2つの手順を実行します。 まず、コンストラクターを呼び出して`CStatic`オブジェクトを構築してから、 [create](#create) member 関数を呼び出して静的コントロールを作成し、それ`CStatic`をオブジェクトにアタッチします。

ダイアログボックス内で`CStatic` (ダイアログリソースを使用して) `CStatic`オブジェクトを作成すると、ユーザーがダイアログボックスを閉じたときにオブジェクトが自動的に破棄されます。

ウィンドウ内に`CStatic`オブジェクトを作成する場合は、そのオブジェクトを破棄することも必要になることがあります。 ウィンドウ`CStatic`内のスタック上に作成されたオブジェクトは、自動的に破棄されます。 新しい関数を使用`CStatic`してヒープ上にオブジェクトを作成した場合は、オブジェクトに対して**delete**を呼び出して、そのオブジェクトが終了したときに破棄する必要があります。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

`CStatic`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxwin.h

##  <a name="create"></a>  CStatic::Create

Windows スタティックコントロールを作成し、 `CStatic`オブジェクトにアタッチします。

```
virtual BOOL Create(
    LPCTSTR lpszText,
    DWORD dwStyle,
    const RECT& rect,
    CWnd* pParentWnd,
    UINT nID = 0xffff);
```

### <a name="parameters"></a>パラメーター

*lpszText*<br/>
コントロールに配置するテキストを指定します。 NULL の場合、テキストは表示されません。

*dwStyle*<br/>
静的コントロールのウィンドウスタイルを指定します。 コントロールに[静的コントロールスタイル](../../mfc/reference/styles-used-by-mfc.md#static-styles)の任意の組み合わせを適用します。

*rect*<br/>
静的コントロールの位置とサイズを指定します。 構造体`RECT` `CRect`またはオブジェクトのいずれかを指定できます。

*pParentWnd*<br/>
親ウィンドウを指定します。 `CDialog`通常はオブジェクトです。 `CStatic` NULL にすることはできません。

*nID*<br/>
スタティックコントロールのコントロール ID を指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

2つ`CStatic`の手順でオブジェクトを構築します。 まず、コンストラクター `CStatic`を呼び出し、次にを`Create`呼び出します。これにより、Windows の静的コントロールが`CStatic`作成され、オブジェクトにアタッチされます。

次の[ウィンドウスタイル](../../mfc/reference/styles-used-by-mfc.md#window-styles)を静的コントロールに適用します。

- 常に WS_CHILD

- WS_VISIBLE 通常

- WS_DISABLED はまれ

静的コントロールにビットマップ、カーソル、アイコン、またはメタファイルを表示する場合は、次の[静的スタイル](../../mfc/reference/styles-used-by-mfc.md#static-styles)のいずれかを適用する必要があります。

- SS_BITMAP ビットマップにこのスタイルを使用します。

- SS_ICON カーソルとアイコンには、このスタイルを使用します。

- SS_ENHMETAFILE 拡張メタファイル用にこのスタイルを使用します。

カーソル、ビットマップ、またはアイコンの場合は、次のスタイルを使用することもできます。

- SS_CENTERIMAGE を使用して、イメージを静的コントロールに中央揃えで配置します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#1](../../mfc/reference/codesnippet/cpp/cstatic-class_1.cpp)]

##  <a name="cstatic"></a>CStatic::CStatic

`CStatic` オブジェクトを構築します。

```
CStatic();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#2](../../mfc/reference/codesnippet/cpp/cstatic-class_2.cpp)]

##  <a name="drawitem"></a>CStatic::D rawItem

オーナー描画の静的コントロールを描画するために、フレームワークによって呼び出されます。

```
virtual void DrawItem(LPDRAWITEMSTRUCT lpDrawItemStruct);
```

### <a name="parameters"></a>パラメーター

*lpDrawItemStruct*<br/>
[DRAWITEMSTRUCT](/windows/win32/api/winuser/ns-winuser-drawitemstruct)構造体へのポインター。 構造体には、描画する項目と必要な描画の種類に関する情報が含まれます。

### <a name="remarks"></a>Remarks

オーナー描画`CStatic`オブジェクトの描画を実装するには、この関数をオーバーライドします (コントロールのスタイルは SS_OWNERDRAW です)。

##  <a name="getbitmap"></a>  CStatic::GetBitmap

に`CStatic`関連付けられているビットマップのハンドルを取得します。これは、以前に[SetBitmap](#setbitmap)で設定したものです。

```
HBITMAP GetBitmap() const;
```

### <a name="return-value"></a>戻り値

現在のビットマップを処理するハンドル。ビットマップが設定されていない場合は NULL。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="getcursor"></a>  CStatic::GetCursor

に`CStatic`関連付けられているカーソルのハンドルを取得します。これは、以前に[SetCursor](#setcursor)が設定されています。

```
HCURSOR GetCursor();
```

### <a name="return-value"></a>戻り値

現在のカーソルを処理するハンドル。カーソルが設定されていない場合は NULL。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="getenhmetafile"></a>  CStatic::GetEnhMetaFile

に`CStatic`関連付けられている拡張メタファイルのハンドルを取得します。これは、以前に[SetEnhMetafile](#setenhmetafile)で設定したものです。

```
HENHMETAFILE GetEnhMetaFile() const;
```

### <a name="return-value"></a>戻り値

現在の拡張メタファイルへのハンドル。拡張メタファイルが設定されていない場合は NULL。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="geticon"></a>  CStatic::GetIcon

に`CStatic`関連付けられている、以前に[SetIcon](#seticon)で設定されたアイコンのハンドルを取得します。

```
HICON GetIcon() const;
```

### <a name="return-value"></a>戻り値

現在のアイコンを示すハンドル。アイコンが設定されていない場合は NULL。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

##  <a name="setbitmap"></a>  CStatic::SetBitmap

新しいビットマップを静的コントロールに関連付けます。

```
HBITMAP SetBitmap(HBITMAP hBitmap);
```

### <a name="parameters"></a>パラメーター

*hBitmap*<br/>
静的コントロールに描画されるビットマップのハンドル。

### <a name="return-value"></a>戻り値

以前に静的コントロールに関連付けられていたビットマップのハンドル。静的コントロールに関連付けられているビットマップがない場合は NULL。

### <a name="remarks"></a>Remarks

ビットマップは、自動的に静的コントロールに描画されます。 既定では、この値は左上隅に描画され、スタティックコントロールはビットマップのサイズにサイズ変更されます。

次のようなさまざまなウィンドウと静的コントロールスタイルを使用できます。

- SS_BITMAP このスタイルは、常にビットマップに使用します。

- SS_CENTERIMAGE を使用して、イメージを静的コントロールに中央揃えで配置します。 イメージが静的コントロールより大きい場合は、クリップされます。 静的コントロールよりも小さい場合は、イメージの周囲の空白が、ビットマップの左上隅にあるピクセルの色によって塗りつぶされます。

- MFC にはクラス`CBitmap`が用意されています。このクラスは、Win32 関数`LoadBitmap`を呼び出すだけではなく、ビットマップイメージに対してさらに多くの操作を行う必要がある場合に使用できます。 `CBitmap`には、1種類の GDI オブジェクトが含まれています。 `CStatic`これは、と`CWnd`の連携でよく使用されます。これは、グラフィックオブジェクトを静的コントロールとして表示するために使用されるクラスです。

`CImage`は、デバイスに依存しないビットマップ (DIB) をより簡単に操作できる ATL/MFC クラスです。 詳細については、「 [CImage クラス](../../atl-mfc-shared/reference/cimage-class.md)」を参照してください。

- 一般的な使用方法と`CStatic::SetBitmap`して、オブジェクト`CBitmap`または`CImage`オブジェクトの HBITMAP 演算子によって返される GDI オブジェクトを指定します。 これを行うコードは、次の行のようになります。

```
MyStaticControl.SetBitmap(HBITMAP(MyBitmap));
```
次の例では`CStatic` 、ヒープ上に2つのオブジェクトを作成します。 次に、を使用`CBitmap::LoadOEMBitmap` `CImage::Load`してシステムビットマップを読み込み、もう1つを使用してファイルから読み込みます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#3](../../mfc/reference/codesnippet/cpp/cstatic-class_3.cpp)]

##  <a name="setcursor"></a>  CStatic::SetCursor

新しいカーソルイメージを静的コントロールに関連付けます。

```
HCURSOR SetCursor(HCURSOR hCursor);
```

### <a name="parameters"></a>パラメーター

*hCursor*<br/>
静的コントロールに描画されるカーソルのハンドル。

### <a name="return-value"></a>戻り値

以前に静的コントロールに関連付けられたカーソルのハンドル。静的コントロールに関連付けられているカーソルがない場合は NULL。

### <a name="remarks"></a>Remarks

カーソルは、自動的に静的コントロールに描画されます。 既定では、この値は左上隅に描画され、静的コントロールはカーソルのサイズに合わせてサイズが変更されます。

次のようなさまざまなウィンドウと静的コントロールスタイルを使用できます。

- SS_ICON カーソルとアイコンには常にこのスタイルを使用します。

- SS_CENTERIMAGE を使用して、スタティックコントロールの中央に配置します。 イメージが静的コントロールより大きい場合は、クリップされます。 静的コントロールより小さい場合は、イメージの周囲の空白が、静的コントロールの背景色で塗りつぶされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#4](../../mfc/reference/codesnippet/cpp/cstatic-class_4.cpp)]

##  <a name="setenhmetafile"></a>  CStatic::SetEnhMetaFile

新しい拡張メタファイルイメージを静的コントロールに関連付けます。

```
HENHMETAFILE SetEnhMetaFile(HENHMETAFILE hMetaFile);
```

### <a name="parameters"></a>パラメーター

*hMetaFile*<br/>
静的コントロールに描画される拡張メタファイルのハンドル。

### <a name="return-value"></a>戻り値

以前に静的コントロールに関連付けられていた拡張メタファイルのハンドル。または、拡張メタファイルが静的コントロールに関連付けられていない場合は NULL。

### <a name="remarks"></a>Remarks

拡張メタファイルは、静的コントロールに自動的に描画されます。 拡張メタファイルは、静的コントロールのサイズに合わせてスケーリングされます。

次のようなさまざまなウィンドウと静的コントロールスタイルを使用できます。

- SS_ENHMETAFILE 拡張メタファイルには、このスタイルを常に使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#5](../../mfc/reference/codesnippet/cpp/cstatic-class_5.cpp)]

##  <a name="seticon"></a>CStatic::SetIcon

新しいアイコンイメージを静的コントロールに関連付けます。

```
HICON SetIcon(HICON hIcon);
```

### <a name="parameters"></a>パラメーター

*hIcon*<br/>
静的コントロールに描画されるアイコンのハンドル。

### <a name="return-value"></a>戻り値

以前に静的コントロールに関連付けられていたアイコンのハンドル。静的コントロールに関連付けられているアイコンがない場合は NULL。

### <a name="remarks"></a>Remarks

アイコンは、静的コントロールに自動的に描画されます。 既定では、これは左上隅に描画され、静的コントロールはアイコンのサイズに合わせてサイズ変更されます。

次のようなさまざまなウィンドウと静的コントロールスタイルを使用できます。

- SS_ICON カーソルとアイコンには常にこのスタイルを使用します。

- SS_CENTERIMAGE を使用して、スタティックコントロールの中央に配置します。 イメージが静的コントロールより大きい場合は、クリップされます。 静的コントロールより小さい場合は、イメージの周囲の空白が、静的コントロールの背景色で塗りつぶされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CStatic#6](../../mfc/reference/codesnippet/cpp/cstatic-class_6.cpp)]

## <a name="see-also"></a>関連項目

[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CWnd クラス](../../mfc/reference/cwnd-class.md)<br/>
[CButton クラス](../../mfc/reference/cbutton-class.md)<br/>
[CComboBox クラス](../../mfc/reference/ccombobox-class.md)<br/>
[CEdit クラス](../../mfc/reference/cedit-class.md)<br/>
[CListBox クラス](../../mfc/reference/clistbox-class.md)<br/>
[CScrollBar クラス](../../mfc/reference/cscrollbar-class.md)<br/>
[CDialog クラス](../../mfc/reference/cdialog-class.md)
