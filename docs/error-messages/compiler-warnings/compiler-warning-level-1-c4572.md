---
title: コンパイラの警告 (レベル 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: 52285f391af0a8028307cbbc320af33f9cb1fca5
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965954"
---
# <a name="compiler-warning-level-1-c4572"></a>コンパイラの警告 (レベル 1) C4572

[ParamArray] 属性は/clr で非推奨とされます。 '... ' を使用してください。その代わりに

可変個引数リストを指定するための古いスタイルが使用されました。 CLR に対してコンパイルする場合は、<xref:System.ParamArrayAttribute>の代わりに省略記号構文を使用します。 詳細については、「[可変個引数リスト (..C++.) (/cli)](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)」を参照してください。

## <a name="example"></a>例

次の例では、C4572 が生成されます。

```cpp
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```