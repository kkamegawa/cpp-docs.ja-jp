---
title: decltype (C++)
ms.date: 11/04/2016
f1_keywords:
- decltype_cpp
helpviewer_keywords:
- operators [C++], decltype
- decltype operator
- operators [C++], type of an expression
- operators [C++], deduce expression type
ms.assetid: 6dcf8888-8196-4f13-af50-51e3797255d4
ms.openlocfilehash: 0a4e9eb015df056dfe2a35da18cfa50875ced432
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222458"
---
# <a name="decltype--c"></a>decltype (C++)

**decltype**型指定子は、指定された式の型を生成します。 **decltype**と共に指定子を入力、 [auto キーワード](../cpp/auto-cpp.md)テンプレートのライブラリを作成する開発者を主に役に立ちます。 使用**auto**と**decltype**テンプレート関数の戻り値を宣言する型は、テンプレート引数の型に依存します。 または、使用して**auto**と**decltype**を別の関数の呼び出しをラップし、ラップされた関数の戻り値の型を返すテンプレート関数を宣言します。

## <a name="syntax"></a>構文

```
decltype( expression )
```

### <a name="parameters"></a>パラメーター

|パラメーター|説明|
|---------------|-----------------|
|*式 (expression)*|任意の式を指定します。 詳細については、次を参照してください。[式](../cpp/expressions-cpp.md)します。|

## <a name="return-value"></a>戻り値

種類、*式*パラメーター。

## <a name="remarks"></a>Remarks

**Decltype**型指定子は、Visual Studio 2010 またはそれ以降のバージョンでサポートされて、ネイティブまたはマネージ コードで使用できます。 `decltype(auto)` (C++14) は Visual Studio 2015 以降でサポートされています。

コンパイラの種類を決定する、次の規則を使用して、*式*パラメーター。

- 場合、*式*パラメーターは、識別子または[クラス メンバーに対するアクセス](../cpp/member-access-operators-dot-and.md)、`decltype(expression)`によってという名前のエンティティの型である*式*します。 このようなエンティティが存在しない場合、または*式*パラメーター名のオーバー ロードされた関数のセットをコンパイラがエラー メッセージが生成されます。

- 場合、*式*パラメーターが関数またはオーバー ロードされた演算子関数では、呼び出し`decltype(expression)`は関数の戻り値の型。 オーバーロードされた演算子を囲んでいるかっこは無視されます。

- 場合、*式*パラメーターは、[右辺値](../cpp/lvalues-and-rvalues-visual-cpp.md)、`decltype(expression)`の型である*式*します。 場合、*式*パラメーターは、[左辺値](../cpp/lvalues-and-rvalues-visual-cpp.md)、`decltype(expression)`は、[左辺値参照](../cpp/lvalue-reference-declarator-amp.md)の型に*式*します。

次のコード例に示しますのいくつかの使用、 **decltype**指定子を入力します。 最初に次のステートメントを記述したとします。

```cpp
int var;
const int&& fx();
struct A { double x; }
const A* a = new A();
```

次に、4 つによって返される型を調べる**decltype**次の表のステートメント。

|ステートメント|型|メモ|
|---------------|----------|-----------|
|`decltype(fx());`|`const int&&`|[右辺値参照](../cpp/rvalue-reference-declarator-amp-amp.md)を**const int**します。|
|`decltype(var);`|**int**|変数 `var` の型。|
|`decltype(a->x);`|**double**|メンバー アクセスの型。|
|`decltype((a->x));`|`const double&`|内側のかっこは、ステートメントをメンバー アクセスではなく式として評価します。 `a`として宣言されている、`const`ポインター型はへの参照を**const 倍**します。|

## <a name="decltype-and-auto"></a>decltype および auto

C++ 14 で使用できます`decltype(auto)`いない後続の戻り値の型テンプレート関数の戻り値の型を宣言すると、テンプレート引数の型に依存します。

C++ 11 で使用することができます、 **decltype**と同時に後続の戻り値の型指定子を入力、**auto**キーワード、テンプレート関数の戻り値の型を宣言するは、そのテンプレートの種類によって異なります。引数。 たとえば、テンプレート関数の戻り値の型がテンプレート引数の型に依存している次のコード例について考えます。 コードの例で、*不明な*プレース ホルダーでは、戻り値の型を指定できないことを示します。

```cpp
template<typename T, typename U>
UNKNOWN func(T&& t, U&& u){ return t + u; };
```

導入に伴い、 **decltype**型指定子により、開発者は、テンプレート関数によって返される式の型を取得します。 使用して、*代替関数宣言の構文*後で、表示される、**auto**キーワード、および**decltype**宣言指定子を入力、 *指定された遅延*型を返します。 遅延指定された戻り値の型は、宣言がコード化されたときではなく、コンパイルされたときに決定します。

次のプロトタイプは代替関数宣言の構文について説明します。 なお、 **const**と**volatile**修飾子、および**throw** [例外の指定](../cpp/exception-specifications-throw-cpp.md)は省略可能です。 *Function_body*プレース ホルダーは、関数の動作を指定する複合ステートメントを表します。 コーディングのプラクティスとして、*式*内のプレース ホルダー、 **decltype**ステートメントがで指定された式に一致する必要があります、**return**文では、に存在する場合、*function_body*します。

**auto** *function_name* **(** *パラメーター*<sub>opt</sub> **)** **const**<sub>opt</sub> **volatile**<sub>opt</sub> **->** **decltype (** *式* **)** **throw**<sub>opt</sub> **{** *function_body* **};**

次のコード例では、`myFunc` テンプレート関数の遅延指定された戻り値の型は、テンプレート引数 `t` と `u` の型によって決まります。 コーディングのプラクティスとして、このコード例もで右辺値参照と`forward`関数テンプレートは、サポート*完全転送*します。 詳細については、「[右辺値参照宣言子: &&](../cpp/rvalue-reference-declarator-amp-amp.md)」を参照してください。

```cpp
//C++11
template<typename T, typename U>
auto myFunc(T&& t, U&& u) -> decltype (forward<T>(t) + forward<U>(u))
        { return forward<T>(t) + forward<U>(u); };

//C++14
template<typename T, typename U>
decltype(auto) myFunc(T&& t, U&& u)
        { return forward<T>(t) + forward<U>(u); };
```

## <a name="decltype-and-forwarding-functions-c11"></a>Decltype および転送関数 (C++11)

転送関数は、他の関数の呼び出しをラップします。 関数テンプレートで、引数、またはそれらの引数を含む式の結果を別の関数に転送する場合を考えます。 さらに、転送関数は、他の関数を呼び出した結果を返します。 このシナリオでは、転送関数の戻り値の型は、ラップされた関数の戻り値の型と同じである必要があります。

このシナリオではなく適切な型式を記述することはできません、 **decltype**指定子を入力します。 **Decltype**型指定子は、関数が参照型を返すかどうかに関する必要な情報が失われないため、ジェネリック転送関数を使用します。 転送関数のコード例については、前の `myFunc` テンプレート関数の例を参照してください。

## <a name="example"></a>例

次のコード例は、テンプレート関数 `Plus()` の遅延指定の戻り値の型を宣言します。 `Plus`関数と 2 つのオペランドを処理する、 **operator +** オーバー ロードします。 その結果、プラス演算子 (+) と `Plus` 関数の戻り値の型の解釈は、関数の引数の型によって異なります。

```cpp
// decltype_1.cpp
// compile with: cl /EHsc decltype_1.cpp

#include <iostream>
#include <string>
#include <utility>
#include <iomanip>

using namespace std;

template<typename T1, typename T2>
auto Plus(T1&& t1, T2&& t2) ->
   decltype(forward<T1>(t1) + forward<T2>(t2))
{
   return forward<T1>(t1) + forward<T2>(t2);
}

class X
{
   friend X operator+(const X& x1, const X& x2)
   {
      return X(x1.m_data + x2.m_data);
   }

public:
   X(int data) : m_data(data) {}
   int Dump() const { return m_data;}
private:
   int m_data;
};

int main()
{
   // Integer
   int i = 4;
   cout <<
      "Plus(i, 9) = " <<
      Plus(i, 9) << endl;

   // Floating point
   float dx = 4.0;
   float dy = 9.5;
   cout <<
      setprecision(3) <<
      "Plus(dx, dy) = " <<
      Plus(dx, dy) << endl;

   // String
   string hello = "Hello, ";
   string world = "world!";
   cout << Plus(hello, world) << endl;

   // Custom type
   X x1(20);
   X x2(22);
   X x3 = Plus(x1, x2);
   cout <<
      "x3.Dump() = " <<
      x3.Dump() << endl;
}
```

```Output
Plus(i, 9) = 13
Plus(dx, dy) = 13.5
Hello, world!
x3.Dump() = 42
```

## <a name="example"></a>例

**Visual Studio 2017 以降:** コンパイラは、テンプレートは宣言ではなくインスタンス化されるときに、decltype 引数を解析します。 その結果、decltype 引数に非依存の特殊化が見つかった場合、インスタンス化時まで遅延されずにすぐに処理され、結果として発生したエラーは、その時点で診断されます。

次の例は、宣言時に発生するこのようなコンパイラ エラーを示しています。

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT> class IsCallable
{
public:
   struct BadType {};
   template <class U>
   static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>
   template <class U>
   static BadType Test(...);
   static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

## <a name="requirements"></a>必要条件

Visual Studio 2010 またはそれ以降のバージョン。

`decltype(auto)` Visual Studio 2015 またはそれ以降が必要です。