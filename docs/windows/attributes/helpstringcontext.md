---
title: helpstringcontext (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstringcontext
helpviewer_keywords:
- helpstringcontext attribute [C++]
ms.assetid: d4cd135e-d91c-4aa3-9353-8aeb096f52cf
ms.openlocfilehash: ae48c6216b1f1d987b33eff50acf9d82dc551400
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501491"
---
# <a name="helpstringcontext"></a>helpstringcontext

.Hlp または .chm ファイルのヘルプトピックの ID を指定します。

## <a name="syntax"></a>構文

```cpp
[ helpstringcontext(contextID) ]
```

### <a name="parameters"></a>パラメーター

*contextID*<br/>
**ヘルプ**ファイル内の32ビットのヘルプコンテキスト識別子。

## <a name="remarks"></a>Remarks

**Helpstringcontext** C++属性には、 [helpstringcontext](/windows/win32/Midl/helpstringcontext) ODL 属性と同じ機能があります。

## <a name="example"></a>例

```cpp
// cpp_attr_ref_helpstringcontext.cpp
// compile with: /LD
#include <unknwn.h>
[module(name="MyLib")];

[   object, helpstring("help string"), helpstringcontext(1), uuid="11111111-1111-1111-1111-111111111111"
]
__interface IMyI
{
   HRESULT xx();
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**インターフェイス**、インターフェイスメソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[module](module-cpp.md)