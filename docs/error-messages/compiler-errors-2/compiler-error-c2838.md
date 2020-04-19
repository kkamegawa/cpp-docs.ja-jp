---
title: コンパイラ エラー C2838
ms.date: 11/04/2016
f1_keywords:
- C2838
helpviewer_keywords:
- C2838
ms.assetid: 176b2ad6-7a84-4019-b97e-328866054457
ms.openlocfilehash: 168f45a8cca8591d4780d056403de70440d25bec
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757840"
---
# <a name="compiler-error-c2838"></a>コンパイラ エラー C2838

' member ': メンバー宣言内の修飾名が無効です

クラス、構造体、または共用体は、別のクラス、構造体、または共用体のメンバーを再宣言するために、完全修飾名を使用します。

次の例では、C2838 が生成されます。

```cpp
// C2838.cpp
// compile with: /c
class Bellini {
public:
    void Norma();
};

class Bottesini {
   Bellini::Norma();  // C2838
};
```
