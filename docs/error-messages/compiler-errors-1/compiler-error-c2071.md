---
title: コンパイラエラー C2071
ms.date: 11/04/2016
f1_keywords:
- C2071
helpviewer_keywords:
- C2071
ms.assetid: f8c09255-a5c4-47e3-8089-3d875ae43cc5
ms.openlocfilehash: 1dc9781bc0cf1bc6c7f879cc3971828983471c6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757749"
---
# <a name="compiler-error-c2071"></a>コンパイラエラー C2071

'識別子' : ストレージ クラスが正しくありません。

無効な[ストレージクラス](../../c-language/c-storage-classes.md)を使用して `identifier` が宣言されました。 1 つの識別子に複数のストレージ クラスが指定されている場合や、定義がストレージ クラスの宣言と互換性がない場合に、このエラーが発生することがあります。

この問題を解決するには、識別子の目的のストレージクラス (`static` や `extern`など) を理解し、一致するように宣言を修正します。

## <a name="example"></a>使用例

次の例では C2071 エラーが生成されます。

```cpp
// C2071.cpp
// compile with: /c
struct C {
   extern int i;   // C2071
};
struct D {
   int i;   // OK, no extern on an automatic
};
```

## <a name="example"></a>使用例

次の例では C2071 エラーが生成されます。

```cpp
// C2071_b.cpp
// compile with: /c
typedef int x(int i) { return i; }   // C2071
typedef int (x)(int);   // OK, no local definition in typedef
```
