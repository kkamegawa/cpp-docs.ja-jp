---
title: CReBar とCReBarCtrl
ms.date: 11/04/2016
f1_keywords:
- CReBar
- CReBarCtrl
helpviewer_keywords:
- CReBar class [MFC], vs. CReBarCtrl
- rebar controls [MFC], CReBarCtrl class [MFC]
- GetReBarCtrl class [MFC]
ms.assetid: 7f9c1d7e-5d5f-4956-843c-69ed3df688d0
ms.openlocfilehash: a1b5cda729e760246449bf197fdc9b32752b96e8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62241788"
---
# <a name="crebar-vs-crebarctrl"></a>CReBar とCReBarCtrl

MFC には、rebars を作成する 2 つのクラスが用意されています。[CReBar](../mfc/reference/crebar-class.md)と[crebarctrl の比較](../mfc/reference/crebarctrl-class.md)(ラップしています。 Windows のコモン コントロール API)。 `CReBar` すべての共通の rebar コントロールの機能を提供しますが、必要な一般的なコントロールの設定と構造体の多くを処理します。

`CReBarCtrl` Win32 rebar コントロールのラッパー クラスは、そのため、MFC のアーキテクチャに rebar を統合する予定がない場合の実装が簡単にあります。 使用して行う場合`CReBarCtrl`と MFC アーキテクチャに rebar を統合、rebar コントロールの操作 (MFC に) を通信するためにさらに注意を行う必要があります。 この通信は困難です。ただしは、使用すると、必要な追加の作業が`CReBar`します。

Visual C には、rebar の一般的なコントロールを活用するために 2 つの方法が用意されています。

- 使用して、rebar の作成`CReBar`を呼び出して[CReBar::GetReBarCtrl](../mfc/reference/crebar-class.md#getrebarctrl)へのアクセスを取得する、`CReBarCtrl`メンバー関数。

    > [!NOTE]
    >  `CReBar::GetReBarCtrl` キャストするインライン メンバー関数は、**this**rebar オブジェクトのポインター。 つまり、実行時に、関数呼び出しのオーバーヘッドが発生しません。

- 使用して、rebar の作成[crebarctrl の比較](../mfc/reference/crebarctrl-class.md)のコンス トラクター。

いずれかの方法、rebar コントロールのメンバー関数へアクセスは許可されます。 呼び出すと`CReBar::GetReBarCtrl`への参照を返します、`CReBarCtrl`オブジェクト メンバー関数のいずれかのセットを使用できるようにします。 参照してください[CReBar](../mfc/reference/crebar-class.md)を構築してを使用して、rebar の作成について`CReBar`します。

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
