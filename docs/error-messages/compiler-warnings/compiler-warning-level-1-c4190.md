---
title: コンパイラの警告 (レベル 1) C4190
ms.date: 11/04/2016
f1_keywords:
- C4190
helpviewer_keywords:
- C4190
ms.assetid: a4d0ad93-a19a-4063-addd-36d605831567
ms.openlocfilehash: 05984594a57878aad8037861a15ac9284ff65192
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62386500"
---
# <a name="compiler-warning-level-1-c4190"></a>コンパイラの警告 (レベル 1) C4190

'identifier1' が指定すると、C リンケージが UDT には C と互換性がない ' identifier2' を返します

関数または関数へのポインターは、戻り値の型として、UDT (ユーザー定義型、クラス、構造体、列挙型、または共用体である) を持つと`extern`"C"リンケージです。 これは、有効な場合。

- この関数に対するすべての呼び出しは、C++ から発生します。

- 関数の定義は、C++ では。

## <a name="example"></a>例

```cpp
// C4190.cpp
// compile with: /W1 /LD
struct X
{
   int i;
   X ();
   virtual ~X ();
};

extern "C" X func ();   // C4190
```