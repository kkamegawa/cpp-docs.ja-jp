---
title: コンパイラ エラー C2862
ms.date: 11/04/2016
f1_keywords:
- C2862
helpviewer_keywords:
- C2862
ms.assetid: c04d8499-b799-48a1-9fb4-7902a0b0ac8e
ms.openlocfilehash: cd14f310a00202dce73f091dee46a4605858b698
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755084"
---
# <a name="compiler-error-c2862"></a>コンパイラ エラー C2862

' interface ': インターフェイスにはパブリックメンバーのみを含めることができます

Protected メンバーと private メンバーは、他のメンバー関数からのみアクセスできます。 このようなメンバーは、そのメンバーの実装を提供しない場合があるため、インターフェイスでは使用されません。

次の例では、C2862 が生成されます。

```cpp
// C2862.cpp
// compile with: /c
#include <unknwn.h>

[object, uuid="60719E20-EF37-11D1-978D-0000F805D73B"]
__interface IMyInterface {
   HRESULT mf1(void);   // OK
protected:
   HRESULT mf2(int *b);   // C2862
private:
   HRESULT mf3(int *c);   // C2862
};
```
