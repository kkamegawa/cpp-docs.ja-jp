---
title: コンパイラの警告 (レベル 1) C4628
ms.date: 11/04/2016
f1_keywords:
- C4628
helpviewer_keywords:
- C4628
ms.assetid: 20fdc6f8-5f6a-40cc-aff8-c7ccf3d8ec26
ms.openlocfilehash: 6063755db5ac517d868bc47d2c417356ccef5d58
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051442"
---
# <a name="compiler-warning-level-1-c4628"></a>コンパイラの警告 (レベル 1) C4628

digraphs は -Ze でサポートされていません。 文字のシーケンス 'digraph' は 'char' の代替トークンとして解釈されません。

[/Ze](../../build/reference/za-ze-disable-language-extensions.md)では digraphs はサポートされていません。 この警告の後にエラーが表示されます。

既定では、この警告はオフに設定されています。 詳細については、「 [既定で無効になっているコンパイラ警告](../../preprocessor/compiler-warnings-that-are-off-by-default.md) 」を参照してください。

次の例では、C4628 が生成されます。

```cpp
// C4628.cpp
// compile with: /WX
#pragma warning(default : 4628)
int main()
<%   // C4628 <% digraph for {
}
```