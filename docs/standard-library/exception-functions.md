---
title: '&lt;exception&gt; 関数'
ms.date: 11/04/2016
f1_keywords:
- exception/std::current_exception
- exception/std::get_terminate
- exception/std::get_unexpected
- exception/std::make_exception_ptr
- exception/std::rethrow_exception
- exception/std::set_terminate
- exception/std::set_unexpected
- exception/std::terminate
- exception/std::uncaught_exception
- exception/std::unexpected
ms.assetid: c09ac569-5e35-4fe8-872d-ca5810274dd7
helpviewer_keywords:
- std::current_exception [C++]
- std::get_terminate [C++]
- std::get_unexpected [C++]
- std::make_exception_ptr [C++]
- std::rethrow_exception [C++]
- std::set_terminate [C++]
- std::set_unexpected [C++]
- std::terminate [C++]
- std::uncaught_exception [C++]
- std::unexpected [C++]
ms.openlocfilehash: 34a34c48be8bb0e319a7d0eebeccba805cafbc1f
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246058"
---
# <a name="ltexceptiongt-functions"></a>&lt;exception&gt; 関数

## <a name="current_exception"></a> current_exception

現在の例外へのスマート ポインターを取得します。

```cpp
exception_ptr current_exception();
```

### <a name="return-value"></a>戻り値

現在の例外を指す [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) オブジェクト。

### <a name="remarks"></a>Remarks

catch ブロックで `current_exception` 関数を呼び出します。 例外が処理中で、catch ブロックで例外をキャッチできる場合、`current_exception` 関数は、例外を参照する `exception_ptr` オブジェクトを返します。 それ以外の場合、関数は null `exception_ptr` オブジェクトを返します。

`current_exception`関数かどうかに関係なく処理中である例外では、**キャッチ**ステートメントを指定します、[例外宣言](../cpp/try-throw-and-catch-statements-cpp.md)ステートメント。

末尾に現在の例外のデストラクターが呼び出されます、**キャッチ**例外が再スローしない場合にブロックします。 ただし、デストラクターで `current_exception` 関数を呼び出しても、その関数は現在の例外を参照する `exception_ptr` オブジェクトを返します。

`current_exception` 関数を連続して呼び出すと、現在の例外のさまざまなコピーを参照する `exception_ptr` オブジェクトが返されます。 その結果、オブジェクトは、異なるコピーを参照しているため、コピーが同じバイナリ値を持っている場合でも、比較においては等しくないと評価されます。

## <a name="make_exception_ptr"></a> make_exception_ptr

例外のコピーを保持する [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr) オブジェクトを作成します。

```cpp
template <class E>
    exception_ptr make_exception_ptr(E Except);
```

### <a name="parameters"></a>パラメーター

*除く*\
コピーする例外を持つクラス。 通常は、[例外クラス](../standard-library/exception-class.md) オブジェクトを `make_exception_ptr` 関数への引数として指定しますが、任意のクラスのオブジェクトを引数に使用できます。

### <a name="return-value"></a>戻り値

[Exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)オブジェクトの現在の例外のコピーを指す*を除く*します。

### <a name="remarks"></a>Remarks

`make_exception_ptr` 関数を呼び出すことは、C++ 例外をスローし、その例外を catch ブロック内でキャッチしてから、[current_exception](../standard-library/exception-functions.md#current_exception) 関数を呼び出し、例外を参照する `exception_ptr` オブジェクトを返すことと同じです。 `make_exception_ptr` 関数の Microsoft 実装は、例外のスローとキャッチよりも効果的です。

通常、アプリケーションは `make_exception_ptr` 関数を必要とせず、使用は推奨されていません。

## <a name="rethrow_exception"></a> rethrow_exception

パラメーターとして渡された例外をスローします。

```cpp
void rethrow_exception(exception_ptr P);
```

### <a name="parameters"></a>パラメーター

*P*\
再スローするためにキャッチされる例外。 場合*P* null [exception_ptr](../standard-library/exception-typedefs.md#exception_ptr)、関数はスロー [std::bad_exception](../standard-library/bad-exception-class.md)します。

### <a name="remarks"></a>Remarks

キャッチした例外を `exception_ptr` オブジェクトに保存すると、プライマリ スレッドはオブジェクトを処理できます。 プライマリ スレッドで、引数として `rethrow_exception` オブジェクトを指定して `exception_ptr` 関数を呼び出します。 `rethrow_exception` 関数は `exception_ptr` オブジェクトから例外を抽出し、プライマリ スレッドのコンテキストで例外をスローします。

## <a name="get_terminate"></a> get_terminate

現在の `terminate_handler` 関数を取得します。

```cpp
terminate_handler get_terminate();
```

## <a name="set_terminate"></a> set_terminate

プログラムの終了時に呼び出される新しい `terminate_handler` を設定します。

```cpp
terminate_handler set_terminate(terminate_handler fnew) throw();
```

### <a name="parameters"></a>パラメーター

*fnew*\
終了時に呼び出される関数。

### <a name="return-value"></a>戻り値

終了時に呼び出されていた、以前の関数のアドレス。

### <a name="remarks"></a>Remarks

関数は、新しい確立[terminate_handler](../standard-library/exception-typedefs.md#terminate_handler)関数として * *fnew*します。 したがって、 *fnew* null ポインターをすることはできません。 この関数は、以前の終了ハンドラーのアドレスを返します。

### <a name="example"></a>例

```cpp
// exception_set_terminate.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void termfunction()
{
    cout << "My terminate function called." << endl;
    abort();
}

int main()
{
    terminate_handler oldHandler = set_terminate(termfunction);

    // Throwing an unhandled exception would also terminate the program
    // or we could explicitly call terminate();

    //throw bad_alloc();
    terminate();
}
```

## <a name="get_unexpected"></a> get_unexpected

現在の `unexpected_handler` 関数を取得します。

```cpp
unexpected_handler get_unexpected();
```

## <a name="rethrow_if_nested"></a> rethrow_if_nested

```cpp
template <class E> 
    void rethrow_if_nested(const E& e);
```

### <a name="remarks"></a>Remarks

ポリモーフィックなクラス型ではなくの場合、または場合`nested_exception`にアクセスできないか、あいまいな場合は、影響はありません。 それ以外の場合、動的なキャストを実行します。

## <a name="set_unexpected"></a> set_unexpected

予期しない例外が発生したときに新しい `unexpected_handler` が存在するように設定します。

```cpp
unexpected_handler set_unexpected(unexpected_handler fnew) throw();
```

### <a name="parameters"></a>パラメーター

*fnew*\
予期しない例外が発生したときに呼び出される関数。

### <a name="return-value"></a>戻り値

以前の `unexpected_handler` のアドレス。

### <a name="remarks"></a>Remarks

*fnew* null ポインターをすることはできません。

C++ 標準では、関数が throw のリストにない例外をスローした場合に、`unexpected` を呼び出す必要があります。 現在の実装では、これをサポートしていません。 次の例では、`unexpected` を直接呼び出し、その後で `unexpected_handler` を呼び出します。

### <a name="example"></a>例

```cpp
// exception_set_unexpected.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>

using namespace std;

void uefunction()
{
    cout << "My unhandled exception function called." << endl;
    terminate(); // this is what unexpected() calls by default
}

int main()
{
    unexpected_handler oldHandler = set_unexpected(uefunction);

    unexpected(); // library function to force calling the
                  // current unexpected handler
}
```

## <a name="terminate"></a> 終了

終了ハンドラーを呼び出します。

```cpp
void terminate();
```

### <a name="remarks"></a>Remarks

関数は、終了ハンドラーを型の関数を呼び出す**void**します。 場合`terminate`は、プログラムでは、終了ハンドラーによって直接呼び出されますが、最も新しく設定されたものを呼び出して[set_terminate](../standard-library/exception-functions.md#set_terminate)します。 場合`terminate`呼びますスロー式の評価中に他のいくつかの理由のいずれかの終了ハンドラーは、有効なスロー式の評価直後後。

終了ハンドラーは、呼び出し元に戻らない場合があります。 終了ハンドラー関数を呼び出すは、プログラムの起動時に`abort`します。

### <a name="example"></a>例

`terminate` の使用例については、「[set_unexpected](../standard-library/exception-functions.md#set_unexpected)」を参照してください。

## <a name="throw_with_nested"></a> throw_with_nested

```cpp
template <class T> [[noreturn]]
    void throw_with_nested(T&& t);
```

### <a name="remarks"></a>Remarks

入れ子になった例外と例外をスローします。

## <a name="uncaught_exception"></a> uncaught_exception

スローされた例外が現在処理されている場合にのみ **true** を返します。

```cpp
bool uncaught_exception();
```

### <a name="return-value"></a>戻り値

返します**true**と、対応するハンドラーまたは呼び出し元の例外宣言の初期化を完了する前にスロー式の評価期間後[予期しない](../standard-library/exception-functions.md#unexpected)の結果として、式をスローします。 具体的には、`uncaught_exception`戻ります**true**例外のアンワインド中に呼び出されるデストラクターから呼び出されるとします。 デバイス上で、`uncaught_exception` は Windows CE 5.00 以降のバージョン (Windows Mobile 2005 プラットフォームを含む) でのみサポートされます。

### <a name="example"></a>例

```cpp
// exception_uncaught_exception.cpp
// compile with: /EHsc
#include <exception>
#include <iostream>
#include <string>

class Test
{
public:
   Test( std::string msg ) : m_msg( msg )
   {
      std::cout << "In Test::Test(\"" << m_msg << "\")" << std::endl;
   }
   ~Test( )
   {
      std::cout << "In Test::~Test(\"" << m_msg << "\")" << std::endl
         << "        std::uncaught_exception( ) = "
         << std::uncaught_exception( )
         << std::endl;
   }
private:
    std::string m_msg;
};

// uncaught_exception will be true in the destructor
// for the object created inside the try block because
// the destructor is being called as part of the unwind.

int main( void )
   {
      Test t1( "outside try block" );
      try
      {
         Test t2( "inside try block" );
         throw 1;
      }
      catch (...) {
   }
}
```

```Output
In Test::Test("outside try block")
In Test::Test("inside try block")
In Test::~Test("inside try block")
        std::uncaught_exception( ) = 1
In Test::~Test("outside try block")
        std::uncaught_exception( ) = 0
```

## <a name="unexpected"></a> 予期しません。

予期しないハンドラーを呼び出します。

```cpp
void unexpected();
```

### <a name="remarks"></a>Remarks

C++ 標準では、関数が throw のリストにない例外をスローした場合に、`unexpected` を呼び出す必要があります。 現在の実装では、これをサポートしていません。 次の例では、予期しないハンドラーを呼び出す `unexpected` を直接呼び出します。

関数は、予期しないハンドラー、型の関数を呼び出す**void**します。 `unexpected` がプログラムによって直接呼び出される場合、予期しないハンドラーは、[set_unexpected](../standard-library/exception-functions.md#set_unexpected) の呼び出しによって最も新しく設定されたものとなります。

予期しないハンドラーは、呼び出し元に戻らない場合があります。 次の処理を行って実行を終了する場合があります。

- 例外指定内にリストされた型のオブジェクトをスローする。予期しないハンドラーがプログラムから直接呼び出される場合は任意の型のオブジェクトをスローする。

- [bad_exception](../standard-library/bad-exception-class.md) 型のオブジェクトをスローする。

- 呼び出す[終了](../standard-library/exception-functions.md#terminate)、`abort`または**終了**(`int`)。

プログラムの起動時に、予期しないハンドラーは、[terminate](../standard-library/exception-functions.md#terminate) を呼び出す関数となります。

### <a name="example"></a>例

`unexpected` の使用例については、「[set_unexpected](../standard-library/exception-functions.md#set_unexpected)」を参照してください。
