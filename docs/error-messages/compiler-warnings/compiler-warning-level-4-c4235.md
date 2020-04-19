---
title: コンパイラの警告 (レベル 4) C4235
ms.date: 11/04/2016
f1_keywords:
- C4235
helpviewer_keywords:
- C4235
ms.assetid: d4214799-d62c-4674-b4e2-9e201c303303
ms.openlocfilehash: 3e3cb2e40ed42b24ee52252003b26ec09cd86710
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541759"
---
# <a name="compiler-warning-level-4-c4235"></a>コンパイラの警告 (レベル 4) C4235

非標準の拡張機能が使用されています : 'キーワード' キーワードはこのアーキテクチャではサポートされていません

使用したキーワードは、サポートされていません。

この警告は、自動的にエラーになります。 この動作を変更する場合は、 [#pragma 警告](../../preprocessor/warning.md)を使用します。 たとえば、C4235 でレベル 2 の警告を発行させるには、

```cpp
#pragma warning(2:4235)
```

をソース コード ファイルに追加します。