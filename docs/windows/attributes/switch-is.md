---
title: switch_is (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.switch_is
helpviewer_keywords:
- switch_is attribute
ms.assetid: f1fffe5d-12d2-4e0f-8803-ccb715177d2d
ms.openlocfilehash: b72052f4cbd7f94b170ea58b8f7b284b85d7ab00
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513982"
---
# <a name="switch_is"></a>switch_is

共用体メンバーを選択する union 判別として機能する式または識別子を指定します。

## <a name="syntax"></a>構文

```cpp
[switch_is]
```

## <a name="remarks"></a>Remarks

**Switch_is** C++属性には、 [switch_is](/windows/win32/Midl/switch-is) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Switch_is**の使用例については、[大文字と小文字](case-cpp.md)の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**typedef**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[switch_type](switch-type.md)