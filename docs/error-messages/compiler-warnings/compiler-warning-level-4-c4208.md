---
title: コンパイラの警告 (レベル 4) C4208
ms.date: 11/04/2016
f1_keywords:
- C4208
helpviewer_keywords:
- C4208
ms.assetid: 5cb0a36e-3fb5-422f-a5f9-e40b70776c27
ms.openlocfilehash: c6e83feacd08bdb2203873a14a47ebde686a94f9
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991613"
---
# <a name="compiler-warning-level-4-c4208"></a>コンパイラの警告 (レベル 4) C4208

非標準の拡張機能が使用されています: delete [exp]-exp を評価しましたが無視

Microsoft 拡張機能 (/Ze) では、 [delete 演算子](../../cpp/delete-operator-cpp.md)を使用して、角かっこ内の値を使用して配列を削除できます。 この値は無視されます。

```cpp
// C4208.cpp
// compile with: /W4
int main()
{
   int * MyArray = new int[18];
   delete [18] MyArray;      // C4208
   MyArray = new int[18];
   delete [] MyArray;        // ok
}
```

ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) では、このような値は無効です。
