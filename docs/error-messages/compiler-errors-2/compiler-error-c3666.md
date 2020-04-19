---
title: コンパイラ エラー C3666
ms.date: 11/04/2016
f1_keywords:
- C3666
helpviewer_keywords:
- C3666
ms.assetid: 459e51dd-cefb-4346-99b3-644f2d8b65b2
ms.openlocfilehash: 990dea32b2928671f426235138698071fe038f63
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758152"
---
# <a name="compiler-error-c3666"></a>コンパイラ エラー C3666

' constructor ': オーバーライド指定子 ' keyword ' はコンストラクターでは使用できません

オーバーライド指定子がコンストラクターで使用されましたが、これは許可されていません。 詳細については、「[オーバーライド指定子](../../extensions/override-specifiers-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3666 が生成されます。

```cpp
// C3666.cpp
// compile with: /clr /c
ref struct R {
   R() new {}   // C3666
   R(int i) {}   // OK
};
```
