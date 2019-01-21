---
title: クラス メンバーの概要
ms.date: 11/04/2016
helpviewer_keywords:
- members [C++], types of class members
- members [C++]
- class members [C++], types of
- class members
ms.assetid: 8802cfa9-705d-4f37-acde-245d6838010c
ms.openlocfilehash: 8edfadefdacf94685952d31f2eaf83e8593eaef8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637919"
---
# <a name="class-member-overview"></a>クラス メンバーの概要

クラスまたは構造体はそのメンバーで構成されます。 クラスが行う作業は、そのメンバー関数によって実行されます。 クラスが維持する状態は、そのデータ メンバー内に格納されます。 メンバーの初期化はコンス トラクター、およびメモリの解放などのクリーンアップ作業が行われ、リソースの解放、デストラクターによって行われます。 C++11 以降では、データ メンバーは宣言の時点で初期化することができます (通常はその必要があります)。

## <a name="kinds-of-class-members"></a>クラス メンバーの種類

メンバーのカテゴリの完全な一覧は次のとおりです。

- [特殊なメンバー関数](special-member-functions.md)します。

- [メンバー関数の概要](overview-of-member-functions.md)します。

- [データ メンバー](static-members-cpp.md)などの組み込み型とその他のユーザー定義型です。

- 演算子

- [入れ子にされたクラス宣言](nested-class-declarations.md)

- [共用体](unions.md)

- [列挙体](../cpp/enumerations-cpp.md)します。

- [ビット フィールド](../cpp/cpp-bit-fields.md)します。

- [friend](../cpp/friend-cpp.md)します。

- [エイリアスと typedef](../cpp/aliases-and-typedefs-cpp.md)します。

    > [!NOTE]
    >  friend はクラス宣言内に含まれているため、前の一覧に含まれます。 ただし、これらは、クラスのスコープ内にないため、真のクラス メンバーではありません。

## <a name="example-class-declaration"></a>クラス宣言の例

次の例は、単純なクラス宣言を示しています。

```cpp
// TestRun.h

class TestRun
{
    // Start member list.

    //The class interface accessible to all callers.
public:
    // Use compiler-generated default constructor:
    TestRun() = default;
    // Don't generate a copy constructor:
    TestRun(const TestRun&) = delete;
    TestRun(std::string name);
    void DoSomething();
    int Calculate(int a, double d);
    virtual ~TestRun();
    enum class State { Active, Suspended };

    // Accessible to this class and derived classes only.
protected:
    virtual void Initialize();
    virtual void Suspend();
    State GetState();

    // Accessible to this class only.
private:
    // Default brace-initialization of instance members:
    State _state{ State::Suspended };
    std::string _testName{ "" };
    int _index{ 0 };

    // Non-const static member:
    static int _instances;
    // End member list.
};

// Define and initialize static member.
int TestRun::_instances{ 0 };
```

## <a name="member-accessibility"></a>メンバーのアクセシビリティ

クラスのメンバーは、メンバーの一覧で宣言されます。 クラスのメンバーの一覧の任意の数に分割できます**プライベート**、**保護**と**パブリック**アクセス指定子と呼ばれるキーワードを使用してセクションします。  コロン **:** アクセス指定子に従う必要があります。  これらのセクションは連続している必要はありません。つまり、これらのキーワードはいずれも、メンバー リスト内で複数回出現してもかまいません。  キーワードは、次のアクセス指定子または右中かっこまでのすべてのメンバーのアクセスを指定します。 詳細については、次を参照してください。[メンバー アクセス コントロール (C++)](../cpp/member-access-control-cpp.md)します。

## <a name="static-members"></a>静的メンバー

データ メンバーが静的として宣言されることがあります。この場合、クラスのすべてのオブジェクトは、そのデータ メンバーの同じコピーにアクセスできます。 メンバー関数宣言すること、静的な場合にのみアクセスできるクラスの静的データ メンバー (持たない*この*ポインター)。 詳細については、次を参照してください。[静的データ メンバー](../cpp/static-members-cpp.md)します。

## <a name="special-member-functions"></a>特殊なメンバー関数

特殊なメンバー関数は、ソース コードで指定しない場合、コンパイラによって自動的に提供される関数です。

1. 既定のコンストラクター

1. コピー コンストラクター

1. **(C++ 11)** 移動コンス トラクター

1. コピー代入演算子

1. **(C++ 11)** 移動代入演算子

1. デストラクターです。

詳細については、次を参照してください。[特殊なメンバー関数](../cpp/special-member-functions.md)します。

## <a name="memberwise-initialization"></a>メンバーごとの初期化

C++11 以降では、非静的メンバーの宣言子に初期化子を含めることができます。

```cpp
class CanInit
{
public:
    long num {7};       // OK in C++11
    int k = 9;          // OK in C++11
    static int i = 9; // Error: must be defined and initialized
                      // outside of class declaration.

    // initializes num to 7 and k to 9
    CanInit(){}

    // overwrites original initialized value of num:
    CanInit(int val) : num(val) {}
};
int main()
{
}
```

コンストラクターにおいてメンバーに値が代入される場合、宣言の時点でメンバーの初期化に使用された値は、その値によって上書きされます。

特定のクラス型のすべてのオブジェクトの静的データ メンバーの共有コピーが 1 つだけあります。 静的データ メンバーは必ず定義する必要があり、ファイル スコープで初期化できます (静的データ メンバーの詳細については、次を参照してください[静的データ メンバー](../cpp/static-members-cpp.md)。)。このような初期化を行う方法を次の例に示します。

```cpp
// class_members2.cpp
class CanInit2
{
public:
    CanInit2() {} // Initializes num to 7 when new objects of type
                 //  CanInit are created.
    long     num {7};
    static int i;
    static int j;
};

// At file scope:

// i is defined at file scope and initialized to 15.
// The initializer is evaluated in the scope of CanInit.
int CanInit2::i = 15;

// The right side of the initializer is in the scope
// of the object being initialized
int CanInit2::j = i;
```

> [!NOTE]
>  クラス名 `CanInit2` は、定義中の `i` が `i` クラスのメンバーであることを指定するために、`CanInit2` の前に配置される必要があります。

## <a name="see-also"></a>関連項目

[クラスと構造体](../cpp/classes-and-structs-cpp.md)
