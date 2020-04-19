---
title: 致命的なエラー C1018
ms.date: 11/04/2016
f1_keywords:
- C1018
helpviewer_keywords:
- C1018
ms.assetid: 2ceb8a99-30b2-4b80-bf42-e9f3305b3c52
ms.openlocfilehash: 3273288f1d60fad840fd8e9c459ce5d209ddb6a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756930"
---
# <a name="fatal-error-c1018"></a>致命的なエラー C1018

予期しない #elif です。

`#elif` ディレクティブが、 `#if`、 `#ifdef`、または `#ifndef` コンストラクトの外側に置かれています。 `#elif` は、これらのコンストラクトのいずれかの内側だけで使用してください。

次の例では C1018 が生成されます。

```cpp
// C1018.cpp
#elif      // C1018
#endif

int main() {}
```

解決方法:

```cpp
// C1018b.cpp
#if 1
#elif
#endif

int main() {}
```
