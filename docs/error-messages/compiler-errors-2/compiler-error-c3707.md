---
title: コンパイラ エラー C3707
ms.date: 11/04/2016
f1_keywords:
- C3707
helpviewer_keywords:
- C3707
ms.assetid: ac63a5dd-7a4b-48d2-9f2a-be9cb090134c
ms.openlocfilehash: 6faf035c0f4f68b10b187c56bea4cafc776998cf
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757957"
---
# <a name="compiler-error-c3707"></a>コンパイラ エラー C3707

' function ': ディスパッチインターフェイスには dispid が必要です

`dispinterface` メソッドを使用する場合は、`dispid`に割り当てる必要があります。 このエラーを解決するには、次のサンプルのメソッドの `id` 属性をコメント解除するなどして、`dispinterface` メソッドに `dispid` を割り当てます。 詳細については、「属性の[ディスパッチインターフェイス](../../windows/dispinterface.md)と[id](../../windows/id.md)」を参照してください。

次の例では、C3707 が生成されます。

```cpp
// C3707.cpp
#include <atlbase.h>
#include <atlcom.h>
#include <atlctl.h>

[module(name="xx")];
[dispinterface]
__interface IEvents : IDispatch
{
   HRESULT event1([in] int i);   // C3707
   // try the following line instead
   // [id(1)] HRESULT event1([in] int i);
};

int main() {
}
```
