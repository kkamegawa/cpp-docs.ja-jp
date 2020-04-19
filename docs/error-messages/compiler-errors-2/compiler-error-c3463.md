---
title: コンパイラ エラー C3463
ms.date: 11/04/2016
f1_keywords:
- C3463
helpviewer_keywords:
- C3463
ms.assetid: 153efcc0-085c-4615-84ea-d22942618bdf
ms.openlocfilehash: e4aa8405d9baac61b8d3addead6ac19bbf6fd3b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756592"
---
# <a name="compiler-error-c3463"></a>コンパイラ エラー C3463

'type':型は属性 'implements' で使用できません

[implements](../../windows/implements-cpp.md) 属性に正しくない型が渡されました。 たとえば、 `implements`にインターフェイスを渡すことはできますが、インターフェイスへのポインターを渡すことはできません。

## <a name="example"></a>使用例

次の例では C3463 が生成されます。

```cpp
// C3463.cpp
// compile with: /c
#include <windows.h>
[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface X {};

typedef X* PX;

[ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=PX) ]   // C3463
// try the following line instead
// [ coclass, uuid("00000000-0000-0000-0000-000000000002"), implements(interfaces=X) ]
class CMyClass : public X {};
```
