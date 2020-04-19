---
title: コンパイラ エラー C3226
ms.date: 11/04/2016
f1_keywords:
- C3226
helpviewer_keywords:
- C3226
ms.assetid: 636106ca-6f4e-4303-a6a0-8803221ec67d
ms.openlocfilehash: 466791f07b7f5dc7f482eec5c6f40bb039947648
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74743472"
---
# <a name="compiler-error-c3226"></a>コンパイラ エラー C3226

テンプレート宣言は、ジェネリック宣言の内部では使用できません

ジェネリック クラス内部のジェネリック宣言を使用します。

次の例では C3226 が生成されます。

```cpp
// C3226.cpp
// compile with: /clr
generic <class T>
ref class C {
   template <class T1>   // C3226
   ref struct S1 {};
};
```

次の例では、考えられる解決策を示しています。

```cpp
// C3226b.cpp
// compile with: /clr /c
generic <class T>
ref class C {
   generic <class T1>
   ref struct S1 {};
};
```
