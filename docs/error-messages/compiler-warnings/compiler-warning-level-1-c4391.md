---
title: コンパイラの警告 (レベル 1) C4391
ms.date: 11/04/2016
f1_keywords:
- C4391
helpviewer_keywords:
- C4391
ms.assetid: 95c6182c-fae9-4174-8f7b-98aa352e68ca
ms.openlocfilehash: 60b68906697f76d56ff6c0e13f1b4ec105ef1c25
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966117"
---
# <a name="compiler-warning-level-1-c4391"></a>コンパイラの警告 (レベル 1) C4391

' signature ': 組み込み関数の戻り値の型が正しくありません。 ' type ' が必要です

コンパイラ組み込みの関数宣言の戻り値の型が正しくありません。 結果のイメージが正常に実行されない可能性があります。

この警告を修正するには、宣言を修正するか、宣言を削除して、適切なヘッダーファイルを #include します。

次の例では、C4391 が生成されます。

```cpp
// C4391.cpp
// compile with: /W1
// processor: x86
// uncomment the following line and delete the line that
// generated the warning to resolve
// #include "xmmintrin.h"

#ifdef  __cplusplus
extern "C" {
#endif

extern void _mm_load_ss(float *p);   // C4391

#ifdef  __cplusplus
}
#endif

int main()
{
}
```