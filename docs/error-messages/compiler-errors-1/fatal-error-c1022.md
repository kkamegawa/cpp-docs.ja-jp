---
title: 致命的なエラー C1022
ms.date: 11/04/2016
f1_keywords:
- C1022
helpviewer_keywords:
- C1022
ms.assetid: edada720-dc73-49bc-bd93-a7945a316312
ms.openlocfilehash: b709d4bd855e38cb3721dec6d09b95ed02454def
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756878"
---
# <a name="fatal-error-c1022"></a>致命的なエラー C1022

#endif が必要です。

`#if`、 `#ifdef`、 `#ifndef` の各ディレクティブに対応する `#endif` ディレクティブがありません。 各 `#if`、 `#ifdef`、 `#ifndef` に対応する `#endif`を指定してください。

次の例では C1022 が生成されます。

```cpp
// C1022.cpp
#define true 1

#if (true)
#else
#else    // C1022
```

解決方法:

```cpp
// C1022b.cpp
// compile with: /c
#define true 1

#if (true)
#else
#endif
```
