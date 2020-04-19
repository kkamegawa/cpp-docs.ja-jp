---
title: コンパイラ エラー C3452
ms.date: 11/04/2016
f1_keywords:
- C3452
helpviewer_keywords:
- C3452
ms.assetid: e5293dcf-cb70-4133-ae2a-0bb496950ba0
ms.openlocfilehash: c491217f01d8e78375401b54faa48d9db410ccad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756722"
---
# <a name="compiler-error-c3452"></a>コンパイラ エラー C3452

リスト引数メンバーは定数ではありません

定数 (コンパイル時に評価できる値) を必要としていた属性に引数が渡されました。

## <a name="example"></a>使用例

次の例では C3452 が生成されます。

```cpp
// C3452.cpp
// compile with: /c
int i;
[module( name="mod", type=dll, custom={i} ) ];   // C3452
// try the following line instead
// [module( name="mod", type=dll, custom={"a"} ) ];
```
