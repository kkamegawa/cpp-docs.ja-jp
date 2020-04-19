---
title: コンパイラ エラー C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 52c4f3a393ffaf2b61a65c8e2e0dcc8efac08288
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380943"
---
# <a name="compiler-error-c3851"></a>コンパイラ エラー C3851

> '*char*': ユニバーサル文字名は基本文字セット内の文字を指定できません

## <a name="remarks"></a>Remarks

C++ としてコンパイルされるコードでは、基本ソース文字セットの文字を表すユニバーサル文字名を使用できません (文字列リテラルまたは文字リテラルの場合を除く)。 詳細については、「 [Character Sets](../../cpp/character-sets.md)」を参照してください。 C としてコンパイルされたコードで使うことはできません、ユニバーサル文字名を範囲 0x20 から 0x7f、0x24 ('$') を除く、包括的で 0x40 ('\@')、または 0x60 ('\`')。

## <a name="example"></a>例

次の例では、C3851 が生成され、その修正方法が表示されます。

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```