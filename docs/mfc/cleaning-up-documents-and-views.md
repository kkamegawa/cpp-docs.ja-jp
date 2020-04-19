---
title: ドキュメントとビューの後処理
ms.date: 11/04/2016
helpviewer_keywords:
- views [MFC], cleaning up
- documents [MFC], cleaning up
- documents [MFC], closing
ms.assetid: 0c454db2-3644-434d-9e53-8108a7aedfe1
ms.openlocfilehash: 940c768823d26950d9710fb1d1a52e6a1955fead
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62327159"
---
# <a name="cleaning-up-documents-and-views"></a>ドキュメントとビューの後処理

フレームワークが呼び出す最初、ドキュメントが閉じている間、その[DeleteContents](../mfc/reference/cdocument-class.md#deletecontents)メンバー関数。 ドキュメントの操作の実行中にヒープにメモリを割り当てた場合`DeleteContents`割り当てを解除することをお勧めします。

> [!NOTE]
>  ドキュメント データをドキュメントのデストラクターで割り当ては解除する必要があります。 SDI アプリケーションの場合は、ドキュメント オブジェクトを再利用する可能性があります。

ヒープに割り当てられたメモリを解放するビューのデストラクターをオーバーライドできます。

## <a name="see-also"></a>関連項目

[ドキュメントとビューの初期化と後処理](../mfc/initializing-and-cleaning-up-documents-and-views.md)
