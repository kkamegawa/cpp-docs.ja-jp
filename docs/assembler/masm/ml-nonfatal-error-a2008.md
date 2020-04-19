---
title: ML の致命的でないエラー A2008
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 79448f9358ffd422b8b25a69ac2b83693e58560e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318047"
---
# <a name="ml-nonfatal-error-a2008"></a>ML の致命的でないエラー A2008

**構文エラー:**

現在の場所のトークンによって構文エラーが発生しました。

次のいずれかが発生している可能性があります。

- ディレクティブにドットプレフィックスが追加されたか、ディレクティブから省略されました。

- 予約語 ( **C**や**サイズ**など) が識別子として使用されました。

- 現在のプロセッサまたはコプロセッサ選択で使用できなかった命令が使用されました。

- 比較実行時演算子 (`==`など) が、関係演算子 ( [EQ](operator-eq.md)など) ではなく、条件付きアセンブリステートメントで使用されました。

- 命令またはディレクティブに指定されたオペランドが少なすぎます。

- Obsolete ディレクティブが使用されました。

## <a name="see-also"></a>関連項目

[ML エラー メッセージ](ml-error-messages.md)
