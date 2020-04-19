---
title: '方法: MFC アプリケーションからリボン リソースを読み込む'
ms.date: 11/04/2016
helpviewer_keywords:
- ribbon resource [MFC], loading
ms.assetid: 1c76bb8f-6345-414a-9f3f-128815ceadc5
ms.openlocfilehash: b7691d4168101209b0e2d2500012a2b4a8e47788
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160329"
---
# <a name="how-to-load-a-ribbon-resource-from-an-mfc-application"></a>方法: MFC アプリケーションからリボン リソースを読み込む

アプリケーションでリボン リソースを使用するには、リボン リソースを読み込むためのアプリケーションを変更します。

### <a name="to-load-a-ribbon-resource"></a>リボン リソースを読み込めません

1. 宣言、`Ribbon Control`オブジェクト、`CMainFrame`クラス。

```
    CMFCRibbonBar m_wndRibbonBar;
```

1. `CMainFrame::OnCreate`を作成し、リボン コントロールを初期化します。

```
    if (!m_wndRibbonBar.Create (this))
{
    return -1;
}

    if (!m_wndRibbonBar.LoadFromResource(IDR_RIBBON))
{
    return -1;
}
```

## <a name="see-also"></a>関連項目

[リボン デザイナー (MFC)](../mfc/ribbon-designer-mfc.md)
