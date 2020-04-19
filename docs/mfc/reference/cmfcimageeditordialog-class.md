---
title: CMFCImageEditorDialog クラス
ms.date: 11/19/2018
f1_keywords:
- CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog
- AFXIMAGEEDITORDIALOG/CMFCImageEditorDialog::CMFCImageEditorDialog
helpviewer_keywords:
- CMFCImageEditorDialog [MFC], CMFCImageEditorDialog
ms.assetid: 6a7d08f3-1ec2-4062-9b79-a0c2776b58d1
ms.openlocfilehash: 97f16fa00b2e90fd9c43bf9b6792b4eafe7d7b88
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394539"
---
# <a name="cmfcimageeditordialog-class"></a>CMFCImageEditorDialog クラス

`CMFCImageEditorDialog`クラスは、イメージ エディター ダイアログ ボックスをサポートしています。

## <a name="syntax"></a>構文

```
class CMFCImageEditorDialog : public CDialogEx
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCImageEditorDialog::CMFCImageEditorDialog](#cmfcimageeditordialog)|`CMFCImageEditorDialog` オブジェクトを構築します。|

## <a name="remarks"></a>Remarks

`CMFCImageEditorDialog`クラスが含まれるダイアログ ボックスを提供します。

- ピクチャの領域を使用して個々 のピクセル イメージに変更します。

- ピクチャの領域のピクセルを修正するためのツールを描画します。

- 描画ツールによって使用される色を指定する色パレット。

- 編集する効果を表示するプレビュー領域。

次の図は、イメージ エディター ダイアログ ボックスを示しています。

![[CMFCImageEditorDialog] ダイアログ ボックス](../../mfc/reference/media/imageedit.png "CMFCImageEditorDialog ダイアログ ボックス")

使用する方法の 1 つ、`CMFCImageEditorDialog`オブジェクトを渡すことが、`CBitmap`編集する画像。 イメージの編集領域が制限されたサイズと論理ピクセルのサイズが領域に合わせて調整するため、大きいイメージを作成できません。 呼び出す、`DoModal`モーダル ダイアログ ボックスを起動する方法。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CDialogEx](../../mfc/reference/cdialogex-class.md)

[CMFCImageEditorDialog](../../mfc/reference/cmfcimageeditordialog-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afximageeditordialog.h

##  <a name="cmfcimageeditordialog"></a>  CMFCImageEditorDialog::CMFCImageEditorDialog

`CMFCImageEditorDialog` オブジェクトを構築します。

```
CMFCImageEditorDialog(
    CBitmap* pBitmap,
    CWnd* pParent=NULL,
    int nBitsPixel=-1);
```

### <a name="parameters"></a>パラメーター

*pBitmap*<br/>
イメージへのポインター。

*pParent*<br/>
現在のイメージ エディター ダイアログ ボックスの親ウィンドウへのポインター。

*nBitsPixel*<br/>
色深度とも呼ばれますが、1 つのピクセルの色を表すために使用されるビット数。  場合、 *nBitsPixel*パラメーターが-1、色の解像度がで指定されたイメージから派生した、 *pBitmap*パラメーター。 既定値は -1 です。

### <a name="return-value"></a>戻り値

イメージを変更するにイメージ ポインターを渡す、`CMFCImageEditorDialog`コンス トラクター。 呼び出して、`DoModal`メソッド モーダル ダイアログ ボックスを開きます。 ときに、`DoModal`メソッドが戻る、ビットマップには、新しいイメージが含まれています。

### <a name="remarks"></a>Remarks

### <a name="example"></a>例

次の例のオブジェクトを構築する方法、`CMFCImageEditorDialog`クラス。 この例は、[新しいコントロール サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_NewControls#8](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_1.cpp)]
[!code-cpp[NVC_MFC_NewControls#40](../../mfc/reference/codesnippet/cpp/cmfcimageeditordialog-class_2.cpp)]

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMFCToolBar クラス](../../mfc/reference/cmfctoolbar-class.md)
