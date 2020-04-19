---
title: コンパイラエラー C2032
ms.date: 11/04/2016
f1_keywords:
- C2032
helpviewer_keywords:
- C2032
ms.assetid: 625d7c83-70b6-42c2-a558-81fbc0026324
ms.openlocfilehash: d20bc61df2d0bab9115768b3bc0589f11a9bcdb9
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302095"
---
# <a name="compiler-error-c2032"></a>コンパイラエラー C2032

' identifier ': 関数を構造体/共用体 ' structorunion ' のメンバーにすることはできません

構造体または共用体にメンバー関数が含まれてC++いますが、これはでは許可されますが、C では使用できません。エラーを解決するには、 C++プログラムとしてコンパイルするか、メンバー関数を削除します。

次の例では、C2032 が生成されます。

```c
// C2032.c
struct z {
   int i;
   void func();   // C2032
};
```

解決方法:

```c
// C2032b.c
// compile with: /c
struct z {
   int i;
};
```
