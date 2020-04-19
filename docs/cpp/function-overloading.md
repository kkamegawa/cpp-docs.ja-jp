---
title: 関数のオーバーロード
ms.date: 03/27/2019
helpviewer_keywords:
- function overloading [C++], about function overloading
- function overloading
- declaring functions [C++], overloading
ms.assetid: 3c9884cb-1d5e-42e8-9a49-6f46141f929e
ms.openlocfilehash: 6cc432e404a7a66de63cf87f0fe87f0ccdcb5d70
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154276"
---
# <a name="function-overloading"></a>関数のオーバーロード

C++ では、同じスコープ内で同じ名前の複数の関数を指定できます。 これらの関数を呼び出す*オーバー ロードされた*関数。 オーバー ロードされた関数では、関数の型と引数の数に応じて、異なるセマンティクスを指定できます。

たとえば、`print`を受け取る関数、`std::string`引数実行する型の引数を受け取る 1 よりも非常にさまざまなタスクが**double**。 によりなどの名前を使用する必要がなくなりますオーバー ロード`print_string`または`print_double`します。 コンパイル時に、コンパイラは、呼び出し元によって渡される引数の型に基づいてどのオーバー ロードを使用するを選択します。  呼び出す場合`print(42.0)`、`void print(double d)`関数が呼び出されます。 呼び出す場合`print("hello world")`、`void print(std::string)`オーバー ロードが呼び出されます。

メンバー関数と非メンバー関数の両方をオーバー ロードすることができます。 次の表は、同じスコープ内の同じ名前を持つ関数を区別するために、C++ で関数宣言のどの部分が使用されるかをまとめたものです。

### <a name="overloading-considerations"></a>オーバーロードに関する考慮事項

|関数宣言要素|オーバーロードに使用されるかどうか|
|----------------------------------|---------------------------|
|関数の戻り値の型|いいえ|
|引数の数|[はい]|
|引数の型|[はい]|
|省略記号の有無|[はい]|
|使用**typedef**名|いいえ|
|未指定の配列の範囲|いいえ|
|**const**または**volatile**|[はい]、関数全体に適用する場合|
|[Ref 修飾子](#ref-qualifiers)|[はい]|

## <a name="example"></a>例

次の例は、どのようにオーバーロードが使用できるかを示しています。

```cpp
// function_overloading.cpp
// compile with: /EHsc
#include <iostream>
#include <math.h>
#include <string>

// Prototype three print functions.
int print(std::string s);             // Print a string.
int print(double dvalue);            // Print a double.
int print(double dvalue, int prec);  // Print a double with a
                                     //  given precision.
using namespace std;
int main(int argc, char *argv[])
{
    const double d = 893094.2987;
    if (argc < 2)
    {
        // These calls to print invoke print( char *s ).
        print("This program requires one argument.");
        print("The argument specifies the number of");
        print("digits precision for the second number");
        print("printed.");
        exit(0);
    }

    // Invoke print( double dvalue ).
    print(d);

    // Invoke print( double dvalue, int prec ).
    print(d, atoi(argv[1]));
}

// Print a string.
int print(string s)
{
    cout << s << endl;
    return cout.good();
}

// Print a double in default precision.
int print(double dvalue)
{
    cout << dvalue << endl;
    return cout.good();
}

//  Print a double in specified precision.
//  Positive numbers for precision indicate how many digits
//  precision after the decimal point to show. Negative
//  numbers for precision indicate where to round the number
//  to the left of the decimal point.
int print(double dvalue, int prec)
{
    // Use table-lookup for rounding/truncation.
    static const double rgPow10[] = {
        10E-7, 10E-6, 10E-5, 10E-4, 10E-3, 10E-2, 10E-1,
        10E0, 10E1,  10E2,  10E3,  10E4, 10E5,  10E6 };
    const int iPowZero = 6;

    // If precision out of range, just print the number.
    if (prec < -6 || prec > 7)
    {
        return print(dvalue);
    }
    // Scale, truncate, then rescale.
    dvalue = floor(dvalue / rgPow10[iPowZero - prec]) *
        rgPow10[iPowZero - prec];
    cout << dvalue << endl;
    return cout.good();
}
```

上記のコードは、ファイル スコープでの `print` 関数のオーバーロードを示しています。

既定の引数はされていない、関数型の一部と見なされます。 そのため、オーバー ロードされた関数を選択するときは使用されません。 既定の引数のみが異なる 2 つの関数は、オーバーロードされた関数ではなく複数の定義と見なされます。

オーバー ロードされた演算子は、既定の引数を指定することはできません。

## <a name="argument-matching"></a>引数の一致

オーバーロード関数は、関数呼び出しで指定された引数に最も合った現在のスコープ内の関数宣言に対して選択します。 適切な関数がある場合、その関数が呼び出されます。 このコンテキストでは「適切」いずれかを意味します。

- 厳密な一致が見つかりませんでした。

- 単純変換が実行されました。

- 整数の上位変換が実行されました。

- 目的の引数の型への標準変換が存在します。

- 目的の引数の型へのユーザー定義の変換 (変換演算子またはコンストラクター) が存在します。

- 省略記号によって表される引数が見つかりませんでした。

コンパイラは、引数ごとに候補関数のセットを作成します。 候補関数は、その位置の実引数を仮引数の型に変換できる関数です。

一連の "最も一致する関数" は各引数にビルドされ、選択した関数はすべての設定の交差部分です。 交差部分に複数の関数が含まれている場合、オーバーロードはあいまいで、エラーが生成されます。 最終的に選択された関数は、少なくとも 1 つの引数についてはグループ内のどの関数よりも優れた一致です。 明確な勝者がない場合は、関数呼び出しはエラーを生成します。

次の宣言を考えます (関数には、以下の説明での識別のために `Variant 1`、`Variant 2`、および `Variant 3` とマーク付けしています)。

```cpp
Fraction &Add( Fraction &f, long l );       // Variant 1
Fraction &Add( long l, Fraction &f );       // Variant 2
Fraction &Add( Fraction &f, Fraction &f );  // Variant 3

Fraction F1, F2;
```

次のステートメントを考えます。

```cpp
F1 = Add( F2, 23 );
```

前のステートメントは 2 つのセットをビルドします。

|セット 1:Fraction 型の最初の引数を持つ候補関数|セット 2:候補関数を 2 番目の引数に変換できる型**int**|
|--------------------------------------------------------------------------|-----------------------------------------------------------------------------------|
|バリアント 1|バリアント 1 (**int**に変換できる**long**標準変換を使用して)|
|バリアント 3||

関数は実際のパラメーターの型から仮パラメーターの型に暗黙的に変換し、このような関数の間では、実際のパラメーターの型をその仮パラメーターの型に変換する「コスト」の関数はセット 2 の関数では、最小値。

これら 2 つのセットの積集合は、バリアント 1 です。 あいまいな関数呼び出しの例は次のとおりです。

```cpp
F1 = Add( 3, 6 );
```

前の関数呼び出しは次のセットをビルドします。

|セット 1:候補の関数型を持つ最初の引数の**int**|セット 2:候補の関数型を持つ 2 つ目の引数の**int**|
|---------------------------------------------------------------------|----------------------------------------------------------------------|
|バリアント 2 (**int**に変換できる**long**標準変換を使用して)|バリアント 1 (**int**に変換できる**long**標準変換を使用して)|

これら 2 つのセットの積集合が空なので、コンパイラはエラー メッセージを生成します。

引数の一致を持つ関数*n*既定の引数として扱われます*n*+1 の個別の関数、それぞれに異なる数の引数。

省略記号 (...) はワイルドカードとして機能します。これは任意の実際の引数と一致します。 これは細心の注意と、オーバー ロードされた関数のセットをデザインしない場合は、多くのあいまいなセットにつながります。

> [!NOTE]
>  関数呼び出しが検出されるまで、オーバー ロードされた関数のあいまいさを判断できません。 その時点で、設定は関数呼び出しの引数ごとに構築され、明確なオーバーロードがあるかどうかを確認できます。 これは、それらが特定の関数呼び出しによって呼び出されるまで、コードにあいまいさが残ることを意味しています。

## <a name="argument-type-differences"></a>引数の型の違い

オーバーロード関数では、異なる初期化子を受け取る引数型が区別されます。 したがって、指定された型の引数とその型への参照は、オーバーロードの目的では同一であると見なされます。 これらが同一であると見なされるのは、同じ初期化子を受け取るためです。 たとえば、`max( double, double )` は `max( double &, double & )` と同じであると見なされます。 このような関数を 2 つ宣言すると、エラーが発生します。

同じ理由で、関数の引数によって修飾された型の**const**または**volatile**オーバー ロードの目的では、基本データ型とは異なる扱われません。

ただし、関数のオーバーロード メカニズムを区別できるで修飾される参照**const**と**volatile**および基本データ型への参照。 次の指定可能なコードになります。

```cpp
// argument_type_differences.cpp
// compile with: /EHsc /W3
// C4521 expected
#include <iostream>

using namespace std;
class Over {
public:
   Over() { cout << "Over default constructor\n"; }
   Over( Over &o ) { cout << "Over&\n"; }
   Over( const Over &co ) { cout << "const Over&\n"; }
   Over( volatile Over &vo ) { cout << "volatile Over&\n"; }
};

int main() {
   Over o1;            // Calls default constructor.
   Over o2( o1 );      // Calls Over( Over& ).
   const Over o3;      // Calls default constructor.
   Over o4( o3 );      // Calls Over( const Over& ).
   volatile Over o5;   // Calls default constructor.
   Over o6( o5 );      // Calls Over( volatile Over& ).
}
```

### <a name="output"></a>Output

```Output
Over default constructor
Over&
Over default constructor
const Over&
Over default constructor
volatile Over&
```

ポインター **const**と**volatile**オブジェクトも対象と基本型をポインターとは異なるオーバーロードの目的で。

## <a name="argument-matching-and-conversions"></a>引数の一致と変換

コンパイラは、関数宣言の引数と実際の引数を照合するとき、厳密な一致が見つからない場合は、正しい型を取得するために標準またはユーザー定義の変換を指定できます。 変換は、次の規則に従って行われます。

- 複数のユーザー定義変換を含む変換のシーケンスは考慮されません。

- 中間変換を削除することによって簡略化できる変換のシーケンスは考慮されません。

変換の結果のシーケンスが存在する場合、それは最適な一致シーケンスと呼ばれます。 型のオブジェクトに変換するいくつかの方法がある**int**入力**unsigned long**標準変換を使用して (で説明されている[標準変換](../cpp/standard-conversions.md))。

- 変換**int**に**long**し**long**に**unsigned long**します。

- 変換**int**に**unsigned long**します。

最初のシーケンスが、目的が達成に役立つは最適な一致シーケンスはありません — 短いシーケンスが存在します。

次の表は、どのシーケンスが最適な一致かの判断に一定の効果を持つ、単純変換と呼ばれる変換を示しています。 単純変換がシーケンスの選択に影響を与える例については、表の後で説明します。

### <a name="trivial-conversions"></a>単純変換

|変換前の型|変換後の型|
|-----------------------|---------------------|
|*type-name*|*type-name* **&**|
|*type-name* **&**|*type-name*|
|*type-name* **[ ]**|*type-name* __\*__|
|*type-name* **(** *argument-list* **)**|**(** __\*__ *type-name* **) (** *argument-list* **)**|
|*type-name*|**const** *type-name*|
|*type-name*|**volatile** *type-name*|
|*type-name* __\*__|**const** *type-name* __\*__|
|*type-name* __\*__|**volatile** *type-name* __\*__|

変換が試行されたシーケンスは次のとおりです。

1. 完全一致。 関数の呼び出しに使用された型と関数プロトタイプで宣言された型の完全な一致は、常に最適な一致です。 単純変換のシーケンスは、完全一致として分類されます。 ただし、これらの変換のいずれかを行わないシーケンスがシーケンスに変換するよりも優れていますと判断されます。

   - ポインターへのポインターから**const** (`type` <strong>\*</strong>に**const** `type` <strong>\*</strong>).

   - ポインターへのポインターから**volatile**(`type` <strong>\*</strong>に**volatile** `type` <strong>\*</strong>).

   - 参照への参照から**const** (`type` **&** に**const** `type` **&** ).

   - 参照への参照から**volatile**(`type` **&** に**volatile** `type` **&**).

1. 上位変換を使用した一致。 のみ整数の上位変換からの変換を含む完全一致として分類されないシーケンス**float**に**double**、および単純変換が上位変換を使用する一致として分類されます。 完全一致による一致ほどではありませんが、標準変換を使用するより上位変換を使用する方が一致の程度が高くなります。

1. 標準変換を使用した一致。 完全一致としても、標準変換および単純変換だけを含む上位変換を使用した一致としても分類されないシーケンスは、標準変換を使用した一致として分類されます。 このカテゴリ内では、次の規則が適用されます。

   - ポインターから直接または間接基底クラスへのポインターへの派生クラスへの変換が変換することをお勧め`void *`または`const void *`します。

   - 派生クラスへのポインターから基底クラスへのポインターに変換すると、基底クラスが直接基底クラスに近ければ近いほど、一致の程度が向上します。 次の図に示すクラスの階層構造を考えます。

![優先される変換のグラフ](../cpp/media/vc391t1.gif "優先される変換のグラフ") <br/>
優先される変換を示すグラフ

`D*` 型から `C*` 型への変換は、`D*` 型から `B*` 型への変換よりも適しています。 同様に、`D*` 型から `B*` 型への変換は、`D*` 型から `A*` 型への変換よりも適しています。

この同じ規則が、参照変換に適用されます。 `D&` 型から `C&` 型への変換は、`D&` 型から `B&` 型への変換などよりも適しています。

この同じ規則は、ポインターからメンバーへの変換にも適用されます。 `T D::*` 型から `T C::*` 型への変換は、`T D::*` 型から `T B::*` 型への変換などよりも適しています (`T` はメンバーの型)。

上記の規則は、派生の特定のパスに沿ってのみ適用されます。 次の図に示すグラフについて考えます。

![複数&#45;優先される変換を示しています継承](../cpp/media/vc391t2.gif "複数&#45;優先される変換を示しています。 継承。") <br/>
優先される変換を示す複数継承グラフ

`C*` 型から `B*` 型への変換は、`C*` 型から `A*` 型への変換よりも適しています。 理由は、これらが同じパスにあり、`B*` の方が近いからです。 ただし、型から変換`C*`入力`D*`型への変換に適していない`A*`;、変換は違うパスをたどるために、基本設定はありません。

1. ユーザー定義変換を使用した一致。 このシーケンスは、完全に一致する、プロモーションを使用する一致または標準変換を使用した一致として分類されることはできません。 このシーケンスには、ユーザー定義の変換、標準変換、またはユーザー定義の変換を使用した一致として分類される単純変換だけが含まれます。 ユーザー定義の変換による一致は、省略記号を含む一致より程度の高い一致と見なされますが、標準変換による一致ほど程度の高い一致とは見なされません。

1. 省略記号を使用した一致。 宣言内の省略記号に一致するシーケンスは、すべて省略記号による一致として分類されます。 これは、最も弱い一致と見なされます。

組み込みの上位変換または変換が存在しない場合、ユーザー定義の変換が適用されます。 これらの変換は照合する引数の型に基づいて選択されます。 次のコードがあるとします。

```cpp
// argument_matching1.cpp
class UDC
{
public:
   operator int()
   {
      return 0;
   }
   operator long();
};

void Print( int i )
{
};

UDC udc;

int main()
{
   Print( udc );
}
```

クラスの使用可能なユーザー定義の変換`UDC`型からは**int**と種類**long**します。 したがって、コンパイラは照合対象のオブジェクトの型、`UDC` に応じて変換を検討します。 変換**int**が存在するが選択されているとします。

引数の照合処理中は、引数とユーザー定義変換の結果の両方に標準変換を適用できます。 したがって、次のコードは機能します。

```cpp
void LogToFile( long l );
...
UDC udc;
LogToFile( udc );
```

前の例では、ユーザー定義の変換、**演算子 long**、変換するために呼び出す`udc`入力**long**。 場合を入力するユーザー定義変換なし**long**だった定義されている場合、変換はように処理します。型`UDC`型に変換された**int**ユーザー定義の変換を使用します。 標準型から変換し、 **int**入力**long**宣言で引数の一致するように適用されるは。

引数の一致には、すべてのユーザー定義変換が必要な標準の変換は最適な一致を評価するときに使用されません。 1 つ以上の候補関数は、ユーザー定義の変換を必要とする場合でも、関数は等しいと見なされます。 例:

```cpp
// argument_matching2.cpp
// C2668 expected
class UDC1
{
public:
   UDC1( int );  // User-defined conversion from int.
};

class UDC2
{
public:
   UDC2( long ); // User-defined conversion from long.
};

void Func( UDC1 );
void Func( UDC2 );

int main()
{
   Func( 1 );
}
```

両方のバージョンの`Func`型に変換するユーザー定義の変換を必要と**int**クラス型の引数にします。 発生しうる変換は、次のとおりです。

- 型から変換する**int**入力`UDC1`(ユーザー定義変換)。

- 型から変換する**int**入力**long**; 型に変換し、 `UDC2` (2 段階の変換)。

2 つ目は、標準変換とユーザー定義の変換の両方を必要とする場合でも、2 つの変換と等しい見なされます。

> [!NOTE]
>  ユーザー定義の変換は、コンストラクションによる変換または初期化による変換 (変換関数) と見なされます。 どちらの方法も、最適一致を検討する際には等しいと判断されます。

## <a name="argument-matching-and-the-this-pointer"></a>引数一致と this ポインター

クラス メンバー関数として宣言されているかどうかに応じて異なる方法で扱われる**static**します。 非静的関数がある暗黙的な引数を提供するため、**this**ポインター、非静的関数を静的関数よりも 1 つ以上の引数を持つと見なされます。 それ以外の場合、宣言されている同じです。

これらの非静的メンバー関数が必要とする暗黙**this**またはポインターが使用される、関数が呼び出される、オブジェクトの種類と一致すると、オーバー ロードされた演算子は、必要な最初の引数が対象となるオブジェクトと一致する、演算子が適用されます。 (オーバー ロードされた演算子の詳細については、次を参照してください[オーバー ロードされた演算子](../cpp/operator-overloading.md)。)。

その他のオーバー ロードされた関数の引数とは異なり一時オブジェクトが追加されていないと、一致させる場合に変換も行われません、**this**ポインター引数。

ときに、`->`メンバー選択演算子はクラスのメンバー関数へのアクセスに使用される`class_name`、**this**ポインター引数の型を持つ`class_name * const`します。 として、メンバーが宣言されている場合**const**または**volatile**、種類は、`const class_name * const`と`volatile class_name * const`、それぞれします。

`.` メンバー選択演算子は、暗黙の `&` (アドレス) 演算子がオブジェクト名の前に付けられている場合を除き、まったく同じ方法で動作します 次の例では、このしくみを説明します。

```cpp
// Expression encountered in code
obj.name

// How the compiler treats it
(&obj)->name
```

引数マッチングに関して、`->*` 演算子および `.*` (メンバーへのポインター) 演算子の左オペランドは `.` 演算子および `->` (メンバー選択) 演算子と同じ方法で処理されます。

## <a name="ref-qualifiers"></a> メンバー関数に対する ref 修飾子

Ref 修飾子できるようになりますが、オブジェクトの指すかどうかに基づいて、メンバー関数をオーバー ロード**this**は右辺値または左辺値です。  この機能は、データへのポインターを提供していないを選択するシナリオでの不要なコピー操作を回避するために使用できます。 たとえば、クラス`C`、コンス トラクター内のデータを初期化し、メンバー関数でそのデータのコピーを返します`get_data()`します。 型のオブジェクトの場合`C`右辺値を破棄しようとしていますが、コンパイラは選択するには、`get_data() &&`それをコピーするのではなく、オーバー ロード、データを移動します。

```cpp
#include <iostream>
#include <vector>

using namespace std;

class C
{

public:
    C() {/*expensive initialization*/}
    vector<unsigned> get_data() &
    {
        cout << "lvalue\n";
        return _data;
    }
    vector<unsigned> get_data() &&
    {
        cout << "rvalue\n";
        return std::move(_data);
    }

private:
    vector<unsigned> _data;
};

int main()
{
    C c;
    auto v = c.get_data(); // get a copy. prints "lvalue".
    auto v2 = C().get_data(); // get the original. prints "rvalue"
    return 0;
}
```

## <a name="restrictions-on-overloading"></a>オーバー ロードに関する制限

許容可能なオーバーロード関数のセットには複数の制限が適用されます。

- 一連のオーバーロードされた関数の 2 つの関数には、異なる引数リストが必要です。

- オーバーロードは、戻り値の型だけに基づいて同じ型の引数リストと共に機能するエラーです。

     **Microsoft 固有の仕様**

オーバー ロードできます**new 演算子**だけで、に基づいて戻り値の型: 指定したメモリ モデル修飾子に基づいて具体的には、します。

**Microsoft 固有の仕様はここまで**

- メンバー関数は、静的で、その他の静的ではない他方に基づいてのみオーバー ロードできません。

- **typedef**宣言は、新しい型を定義しないでください。 既存の型のシノニムを導入します。 オーバー ロード メカニズムには影響しません。 次のコードがあるとします。

    ```cpp
    typedef char * PSTR;

    void Print( char *szToPrint );
    void Print( PSTR szToPrint );
    ```

   先行する 2 つの関数の引数リストはまったく同じです。 `PSTR` 型のシノニムです`char *`します。 メンバーのスコープでは、このコードによりエラーが発生します。

- 列挙型は別個の型です。また、オーバーロードされた関数を識別するために使用できます。

- 型"array"と"pointer to"が単独配列の次元がオーバー ロードされた関数は、間のみを識別する目的で同じと見なされます。 その理由はこれらのオーバー ロードされた関数が競合してエラー メッセージを生成します。

    ```cpp
    void Print( char *szToPrint );
    void Print( char szToPrint[] );
    ```

   次元配列の乗算では、2 番目以降のすべてのディメンションは、型の一部と見なされます。 したがって、オーバーロードされた関数を識別するために使用されます。

    ```cpp
    void Print( char szToPrint[] );
    void Print( char szToPrint[][7] );
    void Print( char szToPrint[][9][42] );
    ```

## <a name="overloading-overriding-and-hiding"></a>オーバー ロード、オーバーライド、および非表示

同じスコープ内で同じ名前の 2 つの関数宣言は、同じ関数またはオーバーロードされる 2 種類の関数を参照できます。 宣言の引数リストに (前のセクションで説明したように) 型が同じ引数が含まれている場合、関数宣言は同じ関数を参照しています。 それ以外の場合は、オーバーロードを使用して選択された 2 つの異なる関数を参照します。

クラス スコープが厳密に遵守されます。基底クラスで宣言された関数が関数と同じスコープにないため、派生クラスで宣言します。 派生クラスの関数が基底クラスの派生クラスの関数の仮想関数と同じ名前で宣言されている*オーバーライド*基底クラス関数。 詳細については、次を参照してください。[仮想関数](../cpp/virtual-functions.md)します。

基底クラス関数は、'virtual' で宣言されていないかどうかは、派生クラスの関数といいます*を非表示に*こと。 オーバーライドして非表示の両方がオーバー ロードとは異なります。

ブロック スコープは、厳密に遵守されます。したがって、ファイル スコープで宣言された関数は、関数と同じスコープでされていません。 ローカルに宣言します。 ローカルで宣言された関数の名前がファイル スコープで宣言された関数と同じ場合、ローカルで宣言された関数では、オーバーロードが発生する代わりに、ファイル スコープ関数を非表示にします。 例:

```cpp
// declaration_matching1.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
void func( int i )
{
    cout << "Called file-scoped func : " << i << endl;
}

void func( char *sz )
{
   cout << "Called locally declared func : " << sz << endl;
}

int main()
{
   // Declare func local to main.
   extern void func( char *sz );

   func( 3 );   // C2664 Error. func( int ) is hidden.
   func( "s" );
}
```

前のコードは、関数 `func` からの 2 つの定義を示します。 型の引数を受け取る定義`char *`ローカル`main`のため、 **extern**ステートメント。 型の引数を受け取る定義ではそのため、 **int**が非表示と最初の呼び出し`func`エラーが発生します。

オーバーロードされたメンバー関数の場合は、関数の各バージョンにそれぞれ異なるアクセス権限を与えることができます。 これらは、依然として外側のクラスのスコープ内にあると見なされます。このため、オーバーロードされた関数です。 `Deposit` メンバー関数をオーバーロードしている次のコードを考えます。1 つのバージョンはパブリック、もう 1 つのバージョンはプライベートです。

このサンプルの目的は、預金を実行するために正しいパスワードが必要となる `Account` クラスを提供することです。 これは、オーバー ロードを使用して行われます。

呼び出し`Deposit`で`Account::Deposit`プライベート メンバー関数を呼び出します。 この呼び出しが正しいため`Account::Deposit`メンバー関数は、クラスのプライベート メンバーにアクセスします。

```cpp
// declaration_matching2.cpp
class Account
{
public:
   Account()
   {
   }
   double Deposit( double dAmount, char *szPassword );

private:
   double Deposit( double dAmount )
   {
      return 0.0;
   }
   int Validate( char *szPassword )
   {
      return 0;
   }

};

int main()
{
    // Allocate a new object of type Account.
    Account *pAcct = new Account;

    // Deposit $57.22. Error: calls a private function.
    // pAcct->Deposit( 57.22 );

    // Deposit $57.22 and supply a password. OK: calls a
    //  public function.
    pAcct->Deposit( 52.77, "pswd" );
}

double Account::Deposit( double dAmount, char *szPassword )
{
   if ( Validate( szPassword ) )
      return Deposit( dAmount );
   else
      return 0.0;
}
```

## <a name="see-also"></a>関連項目

[関数 (C++)](../cpp/functions-cpp.md)