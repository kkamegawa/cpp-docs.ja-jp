---
title: コンパイラ エラー C3372
ms.date: 11/04/2016
f1_keywords:
- C3372
helpviewer_keywords:
- C3372
ms.assetid: 38ee39ed-03ff-4e6d-9104-f1977b96645d
ms.openlocfilehash: 3ce3424559ff58dd36d6f2544a9d85c958f2ab3a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758594"
---
# <a name="compiler-error-c3372"></a>コンパイラ エラー C3372

最低 1 つのインターフェイスをコクラスの属性 'source' に指定しなければなりません

特定の属性では、パラメーターとしてインターフェイス名を渡す必要があります。

次の例では C3372 が生成されます。

```cpp
// C3372.cpp
#include <windows.h>
[module(name="MyModule")];

[ object, uuid(373a1a4c-469b-11d3-a6b0-00c04f79ae8f) ]
__interface IMyIface {
   HRESULT f1();
};
// to resolve, pass an interface name to the source attribute
// for example, source(IMyIface)
[ coclass, uuid(373a1a4d-469b-11d3-a6b0-00c04f79ae8f), source,
  default(IMyIface) ] // C3372
class CMyClass {
};

int main() {
}
```
