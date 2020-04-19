---
title: コンパイラエラー C2086
ms.date: 11/04/2016
f1_keywords:
- C2086
helpviewer_keywords:
- C2086
ms.assetid: 4329bf72-90c8-444c-8524-4ef75e6b2139
ms.openlocfilehash: 417763e8c26918d3cd83702b283244d1c13d9d1f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735750"
---
# <a name="compiler-error-c2086"></a>コンパイラエラー C2086

' identifier ': 再定義

識別子が2回以上定義されているか、それ以降の宣言が前の宣言と異なっています。

C2086 は、参照C#されたアセンブリのインクリメンタルビルドの結果である場合もあります。 このエラー C#を解決するには、アセンブリをリビルドしてください。

次の例では、C2086 が生成されます。

```cpp
// C2086.cpp
main() {
  int a;
  int a;   // C2086 not an error in ANSI C
}
```
