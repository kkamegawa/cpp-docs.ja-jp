---
title: コンパイラ エラー C2287
ms.date: 11/04/2016
f1_keywords:
- C2287
helpviewer_keywords:
- C2287
ms.assetid: 64556299-4e1f-4437-88b7-2464fc0b95bb
ms.openlocfilehash: 234d0e85d0d6772340797fb6880e0ef79d4191ef
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759140"
---
# <a name="compiler-error-c2287"></a>コンパイラ エラー C2287

' class ': 継承表現: ' representation1 ' は、必要な ' representation2 ' よりも一般的ではありません

クラスが、必要以上に単純な表現で宣言されています。

次の例では、C2287 が生成されます。

```cpp
// C2287.cpp
// compile with: /vmg /c
class __single_inheritance X;
class __single_inheritance Y;

struct A { };
struct B { };
struct X : A, B { };  // C2287  X uses multiple inheritance
struct Y : A { };  // OK
```
