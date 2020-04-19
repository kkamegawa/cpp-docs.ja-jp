---
title: propget (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propget
helpviewer_keywords:
- propget attribute
ms.assetid: c9d4a97f-36dd-4b61-8eb0-b1a217598f14
ms.openlocfilehash: 044562ba870d6e36ddfcec0c7e84253b111a9eea
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514211"
---
# <a name="propget"></a>propget

プロパティアクセサー関数を指定します。

## <a name="syntax"></a>構文

```cpp
[propget]
```

## <a name="remarks"></a>Remarks

**Propget** C++属性には、 [propget](/windows/win32/Midl/propget) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Propget**の使用例については、[バインド](bindable.md)可能なの例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|メソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|`propput`, `propputref`|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[propput](propput.md)<br/>
[propputref](propputref.md)