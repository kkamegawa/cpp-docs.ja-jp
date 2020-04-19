---
title: 関数テンプレートの明示的特殊化
ms.date: 11/04/2016
helpviewer_keywords:
- overriding, functions
- function templates, specialization
- explicit specialization of function templates
- declaring functions [C++], specialization of function template
- specialization of function templates
ms.assetid: eb0fcb73-eaed-42a1-9b83-14b055a34bf8
ms.openlocfilehash: 3d91383f895f1a8be983efe42f685419ca988823
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62184275"
---
# <a name="explicit-specialization-of-function-templates"></a>関数テンプレートの明示的特殊化

関数テンプレートを使用すると、特定の型のために関数テンプレートの明示的な特殊化 (オーバーライド) を提供することによって、その型の特別な動作を定義できます。 例:

```cpp
template<> void MySwap(double a, double b);
```

この宣言では、別の関数を定義できます。**double**変数。 などの非テンプレート関数では、標準的な型変換 (型の変数の昇格など**float**に**double**) 適用されます。

## <a name="example"></a>例

```cpp
// explicit_specialization.cpp
template<class T> void f(T t)
{
};

// Explicit specialization of f with 'char' with the
// template argument explicitly specified:
//
template<> void f<char>(char c)
{
}

// Explicit specialization of f with 'double' with the
// template argument deduced:
//
template<> void f(double d)
{
}
int main()
{
}
```

## <a name="see-also"></a>関連項目

[関数テンプレート](../cpp/function-templates.md)