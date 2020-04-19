---
title: helpstring (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpstring
helpviewer_keywords:
- helpstring attribute [C++]
ms.assetid: 0401e905-a63e-4fad-98d0-d1efea111966
ms.openlocfilehash: 47a07ee94ad774bde46dce00ea46612fae3a4eca
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490870"
---
# <a name="helpstring"></a>helpstring

適用先となる要素を記述するために使用される文字列を指定します。

## <a name="syntax"></a>構文

```cpp
[ helpstring("string") ]
```

### <a name="parameters"></a>パラメーター

*string*<br/>
ヘルプ文字列のテキスト。

## <a name="remarks"></a>Remarks

**Helpstring** C++属性には、 [helpstring](/windows/win32/Midl/helpstring) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Helpstring**の使用例については、 [defaultvalue](defaultvalue.md)の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**interface**、 **typedef**、 **class**、method、property|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpcontext](helpcontext.md)