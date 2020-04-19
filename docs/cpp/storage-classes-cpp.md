---
title: ストレージ クラス (C++)
description: でC++は、static、extern、および thread_local キーワードによって、変数または関数の有効期間、リンケージ、およびメモリ位置が指定されます。
ms.date: 12/11/2019
f1_keywords:
- thread_local_cpp
- extern_cpp
- static_cpp
- register_cpp
helpviewer_keywords:
- storage classes [C++], basic concepts
ms.assetid: f10e1c56-6249-4eb6-b08f-09ab1eef1992
ms.openlocfilehash: ab00a5c64a32dc1dab5fef4bc15b722587bc2d6b
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301315"
---
# <a name="storage-classes"></a>ストレージ クラス

*ストレージ クラス*C++ のコンテキストでの変数宣言は、オブジェクトの有効期間、リンケージ、およびメモリの場所を制御する型指定子。 特定のオブジェクトはストレージ クラスを 1 つのみ持つことができます。 ブロック内で定義された変数は、特に**extern**、 **static**、または**thread_local**指定子を使用して指定されていない限り、自動ストレージを持ちます。 自動オブジェクトおよび変数にはリンケージがないため、ブロックの外側のコードには不可視です。 メモリは、ブロックが終了したときにブロックに入って割り当てが解除されると、自動的に割り当てられます。

**ノート**

1. [Mutable](../cpp/mutable-data-members-cpp.md)キーワードは、ストレージクラス指定子と見なすことができます。 ただし、クラス定義のメンバー一覧でのみ使用できます。

1. **Visual Studio 2010 以降:** **Auto**キーワードは、 C++ストレージクラス指定子ではなくなりました。また、 **register**キーワードは非推奨とされます。 **Visual Studio 2017 バージョン15.7 以降:** ( [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)で利用可能): **register**キーワードがC++言語から削除されます。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="static"></a>雑音

**static**キーワードを使用して、変数やグローバル スコープ、名前空間スコープ、およびクラス スコープで関数を宣言することができます。 静的変数は、ローカル スコープでも宣言できます。

静的存続期間は、オブジェクトまたは変数がプログラム起動時に割り当てられ、プログラムの終了時に解放されることを意味します。 外部リンケージは、変数が宣言されたファイルの外部から変数名が参照できることを意味します。 逆に、内部リンケージは、変数が宣言されたファイルの外部でその名前を参照できないことを意味します。 既定では、グローバル名前空間で定義されたオブジェクトまたは変数には静的存続期間と外部リンケージがあります。 **static**キーワードは、次の状況で使用することができます。

1. 変数またはファイルのスコープで関数を宣言する場合 (グローバルまたは名前空間スコープ)、**static**キーワードは、変数または関数が、内部リンケージを持つことを指定します。 変数を宣言すると、変数は静的存続期間が設定され、コンパイラによって 0 に初期化されます (別の値を指定していない場合)。

1. 関数で変数を宣言するときに、**static**キーワードは、変数がその関数呼び出しの間には、その状態を保持することを指定します。

1. クラス宣言でのデータ メンバーを宣言するときに、**static**キーワードは、メンバーの 1 つのコピーが、クラスのすべてのインスタンスで共有されることを指定します。 静的データ メンバーはファイル スコープで定義する必要があります。 整数データ メンバーとして宣言する**const static**初期化子を持つことができます。

1. クラス宣言でメンバー関数を宣言するときに、**static**キーワードは、関数がクラスのすべてのインスタンスで共有されることを指定します。 静的メンバー関数は、関数は、暗黙の型があるないために、インスタンス メンバーにアクセスできません**this**ポインター。 インスタンス メンバーにアクセスするには、インスタンスのポインターまたは参照であるパラメーターを受け取る関数を宣言します。

1. 共用体のメンバーを static として宣言することはできません。 グローバルに宣言された匿名共用体に明示的に宣言する必要がありますが、**static**します。

この例では、変数の宣言方法**static**関数でその関数呼び出しの間には、その状態を保持します。

```cpp
// static1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void showstat( int curr ) {
   static int nStatic;    // Value of nStatic is retained
                          // between each function call
   nStatic += curr;
   cout << "nStatic is " << nStatic << endl;
}

int main() {
   for ( int i = 0; i < 5; i++ )
      showstat( i );
}
```

```Output
nStatic is 0
nStatic is 1
nStatic is 3
nStatic is 6
nStatic is 10
```

この例の使用を示しています。**static**クラスでします。

```cpp
// static2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class CMyClass {
public:
   static int m_i;
};

int CMyClass::m_i = 0;
CMyClass myObject1;
CMyClass myObject2;

int main() {
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject1.m_i = 1;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   myObject2.m_i = 2;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;

   CMyClass::m_i = 3;
   cout << myObject1.m_i << endl;
   cout << myObject2.m_i << endl;
}
```

```Output
0
0
1
1
2
2
3
3
```

この例で宣言されたローカル変数**static**メンバー関数。 静的変数は、プログラム全体で使用できます。型のすべてのインスタンスは、静的変数の同じコピーを共有します。

```cpp
// static3.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;
struct C {
   void Test(int value) {
      static int var = 0;
      if (var == value)
         cout << "var == value" << endl;
      else
         cout << "var != value" << endl;

      var = value;
   }
};

int main() {
   C c1;
   C c2;
   c1.Test(100);
   c2.Test(100);
}
```

```Output
var != value
var == value
```

C++11 以降では、静的ローカル変数の初期化はスレッド セーフであることが保証されています。 この機能は、*マジックスタティック*と呼ばれることもあります。 ただし、マルチスレッド アプリケーションでは、後続の割り当てはすべて同期する必要があります。 CRT に依存しないようにするには、 [/zc: threadSafeInit-](../build/reference/zc-threadsafeinit-thread-safe-local-static-initialization.md)フラグを使用して、スレッドセーフな静的初期化機能を無効にすることができます。

## <a name="extern"></a>不十分

**Extern**として宣言されたオブジェクトと変数は、別の翻訳単位または外側のスコープで定義されているオブジェクトを外部リンケージとして宣言します。 詳細については、「 [extern](extern-cpp.md)および[Translation の単位とリンケージ](program-and-linkage-cpp.md)」を参照してください。

## <a name="thread_local"></a>thread_local (C++ 11)

**Thread_local**指定子を使用して宣言された変数は、その変数が作成されたスレッドでのみアクセスできます。 変数は、スレッドが作成されるときに作成され、スレッドが破棄されるときに破棄されます。 各スレッドには、それ自体の変数のコピーがあります。 Windows では、 **thread_local**は Microsoft 固有の[__declspec (スレッド)](../cpp/thread.md)属性と機能的に等価です。

```cpp
thread_local float f = 42.0; // Global namespace. Not implicitly static.

struct S // cannot be applied to type definition
{
    thread_local int i; // Illegal. The member must be static.
    thread_local static char buf[10]; // OK
};

void DoSomething()
{
    // Apply thread_local to a local variable.
    // Implicitly "thread_local static S my_struct".
    thread_local S my_struct;
}
```

**Thread_local**指定子に関する注意事項:

- Dll 内の動的に初期化されたスレッドローカル変数は、すべての呼び出し元スレッドで正しく初期化されない場合があります。 詳細については、[スレッド](thread.md) に関するページを参照してください。

- **Thread_local**指定子は、 **static**または**extern**と組み合わせることができます。

- **Thread_local**は、データの宣言と定義にのみ適用できます。**thread_local**を関数の宣言または定義で使用することはできません。

- **Thread_local**は、静的ストレージ存続期間を持つデータ項目に対してのみ指定できます。 これには、グローバルなデータ オブジェクトが含まれます (どちらも**static**と**extern**)、ローカルな静的オブジェクト、およびクラスの静的データ メンバー。 **Thread_local**宣言されたローカル変数は、他のストレージクラスが指定されていない場合は暗黙的に静的になります。つまり、ブロックスコープ**thread_local**は `thread_local static`と同じです。

- 宣言と定義が同じファイルと個別のファイルのどちらで発生するかにかかわらず、スレッドローカルオブジェクトの宣言と定義の両方に**thread_local**を指定する必要があります。

Windows では、 **thread_local**は[__declspec (thread)](../cpp/thread.md)と機能的に等価ですが、 **__declspec (thread)** は型定義に適用でき、C コードでは有効である点が異なります。 可能な限り、 **thread_local**を使用します。これC++は標準の一部であるため、移植性が高くなります。

##  <a name="register"></a>  register

**Visual Studio 2017 バージョン15.3 以降**( [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)で利用可能): **register**キーワードはサポートされているストレージクラスではなくなりました。 キーワードは、将来使用するために標準で予約されています。

```cpp
   register int val; // warning C5033: 'register' is no longer a supported storage class
```

## <a name="example-automatic-vs-static-initialization"></a>例: 自動初期化と静的初期化

ローカル自動オブジェクトまたは変数が、制御フローが定義に到達するたびに初期化されます。 ローカル静的オブジェクトまたは変数が、最初に制御フローが定義に到達すると初期化されます。

オブジェクトの初期化と破棄をログに記録するクラスを定義し、`I1`、`I2`、および `I3` の 3 つのオブジェクトを定義する、次の例を考えます。

```cpp
// initialization_of_objects.cpp
// compile with: /EHsc
#include <iostream>
#include <string.h>
using namespace std;

// Define a class that logs initializations and destructions.
class InitDemo {
public:
    InitDemo( const char *szWhat );
    ~InitDemo();

private:
    char *szObjName;
    size_t sizeofObjName;
};

// Constructor for class InitDemo
InitDemo::InitDemo( const char *szWhat ) :
    szObjName(NULL), sizeofObjName(0) {
    if ( szWhat != 0 && strlen( szWhat ) > 0 ) {
        // Allocate storage for szObjName, then copy
        // initializer szWhat into szObjName, using
        // secured CRT functions.
        sizeofObjName = strlen( szWhat ) + 1;

        szObjName = new char[ sizeofObjName ];
        strcpy_s( szObjName, sizeofObjName, szWhat );

        cout << "Initializing: " << szObjName << "\n";
    }
    else {
        szObjName = 0;
    }
}

// Destructor for InitDemo
InitDemo::~InitDemo() {
    if( szObjName != 0 ) {
        cout << "Destroying: " << szObjName << "\n";
        delete szObjName;
    }
}

// Enter main function
int main() {
    InitDemo I1( "Auto I1" ); {
        cout << "In block.\n";
        InitDemo I2( "Auto I2" );
        static InitDemo I3( "Static I3" );
    }
    cout << "Exited block.\n";
}
```

```Output
Initializing: Auto I1
In block.
Initializing: Auto I2
Initializing: Static I3
Destroying: Auto I2
Exited block.
Destroying: Auto I1
Destroying: Static I3
```

この例では、オブジェクト `I1`、`I2`、および `I3` が初期化され、いつ破棄されるかを示します。

プログラムに関して注意すべき点がいくつかあります。

- 最初に、制御フローが `I1` と `I2` を定義しているブロックを終了すると、これらは自動的に破棄されます。

- 次に、C++ では、ブロックの先頭でオブジェクトや変数を宣言する必要はありません。 さらに、これらのオブジェクトは、制御フローが定義に到達した場合にのみ初期化されます (`I2` と `I3` は、このような定義の例です)。出力は、初期化された時点で正確に示されます。

- 最後に、`I3` などの静的ローカル変数は、プログラム実行中は値が保持されますが、プログラムが終了すると破棄されます。

## <a name="see-also"></a>関連項目

[宣言と定義](../cpp/declarations-and-definitions-cpp.md)