---
title: コンパイラ エラー C2337
ms.date: 09/19/2019
f1_keywords:
- C2337
helpviewer_keywords:
- C2337
ms.assetid: eccc9178-a15e-42cd-bbd0-3cea7cf2d55b
ms.openlocfilehash: bf9b3e782804add13aeaef0e6672d2dd66d193be
ms.sourcegitcommit: f907b15f50a6b945d0b87c03af0050946157d701
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/20/2019
ms.locfileid: "71158771"
---
# <a name="compiler-error-c2337"></a>コンパイラ エラー C2337

> '*attribute name*': 属性が見つかりません

コードでは、このコンテキストでサポートされていない属性を使用しています。 または、このバージョンのコンパイラでは属性を使用できません。 この問題を解決するには、サポートされていない属性を削除します。

次の例では C2337 が生成されます。

```cpp
// C2337.cpp
// compile with: /c
[emitidl];
[module(name="x")];
[grasshopper]   // C2337, not a supported attribute
class a{};
```
