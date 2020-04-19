---
title: parallel_unsequenced_policy クラス
ms.date: 04/18/2019
f1_keywords:
- execution/std::execution::parallel_unsequenced_policy
ms.openlocfilehash: 92b4e3ce3743fdd3d5ba112a333b2306829b95d4
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268784"
---
# <a name="parallelunsequencedpolicy-class"></a>parallel_unsequenced_policy クラス

並列アルゴリズムの実行の並列化されベクター化ことを示し、並列アルゴリズムのオーバー ロードを明確に一意の型として使用されます。

## <a name="syntax"></a>構文

```cpp
class execution::parallel_unsequenced_policy;
```

## <a name="remarks"></a>Remarks

使用の並列アルゴリズムの実行中に、 `execution::parallel_unsequenced_policy` 、キャッチされない例外を使用して、要素アクセス関数の呼び出しが終了した場合、ポリシー`terminate()`呼び出されます。
