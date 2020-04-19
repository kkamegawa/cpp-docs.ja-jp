---
title: コンパイラ エラー C2920
ms.date: 11/04/2016
f1_keywords:
- C2920
helpviewer_keywords:
- C2920
ms.assetid: 0a4cb2de-00a0-4209-8160-c7ce6ed7d9ab
ms.openlocfilehash: 2b744729097f7e697c7a7695a849b5ee46d7a4ab
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761033"
---
# <a name="compiler-error-c2920"></a>コンパイラ エラー C2920

再定義 : 'class' : クラス テンプレートまたはジェネリックは既に 'type' として宣言されています

ジェネリックまたはテンプレート クラスに複数の宣言が存在しますが、これらは同じではありません。 このエラーを修正するには、型ごとに異なる名前を使用するか、型名の再定義を削除します。

次の例では、C2920 を生成し、その修正方法を示しています。

```cpp
// C2920.cpp
// compile with: /c
typedef int TC1;
template <class T>
struct TC1 {};   // C2920
struct TC2 {};   // OK - fix by using a different name
```

C2920 は、ジェネリックを使用する場合にも発生することがあります。

```cpp
// C2920b.cpp
// compile with: /clr /c
typedef int GC1;
generic <class T>
ref struct GC1 {};   // C2920
ref struct GC2 {};   // OK - fix by using a different name
```
