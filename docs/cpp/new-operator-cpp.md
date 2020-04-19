---
title: new 演算子 (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- new keyword [C++]
ms.assetid: 69fee812-1c28-4882-8fda-d1ad17860004
ms.openlocfilehash: bcb7784e59966510970bd9b3ae0157ae982e462d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245388"
---
# <a name="new-operator-c"></a>new 演算子 (C++)

オブジェクトまたはオブジェクトの配列にメモリを割り当てます*型名*フリー ストアから、オブジェクトに適切に型指定されたゼロ以外のポインターを返します。

> [!NOTE]
>  Microsoft C Component Extensions のサポートを提供する、**new** キーワードによる vtable スロット エントリを追加します。 詳細については、[new (vtable の新しいスロット) ](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) を参照してください。
>  Microsoft C Component Extensions のサポートを提供する、**new**キーワードによる vtable スロット エントリを追加します。 詳細については、[new (vtable の新しいスロット) ](../extensions/new-new-slot-in-vtable-cpp-component-extensions.md) を参照してください。


## <a name="syntax"></a>構文

```
[::] new [placement] new-type-name [new-initializer]
[::] new [placement] ( type-name ) [new-initializer]
```

## <a name="remarks"></a>Remarks

失敗した場合、**new**は 0 を返しますまたは例外をスローします。 を参照してください[new 演算子と delete 演算子](../cpp/new-and-delete-operators.md)詳細についてはします。 この既定の動作を変更するには、カスタム例外処理ルーチンを記述し、呼び出すことによって、 [_set_new_handler](../c-runtime-library/reference/set-new-handler.md)ランタイム ライブラリ関数を引数として関数名。

マネージ ヒープのオブジェクトを作成する方法については、次を参照してください。 [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)します。

ときに**new**は C++ クラス オブジェクトのメモリを割り当てに使用されるに、メモリが割り当てられた後、オブジェクトのコンス トラクターは呼び出されます。

使用して、[delete](../cpp/delete-operator-cpp.md) 演算子を使用して割り当てられたメモリの割り当てを解放、**new** 演算子。

次の例では、サイズ `dim` × 10 の文字の 2 次元配列を割り当てた後、解放します。 多次元配列を割り当てるときに、最初の次元を除くすべての次元は、正の値に評価される定数式であることが必要です。配列の一番左の次元は、正の値に評価される任意の値でかまいません。 使用して、配列を割り当てるときに、**new** 演算子は、最初の次元を 0 にすることができます。**new** 演算子は一意のポインターを返します。
次の例では、サイズ `dim` × 10 の文字の 2 次元配列を割り当てた後、解放します。 多次元配列を割り当てるときに、最初の次元を除くすべての次元は、正の値に評価される定数式であることが必要です。配列の一番左の次元は、正の値に評価される任意の値でかまいません。 使用して、配列を割り当てるときに、**new** 演算子は、最初の次元を 0 にすることができます。**new** 演算子は一意のポインターを返します。


```cpp
char (*pchar)[10] = new char[dim][10];
delete [] pchar;
```

*型名*含めることはできません**const**、**volatile**、クラス宣言、または列挙体の宣言。 したがって、次の式は無効です。

```cpp
volatile char *vch = new volatile char[20];
```

**new**オブジェクトではないために、演算子が参照型を割り当てられません。

**new** 演算子を使用して、関数を割り当てることはできませんが、関数へのポインターを割り当てるために使用できます。 次の例では、整数を返す関数への 7 個のポインターの配列を割り当てた後、解放します。

```cpp
int (**p) () = new (int (*[7]) ());
delete *p;
```

演算子を使用する場合**new**なしでコンパイル、追加の引数、 [/GX](../build/reference/gx-enable-exception-handling.md)、 [/EHa](../build/reference/eh-exception-handling-model.md)、または[/EHs](../build/reference/eh-exception-handling-model.md)オプション、コンパイラでは演算子を呼び出すコードを生成**delete**場合は、コンス トラクターが例外をスローします。

次に示しますの文法要素**new**:

*placement*<br/>
オーバー ロードする場合は、追加の引数を渡す方法を提供します。**new**します。

*type-name*<br/>
割り当てる型を指定します。組み込みまたはユーザー定義の型を指定できます。 型の指定が複雑な場合には、かっこで囲むことでバインディング順を強制的に適用できます。

*initializer*<br/>
初期化されたオブジェクトの値を指定します。 初期化子は配列には指定できません。 **new** 演算子は、クラスに既定のコンス トラクターがある場合にのみ、オブジェクトの配列は作成します。

## <a name="example"></a>例

次のコード例では、文字配列と `CName` クラスのオブジェクトを割り当てた後、解放します。

```cpp
// expre_new_Operator.cpp
// compile with: /EHsc
#include <string.h>

class CName {
public:
   enum {
      sizeOfBuffer = 256
   };

   char m_szFirst[sizeOfBuffer];
   char m_szLast[sizeOfBuffer];

public:
   void SetName(char* pszFirst, char* pszLast) {
     strcpy_s(m_szFirst, sizeOfBuffer, pszFirst);
     strcpy_s(m_szLast, sizeOfBuffer, pszLast);
   }

};

int main() {
   // Allocate memory for the array
   char* pCharArray = new char[CName::sizeOfBuffer];
   strcpy_s(pCharArray, CName::sizeOfBuffer, "Array of characters");

   // Deallocate memory for the array
   delete [] pCharArray;
   pCharArray = NULL;

   // Allocate memory for the object
   CName* pName = new CName;
   pName->SetName("Firstname", "Lastname");

   // Deallocate memory for the object
   delete pName;
   pName = NULL;
}
```

## <a name="example"></a>例

**new** 演算子の配置の新しいフォーム (割り当てサイズに加えて引数を持つフォーム) を使用する場合と、コンストラクターが例外をスローする場合、コンパイラは、**delete** 演算子の配置フォームををサポートしません。 例:


```cpp
// expre_new_Operator2.cpp
// C2660 expected
class A {
public:
   A(int) { throw "Fail!"; }
};
void F(void) {
   try {
      // heap memory pointed to by pa1 will be deallocated
      // by calling ::operator delete(void*).
      A* pa1 = new A(10);
   } catch (...) {
   }
   try {
      // This will call ::operator new(size_t, char*, int).
      // When A::A(int) does a throw, we should call
      // ::operator delete(void*, char*, int) to deallocate
      // the memory pointed to by pa2.  Since
      // ::operator delete(void*, char*, int) has not been implemented,
      // memory will be leaked when the deallocation cannot occur.

      A* pa2 = new(__FILE__, __LINE__) A(20);
   } catch (...) {
   }
}

int main() {
   A a;
}
```

## <a name="initializing-object-allocated-with-new"></a>new で割り当てたオブジェクトの初期化

省略可能な*初期化子*の文法でフィールドが含まれる、**new** 演算子。 これにより、新しいオブジェクトをユーザー定義コンストラクターで初期化できます。 初期化を行う方法の詳細については、次を参照してください。[初期化子](../cpp/initializers.md)します。 次の例で、初期化式を使用する方法を示しています、**new** 演算子。

```cpp
// expre_Initializing_Objects_Allocated_with_new.cpp
class Acct
{
public:
    // Define default constructor and a constructor that accepts
    //  an initial balance.
    Acct() { balance = 0.0; }
    Acct( double init_balance ) { balance = init_balance; }
private:
    double balance;
};

int main()
{
    Acct *CheckingAcct = new Acct;
    Acct *SavingsAcct = new Acct ( 34.98 );
    double *HowMuch = new double ( 43.0 );
    // ...
}
```

この例では、オブジェクトで`CheckingAcct`を使用して割り当てられている、**new** 演算子がない既定の初期化を指定します。 したがって、`Acct()` クラスの既定のコンストラクターが呼び出されます。 その後、オブジェクト `SavingsAcct` は、同じように割り当てられます。ただし、明示的に 34.98 に初期化されます。 型の 34.98 であるため**double**初期化を処理するためにその型の引数を受け取るコンス トラクターが呼び出されます。 最後に、`HowMuch` 非クラス型は 43.0 に初期化されます。

オブジェクトを初期化できるように、クラス型のオブジェクトは、そのクラスがコンス トラクター (前の例では) のように、**new** 演算子がこれらの条件のいずれかが満たされた場合にのみ。

- 初期化子内に指定された引数は、コンストラクターの引数と一致します。

- クラスには、既定のコンストラクター (引数を指定せずに呼び出すことができるコンストラクター) があります。

要素ごとの明示的な初期化を完了できませんを使用して配列を割り当てる場合、**new** 演算子です。 既定コンス トラクターのみ存在する場合と呼びます。 参照してください[既定の引数](../cpp/default-arguments.md)詳細についてはします。

メモリ割り当てが失敗した場合 (**new 演算子** は 0 の値を返します)、初期化は行われません。 これによって、存在しないデータを初期化しようとすることを防止できます。


関数呼び出しの場合と同様に、初期化された式が評価される順序は定義されていません。 さらに、メモリの割り当てが実行される前に、これらの式が完全に評価されるものとして信頼しないでください。 メモリの割り当てが失敗した場合、**new** 演算子は 0 を返します、初期化子の一部の式の評価を完全にない場合があります。

## <a name="lifetime-of-objects-allocated-with-new"></a>new で割り当てたオブジェクトの有効期間

オブジェクトが割り当てられた、**new** 演算子は定義されているスコープが終了したときに破棄されません。 **new** 演算子が割り当てたオブジェクトへのポインターを返します、プログラムでこれらのオブジェクトにアクセスする適切なスコープを持つポインターを定義する必要があります。 例:

```cpp
// expre_Lifetime_of_Objects_Allocated_with_new.cpp
// C2541 expected
int main()
{
    // Use new operator to allocate an array of 20 characters.
    char *AnArray = new char[20];

    for( int i = 0; i < 20; ++i )
    {
        // On the first iteration of the loop, allocate
        //  another array of 20 characters.
        if( i == 0 )
        {
            char *AnotherArray = new char[20];
        }
    }

    delete [] AnotherArray; // Error: pointer out of scope.
    delete [] AnArray;      // OK: pointer still in scope.
}
```

この例では、ポインター `AnotherArray` がスコープ外になると、オブジェクトを削除できなくなります。

## <a name="how-new-works"></a>new の機能

*割り当て式*-式を含む、**new** 演算子: 3 つの処理します。

- 割り当てられるオブジェクトのストレージを探し、予約します。 この段階が完了すると、適切なサイズのストレージが割り当てられます。ただし、まだオブジェクトではありません。

- オブジェクトを初期化します。 初期化が完了すると、割り当てられたストレージをオブジェクトにするための十分な情報が得られます。

- 派生したポインター型のオブジェクトへのポインターを返します。*新しい型名*または*型名*します。 プログラムでは、このポインターを使用して新しく割り当てられたオブジェクトにアクセスします。

**new** 演算子は、**new 演算子** 関数を呼び出します。 任意の型の配列および **class**、**struct** 、**union** 型でないオブジェクト、グローバル関数では、 **:: new 演算子** は、記憶域の割り当てに呼び出されます。 class 型のオブジェクトは、クラスごとに **new 演算子**独自静的メンバー関数を定義できます。

コンパイラは、**type** 型のオブジェクトを割り当てるために **new** 演算子を検出すると、`type` **:: new 演算子 (sizeof (** `type` **))** の呼び出しを発行します。または、ユーザー定義 **new 演算子** が定義されていない場合、 **:: new 演算子 (sizeof (** `type` **))** の呼び出しを発行します。 そのため、**new** 演算子は、オブジェクトに適切なメモリ量を割り当てることができます。

コンパイラは、**type** 型のオブジェクトを割り当てるために **new** 演算子を検出すると、`type` **:: new 演算子 (sizeof (** `type`**))**の呼び出しを発行します。または、ユーザー定義 **new 演算子** が定義されていない場合、 **:: new 演算子 (sizeof (** `type` **))** の呼び出しを発行します。そのため、**new** 演算子は、オブジェクトに適切なメモリ量を割り当てることができます。

> [!NOTE]
>  **new 演算子** の引数は `size_t` 型です。 この型は、\<direct.h >、 \<malloc.h >、 \<memory.h >、 \<search.h >、 \<stddef.h >、 \<stdio.h >、 \<stdlib.h >、 \<string.h >、および\<time.h > で定義されます。

文法のオプションが指定できるように *配置* を指定できます([new 演算子](../cpp/new-operator-cpp.md) の文法を参照してください)。 *配置* パラメーターは、**new 演算子** のユーザー定義の実装にのみ使用でき、**new 演算子** に追加情報を渡すことができます。クラス T を持つメンバー演算子で、`T *TObject = new ( 0x0040 ) T;` のように *配置* フィールドを持つ式は、`T *TObject = T::operator new( sizeof( T ), 0x0040 );` に変換されます。それ以外の場合は`T *TObject = ::operator new( sizeof( T ), 0x0040 );` に変換されます。

文法のオプションにより、*配置* を指定できます ([new 演算子](../cpp/new-operator-cpp.md)) の文法を参照してください) 。 *配置* パラメーターは、**new 演算子** のユーザー定義の実装のパラメーターにのみ使用でき、**new 演算子** に追加情報を渡すことができます。 クラス T にメンバー new 演算子を持つ、`T *TObject = new ( 0x0040 ) T;`のようなフィールドは、`T *TObject = T::operator new( sizeof( T ), 0x0040 );`に変換され、そうでない場合は `T *TObject = ::operator new( sizeof( T ), 0x0040 );`に変換されます。

本来の目的、*配置*フィールドは、ユーザーが指定したアドレスに割り当てられるハードウェアに依存するオブジェクトを許可するがします。

> [!NOTE]
>  前の例では、*配置*フィールドに引数が 1 つだけしか示されていませんが、この方法で **new 演算子** に渡すことができる引数の数に制限はありません。

**new 演算子**が定義されているクラス型の場合でも、この例のフォームを使用して、グローバル演算子が使用することができます。

**new 演算子**が定義されているクラス型の場合でも、この例のフォームを使用して、グローバル演算子が使用することができます。


```cpp
T *TObject =::new TObject;
```

スコープ解決演算子 (`::`)、グローバルの使用を強制**new**演算子。

## <a name="see-also"></a>関連項目

[単項演算子を含む式](../cpp/expressions-with-unary-operators.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[new 演算子と delete 演算子](../cpp/new-and-delete-operators.md)

