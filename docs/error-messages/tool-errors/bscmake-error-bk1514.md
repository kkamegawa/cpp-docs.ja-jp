---
title: BSCMAKE エラー BK1514
ms.date: 11/04/2016
f1_keywords:
- BK1514
helpviewer_keywords:
- BK1514
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
ms.openlocfilehash: 410c24b67e76bb2d412e1594abbb4a668c79aa1e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324481"
---
# <a name="bscmake-error-bk1514"></a>BSCMAKE エラー BK1514

すべての。SBR ファイルが切り捨てファイル名に見つかりませんでした。

指定されている更新プログラムの .sbr ファイルのいずれも、元の参照情報 (.bsc) ファイルの一部であった。 このエラーの原因となった .sbr ファイルの名前を検索するには、読み取り、 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md)前に警告します。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. .Sbr または .bsc ファイルに指定されたファイル名が間違っています。

1. 破損した .bsc ファイルには、BSCMAKE の処理を再構築が必要です。