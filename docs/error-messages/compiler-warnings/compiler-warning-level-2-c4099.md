---
title: コンパイラの警告 (レベル 2) C4099
ms.date: 11/04/2016
f1_keywords:
- C4099
helpviewer_keywords:
- C4099
ms.assetid: 00bb803d-cae7-4ab8-8969-b46f54139ac8
ms.openlocfilehash: d685f1f40826b975623dbedc2ba8115c6b3edc45
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052179"
---
# <a name="compiler-warning-level-2-c4099"></a>コンパイラの警告 (レベル 2) C4099

' identifier ': ' objecttype1 ' を使用して最初に検出された型名は ' objecttype2 ' を使用して表示されるようになりました

構造体として宣言されたオブジェクトは、クラスとして定義されます。また、クラスとして宣言されたオブジェクトは、構造体として定義されます。 コンパイラは、定義で指定された型を使用します。

## <a name="example"></a>例

次の例では、C4099 が生成されます。

```cpp
// C4099.cpp
// compile with: /W2 /c
struct A;
class A {};   // C4099, use different identifer or use same object type
```