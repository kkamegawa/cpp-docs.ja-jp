---
title: implements_category (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.implements_category
helpviewer_keywords:
- implements_category attribute
ms.assetid: fb162df3-1ebe-43dc-a084-668d7ef8c03f
ms.openlocfilehash: 6e0036b7008b67a1e21bcbe64977f4703bbdf3be
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514636"
---
# <a name="implements_category"></a>implements_category

ターゲットクラスによって実装されるコンポーネントのカテゴリを指定します。

## <a name="syntax"></a>構文

```cpp
[ implements_category(implements_category="uuid") ]
```

### <a name="parameters"></a>パラメーター

*implements_category*<br/>
実装されているカテゴリの ID。

## <a name="remarks"></a>Remarks

**Implements_category** C++属性は、ターゲットクラスによって実装されるコンポーネントカテゴリを指定します。 これを行うには、カテゴリマップを作成し、 **implements_category**属性によって指定された個別のエントリを追加します。 詳細については、「[コンポーネントのカテゴリ」と「しくみ](/windows/win32/com/component-categories-and-how-they-work)」を参照してください。

この属性を使用するには、 [coclass](coclass.md)、 [progid](progid.md)、または [vi_progid](vi-progid.md) 属性 (または、これらのいずれかを意味する別の属性) も同じ要素に適用する必要があります。 いずれか 1 つの属性を使用すると、他の 2 つも自動的に適用されます。 たとえば、が`vi_progid`適用`progid`されている`coclass`場合、とも適用されます。

## <a name="example"></a>例

次のコードでは、次のオブジェクトが`Control`カテゴリを実装することを指定しています。

```cpp
// cpp_attr_ref_implements_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLib")];
[ coclass, implements_category("CATID_Control"),
  uuid("20a0d0cc-5172-40f5-99ae-5e032f3205ae")]
class CMyClass {};
```

## <a name="requirements"></a>要件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**|
|**反復可能**|はい|
|**必要な属性**|次のいずれか: `coclass`、 `progid`、または`vi_progid`|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[COM 属性](com-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[IMPLEMENTED_CATEGORY](../../atl/reference/category-macros.md#implemented_category)