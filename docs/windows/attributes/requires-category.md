---
title: requires_category (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.requires_category
helpviewer_keywords:
- requires_category attribute
ms.assetid: a645fdc6-1ef5-414d-8c56-5fe2686d4687
ms.openlocfilehash: ec35a1958d9fbcf77fef7f498c6c0dba3ab17df9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407368"
---
# <a name="requirescategory"></a>requires_category

ターゲット クラスの必須コンポーネントのカテゴリを指定します。

## <a name="syntax"></a>構文

```cpp
[ requires_category(
  requires_category) ]
```

### <a name="parameters"></a>パラメーター

*requires_category*<br/>
必要なカテゴリの ID。

## <a name="remarks"></a>Remarks

**Requires_category** C++属性がターゲット クラスに必須コンポーネントのカテゴリを指定します。 詳細については、次を参照してください。[要求する](../../atl/reference/category-macros.md#required_category)します。

この属性を使用するには、 [coclass](coclass.md)、 [progid](progid.md)、または [vi_progid](vi-progid.md) 属性 (または、これらのいずれかを意味する別の属性) も同じ要素に適用する必要があります。

## <a name="example"></a>例

次のコードでは、オブジェクトがコントロールのカテゴリを実装することが必要です。

```cpp
// cpp_attr_ref_requires_category.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name="MyLibrary")];

[ coclass, requires_category("CATID_Control"),
  uuid("1e1a2436-f3ea-4ff3-80bf-5409370e8144")]
class CMyClass {};
```

## <a name="requirements"></a>要件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**|
|**反復可能**|いいえ|
|**必要な属性**|次のいずれかまたは: `coclass`、 `progid`、または`vi_progid`します。|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[COM 属性](com-attributes.md)<br/>
[implements_category](implements-category.md)