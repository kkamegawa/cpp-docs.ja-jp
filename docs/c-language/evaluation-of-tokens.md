---
title: トークンの評価
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152548"
---
# <a name="evaluation-of-tokens"></a>トークンの評価

コンパイラは、トークンを解釈するときに、1 つのトークンにできる限り多くの文字を含めてから、次のトークンに進みます。 このような動作をするため、空白で正しく区切られていない場合、意図したとおりにトークンが解釈されない可能性があります。 次のような式があるとします。

```
i+++j
```

この例では、コンパイラは、3 個のプラス記号から最初に最も長い可能な演算子 (`++`) を取り出し、次に残りの正符号を加算演算子 (`+`) として処理します。 したがって、この式は `(i++) + (j)` ではなく、`(i) + (++j)` として評価されます。 この場合や同様の場合、空白とかっこを使用してあいまいさを回避し、式が適切に評価されるようにします。

**Microsoft 固有の仕様**

C コンパイラは Ctrl + Z 文字をファイル終端 (EOF) として扱います。 Ctrl + Z 以降のテキストは無視されます。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[C トークン](../c-language/c-tokens.md)
