---
title: CDragListBox クラス
ms.date: 11/04/2016
f1_keywords:
- CDragListBox
- AFXCMN/CDragListBox
- AFXCMN/CDragListBox::CDragListBox
- AFXCMN/CDragListBox::BeginDrag
- AFXCMN/CDragListBox::CancelDrag
- AFXCMN/CDragListBox::Dragging
- AFXCMN/CDragListBox::DrawInsert
- AFXCMN/CDragListBox::Dropped
- AFXCMN/CDragListBox::ItemFromPt
helpviewer_keywords:
- CDragListBox [MFC], CDragListBox
- CDragListBox [MFC], BeginDrag
- CDragListBox [MFC], CancelDrag
- CDragListBox [MFC], Dragging
- CDragListBox [MFC], DrawInsert
- CDragListBox [MFC], Dropped
- CDragListBox [MFC], ItemFromPt
ms.assetid: fee20b42-60ae-4aa9-83f9-5a3d9b96e33b
ms.openlocfilehash: d8afc5b14f5f52ca7a4d28a3d3c3c5440b7c819f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164047"
---
# <a name="cdraglistbox-class"></a>CDragListBox クラス

Windows は、リスト ボックスの機能を提供するだけでなく、`CDragListBox`クラスは、リスト ボックス内でファイル名など、リスト ボックス アイテムを移動するユーザーを使用できます。

## <a name="syntax"></a>構文

```
class CDragListBox : public CListBox
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CDragListBox::CDragListBox](#cdraglistbox)|`CDragListBox` オブジェクトを構築します。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|[CDragListBox::BeginDrag](#begindrag)|ドラッグ操作を開始するときに、フレームワークによって呼び出されます。|
|[CDragListBox::CancelDrag](#canceldrag)|ドラッグ操作が取り消されたときに、フレームワークによって呼び出されます。|
|[CDragListBox::Dragging](#dragging)|ドラッグ操作中に、フレームワークによって呼び出されます。|
|[CDragListBox::DrawInsert](#drawinsert)|ドラッグ リスト ボックスの挿入ガイドを描画します。|
|[CDragListBox::Dropped](#dropped)|項目がドロップされた後に、フレームワークによって呼び出されます。|
|[CDragListBox::ItemFromPt](#itemfrompt)|ドラッグされている項目の座標を返します。|

## <a name="remarks"></a>Remarks

この機能を持つリスト ボックスには、任意の方法が最も役に立つことで、一覧内の項目の並べ替えにユーザーができるようにします。 既定では、リスト ボックスは、リスト内の新しい場所に、項目を移動することにします。 ただし、`CDragListBox`に移動する代わりに項目をコピーするオブジェクトをカスタマイズできます。

リスト ボックス コントロールに関連付けられている、`CDragListBox`な LBS_SORT または LBS_MULTIPLESELECT スタイル クラスが必要ありません。 リスト ボックスのスタイルの説明は、次を参照してください。[リスト ボックス スタイル](../../mfc/reference/styles-used-by-mfc.md#list-box-styles)します。

アプリケーションの既存のダイアログ ボックスでのドラッグ リスト ボックスを使用するダイアログ エディターを使用して、ダイアログ テンプレートをリスト ボックス コントロールを追加し、メンバー変数を割り当てる (カテゴリの`Control`変数型と`CDragListBox`)、リスト ボックスに対応します。ダイアログ テンプレートを制御します。

コントロールをメンバー変数に割り当てる方法に関する詳細については、次を参照してください。[ダイアログ コントロールのメンバー変数を定義するためのショートカット](../../windows/defining-member-variables-for-dialog-controls.md)します。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CListBox](../../mfc/reference/clistbox-class.md)

`CDragListBox`

## <a name="requirements"></a>必要条件

**ヘッダー:** afxcmn.h

##  <a name="begindrag"></a>  CDragListBox::BeginDrag

メソッドを呼び出して、イベントが発生したときに、フレームワークがマウスの左ボタンを押すなどのドラッグ操作を開始します。

```
virtual BOOL BeginDrag(CPoint pt);
```

### <a name="parameters"></a>パラメーター

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)ドラッグされている項目の座標を格納しているオブジェクト。

### <a name="return-value"></a>戻り値

ドラッグすることができる場合、それ以外の場合 0 0 以外の値。

### <a name="remarks"></a>Remarks

ドラッグ操作が開始されるときの動作を制御する場合は、この関数をオーバーライドします。 既定の実装では、マウスをキャプチャし、ユーザーがマウスの左または右ボタンをクリックしてまたはドラッグ操作が取り消された時点で、esc キーを押すまでドラッグ モードのままです。

##  <a name="canceldrag"></a>  CDragListBox::CancelDrag

ドラッグ操作が取り消されたときに、フレームワークによって呼び出されます。

```
virtual void CancelDrag(CPoint pt);
```

### <a name="parameters"></a>パラメーター

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)ドラッグされている項目の座標を格納しているオブジェクト。

### <a name="remarks"></a>Remarks

この関数をリスト ボックス コントロールの特別な処理をオーバーライドします。

##  <a name="cdraglistbox"></a>  CDragListBox::CDragListBox

`CDragListBox` オブジェクトを構築します。

```
CDragListBox();
```

##  <a name="dragging"></a>  CDragListBox::Dragging

内でリスト ボックスの項目がドラッグされているときに、フレームワークによって呼び出されます、`CDragListBox`オブジェクト。

```
virtual UINT Dragging(CPoint pt);
```

### <a name="parameters"></a>パラメーター

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)オブジェクト x と y を含む画面、カーソルの座標。

### <a name="return-value"></a>戻り値

表示されるカーソルのリソース ID。 次の値が考えられます。

- DL_COPYCURSOR では、項目がコピーされることを示します。

- は、項目が移動されることを示します。

- DL_STOPCURSOR では、現在のドロップ ターゲットが許容されないことを示します。

### <a name="remarks"></a>Remarks

既定の動作でを返します。 追加機能を提供する場合は、この関数をオーバーライドします。

##  <a name="drawinsert"></a>  CDragListBox::DrawInsert

指定されたインデックスで項目の前に挿入ガイドを描画するためにフレームワークによって呼び出されます。

```
virtual void DrawInsert(int nItem);
```

### <a name="parameters"></a>パラメーター

*nItem*<br/>
カーソル位置の 0 から始まるインデックス。

### <a name="remarks"></a>Remarks

値 - 1 は、挿入ガイドをクリアします。 表示または挿入ガイドの動作を変更するには、この関数をオーバーライドします。

##  <a name="dropped"></a>  CDragListBox::Dropped

内の項目が削除されるときに、フレームワークによって呼び出されます、`CDragListBox`オブジェクト。

```
virtual void Dropped(
    int nSrcIndex,
    CPoint pt);
```

### <a name="parameters"></a>パラメーター

*nSrcIndex*<br/>
削除された文字列の 0 から始まるインデックスを指定します。

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)ドロップ サイトの座標を格納しているオブジェクト。

### <a name="remarks"></a>Remarks

既定の動作は、リスト ボックスの項目とそのデータを新しい場所にコピーし、元の項目を削除します。 リスト内の他の場所にドラッグするリスト ボックス項目のコピーを有効にするなど、既定の動作をカスタマイズするには、この関数をオーバーライドします。

##  <a name="itemfrompt"></a>  CDragListBox::ItemFromPt

リスト ボックス項目の 0 から始まるインデックスを取得するには、この関数がある呼び出し*pt*します。

```
int ItemFromPt(
    CPoint pt,
    BOOL bAutoScroll = TRUE) const;
```

### <a name="parameters"></a>パラメーター

*pt*<br/>
A [CPoint](../../atl-mfc-shared/reference/cpoint-class.md)リスト ボックス内のポイントの座標を格納しているオブジェクト。

*bAutoScroll*<br/>
スクロールが許可された場合、それ以外の場合 0 0 以外の値。

### <a name="return-value"></a>戻り値

ドラッグ リスト ボックス項目の 0 から始まるインデックス。

## <a name="see-also"></a>関連項目

[MFC サンプル TSTCON](../../overview/visual-cpp-samples.md)<br/>
[CListBox クラス](../../mfc/reference/clistbox-class.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[CListBox クラス](../../mfc/reference/clistbox-class.md)
