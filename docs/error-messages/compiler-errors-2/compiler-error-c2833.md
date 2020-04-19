---
title: コンパイラ エラー C2833
ms.date: 11/04/2016
f1_keywords:
- C2833
helpviewer_keywords:
- C2833
ms.assetid: b9418ce1-e2ee-4599-8959-6fde89c27569
ms.openlocfilehash: c1467a3c67cccf28cc6b9bd0f987fe77b8da8988
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757879"
---
# <a name="compiler-error-c2833"></a>コンパイラ エラー C2833

' operator operator ' は、演算子または型として認識されません。

`operator` 単語には、オーバーライドする演算子または変換する型を指定する必要があります。

マネージ型で定義できる演算子の一覧については、「[ユーザー定義演算子](../../dotnet/user-defined-operators-cpp-cli.md)」を参照してください。

次の例では、C2833 が生成されます。

```cpp
// C2833.cpp
// compile with: /c
class A {};

void operator ::* ();   // C2833
void operator :: ();   // OK
```
