---
title: コンパイラエラー C2084
ms.date: 11/04/2016
f1_keywords:
- C2084
helpviewer_keywords:
- C2084
ms.assetid: 990b107f-3721-4851-ae8b-4b69a8c149ed
ms.openlocfilehash: 881ae051b2779fe674b31b64a7cbe7be7cf63705
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757892"
---
# <a name="compiler-error-c2084"></a>コンパイラエラー C2084

関数 '*function*' には既に本体があります

関数は既に定義されています。

Visual Studio 2002 より前の場合

- コンパイラは、同じ実際の型に解決される複数のテンプレートの特殊化を受け入れますが、追加の定義は使用できません。 コンパイラは、これらの複数の定義を検出するようになりました。

- `__int32` と `int` は個別の型として扱われました。 コンパイラは、`__int32` を `int`のシノニムとして扱うようになりました。 つまり、関数が `__int32` と `int` の両方でオーバーロードされている場合、コンパイラは複数の定義を検出し、エラーが発生します。

## <a name="example"></a>使用例

次の例では、C2084 が生成されます。

```cpp
// C2084.cpp
void Func(int);
void Func(int) {}   // define function
void Func(int) {}   // C2084 second definition
```

このエラーを修正するには、重複する定義を削除します。

```cpp
// C2084b.cpp
// compile with: /c
void Func(int);
void Func(int) {}
```
