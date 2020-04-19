---
title: コンパイラ エラー C2530
ms.date: 11/04/2016
f1_keywords:
- C2530
helpviewer_keywords:
- C2530
ms.assetid: b790a312-48df-4a6a-9e27-be2c5f32f16c
ms.openlocfilehash: 0816fcb4d9e2a3e6588dfcf937383fed7ab11395
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74737128"
---
# <a name="compiler-error-c2530"></a>コンパイラ エラー C2530

' identifier ': 参照を初期化する必要があります

宣言されている場合を除き、参照を初期化する必要があります。

- キーワード[extern](../../cpp/using-extern-to-specify-linkage.md)を使用します。

- クラス、構造体、または共用体のメンバーとして (およびコンストラクターで初期化されます)。

- 関数の宣言または定義のパラメーターとして。

- 関数の戻り値の型として。

次の例では、C2530 が生成されます。

```cpp
// C2530.cpp
int main() {
   int i = 0;
   int &j;   // C2530
   int &k = i;   // OK
}
```
