---
title: コンパイラ エラー C2190
ms.date: 11/04/2016
f1_keywords:
- C2190
helpviewer_keywords:
- C2190
ms.assetid: 34e15f85-d979-4948-80fc-46c414508a70
ms.openlocfilehash: 027c7f49b361ef3aa06a4d74e10f0ff27331b4a9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301887"
---
# <a name="compiler-error-c2190"></a>コンパイラ エラー C2190

最初のパラメーターリストが秒より長くなっています

C 関数は、より短いパラメーターリストを使用して2回目に宣言されました。 C は、オーバーロードされた関数をサポートしていません。

次の例では、C2190 が生成されます。

```c
// C2190.c
// compile with: /Za /c
void func( int, float );
void func( int  );   // C2190, different parameter list
void func2( int  );   // OK
```
