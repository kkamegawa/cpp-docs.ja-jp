---
title: 既定の引数
ms.date: 11/04/2016
helpviewer_keywords:
- arguments [C++], function
- function declarators
- functions [C++], default arguments
- declaring functions [C++], declarators
- default arguments
- arguments [C++], default
- defaults [C++], arguments
ms.assetid: d32cf516-05cb-4d4d-b169-92f5649fdfa2
ms.openlocfilehash: 5ffc0301e7a89a379a2ea1eda9a113276df7a88e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154517"
---
# <a name="default-arguments"></a>既定の引数

多くの場合、関数には引数がありますが、ほとんど使用されることはありません。既定値で十分です。 これに対処するために、既定の引数機能では、特定の呼び出しで有効な引数だけを関数に指定できます。 この概念を示すために示されている例を検討してください。[関数のオーバー ロード](../cpp/function-overloading.md)します。

```cpp
// Prototype three print functions.
int print( char *s );                  // Print a string.
int print( double dvalue );            // Print a double.
int print( double dvalue, int prec );  // Print a double with a
//  given precision.
```

多くのアプリケーションでは、適切な既定値は `prec` で指定できるので、次の 2 つの関数は不要です。

```cpp
// Prototype two print functions.
int print( char *s );                    // Print a string.
int print( double dvalue, int prec=2 );  // Print a double with a
//  given precision.
```

実装、`print`型の 1 つだけこのような関数が存在するという事実を反映するように関数が若干変更**double**:

```cpp
// default_arguments.cpp
// compile with: /EHsc /c

// Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.

#include <iostream>
#include <math.h>
using namespace std;

int print( double dvalue, int prec ) {
   // Use table-lookup for rounding/truncation.
   static const double rgPow10[] = {
      10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1, 10E0,
         10E1,  10E2,  10E3,  10E4, 10E5,  10E6
   };
   const int iPowZero = 6;
   // If precision out of range, just print the number.
   if( prec >= -6 && prec <= 7 )
      // Scale, truncate, then rescale.
      dvalue = floor( dvalue / rgPow10[iPowZero - prec] ) *
      rgPow10[iPowZero - prec];
   cout << dvalue << endl;
   return cout.good();
}
```

新しい `print` 関数を呼び出すには、次のようなコードを使用します:

```cpp
print( d );    // Precision of 2 supplied by default argument.
print( d, 0 ); // Override default argument to achieve other
//  results.
```

既定の引数を使用する場合は、これらのポイントに注意します。

- 既定の引数は、後続の引数を省略した関数呼び出しでのみ使用されます。既定の引数は、最後の引数である必要があります。 したがって、次のコードは正しくありません。

    ```cpp
    int print( double dvalue = 0.0, int prec );
    ```

- 既定の引数は、以降の宣言で再定義が元と同じでも再定義できません。 したがって、次のコードはエラーになります。

    ```cpp
    // Prototype for print function.
    int print( double dvalue, int prec = 2 );

    ...

    // Definition for print function.
    int print( double dvalue, int prec = 2 )
    {
    ...
    }
    ```

   このコードの問題は、定義での関数宣言が `prec` の既定の引数を定義し直すことです。

- 追加の既定の引数は、後の宣言によって追加できます。

- 既定の引数は、関数へのポインターに対して指定できます。 例:

    ```cpp
    int (*pShowIntVal)( int i = 0 );
    ```