---
title: コンパイラ エラー C2341
ms.date: 11/04/2016
f1_keywords:
- C2341
helpviewer_keywords:
- C2341
ms.assetid: aa2a7da5-e1c8-4225-9939-5bdc50158f31
ms.openlocfilehash: 6147ce954c6d21d86f76d1fd8ec6b8a1a5070a12
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760050"
---
# <a name="compiler-error-c2341"></a>コンパイラ エラー C2341

' section name ': セグメントは、使用する前に #pragma data_seg、code_seg またはセクションを使用して定義する必要があります

[Allocate](../../cpp/allocate.md)ステートメントが、 [code_seg](../../preprocessor/code-seg.md)、 [data_seg](../../preprocessor/data-seg.md)、または[section](../../preprocessor/section.md)プラグマによってまだ定義されていないセグメントを参照しています。

次の例では、C2341 が生成されます。

```cpp
// C2341.cpp
// compile with: /c
__declspec(allocate(".test"))   // C2341
int j = 1;
```

解決方法:

```cpp
// C2341b.cpp
// compile with: /c
#pragma data_seg(".test")
__declspec(allocate(".test"))
int j = 1;
```
