---
title: コンパイラの警告 (レベル 1) C4616
ms.date: 11/04/2016
f1_keywords:
- C4616
helpviewer_keywords:
- C4616
ms.assetid: 71e15265-c5bc-42ce-a6a9-4879892472b1
ms.openlocfilehash: 3c13eb28981779e2d089575660d8968c54e4e75f
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051475"
---
# <a name="compiler-warning-level-1-c4616"></a>コンパイラの警告 (レベル 1) C4616

\#プラグマ警告: 警告番号 ' number ' は有効なコンパイラ警告ではありません

[警告](../../preprocessor/warning.md)プラグマに指定された警告番号を再割り当てできません。 プラグマは無視されました。

次の例では、C4616 が生成されます。

```cpp
// C4616.cpp
// compile with: /W1 /c
#pragma warning( disable : 0 )   // C4616
#pragma warning( disable : 999 )   // OK
#pragma warning( disable : 4998 )   // OK
```