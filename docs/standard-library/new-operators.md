---
title: '&lt;new&gt;演算子と列挙型'
ms.date: 11/04/2016
f1_keywords:
- new/std::operator delete
- new/std::operator new
ms.assetid: d1af4b56-9a95-4c65-ab01-bf43e982c7bd
ms.openlocfilehash: a3fd5b825fe1eaf3a07d9d001f03b9d0c64ffa31
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243681"
---
# <a name="ltnewgt-operators-and-enums"></a>&lt;new&gt;演算子と列挙型

## <a name="op_align_val_t"></a> enum align_val_t

```cpp
enum class align_val_t : size_t {};
```

## <a name="op_delete"></a>delete 演算子

個々 のオブジェクト ストレージの割り当てを解除する削除式によって呼び出される関数。

```cpp
void operator delete(void* ptr) throw();
void operator delete(void *, void*) throw();
void operator delete(void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>パラメーター

*ptr*\
削除によって値が無効になるポインター。

### <a name="remarks"></a>Remarks

値を表示するために delete 式によって、最初の関数が呼び出されます*ptr*が無効です。 プログラムでは、この関数のシグネチャを持つ関数を定義できます。これは、C++ 標準ライブラリで定義されている既定のバージョンに置き換わります。 必要な動作は、の値を受け入れる*ptr*または null をする以前の呼び出しによって返されたつまり[new 演算子](../standard-library/new-operators.md#op_new)(**size_t**)。

Null 値の既定の動作*ptr*は何もしないようにします。 その他の値の*ptr*前述のような呼び出しによって以前返される値を指定する必要があります。 Null 以外の値の既定の動作*ptr*が、以前の呼び出しによって割り当てられたストレージを再利用されます。 どのような条件下でこのような再利用できるストレージの一部またはすべてが後続の呼び出しによって割り当てが指定されていない場合`operator new`(**size_t**)、または任意の`calloc`( **size_t**)、 `malloc`( **size_t**)、または`realloc`( **void**<strong>\*</strong>、 **size_t**)。

2 番目の関数は、**new**( **std::size_t**) の形式の new 式に対応する配置 delete 式で呼び出されます。 何も実行されません。

3 番目の関数は、**new**( **std::size_t**, **conststd::nothrow_t&** ) の形式の new 式に対応する配置 delete 式で呼び出されます。 プログラムでは、この関数のシグネチャを持つ関数を定義できます。これは、C++ 標準ライブラリで定義されている既定のバージョンに置き換わります。 必要な動作は、null であるかまたは以前の `operator new`( **size_t**) の呼び出しで返された `ptr` の値を受け入れることです。 既定の動作が評価するには**削除**(`ptr`)。

### <a name="example"></a>例

参照してください[new 演算子](../standard-library/new-operators.md#op_new)を使用する例については**delete 演算子**します。

## <a name="op_delete_arr"></a>delete 演算子

オブジェクトの配列に対するストレージの割り当てを解除する削除式によって呼び出される関数。

```cpp
void operator delete[](void* ptr) throw();
void operator delete[](void *, void*) throw();
void operator delete[](void* ptr, const std::nothrow_t&) throw();
```

### <a name="parameters"></a>パラメーター

*ptr*\
削除によって値が無効になるポインター。

### <a name="remarks"></a>Remarks

最初の関数を呼び出して、`delete[]`式の値を表示するために*ptr*が無効です。 関数は置き換え可能です。プログラムでこの関数のシグネチャを持つ関数を定義でき、これが C++ 標準ライブラリで定義された既定のバージョンに置き換わるためです。 必要な動作は、の値を受け入れる*ptr*または null をする以前の呼び出しによって返されたつまり[new 演算子](../standard-library/new-operators.md#op_new_arr)(**size_t**)。 Null 値の既定の動作*ptr*は何もしないようにします。 その他の値の*ptr*前述のような呼び出しによって以前返される値を指定する必要があります。 このような非 null 値の既定の動作*ptr*が、以前の呼び出しによって割り当てられたストレージを再利用されます。 どのような条件下でこのような再利用できるストレージの一部またはすべてが後続の呼び出しによって割り当てが指定されていない場合[new 演算子](../standard-library/new-operators.md#op_new)(**size_t**)、または任意の`calloc`(**size_t**)、 `malloc`(**size_t**)、または`realloc`( **void**<strong>\*</strong>、 **size_t**).

2 番目の関数は、配置によって呼び出されます`delete[]`に対応する式を`new[]`形式の式`new[]`(**std::size_t**)。 何も実行されません。

3 番目の関数は、`new[]`( **std::size_t**, **const std::nothrow_t&** ) の形式の `new[]` 式に対応する配置 delete 式で呼び出されます。 プログラムでは、この関数のシグネチャを持つ関数を定義できます。これは、C++ 標準ライブラリで定義されている既定のバージョンに置き換わります。 必要な動作は、の値を受け入れる*ptr*または null をオペレーターに以前の呼び出しによって返されたつまり`new[]`(**size_t**)。 既定の動作では、`delete[]`( `ptr`) が評価されます。

### <a name="example"></a>例

`operator delete[]` の使用例については、「[operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr)」を参照してください。

## <a name="op_new"></a> new 演算子

new 式によって個々のオブジェクトにストレージを割り当てるために呼び出される関数。

```cpp
void* operator new(std::size_t count) throw(bad_alloc);
void* operator new(std::size_t count, const std::nothrow_t&) throw();
void* operator new(std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>パラメーター

*カウント*\
割り当てられるストレージのバイト数。

*ptr*\
返されるポインター。

### <a name="return-value"></a>戻り値

新たに割り当てられるストレージの最下位バイト アドレスへのポインター。 または*ptr*します。

### <a name="remarks"></a>Remarks

1 番目の関数は new 式によって呼び出され、そのサイズのオブジェクトを表すために適切にアラインされた `count` バイトのストレージを割り当てます。 プログラムでは、この関数のシグネチャを持つ別の関数を定義できます。これは、C++ 標準ライブラリで定義されている既定のバージョンに置き換わります。つまり、関数は置き換え可能です。

必要な動作は、要求されたとおりにストレージを割り当てできる場合にのみ、null 以外のポインターを返すことです。 このようなそれぞれの割り当てによって、ストレージが、割り当て済みの他のストレージから分離されます。 後続の呼び出しで割り当てられるストレージの順序および連続性は不定です。 最初の格納値は不定です。 返されるポインターは、割り当てられたストレージの開始位置 (最下位バイト アドレス) を指します。 カウントがゼロの場合、返される値は、この関数によって返される他のどの値とも等しくなりません。

既定の動作ではループが実行されます。 ループ内で、関数はまず要求されたストレージの割り当てを試みます。 試行に `malloc`( **size_t**) の呼び出しが含まれるかどうかは不定です。 試行が成功した場合、関数は割り当てられたストレージへのポインターを返します。 それ以外の場合、関数は指定された[new ハンドラー](../standard-library/new-typedefs.md#new_handler)を呼び出します。 呼び出された関数が戻った場合、ループが繰り返されます。 ループは、要求されたストレージ割り当ての試行に成功したとき、または呼び出された関数が戻らなかったときに終了します。

new ハンドラーに必要な動作は、次の操作のいずれかを実行することです。

- さらに多くのストレージを割り当てに使用できるようにして、戻ります。

- いずれかを呼び出す**中止**または**終了**(`int`)。

- **bad_alloc** 型のオブジェクトをスローします。

[new ハンドラー](../standard-library/new-typedefs.md#new_handler)の既定の動作では、`bad_alloc` 型のオブジェクトがスローされます。 Null ポインターは既定の new ハンドラーを指定します。

順序との連続呼び出しで割り当てられるストレージの連続性`operator new`(**size_t**) が格納されている初期値は指定しません。

2 番目の関数は配置 new 式によって呼び出され、そのサイズのオブジェクトを表すために適切にアラインされた `count` バイトのストレージを割り当てます。 プログラムでは、この関数のシグネチャを持つ別の関数を定義できます。これは、C++ 標準ライブラリで定義されている既定のバージョンに置き換わります。つまり、関数は置き換え可能です。

既定の動作を返す`operator new`(`count`) その関数が成功した場合。 それ以外の場合は、Null ポインターが返されます。

3 番目の関数は、**new**( *args*) T の形式の配置 **new** 式によって呼び出されます。ここで、*args* は 1 つのオブジェクトのポインターで構成されます。 これは、既知のアドレスにあるオブジェクトの構築に役立ちます。 *ptr* が返されます。

によって割り当てられたストレージを解放する**new 演算子**、呼び出す[delete 演算子](../standard-library/new-operators.md#op_delete)します。

スローすることについてや、新しい参照の動作をスローしない[new 演算子と delete 演算子](../cpp/new-and-delete-operators.md)します。

### <a name="example"></a>例

```cpp
// new_op_new.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;

class MyClass
{
public:
   MyClass( )
   {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass( )
   {
      imember = 0; cout << "Destructing MyClass." << this << endl;
   };
   int imember;
};

int main( )
{
   // The first form of new delete
   MyClass* fPtr = new MyClass;
   delete fPtr;

   // The second form of new delete
   MyClass* fPtr2 = new( nothrow ) MyClass;
   delete fPtr2;

   // The third form of new delete
   char x[sizeof( MyClass )];
   MyClass* fPtr3 = new( &x[0] ) MyClass;
   fPtr3 -> ~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;
}
```

## <a name="op_new_arr"></a> new 演算子

new 式によってオブジェクトの配列にストレージを割り当てるために呼び出される割り当て関数。

```cpp
void* operator new[](std::size_t count) throw(std::bad_alloc);
void* operator new[](std::size_t count, const std::nothrow_t&) throw();
void* operator new[](std::size_t count, void* ptr) throw();
```

### <a name="parameters"></a>パラメーター

*カウント*\
配列オブジェクトに割り当てられるストレージのバイト数。

*ptr*\
返されるポインター。

### <a name="return-value"></a>戻り値

新たに割り当てられるストレージの最下位バイト アドレスへのポインター。 または*ptr*します。

### <a name="remarks"></a>Remarks

1 番目の関数は `new[]` 式によって呼び出され、そのサイズ以下の配列オブジェクトを表すために適切にアラインされた `count` バイトのストレージを割り当てます。 プログラムでは、この関数のシグネチャを持つ関数を定義できます。これは、C++ 標準ライブラリで定義されている既定のバージョンに置き換わります。 必要な動作は同じである[new 演算子](../standard-library/new-operators.md#op_new)(**size_t**)。 既定の動作では、`operator new`( `count`) が返されます。

2 番目の関数は配置 `new[]` 式によって呼び出され、そのサイズの配列オブジェクトを表すために適切にアラインされた `count` バイトのストレージを割り当てます。 プログラムでは、この関数のシグネチャを持つ関数を定義できます。これは、C++ 標準ライブラリで定義されている既定のバージョンに置き換わります。 既定の動作を返す**operatornew**(`count`) その関数が成功した場合。 それ以外の場合は、Null ポインターが返されます。

3 番目の関数は、**new** ( *args*) **T** **[N]** の形式の配置 `new[]` 式によって呼び出されます。 ここで、*args* は 1 つのオブジェクトのポインターで構成されます。 `ptr` が返されます。

`operator new[]` によって割り当てられたストレージを解放するには、[delete 演算子](../standard-library/new-operators.md#op_delete_arr) を呼び出します。

スローする場合またはスローしない場合の動作については、「[new および delete 演算子](../cpp/new-and-delete-operators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// new_op_alloc.cpp
// compile with: /EHsc
#include <new>
#include <iostream>

using namespace std;

class MyClass {
public:
   MyClass() {
      cout << "Construction MyClass." << this << endl;
   };

   ~MyClass() {
      imember = 0; cout << "Destructing MyClass." << this << endl;
      };
   int imember;
};

int main() {
   // The first form of new delete
   MyClass* fPtr = new MyClass[2];
   delete[ ] fPtr;

   // The second form of new delete
   char x[2 * sizeof( MyClass ) + sizeof(int)];

   MyClass* fPtr2 = new( &x[0] ) MyClass[2];
   fPtr2[1].~MyClass();
   fPtr2[0].~MyClass();
   cout << "The address of x[0] is : " << ( void* )&x[0] << endl;

   // The third form of new delete
   MyClass* fPtr3 = new( nothrow ) MyClass[2];
   delete[ ] fPtr3;
}
```
