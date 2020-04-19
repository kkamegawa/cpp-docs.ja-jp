---
title: NMAKE の致命的なエラー U1073
ms.date: 11/04/2016
f1_keywords:
- U1073
helpviewer_keywords:
- U1073
ms.assetid: d46bf2dd-400a-4802-9db2-f832e1c97f02
ms.openlocfilehash: 2aa02fd86906bd545373a313fa5e6e409ffb3cf9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366934"
---
# <a name="nmake-fatal-error-u1073"></a>NMAKE の致命的なエラー U1073

'targetname' を作成する方法がわからない

指定されたターゲットが存在しないと、実行するコマンドまたは推論規則を適用はありません。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. ターゲット名のスペルを確認します。

1. 場合*targetname* 、疑似ターゲットは、別の記述ブロックのターゲットとして指定します。

1. 場合*targetname*マクロの呼び出しは、null 文字列に展開されないことを確認します。