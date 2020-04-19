---
title: '方法: リボン コントロールとイベント ハンドラーを追加します。'
ms.date: 11/04/2016
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
ms.openlocfilehash: c21e8b86962ebf37ca1a06bae056d09b9a9dbb2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62389516"
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>方法: リボン コントロールとイベント ハンドラーを追加します。

リボン コントロールは、ボタンやコンボ ボックス、パネルに追加するなどの要素です。 パネルは、関連するコントロールのグループを表示するリボン バーの領域です。

このトピックでは、リボン デザイナーを開く、ボタンを追加、"Hello World"を表示するイベントをリンクします。

### <a name="to-open-the-ribbon-designer"></a>リボン デザイナーを開く

1. Visual Studio での**ビュー**  メニューのをクリックして**リソース ビュー**します。

1. **リソース ビュー**、デザイン画面上に表示するリボン リソースをダブルクリックします。

### <a name="to-add-a-button-and-an-event-handler"></a>ボタンと、イベント ハンドラーを追加するには

1. **ツールバー**、 をクリックして**ボタン**デザイン サーフェイス上のパネルにドラッグします。

1. ボタンを右クリックし、をクリックして**イベント ハンドラーの追加**します。

1. **イベント ハンドラー ウィザード**で既定の設定を確認し、をクリックして**の追加し、編集**します。 詳細については、次を参照してください。[イベント ハンドラー ウィザード](../ide/event-handler-wizard.md)します。

1. コード エディターでは、ハンドラー関数に次のコードを追加します。

```
    MessageBox((LPCTSTR)L"Hello World");
```

## <a name="see-also"></a>関連項目

[RibbonGadgets サンプル:リボンのガジェット アプリケーション](../overview/visual-cpp-samples.md)<br/>
[リボン デザイナー (MFC)](../mfc/ribbon-designer-mfc.md)
