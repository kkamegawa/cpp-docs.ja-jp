---
title: コンパイラの警告 (レベル 1) C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: dc718e5f7ebe9478ed1bf2a7323db940935cb1d6
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926117"
---
# <a name="compiler-warning-level-1-c4305"></a>コンパイラの警告 (レベル 1) C4305

> '*context*': ' type1 *' から '* *type1*' への切り捨て

## <a name="remarks"></a>Remarks

この警告は、値が初期化時に小さい型に変換されるか、コンストラクター引数として変換されると、情報が失われる場合に発行されます。

## <a name="example"></a>例

このサンプルでは、次の2つの方法でこの警告が表示されます。

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

この問題を解決するには、正しい型の値を使用してを初期化するか、適切な型への明示的なキャストを使用します。 たとえば、 **double** (浮動小数点リテラルの既定の型) ではなく 2.71828 f などの**float**リテラルを使用して、 **float**変数を初期化したり、 **float**引数を受け取るコンストラクターに渡したりします。
