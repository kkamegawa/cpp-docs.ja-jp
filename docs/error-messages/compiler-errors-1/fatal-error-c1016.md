---
title: 致命的なエラー C1016
ms.date: 11/04/2016
f1_keywords:
- C1016
helpviewer_keywords:
- C1016
ms.assetid: 33f45c3e-2d8f-43ad-a445-c412d1d54ce1
ms.openlocfilehash: b5774503297c596a351d72f3af4de6040628b078
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756956"
---
# <a name="fatal-error-c1016"></a>致命的なエラー C1016

\#ifdef で識別子 # ifndef が必要ですが、識別子が必要です

条件付きコンパイル ディレクティブ ([#ifdef](../../preprocessor/hash-ifdef-and-hash-ifndef-directives-c-cpp.md) または `#ifndef`) に、評価する識別子が指定されていません。 このエラーを解決するには、識別子を指定してください。

次の例では C1016 が生成されます。

```cpp
// C1016.cpp
#ifdef   // C1016
#define FC1016
#endif

int main() {}
```

解決方法:

```cpp
// C1016b.cpp
#ifdef X
#define FC1016
#endif

int main() {}
```
