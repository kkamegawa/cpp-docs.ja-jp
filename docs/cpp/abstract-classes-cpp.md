---
title: 抽象クラス (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- classes [C++], abstract
- base classes [C++], abstract classes [C++]
- abstract classes [C++]
- derived classes [C++], abstract classes [C++]
ms.assetid: f0c5975b-39de-4d68-9640-6ce57f4632e6
ms.openlocfilehash: a7b41a2cabc2cff2eca24cf50c6c30d5190d39a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62385090"
---
# <a name="abstract-classes-c"></a>抽象クラス (C++)

抽象クラスは一般的な概念を表現したもので、このクラスからより具体的なクラスを派生するために使用できます。抽象クラス型のオブジェクトは作成できませんが、抽象クラス型へのポインターと参照は使用できます。

純粋仮想関数を 1 つでも含むクラスは抽象クラスと見なされます。 抽象クラスから派生したクラスは純粋仮想関数を実装する必要があります。そうしなければ、派生クラスも抽象クラスになります。

[仮想関数](../cpp/virtual-functions.md)に示されている例を検討してください。 `Account` クラスの目的は一般的な機能を提供することですが、`Account` 型のオブジェクトは一般的すぎて役に立ちません。 したがって、`Account` は抽象クラスの候補として適しています。

```cpp
// deriv_AbstractClasses.cpp
// compile with: /LD
class Account {
public:
   Account( double d );   // Constructor.
   virtual double GetBalance();   // Obtain balance.
   virtual void PrintBalance() = 0;   // Pure virtual function.
private:
    double _balance;
};
```

この宣言と前の宣言の唯一の違いは、`PrintBalance` が pure 指定子 (`= 0`) 付きで宣言されていることです。

## <a name="restrictions-on-abstract-classes"></a>抽象クラスに関する制約

抽象クラスは以下の項目では使用できません。

- 変数またはメンバー データ

- 引数の型

- 関数の戻り値の型

- 明示的な変換の型

もう 1 つの制限は、抽象クラスのコンストラクターが純粋仮想関数を直接または間接的に呼び出すと、結果が未定義になることです。 ただし、抽象クラスのコンストラクターとデストラクターは、他のメンバー関数を呼び出すことができます。

純粋仮想関数は抽象クラスに対して定義できますが、直接呼び出すには次の構文を使用する必要があります。

*abstract-class-name*::*function-name*()

これが役立つのは、オブジェクトを破棄する処理では常に基底クラスのデストラクターが呼び出されるため、基底クラスに純粋仮想デストラクターが含まれているクラスの階層構造をデザインするときです。 次に例を示します。

```cpp
// Declare an abstract base class with a pure virtual destructor.
// deriv_RestrictionsonUsingAbstractClasses.cpp
class base {
public:
    base() {}
    virtual ~base()=0;
};

// Provide a definition for destructor.
base::~base() {}

class derived:public base {
public:
    derived() {}
    ~derived(){}
};

int main() {
    derived *pDerived = new derived;
    delete pDerived;
}
```

`pDerived` によって指されるオブジェクトが削除されると、`derived` クラスのデストラクターが呼び出され、次に `base` クラスのデストラクターが呼び出されます。 純粋仮想関数の空の実装は、その関数に対して少なくとも実装が存在することを保証します。

> [!NOTE]
> 前の例では、純粋仮想関数 `base::~base` は、`derived::~derived` から暗黙的に呼び出されます。 完全修飾メンバー関数名を使用して純粋仮想関数を明示的に呼び出すこともできます。

## <a name="see-also"></a>関連項目

[継承](../cpp/inheritance-cpp.md)
