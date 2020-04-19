---
title: max_is (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.max_is
helpviewer_keywords:
- max_is attribute
ms.assetid: 7c851f5c-6649-4d77-a792-247c37d8f560
ms.openlocfilehash: f2e6db997891817620c1b2c1f70cb310818dd346
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514427"
---
# <a name="max_is"></a>max_is

有効な配列インデックスの最大値を指定します。

## <a name="syntax"></a>構文

```cpp
[ max_is("expression") ]
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
1つ以上の C 言語式。 空の引数スロットが許可されます。

## <a name="remarks"></a>Remarks

**Max_is** C++属性には、 [max_is](/windows/win32/Midl/max-is) MIDL 属性と同じ機能があります。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**struct**または**union**のフィールド、インターフェイスパラメーター、インターフェイスメソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|**size_is**|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="example"></a>例

配列のセクションを指定する方法の例については、「 [first_is](first-is.md) 」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[length_is](length-is.md)<br/>
[size_is](size-is.md)