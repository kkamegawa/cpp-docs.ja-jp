---
title: sequenced_policy クラス
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_policy
ms.openlocfilehash: 63be7166b84fa452f53baf6b6de16831eb657a23
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68269194"
---
# <a name="sequencedpolicy-class"></a>sequenced_policy クラス

並列アルゴリズムのオーバー ロードを区別する、並列アルゴリズムの実行を並列いない可能性がありますを必要とする一意の型として使用されます。

## <a name="syntax"></a>構文

```cpp
class execution::sequenced_policy;
```

## <a name="remarks"></a>Remarks

使用の並列アルゴリズムの実行中に、 `execution::sequenced_policy` 、キャッチされない例外を使用して、要素アクセス関数の呼び出しが終了した場合、ポリシー`terminate()`呼び出されます。
