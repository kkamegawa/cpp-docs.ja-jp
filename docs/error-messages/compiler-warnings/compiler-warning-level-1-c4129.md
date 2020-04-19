---
title: コンパイラの警告 (レベル 1) C4129
ms.date: 11/04/2016
f1_keywords:
- C4129
helpviewer_keywords:
- C4129
ms.assetid: a4190c64-4bfb-48fd-8e98-52720bc0d878
ms.openlocfilehash: ab3108c60c18276e8e4797c7cfde1b66535dbaaa
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627423"
---
# <a name="compiler-warning-level-1-c4129"></a>コンパイラの警告 (レベル 1) C4129

' character ': 認識できない文字エスケープシーケンスです。

文字または文字列定数内の円記号 (\\) に続く `character` は、有効なエスケープシーケンスとして認識されません。 円記号は無視され、印刷されません。 円記号の後に続く文字が出力されます。

1つの円記号を印刷するには、2つの円記号 (\\\\) を指定します。

セクションC++ 2.13.2 の標準では、エスケープシーケンスについて説明しています。

次の例では、C4129 が生成されます。

```cpp
// C4129.cpp
// compile with: /W1
int main() {
   char array1[] = "\/709";   // C4129
   char array2[] = "\n709";   // OK
}
```