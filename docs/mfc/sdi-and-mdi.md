---
title: SDI と MDI
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], SDI applications
- frame windows [MFC], MDI applications
- MFC, windows
- single document interface (SDI) [MFC], applications
- MDI [MFC], vs. SDI
ms.assetid: bb7239d9-4759-4f63-bfff-44a04b48c067
ms.openlocfilehash: 725249e5a71e8ee097c641e5972e3cc8bb0e3e33
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62308535"
---
# <a name="sdi-and-mdi"></a>SDI と MDI

MFC では、シングル ドキュメント インターフェイス (SDI) とマルチ ドキュメント インターフェイス (MDI) アプリケーションの両方を簡単に処理します。

SDI アプリケーションでは、一度に 1 つだけ開いているドキュメント フレーム ウィンドウを許可します。 MDI アプリケーションは、複数のドキュメントのフレーム ウィンドウが開いているアプリケーションの同じインスタンスを許可します。 MDI アプリケーションでは、個別のドキュメントを格納している各ウィンドウ内、複数の MDI フレーム ウィンドウ自体には、子ウィンドウを開くことができるがあります。 一部のアプリケーションで、グラフの windows および windows のスプレッドシートなどのさまざまな種類の子ウィンドウができます。 その場合は、メニュー バーでは、さまざまな種類の MDI 子ウィンドウがアクティブ化を変更できます。

> [!NOTE]
>  Windows 95 以降、アプリケーションは通常、SDI のため、オペレーティング システムは、「ドキュメント中心の」ビューを採用しています。

詳細については、次を参照してください。[ドキュメント、ビュー、およびフレームワーク](../mfc/documents-views-and-the-framework.md)します。

## <a name="see-also"></a>関連項目

[クラスを使用した Windows アプリケーションの作成](../mfc/using-the-classes-to-write-applications-for-windows.md)
