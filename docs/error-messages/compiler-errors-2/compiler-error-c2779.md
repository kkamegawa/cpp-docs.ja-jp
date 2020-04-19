---
title: コンパイラエラー C2779
ms.date: 11/04/2016
f1_keywords:
- C2779
helpviewer_keywords:
- C2779
ms.assetid: 4a00e492-855a-41f3-8a18-5f60ee20c2f2
ms.openlocfilehash: 9b4e0f255fd62801cb2010c109d05de89362bb9f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740001"
---
# <a name="compiler-error-c2779"></a>コンパイラエラー C2779

' 宣言 ': プロパティメソッドは、非静的データメンバーにのみ関連付けることができます

`property` 拡張属性が静的データメンバーに不適切に適用されています。

次の例では、C2779 が生成されます。

```cpp
// C2779.cpp
struct A {
   static __declspec(property(put=PutProp))
   // try the following line instead
   __declspec(property(put=PutProp))
      int prop;   // C2779
   int PutProp(void);
};
```
