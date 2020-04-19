---
title: コンパイラエラー C2788
ms.date: 11/04/2016
f1_keywords:
- C2788
helpviewer_keywords:
- C2788
ms.assetid: 8688fc5c-e652-43b4-b407-9c488c76f2db
ms.openlocfilehash: a708e711fd086d31ecd5e8cc9c35679571af48c4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74739572"
---
# <a name="compiler-error-c2788"></a>コンパイラエラー C2788

' identifier ': このオブジェクトに関連付けられている GUID が複数あります。

[__Uuidof](../../cpp/uuidof-operator.md)演算子は、GUID が割り当てられたユーザー定義型、またはそのようなユーザー定義型のオブジェクトを受け取ります。 このエラーは、引数が複数の Guid を持つオブジェクトである場合に発生します。

次の例では、C2788 が生成されます。

```cpp
// C2788.cpp
#include <windows.h>
struct __declspec(uuid("00000001-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000002-0000-0000-0000-000000000000}")) B {};
template <class T, class U> class MyClass {};

typedef MyClass<A,B> MyBadClass;
typedef MyClass<A,A> MyGoodClass;

int main() {
   __uuidof(MyBadClass);    // C2788
   // try the following line instead
   __uuidof(MyGoodClass);
}
```
