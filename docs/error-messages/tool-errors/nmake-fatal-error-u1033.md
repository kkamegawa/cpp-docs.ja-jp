---
title: NMAKE の致命的なエラー U1033
ms.date: 11/04/2016
f1_keywords:
- U1033
helpviewer_keywords:
- U1033
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
ms.openlocfilehash: 3b1df28e3cd7b27a9e7a130d9d71c1af68db9aec
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324364"
---
# <a name="nmake-fatal-error-u1033"></a>NMAKE の致命的なエラー U1033

構文エラー: 予期しない ' string'

メイクファイルの有効な構文の一部でない文字列。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 山かっこの終了を設定する場合 (**<<**) のインライン ファイル行の先頭には、次のエラーが発生します。

    ```
    syntax error : 'EOF' unexpected
    ```

1. メイクファイルのマクロ定義に等号 (=) が含まれているかどうか (**=**)、次のエラーが発生した先行名または名前が定義されている場合は nothing に展開されるマクロ、なし。

    ```
    syntax error : '=' unexpected
    ```

1. 場合、セミコロン (**;**) ツール内のコメント行にします。INI は、行の先頭に次のエラーが発生します。

    ```
    syntax error : ';' unexpected
    ```

1. ワード プロセッサでメイクファイルが書式設定されている場合、次のエラーが発生します。

    ```
    syntax error : ':' unexpected
    ```