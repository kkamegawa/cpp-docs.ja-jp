---
title: id (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.id
helpviewer_keywords:
- id attribute
ms.assetid: a48d2c99-c5d2-4f46-bf96-5ac88dcb5d0c
ms.openlocfilehash: 6f1d1d2b9d147e8b33b3b5fae629e0805971bb71
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501415"
---
# <a name="id"></a>id

メンバー関数 (インターフェイスまたはディスパッチインターフェイスのプロパティまたはメソッド) の*dispid*パラメーターを指定します。

## <a name="syntax"></a>構文

```cpp
[ id(dispid) ]
```

### <a name="parameters"></a>パラメーター

*dispid*<br/>
インターフェイスメソッドのディスパッチ ID。

## <a name="remarks"></a>Remarks

**Id** C++属性には、 [id](/windows/win32/Midl/id) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Id**の使用方法の例については、[バインド](bindable.md)可能なの例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|インターフェイス メソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[データ メンバー属性](data-member-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[in](in-cpp.md)<br/>
[out](out-cpp.md)