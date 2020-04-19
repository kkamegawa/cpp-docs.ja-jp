---
title: コンパイラの警告 (レベル 4) C4211
ms.date: 11/04/2016
f1_keywords:
- C4211
helpviewer_keywords:
- C4211
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
ms.openlocfilehash: 6387f58430098e49e7add25e8915bf6b181634e9
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541843"
---
# <a name="compiler-warning-level-4-c4211"></a>コンパイラの警告 (レベル 4) C4211

非標準の拡張が使用されています: extern を static に再定義します

既定の Microsoft 拡張機能 (/Ze) では、`extern` 識別子を**static**として再定義できます。

## <a name="example"></a>使用例

```c
// C4211.c
// compile with: /W4
extern int i;
static int i;   // C4211

int main()
{
}
```

このような再定義は ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では無効です。
