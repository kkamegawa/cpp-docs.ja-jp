---
title: CMFCImagePaintArea::IMAGE_EDIT_MODE 列挙体
ms.date: 11/04/2016
f1_keywords:
- IMAGE_EDIT_MODE Enumeration
helpviewer_keywords:
- IMAGE_EDIT_MODE Enumeration method [MFC]
ms.assetid: e51db66a-fa1c-4766-9dac-a25b595f871a
ms.openlocfilehash: 372a1df6500f4d7219c89d8f82425246c2236514
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410175"
---
# <a name="cmfcimagepaintareaimageeditmode-enumeration"></a>CMFCImagePaintArea::IMAGE_EDIT_MODE 列挙体

イメージ エディター ダイアログ ボックスでイメージを変更するために使用する描画モードを指定します。

## <a name="syntax"></a>構文

```
enum IMAGE_EDIT_MODE
{
    IMAGE_EDIT_MODE_PEN = 0,
    IMAGE_EDIT_MODE_FILL,
    IMAGE_EDIT_MODE_LINE,
    IMAGE_EDIT_MODE_RECT,
    IMAGE_EDIT_MODE_ELLIPSE,
    IMAGE_EDIT_MODE_COLOR
};
```

## <a name="members"></a>メンバー

|||
|-|-|
|名前|説明|
|IMAGE_EDIT_MODE_PEN|個々 のピクセルの描画に使用します。|
|IMAGE_EDIT_MODE_FILL|現在のカーソル位置の色を含むすべての隣接する領域を塗りつぶすために使用します。|
|IMAGE_EDIT_MODE_LINE|線を描画するために使用します。|
|IMAGE_EDIT_MODE_RECT|四角形を描画するために使用します。|
|IMAGE_EDIT_MODE_ELLIPSE|楕円を描画するために使用します。|
|IMAGE_EDIT_MODE_COLOR|現在のカーソル位置にある現在の色を色に設定するために使用します。|

### <a name="remarks"></a>Remarks

`CMFCImagePaintArea`と`CMFCImageEditorDialog`クラスでは、この列挙体を使用して、現在の描画モードを設定します。 描画モードと現在の色は、イメージ エディター ダイアログ ボックスで画像領域の変更に使用されます。 詳細については`CMFCImagePaintArea`と`CMFCImageEditorDialog`を参照してください[CMFCImagePaintArea クラス](../../mfc/reference/cmfcimagepaintarea-class.md)と[CMFCImageEditorDialog クラス](../../mfc/reference/cmfcimageeditordialog-class.md)します。

イメージから IMAGE_EDIT_MODE_COLOR の描画モードを使用して色を選択すると、フレームワークは IMAGE_EDIT_MODE_PEN を現在の描画モードを設定します。

## <a name="requirements"></a>必要条件

**ヘッダー:** afximagepaintarea.h

## <a name="see-also"></a>関連項目

[マクロとグローバル](../../mfc/reference/mfc-macros-and-globals.md)<br/>
[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCImagePaintArea クラス](../../mfc/reference/cmfcimagepaintarea-class.md)<br/>
[CMFCImageEditorDialog クラス](../../mfc/reference/cmfcimageeditordialog-class.md)
