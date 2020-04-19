---
title: call_as (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.call_as
helpviewer_keywords:
- call_as attribute
ms.assetid: a09d7f1f-353b-4870-9b45-f0284161695d
ms.openlocfilehash: f36cf8d1be589cc614a6def583b00af00aabdb61
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501807"
---
# <a name="call_as"></a>call_as

リモート関数が呼び出されたときにローカル関数が呼び出されるように、[ローカル](local-cpp.md)関数をリモート関数にマップできるようにします。

## <a name="syntax"></a>構文

```cpp
[ call_as(function) ]
```

### <a name="parameters"></a>パラメーター

*function*<br/>
リモート関数が呼び出されたときに呼び出されるローカル関数。

## <a name="remarks"></a>Remarks

**Call_as** C++属性には、 [call_as](/windows/win32/Midl/call-as) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

次のコードは、 **call_as**を使用して、リモート処理不可能関数 (`f1`) をリモート処理可能な関数 (`Remf1`) にマップする方法を示しています。

```cpp
// cpp_attr_ref_call_as.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];
[dual, uuid("00000000-0000-0000-0000-000000000001")]
__interface IMInterface {
   [local] HRESULT f1 ( int i );
   [call_as(f1)] HRESULT Remf1 ( int i );
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|インターフェイス メソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[local](local-cpp.md)