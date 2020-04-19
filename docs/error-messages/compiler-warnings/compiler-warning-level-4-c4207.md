---
title: コンパイラの警告 (レベル 4) C4207
ms.date: 11/04/2016
f1_keywords:
- C4207
helpviewer_keywords:
- C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
ms.openlocfilehash: bd18964f8969bc75967de435e2ca3099b12213e0
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541881"
---
# <a name="compiler-warning-level-4-c4207"></a>コンパイラの警告 (レベル 4) C4207

非標準の拡張機能が使用されています: 拡張初期化子フォーム

Microsoft 拡張機能 (/Ze) では、中かっこ内の文字列を使用して `char` の可変長配列を初期化できます。

## <a name="example"></a>使用例

```c
// C4207.c
// compile with: /W4
char c[] = { 'a', 'b', "cdefg" }; // C4207

int main()
{
}
```

このような初期化は、ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では無効です。