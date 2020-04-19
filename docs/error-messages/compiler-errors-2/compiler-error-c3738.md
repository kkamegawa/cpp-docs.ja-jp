---
title: コンパイラ エラー C3738
ms.date: 11/04/2016
f1_keywords:
- C3738
helpviewer_keywords:
- C3738
ms.assetid: dd3ee011-e204-4264-bf3a-da32c4ef7038
ms.openlocfilehash: ffefa0eff23e11412573b8062fa15bb5679923e7
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752770"
---
# <a name="compiler-error-c3738"></a>コンパイラ エラー C3738

' calling_convention ': 明示的なインスタンス化の呼び出し規約は、インスタンス化されているテンプレートの規約と一致しなければなりません

明示的なインスタンス化では、呼び出し規約を指定しないことをお勧めします。 ただし、必要な場合は、呼び出し規則を一致させる必要があります。

## <a name="example"></a>使用例

次の例では、C3738 が生成されます。

```cpp
// C3738.cpp
// compile with: /clr
// processor: x86
#include <stdio.h>
template< class T >
void f ( T arg ) {   // by default calling convention is __cdecl
   printf ( "f: %s\n", __FUNCSIG__ );
}

template
void __stdcall f< int > ( int arg );   // C3738
// try the following line instead
// void f< int > ( int arg );

int main () {
   f(1);
   f< int > ( 1 );
}
```
