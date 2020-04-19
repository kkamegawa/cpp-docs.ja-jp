---
title: CMFCRibbonCustomizeDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog
- AFXRIBBONCUSTOMIZEDIALOG/CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog
helpviewer_keywords:
- CMFCRibbonCustomizeDialog [MFC], CMFCRibbonCustomizeDialog
ms.assetid: ce67de7f-5eaa-4c75-9b94-f290f36df073
ms.openlocfilehash: d73fd05a775ac26f5d289a5233341102f40e9af3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62237627"
---
# <a name="cmfcribboncustomizedialog-class"></a>CMFCRibbonCustomizeDialog クラス

リボンが表示されます**カスタマイズ**ページ。

## <a name="syntax"></a>構文

```
class CMFCRibbonCustomizeDialog : public CMFCPropertySheet
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog](#cmfcribboncustomizedialog)|`CMFCRibbonCustomizeDialog` オブジェクトを構築します。|
|`CMFCRibbonCustomizeDialog::~CMFCRibbonCustomizeDialog`|デストラクターです。|

### <a name="public-methods"></a>パブリック メソッド

|名前|説明|
|----------|-----------------|
|`CMFCRibbonCustomizeDialog::GetThisClass`|ポインターを取得する、framework によって使用される、 [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md)このクラス型に関連付けられているオブジェクト。|

## <a name="remarks"></a>Remarks

MFC では、AFX_WM_ON_RIBBON_CUSTOMIZE メッセージを処理しない場合、またはメッセージ ハンドラーから 0 を返す場合は自動的にこのクラスがインスタンス化します。

アプリケーションで、リボンを表示するこのクラスを使用するかどうか**カスタマイズ** ダイアログ ボックスでのみインスタンス化し、呼び出し、`DoModal`メソッド。

このクラスはから派生しているため[CMFCPropertySheet クラス](../../mfc/reference/cmfcpropertysheet-class.md)を使用してカスタム ページを追加することができます、 `CMFCPropertySheet` API。

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CPropertySheet](../../mfc/reference/cpropertysheet-class.md)

[CMFCPropertySheet](../../mfc/reference/cmfcpropertysheet-class.md)

[CMFCRibbonCustomizeDialog](../../mfc/reference/cmfcribboncustomizedialog-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxribboncustomizedialog.h

##  <a name="cmfcribboncustomizedialog"></a>  CMFCRibbonCustomizeDialog::CMFCRibbonCustomizeDialog

`CMFCRibbonCustomizeDialog` オブジェクトを構築します。

```
CMFCRibbonCustomizeDialog(
    CWnd* pWndParent,
    CMFCRibbonBar* pRibbon);
```

### <a name="parameters"></a>パラメーター

*pWndParent*<br/>
[in]親ウィンドウ (通常はメイン フレーム) へのポインター。

*pRibbon*<br/>
[in]ポインター、`CMFCRibbonBar`カスタマイズです。

### <a name="example"></a>例

次の例は、構築する方法を示します、`CMFCRibbonCustomizeDialog`オブジェクト。

[!code-cpp[NVC_MFC_RibbonApp#18](../../mfc/reference/codesnippet/cpp/cmfcribboncustomizedialog-class_1.cpp)]

### <a name="remarks"></a>Remarks

コンス トラクターをインスタンス化、 [CMFCRibbonCustomizePropertyPage クラス](../../mfc/reference/cmfcribboncustomizepropertypage-class.md)オブジェクトし、プロパティ シートのページのコレクションに追加します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)
