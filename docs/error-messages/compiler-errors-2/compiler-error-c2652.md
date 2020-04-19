---
title: コンパイラエラー C2652
ms.date: 11/04/2016
f1_keywords:
- C2652
helpviewer_keywords:
- C2652
ms.assetid: 6e3d1a90-a989-4088-8afd-dc82f6a2d66f
ms.openlocfilehash: cedee3f1e3289aaf0ea38d75b6c812b61f891435
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756124"
---
# <a name="compiler-error-c2652"></a>コンパイラエラー C2652

' identifier ': コピーコンストラクターが無効です: 最初のパラメーターを ' identifier ' にすることはできません

コピーコンストラクターの最初のパラメーターの型は、定義されているクラス、構造体、または共用体と同じです。 最初のパラメーターには、型への参照を指定できますが、型自体は使用できません。

次の例では、C2651 が生成されます。

```cpp
// C2652.cpp
// compile with: /c
class A {
   A( A );   // C2652 takes an A
};
class B {
   B( B& );   // OK, reference to B
};
```
