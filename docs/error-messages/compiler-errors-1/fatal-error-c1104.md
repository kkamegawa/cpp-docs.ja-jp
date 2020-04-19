---
title: 致命的なエラー C1104
ms.date: 11/04/2016
f1_keywords:
- C1104
helpviewer_keywords:
- C1104
ms.assetid: 45bd85c4-77d3-4d3c-b167-49c563aefb4d
ms.openlocfilehash: a26e65e98b44a69eb14daf6d835fafb23362dfa2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747333"
---
# <a name="fatal-error-c1104"></a>致命的なエラー C1104

libid をインポート中の致命的なエラー: 'message'

コンパイラがタイプ ライブラリのインポートで問題を検出しました。  たとえば、libid を持つタイプ ライブラリを指定し、さらに `no_registry`を指定することはできません。

詳細については、「 [#import ディレクティブ](../../preprocessor/hash-import-directive-cpp.md)」を参照してください。

次の例では C1104 エラーが生成されます。

```cpp
// C1104.cpp
#import "libid:11111111.1111.1111.1111.111111111111" version("4.0") lcid("9") no_registry auto_search   // C1104
```
