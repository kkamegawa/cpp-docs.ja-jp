---
title: friend (C++)
ms.date: 07/15/2019
f1_keywords:
- friend_cpp
helpviewer_keywords:
- member access, from friend functions
- friend classes [C++]
- friend keyword [C++]
ms.assetid: 8fe9ee55-d56f-40cd-9075-d9fb1375aff4
ms.openlocfilehash: 03b6cb7f856ec59c10f5e410c947f74d17ec4e46
ms.sourcegitcommit: fd466f2e14ad001f52f3dbe54f46d77be10f2d7b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "67894419"
---
# <a name="friend-c"></a>friend (C++)

状況によっては、クラスのメンバーではない関数、または別のクラスのすべてのメンバーにメンバー レベルのアクセスを許可する方が便利です。 クラスの実装側が自分のフレンドを宣言することだけが可能です。 関数またはクラスが自分自身をいずれかのクラスのフレンドとして宣言することはできません。 クラスの定義で使用して、**friend**キーワードと、非メンバー関数またはクラスのプライベートおよびプロテクト メンバーにアクセス権を付与するには、その他のクラスの名前。 テンプレートの定義で型パラメーターは、フレンドとして宣言できます。

## <a name="syntax"></a>構文

```
class friend F
friend F;
```

## <a name="friend-declarations"></a>フレンド宣言

以前に宣言されなかったフレンド関数を宣言すると、その関数は外側の非クラス スコープにエクスポートされます。

フレンド宣言で宣言された関数として扱われますを使用して宣言された、 **extern**キーワード。 詳細については、次を参照してください。 [extern](extern-cpp.md)します。

グローバル スコープの関数はプロトタイプの前にフレンドとして宣言できますが、メンバー関数は、完全なクラス宣言の前にフレンドとして宣言することはできません。 次のコードは、なぜこれが失敗するかを示します。

```cpp
class ForwardDeclared;   // Class name is known.
class HasFriends
{
    friend int ForwardDeclared::IsAFriend();   // C2039 error expected
};
```

前の例では、スコープにクラス名 `ForwardDeclared` を入力しますが、宣言全体、特に関数 `IsAFriend` を宣言する部分は不明です。 そのため、**friend**クラスの宣言で`HasFriends`エラーが生成されます。

クラスのフレンド宣言の 2 つの形式がある、c++ 11 以降します。

```cpp
friend class F;
friend F;
```

最初のフォームでは、最も内側の名前空間にその名前の既存のクラスが見つからなかった場合、新しいクラス F が導入されています。 **C++ 11**:2 番目の形式は、新しいクラスを導入していませんクラスは既に宣言されているし、テンプレートの型パラメーターまたはフレンドとしての typedef を宣言するときに使用する必要がありますが使用できます。

使用`class friend F`と参照先の型はまだ宣言されていません。

```cpp
namespace NS
{
    class M
    {
        class friend F;  // Introduces F but doesn't define it
    };
}
```

```cpp
namespace NS
{
    class M
    {
        friend F; // error C2433: 'NS::F': 'friend' not permitted on data declarations
    };
}
```

次の例では、`friend F`を指す、 `F` NS のスコープ外部で宣言されたクラスです。

```cpp
class F {};
namespace NS
{
    class M
    {
        friend F;  // OK
    };
}
```

使用`friend F`フレンドとしてテンプレート パラメーターを宣言します。

```cpp
template <typename T>
class my_class
{
    friend T;
    //...
};
```

使用`friend F`フレンドとしての typedef を宣言します。

```cpp
class Foo {};
typedef Foo F;

class G
{
    friend F; // OK
    friend class F // Error C2371 -- redefinition
};
```

相互にフレンドである 2 つのクラスを宣言するには、2 番目のクラス全体が最初のクラスのフレンドとして指定される必要があります。 この制限の理由は、2 番目のクラスが宣言された位置でのみコンパイラは個々のフレンド関数を宣言するために十分な情報を得られるためです。

> [!NOTE]
>  2 番目のクラス全体は最初のクラスへのフレンドである必要がありますが、最初のクラスのどの関数が 2 番目のクラスのフレンドであるかを選択できます。

## <a name="friend-functions"></a>friend 関数

**friend**関数は、クラスのメンバーではないが、クラスのプライベートおよびプロテクト メンバーにアクセスする関数。 friend 関数はクラス メンバーと見なされません。これらの関数は、特別なアクセス特権が付与されている標準の外部関数です。 friend はクラスのスコープでないと、メンバー選択演算子を使用して呼び出されません (**します。** および **>** ) 別のクラスのメンバーでない限りです。 **friend**関数がアクセスを許可しているクラスで宣言されています。 **friend**クラス宣言で宣言をどこにでも配置できます。 アクセス制御キーワードによる影響はありません。

次に、`Point` クラスと `ChangePrivate` フレンド関数の例を示します。 **friend**関数のプライベート データ メンバーへのアクセスには、`Point`をパラメーターとして受け取るオブジェクトします。

```cpp
// friend_functions.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class Point
{
    friend void ChangePrivate( Point & );
public:
    Point( void ) : m_i(0) {}
    void PrintPrivate( void ){cout << m_i << endl; }

private:
    int m_i;
};

void ChangePrivate ( Point &i ) { i.m_i++; }

int main()
{
   Point sPoint;
   sPoint.PrintPrivate();
   ChangePrivate(sPoint);
   sPoint.PrintPrivate();
// Output: 0
           1
}
```

## <a name="class-members-as-friends"></a>フレンドとしてのクラス メンバー

クラス メンバー関数は他のクラスのフレンドとして宣言できます。 次に例を示します。

```cpp
// classes_as_friends1.cpp
// compile with: /c
class B;

class A {
public:
   int Func1( B& b );

private:
   int Func2( B& b );
};

class B {
private:
   int _b;

   // A::Func1 is a friend function to class B
   // so A::Func1 has access to all members of B
   friend int A::Func1( B& );
};

int A::Func1( B& b ) { return b._b; }   // OK
int A::Func2( B& b ) { return b._b; }   // C2248
```

この例では、`A::Func1( B& )` 関数に `B` クラスへのフレンド アクセスのみ許可されます。 そのため、プライベート メンバーへのアクセスを`_b`で正しい`Func1`クラスの`A`ではなく`Func2`します。

`friend` クラスは、すべてのメンバー関数が、クラスのその他のプライベート メンバーとプロテクト メンバーにアクセスできるメンバー関数を持つ、クラスのフレンド関数であるクラスです。 `friend` クラスの `B` 宣言が次のようになっていたとします。

```cpp
friend class A;
```

その場合、`A` クラスのすべてのメンバー関数に `B` クラスへのフレンド アクセスが許可されます。 次に、フレンド クラスの例を示します。

```cpp
// classes_as_friends2.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
class YourClass {
friend class YourOtherClass;  // Declare a friend class
public:
   YourClass() : topSecret(0){}
   void printMember() { cout << topSecret << endl; }
private:
   int topSecret;
};

class YourOtherClass {
public:
   void change( YourClass& yc, int x ){yc.topSecret = x;}
};

int main() {
   YourClass yc1;
   YourOtherClass yoc1;
   yc1.printMember();
   yoc1.change( yc1, 5 );
   yc1.printMember();
}
```

明示的に指定されていない限り、フレンド関係は相互関係ではありません。 上の例では、`YourClass` のメンバー関数は `YourOtherClass` のプライベート メンバーにアクセスできません。

マネージ型 (でC++/CLI) 任意のフレンド関数、フレンド クラス、またはフレンド インターフェイスを持つことはできません。

フレンド関係は継承されません。つまり、`YourOtherClass` から派生したクラスは `YourClass` のプライベート メンバーにアクセスできません。 フレンド関係は推移的ではないため、`YourOtherClass` のフレンドであるクラスは `YourClass` にアクセスできません。

次の図は、4 つのクラス宣言 (`Base`、`Derived`、`aFriend`、`anotherFriend`) を示しています。 `aFriend` のプライベート メンバー (および `Base` が継承した可能性があるすべてのメンバー) に直接アクセスできるのは、`Base` クラスだけです。

![フレンド関係の包含](../cpp/media/vc38v41.gif "フレンド関係の包含") <br/>
フレンド関係の包含

## <a name="inline-friend-definitions"></a>インラインのフレンドの定義

フレンド関数は、クラス宣言内で (特定の関数本体) 定義できます。 これらの関数はインライン関数であり、メンバーのインライン関数のように、すべてのクラス メンバーが発生した直後、クラス スコープが閉じる前に定義されているように動作します (クラス宣言の末尾)。 クラス宣言内で定義されているフレンド関数は、外側のクラスのスコープになります。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)