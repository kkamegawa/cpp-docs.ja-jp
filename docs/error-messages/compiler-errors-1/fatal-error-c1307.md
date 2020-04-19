---
title: 致命的なエラー C1307
ms.date: 11/04/2016
f1_keywords:
- C1307
helpviewer_keywords:
- C1307
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
ms.openlocfilehash: 1acdda77ac9cbf8d99752de3b78ab9c32bbb4cbc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62338533"
---
# <a name="fatal-error-c1307"></a>致命的なエラー C1307

プロファイル データが集められてからプログラムが編集されました。

使用する場合[/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)リンカーは、/LTCG:PGINSTRUMENT 後に再コンパイルされた入力モジュールを検出およびモジュールが、既存のプロファイル データは関連性がなくなった点に変更されました。 たとえば、再コンパイルされたモジュールの呼び出し先が変更された場合、コンパイラは C1307 を生成します。

このエラーを解決するには、/LTCG:PGINSTRUMENT を実行、すべてのテストの実行を再実行および/LTCG:PGOPTIMIZE を実行します。 実行を/LTCG:PGINSTRUMENT とすべてのテストを再に実行することはできない場合、は、最適化されたイメージを作成する/LTCG:PGOPTIMIZE ではなく/LTCG:PGUPDATE を使用します。