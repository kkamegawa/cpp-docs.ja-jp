---
title: コンパイラ エラー C2868
ms.date: 11/04/2016
f1_keywords:
- C2868
helpviewer_keywords:
- C2868
ms.assetid: 6ff5837b-e66d-44d1-9d17-80af35e08d08
ms.openlocfilehash: 4cb259ed0f43831226fb7e1a1ccf7b28bcef7819
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165204"
---
# <a name="compiler-error-c2868"></a>コンパイラ エラー C2868

> '*識別子*': using 宣言の構文上の誤り予期される修飾名。

A[宣言を使用して](../../cpp/using-declaration.md)が必要です、*修飾名*、スコープ演算子 (`::`) 区切り識別子名で終わる名前空間、クラス、または列挙型の名前のシーケンス。 1 つのスコープ解決演算子は、グローバル名前空間から名前を導入するために可能性があります。

## <a name="example"></a>例

次の例では、C2868 を生成し、また正しい使用法を示します。

```cpp
// C2868.cpp
class X {
public:
   int i;
};

class Y : X {
public:
   using X::i;   // OK
};

int main() {
   using X;   // C2868
}
```