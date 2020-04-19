---
title: コンパイラ エラー C2936
ms.date: 11/04/2016
f1_keywords:
- C2936
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
ms.openlocfilehash: d73f45440cf373368b70a11a7779f43587e73aca
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754655"
---
# <a name="compiler-error-c2936"></a>コンパイラ エラー C2936

'class': type-class-id がグローバル データ変数として再定義されています

ジェネリック クラスまたはテンプレート クラスをグローバル データ変数として使用することはできません。

このエラーは、中かっこが正しく一致していない場合に発生することがあります。

次の例では C2936 が生成されます。

```cpp
// C2936.cpp
// compile with: /c
template<class T> struct TC { };
int TC<int>;   // C2936

// OK
struct TC2 { };
int TC2;
```

C2936 は、ジェネリックを使用している場合にも発生することがあります。

```cpp
// C2936b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
int GC<int>;   // C2936

// OK
ref struct GC2 {};
int GC2;
```
