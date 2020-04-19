---
title: リンカ ツール エラー LNK2013
ms.date: 11/04/2016
f1_keywords:
- LNK2013
helpviewer_keywords:
- LNK2013
ms.assetid: 21408e2d-3f56-4d1f-a031-00df70785ed4
ms.openlocfilehash: 4d932a89f1b0bde27f6de2f84b2ed103dab1b1b0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62299069"
---
# <a name="linker-tools-error-lnk2013"></a>リンカ ツール エラー LNK2013

fixup type フィックスアップのオーバーフローです。 ターゲット 'symbol name' が範囲を超えています。

ターゲット シンボルが命令の位置から離れすぎているため、リンカーは必要なアドレスまたはオフセットを指定された命令に収めることができません。

この問題を解決するには、複数のイメージを作成するかを使用して、 [/order](../../build/reference/order-put-functions-in-order.md)命令とターゲットはまとめて近いはオプションです。

シンボルがユーザー定義シンボルであり、コンパイラが生成したシンボルでない場合は、次の処理を実行して、エラーを解決することもできます。

- 静的関数を非静的関数に変更します。

- 静的関数を含むコード セクションを呼び出し側と同じ名前に変更します。

`DUMPBIN /SYMBOLS` を使用して、関数が静的かどうかを調べます。