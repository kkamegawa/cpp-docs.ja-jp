---
title: コンパイラの警告 (レベル 4) C4214
ms.date: 11/04/2016
f1_keywords:
- C4214
helpviewer_keywords:
- C4214
ms.assetid: 9b8db279-1f12-4a6b-a923-2db22acd1947
ms.openlocfilehash: 85f37810708eff43574129f42dd8444fe7dc37c2
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541898"
---
# <a name="compiler-warning-level-4-c4214"></a>コンパイラの警告 (レベル 4) C4214

非標準の拡張機能が使用されています: int 以外のビットフィールド型

既定の Microsoft 拡張機能 (/Ze) では、ビットフィールド構造体のメンバーは任意の整数型にすることができます。

## <a name="example"></a>使用例

```c
// C4214.c
// compile with: /W4
struct bitfields
{
   unsigned short j:4;  // C4214
};

int main()
{
}
```

ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では、このようなビットフィールドは無効です。