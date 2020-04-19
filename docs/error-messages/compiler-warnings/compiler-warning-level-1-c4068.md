---
title: コンパイラの警告 (レベル 1) C4068
ms.date: 11/04/2016
f1_keywords:
- C4068
helpviewer_keywords:
- C4068
ms.assetid: 96a7397a-4eab-44ab-b3bb-36747503f7e5
ms.openlocfilehash: ba6e57fb954e0331e8eede5e7859fbeed5ce6424
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73626927"
---
# <a name="compiler-warning-level-1-c4068"></a>コンパイラの警告 (レベル 1) C4068

不明なプラグマがありました。

コンパイラで、認識できない [プラグマ](../../preprocessor/pragma-directives-and-the-pragma-keyword.md)が無視されました。 この **プラグマ** が使用中のコンパイラで許可されていることを確認してください。 次の例では C4068 が生成されます。

```cpp
// C4068.cpp
// compile with: /W1
#pragma NotAValidPragmaName   // C4068, use valid name to resolve
int main()
{
}
```