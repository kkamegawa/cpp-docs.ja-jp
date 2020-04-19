---
title: noncreatable (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.noncreatable
helpviewer_keywords:
- noncreatable attribute
ms.assetid: 4d17937b-0bff-41af-ba57-53e18b7ab5a9
ms.openlocfilehash: e855497cb6f619ecdaa6aedf16a04f045a60faa7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514570"
---
# <a name="noncreatable"></a>noncreatable

単独ではインスタンス化できないオブジェクトを定義します。

## <a name="syntax"></a>構文

```cpp
[noncreatable]
```

## <a name="remarks"></a>Remarks

**Noncreatable** C++属性には、 [noncreatable](/windows/win32/Midl/noncreatable) MIDL 属性と同じ機能があり、生成されたに自動的に渡されます。コンパイラによって IDL ファイルが生成されます。

ATL を使用するプロジェクト内でこの属性を使用すると、属性の動作が変更されます。 上記の動作に加えて、属性は[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)マクロも挿入します。 このマクロは、オブジェクトが外部で作成できないことを ATL に示します。

## <a name="example"></a>例

```cpp
// cpp_attr_ref_noncreatable.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[object, uuid("11111111-1111-1111-1111-111111111111")]
__interface A
{
};

[coclass, uuid("11111111-1111-1111-1111-111111111112"), noncreatable]
class CMyClass : public A
{
   HRESULT xx();
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**|
|**反復可能**|いいえ|
|**必要な属性**|**coclass**|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[クラス属性](class-attributes.md)
