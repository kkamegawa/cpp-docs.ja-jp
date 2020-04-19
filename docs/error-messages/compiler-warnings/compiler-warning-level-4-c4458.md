---
title: コンパイラの警告 (レベル 4) C4458
ms.date: 11/04/2016
f1_keywords:
- C4458
helpviewer_keywords:
- C4458
ms.assetid: 7bdaa1b1-0caf-4d68-98c4-6bdd441c23fb
ms.openlocfilehash: 9e5eb8dc44968332abc097bfbd16b48e3240695c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391453"
---
# <a name="compiler-warning-level-4-c4458"></a>コンパイラの警告 (レベル 4) C4458

> 宣言 '*識別子*' クラスのメンバーを非表示にします

宣言*識別子*ローカル スコープで、同じ名前の宣言を非表示に*識別子*クラス スコープでします。 この警告を参照するかを把握できます。*識別子*このスコープでの解決をローカルに宣言されたバージョンに、クラス メンバー バージョンではなく、可能性のあるユーザーの意図ができない可能性があります。 この問題を解決するには、クラス メンバーの名前と競合しないローカル変数名の提供をお勧めします。

## <a name="example"></a>例

次の例では、ため、C4458 が生成されますパラメーター`x`し、ローカル変数`y`で`member_fn`クラスにデータ メンバーと同じ名前があります。 この問題を解決するには、異なる名前をパラメーターとローカル変数を使用します。

```cpp
// C4458_hide.cpp
// compile with: cl /W4 /c C4458_hide.cpp

struct S {
    int x;
    float y;
    void member_fn(long x) {   // C4458
        double y;  // C4458
        y = x;
        // To fix this issue, change the parameter name x
        // and local name y to something that does not
        // conflict with the data member names.
    }
} s;
```
