---
title: コンパイラの警告 (レベル 1) C4829
ms.date: 11/04/2016
f1_keywords:
- C4829
helpviewer_keywords:
- C4829
ms.assetid: 4ffabe2b-2ddc-4c52-8564-d1355c93cfa6
ms.openlocfilehash: e8765f206d099f808ab261fbbde19273e46b5c90
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051236"
---
# <a name="compiler-warning-level-1-c4829"></a>コンパイラの警告 (レベル 1) C4829

関数 main への正しくないパラメーターである可能性があります。 ' Intmain (Platform:: Array\<Platform:: String ^ > ^ argv) ' を検討してください

main などの特定の関数は、参照型パラメーターを受け取れません。 コンパイルは成功しても、結果のイメージは実行できない場合があります。

次の例では C4829 が生成されます。

```cpp
// C4829.cpp
// compile by using: cl /EHsc /ZW /W4 /c C4829.cpp
int main(Platform::String ^ s) {}   // C4829
```