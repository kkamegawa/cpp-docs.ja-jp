---
title: コンパイラ エラー C2593
ms.date: 11/04/2016
f1_keywords:
- C2593
helpviewer_keywords:
- C2593
ms.assetid: 4a0fe9bb-2163-447d-91f6-1890ed8250f6
ms.openlocfilehash: 2a385e35376ddce528678980705595bfb98aca95
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759348"
---
# <a name="compiler-error-c2593"></a>コンパイラ エラー C2593

' operator identifier ' があいまいです

オーバーロードされた演算子に対して、複数の使用可能な演算子が定義されています。

1つ以上の実際のパラメーターに対して明示的なキャストを使用すると、このエラーが解決される場合があります。

次の例では、C2593 が生成されます。

```cpp
// C2593.cpp
struct A {};
struct B : A {};
struct X {};
struct D : B, X {};
void operator+( X, X );
void operator+( A, B );
D d;

int main() {
   d +  d;         // C2593, D has an A, B, and X
   (X)d + (X)d;    // OK, uses operator+( X, X )
}
```

このエラーは、`CArchive` オブジェクトを使用して浮動小数点変数をシリアル化することによって発生することがあります。 コンパイラは `<<` 演算子をあいまいとして識別します。 `CArchive` シリアル化C++できるプリミティブ型は、固定サイズの型 `BYTE`、`WORD`、`DWORD`、および `LONG`だけです。 シリアル化のために、すべての整数型をこれらの型のいずれかにキャストする必要があります。 浮動小数点型は、`CArchive::Write()` メンバー関数を使用してアーカイブする必要があります。

次の例では、浮動小数点変数 (`f`) をアーカイブ `ar`にアーカイブする方法を示します。

```
ar.Write(&f, sizeof( float ));
```
