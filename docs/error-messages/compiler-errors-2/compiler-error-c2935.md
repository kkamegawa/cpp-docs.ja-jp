---
title: コンパイラ エラー C2935
ms.date: 11/04/2016
f1_keywords:
- C2935
helpviewer_keywords:
- C2935
ms.assetid: e11ef90d-0756-4e43-8a09-4974c6aa72a3
ms.openlocfilehash: 676c238dfb0ae78dbe5b144b5242bfb4ccbda76c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756150"
---
# <a name="compiler-error-c2935"></a>コンパイラ エラー C2935

'class': type-class-id がグローバル関数として再定義されています

ジェネリック クラスまたはテンプレート クラスをグローバル関数として使用することはできません。

このエラーは、中かっこが正しく一致していない場合に発生することがあります。

次の例では C2935 が生成されます。

```cpp
// C2935.cpp
// compile with: /c
template<class T>
struct TC {};
void TC<int>() {}   // C2935

// OK
struct TC2 {};
void TC2() {}
```

C2935 は、ジェネリックを使用しているときも発生します。

```cpp
// C2935b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC { };
void GC<int>() {}   // C2935
void GC() {}   // OK
```
