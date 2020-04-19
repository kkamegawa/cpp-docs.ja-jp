---
title: コンパイラの警告 (レベル 4) C4202
ms.date: 11/04/2016
f1_keywords:
- C4202
helpviewer_keywords:
- C4202
ms.assetid: 253293aa-97a3-4878-a2e8-c6cc9e20b1cb
ms.openlocfilehash: 0d5e7dd45b58f1231c39565bfd74c5895096a8b7
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541645"
---
# <a name="compiler-warning-level-4-c4202"></a>コンパイラの警告 (レベル 4) C4202

非標準の拡張機能が使用されています: '... ': プロトタイプのパラメーター名の一覧が正しくありません。

旧形式の関数定義には、可変個の引数が含まれています。 これらの定義は、ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) でエラーを生成します。

## <a name="example"></a>使用例

```c
// C4202.c
// compile with: /W4
void func( a, b, ...)   // C4202
int a, b;
{}

int main()
{
}
```