---
title: MDI 子ウィンドウの管理
ms.date: 11/19/2018
f1_keywords:
- MDICLIENT
helpviewer_keywords:
- MDI [MFC], child windows
- child windows [MFC], and MDICLIENT window
- MDICLIENT window [MFC]
- windows [MFC], MDI
- frame windows [MFC], MDI child windows
- child windows [MFC]
- MDI [MFC], frame windows
ms.assetid: 1828d96e-a561-48ae-a661-ba9701de6bee
ms.openlocfilehash: d4b4a4876f47452361b13837b0279f5bf98f8658
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279352"
---
# <a name="managing-mdi-child-windows"></a>MDI 子ウィンドウの管理

MDI メイン フレーム ウィンドウ (アプリケーションごとに 1 つ) には、クイック ウォッチ ウィンドウと呼ばれる特殊な子ウィンドウが含まれています。 [クイック ウォッチ] ウィンドウがメイン フレーム ウィンドウのクライアント領域を管理し、子ウィンドウ自体に含まれて: から派生して、ドキュメント ウィンドウ`CMDIChildWnd`します。 ドキュメント ウィンドウは、フレーム ウィンドウ自体 (MDI 子ウィンドウ) であるため、それぞれに子こともできます。 すべてのこれらのケースでは、親ウィンドウは、その子ウィンドウを管理し、いくつかのコマンドを転送します。

MDI フレーム ウィンドウは、フレーム ウィンドウは、クイック ウォッチ ウィンドウで、コントロール バーと共に再配置を管理します。 [クイック ウォッチ] ウィンドウで、さらに、すべての MDI 子フレーム ウィンドウを管理します。 次の図は、MDI フレーム ウィンドウ、クイック ウォッチ ウィンドウ、およびその子ドキュメント フレーム ウィンドウ間の関係を示します。

![子ウィンドウの MDI フレーム ウィンドウ](../mfc/media/vc37gb1.gif "子ウィンドウの MDI フレーム ウィンドウ") <br/>
MDI フレーム ウィンドウと子ウィンドウ

MDI フレーム ウィンドウは、1 つを使用する必要がある場合も、現在の MDI 子ウィンドウと組み合わせては機能します。 MDI フレーム ウィンドウは、自分で処理する前に、MDI 子ウィンドウにコマンド メッセージを委任します。

## <a name="what-do-you-want-to-know-more-about"></a>方法については、するして操作を行います

- [ドキュメント フレーム ウィンドウの作成](../mfc/creating-document-frame-windows.md)

- [フレーム ウィンドウ スタイル](../mfc/frame-window-styles-cpp.md)

## <a name="see-also"></a>関連項目

[フレーム ウィンドウの使用](../mfc/using-frame-windows.md)
