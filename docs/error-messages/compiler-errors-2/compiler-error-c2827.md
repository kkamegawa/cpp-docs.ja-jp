---
title: コンパイラ エラー C2827
ms.date: 11/04/2016
f1_keywords:
- C2827
helpviewer_keywords:
- C2827
ms.assetid: cb3e5814-0c92-40e4-b620-98578ae3003a
ms.openlocfilehash: 7f1f19b91580bffa1133ae11ab91f2243153a389
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406874"
---
# <a name="compiler-error-c2827"></a>コンパイラ エラー C2827

'operator 演算子' は、単項形式でグローバルに上書きすることはできません。

演算子は、オブジェクトの外部で単項形式を持つことはできません。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. オブジェクトにオーバー ロードされた演算子をローカルに行います。

1. 適切な単項演算子をオーバー ロードを選択します。