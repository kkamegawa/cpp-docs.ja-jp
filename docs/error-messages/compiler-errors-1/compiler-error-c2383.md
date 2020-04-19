---
title: コンパイラ エラー C2383
ms.date: 11/04/2016
f1_keywords:
- C2383
helpviewer_keywords:
- C2383
ms.assetid: 6696221d-879c-477a-a0f3-a6edc15fd3d7
ms.openlocfilehash: e9c1774fe7cd4a6883aa79f384cc64521a57ed17
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448007"
---
# <a name="compiler-error-c2383"></a>コンパイラ エラー C2383

'*シンボル*': 既定の引数はこのシンボルでは許可されていません

C++ コンパイラ、既定の引数を関数へのポインターにはできません。

このコードは、Microsoft によって承認されましたC++、Visual Studio 2005 より前に、のバージョンのコンパイラがエラーになります。 Visual C のすべてのバージョンで動作するコードでは、関数へのポインター引数に既定値は割り当てないでください。

## <a name="example"></a>例

次の例では、C2383 を生成し、解決策を示しています。

```cpp
// C2383.cpp
// compile with: /c
void (*pf)(int = 0);   // C2383
void (*pf)(int);   // OK
```