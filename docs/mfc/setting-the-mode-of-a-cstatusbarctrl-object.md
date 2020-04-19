---
title: CStatusBarCtrl オブジェクトのモードの設定
ms.date: 11/04/2016
f1_keywords:
- CStatusBarCtrl
helpviewer_keywords:
- simple mode and status bar controls
- IsSimple method, using
- SetSimple method [MFC]
- status bar controls [MFC], simple and nonsimple modes
- non-simple mode and status bar controls
- CStatusBarCtrl class [MFC], simple and nonsimple modes
ms.assetid: ca6076e5-1501-4e33-8d35-9308941e46c0
ms.openlocfilehash: a6d1a0edb356f9737aa287809dd8bca4146c1854
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62307721"
---
# <a name="setting-the-mode-of-a-cstatusbarctrl-object"></a>CStatusBarCtrl オブジェクトのモードの設定

2 つのモードを`CStatusBarCtrl`オブジェクト: シンプルで標準。 ほとんどの場合、ステータス バー コントロールはテキストとアイコンではおそらくまたはアイコンと共に、1 つまたは複数の部分になります。 これは標準モードと呼ばれます。 このモードの詳細については、次を参照してください。[の CStatusBarCtrl オブジェクトの初期化](../mfc/initializing-the-parts-of-a-cstatusbarctrl-object.md)します。

ただし、だけする必要がある 1 行のテキストを表示する場合があります。 この場合は、単純なモードは、ニーズのための十分なは。 モードを変更する、`CStatusBarCtrl`シンプル オブジェクト、呼び出しを行う、 [SetSimple](../mfc/reference/cstatusbarctrl-class.md#setsimple)メンバー関数。 ステータス バー コントロールは、単純なモードでは後で呼び出すことによって、テキストを設定、`SetText`メンバー関数を値として 255、 *nPane*パラメーター。

使用することができます、 [IsSimple](../mfc/reference/cstatusbarctrl-class.md#issimple)モードを決定する関数、`CStatusBarCtrl`オブジェクトします。

> [!NOTE]
>  単純でないから、[シンプル] に変更されるステータス バーのオブジェクトまたはその逆の場合、ウィンドウがすぐに再描画される場合と、該当する場合、定義されている任意の部分が自動的に復元します。

## <a name="see-also"></a>関連項目

[CStatusBarCtrl の使い方](../mfc/using-cstatusbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
