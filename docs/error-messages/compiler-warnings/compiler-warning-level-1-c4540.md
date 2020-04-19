---
title: コンパイラの警告 (レベル 1) C4540
ms.date: 11/04/2016
f1_keywords:
- C4540
helpviewer_keywords:
- C4540
ms.assetid: 8085e748-5f4d-43c2-b06d-eaf794edbf72
ms.openlocfilehash: 8e514f4f3cf0cc3ee95ff709eda307b143ab3b1c
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965687"
---
# <a name="compiler-warning-level-1-c4540"></a>コンパイラの警告 (レベル 1) C4540

アクセスできない、またはあいまいなベースへの変換に使用 dynamic_castランタイムテストが失敗します (' type1 ' から ' type1 ')

`dynamic_cast` を使用して、ある型から別の型に変換します。 コンパイラは、基底クラスにアクセスできない (`private`、インスタンス)、あいまいである (たとえば、クラス階層に複数回出現する) ため、キャストが常に失敗する ( **NULL**を返す) と判断しました。

この警告の例を次に示します。 クラス**B**はクラス**A**から派生しています。このプログラムは、クラス**b** (派生クラス) からクラス**A**にキャストするために `dynamic_cast` を使用します。これは、クラス**b**が `private` であり、アクセスできないため、常に失敗します。 のアクセスをパブリック**に**変更すると、警告が解決されます。

```cpp
// C4540.cpp
// compile with: /W1

struct A {
   virtual void g() {}
};

struct B : private A {
   virtual void g() {}
};

int main() {
   B b;
   A * ap = dynamic_cast<A*>(&b);   // C4540
}
```