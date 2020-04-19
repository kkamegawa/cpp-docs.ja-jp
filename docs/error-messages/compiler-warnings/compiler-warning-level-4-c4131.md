---
title: コンパイラの警告 (レベル 4) C4131
ms.date: 11/04/2016
f1_keywords:
- C4131
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
ms.openlocfilehash: 266d62126d9154cd87706d3124e69e107bbdefde
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541575"
---
# <a name="compiler-warning-level-4-c4131"></a>コンパイラの警告 (レベル 4) C4131

'function': 旧スタイルの宣言が使われています

指定された関数の宣言は、プロトタイプ形式ではありません。

旧スタイルの関数の宣言をプロトタイプ形式に変換する必要があります。

旧スタイルの関数の宣言の例を次に示します。

```c
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

プロトタイプ形式の例を次に示します。

```c
void addrec( char *name, int id )
{ }
```