---
title: last_is (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.last_is
helpviewer_keywords:
- last_is attribute
ms.assetid: 9e045ac0-fa38-4249-af55-67bde5d0a58c
ms.openlocfilehash: 4745d4eb59fd2adb79937b34184081dbbd0814fb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514511"
---
# <a name="last_is"></a>last_is

転送する最後の配列要素のインデックスを指定します。

## <a name="syntax"></a>構文

```cpp
[ last_is("expression") ]
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
1つ以上の C 言語式。 空の引数スロットが許可されます。

## <a name="remarks"></a>Remarks

**Last_is** C++属性には、 [last_is](/windows/win32/Midl/last-is) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

配列のセクションを指定する方法の例については、「 [first_is](first-is.md) 」を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**struct**または**union**のフィールド、インターフェイスパラメーター、インターフェイスメソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)