---
title: ドキュメント テンプレート クラス
ms.date: 11/04/2016
f1_keywords:
- vc.classes.document
helpviewer_keywords:
- document templates [MFC], classes
ms.assetid: 901749e9-8048-44a0-b5e2-361554650a73
ms.openlocfilehash: 2589bc8f04e791f73529af91ffb148c2c717cd08
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62164990"
---
# <a name="document-template-classes"></a>ドキュメント テンプレート クラス

ドキュメント テンプレート オブジェクトがドキュメント、ビュー、および、新しいドキュメントのフレーム ウィンドウ オブジェクトの作成を調整またはビューを作成します。

[CDocTemplate](../mfc/reference/cdoctemplate-class.md)<br/>
ドキュメント テンプレートの基本クラスです。 このクラスを直接; 使用はしないでください。代わりに、このクラスから派生したその他のドキュメント テンプレート クラスのいずれかを使用します。

[CMultiDocTemplate](../mfc/reference/cmultidoctemplate-class.md)<br/>
マルチ ドキュメント インターフェイス (MDI) 内のドキュメントのテンプレート。 MDI アプリケーションには、複数のドキュメントを同時に開くことができます。

[CSingleDocTemplate](../mfc/reference/csingledoctemplate-class.md)<br/>
シングル ドキュメント インターフェイス (SDI) 内のドキュメントのテンプレート。 SDI アプリケーションでは、同時に開く 1 つだけのドキュメントがあります。

## <a name="related-class"></a>関連クラス

[CCreateContext](../mfc/reference/ccreatecontext-structure.md)<br/>
構造体は、ドキュメント、ビュー、フレーム ウィンドウ オブジェクトの作成を調整するウィンドウの作成関数には、ドキュメント テンプレートで渡されます。

## <a name="see-also"></a>関連項目

[クラスの概要](../mfc/class-library-overview.md)
