---
title: コンパイラの警告 (レベル 1) C4715
ms.date: 11/04/2016
f1_keywords:
- C4715
helpviewer_keywords:
- C4715
ms.assetid: 1c819bf7-0d8b-4f5e-b338-9cc292870439
ms.openlocfilehash: 268a26f5de1bb7f757a8e7cba6d3f5e6ddff882e
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052479"
---
# <a name="compiler-warning-level-1-c4715"></a>コンパイラの警告 (レベル 1) C4715

' function ': すべてのコントロールパスが値を返すわけではありません

指定された関数は、値を返さない可能性があります。

## <a name="example"></a>例

```cpp
// C4715a.cpp
// compile with: /W1 /LD
int func1( int i )
{
   if( i )
   return 3;  // C4715 warning, nothing returned if i == 0
}
```

この警告を回避するには、すべてのパスが関数に戻り値を割り当てるようにコードを変更します。

```cpp
// C4715b.cpp
// compile with: /LD
int func1( int i )
{
   if( i ) return 3;
   else return 0;     // OK, always returns a value
}
```

次の例のように、コードにが返されることがない関数の呼び出しが含まれている可能性があります。

```cpp
// C4715c.cpp
// compile with: /W1 /LD
void fatal()
{
}
int glue()
{
   if(0)
      return 1;
   else if(0)
      return 0;
   else
      fatal();   // C4715
}
```

また、このコードでは、`fatal` が返されないことをコンパイラが認識しないため、警告が生成されます。 このコードによってエラーメッセージが生成されないようにするには、 [__declspec (noreturn)](../../cpp/noreturn.md)を使用して `fatal` を宣言します。