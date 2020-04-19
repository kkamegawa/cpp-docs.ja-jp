---
title: pragma (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.pragma
helpviewer_keywords:
- pragma attribute
ms.assetid: 3f90d023-b8b5-4007-8311-008bb72cbea1
ms.openlocfilehash: 5c3ee0d3f99bd27ca41d68b11c11522e92c8d40a
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514280"
---
# <a name="pragma"></a>pragma

指定された文字列を、引用符を使用せずに、生成された .idl ファイルに出力します。

## <a name="syntax"></a>構文

```cpp
[ pragma(pragma_statement) ];
```

### <a name="parameters"></a>パラメーター

*pragma_statement*<br/>
生成された .idl ファイルに含めるプラグマ。

## <a name="remarks"></a>Remarks

**プラグマ** C++属性には、 [pragma](/windows/win32/Midl/pragma) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

```cpp
// cpp_attr_ref_pragma.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[pragma(pack(4))];

[dispinterface, uuid("00000000-0000-0000-0000-000000000001")]
__interface A
{
   [id(1)] HRESULT MyMethod ([in, satype("BSTR")] SAFEARRAY **p);
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|任意の場所|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[スタンドアロン属性](stand-alone-attributes.md)<br/>
[pack](../../preprocessor/pack.md)