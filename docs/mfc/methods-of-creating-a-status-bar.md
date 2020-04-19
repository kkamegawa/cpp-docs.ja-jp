---
title: ステータス バーの作成方法
ms.date: 11/04/2016
helpviewer_keywords:
- CStatusBar class [MFC], vs. CStatusBarCtrl
- methods [MFC], creating status bars
- CStatusBarCtrl class [MFC], vs. CStatusBar
- CStatusBarCtrl class [MFC], creating
- methods [MFC]
- status bars [MFC], creating
ms.assetid: 9aeaf290-7099-4762-a5ba-9c26705333c9
ms.openlocfilehash: a2301301d0012bd93ffedd0452dec140174402e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62383892"
---
# <a name="methods-of-creating-a-status-bar"></a>ステータス バーの作成方法

MFC には、ステータス バーを作成する 2 つのクラスが用意されています。[CStatusBar](../mfc/reference/cstatusbar-class.md)と[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) (ラップしています。 Windows のコモン コントロール API)。 `CStatusBar` すべての機能を提供のステータス バー コモン コントロールには、自動的に対話メニューとツールバーと必要な一般的なコントロールの設定と構造体の多くを処理。ただし、結果として得られる実行可能ファイルは、通常はより大きくするを使用して作成`CStatusBarCtrl`です。

`CStatusBarCtrl` 小さい実行可能ファイルでの結果を使用することもできます通常`CStatusBarCtrl`MFC アーキテクチャにステータス バーを統合する予定がない場合。 使用して行う場合`CStatusBarCtrl`とステータス バーを MFC アーキテクチャに統合、ステータス バーの mfc コントロールの操作を通信するためにさらに注意を行う必要があります。 この通信は困難です。ただしは、使用すると、必要な追加の作業が`CStatusBar`します。

Visual C には、ステータス バーの一般的なコントロールを活用するために 2 つの方法が用意されています。

- ステータス バーを使用して作成`CStatusBar`を呼び出して[CStatusBar::GetStatusBarCtrl](../mfc/reference/cstatusbar-class.md#getstatusbarctrl)へのアクセスを取得する、`CStatusBarCtrl`メンバー関数。

- ステータス バーを使用して作成[CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md)のコンス トラクター。

いずれかの方法、ステータス バー コントロールのメンバー関数にアクセスは許可されます。 呼び出すと`CStatusBar::GetStatusBarCtrl`への参照を返します、`CStatusBarCtrl`オブジェクト メンバー関数のいずれかのセットを使用できるようにします。 参照してください[CStatusBar](../mfc/reference/cstatusbar-class.md)を構築して、ステータス バーを使用して作成について`CStatusBar`します。

## <a name="see-also"></a>関連項目

[CStatusBarCtrl の使い方](../mfc/using-cstatusbarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
