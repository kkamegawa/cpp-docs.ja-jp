---
title: 'キャスト演算子: ()'
ms.date: 11/04/2016
helpviewer_keywords:
- cast operators [C++]
- () cast operator
ms.assetid: 4c99eb92-1b19-4a5d-9840-5d8c29b8453e
ms.openlocfilehash: 54345637665736085d812b88f5822a94014eaa74
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345082"
---
# <a name="cast-operator-"></a>キャスト演算子: ()

型キャストは、特定の状況におけるオブジェクトの型の明示的な変換方法を示します。

## <a name="syntax"></a>構文

```
unary-expression ( type-name ) cast-expression
```

## <a name="remarks"></a>Remarks

単項式は、すべてキャスト式と見なされます。

コンパイラは、型キャストが実行された後で、*cast-expression* を *type-name* 型として処理します。 キャストを使用すると、スカラー型オブジェクトの型を他のスカラー型との間で変換できます。 明示的な型キャストは、暗黙的な変換の結果を決定するのと同じ規則によって制限されます。 特定の型の実際のサイズまたは表現から、キャストにさらに制限が課せられる場合があります。

## <a name="example"></a>例

```cpp
// expre_CastOperator.cpp
// compile with: /EHsc
// Demonstrate cast operator
#include <iostream>

using namespace std;

int main()
{
    double x = 3.1;
    int i;
    cout << "x = " << x << endl;
    i = (int)x;   // assign i the integer part of x
    cout << "i = " << i << endl;
}
```

## <a name="example"></a>例

```cpp
// expre_CastOperator2.cpp
// The following sample shows how to define and use a cast operator.
#include <string.h>
#include <stdio.h>

class CountedAnsiString
{
public:
    // Assume source is not null terminated
    CountedAnsiString(const char *pStr, size_t nSize) :
                      m_nSize(nSize)
    {
        m_pStr = new char[sizeOfBuffer];

        strncpy_s(m_pStr, sizeOfBuffer, pStr, m_nSize);
        memset(&m_pStr[m_nSize], '!', 9); // for demonstration purposes.
    }

    // Various string-like methods...

    const char *GetRawBytes() const
    {
        return(m_pStr);
    }

    //
    // operator to cast to a const char *
    //
    operator const char *()
    {
        m_pStr[m_nSize] = '\0';
        return(m_pStr);
    }

    enum
    {
        sizeOfBuffer = 20
    } size;

private:
    char *m_pStr;
    const size_t m_nSize;
};

int main()
{
    const char *kStr = "Excitinggg";
    CountedAnsiString myStr(kStr, 8);

    const char *pRaw = myStr.GetRawBytes();
    printf_s("RawBytes truncated to 10 chars:   %.10s\n", pRaw);

    const char *pCast = myStr; // or (const char *)myStr;
    printf_s("Casted Bytes:   %s\n", pCast);

    puts("Note that the cast changed the raw internal string");
    printf_s("Raw Bytes after cast:   %s\n", pRaw);
}
```

```Output
RawBytes truncated to 10 chars:   Exciting!!
Casted Bytes:   Exciting
Note that the cast changed the raw internal string
Raw Bytes after cast:   Exciting
```

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[明示的な型変換演算子: ()](../cpp/explicit-type-conversion-operator-parens.md)<br/>
[キャスト演算子](../cpp/casting-operators.md)<br/>
[キャスト演算子](../c-language/cast-operators.md)