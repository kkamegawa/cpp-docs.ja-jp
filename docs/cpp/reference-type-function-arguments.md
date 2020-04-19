---
title: Reference-Type Function Arguments (参照型関数の引数)
ms.date: 08/27/2018
helpviewer_keywords:
- arguments [C++], function
- functions [C++], parameters
- function parameters [C++], reference-type
- function arguments [C++], reference-type
- passing parameters [C++], reference-type arguments
ms.assetid: 0a70e831-9e76-46c0-821d-aeba13d73cc0
ms.openlocfilehash: 2a0bd21023bd1c6bc14b1f587c85960cf1e8b820
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244183"
---
# <a name="reference-type-function-arguments"></a>Reference-Type Function Arguments (参照型関数の引数)

多くの場合、大きなオブジェクトよりも、関数への参照を渡す方が効率的です。 これにより、コンパイラは、オブジェクトへのアクセスに使用される構文を保持しつつ、オブジェクトのアドレスを渡すことができます。 `Date` 構造体を使用する次の例について考えます。

```cpp
// reference_type_function_arguments.cpp
#include <iostream>

struct Date
{
    short Month;
    short Day;
    short Year;
};

// Create a date of the form DDDYYYY (day of year, year)
// from a Date.
long DateOfYear( Date& date )
{
    static int cDaysInMonth[] = {
        31, 28, 31, 30, 31, 30, 31, 31, 30, 31, 30, 31
    };
    long dateOfYear = 0;

    // Add in days for months already elapsed.
    for ( int i = 0; i < date.Month - 1; ++i )
        dateOfYear += cDaysInMonth[i];

    // Add in days for this month.
    dateOfYear += date.Day;

    // Check for leap year.
    if ( date.Month > 2 &&
        (( date.Year % 100 != 0 || date.Year % 400 == 0 ) &&
        date.Year % 4 == 0 ))
        dateOfYear++;

    // Add in year.
    dateOfYear *= 10000;
    dateOfYear += date.Year;

    return dateOfYear;
}

int main()
{
    Date date{ 8, 27, 2018 };
    long dateOfYear = DateOfYear(date);
    std::cout << dateOfYear << std::endl;
}
```

上記のコードは、メンバー選択演算子を使用して参照渡しで渡された構造体のメンバーにアクセスすることを示しています (**.**) ポインター メンバー選択演算子ではなく (**->**)。

参照型として渡された引数が非ポインター型の構文を観察しますが、ポインター型の 1 つの重要な特性を保持、: として宣言しない限り変更可能な**const**します。 前のコードの意図は `date` オブジェクトを変更することではないため、より適切な関数プロトタイプは次のとおりです。

```cpp
long DateOfYear( const Date& date );
```

このプロトタイプによって、関数 `DateOfYear` が引数を変更しないことが保証されます。

標準変換があるために、参照型を受け取るようにプロトタイプ宣言された任意の関数は、代わりに、同じ型のオブジェクトを受け取ることができます*typename*に*typename*  <strong>&</strong>.

## <a name="see-also"></a>関連項目

[参照](../cpp/references-cpp.md)<br/>
