---
title: コントロールの描画の最適化
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], optimizing
ms.assetid: 29ff985d-9bf5-4678-b62d-aad12def75fb
ms.openlocfilehash: 354ec1678747be57d387673f2611d526df8dfb47
ms.sourcegitcommit: 0ad35b26e405bbde17dc0bd0141e72f78f0a38fb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2019
ms.locfileid: "67194733"
---
# <a name="optimizing-control-drawing"></a>コントロールの描画の最適化

コントロールは、自身のコンテナーが指定したデバイス コンテキストに描画するように指示されます、ときに通常デバイス コンテキストに (ペン、ブラシ、およびフォント) などの GDI オブジェクトを選択します、その図面の操作を実行し、前の GDI オブジェクトを復元します。 コンテナーが同じデバイス コンテキストに描画するのには複数のコントロール、各コントロールに要する GDI オブジェクトを選択する場合は、時間は、コントロールは以前に選択したオブジェクトを個別に復元されない場合に保存できます。 すべてのコントロールを描画すると、コンテナーは自動的に元のオブジェクトを復元できます。

コンテナーがこの手法をサポートしているかどうかを検出するためのコントロールを呼び出すことができます、 [COleControl::IsOptimizedDraw](../mfc/reference/colecontrol-class.md#isoptimizeddraw)メンバー関数。 この関数が返す場合**TRUE**、以前に選択したオブジェクトの復元の通常の手順を省略できます。

(最適化されていない)、次を含むコントロールについて考えてみます`OnDraw`関数。

[!code-cpp[NVC_MFC_AxOpt#15](../mfc/codesnippet/cpp/optimizing-control-drawing_1.cpp)]

ペンとブラシをこの例では、ローカル変数、つまり、スコープ外に出るときに、デストラクターが呼び出されます (ときに、`OnDraw`関数の終了)。 デストラクターは、対応する GDI オブジェクトを削除しようとします。 戻ったときに、デバイス コンテキストに選択されたままにする場合、削除できないが、`OnDraw`します。

防ぐために、 [CPen](../mfc/reference/cpen-class.md)と[CBrush](../mfc/reference/cbrush-class.md)ときに破棄されるオブジェクト`OnDraw`が終了したら、ローカル変数ではなくメンバー変数に保存します。 コントロールのクラスの宣言では、2 つの新しいメンバー変数の宣言を追加します。

[!code-cpp[NVC_MFC_AxOpt#16](../mfc/codesnippet/cpp/optimizing-control-drawing_2.h)]
[!code-cpp[NVC_MFC_AxOpt#17](../mfc/codesnippet/cpp/optimizing-control-drawing_3.h)]

次に、`OnDraw`関数は次のように書き換えることができます。

[!code-cpp[NVC_MFC_AxOpt#18](../mfc/codesnippet/cpp/optimizing-control-drawing_4.cpp)]

このアプローチは、毎回、ペンとブラシの作成を回避できます。`OnDraw`が呼び出されます。 速度の向上が追加のインスタンスのデータを維持する犠牲にします。

前景色または背景色のプロパティが変更された場合、ブラシ、ペンを再作成する必要があります。 これを行うには、オーバーライド、 [OnForeColorChanged](../mfc/reference/colecontrol-class.md#onforecolorchanged)と[OnBackColorChanged](../mfc/reference/colecontrol-class.md#onbackcolorchanged)メンバー関数。

[!code-cpp[NVC_MFC_AxOpt#19](../mfc/codesnippet/cpp/optimizing-control-drawing_5.cpp)]

最後に、不要に`SelectObject`呼び出し、変更`OnDraw`次のようにします。

[!code-cpp[NVC_MFC_AxOpt#20](../mfc/codesnippet/cpp/optimizing-control-drawing_6.cpp)]

## <a name="see-also"></a>関連項目

[MFC ActiveX コントロール: 最適化](../mfc/mfc-activex-controls-optimization.md)<br/>
[COleControl クラス](../mfc/reference/colecontrol-class.md)<br/>
[MFC ActiveX コントロール](../mfc/mfc-activex-controls.md)<br/>
[MFC ActiveX コントロール ウィザード](../mfc/reference/mfc-activex-control-wizard.md)<br/>
[MFC ActiveX コントロール: ActiveX コントロールの描画](../mfc/mfc-activex-controls-painting-an-activex-control.md)
