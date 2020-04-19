---
title: リンカー ツールの警告 LNK4219
ms.date: 11/04/2016
f1_keywords:
- LNK4219
helpviewer_keywords:
- LNK4219
ms.assetid: 363fedf4-b10c-4985-811a-55a9fba688d6
ms.openlocfilehash: 7407537b55525bf622fc11cdbdb8e00244e51c18
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410253"
---
# <a name="linker-tools-warning-lnk4219"></a>リンカー ツールの警告 LNK4219

フィックス アップ名前 fixup オーバーフロー。 ターゲット 'ターゲット symbol name' がサンクを挿入する範囲外です。

リンカーでは、場所、アドレスまたはオフセットできなかったターゲット シンボルが命令の位置から離れすぎているために、指定された命令に収まるように状況にサンクが挿入されます。

イメージの順序を変更することがあります (を使用して、 [/order](../../build/reference/order-put-functions-in-order.md)オプション、たとえば) 余分なレベルの間接参照を回避するためにします。