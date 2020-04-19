---
title: リンカー ツールの警告 LNK4037
ms.date: 10/04/2017
f1_keywords:
- LNK4037
helpviewer_keywords:
- LNK4037
ms.assetid: 9ba02fd3-b04f-4679-bab9-26fa82cf09bb
ms.openlocfilehash: 9a8121617e622fc12efe5bd26aac23faf2530f24
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62410305"
---
# <a name="linker-tools-warning-lnk4037"></a>リンカー ツールの警告 LNK4037

>'*symbol*' does not exist; ignored

装飾名*シンボル*を使用して順序付けされませんでした、 [/order](../../build/reference/order-put-functions-in-order.md)プログラムで見つかりませんオプションを指定します。 仕様の確認*シンボル*順序応答ファイルにします。 詳細については、次を参照してください。、 [/ORDER (関数の順序に Put)](../../build/reference/order-put-functions-in-order.md)リンカー オプション。

> [!NOTE]
> 静的関数の名前は、パブリック シンボル名ではないために、リンクは静的関数を注文ことはできません。 ときに **/order**が指定すると、各シンボルが静的である注文の応答ファイル内のこのリンカー警告が生成されるかが見つかりませんでした。