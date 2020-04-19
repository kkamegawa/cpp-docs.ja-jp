---
title: コンパイラ エラー C3553
ms.date: 11/04/2016
f1_keywords:
- C3553
helpviewer_keywords:
- C3553
ms.assetid: 7f84bf37-6419-4ad3-ab30-64266100b930
ms.openlocfilehash: 219592f2403904f9923e84bfd4539a22cddd02de
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345466"
---
# <a name="compiler-error-c3553"></a>コンパイラ エラー C3553

> decltype には型ではなく式を指定してください

`decltype()` キーワードでは、型の名前ではなく、引数として式を指定する必要があります。 たとえば、次のコード フラグメントの最後のステートメントではエラー C3553 が生成されます。

```cpp
int x = 0;
decltype(x+1);
decltype(int); // C3553
```