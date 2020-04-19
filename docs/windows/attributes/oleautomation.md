---
title: oleautomation (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.oleautomation
helpviewer_keywords:
- oleautomation attribute
ms.assetid: c1086c91-260b-4dc3-b244-662852d09906
ms.openlocfilehash: 56970d8b1067e1ac38230b6995074210ddc5549b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514361"
---
# <a name="oleautomation"></a>oleautomation

インターフェイスがオートメーションと互換性があることを示します。

## <a name="syntax"></a>構文

```cpp
[oleautomation]
```

## <a name="remarks"></a>Remarks

**Oleautomation** C++属性には、 [oleautomation](/windows/win32/Midl/oleautomation) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Oleautomation**の使用例については、 [defaultvalue](defaultvalue.md)の例と[非拡張](nonextensible.md)の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**interface**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|**dispinterface**|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)