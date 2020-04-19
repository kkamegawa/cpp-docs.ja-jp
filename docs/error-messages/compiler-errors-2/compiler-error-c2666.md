---
title: コンパイラエラー C2666
ms.date: 11/04/2016
f1_keywords:
- C2666
helpviewer_keywords:
- C2666
ms.assetid: 78364d15-c6eb-439a-9088-e04a0176692b
ms.openlocfilehash: ca779269d573e3e5d270fccad6afe6220083fa42
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755994"
---
# <a name="compiler-error-c2666"></a>コンパイラエラー C2666

' identifier ': 数値のオーバーロードに似た変換があります

オーバーロードされた関数または演算子があいまいです。   あいまいさを解決するために、仮パラメーターリストがコンパイラに似ている場合があります。  このエラーを解決するには、1つまたは複数の実際のパラメーターを明示的にキャストします。

次の例では、C2666 が生成されます。

```cpp
// C2666.cpp
struct complex {
   complex(double);
};

void h(int,complex);
void h(double, double);

int main() {
   h(3,4);   // C2666
}
```

このエラーは、Visual Studio .NET 2003 で実行されたコンパイラ準拠作業の結果としても生成されます。

- 二項演算子とポインター型へのユーザー定義変換

- 修飾変換は id 変換と同じではありません

二項演算子 \<、>、\<=、および > = の場合、渡されたパラメーターは、オペランドの型に変換するユーザー定義の変換演算子をパラメーターの型が定義する場合に、オペランドの型に暗黙的に変換されるようになりました。 あいまいさが生じる可能性があります。

Visual Studio .NET 2003 と visual Studio .NET の両方のバージョンの Visual C++studio で有効なコードについては、関数構文を使用してクラス演算子を明示的に呼び出します。

## <a name="example"></a>使用例

```cpp
// C2666b.cpp
#include <string.h>
#include <stdio.h>

struct T
{
    T( const T& copy )
    {
        m_str = copy.m_str;
    }

    T( const char* str )
    {
        int iSize = (strlen( str )+ 1);
        m_str = new char[ iSize ];
        if (m_str)
            strcpy_s( m_str, iSize, str );
    }

    bool operator<( const T& RHS )
    {
        return m_str < RHS.m_str;
    }

    operator char*() const
    {
        return m_str;
    }

    char* m_str;
};

int main()
{
    T str1( "ABCD" );
    const char* str2 = "DEFG";

    // Error - Ambiguous call to operator<()
    // Trying to convert str1 to char* and then call
    // operator<( const char*, const char* )?
    //  OR
    // trying to convert str2 to T and then call
    // T::operator<( const T& )?

    if( str1 < str2 )   // C2666

    if ( str1.operator < ( str2 ) )   // Treat str2 as type T
        printf_s("str1.operator < ( str2 )\n");

    if ( str1.operator char*() < str2 )   // Treat str1 as type char*
        printf_s("str1.operator char*() < str2\n");
}
```

## <a name="example"></a>使用例

次の例では、C2666 が生成されます。

```cpp
// C2666c.cpp
// compile with: /c

enum E
{
    E_A,   E_B
};

class A
{
    int h(const E e) const {return 0; }
    int h(const int i) { return 1; }
    // Uncomment the following line to resolve.
    // int h(const E e) { return 0; }

    void Test()
    {
        h(E_A);   // C2666
        h((const int) E_A);
        h((int) E_A);
    }
};
```
