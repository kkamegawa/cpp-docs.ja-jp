---
title: CMFCWindowsManagerDialog クラス
ms.date: 11/04/2016
f1_keywords:
- CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog
- AFXWINDOWSMANAGERDIALOG/CMFCWindowsManagerDialog::CMFCWindowsManagerDialog
helpviewer_keywords:
- CMFCWindowsManagerDialog [MFC], CMFCWindowsManagerDialog
ms.assetid: 35b4b0db-33c4-4b22-94d8-5e3396341340
ms.openlocfilehash: 5089decc7a118cd867aa14df51f5d7e269221108
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62373662"
---
# <a name="cmfcwindowsmanagerdialog-class"></a>CMFCWindowsManagerDialog クラス

`CMFCWindowsManagerDialog`オブジェクトは、MDI アプリケーションでの MDI 子ウィンドウを管理するユーザーを使用できます。

## <a name="syntax"></a>構文

```
class CMFCWindowsManagerDialog : public CDialog
```

## <a name="members"></a>メンバー

### <a name="public-constructors"></a>パブリック コンストラクター

|名前|説明|
|----------|-----------------|
|[CMFCWindowsManagerDialog::CMFCWindowsManagerDialog](#cmfcwindowsmanagerdialog)|`CMFCWindowsManagerDialog` オブジェクトを構築します。|

## <a name="remarks"></a>Remarks

`CMFCWindowsManagerDialog`アプリケーションで現在開いている MDI 子ウィンドウの一覧が含まれています。 このダイアログ ボックスを使用して、MDI 子ウィンドウの状態を手動で制御できます。

`CMFCWindowsManagerDialog` 埋め込まれています、 [CMDIFrameWndEx クラス](../../mfc/reference/cmdiframewndex-class.md)します。 `CMFCWindowsManagerDialog`手動で作成する必要がありますクラスではありません。 代わりに、関数を呼び出す[CMDIFrameWndEx::ShowWindowsDialog](../../mfc/reference/cmdiframewndex-class.md#showwindowsdialog)と作成が表示され、`CMFCWindowsManagerDialog`オブジェクト。

## <a name="example"></a>例

次の例は、構築する方法を示します、`CMFCWindowsManagerDialog`オブジェクトを呼び出すことによって`CMDIFrameWndEx::ShowWindowsDialog`します。 このコード スニペットの一部、 [Visual Studio のデモ サンプル](../../overview/visual-cpp-samples.md)します。

[!code-cpp[NVC_MFC_VisualStudioDemo#18](../../mfc/codesnippet/cpp/cmfcwindowsmanagerdialog-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>継承階層

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CDialog](../../mfc/reference/cdialog-class.md)

[CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)

## <a name="requirements"></a>必要条件

**ヘッダー:** afxWindowsManagerDialog.h

##  <a name="cmfcwindowsmanagerdialog"></a>  CMFCWindowsManagerDialog::CMFCWindowsManagerDialog

構築、 [CMFCWindowsManagerDialog](../../mfc/reference/cmfcwindowsmanagerdialog-class.md)オブジェクト。

```
CMFCWindowsManagerDialog(
    CMDIFrameWndEx* pMDIFrame,
    BOOL bHelpButton = FALSE);
```

### <a name="parameters"></a>パラメーター

*pMDIFrame*<br/>
[in]親またはオーナー ウィンドウへのポインター。

*bHelpButton*<br/>
[in]フレームワークを表示するかどうかを指定するブール型パラメーター、**ヘルプ**ボタンをクリックします。

### <a name="remarks"></a>Remarks

ビジュアル マネージャーの詳細については、次を参照してください。[ビジュアル マネージャー](../../mfc/visualization-manager.md)します。

## <a name="see-also"></a>関連項目

[階層図](../../mfc/hierarchy-chart.md)<br/>
[クラス](../../mfc/reference/mfc-classes.md)<br/>
[CMDIFrameWndEx クラス](../../mfc/reference/cmdiframewndex-class.md)
