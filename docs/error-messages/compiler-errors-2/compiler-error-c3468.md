---
title: コンパイラ エラー C3468
ms.date: 11/04/2016
f1_keywords:
- C3468
helpviewer_keywords:
- C3468
ms.assetid: cfd320db-2f6e-4e0d-ba02-e79ece87e1e0
ms.openlocfilehash: e4a507dad1d795e703e8db7f8704aad959c95b6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757308"
---
# <a name="compiler-error-c3468"></a>コンパイラ エラー C3468

'type': 型は次のアセンブリにのみ転送できます:

'`file`' はアセンブリではありません

アセンブリ内の型のみを転送することができます。

詳細については、「[型C++の転送 (/cli)](../../extensions/type-forwarding-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

モジュールを作成する例を次に示します。

```cpp
// C3468.cpp
// compile with: /LN /clr
public ref class R {};
```

## <a name="example"></a>使用例

次の例では C3468 が生成されます。

```cpp
// C3468_b.cpp
// compile with: /clr /c
#using "C3468.netmodule"
[ assembly:TypeForwardedTo(R::typeid) ];   // C3468
```
