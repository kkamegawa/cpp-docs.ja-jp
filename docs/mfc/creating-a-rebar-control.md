---
title: Rebar コントロールの作成
ms.date: 11/04/2016
helpviewer_keywords:
- rebar controls [MFC], creating
- CReBarCtrl class [MFC], creating
ms.assetid: 0a012e08-772b-4f6a-af86-7cb651d11d3e
ms.openlocfilehash: 0fb651aef599b64b787d96a668e2e1496c1dff8e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62153346"
---
# <a name="creating-a-rebar-control"></a>Rebar コントロールの作成

[Crebarctrl の比較](../mfc/reference/crebarctrl-class.md)親オブジェクトが表示される前に、オブジェクトを作成する必要があります。 これにより、描画上の問題の可能性を最小限に抑えられます。

たとえば、rebar コントロールの (フレーム ウィンドウ オブジェクトで使用) は、ツール バー コントロールの親ウィンドウとして使用よくされます。 そのため、rebar コントロールの親は、フレーム ウィンドウ オブジェクトです。 フレーム ウィンドウ オブジェクトが、親であるため、 `OnCreate` (親) のメンバー関数は、rebar コントロールを作成するにふさわしい場です。

使用する、`CReBarCtrl`オブジェクトに、次の手順を通常になります。

### <a name="to-use-a-crebarctrl-object"></a>Crebarctrl の比較オブジェクトを使用するには

1. 構築、 [crebarctrl の比較](../mfc/reference/crebarctrl-class.md)オブジェクト。

1. 呼び出す[作成](../mfc/reference/crebarctrl-class.md#create)Windows rebar の一般的なコントロールを作成し、アタッチ先、`CReBarCtrl`任意のスタイルを指定するオブジェクト。

1. 呼び出して、ビットマップを読み込む[CBitmap::LoadBitmap](../mfc/reference/cbitmap-class.md#loadbitmap)、rebar コントロール オブジェクトの背景として使用します。

1. 作成し、rebar コントロール オブジェクトが含まれる子ウィンドウ オブジェクト (ツールバー、ダイアログのコントロール) を初期化します。

1. 初期化を**REBARBANDINFO**構造体に挿入するバンドのために必要な情報。

1. 呼び出す[InsertBand](../mfc/reference/crebarctrl-class.md#insertband)既存の子ウィンドウを挿入する (など`m_wndReToolBar`) 新しい rebar コントロールにします。 既存の rebar コントロール バンドを挿入の詳細については、次を参照してください。 [Rebar コントロールとバンド](../mfc/rebar-controls-and-bands.md)します。

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
