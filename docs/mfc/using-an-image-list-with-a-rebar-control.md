---
title: Rebar コントロールでのイメージ リストの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- image lists [MFC], rebar controls
- rebar controls [MFC], image lists
ms.assetid: 1a5836ac-019a-46aa-8741-b35c3376b839
ms.openlocfilehash: fa5307c201850fc42439c79a1c638a0707379913
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62180499"
---
# <a name="using-an-image-list-with-a-rebar-control"></a>Rebar コントロールでのイメージ リストの使い方

各 rebar バンド含めることができます、特に、関連付けられているイメージ リストのイメージ。 次の手順では、rebar バンドでイメージを表示するために必要な手順について説明します。

### <a name="to-display-images-in-a-rebar-band"></a>Rebar バンドでイメージを表示するには

1. 呼び出すことによって、イメージ リストを rebar コントロール オブジェクトにアタッチ[SetImageList](../mfc/reference/crebarctrl-class.md#setimagelist)、既存のイメージ リストにポインターを渡すことです。

1. 変更、 **REBARBANDINFO** rebar バンドにイメージを割り当てる構造体。

   - 設定、 *fMask*メンバー `RBBIM_IMAGE`、必要に応じて、追加のフラグを含めるには、ビットごとの OR 演算子を使用します。

   - 設定、*画像を*メンバーは、イメージのイメージ リスト インデックスを表示します。

1. サイズ、テキスト、および、必要な情報は含まれている子ウィンドウのハンドルなど、残りのデータ メンバーを初期化します。

1. 呼び出して (イメージ) を含む新しいバンドの挿入[CReBarCtrl::InsertBand](../mfc/reference/crebarctrl-class.md#insertband)を渡して、 **REBARBANDINFO**構造体。

次の例では、2 つのイメージを既存のイメージ リスト オブジェクトが rebar コントロール オブジェクトに接続されている前提としています (`m_wndReBar`)。 新しい rebar バンド (によって定義された`rbi`)、最初のイメージを含むへの呼び出しは追加`InsertBand`:

[!code-cpp[NVC_MFCControlLadenDialog#28](../mfc/codesnippet/cpp/using-an-image-list-with-a-rebar-control_1.cpp)]

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
