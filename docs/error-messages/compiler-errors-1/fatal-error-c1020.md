---
title: 致命的なエラー C1020
ms.date: 11/04/2016
f1_keywords:
- C1020
helpviewer_keywords:
- C1020
ms.assetid: 42f429e2-5e3b-4086-a10d-b99e032e51c5
ms.openlocfilehash: 67cf5067c85d07215f6391d9e5d3d1bcb4978e42
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756904"
---
# <a name="fatal-error-c1020"></a>致命的なエラー C1020

予期しない #endif です。

`#endif` ディレクティブに対応する `#if`、 `#ifdef`、または `#ifndef` のディレクティブがありません。 各 `#endif` には対応するディレクティブを指定してください。

次の例では C1020 が生成されます。

```cpp
// C1020.cpp
#endif     // C1020
```

解決方法:

```cpp
// C1020b.cpp
// compile with: /c
#if 1
#endif
```
