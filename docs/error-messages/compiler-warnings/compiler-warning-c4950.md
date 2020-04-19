---
title: コンパイラの警告 C4950
ms.date: 11/04/2016
f1_keywords:
- C4950
helpviewer_keywords:
- C4950
ms.assetid: 50226a5c-c664-4d09-ac59-e9e874ca244f
ms.openlocfilehash: 784179af68ff55ba70c61255c88688105ecb1738
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208097"
---
# <a name="compiler-warning-c4950"></a>コンパイラの警告 C4950

'type_or_member': 廃止としてマークされています

メンバーまたは型がで obsolete としてマークされた、<xref:System.ObsoleteAttribute>属性。

C4950 は、常にエラーとして表示されます。 使用してこの警告をオフにすることができます、[警告](../../preprocessor/warning.md)プラグマ ディレクティブまたは[/wd](../../build/reference/compiler-option-warning-level.md)コンパイラ オプション。

## <a name="example"></a>例

次の例では C4950 が生成されます。

```cpp
// C4950.cpp
// compile with: /clr
using namespace System;

// Any reference to Func3 should generate an error with message
[System::ObsoleteAttribute("Will be removed in next version", true)]
Int32 Func3(Int32 a, Int32 b) {
   return (a + b);
}

int main() {
   Int32 MyInt3 = ::Func3(2, 2);   // C4950
}
```