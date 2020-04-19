---
title: コンパイラ エラー C2921
ms.date: 11/04/2016
f1_keywords:
- C2921
helpviewer_keywords:
- C2921
ms.assetid: 323642a0-bfc4-4942-9f41-c3adf5c54296
ms.openlocfilehash: 82042b851282e686719ed54ccad0a2802afda22b
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761020"
---
# <a name="compiler-error-c2921"></a>コンパイラ エラー C2921

再定義 : 'class' : クラス テンプレートまたはジェネリックは 'type' として宣言されます。

ジェネリックまたはクラス テンプレートに複数の等しくない宣言が存在します。 このエラーを修正するには、型ごとに異なる名前を使用するか、型名の再定義を削除します。

次の例では、C2921 エラーが生成されます。

```cpp
// C2921.cpp
// compile with: /c
template <class T> struct TC2 {};
typedef int TC2;   // C2921
// try the following line instead
// typedef struct TC2<int> x;   // OK - declare a template instance
```

C2921 は、ジェネリックを使用する場合にも発生することがあります。

```cpp
// C2921b.cpp
// compile with: /clr /c
generic <class T> ref struct GC2 {};
typedef int GC2;   // C2921
// try the following line instead
// typedef ref struct GC2<int> x;
```
