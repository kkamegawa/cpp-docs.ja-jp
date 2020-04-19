---
title: コンパイラの警告 (レベル 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: 5e8b546e4eb4b60197db504382b3230e779b1dec
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/12/2019
ms.locfileid: "70924847"
---
# <a name="compiler-warning-level-4-c4295"></a>コンパイラの警告 (レベル 4) C4295

> '*array*': 配列が小さすぎるため、終端の null 文字を含めることができません

配列は初期化されましたが、配列の最後の文字が null ではありません。配列に文字列としてアクセスすると、予期しない結果が生じる可能性があります。

## <a name="example"></a>例

次の例では、C4295 が生成されます。 この問題を解決するには、配列のサイズを大きく宣言し、初期化子文字列から終端の null を保持するか、配列初期化子リストを使用して、これが null で終わる`char`文字列ではなくの配列であることを明確にすることができます。

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
