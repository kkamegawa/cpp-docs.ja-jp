---
title: コンパイラエラー C2085
ms.date: 11/04/2016
f1_keywords:
- C2085
helpviewer_keywords:
- C2085
ms.assetid: 0a86785c-8e6f-481b-8c7b-412220c1950d
ms.openlocfilehash: 7dbf7266a6330a1fdb46d7f2df90e7684f026d9a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301965"
---
# <a name="compiler-error-c2085"></a>コンパイラエラー C2085

' identifier ': 仮パラメーターリスト内にありません

識別子が関数定義で宣言されていますが、仮パラメーターリストでは宣言されていません。 (ANSI C のみ)

次の例では、C2085 が生成されます。

```c
// C2085.c
void func1( void )
int main( void ) {}   // C2085
```

解決方法:

```c
// C2085b.c
void func1( void );
int main( void ) {}
```

セミコロンが欠落している場合、`func1()` はプロトタイプではなく関数定義のように見えます。そのため、`func1()`内で `main` が定義されており、識別子 `main`のエラー C2085 が生成されます。
