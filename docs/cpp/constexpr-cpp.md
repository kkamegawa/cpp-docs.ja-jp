---
title: constexpr (C++)
description: 言語 constexpr キーワードC++のガイド。
ms.date: 01/28/2020
f1_keywords:
- constexpr_cpp
ms.assetid: c6458ccb-51c6-4a16-aa61-f69e6f4e04f7
no-loc:
- constexpr
- const
- inline
- goto
- try
- if
- switch
- for
- while
ms.openlocfilehash: 4f34eef3217377ab50a2d80d42b5bea4b054c5be
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821780"
---
# <a name="opno-locconstexpr-c"></a>constexpr (C++)

キーワード **constexpr** は c++ 11 で導入され、c++ 14 で改良されました。 これは、*定数式*を意味します。 **const** と同様に、変数に適用できます。コードが値を変更しようとしたときにコンパイラエラーが発生します。 **const** とは異なり、 **constexpr** は関数およびクラスコンストラクターにも適用できます。 **constexpr** は、値 (戻り値) が定数であり、可能であればコンパイル時に計算されることを示します。

**constexpr** 整数値は、テンプレート引数や配列宣言など、const 整数が必要な場所で使用できます。 また、値が実行時ではなくコンパイル時に計算されると、プログラムの実行速度が向上し、使用するメモリが少なくなります。

コンパイル時の定数計算の複雑さと、コンパイル時の潜在的な影響を制限するために、C++ 14 標準では定数式の型が[リテラル型](trivial-standard-layout-and-pod-types.md#literal_types)である必要があります。

## <a name="syntax"></a>構文

> **constexpr** *リテラル型* *識別子* **=** *定数式* **\**
> **constexpr** *リテラル型* *識別子* **{** *定数式* **}** **;** \
> **constexpr** *リテラル型* *識別子* **(** *params* **)** **;** \
> **constexpr** *.ctor* **(** *params* **)** **;**

## <a name="parameters"></a>パラメーター

*params*\
1つ以上のパラメーター。それぞれがリテラル型である必要があり、それ自体が定数式である必要があります。

## <a name="return-value"></a>戻り値

**constexpr** の変数または関数は、[リテラル型](trivial-standard-layout-and-pod-types.md#literal_types)を返す必要があります。

## <a name="opno-locconstexpr-variables"></a>constexpr 変数

**const** 変数と **constexpr** 変数の主な違いは、 **const** 変数の初期化を実行時まで延期できることです。 **constexpr** 変数は、コンパイル時に初期化する必要があります。  すべての **constexpr** 変数が **const** ます。

- 変数は、リテラル型を持ち、初期化されている場合に **constexpr** で宣言できます。 初期化がコンストラクターによって実行される場合は、コンストラクターを **constexpr** として宣言する必要があります。

- 参照は、両方の条件が満たされた場合に **constexpr** として宣言できます。参照されるオブジェクトは定数式によって初期化され、初期化中に呼び出された暗黙の変換も定数式です。

- **constexpr** 変数または関数のすべての宣言には、 **constexpr** 指定子が必要です。

```cpp
constexpr float x = 42.0;
constexpr float y{108};
constexpr float z = exp(5, 3);
constexpr int i; // Error! Not initialized
int j = 0;
constexpr int k = j + 1; //Error! j not a constant expression
```

## <a name="constexpr_functions"></a>constexpr 関数

**constexpr** 関数は、コンパイル時にコードを必要とする場合に、戻り値が計算できるである関数です。 コードを使用するには、コンパイル時に **constexpr** 変数を初期化するか、非型テンプレート引数を指定する必要があります。 引数が値 **constexpr** 場合、 **constexpr** 関数は、コンパイル時の定数を生成します。 **constexpr** 以外の引数を使用して呼び出された場合、またはコンパイル時に値が必要ない場合は、実行時に通常の関数のように値が生成されます。 (この2つの動作により、同じ関数の **constexpr** と非 **constexpr** バージョンを記述する必要がなくなります)。

**constexpr** 関数またはコンストラクターは、暗黙的に **inline** ます。

constexpr の関数には、次の規則が適用されます。

- **constexpr** 関数は、[リテラル型](trivial-standard-layout-and-pod-types.md#literal_types)のみを受け入れて返す必要があります。

- **constexpr** 関数は再帰的に使用できます。

- [仮想](../cpp/virtual-cpp.md)にすることはできません。 外側のクラスに仮想基底クラスがある場合、コンストラクターを **constexpr** として定義することはできません。

- 本体は `= default` または `= delete` として定義できます。

- 本文には、 **goto** ステートメントや **try** ブロックを含めることはできません。

- 非 **constexpr** テンプレートの明示的な特殊化は、 **constexpr** として宣言できます。

- **constexpr** テンプレートの明示的な特殊化は、 **constexpr** する必要もありません。

次の規則は、Visual Studio 2017 以降の **constexpr** 関数に適用されます。

- これには、 **if** と **switch** のステートメント、および **for** 、範囲ベースの **for** 、 **while** 、および**dowhile** を含むすべてのループステートメントが含まれる場合があります。

- ローカル変数宣言が含まれている場合がありますが、変数を初期化する必要があります。 これはリテラル型である必要があり、**静的**またはスレッドローカルにすることはできません。 ローカルで宣言された変数は、 **const** する必要がなく、変化する可能性があります。

- **constexpr** **静的**でないメンバー関数は、暗黙的に **const** する必要はありません。

```cpp
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};
```

> [!TIP]
> Visual Studio デバッガーでは、最適化されていないデバッグビルドをデバッグするときに、コンパイル時にブレークポイントを配置することによって **constexpr** 関数が評価されているかどうかを判断できます。 ブレークポイントにヒットすると、実行時に関数が呼び出されます。  ヒットしなければ、コンパイル時に関数が呼び出されます。

## <a name="extern-opno-locconstexpr"></a>extern constexpr

[/Zc: externConstexpr](../build/reference/zc-externconstexpr.md)コンパイラオプションにより、コンパイラは[外部リンケージ](../c-language/external-linkage.md)を**extern constexpr** を使用して宣言された変数に適用します。 以前のバージョンの Visual Studio では、既定で、または **/zc: externConstexpr**が指定されている場合、visual studio は**extern**キーワードが使用されている場合でも、 **constexpr** の変数への内部リンケージを適用します。 **/Zc: externConstexpr**オプションは、Visual Studio 2017 更新プログラム15.6 以降で使用でき、既定ではオフになっています。 [/Permissive-](../build/reference/permissive-standards-conformance.md)オプションでは **/zc: externConstexpr**が有効になっていません。

## <a name="example"></a>使用例

次の例は **constexpr** 変数、関数、およびユーザー定義型を示しています。 `main()`の最後のステートメントでは、コンパイル時に値が認識される必要がないため、 **constexpr** メンバー関数 `GetValue()` は実行時の呼び出しです。

```cpp
// constexpr.cpp
// Compile with: cl /EHsc /W4 constexpr.cpp
#include <iostream>

using namespace std;

// Pass by value
constexpr float exp(float x, int n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp(x * x, n / 2) :
        exp(x * x, (n - 1) / 2) * x;
};

// Pass by reference
constexpr float exp2(const float& x, const int& n)
{
    return n == 0 ? 1 :
        n % 2 == 0 ? exp2(x * x, n / 2) :
        exp2(x * x, (n - 1) / 2) * x;
};

// Compile-time computation of array length
template<typename T, int N>
constexpr int length(const T(&)[N])
{
    return N;
}

// Recursive constexpr function
constexpr int fac(int n)
{
    return n == 1 ? 1 : n * fac(n - 1);
}

// User-defined type
class Foo
{
public:
    constexpr explicit Foo(int i) : _i(i) {}
    constexpr int GetValue() const
    {
        return _i;
    }
private:
    int _i;
};

int main()
{
    // foo is const:
    constexpr Foo foo(5);
    // foo = Foo(6); //Error!

    // Compile time:
    constexpr float x = exp(5, 3);
    constexpr float y { exp(2, 5) };
    constexpr int val = foo.GetValue();
    constexpr int f5 = fac(5);
    const int nums[] { 1, 2, 3, 4 };
    const int nums2[length(nums) * 2] { 1, 2, 3, 4, 5, 6, 7, 8 };

    // Run time:
    cout << "The value of foo is " << foo.GetValue() << endl;
}
```

## <a name="requirements"></a>要件

Visual Studio 2015 以降。

## <a name="see-also"></a>関連項目

[宣言と定義](../cpp/declarations-and-definitions-cpp.md)\
[const](../cpp/const-cpp.md)
