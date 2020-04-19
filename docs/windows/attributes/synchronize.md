---
title: 同期 (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.synchronize
helpviewer_keywords:
- synchronize attribute
ms.assetid: 15fc8544-955d-4765-b3d5-0f619c8b3f40
ms.openlocfilehash: ea5236b887fb0df2a0acdd1e4050c66a4719072b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407134"
---
# <a name="synchronize"></a>synchronize

ターゲット メソッドへのアクセスを同期します。

## <a name="syntax"></a>構文

```cpp
[synchronize]
```

## <a name="remarks"></a>Remarks

**同期**C++ 属性には、オブジェクトのターゲット メソッドを同期するためのサポートが実装されています。 同期により、ターゲット メソッドへのアクセスを制御することで、クラスのメソッド) などの一般的なリソースを使用する複数のオブジェクト。

この属性によって挿入されたコードの呼び出し、適切な`Lock`ターゲット メソッドの先頭には、(スレッド処理モデルによって決定) メソッドです。 メソッドが終了したときに`Unlock`自動的に呼び出されます。 これらの関数の詳細については、次を参照してください[CComAutoThreadModule::Lock。](../../atl/reference/ccomautothreadmodule-class.md#lock)

この属性を使用するには、 [coclass](coclass.md)、 [progid](progid.md)、または [vi_progid](vi-progid.md) 属性 (または、これらのいずれかを意味する別の属性) も同じ要素に適用する必要があります。 いずれか 1 つの属性を使用すると、他の 2 つも自動的に適用されます。 たとえば場合、`progid`が適用される`vi_progid`と`coclass`も適用されます。

## <a name="example"></a>例

次のコードの同期、`UpdateBalance`のメソッド、`CMyClass`オブジェクト。

```cpp
// cpp_attr_ref_synchronize.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module(name="SYNC")];

[coclass,
threading(both),
vi_progid("MyProject.MyClass"),
progid("MyProject.MyClass.1"),
uuid("7a7baa0d-59b8-4576-b754-79d07e1d1cc3")
]
class CMyClass {
   float m_nBalance;

   [synchronize]
   void UpdateBalance(float nAdjust) {
      m_nBalance += nAdjust;
   }
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|クラスのメソッド|
|**反復可能**|いいえ|
|**必要な属性**|次のいずれかまたは: `coclass`、 `progid`、または`vi_progid`します。|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[COM 属性](com-attributes.md)