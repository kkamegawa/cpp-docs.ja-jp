---
title: デリゲートコンストラクター (C++)
description: のデリゲートコンストラクター C++を使用して、他のコンストラクターを呼び出し、コードの繰り返しを減らします。
ms.date: 11/19/2019
ms.openlocfilehash: 533cdfbeb882f3770cc554b0633611a4ffc2cfbd
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74250698"
---
# <a name="delegating-constructors"></a>コンストラクターのデリゲート

多くのクラスに、パラメーターの検証など、同じような処理を実行するコンストラクターが複数含まれます。

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c() {}
    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) {
        max = my_max > 0 ? my_max : 10;
        min = my_min > 0 && my_min < max ? my_min : 1;
        middle = my_middle < max && my_middle > min ? my_middle : 5;
    }
};
```

繰り返し出現するコードを減らすには、すべての検証を行う関数を追加します。ただし、`class_c` のコードについては、1 つのコンストラクターが作業の一部を他にデリゲートできる方が、理解や保守が簡単になります。 デリゲート コンストラクターを追加するには、`constructor (. . .) : constructor (. . .)` 構文を使用します。

```cpp
class class_c {
public:
    int max;
    int min;
    int middle;

    class_c(int my_max) {
        max = my_max > 0 ? my_max : 10;
    }
    class_c(int my_max, int my_min) : class_c(my_max) {
        min = my_min > 0 && my_min < max ? my_min : 1;
    }
    class_c(int my_max, int my_min, int my_middle) : class_c (my_max, my_min){
        middle = my_middle < max && my_middle > min ? my_middle : 5;
}
};
int main() {

    class_c c1{ 1, 3, 2 };
}
```

前の例では、`class_c(int, int, int)` コンストラクターが最初に `class_c(int, int)` コンストラクターを呼び出し、その後、この呼び出されたコンストラクターが `class_c(int)` を呼び出していることに注意してください。 各コンストラクターが、他のコンストラクターで実行されていない作業のみを行います。

オブジェクトは、呼び出された最初のコンストラクターによって初期化されるため、そのメンバーすべてがこの時点で初期化されます。 ここで示すように、他のコンストラクターにデリゲートされたコンストラクターでは、メンバーの初期化を実行できません。

```cpp
class class_a {
public:
    class_a() {}
    // member initialization here, no delegate
    class_a(string str) : m_string{ str } {}

    //can’t do member initialization here
    // error C3511: a call to a delegating constructor shall be the only member-initializer
    class_a(string str, double dbl) : class_a(str) , m_double{ dbl } {}

    // only member assignment
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string;
};
```

次の例は、静的でないデータ メンバー初期化子の使用例を示しています。 コンストラクターも特定のデータ メンバーを初期化する場合は、メンバーの初期化子がオーバーライドされることに注意してください。

```cpp
class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : class_a(str) { m_double = dbl; }
    double m_double{ 1.0 };
    string m_string{ m_double < 10.0 ? "alpha" : "beta" };
};

int main() {
    class_a a{ "hello", 2.0 };  //expect a.m_double == 2.0, a.m_string == "hello"
    int y = 4;
}
```

コンストラクター デリゲート構文では、コンストラクターの再帰 (Constructor1 が、Constructor1 を呼び出す Constructor2 を呼び出すなど) が誤って作成されるのを防ぐことができず、さらに、スタック オーバーフローが発生するまでエラーがスローされません。 このサイクルを回避する必要があります。

```cpp
class class_f{
public:
    int max;
    int min;

    // don't do this
    class_f() : class_f(6, 3){ }
    class_f(int my_max, int my_min) : class_f() { }
};
```
