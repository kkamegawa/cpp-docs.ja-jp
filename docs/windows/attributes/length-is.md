---
title: length_is (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.length_is
helpviewer_keywords:
- length_is attribute
ms.assetid: 1d99b883-84bb-4b1e-b098-eb780fc94f40
ms.openlocfilehash: 4f4bfe233e3228c50aee734de4ad979c38a55fda
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514526"
---
# <a name="length_is"></a>length_is

転送する配列要素の数を指定します。

## <a name="syntax"></a>構文

```cpp
[ length_is("expression") ]
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
1つ以上の C 言語式。 空の引数スロットが許可されます。

## <a name="remarks"></a>Remarks

**Length_is** C++属性には、 [length_is](/windows/win32/Midl/length-is) MIDL 属性と同じ機能があります。

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
[last_is](last-is.md)<br/>
[size_is](size-is.md)