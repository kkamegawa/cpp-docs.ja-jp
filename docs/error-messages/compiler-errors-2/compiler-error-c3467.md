---
title: コンパイラ エラー C3467
ms.date: 11/04/2016
f1_keywords:
- C3467
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
ms.openlocfilehash: bba505b01df8eb1b253fbecb0db93d94ae62d5ac
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756371"
---
# <a name="compiler-error-c3467"></a>コンパイラ エラー C3467

'type': この型は既に転送されました

同じ型の事前宣言が複数検出されました。 宣言は、型ごとに 1 回しかできません。

詳細については、「[型C++の転送 (/cli)](../../extensions/type-forwarding-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

コンポーネントを作成する例を次に示します。

```cpp
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

## <a name="example"></a>使用例

次の例では C3467 が生成されます。

```cpp
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```
