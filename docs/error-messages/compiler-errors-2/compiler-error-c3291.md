---
title: コンパイラ エラー C3291
ms.date: 11/04/2016
f1_keywords:
- C3291
helpviewer_keywords:
- C3291
ms.assetid: ed2e9f89-8dbc-4387-bc26-cc955e840858
ms.openlocfilehash: eb98be3677de6c93fdb7bedf7c0d482115891697
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760141"
---
# <a name="compiler-error-c3291"></a>コンパイラ エラー C3291

'default': trivial プロパティの名前にすることはできません

trivial プロパティに `default`という名前を付けることはできません。 詳細については、「 [property](../../extensions/property-cpp-component-extensions.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では C3291 が生成されます。

```cpp
// C3291.cpp
// compile with: /clr /c
ref struct C {
   property System::String ^ default;   // C3291
   property System::String ^ Default;   // OK
};
```
