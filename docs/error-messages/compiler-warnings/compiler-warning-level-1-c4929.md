---
title: コンパイラの警告 (レベル 1) C4929
ms.date: 11/04/2016
f1_keywords:
- C4929
helpviewer_keywords:
- C4929
ms.assetid: 95f8ab4f-4468-4caa-acd5-8f4592f03b3c
ms.openlocfilehash: f8ed1252d61748047077defb4e7e77c85e596107
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052273"
---
# <a name="compiler-warning-level-1-c4929"></a>コンパイラの警告 (レベル 1) C4929

' file ': タイプライブラリ含みに共用体が含まれています。' embedded_idl ' 修飾子を無視します

タイプライブラリに共用体が存在するため、 [#import](../../preprocessor/hash-import-directive-cpp.md)の embedded_idl 属性をタイプライブラリに適用できませんでした。 この警告を解決するには、embedded_idl を使用しないでください。

## <a name="example"></a>例

次の例では、コンポーネントを定義します。

```cpp
// C4929a.cpp
// compile with: /LD /link /TLBOUT:C4929a.tlb
#include <objbase.h>
[module(name="Test")];
[public, switch_type(short)] typedef union _TD_UNION_TYPE   {
   [case(24)]
      float fM;
   [case(25)]
      double dMN;
   [default]
      int x;
} TD_UNION_TYPE;

[export, public] typedef struct _TDW_TYPE {
   [switch_is(sU)] TD_UNION_TYPE w;
      short sU;
} TD_TYPE;

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface I {
   HRESULT f(TD_TYPE*);
};

[coclass, uuid("00000000-0000-0000-0000-000000000002")]
struct C : I {
   HRESULT f(TD_TYPE*) { return 0; }
};
```

## <a name="example"></a>例

次の例では、C4929 が生成されます。

```cpp
// C4929b.cpp
// compile with: /c /W1
#import "C4929a.tlb" embedded_idl   // C4929
```