---
title: コンパイラエラー C2755
ms.date: 11/04/2016
f1_keywords:
- C2755
helpviewer_keywords:
- C2755
ms.assetid: 8ee4eeb6-4757-4efe-9100-38ff4a96f1de
ms.openlocfilehash: fcd4bb5d49f6f6e807ad240c377debb220138c93
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759556"
---
# <a name="compiler-error-c2755"></a>コンパイラエラー C2755

' param ': 部分的特殊化の非型パラメーターは、単純な識別子でなければなりません

非型パラメーターは、単純な識別子である必要があります。これは、コンパイル時にコンパイラが単一の識別子または定数値に解決できるものです。

次の例では、C2755 が生成されます。

```cpp
// C2755.cpp
template<int I, int J>
struct A {};

template<int I>
struct A<I,I*5> {};   // C2755
// try the following line instead
// struct A<I,5> {};
```
