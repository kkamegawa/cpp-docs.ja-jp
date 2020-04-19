---
title: restricted (C++ COM 属性)
ms.date: 10/03/2018
f1_keywords:
- vc-attr.restricted
helpviewer_keywords:
- restricted attribute
ms.assetid: 504a96be-b904-4269-8be1-920feba201b4
ms.openlocfilehash: 01dabcd15eb1a14734c16b9e54c0ab2e030d0479
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514063"
---
# <a name="restricted"></a>restricted

モジュール、インターフェイス、またはディスパッチインターフェイスのメンバーを任意に呼び出すことができないことを指定します。

## <a name="syntax"></a>構文

```cpp
[ restricted(
   interfaces
) ]
```

### <a name="parameters"></a>パラメーター

*interfaces*<br/>
COM オブジェクトで任意に呼び出すことができない1つ以上のインターフェイス。 このパラメーターは、クラスに適用された場合にのみ有効です。

## <a name="remarks"></a>Remarks

**Restricted** C++属性には、[制限付き](/windows/win32/Midl/restricted)MIDL 属性と同じ機能があります。

## <a name="example"></a>例

次のコードは、**制限**された属性の使用方法を示しています。

```cpp
// cpp_attr_ref_restricted.cpp
// compile with: /LD
#include "windows.h"
#include "unknwn.h"
[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000001")]
__interface a
{
};

[object, uuid("00000000-0000-0000-0000-000000000002")]
__interface b
{
};

[coclass, restricted(a,b), uuid("00000000-0000-0000-0000-000000000003")]
class c : public a, public b
{
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|インターフェイスメソッド、**インターフェイス**、**クラス**、**構造体**|
|**反復可能**|いいえ|
|**必要な属性**|**コクラス**(**クラス**または**構造体**に適用される場合)|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[メソッド属性](method-attributes.md)