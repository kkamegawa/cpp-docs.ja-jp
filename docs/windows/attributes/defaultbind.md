---
title: defaultbind (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.defaultbind
helpviewer_keywords:
- defaultbind attribute
ms.assetid: b20a8437-24e6-4b6d-a2df-09fe5e1006e0
ms.openlocfilehash: a2f612c4869a62a84a6a2af99057ced365f875f2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490988"
---
# <a name="defaultbind"></a>defaultbind

オブジェクトを最もよく表す、1つのバインド可能なプロパティを示します。

## <a name="syntax"></a>構文

```cpp
[defaultbind]
```

## <a name="remarks"></a>Remarks

**Defaultbind** C++属性には、 [defaultbind](/windows/win32/Midl/defaultbind) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Defaultbind**の使用例については、[バインド](bindable.md)可能なの例を参照してください。

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
[displaybind](displaybind.md)<br/>
[immediatebind](immediatebind.md)<br/>
[requestedit](requestedit.md)