---
title: Rebar コントロールでのダイアログ バーの使い方
ms.date: 11/04/2016
helpviewer_keywords:
- WS_EX_TRANSPARENT style
- rebar controls [MFC], dialog bars
- dialog bars [MFC], using with rebar bands
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
ms.openlocfilehash: e4e786d3670ec74b734739e29aa7e3e33b5af384
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302368"
---
# <a name="using-a-dialog-bar-with-a-rebar-control"></a>Rebar コントロールでのダイアログ バーの使い方

「 [Rebar コントロールとバンド](../mfc/rebar-controls-and-bands.md)」で説明したように、各バンドには子ウィンドウ (またはコントロール) を1つだけ含めることができます。 これは、1つの帯域につき複数の子ウィンドウを使用する場合に制限されることがあります。 便利な回避策として、複数のコントロールを含むダイアログバーリソースを作成し、rebar コントロールに rebar バンド (ダイアログバーを含む) を追加します。

通常、ダイアログバーのバンドを透明に見えるようにするには、ダイアログバーオブジェクトの WS_EX_TRANSPARENT 拡張スタイルを設定します。 ただし、WS_EX_TRANSPARENT には、ダイアログバーの背景を適切に描画するためのいくつかの問題があるため、必要な効果を実現するために、少し余分な作業を行う必要があります。

次の手順では、WS_EX_TRANSPARENT 拡張スタイルを使用せずに透明度を実現するために必要な手順について説明します。

### <a name="to-implement-a-transparent-dialog-bar-in-a-rebar-band"></a>Rebar バンドに透過的なダイアログバーを実装するには

1. [[クラスの追加] ダイアログボックス](../mfc/reference/adding-an-mfc-class.md)を使用して、ダイアログバーオブジェクトを実装する新しいクラス (`CMyDlgBar`など) を追加します。

1. WM_ERASEBKGND メッセージのハンドラーを追加します。

1. 新しいハンドラーで、次の例に一致するように既存のコードを変更します。

   [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_1.cpp)]

1. WM_MOVE メッセージのハンドラーを追加します。

1. 新しいハンドラーで、次の例に一致するように既存のコードを変更します。

   [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/cpp/using-a-dialog-bar-with-a-rebar-control_2.cpp)]

新しいハンドラーは、WM_ERASEBKGND メッセージを親ウィンドウに転送し、ダイアログバーオブジェクトが移動されるたびに再描画を強制することによって、ダイアログバーの透明度をシミュレートします。

## <a name="see-also"></a>関連項目

[CReBarCtrl の使い方](../mfc/using-crebarctrl.md)<br/>
[コントロール](../mfc/controls-mfc.md)
