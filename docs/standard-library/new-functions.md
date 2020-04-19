---
title: '&lt;new&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- new/std::get_new_handler
- new/std::nothrow
- new/std::set_new_handler
ms.assetid: e250f06a-b025-4509-ae7a-5356d56aad7d
ms.openlocfilehash: c912e5be07ea0ebdd3148d30c80c39a5f8cfa1a5
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243663"
---
# <a name="ltnewgt-functions"></a>&lt;new&gt; 関数

## <a name="get_new_handler"></a> get_new_handler

```cpp
new_handler get_new_handler() noexcept;
```

### <a name="remarks"></a>Remarks

現在を返して`new_handler`します。

## <a name="launder"></a> launder

```cpp
template <class T>
    constexpr T* launder(T* ptr) noexcept;
```

### <a name="parameters"></a>パラメーター

*ptr*\
型を持つオブジェクトを保持するメモリのバイトのアドレスと似ています*T*します。

### <a name="return-value"></a>戻り値

型の値*T\**  X を指します。

### <a name="remarks"></a>Remarks

ポインターの最適化のバリアとも呼ばれます。

引数の値定数式で使用できる定数式として使用されます。 ストレージのバイトがオブジェクトのようなポインターを使用して、別のオブジェクトによって占有されているストレージ内でオブジェクトを指しているポインター値を使用してアクセスします。

### <a name="example"></a>例

```cpp
struct X { const int n; };

X *p = new X{3};
const int a = p->n;
new (p) X{5}; // p does not point to new object because X::n is const
const int b = p->n; // undefined behavior
const int c = std::launder(p)->n; // OK
```

## <a name="nothrow"></a> nothrow

引数として使用するオブジェクトを提供します、 **nothrow**のバージョンの**新しい**と**削除**します。

```cpp
extern const std::nothrow_t nothrow;
```

### <a name="remarks"></a>Remarks

オブジェクトは、パラメーターの型 [std::nothrow_t](../standard-library/nothrow-t-structure.md) に一致する関数の引数として使用されます。

### <a name="example"></a>例

`std::nothrow_t` を関数パラメーターとして使用する方法の例については、[operator new](../standard-library/new-operators.md#op_new) および [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) に関する記事をご覧ください。

## <a name="set_new_handler"></a> set_new_handler

インストールするときに呼び出されるユーザー関数**new 演算子**メモリの割り当ての試行に失敗します。

```cpp
new_handler set_new_handler(new_handler Pnew) throw();
```

### <a name="parameters"></a>パラメーター

*Pnew*\
`new_handler`をインストールします。

### <a name="return-value"></a>戻り値

最初の呼び出しの場合は 0、それ以降の呼び出しの場合は以前の `new_handler`。

### <a name="remarks"></a>Remarks

関数は*Pnew*静的な[新しいハンドラー](../standard-library/new-typedefs.md#new_handler)ポインターが保持するポインターに以前に格納されている値が返されます。 新しいハンドラーを使って[演算子 new](../standard-library/new-operators.md#op_new)(**size_t**)。

### <a name="example"></a>例

```cpp
// new_set_new_handler.cpp
// compile with: /EHsc
#include<new>
#include<iostream>

using namespace std;
void __cdecl newhandler( )
{
   cout << "The new_handler is called:" << endl;
   throw bad_alloc( );
   return;
}

int main( )
{
   set_new_handler (newhandler);
   try
   {
      while ( 1 )
      {
         new int[5000000];
         cout << "Allocating 5000000 ints." << endl;
      }
   }
   catch ( exception e )
   {
      cout << e.what( ) << endl;
   }
}
```

```Output
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
Allocating 5000000 ints.
The new_handler is called:
bad allocation
```
