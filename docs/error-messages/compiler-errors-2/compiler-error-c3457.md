---
title: コンパイラ エラー C3457
ms.date: 11/04/2016
f1_keywords:
- C3457
helpviewer_keywords:
- C3457
ms.assetid: 5c1e366a-fa75-4cca-b9a3-86d4ebe4090e
ms.openlocfilehash: 813b1c085cb0464880cb400b6200f9574220bd71
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62363727"
---
# <a name="compiler-error-c3457"></a>コンパイラ エラー C3457

'attribute': 属性は、名前が指定されていない引数をサポートしていません

CLR カスタム属性やコンパイラ属性とは異なり、ソースの注釈属性は名前付き引数のみをサポートします。

## <a name="example"></a>例

次の例では C3457 が生成されます。

```
#include "SourceAnnotations.h"
[vc_attributes::Post( 1 )] int f();   // C3457
[vc_attributes::Post( Valid=vc_attributes::Yes )] int f2();   // OK
```