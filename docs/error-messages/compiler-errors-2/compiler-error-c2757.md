---
title: コンパイラエラー C2757
ms.date: 11/04/2016
f1_keywords:
- C2757
helpviewer_keywords:
- C2757
ms.assetid: 421f102f-8a32-4d47-a109-811ddf2c909d
ms.openlocfilehash: a9f4661495e0fa5219a517b6f6ca410323a77269
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759530"
---
# <a name="compiler-error-c2757"></a>コンパイラエラー C2757

' symbol ': この名前のシンボルは既に存在するため、この名前を名前空間名として使用することはできません

現在のコンパイルで名前空間識別子として使用されているシンボルは、参照されたアセンブリで既に使用されています。

次の例では、C2757 が生成されます。

```cpp
// C2757a.cpp
// compile with: /clr /LD
public ref class Nes {};
```

この場合、次のようになります。

```cpp
// C2757b.cpp
// compile with: /clr /c
#using <C2757a.dll>

namespace Nes {    // C2757
// try the following line instead
// namespace Nes2 {
   public ref class X {};
}
```
