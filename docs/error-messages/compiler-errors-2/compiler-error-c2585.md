---
title: コンパイラ エラー C2585
ms.date: 11/04/2016
f1_keywords:
- C2585
helpviewer_keywords:
- C2585
ms.assetid: 05bb1a9c-28fb-4a88-a1b5-aea85ebdee1c
ms.openlocfilehash: 812ab15aacd1f6a215c6a5beb7781983859fe858
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62360503"
---
# <a name="compiler-error-c2585"></a>コンパイラ エラー C2585

'type' に明示的な変換があいまいです。

型変換では、1 つ以上の結果を生成できます。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. 多重継承に基づく、クラスまたは構造体の型から変換します。 変換関数または演算子がスコープ解決演算子を使用する必要があります型は複数回、同じ基本クラスを継承している場合 (`::`) の変換に使用する継承されたクラスを指定します。

1. 同じ変換を行う変換演算子およびコンス トラクターを定義されています。