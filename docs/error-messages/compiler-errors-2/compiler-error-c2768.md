---
title: コンパイラエラー C2768
ms.date: 11/04/2016
f1_keywords:
- C2768
helpviewer_keywords:
- C2768
ms.assetid: a7f6047a-6a80-4737-ad5c-c12868639fb5
ms.openlocfilehash: bcc801bb5802598e936d577f08729214bb7e13a1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759790"
---
# <a name="compiler-error-c2768"></a>コンパイラエラー C2768

' function ': 明示的なテンプレート引数が不適切に使用しています

コンパイラは、関数定義が関数テンプレートの明示的な特殊化であることが想定されていたか、または関数定義が新しい関数に対して想定されているかどうかを判断できませんでした。

このエラーは、コンパイラ準拠の強化の一環として、Visual Studio .NET 2003 で導入されました。

次の例では、C2768 が生成されます。

```cpp
// C2768.cpp
template<typename T>
void f(T) {}

void f<int>(int) {}   // C2768

// an explicit specialization
template<>
void f<int>(int) {}

// global nontemplate function overload
void f(int) {}
```
