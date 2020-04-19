---
title: CMFCImagePaintArea クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::CMFCImagePaintArea
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::GetMode
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetBitmap
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetColor
- AFXIMAGEPAINTAREA/CMFCImagePaintArea::SetMode
helpviewer_keywords:
- CMFCImagePaintArea [MFC], CMFCImagePaintArea
- CMFCImagePaintArea [MFC], GetMode
- CMFCImagePaintArea [MFC], SetBitmap
- CMFCImagePaintArea [MFC], SetColor
- CMFCImagePaintArea [MFC], SetMode
ms.assetid: c59eec22-f15a-4e58-8c4d-4a18a41f4452
ms.openlocfilehash: 37d975ace4d144cc6274b49a3406382f0fb300ee
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374182"
---
# <a name="cmfcimagepaintarea-class"></a>CMFCImagePaintArea クラス

イメージ エディター ダイアログ ボックスでイメージを変更するために使用するピクチャの領域を提供します。

## <a name="syntax"></a>構文

```
class CMFCImagePaintArea : public CButton
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|||
|-|-|
|名前|説明|
|[CMFCImagePaintArea::CMFCImagePaintArea](#cmfcimagepaintarea)|`CMFCImagePaintArea` オブジェクトを構築します。|
|`CMFCImagePaintArea::~CMFCImagePaintArea`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|||
|-|-|
|名前|説明|
|[CMFCImagePaintArea::GetMode](#getmode)|現在の描画モードを取得します。|
|[CMFCImagePaintArea::SetBitmap](#setbitmap)|ピクチャの領域のビットマップ イメージを設定します。|
|[CMFCImagePaintArea::SetColor](#setcolor)|現在の描画の色を設定します。|
|[CMFCImagePaintArea::SetMode](#setmode)|現在の描画モードを設定します。|

### <a name="remarks"></a>Remarks

このクラスは、コードから直接使用するものではありません。

フレームワークでは、このクラスを使用して、イメージ エディター ダイアログ ボックスで、ピクチャの領域を表示します。 イメージ エディターのダイアログ ボックスの詳細については、次を参照してください。 [CMFCImageEditorDialog クラス](../../mfc/reference/cmfcimageeditordialog-class.md)します。

## <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCImagePaintArea`を現在の色を描画するには、現在の描画モードを設定し、ビットマップ画像画像領域の設定を設定します。

[!code-cpp[NVC_MFC_RibbonApp#37](../../mfc/reference/codesnippet/cpp/cmfcimagepaintarea-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CButton](../../mfc/reference/cbutton-class.md)

[CMFCImagePaintArea](../../mfc/reference/cmfcimagepaintarea-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afximagepaintarea.h

##  <a name="cmfcimagepaintarea"></a>  CMFCImagePaintArea::CMFCImagePaintArea

`CMFCImagePaintArea` オブジェクトを構築します。

```
CMFCImagePaintArea(CMFCImageEditorDialog* pParentDlg);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pParentDlg*|[in]イメージ エディターの親であるダイアログ ボックスへのポインター。|

##  <a name="getmode"></a>  CMFCImagePaintArea::GetMode

現在の描画モードを取得します。

```
IMAGE_EDIT_MODE GetMode() const;
```

### <a name="return-value"></a>戻り値

[IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)現在の描画モードを指定する値。

##  <a name="setbitmap"></a>  CMFCImagePaintArea::SetBitmap

ピクチャの領域のビットマップ イメージを設定します。

```
void SetBitmap(CBitmap* pBitmap);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*pBitmap*|[in]表示する新しいビットマップ イメージ。|

### <a name="remarks"></a>Remarks

場合*pBitmap*が null の場合、このメソッドは、0 に変更可能な描画領域のサイズを設定します。 それ以外の場合、指定されたビットマップ イメージのサイズ変更可能な描画領域のサイズに設定します。

##  <a name="setcolor"></a>  CMFCImagePaintArea::SetColor

現在の描画の色を設定します。

```
void SetColor(COLORREF color);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*色*|[in]新しい描画の色。|

### <a name="remarks"></a>Remarks

ときに、イメージ エディター パレット バーから色を選択またはカラー ピッカー、フレームワークは、現在の描画の色を更新するには、このメソッドを呼び出します。 初期の描画の色は黒 (0 の COLORREF 値)。

描画の色は、IMAGE_EDIT_MODE_COLOR を除くすべての描画モードのイメージ エディターのダイアログ ボックスで使用されます。 描画モードの詳細については、次を参照してください。 [cmfcimagepaintarea::image_edit_mode 列挙体](cmfcimagepaintarea-image-edit-mode-enumeration.md)します。

##  <a name="setmode"></a>  CMFCImagePaintArea::SetMode

現在の描画モードを設定します。

```
void SetMode(IMAGE_EDIT_MODE mode);
```

### <a name="parameters"></a>パラメーター

|||
|-|-|
|パラメーター|説明|
|*モード*|[in][IMAGE_EDIT_MODE](cmfcimagepaintarea-image-edit-mode-enumeration.md)現在の描画モードを指定する値。|

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImageEditorDialog クラス](../../mfc/reference/cmfcimageeditordialog-class.md)
