---
title: コンパイラ エラー C2423
ms.date: 11/04/2016
f1_keywords:
- C2423
helpviewer_keywords:
- C2423
ms.assetid: 8797fb8b-b58b-4add-b6e6-2a9a3cd9084d
ms.openlocfilehash: 29203d3816f82bce95be656fdf71cb6536b325b9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74744668"
---
# <a name="compiler-error-c2423"></a>コンパイラ エラー C2423

' number ': 小数点以下桁数が正しくありません。

インラインアセンブリコードは、1、2、4、または8以外の数値を使用してレジスタをスケーリングします。

次の例では、C2423 が生成されます。

```cpp
// C2423.cpp
// processor: x86
int main() {
   _asm {
      lea EAX, [EAX*3]   // C2423
      lea EAX, [EAX+EAX*2]   // OK
   }
}
```
