---
title: CImageList クラス
ms.date: 11/04/2016
f1_keywords:
- CImageList
- AFXCMN/CImageList
- AFXCMN/CImageList::CImageList
- AFXCMN/CImageList::Add
- AFXCMN/CImageList::Attach
- AFXCMN/CImageList::BeginDrag
- AFXCMN/CImageList::Copy
- AFXCMN/CImageList::Create
- AFXCMN/CImageList::DeleteImageList
- AFXCMN/CImageList::DeleteTempMap
- AFXCMN/CImageList::Detach
- AFXCMN/CImageList::DragEnter
- AFXCMN/CImageList::DragLeave
- AFXCMN/CImageList::DragMove
- AFXCMN/CImageList::DragShowNolock
- AFXCMN/CImageList::Draw
- AFXCMN/CImageList::DrawEx
- AFXCMN/CImageList::DrawIndirect
- AFXCMN/CImageList::EndDrag
- AFXCMN/CImageList::ExtractIcon
- AFXCMN/CImageList::FromHandle
- AFXCMN/CImageList::FromHandlePermanent
- AFXCMN/CImageList::GetBkColor
- AFXCMN/CImageList::GetDragImage
- AFXCMN/CImageList::GetImageCount
- AFXCMN/CImageList::GetImageInfo
- AFXCMN/CImageList::GetSafeHandle
- AFXCMN/CImageList::Read
- AFXCMN/CImageList::Remove
- AFXCMN/CImageList::Replace
- AFXCMN/CImageList::SetBkColor
- AFXCMN/CImageList::SetDragCursorImage
- AFXCMN/CImageList::SetImageCount
- AFXCMN/CImageList::SetOverlayImage
- AFXCMN/CImageList::Write
- AFXCMN/CImageList::m_hImageList
helpviewer_keywords:
- CImageList [MFC], CImageList
- CImageList [MFC], Add
- CImageList [MFC], Attach
- CImageList [MFC], BeginDrag
- CImageList [MFC], Copy
- CImageList [MFC], Create
- CImageList [MFC], DeleteImageList
- CImageList [MFC], DeleteTempMap
- CImageList [MFC], Detach
- CImageList [MFC], DragEnter
- CImageList [MFC], DragLeave
- CImageList [MFC], DragMove
- CImageList [MFC], DragShowNolock
- CImageList [MFC], Draw
- CImageList [MFC], DrawEx
- CImageList [MFC], DrawIndirect
- CImageList [MFC], EndDrag
- CImageList [MFC], ExtractIcon
- CImageList [MFC], FromHandle
- CImageList [MFC], FromHandlePermanent
- CImageList [MFC], GetBkColor
- CImageList [MFC], GetDragImage
- CImageList [MFC], GetImageCount
- CImageList [MFC], GetImageInfo
- CImageList [MFC], GetSafeHandle
- CImageList [MFC], Read
- CImageList [MFC], Remove
- CImageList [MFC], Replace
- CImageList [MFC], SetBkColor
- CImageList [MFC], SetDragCursorImage
- CImageList [MFC], SetImageCount
- CImageList [MFC], SetOverlayImage
- CImageList [MFC], Write
- CImageList [MFC], m_hImageList
ms.assetid: b6d1a704-1c82-4548-8a8f-77972adc98a5
ms.openlocfilehash: 1555209ce0f1c2caacbfb4b01107775db948d230
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69505954"
---
# <a name="cimagelist-class"></a>CImageList クラス

Windows コモン イメージ リスト コントロールの機能が用意されています。

## <a name="syntax"></a>構文

```
class CImageList : public CObject
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CImageList:: CImageList](#cimagelist)|`CImageList` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CImageList:: Add](#add)|イメージリストにイメージまたはイメージを追加します。|
|[CImageList:: Attach](#attach)|イメージリストを`CImageList`オブジェクトにアタッチします。|
|[CImageList:: BeginDrag](#begindrag)|イメージのドラッグを開始します。|
|[CImageList:: Copy](#copy)|`CImageList`オブジェクト内のイメージをコピーします。|
|[CImageList:: Create](#create)|イメージリストを初期化し、 `CImageList`オブジェクトにアタッチします。|
|[CImageList::D eleteImageList](#deleteimagelist)|イメージリストを削除します。|
|[CImageList::DeleteTempMap](#deletetempmap)|`FromHandle` によって作成された一時 `CImageList` オブジェクトを削除するために、[CWinApp](../../mfc/reference/cwinapp-class.md) idle time ハンドラーによって呼び出されます。|
|[CImageList::D します。](#detach)|`CImageList`オブジェクトからイメージリストオブジェクトをデタッチし、イメージリストへのハンドルを返します。|
|[CImageList::D ragEnter](#dragenter)|ドラッグ操作中に更新をロックし、指定した位置にドラッグイメージを表示します。|
|[CImageList::D ragLeave](#dragleave)|ウィンドウのロックを解除し、ウィンドウを更新できるようにドラッグイメージを非表示にします。|
|[CImageList::D ragMove](#dragmove)|ドラッグアンドドロップ操作中に、ドラッグされているイメージを移動します。|
|[CImageList::D ragShowNolock](#dragshownolock)|ドラッグ操作中に、ウィンドウをロックせずにドラッグイメージの表示と非表示を切り替えます。|
|[CImageList::D raw](#draw)|ドラッグアンドドロップ操作中にドラッグされるイメージを描画します。|
|[CImageList::D rawEx](#drawex)|指定したデバイスコンテキストでイメージリスト項目を描画します。 関数は、指定された描画スタイルを使用して、指定した色でイメージをブレンドします。|
|[CImageList::D rawIndirect](#drawindirect)|イメージリストからイメージを描画します。|
|[CImageList:: EndDrag](#enddrag)|ドラッグ操作を終了します。|
|[CImageList:: ExtractIcon](#extracticon)|イメージリスト内のイメージとマスクに基づいてアイコンを作成します。|
|[CImageList:: FromHandle](#fromhandle)|イメージリストへのハンドル`CImageList`が指定された場合に、オブジェクトへのポインターを返します。   `CImageList` オブジェクトがハンドルに関連付けられていない場合は、一時的な `CImageList` オブジェクトが生成され、関連付けられます。|
|[CImageList:: FromHandlePermanent](#fromhandlepermanent)|イメージリストへのハンドル`CImageList`が指定された場合に、オブジェクトへのポインターを返します。 `CImageList`オブジェクトがハンドルにアタッチされていない場合は、NULL が返されます。|
|[CImageList:: GetBkColor](#getbkcolor)|イメージリストの現在の背景色を取得します。|
|[CImageList:: GetDragImage](#getdragimage)|ドラッグに使用される一時イメージリストを取得します。|
|[CImageList:: GetImageCount](#getimagecount)|イメージリスト内のイメージの数を取得します。|
|[CImageList:: GetImageInfo](#getimageinfo)|イメージに関する情報を取得します。|
|[CImageList:: GetSafeHandle](#getsafehandle)|を`m_hImageList`取得します。|
|[CImageList:: Read](#read)|アーカイブからイメージリストを読み取ります。|
|[CImageList::Remove](#remove)|イメージリストからイメージを削除します。|
|[CImageList:: Replace](#replace)|イメージリスト内のイメージを新しいイメージに置き換えます。|
|[CImageList:: SetBkColor](#setbkcolor)|イメージリストの背景色を設定します。|
|[CImageList:: Setdragカーソルイメージ](#setdragcursorimage)|新しいドラッグイメージを作成します。|
|[CImageList:: SetImageCount](#setimagecount)|イメージリスト内のイメージの数をリセットします。|
|[CImageList:: SetOverlayImage](#setoverlayimage)|オーバーレイマスクとして使用するイメージの一覧に、イメージの0から始まるインデックスを追加します。|
|[CImageList:: Write](#write)|イメージリストをアーカイブに書き込みます。|

### <a name="public-operators"></a>パブリック演算子

|名前|説明|
|----------|-----------------|
|[CImageList:: operator HIMAGELIST](#operator_himagelist)|にアタッチされている HIMAGELIST を返し`CImageList`ます。|

### <a name="public-data-members"></a>パブリック データ メンバー

|名前|説明|
|----------|-----------------|
|[CImageList:: m_hImageList](#m_himagelist)|このオブジェクトにアタッチされているイメージリストを格納しているハンドル。|

## <a name="remarks"></a>Remarks

"イメージリスト" は、同じサイズのイメージのコレクションであり、それぞれが0から始まるインデックスで参照できます。 イメージリストは、多数のアイコンまたはビットマップのセットを効率的に管理するために使用されます。 イメージリスト内のすべてのイメージは、画面デバイス形式の1つのワイドビットマップに含まれています。 イメージリストには、画像を透過的に描画するために使用されるマスクを含むモノクロビットマップを含めることもできます (アイコンのスタイル)。 Microsoft Win32 アプリケーションプログラミングインターフェイス (API) には、イメージの描画、イメージリストの作成と破棄、イメージの追加と削除、イメージの置換、イメージの結合、イメージのドラッグなどを可能にするイメージリスト関数が用意されています。

このコントロール (および`CImageList`クラス) は、windows 95/98 および windows NT バージョン3.51 以降で実行されているプログラムに対してのみ使用できます。

の使用方法`CImageList`の詳細については、「[コントロール](../../mfc/controls-mfc.md)」および「 [using CImageList](../../mfc/using-cimagelist.md)」を参照してください。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

`CImageList`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="add"></a>  CImageList::Add

イメージリストに1つ以上のイメージまたはアイコンを追加するには、この関数を呼び出します。

```
int Add(
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Add(
    CBitmap* pbmImage,
    COLORREF crMask);

int Add(HICON hIcon);
```

### <a name="parameters"></a>パラメーター

*pbmImage*<br/>
イメージまたはイメージを格納しているビットマップへのポインター。 イメージの数は、ビットマップの幅から推測されます。

*pbmMask*<br/>
マスクを格納しているビットマップへのポインター。 イメージリストでマスクが使用されていない場合、このパラメーターは無視されます。

*crMask*<br/>
マスクの生成に使用される色。 指定されたビットマップ内のこの色の各ピクセルが黒に変更され、マスクの対応するビットが1に設定されます。

*hIcon*<br/>
新しいイメージのビットマップとマスクを含むアイコンのハンドル。

### <a name="return-value"></a>戻り値

成功した場合は、最初の新しいイメージの0から始まるインデックス。それ以外の場合は-1。

### <a name="remarks"></a>Remarks

操作が完了したら、アイコンハンドルを解放する必要があります。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#1](../../mfc/reference/codesnippet/cpp/cimagelist-class_1.cpp)]

##  <a name="attach"></a>CImageList:: Attach

イメージリストを`CImageList`オブジェクトにアタッチするには、この関数を呼び出します。

```
BOOL Attach(HIMAGELIST hImageList);
```

### <a name="parameters"></a>パラメーター

*hImageList*<br/>
イメージリストオブジェクトを表すハンドル。

### <a name="return-value"></a>戻り値

添付ファイルが成功した場合は0以外の。それ以外の場合は0です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#2](../../mfc/reference/codesnippet/cpp/cimagelist-class_2.cpp)]

##  <a name="begindrag"></a>CImageList:: BeginDrag

イメージのドラッグを開始するには、この関数を呼び出します。

```
BOOL BeginDrag(
    int nImage,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>パラメーター

*nImage*<br/>
ドラッグするイメージの0から始まるインデックス。

*ptHotSpot*<br/>
開始するドラッグ位置 (通常はカーソル位置) の座標。 座標は、イメージの左上隅を基準としています。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

この関数は、ドラッグに使用される一時イメージリストを作成します。 イメージは、指定されたイメージとそのマスクを現在のカーソルと結合します。 後続の WM_MOUSEMOVE メッセージに応答して、 `DragMove`メンバー関数を使用してドラッグイメージを移動できます。 ドラッグ操作を終了するには、 `EndDrag`メンバー関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#3](../../mfc/reference/codesnippet/cpp/cimagelist-class_3.cpp)]

##  <a name="cimagelist"></a>CImageList:: CImageList

`CImageList` オブジェクトを構築します。

```
CImageList();
```

##  <a name="copy"></a>  CImageList::Copy

このメンバー関数は、Windows SDK で説明されているように、Win32 関数[ImageList_Copy](/windows/win32/api/commctrl/nf-commctrl-imagelist_copy)の動作を実装します。

```
BOOL Copy(
    int iDst,
    int iSrc,
    UINT uFlags = ILCF_MOVE);

BOOL Copy(
    int iDst,
    CImageList* pSrc,
    int iSrc,
    UINT uFlags = ILCF_MOVE);
```

### <a name="parameters"></a>パラメーター

*iDst*<br/>
コピー操作のコピー先として使用されるイメージの、0から始まるインデックス。

*iSrc*<br/>
コピー操作のソースとして使用されるイメージの0から始まるインデックス。

*uFlags*<br/>
作成するコピー操作の種類を指定するビットフラグ値。 このパラメーターには、次のいずれかの値を指定できます。

|[値]|説明|
|-----------|-------------|
|ILCF_MOVE|ソースイメージがコピー先のイメージのインデックスにコピーされます。 この操作により、特定のイメージの複数のインスタンスが生成されます。 既定値は ILCF_MOVE です。|
|ILCF_SWAP|ソースとターゲットのイメージは、イメージリスト内での位置を交換します。|

*.Psrc*<br/>
コピー操作の対象`CImageList`であるオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#6](../../mfc/reference/codesnippet/cpp/cimagelist-class_4.cpp)]

##  <a name="create"></a>CImageList:: Create

イメージリストを初期化し、それを[CImageList](../../mfc/reference/cimagelist-class.md)オブジェクトにアタッチします。

```
BOOL Create(
    int cx,
    int cy,
    UINT nFlags,
    int nInitial,
    int nGrow);

BOOL Create(
    UINT nBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    LPCTSTR lpszBitmapID,
    int cx,
    int nGrow,
    COLORREF crMask);

BOOL Create(
    CImageList& imagelist1,
    int nImage1,
    CImageList& imagelist2,
    int nImage2,
    int dx,
    int dy);

BOOL Create(CImageList* pImageList);
```

### <a name="parameters"></a>パラメーター

*cx*<br/>
各イメージの大きさ (ピクセル単位)。

*暦年*<br/>
各イメージの大きさ (ピクセル単位)。

*nFlags*<br/>
作成するイメージリストの種類を指定します。 このパラメーターは、次の値の組み合わせにすることができますが、 `ILC_COLOR`値を1つだけ含めることができます。

|[値]|説明|
|-----------|-------------|
|ILC_COLOR|他の ILC_COLOR * フラグが指定されていない場合は、既定の動作を使用します。 通常、既定値は ILC_COLOR4 です。ただし、古いディスプレイドライバーの場合、既定値は ILC_COLORDDB です。|
|ILC_COLOR4|イメージリストのビットマップとして、4ビット (16 色) のデバイスに依存しないビットマップ (DIB) セクションを使用します。|
|ILC_COLOR8|8ビットの DIB セクションを使用します。 カラーテーブルに使用される色は、ハーフトーンパレットと同じ色です。|
|ILC_COLOR16|16ビット (32/64k 色) の DIB セクションを使用します。|
|ILC_COLOR24|24ビットの DIB セクションを使用します。|
|ILC_COLOR32|32ビットの DIB セクションを使用します。|
|ILC_COLORDDB|デバイスに依存するビットマップを使用します。|
|ILC_MASK|マスクを使用します。 イメージリストには、2つのビットマップが含まれています。1つは、マスクとして使用されるモノクロビットマップです。 この値が含まれていない場合、イメージリストにはビットマップが1つだけ含まれます。 マスクされた画像の詳細については[、「イメージリストの](../../mfc/drawing-images-from-an-image-list.md)イメージの描画」を参照してください。|

*nInitial*<br/>
イメージリストに初期状態で含まれているイメージの数。

*nGrow*<br/>
新しいイメージのための領域を確保するためにシステムでリストのサイズを変更する必要がある場合に、イメージの一覧を拡張できるイメージの数。 このパラメーターは、サイズ変更されたイメージリストに含めることができる新しいイメージの数を表します。

*nBitmapID*<br/>
イメージリストに関連付けられるビットマップのリソース Id。

*crMask*<br/>
マスクの生成に使用される色。 指定したビットマップのこの色のピクセルが黒に変更され、マスクの対応するビットが1に設定されます。

*lpszBitmapID*<br/>
イメージのリソース Id を格納している文字列。

*imagelist1*<br/>
`CImageList` オブジェクトへの参照。

*nImage1*<br/>
最初の既存のイメージのインデックス。

*imagelist2*<br/>
`CImageList` オブジェクトへの参照。

*nImage2*<br/>
2番目の既存のイメージのインデックス。

*dx*<br/>
最初のイメージとの関係における2番目のイメージの x 軸のオフセット (ピクセル単位)。

*dy*<br/>
最初のイメージとの関係における2番目のイメージの y 軸のオフセット (ピクセル単位)。

*pImageList*<br/>
`CImageList` オブジェクトへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

を作成する`CImageList`には、2つの手順を実行します。 まず、コンストラクターを呼び出し、次に`Create`を呼び出します。これにより、イメージリストが`CImageList`作成され、オブジェクトにアタッチされます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#7](../../mfc/reference/codesnippet/cpp/cimagelist-class_5.cpp)]

##  <a name="deleteimagelist"></a>  CImageList::DeleteImageList

イメージリストを削除するには、この関数を呼び出します。

```
BOOL DeleteImageList();
```

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#8](../../mfc/reference/codesnippet/cpp/cimagelist-class_6.cpp)]

##  <a name="deletetempmap"></a>  CImageList::DeleteTempMap

`CWinApp`アイドルタイムハンドラーによって自動的に呼び出さ`DeleteTempMap`れ、 [FromHandle](#fromhandle)によって作成された一時`hImageList` `CImageList`オブジェクトを削除しますが、一時的に`ImageList`関連付けられているハンドル () を破棄しません。表す.

```
static void PASCAL DeleteTempMap();
```

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#9](../../mfc/reference/codesnippet/cpp/cimagelist-class_7.cpp)]

##  <a name="detach"></a>CImageList::D します。

`CImageList`オブジェクトからイメージリストオブジェクトをデタッチするには、この関数を呼び出します。

```
HIMAGELIST Detach();
```

### <a name="return-value"></a>戻り値

イメージリストオブジェクトを表すハンドル。

### <a name="remarks"></a>Remarks

この関数は、イメージリストオブジェクトへのハンドルを返します。

### <a name="example"></a>例

  「 [CImageList:: Attach](#attach)」の例を参照してください。

##  <a name="dragenter"></a>CImageList::D ragEnter

ドラッグ操作中、は*pWndLock*によって指定されたウィンドウへの更新をロックし、*ポイント*で指定された位置にドラッグイメージを表示します。

```
static BOOL PASCAL DragEnter(
    CWnd* pWndLock,
    CPoint point);
```

### <a name="parameters"></a>パラメーター

*pWndLock*<br/>
ドラッグイメージを所有するウィンドウへのポインター。

*視点*<br/>
ドラッグイメージを表示する位置。 座標は、ウィンドウの左上隅を基準とした相対値です (クライアント領域ではありません)。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

座標はウィンドウの左上隅に対して相対的であるため、座標を指定するときに、境界線、タイトルバー、メニューバーなどのウィンドウ要素の幅を補正する必要があります。

*PWndLock*が NULL の場合、この関数はデスクトップウィンドウに関連付けられた表示コンテキストでイメージを描画します。座標は画面の左上隅を基準としています。

この関数は、ドラッグ操作中に、指定されたウィンドウに対する他のすべての更新をロックします。 ドラッグアンドドロップ操作の対象を強調表示するなど、ドラッグ操作中に描画を行う必要がある場合は、 [CImageList::D ragleave](#dragleave)関数を使用して、ドラッグしたイメージを一時的に非表示にすることができます。

### <a name="example"></a>例

  「 [CImageList:: BeginDrag](#begindrag)」の例を参照してください。

##  <a name="dragleave"></a>CImageList::D ragLeave

*PWndLock*で指定されたウィンドウのロックを解除し、ドラッグイメージを非表示にして、ウィンドウを更新できるようにします。

```
static BOOL PASCAL DragLeave(CWnd* pWndLock);
```

### <a name="parameters"></a>パラメーター

*pWndLock*<br/>
ドラッグイメージを所有するウィンドウへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

  「 [CImageList:: EndDrag](#enddrag)」の例を参照してください。

##  <a name="dragmove"></a>CImageList::D ragMove

ドラッグアンドドロップ操作中にドラッグされているイメージを移動するには、この関数を呼び出します。

```
static BOOL PASCAL DragMove(CPoint pt);
```

### <a name="parameters"></a>パラメーター

*未満*<br/>
新しいドラッグ位置。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

通常、この関数は、WM_MOUSEMOVE メッセージに応答して呼び出されます。 ドラッグ操作を開始するには、 `BeginDrag`メンバー関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#4](../../mfc/reference/codesnippet/cpp/cimagelist-class_8.cpp)]

##  <a name="dragshownolock"></a>CImageList::D ragShowNolock

ドラッグ操作中に、ウィンドウをロックせずにドラッグイメージの表示と非表示を切り替えます。

```
static BOOL PASCAL DragShowNolock(BOOL bShow);
```

### <a name="parameters"></a>パラメーター

*bShow*<br/>
ドラッグイメージを表示するかどうかを指定します。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

[CImageList::D ragenter](#dragenter)関数は、ドラッグ操作中にウィンドウに対するすべての更新をロックします。 ただし、この関数ではウィンドウはロックされません。

##  <a name="draw"></a>CImageList::D raw

ドラッグアンドドロップ操作中にドラッグされるイメージを描画するには、この関数を呼び出します。

```
BOOL Draw(
    CDC* pDC,
    int nImage,
    POINT pt,
    UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
宛先デバイスコンテキストへのポインター。

*nImage*<br/>
描画するイメージの0から始まるインデックス。

*未満*<br/>
指定したデバイスコンテキスト内で描画する位置。

*nStyle*<br/>
描画スタイルを指定するフラグ。 次の値の1つ以上を指定できます。

|[値]|説明|
|-----------|-------------|
|ILD_BLEND25, ILD_FOCUS|システムの強調表示色で 25% をブレンドしてイメージを描画します。 この値は、イメージリストにマスクが含まれていない場合は効果がありません。|
|ILD_BLEND50, ILD_SELECTED, ILD_BLEND|イメージを描画し、システムの強調表示色で 50% をブレンドします。 この値は、イメージリストにマスクが含まれていない場合は効果がありません。|
|ILD_MASK|マスクを描画します。|
|ILD_NORMAL|イメージリストの背景色を使用してイメージを描画します。 背景色が CLR_NONE 値の場合、画像はマスクを使用して透過的に描画されます。|
|ILD_TRANSPARENT|背景色に関係なく、マスクを使用して画像を透過的に描画します。|

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

  「 [CImageList:: SetOverlayImage](#setoverlayimage)」の例を参照してください。

##  <a name="drawex"></a>CImageList::D rawEx

指定したデバイスコンテキストでイメージリスト項目を描画します。

```
BOOL DrawEx(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    COLORREF clrBk,
    COLORREF clrFg,
    UINT nStyle);
```

### <a name="parameters"></a>パラメーター

*pDC*<br/>
宛先デバイスコンテキストへのポインター。

*nImage*<br/>
描画するイメージの0から始まるインデックス。

*未満*<br/>
指定したデバイスコンテキスト内で描画する位置。

*sz*<br/>
イメージの左上隅を基準として描画するイメージの部分のサイズ。 Windows SDK の「 *dx* and *dy* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) 」を参照してください。

*clrBk*<br/>
画像の背景色。 Windows SDK の[ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)の*rgbBk*を参照してください。

*clrFg*<br/>
イメージの前景色。 Windows SDK の[ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex)の*rgbFg*を参照してください。

*nStyle*<br/>
描画スタイルを指定するフラグ。 Windows SDK の「 *Fstyle* in [ImageList_DrawEx](/windows/win32/api/commctrl/nf-commctrl-imagelist_drawex) 」を参照してください。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

関数は、指定された描画スタイルを使用して、指定した色でイメージをブレンドします。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#10](../../mfc/reference/codesnippet/cpp/cimagelist-class_9.cpp)]

##  <a name="drawindirect"></a>CImageList::D rawIndirect

イメージリストからイメージを描画するには、このメンバー関数を呼び出します。

```
BOOL DrawIndirect(IMAGELISTDRAWPARAMS* pimldp);

BOOL DrawIndirect(
    CDC* pDC,
    int nImage,
    POINT pt,
    SIZE sz,
    POINT ptOrigin,
    UINT fStyle = ILD_NORMAL,
    DWORD dwRop = SRCCOPY,
    COLORREF rgbBack = CLR_DEFAULT,
    COLORREF rgbFore = CLR_DEFAULT,
    DWORD fState = ILS_NORMAL,
    DWORD Frame = 0,
    COLORREF crEffect = CLR_DEFAULT);
```

### <a name="parameters"></a>パラメーター

*pimldp*<br/>
描画操作に関する情報を格納している[Imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)構造体へのポインター。

*pDC*<br/>
宛先デバイスコンテキストへのポインター。 作業が終わったら、この[CDC](../../mfc/reference/cdc-class.md)オブジェクトを削除する必要があります。

*nImage*<br/>
描画するイメージの0から始まるインデックス。

*未満*<br/>
イメージが描画される x 座標と y 座標を格納している[ポイント](/previous-versions/dd162805\(v=vs.85\))構造体。

*sz*<br/>
描画するイメージのサイズを示す[サイズ](/windows/win32/api/windef/ns-windef-size)構造体。

*ptOrigin*<br/>
イメージ自体に対する描画操作の左上隅を指定する x 座標と y 座標を格納している[ポイント](/previous-versions/dd162805\(v=vs.85\))構造体。 X 座標と y 座標の左上にあるイメージのピクセルは描画されません。

*fStyle*<br/>
描画スタイルと、必要に応じてオーバーレイイメージを指定するフラグです。 オーバーレイイメージの詳細については、「解説」を参照してください。 MFC の既定の実装である ILD_NORMAL は、イメージリストの背景色を使用してイメージを描画します。 背景色が CLR_NONE 値の場合、画像はマスクを使用して透過的に描画されます。

その他の使用可能なスタイルについては、 [Imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)構造体の*fstyle*メンバーで説明されています。

*dwRop*<br/>
ラスター操作コードを指定する値。 これらのコードは、コピー元の四角形の色データを変換先の四角形の色データと結合して最終的な色を実現する方法を定義します。 MFC の既定の実装である SRCCOPY は、コピー元の四角形をコピー先の四角形に直接コピーします。 *Fstyle*パラメーターに ILD_ROP フラグが含まれていない場合、このパラメーターは無視されます。

その他の有効な値については、 [Imagelistdrawparams](/windows/win32/api/commctrl/ns-commctrl-imagelistdrawparams)構造体の*dwRop*メンバーに記載されています。

*rgbBack*<br/>
イメージの背景色 (既定では CLR_DEFAULT)。 このパラメーターには、アプリケーション定義の RGB 値または次の値のいずれかを指定できます。

|[値]|説明|
|-----------|-------------|
|CLR_DEFAULT|既定の背景色。 イメージは、イメージリストの背景色を使用して描画されます。|
|CLR_NONE|背景色はありません。 画像は透過的に描画されます。|

*rgbFore*<br/>
画像の前景色 (既定では CLR_DEFAULT)。 このパラメーターには、アプリケーション定義の RGB 値または次の値のいずれかを指定できます。

|[値]|説明|
|-----------|-------------|
|CLR_DEFAULT|既定の前景色。 イメージは、システムの強調表示の色を前景色として使用して描画されます。|
|CLR_NONE|Blend の色はありません。 イメージは、変換先デバイスコンテキストの色とブレンドされます。|

このパラメーターは、 *Fstyle*に ILD_BLEND25 または ILD_BLEND50 フラグが含まれている場合にのみ使用されます。

*fState*<br/>
描画状態を指定するフラグ。 このメンバーには、1つまたは複数のイメージリスト状態フラグを含めることができます。

*Frame*<br/>
彩度とアルファブレンディング効果の動作に影響します。

ILS_SATURATE と共に使用する場合、このメンバーは、アイコン内の各ピクセルの RGB の各色コンポーネントに追加される値を保持します。

ILS_APLHA と共に使用する場合、このメンバーはアルファチャネルの値を保持します。 この値には 0 ~ 255 の値を指定できます。0は完全に透明で、255は完全に不透明です。

*crEffect*<br/>
光彩および影効果に使用される[COLORREF](/windows/win32/gdi/colorref)値。

### <a name="return-value"></a>戻り値

イメージが正常に描画された場合は TRUE。それ以外の場合は FALSE。

### <a name="remarks"></a>Remarks

Win32 構造体を自分で入力する場合は、最初のバージョンを使用します。 1つ以上の MFC の既定の引数を利用する場合、または構造の管理を避ける場合は、2番目のバージョンを使用します。

オーバーレイイメージは、このメンバー関数で*nimage*パラメーターによって指定されたプライマリイメージの上に描画されるイメージです。 [INDEXTOOVERLAYMASK](/windows/win32/api/commctrl/nf-commctrl-indextooverlaymask)マクロを使用して指定されたオーバーレイマスクの1から始まるインデックスを持つ[描画](#draw)メンバー関数を使用して、オーバーレイマスクを描画します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#11](../../mfc/reference/codesnippet/cpp/cimagelist-class_10.cpp)]

##  <a name="enddrag"></a>CImageList:: EndDrag

ドラッグ操作を終了するには、この関数を呼び出します。

```
static void PASCAL EndDrag();
```

### <a name="remarks"></a>Remarks

ドラッグ操作を開始するには、 `BeginDrag`メンバー関数を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#5](../../mfc/reference/codesnippet/cpp/cimagelist-class_11.cpp)]

##  <a name="extracticon"></a>CImageList:: ExtractIcon

イメージリスト内のイメージとそれに関連するマスクに基づいてアイコンを作成するには、この関数を呼び出します。

```
HICON ExtractIcon(int nImage);
```

### <a name="parameters"></a>パラメーター

*nImage*<br/>
イメージの0から始まるインデックス。

### <a name="return-value"></a>戻り値

成功した場合は、アイコンのハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

このメソッドは、アイコンを作成するための[ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)マクロの動作に依存します。 アイコンの作成とクリーンアップの詳細については、 [ImageList_ExtractIcon](/windows/win32/api/commctrl/nf-commctrl-imagelist_extracticon)マクロを参照してください。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#12](../../mfc/reference/codesnippet/cpp/cimagelist-class_12.cpp)]

##  <a name="fromhandle"></a>CImageList:: FromHandle

イメージリストへのハンドル`CImageList`が指定された場合に、オブジェクトへのポインターを返します。

```
static CImageList* PASCAL FromHandle(HIMAGELIST hImageList);
```

### <a name="parameters"></a>パラメーター

*hImageList*<br/>
イメージリストを指定します。

### <a name="return-value"></a>戻り値

成功した場合`CImageList`はオブジェクトへのポインター、それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

がハンドルにまだアタッチされていない場合は`CImageList` 、一時オブジェクトが作成され、アタッチされます。 `CImageList` この一時`CImageList`オブジェクトは、アプリケーションが次にそのイベントループ内でアイドル状態になるまで有効です。その時点で、すべての一時オブジェクトが削除されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#13](../../mfc/reference/codesnippet/cpp/cimagelist-class_13.cpp)]

##  <a name="fromhandlepermanent"></a>CImageList:: FromHandlePermanent

イメージリストへのハンドル`CImageList`が指定された場合に、オブジェクトへのポインターを返します。

```
static CImageList* PASCAL FromHandlePermanent(HIMAGELIST hImageList);
```

### <a name="parameters"></a>パラメーター

*hImageList*<br/>
イメージリストを指定します。

### <a name="return-value"></a>戻り値

成功した場合`CImageList`はオブジェクトへのポインター、それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

`CImageList`オブジェクトがハンドルにアタッチされていない場合は、NULL が返されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#14](../../mfc/reference/codesnippet/cpp/cimagelist-class_14.cpp)]

##  <a name="getbkcolor"></a>CImageList:: GetBkColor

イメージリストの現在の背景色を取得するには、この関数を呼び出します。

```
COLORREF GetBkColor() const;
```

### <a name="return-value"></a>戻り値

`CImageList`オブジェクトの背景色の RGB カラー値。

### <a name="example"></a>例

  「 [CImageList:: SetBkColor](#setbkcolor)」の例を参照してください。

##  <a name="getdragimage"></a>CImageList:: GetDragImage

ドラッグに使用される一時イメージリストを取得します。

```
static CImageList* PASCAL GetDragImage(
    LPPOINT lpPoint,
    LPPOINT lpPointHotSpot);
```

### <a name="parameters"></a>パラメーター

*lpPoint*<br/>
現在のドラッグ位置を受け取る[ポイント](/previous-versions/dd162805\(v=vs.85\))構造のアドレス。

*lpPointHotSpot*<br/>
ドラッグ位置に`POINT`対して相対的なドラッグイメージのオフセットを受け取る構造体のアドレス。

### <a name="return-value"></a>戻り値

正常に終了した場合は、ドラッグに使用される一時イメージリストへのポインター。それ以外の場合は NULL。

##  <a name="getimagecount"></a>  CImageList::GetImageCount

イメージリスト内のイメージの数を取得するには、この関数を呼び出します。

```
int GetImageCount() const;
```

### <a name="return-value"></a>戻り値

イメージの数。

### <a name="example"></a>例

  「 [CImageList:: ExtractIcon](#extracticon)」の例を参照してください。

##  <a name="getimageinfo"></a>CImageList:: GetImageInfo

イメージに関する情報を取得するには、この関数を呼び出します。

```
BOOL GetImageInfo(
    int nImage,
    IMAGEINFO* pImageInfo) const;
```

### <a name="parameters"></a>パラメーター

*nImage*<br/>
イメージの0から始まるインデックス。

*pImageInfo*<br/>
イメージに関する情報を受け取る[IMAGEINFO](/windows/win32/api/commctrl/ns-commctrl-imageinfo)構造体へのポインター。 この構造体の情報は、イメージのビットマップを直接操作するために使用できます。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

`IMAGEINFO`構造体には、イメージリスト内のイメージに関する情報が含まれます。

##  <a name="getsafehandle"></a>CImageList:: GetSafeHandle

データメンバーを取得するに`m_hImageList`は、この関数を呼び出します。

```
HIMAGELIST GetSafeHandle() const;
```

### <a name="return-value"></a>戻り値

アタッチされたイメージリストへのハンドル。それ以外の場合は、オブジェクトがアタッチされていない場合は NULL です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#15](../../mfc/reference/codesnippet/cpp/cimagelist-class_15.cpp)]

##  <a name="m_himagelist"></a>CImageList:: m_hImageList

このオブジェクトにアタッチされているイメージリストのハンドル。

`HIMAGELIST m_hImageList;`

### <a name="remarks"></a>Remarks

この`m_hImageList`データメンバーは、himagelist 型のパブリック変数です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#23](../../mfc/reference/codesnippet/cpp/cimagelist-class_16.cpp)]

##  <a name="operator_himagelist"></a>CImageList:: operator HIMAGELIST

`CImageList`オブジェクトのアタッチされたハンドルを取得するには、この演算子を使用します。

```
operator HIMAGELIST() const;
```

### <a name="return-value"></a>戻り値

成功した場合は、 `CImageList`オブジェクトによって表されるイメージリストへのハンドル。それ以外の場合は NULL。

### <a name="remarks"></a>Remarks

この演算子は、HIMAGELIST オブジェクトの直接使用をサポートするキャスト演算子です。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#16](../../mfc/reference/codesnippet/cpp/cimagelist-class_17.cpp)]

##  <a name="read"></a>  CImageList::Read

アーカイブからイメージリストを読み取るには、この関数を呼び出します。

```
BOOL Read(CArchive* pArchive);
```

### <a name="parameters"></a>パラメーター

*pArchive*<br/>
イメージリストの読み取り`CArchive`元となるオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#18](../../mfc/reference/codesnippet/cpp/cimagelist-class_18.cpp)]

##  <a name="remove"></a>  CImageList::Remove

イメージリストオブジェクトからイメージを削除するには、この関数を呼び出します。

```
BOOL Remove(int nImage);
```

### <a name="parameters"></a>パラメーター

*nImage*<br/>
削除するイメージの0から始まるインデックス。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

*N イメージ*の後にあるすべての項目が1つ下に移動します。 たとえば、イメージリストに2つの項目が含まれている場合、最初の項目を削除すると、残りの項目が最初の位置になります。 最初の位置の項目については、 *Nimage*= 0 を使用します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#19](../../mfc/reference/codesnippet/cpp/cimagelist-class_19.cpp)]

##  <a name="replace"></a>  CImageList::Replace

イメージリスト内のイメージを新しいイメージに置き換えるには、この関数を呼び出します。

```
BOOL Replace(
    int nImage,
    CBitmap* pbmImage,
    CBitmap* pbmMask);

int Replace(
    int nImage,
    HICON hIcon);
```

### <a name="parameters"></a>パラメーター

*nImage*<br/>
置換するイメージの0から始まるインデックス。

*pbmImage*<br/>
イメージを格納しているビットマップへのポインター。

*pbmMask*<br/>
マスクを格納しているビットマップへのポインター。 イメージリストでマスクが使用されていない場合、このパラメーターは無視されます。

*hIcon*<br/>
新しいイメージのビットマップとマスクを格納しているアイコンへのハンドル。

### <a name="return-value"></a>戻り値

成功した場合、BOOL を返すバージョンは0以外の値を返します。それ以外の場合は0です。

**Int**を返すバージョンは、成功した場合、イメージの0から始まるインデックスを返します。それ以外の場合は-1。

### <a name="remarks"></a>Remarks

[SetImageCount](#setimagecount)を呼び出した後にこのメンバー関数を呼び出して、新しい有効なイメージをプレースホルダーイメージのインデックス番号に割り当てます。

### <a name="example"></a>例

  「 [CImageList:: SetImageCount](#setimagecount)」の例を参照してください。

##  <a name="setbkcolor"></a>CImageList:: SetBkColor

イメージリストの背景色を設定するには、この関数を呼び出します。

```
COLORREF SetBkColor(COLORREF cr);
```

### <a name="parameters"></a>パラメーター

*リターン*<br/>
設定する背景色。 CLR_NONE することができます。 その場合、画像はマスクを使用して透過的に描画されます。

### <a name="return-value"></a>戻り値

成功した場合は、前の背景色。それ以外の場合は CLR_NONE。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#20](../../mfc/reference/codesnippet/cpp/cimagelist-class_20.cpp)]

##  <a name="setdragcursorimage"></a>CImageList:: Setdragカーソルイメージ

指定されたイメージ (通常はマウスカーソルイメージ) と現在のドラッグイメージを組み合わせて、新しいドラッグイメージを作成します。

```
BOOL SetDragCursorImage(
    int nDrag,
    CPoint ptHotSpot);
```

### <a name="parameters"></a>パラメーター

*nDrag*<br/>
ドラッグイメージと結合する新しいイメージのインデックス。

*ptHotSpot*<br/>
新しいイメージ内のホットスポットの位置。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

ドラッグ関数ではドラッグ操作中に新しいイメージが使用されるため、`CImageList::SetDragCursorImage` を呼び出した後、Windows の [ShowCursor](/windows/win32/api/winuser/nf-winuser-showcursor) 関数を使用して、実際のマウスカーソルを非表示にする必要があります。 それ以外の場合、ドラッグ操作の間、システムには2つのマウスカーソルが表示されることがあります。

##  <a name="setimagecount"></a>CImageList:: SetImageCount

このメンバー関数を呼び出して、 `CImageList`オブジェクト内のイメージの数をリセットします。

```
BOOL SetImageCount(UINT uNewCount);
```

### <a name="parameters"></a>パラメーター

*uNewCount*<br/>
イメージリスト内のイメージの新しい合計数を指定する値。

### <a name="return-value"></a>戻り値

成功した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

このメンバー関数を呼び出してイメージリスト内のイメージの数を増やす場合は、追加のイメージごとに[Replace](#replace)を呼び出して、新しいインデックスを有効なイメージに割り当てます。 有効なイメージにインデックスを割り当てられなかった場合、新しいイメージを作成する描画操作は予測できません。

この関数を使用してイメージリストのサイズを小さくすると、切り捨てられたイメージが解放されます。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#21](../../mfc/reference/codesnippet/cpp/cimagelist-class_21.cpp)]

##  <a name="setoverlayimage"></a>CImageList:: SetOverlayImage

イメージの0から始まるインデックスをオーバーレイマスクとして使用するイメージの一覧に追加するには、この関数を呼び出します。

```
BOOL SetOverlayImage(
    int nImage,
    int nOverlay);
```

### <a name="parameters"></a>パラメーター

*nImage*<br/>
オーバーレイマスクとして使用するイメージの0から始まるインデックス。

*nOverlay*<br/>
オーバーレイマスクの1から始まるインデックス。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="remarks"></a>Remarks

最大4つのインデックスを一覧に追加できます。

オーバーレイマスクは、別のイメージに対して透過的に描画されるイメージです。 INDEXTOOVERLAYMASK マクロを使用して指定されたオーバーレイマスクの1から始まるインデックスを持つ[CImageList::D raw](#draw)メンバー関数を使用して、イメージにオーバーレイマスクを描画します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#22](../../mfc/reference/codesnippet/cpp/cimagelist-class_22.cpp)]

##  <a name="write"></a>CImageList:: Write

イメージリストオブジェクトをアーカイブに書き込むには、この関数を呼び出します。

```
BOOL Write(CArchive* pArchive);
```

### <a name="parameters"></a>パラメーター

*pArchive*<br/>
イメージリストを格納`CArchive`するオブジェクトへのポインター。

### <a name="return-value"></a>戻り値

正常終了した場合は 0 以外を返します。それ以外の場合は 0 を返します。

### <a name="example"></a>例

[!code-cpp[NVC_MFC_CImageList#17](../../mfc/reference/codesnippet/cpp/cimagelist-class_23.cpp)]

## <a name="see-also"></a>関連項目

[CObject クラス](../../mfc/reference/cobject-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CListCtrl クラス](../../mfc/reference/clistctrl-class.md)<br/>
[CTabCtrl クラス](../../mfc/reference/ctabctrl-class.md)
