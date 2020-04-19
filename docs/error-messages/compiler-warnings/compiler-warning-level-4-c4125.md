---
title: コンパイラの警告 (レベル 4) C4125
ms.date: 11/04/2016
f1_keywords:
- C4125
helpviewer_keywords:
- C4125
ms.assetid: a081d1f4-0789-4915-91df-7ff0b28ca245
ms.openlocfilehash: f194f0efc8012bf027e4785c2f398a0a7027b368
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991579"
---
# <a name="compiler-warning-level-4-c4125"></a>コンパイラの警告 (レベル 4) C4125

8 進数のエスケープ シーケンスが、10 進数のところで中断されました。

コンパイラは、10 進数を含まない 8 進数を評価し、10 進数を文字と見なします。

## <a name="example"></a>使用例

```cpp
// C4125a.cpp
// compile with: /W4
char array1[] = "\709"; // C4125
int main()
{
}
```

数字 9 を文字として使用する場合は、次のように例を修正します。

```cpp
// C4125b.cpp
// compile with: /W4
char array[] = "\0709";  // C4125 String containing "89"
int main()
{
}
```
