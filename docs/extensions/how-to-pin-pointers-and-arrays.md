---
title: '方法: ポインターと配列を固定する'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- pointers, pinning
- arrays [C++], pinning
ms.assetid: ee783260-e676-46b8-a38e-11a06f1d57b0
ms.openlocfilehash: ae8c1da79f41cf9209f2765ce5aa2f7ca3d34aea
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515687"
---
# <a name="how-to-pin-pointers-and-arrays"></a>方法: ポインターと配列を固定する

マネージ オブジェクトに定義されているサブオブジェクトの固定には、オブジェクト全体を固定するという効果があります。  たとえば、配列の要素が固定されている場合、配列全体も固定されます。 固定された配列を宣言するための言語の拡張機能はありません。 配列を固定するには、その要素の型に対して固定ポインターを宣言し、要素の 1 つを固定します。

## <a name="example"></a>例

### <a name="code"></a>コード

```cpp
// pin_ptr_array.cpp
// compile with: /clr
#include <stdio.h>
using namespace System;

int main() {
   array<Byte>^ arr = gcnew array<Byte>(4);
   arr[0] = 'C';
   arr[1] = '+';
   arr[2] = '+';
   arr[3] = '\0';
   pin_ptr<Byte> p = &arr[1];   // entire array is now pinned
   unsigned char * cp = p;

   printf_s("%s\n", cp); // bytes pointed at by cp
                         // will not move during call
}
```

```Output
++
```

## <a name="see-also"></a>関連項目

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)