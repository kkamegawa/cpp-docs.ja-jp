---
title: Reference-Type Function Returns (参照型関数の戻り値)
ms.date: 11/04/2016
helpviewer_keywords:
- function return types [C++], reference type
- data types [C++], function return types
- functions [C++], return types
ms.assetid: 5b73be1d-2dc7-41df-ab0a-adcba36f2ad1
ms.openlocfilehash: a2d7fa9ddbc1d4a2f922b5a20930e150ae991f38
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62403439"
---
# <a name="reference-type-function-returns"></a>Reference-Type Function Returns (参照型関数の戻り値)

関数は、参照型を返すように宣言できます。 このような宣言をする場合は、次の 2 つの理由があります。

- 返される情報がかなり大きなオブジェクトになるため、参照を返す方がコピーを返すよりも効率が高い。

- 関数の型が左辺値となる必要がある。

- 関数が戻るとき、参照先オブジェクトはスコープ外に出ません。

ラージ オブジェクトを渡す方が効率的であることができますよう*に*参照によって関数を指定することも大きなオブジェクトを返すより効率的な*から*参照によって関数。 参照戻しプロトコルを使用すると、オブジェクトを返す前に一時的な場所にコピーする必要がなくなります。

参照戻り値の型は、関数を左辺値に評価する必要がある場合にも役立ちます。 ほとんどのオーバーロードされた演算子 (特に代入演算子) は、このカテゴリに分類されます。 オーバー ロードされた演算子は、「[オーバー ロードされた演算子](../cpp/operator-overloading.md)します。

## <a name="example"></a>例

`Point` の例を考えます。

```cpp
// refType_function_returns.cpp
// compile with: /EHsc

#include <iostream>
using namespace std;

class Point
{
public:
// Define "accessor" functions as
//  reference types.
unsigned& x();
unsigned& y();
private:
// Note that these are declared at class scope:
unsigned obj_x;
unsigned obj_y;
};

unsigned& Point :: x()
{
return obj_x;
}
unsigned& Point :: y()
{
return obj_y;
}

int main()
{
Point ThePoint;
// Use x() and y() as l-values.
ThePoint.x() = 7;
ThePoint.y() = 9;

// Use x() and y() as r-values.
cout << "x = " << ThePoint.x() << "\n"
<< "y = " << ThePoint.y() << "\n";
}
```

## <a name="output"></a>出力

```Output
x = 7
y = 9
```

`x` 関数と `y` 関数が、参照型を返すように宣言されていることに注意してください。 これらの関数は、代入ステートメントのどちら側にも使用できます。

main 関数のスコープに ThePoint オブジェクトが残っており、参照メンバーが動作し続けていて安全にアクセスできる点に注目してください。

参照型の宣言には、次のような場合を除き、初期化子を含める必要があります。

- 明示的な**extern**宣言

- クラス メンバーの宣言

- クラス内の宣言

- 関数の引数または関数の戻り値の型の宣言

## <a name="caution-returning-address-of-local"></a>ローカルのアドレスを返す際の注意

ローカル スコープでオブジェクトを宣言する場合、関数が戻るときにそのオブジェクトは破棄されます。 関数がそのオブジェクトへの参照を返す場合、実行時に呼び出し元が null 参照の使用を試みると、その参照によるアクセス違反がおそらく発生します。

```cpp
// C4172 means Don’t do this!!!
Foo& GetFoo()
{
    Foo f;
    ...
    return f;
} // f is destroyed here
```

この場合、コンパイラで警告:`warning C4172: returning address of local variable or temporary`します。 単純なプログラムで、メモリ位置が上書きされる前に呼び出し元がその参照にアクセスする場合には、アクセス違反が発生しない場合もあります。 これは全くの運任せです。 警告に留意してください。

## <a name="see-also"></a>関連項目

[参照](../cpp/references-cpp.md)