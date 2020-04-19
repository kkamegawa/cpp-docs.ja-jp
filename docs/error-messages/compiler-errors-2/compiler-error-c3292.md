---
title: コンパイラ エラー C3292
ms.date: 11/04/2016
f1_keywords:
- C3292
helpviewer_keywords:
- C3292
ms.assetid: ead485cc-5471-4e10-b361-300589ff5b70
ms.openlocfilehash: 566c92a5dc24c28b334653c6b5507b0bd9330992
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760128"
---
# <a name="compiler-error-c3292"></a>コンパイラ エラー C3292

cli 名前空間はを再度開くことはできません

コード内で cli 名前空間を宣言することはできません。  詳細については、「[プラットフォーム、既定、および cli 名前空間](../../extensions/platform-default-and-cli-namespaces-cpp-component-extensions.md)」を参照してください。

## <a name="example"></a>使用例

次の例では C3292 が生成されます。

```cpp
// C3292.cpp
// compile with: /clr /c
namespace cli {};   // C3292
```
