---
title: 1 段階でのオブジェクトの構築と 2 段階でのオブジェクトの構築
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 871db7abd2682d557bf2e80e9cb97624f0dc53a6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160160"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>1 段階でのオブジェクトの構築と 2 段階でのオブジェクトの構築

ペンとブラシなどのグラフィック オブジェクトを作成するための 2 つの手法のどちらかがあります。

- *1 つのステージ構築*:構築し、すべてのコンス トラクターを持つ 1 つの段階で、オブジェクトを初期化します。

- *2 段階構築*:構築し、2 つの別個の段階で、オブジェクトを初期化します。 コンス トラクターがオブジェクトを作成し、初期化関数では、それを初期化します。

2 段階で構築する方が安全です。 1 つのステージの構築が正しくない引数を指定するか、メモリの割り当てが失敗した場合、コンス トラクターは例外をスローする可能性があります。 エラーを確認する必要は、2 段階の構築によってに問題が回避されます。 いずれの場合も、同じプロセスは、オブジェクトを破棄します。

> [!NOTE]
>  これらの手法は、いないグラフィック オブジェクトだけで、あらゆるオブジェクトの作成に適用されます。

## <a name="example-of-both-construction-techniques"></a>両方の構築方法の例

次の簡単な例は、両方の pen オブジェクトを構築する方法を示しています。

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [グラフィック オブジェクト](../mfc/graphic-objects.md)

- [グラフィック オブジェクトをデバイス コンテキストに選択します。](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [デバイス コンテキスト](../mfc/device-contexts.md)

- [ビューの描画](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>関連項目

[グラフィック オブジェクト](../mfc/graphic-objects.md)
