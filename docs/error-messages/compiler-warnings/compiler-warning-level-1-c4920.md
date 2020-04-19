---
title: コンパイラの警告 (レベル 1) C4920
ms.date: 11/04/2016
f1_keywords:
- C4920
helpviewer_keywords:
- C4920
ms.assetid: 1e501f2e-93c1-4d27-a4fa-54fc86271ae7
ms.openlocfilehash: 7cbb29c8dae24a87fcd5a32b4cf46d7a8ac4c790
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74050243"
---
# <a name="compiler-warning-level-1-c4920"></a>コンパイラの警告 (レベル 1) C4920

enum enum member member=value は既に enum enum as member=value に示されています

#import に渡す .tlb に 2 つ以上の列挙型で定義された同じシンボルが含まれる場合、この警告は、後に続く同じシンボルが無視され、.tlh ファイル内でコメント アウトされることを示します。

次を含む .tlb を想定します。

```
library MyLib
{
    typedef enum {
        enumMember = 512
    } AProblem;

    typedef enum {
        enumMember = 1024
    } BProblem;
};
```

次の例では C4920 が生成されます。

```cpp
// C4920.cpp
// compile with: /W1
#import "t4920.tlb"   // C4920

int main() {
}
```