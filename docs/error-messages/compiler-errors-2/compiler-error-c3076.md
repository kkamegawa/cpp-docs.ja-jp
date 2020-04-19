---
title: コンパイラ エラー C3076
ms.date: 11/04/2016
f1_keywords:
- C3076
helpviewer_keywords:
- C3076
ms.assetid: 8a87b3e4-2c17-4b87-9622-ef0962d6a34e
ms.openlocfilehash: f3ce849113b0fc21a192f748bc46fc35be48880d
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74749634"
---
# <a name="compiler-error-c3076"></a>コンパイラ エラー C3076

' instance ': 参照型 ' type ' のインスタンスをネイティブ型に埋め込むことはできません

ネイティブ型に CLR 型のインスタンスを含めることはできません。

詳細については、「 [ C++参照型のスタックセマンティクス](../../dotnet/cpp-stack-semantics-for-reference-types.md)」を参照してください。

## <a name="example"></a>使用例

次の例では、C3076 が生成されます。

```cpp
// C3076.cpp
// compile with: /clr /c
ref struct U {};

struct V {
   U y;   // C3076
};

ref struct W {
   U y;   // OK
};
```
