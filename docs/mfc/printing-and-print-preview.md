---
title: 印刷および印刷プレビュー
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC]
- previewing printing
- printing [MFC]
- print preview
- printing [MFC], print preview
ms.assetid: d15059cd-32de-4450-95f7-e73aece238f6
ms.openlocfilehash: 70740922ec7f2030d14eebee72144a373550aacc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62218717"
---
# <a name="printing-and-print-preview"></a>印刷および印刷プレビュー

MFC クラスを使用して、プログラムのドキュメントの印刷と印刷プレビューをサポートしている[CView](../mfc/reference/cview-class.md)します。 基本的な印刷と印刷プレビューでは、ビュー クラスをオーバーライドするだけで[OnDraw](../mfc/reference/cview-class.md#ondraw)メンバー関数で行うことができます。 その関数が実際のプリンターのプリンター デバイス コンテキストを画面上の表示を描画できます。 または画面上のプリンターをシミュレートするデバイス コンテキストにします。

マルチページ ドキュメントの印刷とプレビュー、それらにヘッダーとフッターを追加して、印刷されたドキュメントでは、改ページ調整を管理するためのコードを追加することもできます。

この一連のトピックでは、印刷は、Microsoft Foundation Class ライブラリ (MFC) を実装する方法と、フレームワークに組み込まれている印刷のアーキテクチャを活用する方法について説明します。 また、記事は、MFC が印刷プレビュー機能の簡単な実装をサポートする方法と、使用して、その機能を変更する方法を説明します。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [印刷](../mfc/printing.md)

- [印刷プレビューのアーキテクチャ](../mfc/print-preview-architecture.md)

- [サンプル](../overview/visual-cpp-samples.md)

## <a name="see-also"></a>関連項目

[ユーザー インターフェイス要素](../mfc/user-interface-elements-mfc.md)
