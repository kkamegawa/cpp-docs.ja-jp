---
title: コンパイラ エラー C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366369"
---
# <a name="compiler-error-c2891"></a>コンパイラ エラー C2891

'parameter': テンプレート パラメーターのアドレスを取得できません

左辺値である場合を除きは、テンプレートのパラメーターのアドレスを取得できません。 型パラメーターは、アドレスがないために、左辺値ではありません。 また、左辺値ではない、テンプレート パラメーター リスト内の非型の値には、アドレスがありません。 これは、テンプレート パラメーターとして渡される値がコンパイラによって生成されたテンプレート引数のコピーであるために、コンパイラ エラー C2891、原因となるコードの例です。

```
template <int i> int* f() { return &i; }
```

など、参照型の左辺値であるテンプレート パラメーターが、アドレスを取ることができます。

```
template <int& r> int* f() { return &r; }
```

このエラーを修正するにはなりませんテンプレートのパラメーターのアドレスを左辺値である場合を除き。