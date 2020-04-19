---
title: コンパイラ エラー C2180
ms.date: 11/04/2016
f1_keywords:
- C2180
helpviewer_keywords:
- C2180
ms.assetid: ea71b39e-b977-48a7-b7bd-af68ef5e263b
ms.openlocfilehash: 5e9444356e536a8369dbcf62cac3c7538d9da5dd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301900"
---
# <a name="compiler-error-c2180"></a>コンパイラ エラー C2180

制御式には、型 'type' が指定されています。

`if`、`while`、`for`、`do` のいずれかのステートメントの制御式は、`void` にキャストした式です。 この問題を解決するには、制御式を、`bool` を生成する制御式または `bool` に変換できる型に変更します。

次の例では C2180 が生成されます。

```c
// C2180.c

int main() {
   while ((void)1)   // C2180
      return 1;
   while (1)         // OK
      return 0;
}
```
