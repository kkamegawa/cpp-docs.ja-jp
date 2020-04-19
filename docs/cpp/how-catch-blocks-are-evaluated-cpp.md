---
title: Catch ブロックの評価方法 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- try-catch keyword [C++], catchable types
- catch keyword [C++], types of catch handlers
- C++ exception handling, catch handlers
- exception handling, catching and deleting exceptions
- types [C++], exception handling
ms.assetid: 202dbf07-8ace-4b3b-b3ae-4b45c275e0b4
ms.openlocfilehash: 027dc87923a588ea891dbf6dd835e2baba75a1cb
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74245854"
---
# <a name="how-catch-blocks-are-evaluated-c"></a>Catch ブロックの評価方法 (C++)

C++ では任意の型の例外をスローすることができますが、一般に std::exception から派生した型をスローすることが推奨されます。 C++例外は、スローされた例外と同じ型を指定する**catch**ハンドラー、または任意の型の例外をキャッチできるハンドラーによってキャッチできます。

スローされる例外の型がクラスである場合、クラスは基底クラスも持つため、その例外は、例外の型の基底クラスを受け入れるハンドラー、および例外の型の基底クラスへの参照を受け入れるハンドラーでキャッチできます。 例外が参照によってキャッチされた場合、それは実際にスローされた例外オブジェクトにバインドされることに注意してください。それ以外の場合は、コピーになります (関数の引数とほぼ同じ)。

例外がスローされると、次の種類の**catch**ハンドラーによってキャッチされる可能性があります。

- 任意の型を受け取ることができるハンドラー (省略記号構文を使用)。

- 例外オブジェクトと同じ型を受け入れるハンドラー。これはコピーであるため、 **const**修飾子と**volatile**修飾子は無視されます。

- 例外オブジェクトと同じ型への参照を受け入れるハンドラー。

- 例外オブジェクトと同じ型の**const**または**volatile**形式への参照を受け入れるハンドラー。

- Exception オブジェクトと同じ型の基底クラスを受け取るハンドラー。これはコピーであるため、 **const**修飾子と**volatile**修飾子は無視されます。 基底クラスの**catch**ハンドラーは、派生クラスの**catch**ハンドラーの前に配置することはできません。

- 例外オブジェクトと同じ型の基底クラスへの参照を受け取るハンドラー。

- Exception オブジェクトと同じ型の基底クラスの**const**または**volatile**形式への参照を受け入れるハンドラー。

- スローされたポインター オブジェクトが標準的なポインター変換規則によって変換できるポインターを受け取るハンドラー。

**Catch**ハンドラーが表示される順序は重要です。これは、特定の**try**ブロックのハンドラーが外観の順序で検証されるためです。 たとえば、派生クラスのハンドラーの前に基底クラスのハンドラーを配置するとエラーになります。 一致する**catch**ハンドラーが見つかると、後続のハンドラーは検証されません。 そのため、省略記号の**catch**ハンドラーは**try**ブロックの最後のハンドラーである必要があります。 例 :

```cpp
// ...
try
{
    // ...
}
catch( ... )
{
    // Handle exception here.
}
// Error: the next two handlers are never examined.
catch( const char * str )
{
    cout << "Caught exception: " << str << endl;
}
catch( CExcptClass E )
{
    // Handle CExcptClass exception here.
}
```

この例では、省略記号の**catch**ハンドラーだけが検査されます。

## <a name="see-also"></a>参照

[例外C++とエラー処理に関する最新のベストプラクティス](../cpp/errors-and-exception-handling-modern-cpp.md)
