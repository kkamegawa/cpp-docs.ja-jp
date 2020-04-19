---
title: コンパイラの警告 (レベル 3) C4638
ms.date: 08/27/2018
f1_keywords:
- C4638
helpviewer_keywords:
- C4638
ms.assetid: 2c07923a-e103-4e40-bd11-fdfed428a5ec
ms.openlocfilehash: 1bdd7541e16f5c02756678ae78a777094b5fe588
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62401659"
---
# <a name="compiler-warning-level-3-c4638"></a>コンパイラの警告 (レベル 3) C4638

> XML ドキュメント コメント対象: 不明なシンボルへの参照を '*シンボル*'

## <a name="remarks"></a>Remarks

コンパイラがシンボル (*symbol*) を解決できませんでした。 シンボルはコンパイルで有効である必要があります。

## <a name="example"></a>例

次の例では C4638 が生成されます。

```cpp
// C4638.cpp
// compile with: /clr /doc /LD /W3
using namespace System;

/// Text for class MyClass.
public ref class MyClass {
public:
   /// <summary> Text </summary>
   /// <see cref="aSymbolThatAppearsNowhereInMyProject"/>
   // Try the following line instead:
   // /// <see cref="System::Console::WriteLine"/>
   void MyMethod() {}
};   // C4638
```