---
title: priority_queue クラス
ms.date: 11/04/2016
f1_keywords:
- queue/std::priority_queue::container_type
- queue/std::priority_queue::size_type
- queue/std::priority_queue::value_type
- queue/std::priority_queue::empty
- queue/std::priority_queue::pop
- queue/std::priority_queue::push
- queue/std::priority_queue::size
- queue/std::priority_queue::top
helpviewer_keywords:
- std::priority_queue [C++], container_type
- std::priority_queue [C++], size_type
- std::priority_queue [C++], value_type
- std::priority_queue [C++], empty
- std::priority_queue [C++], pop
- std::priority_queue [C++], push
- std::priority_queue [C++], size
- std::priority_queue [C++], top
ms.assetid: 69fca9cc-a449-4be4-97b7-02ca5db9cbb2
ms.openlocfilehash: 3591264efec87c2c3454d0f885c19b30b73ae51c
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458425"
---
# <a name="priorityqueue-class"></a>priority_queue クラス

基になるコンテナー型の先頭にあって常に最大になるか、または優先順位が最も高くなる要素へのアクセスを制限することにより、機能の制限を提供するテンプレート コンテナーのアダプター クラスです。 priority_queue に新しい要素を追加でき、priority_queue の最上位の要素を検査または削除できます。

## <a name="syntax"></a>構文

```cpp
template <class Type, class Container= vector <Type>, class Compare= less <typename Container ::value_type>>
class priority_queue
```

### <a name="parameters"></a>パラメーター

*各種*\
priority_queue に格納される要素のデータ型。

*コンテナー*\
priority_queue を実装するために使用する基になるコンテナーの型。

*対照*\
2 つの要素の値を並べ替えキーとして比較して、priority_queue 内の要素の相対順序を決定できる関数オブジェクトを提供する型。 この引数は省略可能であり、既定値は二項述語 `less<typename Container::value_type>` です。

## <a name="remarks"></a>Remarks

Queue オブジェクトの最初`Type`のテンプレートパラメーターで指定されるクラスの要素は[value_type](#value_type)と同義であり、2つ目のテンプレートによって指定`Container`される、基になるコンテナークラスの要素の型と一致している必要があります。引き. その`Type`型のオブジェクトをコピーし、その型の変数に値を割り当てることができるように、は割り当て可能である必要があります。

Priority_queue は、クラス`Traits`の格納されている関数オブジェクトを呼び出すことによって、制御するシーケンスを並べ替えます。 通常、要素は、この順序を確立するために小なり比較だけを実行できる必要があります。これにより、2 つの要素が指定されたときに、それらの要素が等しいか (どちらか一方が小さくはない)、または一方が他方より小さいかを判断できます。 この結果、等価でない複数の要素間で順序が付けられます。 テクニカル ノートでは、比較関数は、数学上の標準的な意味で厳密弱順序を発生させる二項述語であると示されています。

priority_queue に適した基になるコンテナー クラスには、[deque クラス](../standard-library/deque-class.md)および既定の [vector クラス](../standard-library/vector-class.md)、または `front`、`push_back`、および `pop_back` の各操作をサポートするその他すべてのシーケンス コンテナーがあります。 基になるコンテナー クラスは、コンテナー アダプター内にカプセル化されます。コンテナー アダプターは、限られた一連のシーケンス コンテナーのメンバーの関数のみをパブリック インターフェイスとして公開します。

`priority_queue` での要素の追加および要素の削除の両方に、対数の複雑さがあります。 `priority_queue` 内の要素へのアクセスには、定数の複雑さがあります。

C++ 標準ライブラリで定義されたコンテナー アダプターには、stack、queue、および priority_queue の 3 つの種類があります。 それぞれが、基になるコンテナー クラスの機能を制限して、標準的なデータ構造に正確に制御されたインターフェイスを提供します。

- [stack クラス](../standard-library/stack-class.md)は、後入れ先出し (LIFO) のデータ構造をサポートしています。 思い描くのに助けとなるのは、積み重ねられた皿です。 要素 (皿) は、積み重ねの一番上からのみ挿入、検査、または削除できます。積み重ねの一番上に相当するのは、基本のコンテナーの末尾にある最後の要素です。 一番上の要素にのみアクセスできる制限があることが、stack クラスを使用する理由です。

- [queue クラス](../standard-library/queue-class.md)は、先入れ先出し (FIFO) のデータ構造をサポートしています。 思い描くのに助けとなるのは、銀行の窓口で並んでいる人です。 要素 (人々) は、列の一番後ろに追加され、列の一番前から取り除くことができます。 列の一番前と一番後ろの両方を検査できます。 このように一番前と一番後ろの要素にのみアクセスできる制限があることが、queue クラスを使用する理由です。

- priority_queue クラスは、最も大きな要素が常に先頭の位置になるように、その要素を並べ替えます。 要素の挿入、および先頭の要素の検査と削除をサポートしています。 思い描くのに助けとなるのは、年齢、身長、またはその他の条件によって整列している人です。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[priority_queue](#priority_queue)|空であるか、基本のコンテナー オブジェクトまたはその他の `priority_queue` の範囲のコピーである `priority_queue` を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[container_type](#container_type)|`priority_queue` によって適合されるように、基本のコンテナーを提供する型。|
|[size_type](#size_type)|`priority_queue` 内の要素の数を表すことができる符号なし整数型。|
|[value_type](#value_type)|`priority_queue` 内に要素として格納されるオブジェクトの種類を表す型。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[empty](#empty)|`priority_queue` が空かどうかをテストします。|
|[pop](#pop)|最上位から `priority_queue` の最大の要素を削除します。|
|[push](#push)|operator< からの要素の優先順位に基づいて、優先順位キューに要素を追加します。|
|[size](#size)|`priority_queue` 内の要素数を返します。|
|[top](#top)|`priority_queue` の最上位にある最大要素への const 参照を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<queue>

**名前空間:** std

## <a name="container_type"></a>  priority_queue::container_type

適合される基本のコンテナーを提供する型。

```cpp
typedef Container container_type;
```

### <a name="remarks"></a>Remarks

この型は、テンプレート パラメーター `Container` のシノニムです。 C++ 標準ライブラリのシーケンス コンテナー クラス `deque` と既定のクラス `vector` は、priority_queue オブジェクトの基本のコンテナーとして使用するための要件を満たしています。 要件を満たすユーザー定義型を使用することもできます。

`Container` の詳細については、「[priority_queue クラス](../standard-library/priority-queue-class.md)」トピックの「コメント」セクションを参照してください。

### <a name="example"></a>例

`container_type` の宣言方法や使用例については、[priority_queue](#priority_queue) の例を参照してください。

## <a name="empty"></a>  priority_queue::empty

priority_queue が空かどうかをテストします。

```cpp
bool empty() const;
```

### <a name="return-value"></a>戻り値

priority_queue が空である場合は **true**、priority_queue が空でない場合は **false**。

### <a name="example"></a>例

```cpp
// pqueue_empty.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue <int> q1, s2;

   q1.push( 1 );

   if ( q1.empty( ) )
      cout << "The priority_queue q1 is empty." << endl;
   else
      cout << "The priority_queue q1 is not empty." << endl;

   if ( s2.empty( ) )
      cout << "The priority_queue s2 is empty." << endl;
   else
      cout << "The priority_queue s2 is not empty." << endl;
}
```

```Output
The priority_queue q1 is not empty.
The priority_queue s2 is empty.
```

## <a name="pop"></a>  priority_queue::pop

最上位から priority_queue の最大の要素を削除します。

```cpp
void pop();
```

### <a name="remarks"></a>Remarks

メンバー関数を適用するには、priority_queue を空にすることはできません。 priority_queue の最上位は、常に、コンテナー内の最大要素に占有されます。

### <a name="example"></a>例

```cpp
// pqueue_pop.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, s2;

   q1.push( 10 );
   q1.push( 20 );
   q1.push( 30 );

   priority_queue <int>::size_type i, iii;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;

   q1.pop( );

   iii = q1.size( );
   cout << "After a pop, the priority_queue length is "
        << iii << "." << endl;

   const int& iv = q1.top( );
   cout << "After a pop, the element at the top of the "
        << "priority_queue is " << iv << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
After a pop, the priority_queue length is 2.
After a pop, the element at the top of the priority_queue is 20.
```

## <a name="priority_queue"></a>  priority_queue::priority_queue

空であるか、基本のコンテナー オブジェクトまたは別の priority_queue の範囲のコピーである priority_queue を構築します。

```cpp
priority_queue();

explicit priority_queue(const Traits& _comp);

priority_queue(const Traits& _comp, const container_type& _Cont);

priority_queue(const priority_queue& right);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp);

template <class InputIterator>
priority_queue(InputIterator first, InputIterator last, const Traits& _comp, const container_type& _Cont);
```

### <a name="parameters"></a>パラメーター

*カンプ (_s)* \
priority_queue 内の要素の並べ替えに使用される、**constTraits** 型の比較関数。既定では基本コンテナーの関数を比較します。

*続き*\
構築された priority_queue がコピーになる元の基本コンテナー。

*そうです*\
構築される set のコピー元となる priority_queue。

*まずは*\
コピーする要素範囲内の最初の要素の位置。

*前の*\
コピーする要素範囲を超える最初の要素の位置。

### <a name="remarks"></a>Remarks

最初の3つの各コンストラクターは、空の初期 priority_queue を指定します。2番目の`comp`コンストラクターは、要素の順序を確立するために使用する比較関数の型 () も指定し、3番目のコンストラクターはを明示的に指定`container_type`します。(`_Cont`) を使用します。 キーワード **explicit** は、特定の種類の自動型変換が実行されないようにします。

4番目のコンストラクターは、priority_queue*権限*のコピーを指定します。

最後の3つのコンストラクターは\[、いくつかのコンテナーの*最初*の範囲をコピーし、その値を使用して priority_queue を初期化し*ます。* 下`Traits`は、クラスの比較関数の型を指定します`container_type`。

### <a name="example"></a>例

```cpp
// pqueue_ctor.cpp
// compile with: /EHsc
#include <queue>
#include <vector>
#include <deque>
#include <list>
#include <iostream>

int main( )
{
   using namespace std;

   // The first member function declares priority_queue
   // with a default vector base container
   priority_queue <int> q1;
   cout << "q1 = ( ";
   while ( !q1.empty( ) )
   {
      cout << q1.top( ) << " ";
      q1.pop( );
   }
   cout << ")" << endl;

   // Explicitly declares a priority_queue with nondefault
   // deque base container
   priority_queue <int, deque <int> > q2;
   q2.push( 5 );
   q2.push( 15 );
   q2.push( 10 );
   cout << "q2 = ( ";
   while ( !q2.empty( ) )
   {
      cout << q2.top( ) << " ";
      q2.pop( );
   }
   cout << ")" << endl;

   // This method of printing out the elements of a priority_queue
   // removes the elements from the priority queue, leaving it empty
   cout << "After printing, q2 has " << q2.size( ) << " elements." << endl;

   // The third member function declares a priority_queue
   // with a vector base container and specifies that the comparison
   // function greater is to be used for ordering elements
   priority_queue <int, vector<int>, greater<int> > q3;
   q3.push( 2 );
   q3.push( 1 );
   q3.push( 3 );
   cout << "q3 = ( ";
   while ( !q3.empty( ) )
   {
      cout << q3.top( ) << " ";
      q3.pop( );
   }
   cout << ")" << endl;

   // The fourth member function declares a priority_queue and
   // initializes it with elements copied from another container:
   // first, inserting elements into q1, then copying q1 elements into q4
   q1.push( 100 );
   q1.push( 200 );
   priority_queue <int> q4( q1 );
   cout << "q4 = ( ";
   while ( !q4.empty( ) )
   {
      cout << q4.top( ) << " ";
      q4.pop( );
   }
   cout << ")" << endl;

   // Creates an auxiliary vector object v5 to be used to initialize q5
   vector <int> v5;
   vector <int>::iterator v5_Iter;
   v5.push_back( 10 );
   v5.push_back( 30 );
   v5.push_back( 20 );
   cout << "v5 = ( " ;
   for ( v5_Iter = v5.begin( ) ; v5_Iter != v5.end( ) ; v5_Iter++ )
      cout << *v5_Iter << " ";
   cout << ")" << endl;

   // The fifth member function declares and
   // initializes a priority_queue q5 by copying the
   // range v5[ first,  last) from vector v5
   priority_queue <int> q5( v5.begin( ), v5.begin( ) + 2 );
   cout << "q5 = ( ";
   while ( !q5.empty( ) )
   {
      cout << q5.top( ) << " ";
      q5.pop( );
   }
   cout << ")" << endl;

   // The sixth member function declares a priority_queue q6
   // with a comparison function greater and initializes q6
   // by copying the range v5[ first,  last) from vector v5
   priority_queue <int, vector<int>, greater<int> >
      q6( v5.begin( ), v5.begin( ) + 2 );
   cout << "q6 = ( ";
   while ( !q6.empty( ) )
   {
      cout << q6.top( ) << " ";
      q6.pop( );
   }
   cout << ")" << endl;
}
```

## <a name="push"></a>  priority_queue::push

operator< からの要素の優先順位に基づいて、優先順位キューに要素を追加します。

```cpp
void push(const Type& val);
```

### <a name="parameters"></a>パラメーター

*val*\
priority_queue の最上位に追加された要素。

### <a name="remarks"></a>Remarks

priority_queue の最上位は、コンテナー内の最大要素に占有される位置です。

### <a name="example"></a>例

```cpp
// pqueue_push.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="size"></a>  priority_queue::size

priority_queue 内の要素の数を返します。

```cpp
size_type size() const;
```

### <a name="return-value"></a>戻り値

priority_queue の現在の長さ。

### <a name="example"></a>例

```cpp
// pqueue_size.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue <int> q1, q2;
   priority_queue <int>::size_type i;

   q1.push( 1 );
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   q1.push( 2 );
   i = q1.size( );
   cout << "The priority_queue length is now " << i << "." << endl;
}
```

```Output
The priority_queue length is 1.
The priority_queue length is now 2.
```

## <a name="size_type"></a>  priority_queue::size_type

priority_queue 内の要素の数を表すことができる符号なし整数型。

```cpp
typedef typename Container::size_type size_type;
```

### <a name="remarks"></a>Remarks

この型は、priority_queue によって採用された基本コンテナーの `size_type` のシノニムです。

### <a name="example"></a>例

`size_type` の宣言方法や使用例については、[size](#size) の例を参照してください。

## <a name="top"></a>  priority_queue::top

priority_queue の最上位にある最大要素への const 参照を返します。

```cpp
const_reference top() const;
```

### <a name="return-value"></a>戻り値

Priority_queue のオブジェクトによって`Traits`決定される最大の要素への参照。

### <a name="remarks"></a>Remarks

メンバー関数を適用するには、priority_queue を空にすることはできません。

### <a name="example"></a>例

```cpp
// pqueue_top.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;
   priority_queue<int> q1;

   q1.push( 10 );
   q1.push( 30 );
   q1.push( 20 );

   priority_queue<int>::size_type i;
   i = q1.size( );
   cout << "The priority_queue length is " << i << "." << endl;

   const int& ii = q1.top( );
   cout << "The element at the top of the priority_queue is "
        << ii << "." << endl;
}
```

```Output
The priority_queue length is 3.
The element at the top of the priority_queue is 30.
```

## <a name="value_type"></a>  priority_queue::value_type

priority_queue 内に要素として格納されるオブジェクトの種類を表す型。

```cpp
typedef typename Container::value_type value_type;
```

### <a name="remarks"></a>Remarks

この型は、priority_queue によって採用された基本コンテナーの `value_type` のシノニムです。

### <a name="example"></a>例

```cpp
// pqueue_value_type.cpp
// compile with: /EHsc
#include <queue>
#include <iostream>

int main( )
{
   using namespace std;

   // Declares priority_queues with default deque base container
   priority_queue<int>::value_type AnInt;

   AnInt = 69;
   cout << "The value_type is AnInt = " << AnInt << endl;

   priority_queue<int> q1;
   q1.push( AnInt );
   cout << "The element at the top of the priority_queue is "
        << q1.top( ) << "." << endl;
}
```

```Output
The value_type is AnInt = 69
The element at the top of the priority_queue is 69.
```

## <a name="see-also"></a>関連項目

[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
