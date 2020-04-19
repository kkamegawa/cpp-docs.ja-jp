---
title: swap 関数 (auto_gcroot)
ms.date: 11/04/2016
ms.topic: reference
f1_keywords:
- msclr::swap
- msclr.swap
helpviewer_keywords:
- swap function
ms.assetid: 2fe8146b-a7f7-445a-9ae9-53b5556be701
ms.openlocfilehash: 7ed4e3f946f314819e6c562d489050182a975b7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62384544"
---
# <a name="swap-function-autogcroot"></a>swap 関数 (auto_gcroot)

1 つの間でオブジェクトを交換`auto_gcroot`別とします。

## <a name="syntax"></a>構文

```
template<typename _element_type>
void swap(
   auto_gcroot<_element_type> & _left,
   auto_gcroot<_element_type> & _right
);
```

#### <a name="parameters"></a>パラメーター

*_left*<br/>
`auto_gcroot`。

*_right*<br/>
もう 1 つ`auto_gcroot`します。

## <a name="example"></a>例

```
// msl_swap_auto_gcroot.cpp
// compile with: /clr
#include <msclr\auto_gcroot.h>

using namespace System;
using namespace msclr;

int main() {
   auto_gcroot<String^> s1 = "string one";
   auto_gcroot<String^> s2 = "string two";

   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
   swap( s1, s2 );
   Console::WriteLine( "s1 = '{0}', s2 = '{1}'",
      s1->ToString(), s2->ToString() );
}
```

```Output
s1 = 'string one', s2 = 'string two'
s1 = 'string two', s2 = 'string one'
```

## <a name="requirements"></a>必要条件

**ヘッダー ファイル** \<msclr\auto_gcroot.h >

**Namespace** msclr

## <a name="see-also"></a>関連項目

[auto_gcroot](../dotnet/auto-gcroot.md)<br/>
[auto_gcroot::swap](../dotnet/auto-gcroot-swap.md)
