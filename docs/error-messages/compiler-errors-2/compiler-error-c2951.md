---
title: コンパイラ エラー C2951
ms.date: 11/04/2016
f1_keywords:
- C2951
helpviewer_keywords:
- C2951
ms.assetid: c6f95aa2-c894-425b-a51c-d40d70c8daa1
ms.openlocfilehash: fdb837f8e9a9b769d470b70b962ce63d144161e1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755981"
---
# <a name="compiler-error-c2951"></a>コンパイラ エラー C2951

型宣言は、グローバル、名前空間、またはクラススコープでのみ許可されます

ジェネリッククラスまたはテンプレートクラスをグローバルまたは名前空間スコープの外部で宣言することはできません。 ジェネリックまたはテンプレート宣言をインクルードファイルで行う場合は、インクルードファイルがグローバルスコープにあることを確認してください。

次の例では、C2951 が生成されます。

```cpp
// C2951.cpp
template <class T>
class A {};

int main() {
   template <class T>   // C2951
   class B {};
}
```

C2951 は、ジェネリックを使用する場合にも発生する可能性があります。

```cpp
// C2951b.cpp
// compile with: /clr /c

// OK
generic <class T>
ref class GC { };

int main() {
   generic <class T> ref class GC2 {};   // C2951
}
```
