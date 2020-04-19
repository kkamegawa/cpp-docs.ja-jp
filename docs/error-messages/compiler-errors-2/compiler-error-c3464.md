---
title: コンパイラ エラー C3464
ms.date: 11/04/2016
f1_keywords:
- C3464
helpviewer_keywords:
- C3464
ms.assetid: 0ede05dc-4486-4921-8e8c-78ab5a2e09c5
ms.openlocfilehash: bcbacf6ad3f3eda1b1f7448f60278bddfc30f4e6
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756579"
---
# <a name="compiler-error-c3464"></a>コンパイラ エラー C3464

'type' 入れ子になっている型のみを転送することができます

型の転送は、入れ子にされた型では動作しません。

詳細については、「[型C++の転送 (/cli)](../../extensions/type-forwarding-cpp-cli.md)」を参照してください。

## <a name="example"></a>使用例

コンポーネントを作成する例を次に示します。

```cpp
// C3464.cpp
// compile with: /LD /clr
public ref class R {
public:
   ref class N {};
};
```

## <a name="example"></a>使用例

次の例では警告 C3464 が生成されます。

```cpp
// C3464_b.cpp
// compile with: /clr /c
#using "C3464.dll"
[assembly:TypeForwardedTo(R::N::typeid)];   // C3464
[assembly:TypeForwardedTo(R::typeid)];   // OK
```
