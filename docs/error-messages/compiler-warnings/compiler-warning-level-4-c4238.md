---
title: コンパイラの警告 (レベル 4) C4238
ms.date: 11/04/2016
f1_keywords:
- C4238
helpviewer_keywords:
- C4238
ms.assetid: 5d4051d3-7b0f-43ea-8c8d-d194bfdceb71
ms.openlocfilehash: cc913a4f92963437347fbc708eca03c25ab9d403
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/10/2019
ms.locfileid: "74991472"
---
# <a name="compiler-warning-level-4-c4238"></a>コンパイラの警告 (レベル 4) C4238

非標準の拡張機能が使用されています

以前のバージョンのビジュアルC++との互換性を保つために、Microsoft extensions ( **/ze**) では、暗黙的または明示的にアドレスを取得するコンテキストで、クラス型を右辺値として使用できます。 次の例のような場合は、これが危険になることがあります。

## <a name="example"></a>使用例

```cpp
// C4238.cpp
// compile with: /W4 /c
struct C {
   C() {}
};

C * pC = &C();   // C4238
```

この使用法により、ANSI 互換 ([/za](../../build/reference/za-ze-disable-language-extensions.md)) でエラーが発生します。
