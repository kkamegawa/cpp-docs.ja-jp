---
title: コンパイラ エラー C2504
ms.date: 11/04/2016
f1_keywords:
- C2504
helpviewer_keywords:
- C2504
ms.assetid: c9e002a6-a4ee-4ba7-970e-edf4adb83692
ms.openlocfilehash: d47d99962d089d873cb9bbdf9baac7eab706fc16
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74746891"
---
# <a name="compiler-error-c2504"></a>コンパイラ エラー C2504

' class ': 基底クラスが定義されていません。

基底クラスが宣言されていますが、定義されていません。  次の原因が考えられます。

1. インクルードファイルがありません。

1. 外部基底クラスが[extern](../../cpp/using-extern-to-specify-linkage.md)で宣言されていません。

次の例では、C2504 が生成されます。

```cpp
// C2504.cpp
// compile with: /c
class A;
class B : public A {};   // C2504
```

わかりました

```
class C{};
class D : public C {};
```
