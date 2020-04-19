---
title: コンパイラエラー C2719
ms.date: 11/04/2016
f1_keywords:
- C2719
helpviewer_keywords:
- C2719
ms.assetid: ea6236d3-8286-45cc-9478-c84ad3dd3c8e
ms.openlocfilehash: 574a04923c20c3104083a6aa05a71838e7ec13d2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760505"
---
# <a name="compiler-error-c2719"></a>コンパイラエラー C2719

'parameter': __declspec(align('#')) の仮引数はアラインされません。

[Align](../../cpp/align-cpp.md) `__declspec` 修飾子は、関数パラメーターでは許可されていません。 関数パラメーターのアラインメントは、呼び出し規則によって制御されます。 詳細については、「[呼び出し規則](../../cpp/calling-conventions.md)」を参照してください。

次の例は C2719 を生成し、その修正方法を示しています。

```cpp
// C2719.cpp
void func(int __declspec(align(32)) i);   // C2719
// try the following line instead
// void func(int i);
```
