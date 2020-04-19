---
title: 式エバリュエーター エラー CXX0033
ms.date: 11/04/2016
f1_keywords:
- CXX0033
helpviewer_keywords:
- CAN0033
- CXX0033
ms.assetid: 0bd62c5b-de89-481f-9b12-88fe84805afe
ms.openlocfilehash: 8563eb2fbc24c6ad8db639d2e227802412a16090
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397056"
---
# <a name="expression-evaluator-error-cxx0033"></a>式エバリュエーター エラー CXX0033

OMF の種類の情報でのエラー

実行可能ファイルには、デバッグの有効なオブジェクト モジュール形式 (OMF) がありませんでした。

このエラーは、can0033 と同じものと同じです。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 実行可能ファイルは、このバージョンの Visual C リンカーによって作成されませんでした。 LINK.exe の現在のバージョンを使用してオブジェクト コードを再リンクします。

1. .Exe ファイルが壊れている可能性があります。 再コンパイルし、プログラムを再リンクします。