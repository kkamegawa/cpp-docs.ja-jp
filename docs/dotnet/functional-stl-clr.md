---
title: functional (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- <cliext/functional>
- cliext::binary_delegate
- cliext::binary_delegate_noreturn
- cliext::binary_negate
- cliext::bind1st
- cliext::bind2nd
- cliext::binder1st
- cliext::binder2nd
- cliext::divides
- cliext::equal_to
- cliext::greater
- cliext::greater_equal
- cliext::less
- cliext::less_equal
- cliext::logical_and
- cliext::logical_not
- cliext::logical_or
- cliext::minus
- cliext::modulus
- cliext::multiplies
- cliext::negate
- cliext::not_equal_to
- cliext::not1
- cliext::not2
- cliext::plus
- cliext::unary_delegate
- cliext::unary_delegate_noreturn
- cliext::unary_negate
helpviewer_keywords:
- <functional> header [STL/CLR]
- <cliext/functional> header [STL/CLR]
- functional functions [STL/CLR]
- binary_delegate function [STL/CLR]
- binary_delegate_noreturn function [STL/CLR]
- binary_negate function [STL/CLR]
- bind1st function [STL/CLR]
- bind2nd function [STL/CLR]
- binder1st function [STL/CLR]
- binder2nd function [STL/CLR]
- divides function [STL/CLR]
- equal_to function [STL/CLR]
- greater function [STL/CLR]
- greater_equal function [STL/CLR]
- less function [STL/CLR]
- less_equal function [STL/CLR]
- logical_and function [STL/CLR]
- logical_not function [STL/CLR]
- logical_or function [STL/CLR]
- minus function [STL/CLR]
- modulus function [STL/CLR]
- multiplies function [STL/CLR]
- negate function [STL/CLR]
- not_equal_to function [STL/CLR]
- not1 function [STL/CLR]
- not2 function [STL/CLR]
- plus function [STL/CLR]
- unary_delegate function [STL/CLR]
- unary_delegate_noreturn function [STL/CLR]
- unary_negate function [STL/CLR]
ms.assetid: 88738b8c-5d37-4375-970e-a4442bf5efde
ms.openlocfilehash: f4a99ea972c6d2ea9b9721664cc75dec257fd7b3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62393754"
---
# <a name="functional-stlclr"></a>functional (STL/CLR)

STL/CLR のヘッダーを含める`<cliext/functional>`を定義する、さまざまなテンプレート クラスと関連するテンプレートのデリゲートと関数。

## <a name="syntax"></a>構文

```
#include <functional>
```

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cliext/機能 >

**Namespace:** cliext

## <a name="declarations"></a>宣言

|Delegate|説明|
|--------------|-----------------|
|[binary_delegate (STL/CLR)](#binary_delegate)|2 つの引数のデリゲート。|
|[binary_delegate_noreturn (STL/CLR)](#binary_delegate_noreturn)|2 つの引数のデリゲートを返す**void**します。|
|[unary_delegate (STL/CLR)](#unary_delegate)|引数が 1 つのデリゲート。|
|[unary_delegate_noreturn (STL/CLR)](#unary_delegate_noreturn)|返すデリゲートの引数が 1 つ**void**します。|

|クラス|説明|
|-----------|-----------------|
|[binary_negate (STL/CLR)](#binary_negate)|2 つの引数ファンクタを否定するファンクタ。|
|[binder1st (STL/CLR)](#binder1st)|2 つの引数ファンクタを最初の引数をバインドするファンクタ。|
|[binder2nd (STL/CLR)](#binder2nd)|2 つの引数ファンクタを 2 番目の引数をバインドするファンクタ。|
|[divides (STL/CLR)](#divides)|ファンクタを分割します。|
|[equal_to (STL/CLR)](#equal_to)|比較ファンクタ。|
|[greater (STL/CLR)](#greater)|大きい比較ファンクタ。|
|[greater_equal (STL/CLR)](#greater_equal)|以上の比較ファンクタ。|
|[less (STL/CLR)](#less)|以下の比較ファンクタ。|
|[less_equal (STL/CLR)](#less_equal)|少ないか等しい比較ファンクタ。|
|[logical_and (STL/CLR)](#logical_and)|論理 AND ファンクタ。|
|[logical_not (STL/CLR)](#logical_not)|論理ファンクターではありません。|
|[logical_or (STL/CLR)](#logical_or)|論理 OR ファンクタ。|
|[minus (STL/CLR)](#minus)|ファンクタを減算します。|
|[modulus (STL/CLR)](#modulus)|剰余ファンクタ。|
|[multiplies (STL/CLR)](#multiplies)|ファンクタを乗算します。|
|[negate (STL/CLR)](#negate)|否定の引数を返すファンクタ。|
|[not_equal_to (STL/CLR)](#not_equal_to)|非等値比較ファンクタ。|
|[plus (STL/CLR)](#plus)|ファンクタを追加します。|
|[unary_negate (STL/CLR)](#unary_negate)|引数が 1 つファンクタを否定するファンクタ。|

|関数|説明|
|--------------|-----------------|
|[bind1st (STL/CLR)](#bind1st)|引数とファンクターの binder1st が生成されます。|
|[bind2nd (STL/CLR)](#bind2nd)|引数とファンクターの binder2nd が生成されます。|
|[not1 (STL/CLR)](#not1)|ファンクター用の unary_negate が生成されます。|
|[not2 (STL/CLR)](#not2)|ファンクター用の binary_negate が生成されます。|

## <a name="members"></a>メンバー

## <a name="binary_delegate"></a> binary_delegate (STL/CLR)

Genereic クラスには、2 つの引数のデリゲートがについて説明します。 これを使用してその引数と戻り値の型の観点からデリゲートを指定します。

### <a name="syntax"></a>構文

```cpp
generic<typename Arg1,
    typename Arg2,
    typename Result>
    delegate Result binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>パラメーター

*arg1*<br/>
最初の引数の型。

*Arg2*<br/>
2 番目の引数の型。

*結果*<br/>
戻り値の型。

### <a name="remarks"></a>Remarks

Genereic デリゲートでは、2 つの引数の関数について説明します。

場合に注意してください。

`binary_delegate<int, int, int> Fun1;`

`binary_delegate<int, int, int> Fun2;`

種類`Fun1`と`Fun2`は、シノニムの中に。

`delegate int Fun1(int, int);`

`delegate int Fun2(int, int);`

同じ型ではありません。

### <a name="example"></a>例

```cpp
// cliext_binary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

bool key_compare(wchar_t left, wchar_t right)
    {
    return (left < right);
    }

typedef cliext::binary_delegate<wchar_t, wchar_t, bool> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    System::Console::WriteLine("compare(L'a', L'a') = {0}",
        kcomp(L'a', L'a'));
    System::Console::WriteLine("compare(L'a', L'b') = {0}",
        kcomp(L'a', L'b'));
    System::Console::WriteLine("compare(L'b', L'a') = {0}",
        kcomp(L'b', L'a'));
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(L'a', L'a') = False
compare(L'a', L'b') = True
compare(L'b', L'a') = False
```

## <a name="binary_delegate_noreturn"></a> binary_delegate_noreturn (STL/CLR)

Genereic クラスの説明を返す 2 つの引数のデリゲート**void**します。 これを使用して、引数の観点からデリゲートを指定します。

### <a name="syntax"></a>構文

```cpp
generic<typename Arg1,
    typename Arg2>
    delegate void binary_delegate(Arg1, Arg2);
```

#### <a name="parameters"></a>パラメーター

*arg1*<br/>
最初の引数の型。

*Arg2*<br/>
2 番目の引数の型。

### <a name="remarks"></a>Remarks

Genereic デリゲートを返す 2 つの引数関数を記述します**void**します。

場合に注意してください。

`binary_delegate_noreturn<int, int> Fun1;`

`binary_delegate_noreturn<int, int> Fun2;`

種類`Fun1`と`Fun2`は、シノニムの中に。

`delegate void Fun1(int, int);`

`delegate void Fun2(int, int);`

同じ型ではありません。

### <a name="example"></a>例

```cpp
// cliext_binary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void key_compare(wchar_t left, wchar_t right)
    {
    System::Console::WriteLine("compare({0}, {1}) = {2}",
        left, right, left < right);
    }

typedef cliext::binary_delegate_noreturn<wchar_t, wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ kcomp = gcnew Mydelegate(&key_compare);

    kcomp(L'a', L'a');
    kcomp(L'a', L'b');
    kcomp(L'b', L'a');
    System::Console::WriteLine();
    return (0);
    }
```

```Output
compare(a, a) = False
compare(a, b) = True
compare(b, a) = False
```

## <a name="binary_negate"></a> binary_negate (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、返す論理ストアドの 2 つの引数ファンクターのではありません。 これを使用してそのストアド ファンクターの観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Fun>
    ref class binary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    explicit binary_negate(Fun% functor);
    binary_negate(binary_negate<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*楽しむ*<br/>
ストアド関数記号の型。

## <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|
|stored_function_type|関数記号の型。|

|メンバー|説明|
|------------|-----------------|
|binary_negate|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^()|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、別の 2 つの引数ファンクタを格納する 2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`論理が返されるように、オブジェクトが関数として呼び出された場合、2 つの引数で呼び出されたストアド ファンクターのではありません。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_binary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="bind1st"></a> bind1st (STL/CLR)

生成、`binder1st`引数とファンクタ。

### <a name="syntax"></a>構文

```cpp
template<typename Fun,
    typename Arg>
    binder1st<Fun> bind1st(Fun% functor,
        Arg left);
```

#### <a name="template-parameters"></a>テンプレート パラメーター

*arg*<br/>
引数の型。

*楽しむ*<br/>
関数記号の型。

#### <a name="function-parameters"></a>関数のパラメーター

*ファンクター*<br/>
ラップするファンクタ。

*left*<br/>
ラップする最初の引数。

### <a name="remarks"></a>Remarks

テンプレート関数を返します[binder1st (STL/CLR)](../dotnet/binder1st-stl-clr.md)`<Fun>(functor, left)`します。 引数が 1 つのファンクタを 2 番目の引数を呼び出すことで、2 つの引数ファンクターと、最初の引数をラップする便利な方法として使用するとします。

### <a name="example"></a>例

```cpp
// cliext_bind1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="bind2nd"></a> bind2nd (STL/CLR)

生成、`binder2nd`引数とファンクタ。

### <a name="syntax"></a>構文

```cpp
template<typename Fun,
    typename Arg>
    binder2nd<Fun> bind2nd(Fun% functor,
        Arg right);
```

#### <a name="template-parameters"></a>テンプレート パラメーター

*arg*<br/>
引数の型。

*楽しむ*<br/>
関数記号の型。

#### <a name="function-parameters"></a>関数のパラメーター

*ファンクター*<br/>
ラップするファンクタ。

*right*<br/>
ラップする 2 番目の引数。

### <a name="remarks"></a>Remarks

テンプレート関数を返します[binder2nd (STL/CLR)](../dotnet/binder2nd-stl-clr.md)`<Fun>(functor, right)`します。 最初の引数による呼び出し元引数が 1 つファンクターに 2 つの引数ファンクターと 2 番目の引数をラップする便利な方法として使用するとします。

### <a name="example"></a>例

```cpp
// cliext_bind2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="binder1st"></a> binder1st (STL/CLR)

テンプレート クラスは、引数が 1 つファンクタをについて説明しますが、呼び出されると、そのストアドの 2 つの引数ファンクター ストアドの最初の引数と 2 番目の指定された引数で呼び出されますを返します。 これを使用してそのストアド ファンクターの観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Fun>
    ref class binder1st
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        second_argument_type, result_type>
        delegate_type;

    binder1st(Fun% functor, first_argument_type left);
    binder1st(binder1st<Arg>% right);

    result_type operator()(second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*楽しむ*<br/>
ストアド関数記号の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|
|stored_function_type|関数記号の型。|

|メンバー|説明|
|------------|-----------------|
|binder1st|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^()|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクターと最初の引数を格納する引数が 1 つファンクタをについて説明します。 メンバー演算子は、定義`operator()`ストアドの最初の引数と指定された 2 番目の引数を持つストアド ファンクターを呼び出すことの結果が返されるように、オブジェクトが関数として呼び出された場合、します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_binder1st.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder1st<cliext::minus<int> > subfrom3(sub_op, 3);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        subfrom3);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind1st(sub_op, 3));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
-1 0
-1 0
```

## <a name="binder2nd"></a> binder2nd (STL/CLR)

テンプレート クラスは、引数が 1 つファンクタをについて説明しますが、呼び出されると、指定された最初の引数とそのストアドの 2 番目の引数で呼び出されますストアドの 2 つの引数ファンクタを返します。 これを使用してそのストアド ファンクターの観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Fun>
    ref class binder2nd
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::first_argument_type first_argument_type;
    typedef typename Fun::second_argument_type second_argument_type;
    typedef typename Fun:result_type result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        first_argument_type, result_type>
        delegate_type;

    binder2nd(Fun% functor, second_argument_type left);
    binder2nd(binder2nd<Arg>% right);

    result_type operator()(first_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*楽しむ*<br/>
ストアド関数記号の型。

## <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|
|stored_function_type|関数記号の型。|

|メンバー|説明|
|------------|-----------------|
|binder2nd|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^()|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクターと 2 番目の引数を格納する引数が 1 つファンクタをについて説明します。 メンバー演算子が定義されています`operator()`関数として、オブジェクトを呼び出すときに、ように、指定された最初の引数と 2 番目の引数がストアド ストアド ファンクターを呼び出すことの結果を返します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_binder2nd.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::minus<int> sub_op;
    cliext::binder2nd<cliext::minus<int> > sub4(sub_op, 4);

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        sub4);
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        bind2nd(sub_op, 4));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
0 -1
0 -1
```

## <a name="divides"></a> 除算 (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、2 番目で除算する最初の引数を返します。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class divides
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    divides();
    divides(divides<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数と戻り値の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|divides|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^()|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`最初の引数が 2 つ目で割った値が返されるように、オブジェクトが関数として呼び出された場合、します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_divides.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::divides<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 3
```

## <a name="equal_to"></a> equal_to (STL/CLR)

テンプレート クラスは、説明、ファンクター、呼び出されると、true を返します、最初の引数が 2 番目の場合にのみです。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    equal_to();
    equal_to(equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|equal_to|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^()|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数が 2 番目のかどうか。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="greater"></a> 大きい (STL/CLR)

テンプレート クラスは、説明、ファンクター、呼び出されると、true を返します、最初の引数が 2 番目より大きい場合にのみです。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class greater
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater();
    greater(greater<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|greater|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数が 2 番目より大きいかどうか。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_greater.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
1 0
```

## <a name="greater_equal"></a> greater_equal (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、ときにのみ true を返します、最初の引数が 2 番目以上のかどうか。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class greater_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    greater_equal();
    greater_equal(greater_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|greater_equal|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数が 2 番目以上のかどうか。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_greater_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::greater_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
```

## <a name="less"></a> 小さい (STL/CLR)

テンプレート クラスは、説明、ファンクター、呼び出されると、true を返します、最初の引数が小さい場合にのみ、1 つ目です。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class less
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less();
    less(less<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|非表示|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数が小さいかどうか、1 つ目です。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_less.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="less_equal"></a> less_equal (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、ときにのみ true を返します、最初の引数が 2 番目に小さいかどうか。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class less_equal
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    less_equal();
    less_equal(less_equal<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|less_equal|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数が 2 番目に小さいかどうか。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_less_equal.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(3);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 3 3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::less_equal<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
3 3
0 1
```

## <a name="logical_and"></a> logical_and (STL/CLR)

テンプレート クラスは、説明、ファンクター、呼び出されると、true を返します、最初の引数と 2 番目のテストとしての両方が true の場合のみです。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class logical_and
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_and();
    logical_and(logical_and<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|logical_and|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数と 2 番目のテストとしての両方の true です。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_logical_and.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 1 0" and " 1 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_and<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
3 0
1 0
```

## <a name="logical_not"></a> logical_not (STL/CLR)

テンプレート クラスは、説明、ファンクター、呼び出されると、true を返す場合にのみ、引数が false としてテストします。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class logical_not
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    logical_not();
    logical_not(logical_not<Arg> %right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|argument_type|ファンクター引数の型。|
|delegate_type|汎用デリゲートの型。|
|result_type|ファンクター結果の型。|

|メンバー|説明|
|------------|-----------------|
|logical_not|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、引数が 1 つファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返しますの引数が false としてテストします。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_logical_not.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::logical_not<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
0 1
```

## <a name="logical_or"></a> logical_or (STL/CLR)

テンプレート クラスは、説明、ファンクター、呼び出されると、true を返します、最初の引数または 2 つ目のテストのいずれかが true の場合のみです。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class logical_or
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    logical_or();
    logical_or(logical_or<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|logical_or|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数または 2 つ目のテストのいずれかの true です。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_logical_or.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(2);
    c1.push_back(0);
    Myvector c2;
    c2.push_back(0);
    c2.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 2 0" and " 0 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::logical_or<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
2 0
0 0
1 0
```

## <a name="minus"></a> マイナス (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、2 番目のマイナスの最初の引数を返します。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class minus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    minus();
    minus(minus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数と戻り値の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|minus|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`マイナス 2 つ目の最初の引数が返されるように、オブジェクトが関数として呼び出された場合、します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_minus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::minus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
2 2
```

## <a name="modulus"></a> 剰余 (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、最初の引数を 2 番目の剰余を返します。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class modulus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    modulus();
    modulus(modulus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数と戻り値の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|modulus|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`モジュロ 2 つ目の最初の引数が返されるように、オブジェクトが関数として呼び出された場合、します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_modulus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(2);
    Myvector c2;
    c2.push_back(3);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 2" and " 3 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::modulus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 2
3 1
1 0
```

## <a name="multiplies"></a> 乗算 (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、時間、2 つ目の最初の引数を返します。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class multiplies
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    multiplies();
    multiplies(multiplies<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数と戻り値の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|multiplies|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`回、2 つ目の最初の引数が返されるように、オブジェクトが関数として呼び出された場合、します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_multiplies.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::multiplies<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
8 3
```

## <a name="negate"></a> 否定 (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、その引数を符号反転されるを返します。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class negate
    { // wrap operator()
public:
    typedef Arg argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    negate();
    negate(negate<Arg>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|argument_type|ファンクター引数の型。|
|delegate_type|汎用デリゲートの型。|
|result_type|ファンクター結果の型。|

|メンバー|説明|
|------------|-----------------|
|negate|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、引数が 1 つファンクタをについて説明します。 メンバー演算子は、定義`operator()`否定の引数が返されるように、オブジェクトが関数として呼び出された場合、します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(-3);
    Myvector c3(2, 0);

// display initial contents " 4 -3"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c3.begin(), cliext::negate<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 -3
-4 3
```

## <a name="not_equal_to"></a> not_equal_to (STL/CLR)

テンプレート クラスは、説明、ファンクター、呼び出されると、true を返します、最初の引数が 2 番目の場合のみです。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class not_equal_to
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    not_equal_to();
    not_equal_to(not_equal_to<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|not_equal_to|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`関数として、オブジェクトを呼び出すときに、ように、のみ true を返します、最初の引数が 2 番目のないかどうか。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_not_equal_to.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not_equal_to<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
0 1
```

## <a name="not1"></a> not1 (STL/CLR)

生成、`unary_negate`をファンクター用です。

### <a name="syntax"></a>構文

```cpp
template<typename Fun>
    unary_negate<Fun> not1(Fun% functor);
```

#### <a name="template-parameters"></a>テンプレート パラメーター

*楽しむ*<br/>
関数記号の型。

#### <a name="function-parameters"></a>関数のパラメーター

*ファンクター*<br/>
ラップするファンクタ。

### <a name="remarks"></a>Remarks

テンプレート関数を返します[unary_negate (STL/CLR)](../dotnet/unary-negate-stl-clr.md)`<Fun>(functor)`します。 その論理 NOT を配信するファンクターに引数が 1 つファンクタをラップする便利な方法として使用するとします。

### <a name="example"></a>例

```cpp
// cliext_not1.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```

## <a name="not2"></a> not2 (STL/CLR)

生成、`binary_negate`をファンクター用です。

### <a name="syntax"></a>構文

```cpp
template<typename Fun>
    binary_negate<Fun> not2(Fun% functor);
```

#### <a name="template-parameters"></a>テンプレート パラメーター

*楽しむ*<br/>
関数記号の型。

#### <a name="function-parameters"></a>関数のパラメーター

*ファンクター*<br/>
ラップするファンクタ。

### <a name="remarks"></a>Remarks

テンプレート関数を返します[binary_negate (STL/CLR)](../dotnet/binary-negate-stl-clr.md)`<Fun>(functor)`します。 その論理 NOT を配信するファンクターに 2 つの引数ファンクタをラップする便利な方法として使用するとします。

### <a name="example"></a>例

```cpp
// cliext_not2.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(4);
    c2.push_back(4);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 4 4"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::less<int> less_op;

    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(),
        cliext::binary_negate<cliext::less<int> >(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::not2(less_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
4 4
1 0
1 0
```

## <a name="plus"></a> plus (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、最初の引数と 2 つ目を返します。 これを使用して、引数の型の観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Arg>
    ref class plus
    { // wrap operator()
public:
    typedef Arg first_argument_type;
    typedef Arg second_argument_type;
    typedef Arg result_type;
    typedef Microsoft::VisualC::StlClr::BinaryDelegate<
        first_argument_type, second_argument_type, result_type>
        delegate_type;

    plus();
    plus(plus<Arg>% right);

    result_type operator()(first_argument_type left,
        second_argument_type right);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数と戻り値の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|delegate_type|汎用デリゲートの型。|
|first_argument_type|ファンクター最初の引数の型。|
|result_type|ファンクター結果の型。|
|second_argument_type|ファンクター 2 番目の引数の型。|

|メンバー|説明|
|------------|-----------------|
|plus|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|operator delegate_type^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、2 つの引数ファンクタをについて説明します。 メンバー演算子は、定義`operator()`最初の引数と 2 つ目が返されるように、オブジェクトが関数として呼び出された場合、します。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_plus.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(3);
    Myvector c2;
    c2.push_back(2);
    c2.push_back(1);
    Myvector c3(2, 0);

// display initial contents " 4 3" and " 2 1"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

    for each (int elem in c2)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::transform(c1.begin(), c1.begin() + 2,
        c2.begin(), c3.begin(), cliext::plus<int>());
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 3
2 1
6 4
```

## <a name="unary_delegate"></a> unary_delegate (STL/CLR)

Genereic クラスには、引数が 1 つのデリゲートがについて説明します。 これを使用してその引数と戻り値の型の観点からデリゲートを指定します。

### <a name="syntax"></a>構文

```cpp
generic<typename Arg,
    typename Result>
    delegate Result unary_delegate(Arg);
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

*結果*<br/>
戻り値の型。

### <a name="remarks"></a>Remarks

Genereic デリゲートでは、引数が 1 つの関数について説明します。

場合に注意してください。

`unary_delegare<int, int> Fun1;`

`unary_delegare<int, int> Fun2;`

種類`Fun1`と`Fun2`は、シノニムの中に。

`delegate int Fun1(int);`

`delegate int Fun2(int);`

同じ型ではありません。

### <a name="example"></a>例

```cpp
// cliext_unary_delegate.cpp
// compile with: /clr
#include <cliext/functional>

int hash_val(wchar_t val)
    {
    return ((val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate<wchar_t, int> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    System::Console::WriteLine("hash(L'a') = {0}", myhash(L'a'));
    System::Console::WriteLine("hash(L'b') = {0}", myhash(L'b'));
    return (0);
    }
```

```Output
hash(L'a') = 5
hash(L'b') = 22
```

## <a name="unary_delegate_noreturn"></a> unary_delegate_noreturn (STL/CLR)

Genereic クラスの説明を返す引数が 1 つのデリゲート**void**します。 これを使用して、引数の型の観点からデリゲートを指定します。

### <a name="syntax"></a>構文

```cpp
generic<typename Arg>
    delegate void unary_delegate_noreturn(Arg);
```

#### <a name="parameters"></a>パラメーター

*arg*<br/>
引数の型。

### <a name="remarks"></a>Remarks

Genereic デリゲートを返す 1 つの引数の関数の説明**void**します。

場合に注意してください。

`unary_delegare_noreturn<int> Fun1;`

`unary_delegare_noreturn<int> Fun2;`

種類`Fun1`と`Fun2`は、シノニムの中に。

`delegate void Fun1(int);`

`delegate void Fun2(int);`

同じ型ではありません。

### <a name="example"></a>例

```cpp
// cliext_unary_delegate_noreturn.cpp
// compile with: /clr
#include <cliext/functional>

void hash_val(wchar_t val)
    {
    System::Console::WriteLine("hash({0}) = {1}",
       val, (val * 17 + 31) % 67);
    }

typedef cliext::unary_delegate_noreturn<wchar_t> Mydelegate;
int main()
    {
    Mydelegate^ myhash = gcnew Mydelegate(&hash_val);

    myhash(L'a');
    myhash(L'b');
    return (0);
    }
```

```Output
hash(a) = 5
hash(b) = 22
```

## <a name="unary_negate"></a> unary_negate (STL/CLR)

テンプレート クラスは、ファンクタをについて説明しますが、呼び出されると、返す論理ストアドの引数が 1 つファンクターのではありません。 これを使用してそのストアド ファンクターの観点からの関数オブジェクトを指定します。

### <a name="syntax"></a>構文

```cpp
template<typename Fun>
    ref class unary_negate
    { // wrap operator()
public:
    typedef Fun stored_function_type;
    typedef typename Fun::argument_type argument_type;
    typedef bool result_type;
    typedef Microsoft::VisualC::StlClr::UnaryDelegate<
        argument_type, result_type>
        delegate_type;

    unary_negate(Fun% functor);
    unary_negate(unary_negate<Fun>% right);

    result_type operator()(argument_type left);
    operator delegate_type^();
    };
```

#### <a name="parameters"></a>パラメーター

*楽しむ*<br/>
ストアド関数記号の型。

### <a name="member-functions"></a>メンバー関数

|型定義|説明|
|---------------------|-----------------|
|argument_type|ファンクター引数の型。|
|delegate_type|汎用デリゲートの型。|
|result_type|ファンクター結果の型。|

|メンバー|説明|
|------------|-----------------|
|unary_negate|ファンクタを構築します。|

|演算子|説明|
|--------------|-----------------|
|演算子 ()|必要な関数を計算します。|
|delegate_type ^|デリゲートにファンクタをキャストします。|

### <a name="remarks"></a>Remarks

テンプレート クラスは、もう 1 つの引数が 1 つファンクタを格納する引数が 1 つファンクタをについて説明します。 メンバー演算子は、定義`operator()`論理が返されるように、オブジェクトが関数として呼び出された場合、引数で呼び出されたストアド ファンクターのではありません。

型が関数の引数としてオブジェクトを渡すことができますも`delegate_type^`適切に変換されます。

### <a name="example"></a>例

```cpp
// cliext_unary_negate.cpp
// compile with: /clr
#include <cliext/algorithm>
#include <cliext/functional>
#include <cliext/vector>

typedef cliext::vector<int> Myvector;
int main()
    {
    Myvector c1;
    c1.push_back(4);
    c1.push_back(0);
    Myvector c3(2, 0);

// display initial contents " 4 0"
    for each (int elem in c1)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display
    cliext::logical_not<int> not_op;

    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::unary_negate<cliext::logical_not<int> >(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();

// transform and display with function
    cliext::transform(c1.begin(), c1.begin() + 2, c3.begin(),
        cliext::not1(not_op));
    for each (int elem in c3)
        System::Console::Write(" {0}", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
4 0
1 0
1 0
```