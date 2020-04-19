---
title: 致命的なエラー C1045
ms.date: 11/04/2016
f1_keywords:
- C1045
helpviewer_keywords:
- C1045
ms.assetid: 766c2f89-4ecd-4281-adaa-14b270cc0829
ms.openlocfilehash: 4503580e33bf89fc913b1941b4f9916f59e397d0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243815"
---
# <a name="fatal-error-c1045"></a>致命的なエラー C1045

コンパイラの制限 : 外部参照の入れ子のレベルがコンパイラの限界を超えています。

入れ子になった外部参照がコンパイラの制限を超えています。 入れ子になった外部参照は、 `extern` "C++" などの外部リンケージの種類で許可されます。 エラーを解決するには、入れ子になった外部参照の数を減らします。