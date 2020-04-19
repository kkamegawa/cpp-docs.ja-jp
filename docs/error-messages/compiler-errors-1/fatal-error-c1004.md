---
title: 致命的なエラー C1004
ms.date: 11/04/2016
f1_keywords:
- C1004
helpviewer_keywords:
- C1004
ms.assetid: dbe034b0-6eb0-41b4-a50c-2fccf9e78ad4
ms.openlocfilehash: 82a1a3e410505be53d4356e46d5521aebb72763c
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756969"
---
# <a name="fatal-error-c1004"></a>致命的なエラー C1004

予期しないファイルの終わりが見つかりました

コンパイラは、コンストラクトを解決せずにソースファイルの末尾に到達しました。 次のいずれかの要素がコードに含まれていない可能性があります。

- 右中かっこ

- 右かっこ

- 終了コメントマーカー (*/)

- セミコロン

このエラーを解決するには、次のことを確認します。

- 既定のディスクドライブには、一時ファイル用に十分な領域がありません。そのためには、ソースファイルと比べて約2倍の領域が必要になります。

- False に評価される `#if` ディレクティブには、`#endif` ディレクティブが不足しています。

- ソースファイルがキャリッジリターンとラインフィードで終了していません。

次の例では、C1004 が生成されます。

```cpp
// C1004.cpp
#if TEST
int main() {}
// C1004
```

解決方法:

```cpp
// C1004b.cpp
#if TEST
#endif

int main() {}
```
