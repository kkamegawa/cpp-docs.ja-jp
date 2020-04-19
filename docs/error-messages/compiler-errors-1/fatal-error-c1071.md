---
title: 致命的なエラー C1071
ms.date: 11/04/2016
f1_keywords:
- C1071
helpviewer_keywords:
- C1071
ms.assetid: 489f1786-370e-4ecd-af67-538fe6e5bd4e
ms.openlocfilehash: 2f39359d55b5564c6379c84f07e942cf3484e011
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747411"
---
# <a name="fatal-error-c1071"></a>致命的なエラー C1071

コメント内で予期しない EOF が見つかりました。

コメントのスキャン中に、コンパイラがファイルの末尾に到達しました。

### <a name="to-fix-by-checking-the-following-possible-causes"></a>次のような原因をチェックして問題を解決するには

1. コメント終端記号 (*/) がありません。

1. ソースファイルの最後の行にあるコメントの後に改行文字がありません。

次の例では、C1071 が生成されます。

```cpp
// C1071.cpp
int main() {
}

/* this comment is fine */
/* forgot the closing tag        // C1071
```
