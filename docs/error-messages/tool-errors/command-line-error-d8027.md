---
title: コマンド ライン エラー D8027
ms.date: 11/04/2016
f1_keywords:
- D8027
helpviewer_keywords:
- D8027
ms.assetid: f228220f-0c7f-49a6-a6e0-1f7bd4745aa6
ms.openlocfilehash: d3a7908ec9e7e37d83fd7b928cad2ef256313c40
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62214182"
---
# <a name="command-line-error-d8027"></a>コマンド ライン エラー D8027

'コンポーネント' を実行できません。

コンポーネントの特定のコンパイラまたはリンカー、コンパイラは実行できませんでした。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. メモリ不足のため、コンポーネントを読み込みます。 NMAKE がコンパイラに呼び出される場合は、外、メイクファイル コンパイラを実行します。

1. 現在のオペレーティング システムでは、コンポーネントは実行できませんでした。 確認パス ポイント実行可能ファイルへのオペレーティング システムに適切なします。

1. コンポーネントが壊れています。 セットアップ プログラムを使用して、パッケージ内のディスクからコンポーネントを再コピーします。

1. オプションが正しく指定されていません。 例えば:

    ```
    cl /B1 file1.c
    ```