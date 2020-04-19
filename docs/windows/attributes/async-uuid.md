---
title: async_uuid (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.async_uuid
helpviewer_keywords:
- async_uuid attribute
ms.assetid: 235cb0d7-be58-4dd9-983c-e2a21bbc42c6
ms.openlocfilehash: 70e73a6286a4b6adaba20b5a35dc16d8389b1948
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501861"
---
# <a name="async_uuid"></a>async_uuid

COM インターフェイスの同期バージョンと非同期バージョンの両方を定義するように MIDL コンパイラに指示する UUID を指定します。

## <a name="syntax"></a>構文

```cpp
[async_uuid (uuid)]
```

### <a name="parameters"></a>パラメーター

*uuid*<br/>
インターフェイスのバージョンを識別する UUID。

## <a name="remarks"></a>Remarks

**Async_uuid** C++属性には、 [async_uuid](/windows/win32/Midl/async-uuid) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

```cpp
// cpp_attr_ref_async_uuid.cpp
// compile with: /LD
#include <Windows.h>
[module(name="Test")];
[object, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb"),
async_uuid("e8583106-38fd-487e-912e-4fc8645c677e")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|`interface`|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|**デュアル**、**ディスパッチインターフェイス**|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)