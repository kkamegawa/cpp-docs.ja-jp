---
title: queue クラス
ms.date: 11/04/2016
f1_keywords:
- queue/std::queue::container_type
- queue/std::queue::size_type
- queue/std::queue::value_type
- queue/std::queue::back
- queue/std::queue::empty
- queue/std::queue::front
- queue/std::queue::pop
- queue/std::queue::push
- queue/std::queue::size
helpviewer_keywords:
- std::queue [C++], container_type
- std::queue [C++], size_type
- std::queue [C++], value_type
- std::queue [C++], back
- std::queue [C++], empty
- std::queue [C++], front
- std::queue [C++], pop
- std::queue [C++], push
- std::queue [C++], size
ms.assetid: 28c20ab0-3a72-4185-9e0f-5a44eea0e204
ms.openlocfilehash: 512b9499e63933a71a27a87f91a3bef8a65339e1
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458354"
---
# <a name="queue-class"></a>queue クラス

基になるコンテナー型のいくつかについて、一番前と一番後ろの要素へのアクセスを制限することで機能を限定するテンプレート コンテナー アダプター クラスです。 要素は一番後ろに追加したり一番前から削除したりすることができ、キューのどちらの端でも要素を検査することができます。

## <a name="syntax"></a>構文

```cpp
template <class Type, class Container = deque <Type>>
class queue
```

### <a name="parameters"></a>パラメーター

*各種*\
キューに格納される要素のデータ型。

*コンテナー*\
キューの実装に使用する基になるコンテナーの型。

## <a name="remarks"></a>Remarks

Queue オブジェクトの最初`Type`のテンプレートパラメーターで指定されるクラスの要素は[value_type](#value_type)と同義であり、2つ目のテンプレートによって指定`Container`される、基になるコンテナークラスの要素の型と一致している必要があります。引き. その`Type`型のオブジェクトをコピーし、その型の変数に値を割り当てることができるように、は割り当て可能である必要があります。

キューに適した基になるコンテナークラスには、 [deque](../standard-library/deque-class.md)と[list](../standard-library/list-class.md)、 `front`または、 `back` `push_back`、、および`pop_front`の操作をサポートするその他のシーケンスコンテナーが含まれます。 基になるコンテナー クラスは、コンテナー アダプター内にカプセル化されます。コンテナー アダプターは、限られた一連のシーケンス コンテナーのメンバーの関数のみをパブリック インターフェイスとして公開します。

Queue オブジェクトは、クラス`Type`の要素が等価比較できる場合にのみ等価比較が可能で、クラス`Type`の要素が比較可能な値よりも小さい場合に限り、小なり比較できます。

C++ 標準ライブラリで定義されたコンテナー アダプターには、stack、queue、および priority_queue の 3 つの種類があります。 それぞれが、基になるコンテナー クラスの機能を制限して、標準的なデータ構造に対して精密に制御されたインターフェイスを提供します。

- [stack クラス](../standard-library/stack-class.md) は、後入れ先出し (LIFO) のデータ構造をサポートしています。 思い描くのに助けとなるのは、積み重ねられた皿です。 要素 (皿) は、積み重ねの一番上からのみ挿入、検査、または削除できます。積み重ねの一番上に相当するのは、基本のコンテナーの末尾にある最後の要素です。 一番上の要素にのみアクセスできる制限があることが、stack クラスを使用する理由です。

- queue クラスは、先入れ先出し (FIFO) のデータ構造をサポートしています。 思い描くのに助けとなるのは、銀行の窓口で並んでいる人です。 要素 (人々) は、列の一番後ろに追加され、列の一番前から取り除くことができます。 列の一番前と一番後ろの両方を検査できます。 このように一番前と一番後ろの要素にのみアクセスできる制限があることが、queue クラスを使用する理由です。

- [priority_queue クラス](../standard-library/priority-queue-class.md)は、最も大きな要素が常に先頭の位置になるように、その要素を並べ替えます。 要素の挿入、および先頭の要素の検査と削除をサポートしています。 思い描くのに助けとなるのは、年齢、身長、またはその他の条件によって整列している人です。

## <a name="members"></a>メンバー

### <a name="constructors"></a>コンストラクター

|||
|-|-|
|[queue](#queue)|空であるか、基本のコンテナー オブジェクトのコピーである `queue` を構築します。|

### <a name="typedefs"></a>Typedef

|||
|-|-|
|[container_type](#container_type)|`queue` によって適合されるように、基本のコンテナーを提供する型。|
|[size_type](#size_type)|`queue` 内の要素の数を表すことができる符号なし整数型。|
|[value_type](#value_type)|`queue` 内に要素として格納されるオブジェクトの種類を表す型。|

### <a name="functions"></a>関数

|||
|-|-|
|[back](#back)|`queue` の後ろに最も直近に追加された要素への参照を返します。|
|[empty](#empty)|`queue` が空かどうかをテストします。|
|[front](#front)|`queue` の一番前にある最初の要素への参照を返します。|
|[pop](#pop)|`queue` の一番前から要素を削除します。|
|[push](#push)|`queue` の後ろに要素を追加します。|
|[size](#size)|`queue` 内の要素数を返します。|

## <a name="back"></a>戻る

キューの後ろに最も直近に追加された要素への参照を返します。

```cpp
reference back();

const_reference back() const;
```

### <a name="return-value"></a>戻り値

キューの最後の要素。 キューが空の場合、戻り値は定義されません。

### <a name="remarks"></a>Remarks

`back` の戻り値が `const_reference` に割り当てられている場合、queue オブジェクトは変更できません。 の`back`戻り値が`reference`に割り当てられている場合は、queue オブジェクトを変更できます。

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) を 1 または 2 として定義してコンパイルすると、空のキュー内の要素にアクセスしようとした場合に実行時エラーが発生します。  詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// queue_back.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 11 );

   int& i = q1.back( );
   const int& ii = q1.front( );

   cout << "The integer at the back of queue q1 is " << i
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << ii
        << "." << endl;
}
```

## <a name="container_type"></a>container_type

適合される基本のコンテナーを提供する型。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Container` のシノニムです。 2 つの C++ 標準ライブラリ シーケンス コンテナー クラス (list クラスと既定の deque クラス) は、queue オブジェクトの基本のコンテナーとして使用する要件を満たしています。 要件を満たすユーザー定義型を使用することもできます。

`Container` の詳細については、[queue クラス](../standard-library/queue-class.md)のトピックのコメントのセクションをご覧ください。

### <a name="example"></a>例

`container_type` の宣言方法や使用方法の例については、[queue](#queue) の例をご覧ください。

## <a name="empty"></a>指定

キューが空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

キューが空の場合は **true**、キューが空ではない場合は **false**。

### <a name="example"></a>例

```cpp
// queue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue <int> q1, q2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The queue q1 is empty." << endl;
   else
      cout << "The queue q1 is not empty." << endl;

   if ( q2.empty( ) )
      cout << "The queue q2 is empty." << endl;
   else
      cout << "The queue q2 is not empty." << endl;
}
```

```Output
The queue q1 is not empty.
The queue q2 is empty.
```

## <a name="front"></a>外側

キューの一番前にある最初の要素への参照を返します。

```cpp
reference front();

const_reference front() const;
```

### <a name="return-value"></a>戻り値

キューの最初の要素。 キューが空の場合、戻り値は定義されません。

### <a name="remarks"></a>Remarks

`front` の戻り値が `const_reference` に割り当てられている場合、queue オブジェクトは変更できません。 の`front`戻り値が`reference`に割り当てられている場合は、queue オブジェクトを変更できます。

このメンバー関数は、 `reference`被制御シーケンスの最初の要素にを返します。この要素は空でなければなりません。

[_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) を 1 または 2 として定義してコンパイルすると、空のキュー内の要素にアクセスしようとした場合に実行時エラーが発生します。  詳細については、「[チェックを行う反復子](../standard-library/checked-iterators.md)」を参照してください。

### <a name="example"></a>例

```cpp
// queue_front.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main() {
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   int& ii = q1.back( );
   int& iii = q1.front( );

   cout << "The integer at the back of queue q1 is " << ii
        << "." << endl;
   cout << "The integer at the front of queue q1 is " << iii
        << "." << endl;
}
```

## <a name="pop"></a>ショート

キューの一番前から要素を削除します。

```cpp
void pop();
```

### <a name="remarks"></a>Remarks

メンバー関数を適用するには、キューは空でない必要があります。 キューの先頭は最も直近に追加された要素によって占有されている位置で、コンテナーの末尾にある最後の要素です。

### <a name="example"></a>例

```cpp
// queue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;

   q1.pop( );

   i = q1.size( );
   cout << "After a pop the queue length is "
        << i << "." << endl;

   i = q1. front ( );
   cout << "After a pop, the element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
After a pop the queue length is 2.
After a pop, the element at the front of the queue is 20.
```

## <a name="push"></a>押し付け

キューの一番後ろに要素を追加します。

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>パラメーター

*val*\
キューの一番後ろに追加する要素。

### <a name="remarks"></a>Remarks

キューの一番後ろは最も直近に追加された要素によって占有されている位置で、コンテナーの末尾にある最後の要素です。

### <a name="example"></a>例

```cpp
// queue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   queue <int>::size_type i;
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   i = q1.front( );
   cout << "The element at the front of the queue is "
        << i << "." << endl;
}
```

```Output
The queue length is 3.
The element at the front of the queue is 10.
```

## <a name="queue"></a>再生

空であるか、基本のコンテナー オブジェクトのコピーであるキューを構築します。

```cpp
queue();

explicit queue(const container_type& right);
```

### <a name="parameters"></a>パラメーター

*そうです*\
構築されるキューのコピー元となる **const** コンテナ―。

### <a name="remarks"></a>Remarks

キューの既定の基本コンテナーは、deque です。 基本のコンテナーとして list を指定することもできますが、vector を指定することはできません。必要な `pop_front` メンバー関数がないからです。

### <a name="example"></a>例

```cpp
// queue_queue.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares queue with default deque base container
   queue <char> q1;

   // Explicitly declares a queue with deque base container
   queue <char, deque<char> > q2;

   // These lines don't cause an error, even though they
   // declares a queue with a vector base container
   queue <int, vector<int> > q3;
   q3.push( 10 );
   // but the following would cause an error because vector has
   // no pop_front member function
   // q3.pop( );

   // Declares a queue with list base container
   queue <int, list<int> > q4;

   // The second member function copies elements from a container
   list<int> li1;
   li1.push_back( 1 );
   li1.push_back( 2 );
   queue <int, list<int> > q5( li1 );
   cout << "The element at the front of queue q5 is "
        << q5.front( ) << "." << endl;
   cout << "The element at the back of queue q5 is "
        << q5.back( ) << "." << endl;
}
```

```Output
The element at the front of queue q5 is 1.
The element at the back of queue q5 is 2.
```

## <a name="size"></a>幅

キュー内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

キューの現在の長さ。

### <a name="example"></a>例

```cpp
// queue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   queue <int> q1, q2;
   queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The queue length is now " << i << "." << endl;
}
```

```Output
The queue length is 1.
The queue length is now 2.
```

## <a name="size_type"></a>size_type

キュー内の要素の数を表すことができる符号なし整数型。

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Remarks

この型は、キューによって採用された基本コンテナーの `size_type` のシノニムです。

### <a name="example"></a>例

`size_type` の宣言方法や使用方法の例については、[queue::front](#front) の例をご覧ください。

## <a name="value_type"></a> value_type

キュー内に要素として格納されるオブジェクトの型を表す型。

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Remarks

この型は、キューによって採用された基本コンテナーの `value_type` のシノニムです。

### <a name="example"></a>例

```cpp
// queue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
using namespace std;

   // Declares queues with default deque base container
   queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   queue<int> q1;
   q1.push(AnInt);
   cout << "The element at the front of the queue is "
        << q1.front( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the front of the queue is 69.
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
