---
title: コンパイラ エラー C2483
ms.date: 09/15/2017
f1_keywords:
- C2483
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
ms.openlocfilehash: 7a627ce28e60f42dabcf0a257464a8bfbd58b9a4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361361"
---
# <a name="compiler-error-c2483"></a>コンパイラ エラー C2483

>'*identifier*' : object with constructor or destructor cannot be declared 'thread'

このエラー メッセージは、Visual Studio 2015 以降で廃止されています。 以前のバージョンで宣言された変数、`thread`コンス トラクターまたは実行時の評価が必要なその他の式では、属性を初期化できません。 静的な式が初期化に必要な`thread`データ。

## <a name="example"></a>例

次の例では、Visual Studio 2013 および以前のバージョンで C2483 が生成されます。

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>関連項目

[thread](../../cpp/thread.md)