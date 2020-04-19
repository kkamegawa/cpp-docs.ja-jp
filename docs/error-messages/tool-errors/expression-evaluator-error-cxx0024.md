---
title: 式エバリュエーター エラー CXX0024
ms.date: 11/04/2016
f1_keywords:
- CXX0024
helpviewer_keywords:
- CXX0024
- CAN0024
ms.assetid: eca6adbd-8ff2-4f51-a1cc-a2e9d5d0a47d
ms.openlocfilehash: 93f8389ed3959d5747e46c1234fd8d2eae0f1ae5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359840"
---
# <a name="expression-evaluator-error-cxx0024"></a>式エバリュエーター エラー CXX0024

操作には、左辺値が必要があります。

左辺値に評価されない式は左辺値を必要とする操作に指定されました。

左辺値 (代入ステートメントの左側にある可能性があるためにとように呼ばれます) は、メモリの場所を参照する式です。

たとえば、`buffer[count]`特定のメモリ位置を指すが左辺値が無効です。 論理比較`zed != 0`メモリ アドレスが TRUE または FALSE に評価されるため、有効な左辺値ではありません。

このエラーは、can0024 と同じものと同じです。