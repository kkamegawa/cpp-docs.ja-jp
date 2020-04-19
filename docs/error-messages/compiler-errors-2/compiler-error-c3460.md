---
title: コンパイラ エラー C3460
ms.date: 11/04/2016
f1_keywords:
- C3460
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
ms.openlocfilehash: 9dc30eea73140ea6f0f436339de249bb714a46c2
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756618"
---
# <a name="compiler-error-c3460"></a>コンパイラ エラー C3460

'type': 転送できるのはユーザー定義型のみです

詳細については、「[型C++の転送 (/cli)](../../extensions/type-forwarding-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

コンポーネントを作成する例を次に示します。

```cpp
// C3460.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>使用例

次の例では C3460 が生成されます。

```cpp
// C3460_b.cpp
// compile with: /clr /c
#using "C3460.dll"
[assembly:TypeForwardedTo(int::typeid)];   // C3460
[assembly:TypeForwardedTo(R::typeid)];
```
