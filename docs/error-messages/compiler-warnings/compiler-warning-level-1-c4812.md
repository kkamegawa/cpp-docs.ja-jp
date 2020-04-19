---
title: コンパイラの警告 (レベル 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 420c44359b9e92cf8e77070bd3a270f992722d48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051281"
---
# <a name="compiler-warning-level-1-c4812"></a>コンパイラの警告 (レベル 1) C4812

旧形式の宣言スタイル: 'new_syntax' を使用してください

現在のリリースの Visual C++ では、コンストラクターの明示的な特殊化がサポートされていますが、将来のリリースではサポートされない可能性があります。

次の例では C4812 が生成されます。

```cpp
// C4812.cpp
// compile with: /W1 /c
template <class T>
class MyClass;

template<class T>
class MyClass<T*> {
   MyClass();
};

template<class T>
MyClass<T*>::MyClass<T*>() {}   // C4812
// try the following line instead
// MyClass<T*>::MyClass() {}
```