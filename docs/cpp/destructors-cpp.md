---
title: デストラクター (C++)
ms.date: 07/20/2019
helpviewer_keywords:
- objects [C++], destroying
- destructors, C++
ms.assetid: afa859b0-f3bc-4c4d-b250-c68b335b6004
ms.openlocfilehash: 1e1190f49c7ccf5c312172f265d32a4b855bd878
ms.sourcegitcommit: 2da5c42928739ca8cd683a9002598f28d8ec5f8e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2019
ms.locfileid: "70060141"
---
# <a name="destructors-c"></a>デストラクター (C++)

デストラクターは、オブジェクトがスコープ外に出たとき、または**delete**の呼び出しによって明示的に破棄されたときに自動的に呼び出されるメンバー関数です。 デストラクターには、クラスと同じ名前が付けられます。その`~`前に、チルダ () が付きます。 たとえば、クラス `String` のデストラクターを宣言するには、`~String()` とします。

デストラクターを定義しない場合は、コンパイラによって既定値が提供されます。多くのクラスでは、これで十分です。 カスタムデストラクターを定義する必要があるのは、解放する必要があるシステムリソースへのハンドル、またはそれが指すメモリを所有するポインターがクラスに格納されている場合のみです。

`String` クラスの次のような宣言があるとします。

```cpp
// spec1_destructors.cpp
#include <string>

class String {
public:
   String( char *ch );  // Declare constructor
   ~String();           //  and destructor.
private:
   char    *_text;
   size_t  sizeOfText;
};

// Define the constructor.
String::String( char *ch ) {
   sizeOfText = strlen( ch ) + 1;

   // Dynamically allocate the correct amount of memory.
   _text = new char[ sizeOfText ];

   // If the allocation succeeds, copy the initialization string.
   if( _text )
      strcpy_s( _text, sizeOfText, ch );
}

// Define the destructor.
String::~String() {
   // Deallocate the memory that was previously reserved
   //  for this string.
   delete[] _text;
}

int main() {
   String str("The piper in the glen...");
}
```

前の例では、デストラクター `String::~String`は**delete**演算子を使用して、テキストストレージに対して動的に割り当てられた領域の割り当てを解除します。

## <a name="declaring-destructors"></a>宣言 (デストラクターを)

デストラクターはクラスと同じ名前の関数ですが、先頭にティルダ (`~`) が付きます。

デストラクターの宣言には以下の規則が適用されます 。

- デストラクタ―は引数を受け取りません。

- 値 (または**void**) を返しません。

- は、 **const**、 **volatile**、または**static**として宣言することはできません。 ただし、 **const**、 **volatile**、または**static**として宣言されたオブジェクトを破棄するために呼び出すことができます。

- は**virtual**として宣言できます。 仮想デストラクターを使用すると、型を知らなくてもオブジェクトを破棄できます。オブジェクトの正しいデストラクターが、仮想関数のメカニズムを使用して呼び出されます。 デストラクターは、抽象クラスの純粋仮想関数として宣言することもできます。

## <a name="using-destructors"></a>デストラクターの使用

デストラクターは、次のいずれかのイベントが発生したときに呼び出されます。

- ブロック スコープを持つローカル (自動) オブジェクトがスコープから外れます。

- **New**演算子を使用して割り当てられたオブジェクトは、 **delete**を使用して明示的に解放されます。

- 一時オブジェクトの有効期間は終了します。

- プログラムは終了し、グローバルまたはスタティック オブジェクトが存在します。

- デストラクターは、デストラクター関数の完全修飾名を使用して明示的に呼び出されます

デストラクターは、自由にクラス メンバー関数を呼び出したり、クラス メンバーのデータにアクセスしたりできます。

デストラクターの使用には、次の2つの制限があります。

- アドレスを取得することはできません。

- 派生クラスは、基底クラスのデストラクターを継承しません。

## <a name="order-of-destruction"></a>破棄の順序

オブジェクトがスコープ外になるとき、または削除されるとき、完全な破棄のイベントの順序は次のとおりです。

1. クラスのデストラクターが呼び出され、デストラクター関数の本体が実行されます。

1. 非静的メンバー オブジェクトのデストラクターは、クラス宣言での出現順序の逆順で呼び出されます。 これらのメンバーの構築で使用される省略可能なメンバー初期化リストは、構築または破棄の順序には影響しません。

1. 非仮想基底クラスのデストラクターは、宣言の逆の順序で呼び出されます。

1. 仮想基底クラスのデストラクターは、宣言の逆順で呼び出されます。

```cpp
// order_of_destruction.cpp
#include <cstdio>

struct A1      { virtual ~A1() { printf("A1 dtor\n"); } };
struct A2 : A1 { virtual ~A2() { printf("A2 dtor\n"); } };
struct A3 : A2 { virtual ~A3() { printf("A3 dtor\n"); } };

struct B1      { ~B1() { printf("B1 dtor\n"); } };
struct B2 : B1 { ~B2() { printf("B2 dtor\n"); } };
struct B3 : B2 { ~B3() { printf("B3 dtor\n"); } };

int main() {
   A1 * a = new A3;
   delete a;
   printf("\n");

   B1 * b = new B3;
   delete b;
   printf("\n");

   B3 * b2 = new B3;
   delete b2;
}

Output: A3 dtor
A2 dtor
A1 dtor

B1 dtor

B3 dtor
B2 dtor
B1 dtor
```

### <a name="virtual-base-classes"></a>仮想基底クラス

仮想基底クラスのデストラクターが有向非循環グラフ (深さ優先、左から右、後順走査) で外観の逆の順序で呼び出されます。 次の図は、継承グラフを示しています。

![仮想基底クラスを示す継承グラフ](../cpp/media/vc392j1.gif "仮想基底クラスを示す継承グラフ") <br/>
仮想基底クラスを示す継承グラフ

図に示されているクラスの先頭を次に示します。

```cpp
class A
class B
class C : virtual public A, virtual public B
class D : virtual public A, virtual public B
class E : public C, public D, virtual public B
```

コンパイラは、`E` 型のオブジェクトの仮想基底クラスの破棄の順序を決定するため、次のアルゴリズムを適用してリストを作成します。

1. グラフを左に走査し、グラフの最も深いポイント (この場合は `E`) で開始します。

1. すべてのノードが表示されるまで左方向への走査を実行します。 現在のノードの名前を確認します。

1. 保持するノードが仮想基底クラスであるかどうかを確認するために、前のノード (右下隅) を再表示します。

1. 保持するノードが仮想基底クラスである場合は、既に構成されているかどうかを参照するために、リストを確認します。 仮想基底クラスでない場合は無視します。

1. 保持するノードがリストにない場合は、リストの末尾に追加します。

1. 上方向および次のパスに沿って右へグラフを走査します。

1. 手順 2. に進みます。

1. 最後の上方向のパスが使い果たされたら、現在のノードの名前を確認します。

1. 手順 3. に進みます。

1. 下部のノードが再び現在のノードになるまで、このプロセスを続行します。

したがって、クラス `E` の場合、破棄の順序は次のようになります。

1. 非仮想基底クラス`E`。

1. 非仮想基底クラス`D`。

1. 非仮想基底クラス`C`。

1. 仮想基底クラス `B`。

1. 仮想基底クラス `A`。

このプロセスにより、一意のエントリの順序付きリストが作成されます。 いずれのクラス名も、2 回表示されることはありません。 リストが構築されると、逆順で走査され、リストの各クラスのデストラクターが最後から最初まで呼び出されます。

構築または破棄の順序は、1 つのクラスのコンストラクターまたはデストラクターが、初めて作成されるか、より長く保持されている他のコンポーネントに依存する場合に、特に重要になります。たとえば、コードが実行されたときに (上記の図に示す) `A` のデストラクター (上記の図に示す) がまだ存在している `B` に依存している場合や、その逆の場合です。

継承グラフでのクラス間のこのような依存関係は、後で派生するクラスが左端のパスを変更し、それによって構築と破棄の順序を変更できるため、本質的に危険です。

### <a name="non-virtual-base-classes"></a>非仮想基底クラス

非仮想基底クラスのデストラクターは、基底クラス名が宣言されている逆の順序で呼び出されます。 クラス宣言の例を次に示します。

```cpp
class MultInherit : public Base1, public Base2
...
```

前の例では、`Base2` のデストラクターは、`Base1` のデストラクターの前に呼び出されます。

## <a name="explicit-destructor-calls"></a>明示的なデストラクター呼び出し

デストラクターを明示的に呼び出す必要はほとんどありません。 ただし、絶対アドレスにあるオブジェクトのクリーンアップを実行すると便利な場合があります。 これらのオブジェクトは、通常、配置引数を受け取るユーザー定義の**new**演算子を使用して割り当てられます。 このメモリはフリーストアから割り当てられていないため、 **delete**演算子はこのメモリの割り当てを解除できません (詳細については、「 [New および delete 演算子](../cpp/new-and-delete-operators.md)」を参照してください)。 ただし、デストラクターへの呼び出しは適切なクリーンアップを実行できます。 オブジェクトのデストラクターを明示的に呼び出すには、`s` (`String` クラス) で次のいずれかのステートメントを使用します。

```cpp
s.String::~String();     // non-virtual call
ps->String::~String();   // non-virtual call

s.~String();       // Virtual call
ps->~String();     // Virtual call
```

先に示したデストラクターへの明示的な呼び出しの表記は、型がデストラクターを定義するかどうかにかかわらず使用できます。 これにより、デストラクターが型に対して定義されているかどうかを確認せずにこのような明示的な呼び出しを行うことができます。 何も定義されていないデストラクターへの明示的な呼び出しは無効です。

## <a name="robust-programming"></a>信頼性の高いプログラミング

クラスは、リソースを取得する場合にデストラクターを必要とし、リソースを安全に管理するために、コピーコンストラクターとコピー割り当てを実装する必要がある場合があります。

これらの特殊な関数がユーザーによって定義されていない場合は、コンパイラによって暗黙的に定義されます。 暗黙的に生成されたコンストラクターと代入演算子は、浅い、メンバーごとのコピーを実行します。これは、オブジェクトがリソースを管理している場合は、ほぼ間違いありません。

次の例では、暗黙的に生成されたコピーコンストラクター `str1.text`が`str2.text`ポインターを作成し、同じメモリを参照します`copy_strings()`。から戻ると、そのメモリは2回削除されます。これは未定義の動作です。

```cpp
void copy_strings()
{
   String str1("I have a sense of impending disaster...");
   String str2 = str1; // str1.text and str2.text now refer to the same object
} // delete[] _text; deallocates the same memory twice
  // undefined behavior
```

デストラクター、コピーコンストラクター、またはコピー代入演算子を明示的に定義すると、移動コンストラクターと移動代入演算子の暗黙的な定義が禁止されます。 この場合、コピー操作の実行に失敗した場合、通常、コピーに負荷がかかると、最適化の機会が失われます。

## <a name="see-also"></a>関連項目

[コピー コンストラクターとコピー代入演算子](../cpp/copy-constructors-and-copy-assignment-operators-cpp.md)</br>
[移動コンストラクターと移動代入演算子](../cpp/move-constructors-and-move-assignment-operators-cpp.md)
