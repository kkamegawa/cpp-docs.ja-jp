---
title: コンパイラの警告 (レベル 1) C4794
ms.date: 11/04/2016
f1_keywords:
- C4794
helpviewer_keywords:
- C4794
ms.assetid: badc9c36-fa1a-4fec-929b-7bfda7a7b79f
ms.openlocfilehash: 7d669280c0dc6a730a22480e602dac8cc6153449
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052376"
---
# <a name="compiler-warning-level-1-c4794"></a>コンパイラの警告 (レベル 1) C4794

スレッドのローカル ストレージ変数 'variable' のセグメントが 'section name' から '.tls$' に変更されました

tls 変数を .tls$ で始まっていないセクションに配置するために [#pragma data_seg](../../preprocessor/data-seg.md) を使用しました。

.tls$*x* セクションは、 [__declspec(thread)](../../cpp/thread.md) 変数が定義されているオブジェクト ファイルに存在します。 EXE または DLL の .tls セクションはこれらのセクションから生成されます。

## <a name="example"></a>例

次の例では C4794 が生成されます。

```cpp
// C4794.cpp
// compile with: /W1 /c
#pragma data_seg(".someseg")
__declspec(thread) int i;   // C4794

// OK
#pragma data_seg(".tls$9")
__declspec(thread) int j;
```