---
title: コンパイラ エラー C3551
ms.date: 11/04/2016
f1_keywords:
- C3551
helpviewer_keywords:
- C3551
ms.assetid: c8ee23da-6568-40db-93a6-3ddb7ac47712
ms.openlocfilehash: 48b378eb734c5830bedbf417d99d34955e2e6d0f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62375978"
---
# <a name="compiler-error-c3551"></a>コンパイラ エラー C3551

"遅延指定の戻り値の型が必要です"

関数の戻り値の型のプレース ホルダーとして `auto` キーワードを使用する場合は、遅延指定の戻り値の型を指定する必要があります。 次の例では、関数 `myFunction` の遅延指定の戻り値の型は、型 `int`の 4 つの要素の配列へのポインターです。

```
auto myFunction()->int(*)[4];
```

## <a name="see-also"></a>関連項目

[auto](../../cpp/auto-cpp.md)