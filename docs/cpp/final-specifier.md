---
title: final 指定子
ms.date: 11/04/2016
f1_keywords:
- final_CPP
helpviewer_keywords:
- final Identifier
ms.assetid: 649866d0-79d4-449f-ab74-f84b911b79a3
ms.openlocfilehash: c6400c8060664713fdd004a5aa9536e0617bc0c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154777"
---
# <a name="final-specifier"></a>final 指定子

使用することができます、**final**キーワードを派生クラスでオーバーライドできない仮想関数を指定します。 また、このキーワードは、継承できないクラスの指定にも使用できます。

## <a name="syntax"></a>構文

```
function-declaration final;
class class-name final base-classes
```

## <a name="remarks"></a>Remarks

**final**は状況依存と予約済みキーワードではありません関数宣言の後に使用されますか、クラスの名前。 それ以外の場合、だけに特別な意味を持ちます。

ときに**final**クラスの宣言で使用される、`base-classes`宣言の省略可能な部分です。

## <a name="example"></a>例

次の例では、**final**仮想関数をオーバーライドできないことを指定するキーワード。

```cpp
class BaseClass
{
    virtual void func() final;
};

class DerivedClass: public BaseClass
{
    virtual void func(); // compiler error: attempting to
                         // override a final function
};
```

メンバー関数をオーバーライドできることを指定する方法については、次を参照してください。[オーバーライド指定子](../cpp/override-specifier.md)します。

次の例では、**final**クラスを継承できないことを指定するキーワード。

```cpp
class BaseClass final
{
};

class DerivedClass: public BaseClass // compiler error: BaseClass is
                                     // marked as non-inheritable
{
};
```

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[override 指定子](../cpp/override-specifier.md)