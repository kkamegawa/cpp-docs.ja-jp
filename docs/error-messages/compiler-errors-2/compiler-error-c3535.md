---
title: コンパイラ エラー C3535
ms.date: 11/04/2016
f1_keywords:
- C3535
helpviewer_keywords:
- C3535
ms.assetid: 24449c98-f681-484d-a00b-32533dca3a88
ms.openlocfilehash: 6b487c0f94a00ec64e0c2178265c5a8c27544a51
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761557"
---
# <a name="compiler-error-c3535"></a>コンパイラ エラー C3535

' type1 ' から ' type1 ' の型を推測できません

`auto` キーワードによって宣言された変数の型は、初期化式の型から推測できません。 たとえば、初期化式が `void`に評価される場合、このエラーが発生します。これは型ではありません。

### <a name="to-correct-this-error"></a>このエラーを解決するには

1. 初期化式の型が `void`されていないことを確認してください。

1. 宣言が基本型へのポインターではないことを確認してください。 詳細については、「[基本型](../../cpp/fundamental-types-cpp.md)」を参照してください。

1. 宣言が型へのポインターである場合は、初期化式がポインター型であることを確認します。

## <a name="example"></a>使用例

次の例では、初期化式が `void`に評価されるため、C3535 が生成されます。

```cpp
// C3535a.cpp
// Compile with /Zc:auto
void f(){}
int main()
{
   auto x = f();   //C3535
   return 0;
}
```

## <a name="example"></a>使用例

次の例では、ステートメントが推測された型へのポインターとして変数 `x` を宣言していますが、初期化子式の型が double であるため、C3535 が生成されます。 そのため、コンパイラは変数の型を推測できません。

```cpp
// C3535b.cpp
// Compile with /Zc:auto
int main()
{
   auto* x = 123.0;   // C3535
   return 0;
}
```

## <a name="example"></a>使用例

次の例では、変数 `p` は推測された型へのポインターを宣言していますが、初期化式はポインター型ではないため、C3535 が生成されます。

```cpp
// C3535c.cpp
// Compile with /Zc:auto
class A { };
A x;
auto *p = x;  // C3535
```

## <a name="see-also"></a>参照

[auto キーワード](../../cpp/auto-keyword.md)<br/>
[基本的な型](../../cpp/fundamental-types-cpp.md)
