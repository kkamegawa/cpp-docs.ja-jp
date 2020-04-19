---
title: コンパイラの警告 (レベル1およびレベル 4) C4949
ms.date: 11/04/2016
f1_keywords:
- C4949
helpviewer_keywords:
- C4949
ms.assetid: 34f45a05-c115-49cb-9f67-0bd4f0735d9b
ms.openlocfilehash: f2876813131271ebb2561f8ea7435bb96dc2ce17
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627412"
---
# <a name="compiler-warning-level-1-and-level-4-c4949"></a>コンパイラの警告 (レベル1およびレベル 4) C4949

プラグマ ' managed ' と ' unmanaged ' は、'/clr [: option] ' でコンパイルされた場合にのみ意味があります

ソースコードが[/clr](../../build/reference/clr-common-language-runtime-compilation.md)でコンパイルされていない場合、コンパイラは[マネージ](../../preprocessor/managed-unmanaged.md)プラグマおよびアンマネージプラグマを無視します。 これは、情報提供の警告です。

次の例では、C4949 が生成されます。

```cpp
// C4949.cpp
// compile with: /LD /W1
#pragma managed   // C4949
```

**/Clr**を指定せずに **#pragma アンマネージ**を使用すると、C4949 はレベル4の警告になります。

次の例では、C4949 が生成されます。

```cpp
// C4949b.cpp
// compile with: /LD /W4
#pragma unmanaged   // C4949
```