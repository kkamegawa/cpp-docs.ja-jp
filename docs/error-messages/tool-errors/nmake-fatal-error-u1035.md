---
title: NMAKE の致命的なエラー U1035
ms.date: 11/04/2016
f1_keywords:
- U1035
helpviewer_keywords:
- U1035
ms.assetid: 68f0cc59-007e-4109-ac30-7ac4ac447e6d
ms.openlocfilehash: 9c4055bb99243f7d20c1da90aef7b916c46c2749
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324338"
---
# <a name="nmake-fatal-error-u1035"></a>NMAKE の致命的なエラー U1035

構文エラー: 予想 ':' または '=' 区切り記号

いずれかにコロン (**:**) または等号 (=) (**=**) が必要です。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. ターゲットの後ろにコロンがありません。

1. 1 文字のターゲットの後にコロンと a:) などの領域がありません。 NMAKE でドライブの指定と、解釈されます。

1. 推論規則の後ろにコロンがありません。

1. マクロ定義は、等号 (=) で後にありませんでした。

1. 後ろに円記号の文字 (**\\**) に新しい行にコマンドを引き続き使用されました。

1. NMAKE の構文規則に従っていない文字列が表示されます。

1. ワード プロセッサでメイクファイルが書式設定されます。