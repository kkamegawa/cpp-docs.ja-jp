---
title: override 指定子
ms.date: 11/04/2016
helpviewer_keywords:
- override Identifier
ms.assetid: b286fb46-9374-4ad8-b2e7-4607119b6133
ms.openlocfilehash: 71505f8b9b4dc2800e80a78a64f0ca6984af1349
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/24/2019
ms.locfileid: "64345868"
---
# <a name="override-specifier"></a>override 指定子

使用することができます、**override**キーワードを基底クラスで仮想関数をオーバーライドする関数のメンバーを指定します。

## <a name="syntax"></a>構文

```
function-declaration override;
```

## <a name="remarks"></a>Remarks

**override**状況依存であり、つまり場合にのみ特別なは、メンバー関数宣言の後に使用されます。 それ以外の場合は、予約済みキーワード。

## <a name="example"></a>例

使用**override**コードでの誤った継承動作を防ぐためです。 次の例を使用せず、where を示しています**override**、派生クラスのメンバー関数の動作が意図されていません。 このコードに対してコンパイラ エラーは発生しません。

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA(); // ok, works as intended

    virtual void funcB(); // DerivedClass::funcB() is non-const, so it does not
                          // override BaseClass::funcB() const and it is a new member function

    virtual void funcC(double = 0.0); // DerivedClass::funcC(double) has a different
                                      // parameter type than BaseClass::funcC(int), so
                                      // DerivedClass::funcC(double) is a new member function
};
```

使用すると**override**コンパイラは自動的に新しいメンバー関数を作成するのではなくエラーを生成します。

```cpp
class BaseClass
{
    virtual void funcA();
    virtual void funcB() const;
    virtual void funcC(int = 0);
    void funcD();
};

class DerivedClass: public BaseClass
{
    virtual void funcA() override; // ok

    virtual void funcB() override; // compiler error: DerivedClass::funcB() does not
                                   // override BaseClass::funcB() const

    virtual void funcC( double = 0.0 ) override; // compiler error:
                                                 // DerivedClass::funcC(double) does not
                                                 // override BaseClass::funcC(int)

    void funcD() override; // compiler error: DerivedClass::funcD() does not
                           // override the non-virtual BaseClass::funcD()
};
```

関数をオーバーライドできないこととクラスを継承できないことを指定するには、使用、[最終的な](../cpp/final-specifier.md)キーワード。

## <a name="see-also"></a>関連項目

[final 指定子](../cpp/final-specifier.md)<br/>
[キーワード](../cpp/keywords-cpp.md)