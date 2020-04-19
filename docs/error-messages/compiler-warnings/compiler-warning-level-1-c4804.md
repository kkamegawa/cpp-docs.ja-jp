---
title: コンパイラの警告 (レベル 1) C4804
ms.date: 11/04/2016
f1_keywords:
- C4804
helpviewer_keywords:
- C4804
ms.assetid: 069e8f44-3ef6-43bb-8524-4116fc6eea83
ms.openlocfilehash: 97ad076325b11329896d98367fb3ac311ec5ded9
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051564"
---
# <a name="compiler-warning-level-1-c4804"></a>コンパイラの警告 (レベル 1) C4804

' operation ': 操作中に型 ' bool ' を使用することは安全ではありません

この警告は、予期しない方法で `bool` 変数または値を使用した場合に発生します。 たとえば、負の単項演算子 ( **-** ) や補数演算子 (`~`) などの演算子を使用すると、C4804 が生成されます。 コンパイラは、式を評価します。

## <a name="example"></a>例

次の例では、C4804 が生成されます。

```cpp
// C4804.cpp
// compile with: /W1

int main()
{
   bool i = true;
   if (-i)   // C4804, remove the '-' to resolve
   {
      i = false;
   }
}
```