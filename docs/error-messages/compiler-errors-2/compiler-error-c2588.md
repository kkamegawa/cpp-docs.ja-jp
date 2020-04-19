---
title: コンパイラ エラー C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: f1f73e2585606e7e86213607a96ef713345419c1
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755409"
---
# <a name="compiler-error-c2588"></a>コンパイラ エラー C2588

':: ~ identifier ': 無効なグローバルデストラクターです。

デストラクターは、クラス、構造体、または共用体以外のものに対して定義されています。 これは許可されていません。

このエラーは、スコープ解決 (`::`) 演算子の左側にクラス、構造体、または共用体の名前がないことが原因で発生する可能性があります。

次の例では、C2588 が生成されます。

```cpp
// C2588.cpp
~F();   // C2588
```
