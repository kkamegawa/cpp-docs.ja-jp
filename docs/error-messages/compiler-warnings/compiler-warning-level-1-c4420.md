---
title: コンパイラの警告 (レベル 1) C4420
ms.date: 11/04/2016
f1_keywords:
- C4420
helpviewer_keywords:
- C4420
ms.assetid: 44a37754-7ddd-4764-a5f7-d33e05c20091
ms.openlocfilehash: a4a7e91e7845cc0fc25d5a6fad16ae7b7e327952
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408174"
---
# <a name="compiler-warning-level-1-c4420"></a>コンパイラの警告 (レベル 1) C4420

'operator': 演算子は使用できません代わりに 'operator' を使用する。実行時チェックを侵害する可能性があります。

使用する場合、この警告が生成された、 [/rtcv させる](../../build/reference/rtc-run-time-error-checks.md)(新規/削除の確認をベクトル) とベクトル形式が見つかりませんでした。 この場合、非ベクター形式が使用されます。

/Rtcv を正しく動作させるためには、コンパイラが常に呼び出しベクトル形式の[新しい](../../cpp/new-operator-cpp.md)/[削除](../../cpp/delete-operator-cpp.md)ベクター構文を使用した場合。