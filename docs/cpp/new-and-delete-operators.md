---
title: new および delete 演算子
ms.date: 11/19/2019
f1_keywords:
- delete_cpp
- new
helpviewer_keywords:
- new keyword [C++]
- delete keyword [C++]
ms.assetid: fa721b9e-0374-4f04-bb87-032ea775bcc8
ms.openlocfilehash: c64b15f1e1e63b1e743743883429ffd11007de0a
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246449"
---
# <a name="new-and-delete-operators"></a>new および delete 演算子

C++では、 [new](new-operator-cpp.md)演算子と[delete](delete-operator-cpp.md)演算子を使用したオブジェクトの動的な割り当てと解放がサポートされています。 これらの演算子は、フリー ストアと呼ばれるプールからオブジェクトのメモリを割り当てます。 **New**演算子は特殊な関数[operator new](new-operator-cpp.md)を呼び出し、 **delete**演算子は特殊な関数[operator delete](delete-operator-cpp.md)を呼び出します。

標準ライブラリの**新しい**関数は、 C++標準で指定されている動作をサポートします。これは、メモリ割り当てが失敗した場合に std:: bad_alloc 例外をスローします。 C++ それでも**新しい**のスローされないバージョンが必要な場合は、プログラムを nothrownew にリンクします。ただし、nothrownew とリンクすると、 C++標準ライブラリの新しい既定の**演算子**は機能しなくなります。

C ランタイムライブラリとC++標準ライブラリを構成するライブラリファイルの一覧については、「 [CRT ライブラリの機能](../c-runtime-library/crt-library-features.md)」を参照してください。

##  <a id="new_operator"></a> New 演算子

次のようなステートメントがプログラムで発生すると、関数**演算子 new**の呼び出しに変換されます。

```cpp
char *pch = new char[BUFFER_SIZE];
```

要求がゼロバイトのストレージに対するものである場合、 **operator new**は別のオブジェクトへのポインターを返します (つまり、 **operator new**を繰り返し呼び出すと異なるポインターが返されます)。 割り当て要求のメモリが不足している場合、 **operator new**は `std::bad_alloc` 例外をスローします。または、非スロー演算子の**新しい**サポートにリンクしている場合は**nullptr**を返します。

メモリの解放を試み、割り当てを再試行するルーチンを作成できます。詳細については、「 [_set_new_handler](../c-runtime-library/reference/set-new-handler.md) 」を参照してください。 復旧スキームの詳細については、このトピックの「メモリ不足の処理」を参照してください。

次の表では、 **operator new**関数の2つのスコープについて説明します。

### <a name="scope-for-operator-new-functions"></a>Operator new 関数のスコープ

|演算子|スコープ|
|--------------|-----------|
|**:: operator new**|Global|
|*クラス名* **:: operator new**|インスタンス|

**Operator new**の最初の引数は `size_t` 型である必要があります (\<stddef.h > で定義されている型)。戻り値の型は常に**void** <strong>\*</strong>です。

グローバルな**operator new**関数は、 **new**演算子を使用して、組み込み型のオブジェクト、ユーザー定義の**演算子の新しい**関数を含まないクラス型のオブジェクト、および任意の型の配列を割り当てるときに呼び出されます。 **New 演算子を**使用して、 **operator new**が定義されているクラス型のオブジェクトを割り当てると、そのクラスの**operator new**が呼び出されます。

クラスに対して定義された**operator new**関数は、そのクラス型のオブジェクトのグローバル**演算子 new**関数を隠す静的メンバー関数です (したがって、仮想にすることはできません)。 **New**を使用してメモリを割り当て、指定された値に設定する場合を考えてみます。

```cpp
#include <malloc.h>
#include <memory.h>

class Blanks
{
public:
    Blanks(){}
    void *operator new( size_t stAllocateBlock, char chInit );
};
void *Blanks::operator new( size_t stAllocateBlock, char chInit )
{
    void *pvTemp = malloc( stAllocateBlock );
    if( pvTemp != 0 )
        memset( pvTemp, chInit, stAllocateBlock );
    return pvTemp;
}
// For discrete objects of type Blanks, the global operator new function
// is hidden. Therefore, the following code allocates an object of type
// Blanks and initializes it to 0xa5
int main()
{
   Blanks *a5 = new(0xa5) Blanks;
   return a5 != 0;
}
```

**New**にかっこで指定した引数は、`chInit` 引数として `Blanks::operator new` に渡されます。 ただし、グローバルな**operator new**関数は非表示になっているため、次のようなコードでエラーが発生します。

```cpp
Blanks *SomeBlanks = new Blanks;
```

コンパイラは、クラス宣言でのメンバー配列**new**および**delete**演算子をサポートしています。 例 :

```cpp
class MyClass
{
public:
   void * operator new[] (size_t)
   {
      return 0;
   }
   void   operator delete[] (void*)
   {
   }
};

int main()
{
   MyClass *pMyClass = new MyClass[5];
   delete [] pMyClass;
}
```

### <a name="handling-insufficient-memory"></a>メモリ不足の処理

次に示すように、失敗したメモリ割り当てのテストを行うことができます。

```cpp
#include <iostream>
using namespace std;
#define BIG_NUMBER 100000000
int main() {
   int *pI = new int[BIG_NUMBER];
   if( pI == 0x0 ) {
      cout << "Insufficient memory" << endl;
      return -1;
   }
}
```

失敗したメモリ割り当て要求を処理するもう1つの方法があります。 このようなエラーを処理するためのカスタム復旧ルーチンを記述し、 [_set_new_handler](../c-runtime-library/reference/set-new-handler.md)ランタイム関数を呼び出して関数を登録します。

##  <a id="delete_operator"></a> Delete 演算子

**New**演算子を使用して動的に割り当てられたメモリは、 **delete**演算子を使用して解放できます。 Delete 演算子は**operator delete**関数を呼び出します。これにより、使用可能なプールにメモリが解放されます。 **Delete**演算子を使用すると、クラスデストラクター (存在する場合) も呼び出されます。

グローバルおよびクラススコープの**operator delete**関数があります。 特定のクラスに対して定義できる**operator delete**関数は1つだけです。定義されている場合、グローバルな**operator delete**関数は非表示になります。 グローバル**operator delete**関数は、常に任意の型の配列に対して呼び出されます。

グローバルな**operator delete**関数。 グローバル**演算子 delete**およびクラスメンバー **operator delete**関数には、次の2つの形式が存在します。

```cpp
void operator delete( void * );
void operator delete( void *, size_t );
```

指定されたクラスには、前の2つのフォームのうち1つだけが存在できます。 最初のフォームは `void *`型の1つの引数を受け取ります。この引数には、割り当てを解除するオブジェクトへのポインターが含まれています。 2番目の形式 (サイズ割り当て解除) では、2つの引数を取ります。最初の引数は、割り当てを解除するメモリブロックへのポインターであり、2番目の引数が割り当て解除するバイト数です。 両方の形式の戻り値の型は**void**です (**operator delete**は値を返すことができません)。

2番目の形式の目的は、削除するオブジェクトの正しいサイズカテゴリの検索を高速化することです。これは、多くの場合、割り当て自体の近くに格納されることはなく、キャッシュされない可能性があります。 2番目の形式は、基底クラスの**operator delete**関数を使用して派生クラスのオブジェクトを削除する場合に便利です。

**Operator delete**関数は static です。そのため、仮想にすることはできません。 **Operator delete**関数は、「[メンバー Access Control](member-access-control-cpp.md)」で説明されているように、アクセス制御に従います。

次の例は、メモリの割り当てと割り当て解除を記録するように設計されたユーザー定義の**operator new**関数と**operator delete**関数を示しています。

```cpp
#include <iostream>
using namespace std;

int fLogMemory = 0;      // Perform logging (0=no; nonzero=yes)?
int cBlocksAllocated = 0;  // Count of blocks allocated.

// User-defined operator new.
void *operator new( size_t stAllocateBlock ) {
   static int fInOpNew = 0;   // Guard flag.

   if ( fLogMemory && !fInOpNew ) {
      fInOpNew = 1;
      clog << "Memory block " << ++cBlocksAllocated
          << " allocated for " << stAllocateBlock
          << " bytes\n";
      fInOpNew = 0;
   }
   return malloc( stAllocateBlock );
}

// User-defined operator delete.
void operator delete( void *pvMem ) {
   static int fInOpDelete = 0;   // Guard flag.
   if ( fLogMemory && !fInOpDelete ) {
      fInOpDelete = 1;
      clog << "Memory block " << cBlocksAllocated--
          << " deallocated\n";
      fInOpDelete = 0;
   }

   free( pvMem );
}

int main( int argc, char *argv[] ) {
   fLogMemory = 1;   // Turn logging on
   if( argc > 1 )
      for( int i = 0; i < atoi( argv[1] ); ++i ) {
         char *pMem = new char[10];
         delete[] pMem;
      }
   fLogMemory = 0;  // Turn logging off.
   return cBlocksAllocated;
}
```

上記のコードを "メモリ リーク" の検出に使うことができます。メモリ リークとは、フリー ストアに割り当てられ、解放されていないメモリを指します。 この検出を実行するために、グローバルな**new**および**delete**演算子は、メモリの割り当てと解放をカウントするように再定義されています。

コンパイラは、クラス宣言でのメンバー配列**new**および**delete**演算子をサポートしています。 例 :

```cpp
// spec1_the_operator_delete_function2.cpp
// compile with: /c
class X  {
public:
   void * operator new[] (size_t) {
      return 0;
   }
   void operator delete[] (void*) {}
};

void f() {
   X *pX = new X[5];
   delete [] pX;
}
```
