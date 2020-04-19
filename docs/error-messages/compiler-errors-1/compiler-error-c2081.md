---
title: コンパイラエラー C2081
ms.date: 11/04/2016
f1_keywords:
- C2081
helpviewer_keywords:
- C2081
ms.assetid: 7db9892d-364d-4178-a49d-f8398ece09a0
ms.openlocfilehash: 2e8e813d8162b9a191b6760366b52783e7c8609f
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301991"
---
# <a name="compiler-error-c2081"></a>コンパイラエラー C2081

' identifier ': 仮パラメーターリスト内の名前が正しくありません

識別子によって構文エラーが発生しました。

このエラーは、仮パラメーターリストの古いスタイルを使用することによって発生することがあります。 仮パラメーターリストでは、仮パラメーターの型を指定する必要があります。

次の例では、C2081 が生成されます。

```c
// C2081.c
void func( int i, j ) {}  // C2081, no type specified for j
```

解決方法:

```c
// C2081b.c
// compile with: /c
void func( int i, int j ) {}
```
