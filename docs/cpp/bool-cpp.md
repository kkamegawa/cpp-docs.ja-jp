---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: a3384bbb118c7363a603b5b9b0c8a375cb3dd185
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301640"
---
# <a name="bool-c"></a>bool (C++)

このキーワードは組み込みの型です。 この型の変数には、 [true](../cpp/true-cpp.md)と[false](../cpp/false-cpp.md)の値を指定できます。 条件式の型は**bool**であるため、 **bool**型の値を持つことになります。 たとえば、`i!=0` は `i`の値に応じて TRUE または FALSE になります。

**Visual Studio 2017 バージョン15.3 以降**( [/std: c++ 17](../build/reference/std-specify-language-standard-version.md)で利用可能): 後置または前置インクリメントまたはデクリメント演算子のオペランドを**bool**型にすることはできません。 言い換えると、**ブール**型の変数 `b` した場合、次の式は使用できなくなります。

```cpp
    b++;
    ++b;
    b--;
    --b;
```

値 TRUE と FALSE には、次のリレーションシップがあります。

```cpp
!false == true
!true == false
```

次のステートメントがあるとします。

```cpp
if (condexpr1) statement1;
```

`condexpr1` が TRUE の場合、`statement1` は常に実行されます。`condexpr1` が FALSE の場合、`statement1` は実行されません。

後置または前置と **++** 型の変数に演算子を適用**bool**変数が TRUE に設定します。
**Visual Studio 2017 バージョン15.3 以降**:**ブール**値の operator + + は言語から削除されたため、サポートされなくなりました。

後置または前置 **--** 演算子は、この型の変数には適用できません。

**bool**型が整数の上位変換に参加します。 **Bool**型の右辺値は**int**型の r 値に変換できますが、FALSE はゼロになり、TRUE は1になります。 別個の型として、 **bool**はオーバーロードの解決に関与します。

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[組み込みの型](../cpp/fundamental-types-cpp.md)