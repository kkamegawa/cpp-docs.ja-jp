---
title: コンパイラ エラー C3461
ms.date: 11/04/2016
f1_keywords:
- C3461
helpviewer_keywords:
- C3461
ms.assetid: bd66833a-545d-445a-bdfe-dee771a450a4
ms.openlocfilehash: d1bf4af63bac2aaee1da4bb98f23c3b15e98c671
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756631"
---
# <a name="compiler-error-c3461"></a>コンパイラ エラー C3461

'type': マネージド型のみ転送できます

型の転送は、CLR 型でのみ実行できます。  詳細については[、「クラスと構造体](../../extensions/classes-and-structs-cpp-component-extensions.md)」を参照してください。

詳細については、「[型C++の転送 (/cli)](../../extensions/type-forwarding-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

コンポーネントを作成する例を次に示します。

```cpp
// C3461.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>使用例

次の例では C3461 が生成されます。

```cpp
// C3461b.cpp
// compile with: /clr /c
#using "C3461.dll"
class N {};
[assembly:TypeForwardedTo(N::typeid)];   // C3461
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
