---
title: クラス、構造体、および共用体の中かっこの初期化
description: 任意C++のクラス、構造体、または共用体と共に中かっこの初期化を使用する
ms.date: 11/19/2019
ms.assetid: 3e55c3d6-1c6b-4084-b9e5-221b151402f4
ms.openlocfilehash: a2c9db4572b0dde94c42ec6768a0f3bed7766a96
ms.sourcegitcommit: 15677b0e4d2518847ce59b158990b25c4077e565
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/03/2020
ms.locfileid: "75652625"
---
# <a name="brace-initialization"></a>かっこ初期化

クラスのコンストラクターの定義は、コンストラクターが比較的単純な場合は特に、必ずしも必要ではありません。 ユーザーは、次の例に示すように、均一初期化を使用してクラスまたは構造体のオブジェクトを初期化できます。

```cpp
// no_constructor.cpp
// Compile with: cl /EHsc no_constructor.cpp
#include <time.h>

// No constructor
struct TempData
{
    int StationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

// Has a constructor
struct TempData2
{
    TempData2(double minimum, double maximum, double cur, int id, time_t t) :
       stationId{id}, timeSet{t}, current{cur}, maxTemp{maximum}, minTemp{minimum} {}
    int stationId;
    time_t timeSet;
    double current;
    double maxTemp;
    double minTemp;
};

int main()
{
    time_t time_to_set;

    // Member initialization (in order of declaration):
    TempData td{ 45978, time(&time_to_set), 28.9, 37.0, 16.7 };

    // Default initialization = {0,0,0,0,0}
    TempData td_default{};

    // Uninitialized = if used, emits warning C4700 uninitialized local variable
    TempData td_noInit;

    // Member declaration (in order of ctor parameters)
    TempData2 td2{ 16.7, 37.0, 28.9, 45978, time(&time_to_set) };

    return 0;
}
```

クラスまたは構造体にコンストラクターがない場合は、メンバーがクラス内で宣言されている順序でリスト要素を指定します。 クラスにコンストラクターがある場合は、パラメーターの順序で要素を指定します。 型に既定のコンストラクターがあり、暗黙的または明示的に宣言されている場合、(空のかっこで) 既定のかっこ初期化を使用できます。 たとえば、次のクラスは、既定のかっこ初期化と既定以外のかっこ初期化を使用して初期化できます。

```cpp
#include <string>
using namespace std;

class class_a {
public:
    class_a() {}
    class_a(string str) : m_string{ str } {}
    class_a(string str, double dbl) : m_string{ str }, m_double{ dbl } {}
double m_double;
string m_string;
};

int main()
{
    class_a c1{};
    class_a c1_1;

    class_a c2{ "ww" };
    class_a c2_1("xx");

    // order of parameters is the same as the constructor
    class_a c3{ "yy", 4.4 };
    class_a c3_1("zz", 5.5);
}
```

クラスに既定以外のコンストラクターがある場合、クラス メンバーがかっこ初期化に表示される順序は、対応するパラメーターがコンストラクターに表示される順序になります。メンバーが宣言される順序ではありません (前の例の `class_a` と同様)。 それ以外の場合、宣言されたコンストラクターが型にないときは、メンバーがかっこ初期化に表示される順序とメンバーが宣言される順序は同じです。この場合、必要な数だけパブリック メンバーを初期化できますが、メンバーをスキップすることはできません。 次の例は、宣言されたコンストラクターがないときに、かっこ初期化で使用される順序を示しています。

```cpp
class class_d {
public:
    float m_float;
    string m_string;
    wchar_t m_char;
};

int main()
{
    class_d d1{};
    class_d d1{ 4.5 };
    class_d d2{ 4.5, "string" };
    class_d d3{ 4.5, "string", 'c' };

    class_d d4{ "string", 'c' }; // compiler error
    class_d d5{ "string", 'c', 2.0 }; // compiler error
}
```

既定のコンストラクターが明示的に宣言されていても、削除対象としてマークされている場合は、既定のかっこ初期化は使用できません。

```cpp
class class_f {
public:
    class_f() = delete;
    class_f(string x): m_string { x } {}
    string m_string;
};
int main()
{
    class_f cf{ "hello" };
    class_f cf1{}; // compiler error C2280: attempting to reference a deleted function
}
```

かっこ初期化を使用することができますの初期化をどこでも通常実行 — たとえば、関数パラメーターまたは戻り値として、**new**キーワード。

```cpp
class_d* cf = new class_d{4.5};
kr->add_d({ 4.5 });
return { 4.5 };
```

**/Std: c++ 17**モードでは、空の中かっこの初期化に関する規則の方が若干制限されています。 「[派生コンストラクターと拡張集計の初期化」を](constructors-cpp.md#extended_aggregate)参照してください。

## <a name="initializer_list-constructors"></a>initializer_list コンストラクター

[Initializer_list クラス](../standard-library/initializer-list-class.md)は、コンストラクターとその他のコンテキストで使用できる、指定した型のオブジェクトのリストを表します。 かっこ初期化を使用して、initializer_list を構築できます。

```cpp
initializer_list<int> int_list{5, 6, 7};
```

> [!IMPORTANT]
>  このクラスを使用するには、 [\<initializer_list >](../standard-library/initializer-list.md)ヘッダーを含める必要があります。

`initializer_list` をコピーできます。 この場合、新しいリストのメンバーは、元のリストのメンバーを参照します。

```cpp
initializer_list<int> ilist1{ 5, 6, 7 };
initializer_list<int> ilist2( ilist1 );
if (ilist1.begin() == ilist2.begin())
    cout << "yes" << endl; // expect "yes"
```

標準ライブラリのコンテナー クラスと、`string`、`wstring`、および `regex` にも `initializer_list` コンストラクターが含まれます。 次の例は、これらのコンストラクターでかっこ初期化を行う方法を示しています。

```cpp
vector<int> v1{ 9, 10, 11 };
map<int, string> m1{ {1, "a"}, {2, "b"} };
string s{ 'a', 'b', 'c' };
regex rgx{ 'x', 'y', 'z' };
```


## <a name="see-also"></a>関連項目

[クラスと構造体](../cpp/classes-and-structs-cpp.md)<br/>
[コンストラクター](../cpp/constructors-cpp.md)
