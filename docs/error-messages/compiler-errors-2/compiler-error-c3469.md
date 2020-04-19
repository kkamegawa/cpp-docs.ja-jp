---
title: コンパイラ エラー C3469
ms.date: 11/04/2016
f1_keywords:
- C3469
helpviewer_keywords:
- C3469
ms.assetid: e23b0e5c-c704-4e67-a868-bf02c2055d85
ms.openlocfilehash: 546de5a65f6e4c2fd370ba781d01945df2bbfce5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760544"
---
# <a name="compiler-error-c3469"></a>コンパイラ エラー C3469

'type': ジェネリック クラスを転送することはできません

ジェネリック クラスでは型の転送を使用できません。

詳細については、「[型C++の転送 (/cli)](../../extensions/type-forwarding-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

コンポーネントを作成する例を次に示します。

```cpp
// C3469.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>使用例

次の例では C3466 が生成されます。

```cpp
// C3469_b.cpp
// compile with: /clr /c
#using "C3469.dll"
[assembly:TypeForwardedTo(GR::typeid)];   // C3469
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```
