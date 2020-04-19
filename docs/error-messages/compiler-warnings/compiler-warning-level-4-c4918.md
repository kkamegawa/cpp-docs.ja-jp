---
title: コンパイラの警告 (レベル 4) C4918
ms.date: 11/04/2016
f1_keywords:
- C4918
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
ms.openlocfilehash: 801c22a45037492dc609d93c6339ab8feff30494
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988807"
---
# <a name="compiler-warning-level-4-c4918"></a>コンパイラの警告 (レベル 4) C4918

'character' : 無効な文字がプラグマ最適化リスト内にあります

[optimize](../../preprocessor/optimize.md) プラグマ ステートメントの最適化の一覧に、不明な文字が見つかりました。

たとえば、次のステートメントでは C4918 が生成されます。

```cpp
// C4918.cpp
// compile with: /W4
#pragma optimize("X", on) // C4918 expected
int main()
{
}
```
