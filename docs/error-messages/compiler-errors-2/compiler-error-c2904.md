---
title: コンパイラ エラー C2904
ms.date: 11/04/2016
f1_keywords:
- C2904
helpviewer_keywords:
- C2904
ms.assetid: d5802f2e-d3fc-473d-aa04-36957b4eaca5
ms.openlocfilehash: 506618da12af7d78db948f1a4197bf93367b7f7d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750599"
---
# <a name="compiler-error-c2904"></a>コンパイラ エラー C2904

'identifier': 名前は、現在のスコープで、テンプレートに対して使用されています。

重複する名前のコードを確認します。

次の例では C2904 が生成されます。

```cpp
// C2904.cpp
// compile with: /c
void X();  // X is declared as a function
template<class T> class X{};  // C2904
```
