---
title: コンパイラエラー C2006
ms.date: 11/04/2016
f1_keywords:
- C2006
helpviewer_keywords:
- C2006
ms.assetid: caaed6f7-ceb9-4742-8820-d66657c0b04d
ms.openlocfilehash: 64f81929916cd3a4adf38a302ea34d46d9a5c070
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756553"
---
# <a name="compiler-error-c2006"></a>コンパイラエラー C2006

' ディレクティブ ' にはファイル名が必要ですが、' token ' が見つかりました。

[#Include](../../preprocessor/hash-include-directive-c-cpp.md)や[#import](../../preprocessor/hash-import-directive-cpp.md)などのディレクティブにはファイル名が必要です。 このエラーを解決するには、*トークン*が有効なファイル名であることを確認します。 また、ファイル名を二重引用符または山かっこで囲みます。

次の例では、C2006 が生成されます。

```cpp
// C2006.cpp
#include stdio.h   // C2006
```

解決方法:

```cpp
// C2006b.cpp
// compile with: /c
#include <stdio.h>
```
