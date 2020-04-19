---
title: コンパイラの警告 (レベル 1) C4103
ms.date: 11/04/2016
f1_keywords:
- C4103
helpviewer_keywords:
- C4103
ms.assetid: 9021b514-375e-4d62-b261-ccb06f299e8e
ms.openlocfilehash: 456e7d393eb751e99c1969619ccfdcc649193c75
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627062"
---
# <a name="compiler-warning-level-1-c4103"></a>コンパイラの警告 (レベル 1) C4103

' filename ': ヘッダーを含めた後にアラインメントが変更されました。 #pragma pack (pop) がないことが原因である可能性があります

パッキングはクラスのレイアウトに影響します。一般的に、ヘッダーファイル間で変更をパッキングする場合は、問題が発生する可能性があります。

ヘッダーファイルを終了する前に #pragma [pack](../../preprocessor/pack.md)(pop) を使用して、この警告を解決してください。

次の例では、C4103 が生成されます。

```cpp
// C4103.h
#pragma pack(push, 4)

// defintions and declarations

// uncomment the following line to resolve
// #pragma pack(pop)
```

この場合、次のようになります。

```cpp
// C4103.cpp
// compile with: /LD /W1
#include "c4103.h"   // C4103
```