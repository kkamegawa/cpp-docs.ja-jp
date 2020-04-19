---
title: stack (STL/CLR)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- cliext::stack
- cliext::operator!=
- cliext::operator<
- cliext::operator<=
- cliext::operator==
- cliext::operator>
- cliext::operator>=
- cliext::stack::assign
- cliext::stack::const_reference
- cliext::stack::container_type
- cliext::stack::difference_type
- cliext::stack::empty
- cliext::stack::generic_container
- cliext::stack::generic_value
- cliext::stack::get_container
- cliext::stack::operator=
- cliext::stack::pop
- cliext::stack::push
- cliext::stack::reference
- cliext::stack::size
- cliext::stack::size_type
- cliext::stack::stack
- cliext::stack::to_array
- cliext::stack::top
- cliext::stack::top_item
- cliext::stack::value_type
helpviewer_keywords:
- <stack> header [STL/CLR]
- <cliext/stack> header [STL/CLR]
- stack class [STL/CLR]
- operator!= member [STL/CLR]
- operator< member [STL/CLR]
- operator<= member [STL/CLR]
- operator== member [STL/CLR]
- operator> member [STL/CLR]
- operator>= member [STL/CLR]
- assign member [STL/CLR]
- const_reference member [STL/CLR]
- container_type member [STL/CLR]
- difference_type member [STL/CLR]
- empty member [STL/CLR]
- generic_container member [STL/CLR]
- generic_value member [STL/CLR]
- get_container member [STL/CLR]
- operator= member [STL/CLR]
- pop member [STL/CLR]
- push member [STL/CLR]
- reference member [STL/CLR]
- size member [STL/CLR]
- size_type member [STL/CLR]
- stack member [STL/CLR]
- to_array member [STL/CLR]
- top member [STL/CLR]
- top_item member [STL/CLR]
- value_type member [STL/CLR]
ms.assetid: 6ee96b9f-8a33-4cf7-b7e0-6535c24bdefb
ms.openlocfilehash: ec3863796f7c49c155af61576c15c1ca8a9d5109
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384609"
---
# <a name="stack-stlclr"></a>stack (STL/CLR)

テンプレート クラスは後入れ先出しのアクセス権を持つ要素の可変長シーケンスを制御するオブジェクトについて説明します。 コンテナー アダプターを使用する`stack`プッシュ ダウン スタックとの基になるコンテナーを管理します。

下記の説明で`GValue`と同じ*値*しない限り、後者の場合は、ref 型である場合は`Value^`します。 同様に、`GContainer`と同じ*コンテナー*しない限り、後者の場合は、ref 型である場合は`Container^`します。

## <a name="syntax"></a>構文

```cpp
template<typename Value,
    typename Container>
    ref class stack
        :   public
        System::ICloneable,
        Microsoft::VisualC::StlClr::IStack<GValue, GContainer>
    { ..... };
```

### <a name="parameters"></a>パラメーター

*[値]*<br/>
被制御シーケンス内の要素の型。

*コンテナー*<br/>
基になるコンテナーの型。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<cliext/stack >

**Namespace:** cliext

## <a name="declarations"></a>宣言

|型定義|説明|
|---------------------|-----------------|
|[stack::const_reference (STL/CLR)](#const_reference)|要素への定数参照の型です。|
|[stack::container_type (STL/CLR)](#container_type)|基になるコンテナーの型。|
|[stack::difference_type (STL/CLR)](#difference_type)|2 つの要素間の距離を表す、符号付きの型です。|
|[stack::generic_container (STL/CLR)](#generic_container)|コンテナー アダプターのジェネリック インターフェイスの型。|
|[stack::generic_value (STL/CLR)](#generic_value)|コンテナー アダプターのジェネリック インターフェイスの要素の型。|
|[stack::reference (STL/CLR)](#reference)|要素への参照の型です。|
|[stack::size_type (STL/CLR)](#size_type)|2 つの要素間の距離を表す、符号付きの型です。|
|[stack::value_type (STL/CLR)](#value_type)|要素の型。|

|メンバー関数|説明|
|---------------------|-----------------|
|[stack::assign (STL/CLR)](#assign)|すべての要素を置換します。|
|[stack::empty (STL/CLR)](#empty)|要素が存在しないかどうかをテストします。|
|[stack::get_container (STL/CLR)](#get_container)|基になるコンテナーにアクセスします。|
|[stack::pop (STL/CLR)](#pop)|最後の要素を削除します。|
|[stack::push (STL/CLR)](#push)|新しい最後の要素を追加します。|
|[stack::size (STL/CLR)](#size)|要素の数をカウントします。|
|[stack::stack (STL/CLR)](#stack)|コンテナー オブジェクトを構築します。|
|[stack::top (STL/CLR)](#top)|最後の要素にアクセスします。|
|[stack::to_array (STL/CLR)](#to_array)|被制御シーケンスを新しい配列にコピーします。|

|プロパティ|説明|
|--------------|-----------------|
|[stack::top_item (STL/CLR)](#top_item)|最後の要素にアクセスします。|

|演算子|説明|
|--------------|-----------------|
|[stack::operator= (STL/CLR)](#op_as)|被制御シーケンスを置き換えます。|
|[operator!= (stack) (STL/CLR)](#op_neq)|かどうかを`stack`オブジェクトが等しく別`stack`オブジェクト。|
|[operator< (stack) (STL/CLR)](#op_lt)|かどうかを`stack`オブジェクトが他よりも小さい`stack`オブジェクト。|
|[operator<= (stack) (STL/CLR)](#op_lteq)|かどうかを`stack`オブジェクトが別に小さい`stack`オブジェクト。|
|[operator== (stack) (STL/CLR)](#op_eq)|かどうかを`stack`オブジェクトが相互に等しい`stack`オブジェクト。|
|[operator> (stack) (STL/CLR)](#op_gt)|かどうかを`stack`オブジェクトが他よりも大きい`stack`オブジェクト。|
|[operator>= (stack) (STL/CLR)](#op_gteq)|かどうかを`stack`オブジェクトより大きいまたは相互に等しい`stack`オブジェクト。|

## <a name="interfaces"></a>インターフェイス

|Interface|説明|
|---------------|-----------------|
|<xref:System.ICloneable>|オブジェクトが重複しています。|
|IStack\<値、コンテナー >|汎用コンテナー アダプターを管理します。|

## <a name="remarks"></a>Remarks

割り当ておよび解放型の基になるコンテナーを通じて制御してシーケンスに対するストレージの*コンテナー*、格納する*値*要素と、必要に応じて大きくなります。 オブジェクトは、プッシュとポップだけ、最後の要素 (LIFO キュー、またはスタックとも呼ばれます) は、後入れ先出しキューの実装へのアクセスを制限します。

## <a name="members"></a>メンバー

## <a name="assign"></a> stack::assign (STL/CLR)

すべての要素を置換します。

### <a name="syntax"></a>構文

```cpp
void assign(stack<Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
挿入するコンテナー アダプター。

### <a name="remarks"></a>Remarks

メンバー関数は、代入`right.get_container()`を基になるコンテナー。 スタックのすべての内容を変更するのに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_stack_assign.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign a repetition of values
    Mystack c2;
    c2.assign(c1);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="const_reference"></a> stack::const_reference (STL/CLR)

要素への定数参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% const_reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への定数参照を表します。

### <a name="example"></a>例

```cpp
// cliext_stack_const_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " c b a"
    for (; !c1.empty(); c1.pop())
        {   // get a const reference to an element
        Mystack::const_reference cref = c1.top();
        System::Console::Write("{0} ", cref);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="container_type"></a> stack::container_type (STL/CLR)

基になるコンテナーの型。

### <a name="syntax"></a>構文

```cpp
typedef Container value_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター *Container* のシノニムです。

### <a name="example"></a>例

```cpp
// cliext_stack_container_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="difference_type"></a> stack::difference_type (STL/CLR)

2 つの要素間の距離を符号付きの型。

### <a name="syntax"></a>構文

```cpp
typedef int difference_type;
```

### <a name="remarks"></a>Remarks

この型は、場合によって負の値の要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_stack_difference_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute negative difference
    Mystack::difference_type diff = c1.size();
    c1.push(L'd');
    c1.push(L'e');
    diff -= c1.size();
    System::Console::WriteLine("pushing 2 = {0}", diff);

// compute positive difference
    diff = c1.size();
    c1.pop();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("popping 3 = {0}", diff);
    return (0);
    }
```

```Output
a b c
pushing 2 = -2
popping 3 = 3
```

## <a name="empty"></a> stack::empty (STL/CLR)

要素が存在しないかどうかをテストします。

### <a name="syntax"></a>構文

```cpp
bool empty();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスが空の場合に true を返します。 同じになります[stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md)`() == 0`します。 これを使用するには、スタックが空かどうかをテストします。

### <a name="example"></a>例

```cpp
// cliext_stack_empty.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());

// clear the container and reinspect
    c1.pop();
    c1.pop();
    c1.pop();
    System::Console::WriteLine("size() = {0}", c1.size());
    System::Console::WriteLine("empty() = {0}", c1.empty());
    return (0);
    }
```

```Output
a b c
size() = 3
empty() = False
size() = 0
empty() = True
```

## <a name="generic_container"></a> stack::generic_container (STL/CLR)

コンテナー アダプターのジェネリック インターフェイスの型。

### <a name="syntax"></a>構文

```cpp
typedef Microsoft::VisualC::StlClr::IStack<Value>
    generic_container;
```

### <a name="remarks"></a>Remarks

この型は、このテンプレート コンテナー アダプター クラスのジェネリック インターフェイスを表します。

### <a name="example"></a>例

```cpp
// cliext_stack_generic_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify generic and display original
    gc1->push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify original and display generic
    c1.push(L'e');
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
a b c d
a b c d e
```

## <a name="generic_value"></a> stack::generic_value (STL/CLR)

コンテナーのジェネリック インターフェイスを使用するための要素の型。

### <a name="syntax"></a>構文

```cpp
typedef GValue generic_value;
```

### <a name="remarks"></a>Remarks

この型は、型のオブジェクトを表します。`GValue`ストアド要素の値をこのテンプレートのコンテナー クラスのジェネリック インターフェイスを使用するについて説明します。 (`GValue`か`value_type`または`value_type^`場合`value_type`ref 型です)。

### <a name="example"></a>例

```cpp
// cliext_stack_generic_value.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// get interface to container
    Mystack::generic_container^ gc1 = %c1;
    for each (wchar_t elem in gc1->get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display in reverse using generic_value
    for (; !gc1->empty(); gc1->pop())
        {
        Mystack::generic_value elem = gc1->top();

        System::Console::Write("{0} ", elem);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
c b a
```

## <a name="get_container"></a> stack::get_container (STL/CLR)

基になるコンテナーにアクセスします。

### <a name="syntax"></a>構文

```cpp
container_type^ get_container();
```

### <a name="remarks"></a>Remarks

メンバー関数は、基になるコンテナーのハンドルを返します。 これを使用して、コンテナー ラッパーによる制限を回避します。

### <a name="example"></a>例

```cpp
// cliext_stack_get_container.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c" using container_type
    Mystack::container_type wc1 = c1.get_container();
    for each (wchar_t elem in wc1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="op_as"></a> stack::operator = (STL/CLR)

被制御シーケンスを置き換えます。

### <a name="syntax"></a>構文

```cpp
stack <Value, Container>% operator=(stack <Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コピーするコンテナー アダプター。

### <a name="remarks"></a>Remarks

メンバー演算子コピー*右*、オブジェクトを返します`*this`します。 使用して、被制御シーケンス内のコピーを持つ、被制御シーケンスを置換する*右*します。

### <a name="example"></a>例

```cpp
// cliext_stack_operator_as.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2 = c1;
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b c
```

## <a name="pop"></a> stack::pop (STL/CLR)

最後の要素を削除します。

### <a name="syntax"></a>構文

```cpp
void pop();
```

### <a name="remarks"></a>Remarks

メンバー関数は、空でない必要があります、被制御シーケンスの最後の要素を削除します。 後ろに 1 つの要素によって、スタックを短縮するのに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_stack_pop.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// pop an element and redisplay
    c1.pop();
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b
```

## <a name="push"></a> stack::push (STL/CLR)

新しい最後の要素を追加します。

### <a name="syntax"></a>構文

```cpp
void push(value_type val);
```

### <a name="remarks"></a>Remarks

メンバー関数は、値を持つ要素を挿入する`val`被制御シーケンスの最後にします。 それを使用するには、スタックに別の要素を追加します。

### <a name="example"></a>例

```cpp
// cliext_stack_push.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
```

## <a name="reference"></a> stack::reference (STL/CLR)

要素への参照の型です。

### <a name="syntax"></a>構文

```cpp
typedef value_type% reference;
```

### <a name="remarks"></a>Remarks

この型は、要素への参照を表します。

### <a name="example"></a>例

```cpp
// cliext_stack_reference.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// modify top of stack and redisplay
    Mystack::reference ref = c1.top();
    ref = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
a b x
```

## <a name="size"></a> stack::size (STL/CLR)

要素の数をカウントします。

### <a name="syntax"></a>構文

```cpp
size_type size();
```

### <a name="remarks"></a>Remarks

このメンバー関数は、被制御シーケンスの長さを返します。 それを使用するには、被制御シーケンス内の現在の要素の数を決定します。 シーケンスを参照してください、0 以外のサイズがかどうかが関心のあるすべての場合[stack::empty (STL/CLR)](../dotnet/stack-empty-stl-clr.md)`()`します。

### <a name="example"></a>例

```cpp
// cliext_stack_size.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    System::Console::WriteLine("size() = {0} starting with 3", c1.size());

// pop an item and reinspect
    c1.pop();
    System::Console::WriteLine("size() = {0} after popping", c1.size());

// add two elements and reinspect
    c1.push(L'a');
    c1.push(L'b');
    System::Console::WriteLine("size() = {0} after adding 2", c1.size());
    return (0);
    }
```

```Output
a b c
size() = 3 starting with 3
size() = 2 after popping
size() = 4 after adding 2
```

## <a name="size_type"></a> stack::size_type (STL/CLR)

2 つの要素の間の距離を符号付きの型。

### <a name="syntax"></a>構文

```cpp
typedef int size_type;
```

### <a name="remarks"></a>Remarks

この型は、負でない要素の数を表します。

### <a name="example"></a>例

```cpp
// cliext_stack_size_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// compute positive difference
    Mystack::size_type diff = c1.size();
    c1.pop();
    c1.pop();
    diff -= c1.size();
    System::Console::WriteLine("size difference = {0}", diff);
    return (0);
    }
```

```Output
a b c
size difference = 2
```

## <a name="stack"></a> stack::stack (STL/CLR)

コンテナー アダプター オブジェクトを構築します。

### <a name="syntax"></a>構文

```cpp
stack();
stack(stack<Value, Container>% right);
stack(stack<Value, Container>^ right);
explicit stack(container_type% wrapped);
```

#### <a name="parameters"></a>パラメーター

*right*<br/>
コピーするオブジェクト。

*ラップされました。*<br/>
使用するラップされたコンテナーです。

### <a name="remarks"></a>Remarks

コンス トラクター。

`stack();`

空のラップされたコンテナーを作成します。 空の初期被制御シーケンスの指定に使用するとします。

コンス トラクター。

`stack(stack<Value, Container>% right);`

コピーであるラップされたコンテナーを作成します。`right.get_container()`します。 Stack オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスを指定するために使用*右*します。

コンス トラクター。

`stack(stack<Value, Container>^ right);`

コピーであるラップされたコンテナーを作成します。`right->get_container()`します。 Stack オブジェクトによって制御されるシーケンスのコピーである初期被制御シーケンスを指定するために使用`*right`します。

コンス トラクター。

`explicit stack(container_type% wrapped);`

既存のコンテナーを使用して*ラップ*ラップされたコンテナーとして。 それを使用して既存のコンテナーからのスタックを構築します。

### <a name="example"></a>例

```cpp
// cliext_stack_construct.cpp
// compile with: /clr
#include <cliext/stack>
#include <cliext/vector>

typedef cliext::stack<wchar_t> Mystack;
typedef cliext::vector<wchar_t> Myvector;
typedef cliext::stack<wchar_t, Myvector> Mystack_vec;
int main()
    {
// construct an empty container
    Mystack c1;
    System::Console::WriteLine("size() = {0}", c1.size());

// construct from an underlying container
    Myvector v2(5, L'x');
    Mystack_vec c2(v2);
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container
    Mystack_vec c3(c2);
    for each (wchar_t elem in c3.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// construct by copying another container through handle
    Mystack_vec c4(%c2);
    for each (wchar_t elem in c4.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
size() = 0
x x x x x
x x x x x
x x x x x
```

## <a name="to_array"></a> stack::to_array (STL/CLR)

被制御シーケンスを新しい配列にコピーします。

### <a name="syntax"></a>構文

```cpp
cli::array<Value>^ to_array();
```

### <a name="remarks"></a>Remarks

メンバー関数は、被制御シーケンスを含む配列を返します。 配列の形式で被制御シーケンスのコピーを取得して使用するとします。

### <a name="example"></a>例

```cpp
// cliext_stack_to_array.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// copy the container and modify it
    cli::array<wchar_t>^ a1 = c1.to_array();

    c1.push(L'd');
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// display the earlier array copy
    for each (wchar_t elem in a1)
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c d
a b c
```

## <a name="top"></a> stack::top (STL/CLR)

最後の要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
reference top();
```

### <a name="remarks"></a>Remarks

メンバー関数は、空でない必要があります、被制御シーケンスの最後の要素への参照を返します。 最後の要素へのアクセスが存在することがわかっている場合に使用するとします。

### <a name="example"></a>例

```cpp
// cliext_stack_top.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("top() = {0}", c1.top());

// alter last item and reinspect
    c1.top() = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
top() = c
a b x
```

## <a name="top_item"></a> stack::top_item (STL/CLR)

最後の要素にアクセスします。

### <a name="syntax"></a>構文

```cpp
property value_type top_item;
```

### <a name="remarks"></a>Remarks

プロパティでは、空でない必要があります、被制御シーケンスの最後の要素にアクセスします。 存在することがわかっている場合、最後の要素の読み書きに使用するとします。

### <a name="example"></a>例

```cpp
// cliext_stack_top_item.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display initial contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// inspect last item
    System::Console::WriteLine("top_item = {0}", c1.top_item);

// alter last item and reinspect
    c1.top_item = L'x';
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();
    return (0);
    }
```

```Output
a b c
top_item = c
a b x
```

## <a name="value_type"></a> stack::value_type (STL/CLR)

要素の型。

### <a name="syntax"></a>構文

```cpp
typedef Value value_type;
```

### <a name="remarks"></a>Remarks

型はテンプレート パラメーターのシノニム*値*します。

### <a name="example"></a>例

```cpp
// cliext_stack_value_type.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display reversed contents " a b c" using value_type
    for (; !c1.empty(); c1.pop())
        {   // store element in value_type object
        Mystack::value_type val = c1.top();

        System::Console::Write("{0} ", val);
        }
    System::Console::WriteLine();
    return (0);
    }
```

```Output
c b a
```

## <a name="op_neq"></a> 演算子! = (スタック) (STL/CLR)

スタックには、比較と等しくありません。

### <a name="syntax"></a>構文

```cpp
template<typename Value,
    typename Container>
    bool operator!=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left == right)`します。 テストに使用するかどうか*左*順序付けされていないと同じ*右*2 つのスタックが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_stack_operator_ne.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] != [a b c] is {0}",
        c1 != c1);
    System::Console::WriteLine("[a b c] != [a b d] is {0}",
        c1 != c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] != [a b c] is False
[a b c] != [a b d] is True
```

## <a name="op_lt"></a> 演算子&lt;(スタック) (STL/CLR)

スタックが比較未満です。

### <a name="syntax"></a>構文

```cpp
template<typename Value,
    typename Container>
    bool operator<(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します。 場合は true、最下位の位置の`i`を`!(right[i] < left[i])`も真であることをお勧め`left[i] < right[i]`します。 返しますそれ以外の場合、 `left->` [stack::size (STL/CLR)](../dotnet/stack-size-stl-clr.md) `() <` `right->size()`テストに使用するかどうか*左*前に順序付けは*右*2 つのスタックが比較対象の要素ごとにいる場合。

### <a name="example"></a>例

```cpp
// cliext_stack_operator_lt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] < [a b c] is {0}",
        c1 < c1);
    System::Console::WriteLine("[a b c] < [a b d] is {0}",
        c1 < c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] < [a b c] is False
[a b c] < [a b d] is True
```

## <a name="op_lteq"></a> 演算子&lt;= (スタック) (STL/CLR)

以下のスタックの比較。

### <a name="syntax"></a>構文

```cpp
template<typename Value,
    typename Container>
    bool operator<=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(right < left)`します。 テストに使用するかどうか*左*後に順序付けされていない*右*2 つのスタックが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_stack_operator_le.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] <= [a b c] is {0}",
        c1 <= c1);
    System::Console::WriteLine("[a b d] <= [a b c] is {0}",
        c2 <= c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] <= [a b c] is True
[a b d] <= [a b c] is False
```

## <a name="op_eq"></a> 演算子 (スタック) (STL/CLR) = =

スタックに比較します。

### <a name="syntax"></a>構文

```cpp
template<typename Value,
    typename Container>
    bool operator==(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子の関数によって制御されるシーケンスの場合にのみ true を返します*左*と*右*同じ長さであると、各位置`i`、 `left[i] ==` `right[i]`します。 テストに使用するかどうか*左*が同じ順序付け*右*2 つのスタックが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_stack_operator_eq.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] == [a b c] is {0}",
        c1 == c1);
    System::Console::WriteLine("[a b c] == [a b d] is {0}",
        c1 == c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] == [a b c] is True
[a b c] == [a b d] is False
```

## <a name="op_gt"></a> 演算子&gt;(スタック) (STL/CLR)

スタックの比較よりも大きいです。

### <a name="syntax"></a>構文

```cpp
template<typename Value,
    typename Container>
    bool operator>(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`right` `<` `left`します。 テストに使用するかどうか*左*が後に順序付け*右*2 つのスタックが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_stack_operator_gt.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] > [a b c] is {0}",
        c1 > c1);
    System::Console::WriteLine("[a b d] > [a b c] is {0}",
        c2 > c1);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] > [a b c] is False
[a b d] > [a b c] is True
```

## <a name="op_gteq"></a> 演算子&gt;= (スタック) (STL/CLR)

Stack より大きいまたは等しい比較します。

### <a name="syntax"></a>構文

```cpp
template<typename Value,
    typename Container>
    bool operator>=(stack<Value, Container>% left,
        stack<Value, Container>% right);
```

#### <a name="parameters"></a>パラメーター

*left*<br/>
比較する左のコンテナー。

*right*<br/>
比較する右のコンテナー。

### <a name="remarks"></a>Remarks

演算子関数を返します`!(left < right)`します。 テストに使用するかどうか*左*する前に順序付けされていない*右*2 つのスタックが比較対象の要素ごとの場合。

### <a name="example"></a>例

```cpp
// cliext_stack_operator_ge.cpp
// compile with: /clr
#include <cliext/stack>

typedef cliext::stack<wchar_t> Mystack;
int main()
    {
    Mystack c1;
    c1.push(L'a');
    c1.push(L'b');
    c1.push(L'c');

// display contents " a b c"
    for each (wchar_t elem in c1.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

// assign to a new container
    Mystack c2;
    c2.push(L'a');
    c2.push(L'b');
    c2.push(L'd');

// display contents " a b d"
    for each (wchar_t elem in c2.get_container())
        System::Console::Write("{0} ", elem);
    System::Console::WriteLine();

    System::Console::WriteLine("[a b c] >= [a b c] is {0}",
        c1 >= c1);
    System::Console::WriteLine("[a b c] >= [a b d] is {0}",
        c1 >= c2);
    return (0);
    }
```

```Output
a b c
a b d
[a b c] >= [a b c] is True
[a b c] >= [a b d] is False
```