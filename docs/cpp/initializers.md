---
title: 初期化子
ms.date: 07/29/2019
description: でC++クラス、構造体、配列、および基本型を初期化する方法について説明します。
helpviewer_keywords:
- arrays [C++], array-element initializers
- aggregate initializers [C++]
ms.assetid: ce301ed8-aa1c-47b2-bb39-9f0541b4af85
ms.openlocfilehash: 2cc68f2384402ce1eb3ac06b414f597a6b3951f0
ms.sourcegitcommit: e93f3e6a110fe38bc642055bdf4785e620d4220f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/16/2020
ms.locfileid: "76123969"
---
# <a name="initializers"></a>初期化子

初期化子は変数の初期値を指定します。 変数は次のコンテキストで初期化できます。

- 変数の定義内:

    ```cpp
    int i = 3;
    Point p1{ 1, 2 };
    ```

- 関数のいずれかのパラメーターとして:

    ```cpp
    set_point(Point{ 5, 6 });
    ```

- 関数の戻り値として:

    ```cpp
    Point get_new_point(int x, int y) { return { x, y }; }
    Point get_new_point(int x, int y) { return Point{ x, y }; }
    ```

初期化子は次の形式で指定できます。

- 丸かっこ内の式 (または式のコンマ区切りのリスト)。

    ```cpp
    Point p1(1, 2);
    ```

- 等号とそれに続く式。

    ```cpp
    string s = "hello";
    ```

- 中かっこで囲まれた初期化子リスト。 次の例のように、リストは空でも、一連のリストで構成していてもかまいません。

    ```cpp
    struct Point{
        int x;
        int y;
    };
    class PointConsumer{
    public:
        void set_point(Point p){};
        void set_points(initializer_list<Point> my_list){};
    };
    int main() {
        PointConsumer pc{};
        pc.set_point({});
        pc.set_point({ 3, 4 });
        pc.set_points({ { 3, 4 }, { 5, 6 } });
    }
    ```

## <a name="kinds-of-initialization"></a>初期化の種類

初期化には複数の種類があり、それぞれプログラム実行中のさまざまなポイントで行うことができます。 異なる種類の初期化は相互に排他的ではありません。たとえば、リストの初期化は値の初期化をトリガーでき、また他の状況で集約の初期化をトリガーできます。

### <a name="zero-initialization"></a>ゼロ初期化

ゼロ初期化では、変数をゼロ値に設定して暗黙的に次の型に変換します。

- 数値変数は 0 (0.0 や 0.0000000000 など) に初期化されます。

- Char 変数は `'\0'`に初期化されます。

- ポインターは**nullptr**に初期化されます。

- 配列、[ポッド](../standard-library/is-pod-class.md)クラス、構造体、および共用体のメンバーは、ゼロ値に初期化されます。

ゼロ初期化は次のさまざまなタイミングで行われます。

- プログラムの起動時に、静的期間があるすべての名前付きの変数を対象に。 これらの変数は後で再初期化できます。

- 値の初期化中に、空のかっこを使用して初期化されるスカラー型と POD クラス 型を対象に。

- メンバーのサブセットのみが初期化された配列を対象に。

ゼロ初期化の例を次にいくつか示します。

```cpp
struct my_struct{
    int i;
    char c;
};

int i0;              // zero-initialized to 0
int main() {
    static float f1;  // zero-initialized to 0.000000000
    double d{};     // zero-initialized to 0.00000000000000000
    int* ptr{};     // initialized to nullptr
    char s_array[3]{'a', 'b'};  // the third char is initialized to '\0'
    int int_array[5] = { 8, 9, 10 };  // the fourth and fifth ints are initialized to 0
    my_struct a_struct{};   // i = 0, c = '\0'
}
```

### <a name="default_initialization"></a>既定の初期化

クラス、構造体、共用体の既定値初期化は、既定のコンストラクターによる初期化です。 既定のコンストラクターは、初期化式なしで、または**new**キーワードを使用して呼び出すことができます。

```cpp
MyClass mc1;
MyClass* mc3 = new MyClass;
```

クラス、構造体、または共用体に既定のコンストラクターがない場合、コンパイル時にエラーが発生します。

スカラー変数は、初期化式なしで定義されると、既定値に初期化され、 不確定な値が設定されます。

```cpp
int i1;
float f;
char c;
```

配列は、初期化式なしで定義されると、既定値に初期化されます。 次の例のように、配列が既定値に初期化されると、そのメンバーは既定値に初期化され、不確定な値が設定されます。

```cpp
int int_arr[3];
```

配列メンバーに既定のコンストラクターがない場合は、コンパイル時にエラーが発生します。

#### <a name="default-initialization-of-constant-variables"></a>定数変数の既定値初期化

定数変数は初期化子と共に宣言する必要があります。 それらの変数がスカラー型である場合はコンパイラ エラーが発生し、既定のコンストラクターがあるクラス型である場合は警告が出力されます。

```cpp
class MyClass{};
int main() {
    //const int i2;   // compiler error C2734: const object must be initialized if not extern
    //const char c2;  // same error
    const MyClass mc1; // compiler error C4269: 'const automatic data initialized with compiler generated default constructor produces unreliable results
}
```

#### <a name="default-initialization-of-static-variables"></a>静的変数の既定値初期化

初期化子を指定せずに宣言された静的変数は 0 に初期化 (暗黙に型変換) されます。

```cpp
class MyClass {
private:
    int m_int;
    char m_char;
};

int main() {
    static int int1;       // 0
    static char char1;     // '\0'
    static bool bool1;   // false
    static MyClass mc1;     // {0, '\0'}
}
```

グローバルな静的オブジェクトの初期化の詳細については、「 [main 関数とコマンドライン引数](main-function-command-line-args.md)」を参照してください。

### <a name="value-initialization"></a>値の初期化

値の初期化は次の場合に発生します。

- 名前付きの値が空の中かっこを使用して初期化される。

- 匿名の一時オブジェクトが空の丸かっこまたは中かっこを使用して初期化される。

- **new**キーワードと空のかっこまたは中かっこを使用してオブジェクトが初期化されます。

値の初期化では次の処理が実行されます。

- クラスに少なくとも 1 つのパブリック コンストラクターがある場合は、既定のコンストラクターが呼び出されます。

- 共用体以外のクラスでコンストラクターが宣言されていない場合、オブジェクトがゼロに初期化され、既定のコンストラクターが呼び出されます。

- 配列の場合、すべての要素の値が初期化されます。

- それ以外の場合は、変数がゼロに初期化されます。

```cpp
class BaseClass {
private:
    int m_int;
};

int main() {
    BaseClass bc{};     // class is initialized
    BaseClass*  bc2 = new BaseClass();  // class is initialized, m_int value is 0
    int int_arr[3]{};  // value of all members is 0
    int a{};     // value of a is 0
    double b{};  // value of b is 0.00000000000000000
}
```

### <a name="copy-initialization"></a>コピー初期化

コピー初期化とは、あるオブジェクトを別のオブジェクトを使用して初期化することです。 これは、次の場合に発生します。

- 変数が等号を使用して初期化される。

- 引数が関数に渡される。

- オブジェクトが関数から返される。

- 例外がスローまたはキャッチされる。

- 非静的データ メンバーが等号を使用して初期化される。

- クラス、構造体、共用体のメンバーが集約の初期化時にコピー初期化によって初期化される。 例については、「[集計の初期化](#agginit)」をご覧ください。

次のコードは、コピー初期化のいくつかの例を示しています。

```cpp
#include <iostream>
using namespace std;

class MyClass{
public:
    MyClass(int myInt) {}
    void set_int(int myInt) { m_int = myInt; }
    int get_int() const { return m_int; }
private:
    int m_int = 7; // copy initialization of m_int

};
class MyException : public exception{};
int main() {
    int i = 5;              // copy initialization of i
    MyClass mc1{ i };
    MyClass mc2 = mc1;      // copy initialization of mc2 from mc1
    MyClass mc1.set_int(i);    // copy initialization of parameter from i
    int i2 = mc2.get_int(); // copy initialization of i2 from return value of get_int()

    try{
        throw MyException();
    }
    catch (MyException ex){ // copy initialization of ex
        cout << ex.what();
    }
}
```

コピー初期化では明示的なコンストラクターを呼び出すことはできません。

```cpp
vector<int> v = 10; // the constructor is explicit; compiler error C2440: cannot convert from 'int' to 'std::vector<int,std::allocator<_Ty>>'
regex r = "a.*b"; // the constructor is explicit; same error
shared_ptr<int> sp = new int(1729); // the constructor is explicit; same error
```

場合によっては、クラスのコピー コンストラクターが削除されるかアクセスできないと、コピー初期化によりコンパイラ エラーが発生します。

### <a name="direct-initialization"></a>直接の初期化

直接の初期化とは、(空でない) 中かっこまたは丸かっこを使用した初期化です。 コピー初期化とは異なり、明示的なコンストラクターを呼び出すことができます。 これは、次の場合に発生します。

- 変数が空でない中かっこまたは丸かっこを使用して初期化される。

- **new**キーワードと空でない中かっこまたはかっこを使用して変数が初期化されています

- 変数が**static_cast**で初期化されています

- コンストラクターで、基底クラスと非静的メンバーが初期化子リストを使用して初期化される。

- ラムダ式のキャプチャされた変数のコピーで。

次のコードは、直接の初期化のいくつかの例を示しています。

```cpp
class BaseClass{
public:
    BaseClass(int n) :m_int(n){} // m_int is direct initialized
private:
    int m_int;
};

class DerivedClass : public BaseClass{
public:
    // BaseClass and m_char are direct initialized
    DerivedClass(int n, char c) : BaseClass(n), m_char(c) {}
private:
    char m_char;
};
int main(){
    BaseClass bc1(5);
    DerivedClass dc1{ 1, 'c' };
    BaseClass* bc2 = new BaseClass(7);
    BaseClass bc3 = static_cast<BaseClass>(dc1);

    int a = 1;
    function<int()> func = [a](){  return a + 1; }; // a is direct initialized
    int n = func();
}
```

### <a name="list-initialization"></a>リストの初期化

リストの初期化が行われるのは、変数が中かっこで囲まれた初期化子リストを使用して初期化されるときです。 中かっこで囲まれたリストは次の場合に使用できます。

- 変数が初期化される。

- クラスは、 **new**キーワードを使用して初期化されます。

- オブジェクトが関数から返される。

- 引数が関数に渡される。

- 直接の初期化の引数の 1 つに対して。

- 非静的データ メンバーの初期化子内で。

- コンストラクターの初期化子リスト内で。

次のコードは、リストの初期化のいくつかの例を示しています。

```cpp
class MyClass {
public:
    MyClass(int myInt, char myChar) {}
private:
    int m_int[]{ 3 };
    char m_char;
};
class MyClassConsumer{
public:
    void set_class(MyClass c) {}
    MyClass get_class() { return MyClass{ 0, '\0' }; }
};
struct MyStruct{
    int my_int;
    char my_char;
    MyClass my_class;
};
int main() {
    MyClass mc1{ 1, 'a' };
    MyClass* mc2 = new MyClass{ 2, 'b' };
    MyClass mc3 = { 3, 'c' };

    MyClassConsumer mcc;
    mcc.set_class(MyClass{ 3, 'c' });
    mcc.set_class({ 4, 'd' });

    MyStruct ms1{ 1, 'a', { 2, 'b' } };
}
```

### <a name="agginit"></a>集計の初期化

集約の初期化は、リストの初期化の一形態であり、次のような配列またはクラス型 (多くの場合は構造体や共用体) に使用されます。

- プライベートまたはプロテクト メンバーでない。

- 明示的に既定化または削除したコンストラクターを除いて、ユーザー定義のコンストラクターがない。

- 基底クラスを持たない。

- 仮想メンバー関数がない。

> [!NOTE]
> <!--conformance note-->Visual Studio 2015 以前では、非静的メンバーに対して、中かっこまたは等号の初期化子を集計に使用することはできません。 この制限は、C++ 14 標準では削除されており、Visual Studio 2017 で実装されています。

次の例のように、集約の初期化子は、中かっこで囲まれた初期化子リストで構成しています。等号は使用してもしなくてもかまいません。

```cpp
#include <iostream>
using namespace std;

struct MyAggregate{
    int myInt;
    char myChar;
};

struct MyAggregate2{
    int myInt;
    char myChar = 'Z'; // member-initializer OK in C++14
};

int main() {
    MyAggregate agg1{ 1, 'c' };
    MyAggregate2 agg2{2};
    cout << "agg1: " << agg1.myChar << ": " << agg1.myInt << endl;
    cout << "agg2: " << agg2.myChar << ": " << agg2.myInt << endl;

    int myArr1[]{ 1, 2, 3, 4 };
    int myArr2[3] = { 5, 6, 7 };
    int myArr3[5] = { 8, 9, 10 };

    cout << "myArr1: ";
    for (int i : myArr1){
        cout << i << " ";
    }
    cout << endl;

    cout << "myArr3: ";
    for (auto const &i : myArr3) {
        cout << i << " ";
    }
    cout << endl;
}
```

以下の出力が表示されます。

```Output
agg1: c: 1
agg2: Z: 2
myArr1: 1 2 3 4
myArr3: 8 9 10 0 0
```

> [!IMPORTANT]
> 前の `myArr3` のように、宣言されているが、集計初期化中に明示的に初期化されていない配列メンバーはゼロ初期化されます。

#### <a name="initializing-unions-and-structs"></a>共用体と構造体の初期化

共用体にコンストラクターがない場合は、単一の値を使用して (または共用体の別のインスタンスを使用して) 共用体を初期化できます。 値は最初の非静的フィールドの初期化に使用されます。 この点は構造体の初期化と異なります。構造体の初期化では、初期化子の最初の値を使用して最初のフィールドを初期化し、2 番目の値を使用して 2 番目のフィールドを初期化するというように続きます。 次の例では、共用体と構造体の初期化を比較しています。

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
union MyUnion {
    int my_int;
    char my_char;
    bool my_bool;
    MyStruct my_struct;
};

int main() {
    MyUnion mu1{ 'a' };  // my_int = 97, my_char = 'a', my_bool = true, {myInt = 97, myChar = '\0'}
    MyUnion mu2{ 1 };   // my_int = 1, my_char = 'x1', my_bool = true, {myInt = 1, myChar = '\0'}
    MyUnion mu3{};      // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    MyUnion mu4 = mu3;  // my_int = 0, my_char = '\0', my_bool = false, {myInt = 0, myChar = '\0'}
    //MyUnion mu5{ 1, 'a', true };  // compiler error: C2078: too many initializers
    //MyUnion mu6 = 'a';            // compiler error: C2440: cannot convert from 'char' to 'MyUnion'
    //MyUnion mu7 = 1;              // compiler error: C2440: cannot convert from 'int' to 'MyUnion'

    MyStruct ms1{ 'a' };            // myInt = 97, myChar = '\0'
    MyStruct ms2{ 1 };              // myInt = 1, myChar = '\0'
    MyStruct ms3{};                 // myInt = 0, myChar = '\0'
    MyStruct ms4{1, 'a'};           // myInt = 1, myChar = 'a'
    MyStruct ms5 = { 2, 'b' };      // myInt = 2, myChar = 'b'
}
```

#### <a name="initializing-aggregates-that-contain-aggregates"></a>他の集約を格納する集約の初期化

集約型には、配列の配列や構造体の配列など、他の集約型が含まれる場合があります。 これらの集約型は、入れ子になった一連の中かっこを使用して初期化されます。たとえば、次のとおりです。

```cpp
struct MyStruct {
    int myInt;
    char myChar;
};
int main() {
    int intArr1[2][2]{{ 1, 2 }, { 3, 4 }};
    int intArr3[2][2] = {1, 2, 3, 4};
    MyStruct structArr[]{ { 1, 'a' }, { 2, 'b' }, {3, 'c'} };
}
```

### <a name="reference-initialization"></a>参照の初期化

参照型の変数は、参照型の派生元のオブジェクト型、または参照型の派生元の型に変換できるオブジェクト型により初期化する必要があります。 例:

```cpp
// initializing_references.cpp
int iVar;
long lVar;
int main()
{
    long& LongRef1 = lVar;        // No conversion required.
    long& LongRef2 = iVar;        // Error C2440
    const long& LongRef3 = iVar;  // OK
    LongRef1 = 23L;               // Change lVar through a reference.
    LongRef2 = 11L;               // Change iVar through a reference.
    LongRef3 = 11L;               // Error C3892
}
```

一時オブジェクトにより参照を初期化する唯一の方法は、定数一時オブジェクトを初期化することです。 reference-type 変数は、初期化後に常に同じオブジェクトを参照します。別のオブジェクトを参照するための変更はできません。

reference-type 変数の初期化と reference-type 変数の代入は、構文は同じであっても意味は異なります。 前の例では、`iVar` と `lVar` を変更する代入は初期化に似ていますが、その効果は異なります。 初期化は、reference-type 変数が参照するオブジェクトを指定します。この代入では、参照を通じて referred-to オブジェクトが割り当てられます。

参照型の引数を関数に渡すこと、および関数から参照型の値を返すことは初期化であるために、関数に対する仮引数は、参照が返される場合と同様に正しく初期化されます。

Reference-type 変数は、以下の場合にのみ初期化子なしで宣言できます。

- 関数宣言 (プロトタイプ)。 例:

    ```cpp
    int func( int& );
    ```

- Function-return 型宣言。 例:

    ```cpp
    int& func( int& );
    ```

- reference-type クラス メンバーの宣言。 例:

    ```cpp
    class c {public:   int& i;};
    ```

- **Extern**として明示的に指定された変数の宣言。 例:

    ```cpp
    extern int& iVal;
    ```

reference-type 変数を初期化する場合、コンパイラではオブジェクトに対する参照の作成、または参照先の一時オブジェクトの作成のいずれかを選択するために、次の図に示す判定グラフを使用します。

![参照型の初期化のためのデシジョングラフ](../cpp/media/vc38s71.gif "参照型の初期化のためのデシジョングラフ") <br/>
参照型の初期化のためのデシジョングラフ

Volatile 型 ( **volatile** *typename* <strong>&</strong> *identifier* **) への**参照は、同じ型の**volatile**オブジェクト、または**volatile**として宣言されていないオブジェクトを使用して初期化できます。 ただし、その型の**const**オブジェクトを使用して初期化することはできません。 同様に、const**型への**参照 ( **const** *typename* <strong>&</strong> *identifier*として宣言) は、同じ型の**const**オブジェクト (または、その型への変換または**const**として宣言されていないオブジェクトによる変換を含むすべてのオブジェクト) を使用して初期化できます。 ただし、その型の**volatile**オブジェクトを使用して初期化することはできません。

**Const**または**volatile**キーワードで修飾されていない参照は、 **const**および**volatile**として宣言されたオブジェクトでのみ初期化できます。

### <a name="initialization-of-external-variables"></a>外部変数の初期化

自動変数、静的変数、外部変数の宣言には初期化子を含めることができます。 ただし、外部変数の宣言には、変数が**extern**として宣言されていない場合にのみ、初期化子を含めることができます。
