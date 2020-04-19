---
title: コンパイラの警告 (レベル 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: c2e9b88125655d9ea0abe3e65500b149289ba83b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393286"
---
# <a name="compiler-warning-level-1-c4952"></a>コンパイラの警告 (レベル 1) C4952

> '*関数*': プログラム データベースにプロファイル データが見つかりません'*pgd_fil*'

コンパイラが、 [/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)の使用時に、 `/LTCG:PGINSTRUMENT` の後で再コンパイルされ、新しい関数 (*function*) を持つ入力モジュールを検出しました。

これは、情報提供の警告です。 この警告を解決するには、 `/LTCG:PGINSTRUMENT`を実行してすべてのテストを再実行し、 `/LTCG:PGOPTIMIZE`を実行します。

`/LTCG:PGOPTIMIZE` が使用されていた場合、この警告はエラーに置き換わります。