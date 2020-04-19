---
title: コンパイラ エラー C2569
ms.date: 11/04/2016
f1_keywords:
- C2569
helpviewer_keywords:
- C2569
ms.assetid: 092bed1e-f631-436c-9586-7750629f6fac
ms.openlocfilehash: 7299fe8daa1fa0fc6e1291bf8c683b33235e8bbf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755526"
---
# <a name="compiler-error-c2569"></a>コンパイラ エラー C2569

' EnumOrUnion ': 列挙型/共用体を基底クラスとして使用することはできません

指定した共用体または列挙体から型を派生させる必要がある場合は、共用体または列挙体をクラスまたは構造体に変更します。

次の例では、C2569 が生成されます。

```cpp
// C2569.cpp
// compile with: /c
union ubase {};
class cHasPubUBase : public ubase {};   // C2569
// OK
struct sbase {};
class cHasPubUBase : public sbase {};
```
