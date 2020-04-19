---
title: コンパイラ エラー C2555
ms.date: 11/04/2016
f1_keywords:
- C2555
helpviewer_keywords:
- C2555
ms.assetid: 5e49ebb8-7c90-457a-aa12-7ca7ab6574b2
ms.openlocfilehash: cc6c3a3a29665ccf65b77a3d9866986cb0a46b9e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62353227"
---
# <a name="compiler-error-c2555"></a>コンパイラ エラー C2555

'class1::function1': 仮想関数をオーバーライドする型の戻り値とは異なる 'class2::function2' の covariant ではありません

仮想関数、派生のオーバーライド関数戻り値の型が同一のパラメーター リストであります。 派生クラスでオーバーライドする関数は、戻り値の型によってのみ、基本クラスの仮想関数と異なることはできません。

このエラーを解決するには、仮想関数が呼び出された後、戻り値をキャストします。

/Clr でコンパイルする場合は、このエラーも表示可能性があります。   たとえば、Visual c 次の c# 宣言と同等です。

```
Guid[] CheckSources(Guid sourceID, Guid[] carouselIDs);
```

is

```
Guid CheckSources(Guid sourceID, Guid carouselIDs[]) [];
```

次の例では、C2555 が生成されます。

```cpp
// C2555.cpp
// compile with: /c
struct X {
   virtual void func();
};
struct Y : X {
   char func();  // C2555
   void func2();   // OK
};
```