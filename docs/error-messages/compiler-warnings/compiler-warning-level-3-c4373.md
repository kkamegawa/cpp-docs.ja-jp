---
title: コンパイラの警告 (レベル 3) C4373
ms.date: 11/04/2016
f1_keywords:
- C4373
helpviewer_keywords:
- C4373
ms.assetid: 670c0ba3-b7d6-4aed-b207-1cb84da3bcde
ms.openlocfilehash: 5891d4679b74695f187fb50bb24fe941882fdcc7
ms.sourcegitcommit: a930a9b47bd95599265d6ba83bb87e46ae748949
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/22/2020
ms.locfileid: "76518349"
---
# <a name="compiler-warning-level-3-c4373"></a>コンパイラの警告 (レベル 3) C4373

> '*function*': 仮想関数は '*base_function*' をオーバーライドします。以前のバージョンのコンパイラは、パラメーターの違いが const/volatile 修飾子に限られている場合はオーバーライドしませんでした

## <a name="remarks"></a>Remarks

アプリケーションには、基底クラスの仮想メソッドをオーバーライドする派生クラスのメソッドが含まれ、オーバーライドする側のメソッドのパラメーターは、 [const](../../cpp/const-cpp.md) または [volatile](../../cpp/volatile-cpp.md) 修飾子についてのみ、仮想メソッドのパラメーターと異なります。 つまり、コンパイラでは、基底クラスまたは派生クラスのいずれかにおけるメソッドに、関数参照をバインドする必要があります。

Visual Studio 2008 より前のバージョンのコンパイラでは、関数が基底クラスのメソッドにバインドされ、警告メッセージが発行されます。 それ以降のバージョンのコンパイラは、`const` または `volatile` 修飾子を無視し、派生クラスのメソッドに関数をバインドしてから、警告**C4373**を発行します。 この後者の動作は、C++ 標準に準拠しています。

## <a name="example"></a>使用例

次のコード例では、警告 C4373 が生成されます。 この問題を解決するには、オーバーライドで基本メンバー関数と同じ CV 修飾子を使用するか、オーバーライドを作成しない場合は、派生クラスの関数に別の名前を付けることができます。

```cpp
// c4373.cpp
// compile with: /c /W3
#include <stdio.h>
struct Base
{
    virtual void f(int i) {
        printf("base\n");
    }
};

struct Derived : Base
{
    void f(const int i) {  // C4373
        printf("derived\n");
    }
};

int main()
{
    Derived d;
    Base* p = &d;
    p->f(1);
}
```

```Output
derived
```
