---
title: コンパイラ エラー C3388
ms.date: 11/04/2016
f1_keywords:
- C3388
helpviewer_keywords:
- C3388
ms.assetid: 34336545-ed13-4d81-ab5f-f869799fe4c2
ms.openlocfilehash: bb2a847c24b2a0b7829008793f311459e76587f4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758347"
---
# <a name="compiler-error-c3388"></a>コンパイラ エラー C3388

'type': 制約として使用できません。解析を続行するために 'ref class' を使用します

ジェネリック型で制約が指定されましたが、正しく指定されませんでした。 詳細については、「[ジェネリック型パラメーターの制約 (C++/cli)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では C3388 が生成されます。

```cpp
// C3388.cpp
// compile with: /clr /c
interface class AA {};

generic <class T>
where T : interface class   // C3388
ref class C {};

// OK
generic <class T>
where T : AA
ref class D {};
```
