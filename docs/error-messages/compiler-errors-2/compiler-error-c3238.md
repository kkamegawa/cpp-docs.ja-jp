---
title: コンパイラ エラー C3238
ms.date: 11/04/2016
f1_keywords:
- C3238
helpviewer_keywords:
- C3238
ms.assetid: 19942497-b3c5-4df0-9144-142ced92468b
ms.openlocfilehash: 6f60a9abbc5702c1a0d14d0f894c9b1684378c3f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74759361"
---
# <a name="compiler-error-c3238"></a>コンパイラ エラー C3238

'type' : この名前の型は、アセンブリ 'assembly' に既に転送されました

クライアント アプリケーションで定義された型は、参照されているアセンブリでも、型の転送構文によって定義されています。 アプリケーションのスコープで、両方の型を定義することはできません。

詳細については、「[型の転送C++(/cli)](../../extensions/type-forwarding-cpp-cli.md) 」を参照してください。

## <a name="example"></a>使用例

次の例では、別のアセンブリから転送された型を含むアセンブリを作成します。

```cpp
// C3238.cpp
// compile with: /clr /LD
public ref class R {};
```

## <a name="example"></a>使用例

次の例は型定義を含んでいたアセンブリを作成しますが、型の転送構文だけを含んでいるわけではありません。

```cpp
// C3238_b.cpp
// compile with: /clr /LD
#using "C3238.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
```

## <a name="example"></a>使用例

次の例では C3238 が生成されます。

```cpp
// C3238_c.cpp
// compile with: /clr /c
// C3238 expected
// Delete the following line to resolve.
#using "C3238_b.dll"
public ref class R {};
```
