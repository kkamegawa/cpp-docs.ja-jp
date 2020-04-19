---
title: コンパイラ エラー C2930
ms.date: 11/04/2016
f1_keywords:
- C2930
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
ms.openlocfilehash: b30e614236298cf9a07cbc29e028039903f9748f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760981"
---
# <a name="compiler-error-c2930"></a>コンパイラ エラー C2930

'クラス' : 'type-class-id' が、'enum identifier' の列挙子として再定義されています

ジェネリック クラスまたはテンプレート クラスは、列挙型のメンバーとして使用できません。

このエラーは、中かっこが正しく一致していない場合に発生することがあります。

次の例では C2930 が生成されます。

```cpp
// C2930.cpp
// compile with: /c
template<class T>
class x{};
enum SomeEnum { x };   // C2930

class y{};
enum SomeEnum { y };
```

C2930 は、ジェネリックを使用する場合にも発生することがあります。

```cpp
// C2930c.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
enum SomeEnum { GC };   // C2930

ref struct GC2 {};
enum SomeEnum2 { GC2 };
```
