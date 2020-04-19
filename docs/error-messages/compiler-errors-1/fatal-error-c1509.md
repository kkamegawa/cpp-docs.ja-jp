---
title: 致命的なエラー C1509
ms.date: 11/04/2016
f1_keywords:
- C1509
helpviewer_keywords:
- C1509
ms.assetid: 40dd100d-c6ba-451c-bd26-2c99ec1c36d6
ms.openlocfilehash: efd5b9dd5cdd7ee174bc786c38d9dd841e2ad6ce
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397485"
---
# <a name="fatal-error-c1509"></a>致命的なエラー C1509

コンパイラの制限: 関数 'function' の例外ハンドラが多すぎます。 関数を簡略化します。

コードは、例外ハンドラーの状態 (32,768 状態) での内部制限値を超えています。

最も一般的な原因は、関数がクラスのユーザー定義変数および算術演算子の複雑な式が含まれています。

### <a name="to-fix-by-using-the-following-possible-solutions"></a>以下の可能性がある解決策を使って修正するには

1. 一時変数に共通部分式を割り当てることで式を簡略化します。

1. 関数を小さな関数に分割します。