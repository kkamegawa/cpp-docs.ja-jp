---
title: ExitInstance メンバー関数
ms.date: 11/04/2016
f1_keywords: []
helpviewer_keywords:
- programs [MFC], terminating
- CWinApp class [MFC], ExitInstance
- ExitInstance method [MFC]
ms.assetid: 5bb597bd-8dab-4d49-8bcf-9c45aa8be4a2
ms.openlocfilehash: c76f588b22ad8ffd1d3dae954c5113feffb62a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405821"
---
# <a name="exitinstance-member-function"></a>ExitInstance メンバー関数

[ExitInstance](../mfc/reference/cwinapp-class.md#exitinstance)クラスのメンバー関数[CWinApp](../mfc/reference/cwinapp-class.md)アプリケーションのコピーを終了すると、通常、ユーザーがアプリケーションの終了結果として毎回と呼びます。

オーバーライド`ExitInstance`グラフィックス デバイス インターフェイス (GDI) のリソースを解放することや、プログラムの実行中に使用されるメモリの割り当てを解除などの特別なクリーンアップ処理を必要があるかどうか。 ただし、ドキュメント、ビューなどの標準的なアイテムのクリーンアップは、これらのオブジェクトに固有のクリーンアップを行うためのオーバーライド可能な他の関数と、フレームワークによって提供されます。

## <a name="see-also"></a>関連項目

[CWinApp: アプリケーション クラス](../mfc/cwinapp-the-application-class.md)
