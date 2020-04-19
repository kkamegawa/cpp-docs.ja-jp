---
title: ドキュメントとビューの初期化
ms.date: 11/04/2016
helpviewer_keywords:
- initializing documents [MFC]
- documents [MFC], initializing
- views [MFC], initializing
- initializing objects [MFC], document objects
- initializing views [MFC]
ms.assetid: 33cb8643-8a16-478c-bc26-eccc734e3661
ms.openlocfilehash: 0cf9faecbb7e0d74c2199a1a829aa68241e1c019
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62297113"
---
# <a name="initializing-documents-and-views"></a>ドキュメントとビューの初期化

ドキュメント クラスは、両方の方法をサポートする必要がありますので、2 つの異なる方法でドキュメントが作成されます。 最初に、ユーザーは、ファイルの新しいコマンドを使用して、新しい空の文書を作成できます。 その場合は、オーバーライドでドキュメントを初期化、[でも実質的](../mfc/reference/cdocument-class.md#onnewdocument)クラスのメンバー関数[CDocument](../mfc/reference/cdocument-class.md)します。 次に、ユーザーは、ファイルから内容を読み取る新しい文書を作成するのに、[ファイル] メニュー、開いているコマンドを使用できます。 その場合は、オーバーライドでドキュメントを初期化、[かまいません](../mfc/reference/cdocument-class.md#onopendocument)クラスのメンバー関数`CDocument`します。 両方の初期化が同じ場合は、両方のオーバーライドから一般的なメンバー関数を呼び出すことができますまたは`OnOpenDocument`呼び出せる`OnNewDocument`をクリーンなドキュメントを初期化して、ファイルを開く操作を完了します。

ビューは、ドキュメントの作成後に作成されます。 ビューを初期化するために最適なタイミングは、フレームワークのドキュメント、フレーム ウィンドウ、およびビューの作成が完了した後です。 オーバーライドすることで、ビューを初期化することができます、 [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)のメンバー関数[CView](../mfc/reference/cview-class.md)します。 再初期化または調整する必要がある場合は、ドキュメントの変更されるたびに、オーバーライドすることができます[OnUpdate](../mfc/reference/cview-class.md#onupdate)します。

## <a name="see-also"></a>関連項目

[ドキュメントとビューの初期化と後処理](../mfc/initializing-and-cleaning-up-documents-and-views.md)
