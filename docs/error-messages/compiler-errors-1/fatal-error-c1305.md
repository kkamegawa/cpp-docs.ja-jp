---
title: 致命的なエラー C1305
ms.date: 11/04/2016
f1_keywords:
- C1305
helpviewer_keywords:
- C1305
ms.assetid: 1629c850-e2db-4678-83d8-9bfc85323bc5
ms.openlocfilehash: 988842a0d5e8002ffd1478a2e10a8c88ee971911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397498"
---
# <a name="fatal-error-c1305"></a>致命的なエラー C1305

プロファイル データベース 'pgd_fil' は異なるアーキテクチャ用です。

渡された別のプラットフォーム用に/LTCG:PGINSTRUMENT 操作から生成された .pgd ファイル[/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md)します。 [プロファイル ガイド付き最適化の](../../build/profile-guided-optimizations.md)x86 および x64 プラットフォームで利用できます。 ただし、あるプラットフォーム用に /LTCG:PGINSTRUMENT 操作によって生成された .pgd ファイルを、別のプラットフォームの /LTCG:PGOPTIMIZE への入力として使用することはできません。

このエラーを解決するには、/LTCG:PGINSTRUMENT で作成された .pgd ファイルを同じプラットフォームの /LTCG:PGOPTIMIZE に渡します。