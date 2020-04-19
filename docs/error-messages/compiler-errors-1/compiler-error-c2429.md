---
title: コンパイラ エラー C2429
ms.date: 11/16/2017
f1_keywords:
- C2429
helpviewer_keywords:
- C2429
ms.assetid: 57ff6df9-5cf1-49f3-8bd8-4e550dfd65a0
ms.openlocfilehash: a5d1e98e91c541729a93f731eede9b047589c63a
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447987"
---
# <a name="compiler-error-c2429"></a>コンパイラ エラー C2429

> '*言語機能*'コンパイラ フラグが必要です'*コンパイラ オプション*'

言語機能には、サポートの特定のコンパイラ オプションが必要です。

エラー **C2429: 言語機能 '入れ子になった名前空間の定義' コンパイラ フラグが必要です '/std:c++17'** 定義しようとする場合に生成される、*複合名前空間*、1 つまたは複数を含む名前空間Visual Studio 2015 の Update 5 で始まる名前空間のスコープに入れ子にされた名。 (Visual Studio 2017 バージョン 15.3 で、 **/std:c++latest*スイッチが必要です)。C++17 の前に定義が C++ では許可されません。 名前空間を合成します。 コンパイラは、複合名前空間の定義をサポートしているときに、 [/std:c++17](../../build/reference/std-specify-language-standard-version.md)コンパイラ オプションが指定されて。

```cpp
// C2429a.cpp
namespace a::b { int i; } // C2429 starting in Visual Studio 2015 Update 3.
                          // Use /std:c++17 to fix, or do this:
// namespace a { namespace b { int i; }}

int main() {
   a::b::i = 2;
}
```
