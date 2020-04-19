---
title: コンパイラの警告 (レベル 4) C4234
ms.date: 11/04/2016
f1_keywords:
- C4234
helpviewer_keywords:
- C4234
ms.assetid: f7fecd5c-8248-4fde-8446-502aedc357ca
ms.openlocfilehash: 63a22fed0832677837eb786268fc92946d295b79
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541778"
---
# <a name="compiler-warning-level-4-c4234"></a>コンパイラの警告 (レベル 4) C4234

非標準の拡張機能が使用されています: ' keyword ' キーワードは将来使用するために予約

コンパイラは、使用したキーワードをまだ実装していません。

この警告は、自動的にエラーになります。 この動作を変更する場合は、 [#pragma 警告](../../preprocessor/warning.md)を使用します。 たとえば、C4234 をレベル4の警告問題にするには、次のようにします。

```cpp
#pragma warning(2:4234)
```

をソース コード ファイルに追加します。