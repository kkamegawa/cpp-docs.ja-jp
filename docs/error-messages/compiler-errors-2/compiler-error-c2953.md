---
title: コンパイラ エラー C2953
ms.date: 11/04/2016
f1_keywords:
- C2953
helpviewer_keywords:
- C2953
ms.assetid: 8dbcfa24-8296-4e40-bdc4-5526c07d8892
ms.openlocfilehash: 8a8d591bfbfa30a4ad2fbed171b5febbd46524b0
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747671"
---
# <a name="compiler-error-c2953"></a>コンパイラ エラー C2953

'identifier' : クラス テンプレートは既に定義されています

ソース ファイルを確認し、他の定義のファイルをインクルードします。

次の例では C2953 が生成されます。

```cpp
// C2953.cpp
// compile with: /c
template <class T>  class A {};
template <class T>  class A {};   // C2953
template <class T>  class B {};   // OK
```
