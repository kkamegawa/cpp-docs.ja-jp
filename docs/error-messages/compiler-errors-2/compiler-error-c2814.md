---
title: コンパイラ エラー C2814
ms.date: 11/04/2016
f1_keywords:
- C2814
helpviewer_keywords:
- C2814
ms.assetid: 7d165136-a08b-4497-a76d-60a21bb19404
ms.openlocfilehash: 5cc22afa29160ce50d658a4a8d4b2a56e5145527
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750859"
---
# <a name="compiler-error-c2814"></a>コンパイラ エラー C2814

'member' : ネイティブ型をマネージド型または WinRT 型の 'type' の中に入れ子にすることはできません

## <a name="example"></a>使用例

ネイティブ型を CLR 型または WinRT 型の中に入れ子にすることはできません。 次の例では、C2814 を生成し、その修正方法を示しています。

```cpp
// C2814.cpp
// compile with: /clr /c
ref class A {
   class B {};   // C2814
   ref class C {};   // OK
};
```
