---
title: 標準のコマンド ルーティングのオーバーライド
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 5383c1053894d44e23baf51b19ac3df4e60158e5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410162"
---
# <a name="overriding-the-standard-command-routing"></a>標準のコマンド ルーティングのオーバーライド

まれなケースで標準フレームワークのルーティングのいくつかのバリエーションを実装する必要がありますとオーバーライドできます。 つまり、1 つまたは複数のクラスでオーバーライドすることでルーティングを変更する`OnCmdMsg`それらのクラスでします。 そのための操作を行います。

- クラスには、既定以外のオブジェクトを渡す順序を中断します。

- 新しい既定以外のオブジェクトまたはコマンド ターゲットでさらにコマンドを渡すこと可能性があります。

ルーティングにいくつかの新しいオブジェクトを挿入する場合、クラスは、コマンド ターゲット クラスである必要があります。 オーバーライド元のバージョンで`OnCmdMsg`、オーバーライドしているバージョンを呼び出してください。 参照してください、 [OnCmdMsg](../mfc/reference/ccmdtarget-class.md#oncmdmsg)クラスのメンバー関数`CCmdTarget`で、 *MFC リファレンス*のようなクラスのバージョンと`CView`と`CDocument`例については、指定されたソース コードにします。

## <a name="see-also"></a>関連項目

[フレームワークがハンドラーを呼び出す方法](../mfc/how-the-framework-calls-a-handler.md)
