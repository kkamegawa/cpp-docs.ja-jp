---
title: propputref (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.propputref
helpviewer_keywords:
- propputref attribute
ms.assetid: 9b0aed74-fdc7-4e59-9117-949bea4f86dd
ms.openlocfilehash: 9dc21494886f80890bcfde7f29bb3d6c86b4a51b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514185"
---
# <a name="propputref"></a>propputref

値ではなく参照を使用するプロパティ設定関数を指定します。

## <a name="syntax"></a>構文

```cpp
[propputref]
```

## <a name="remarks"></a>Remarks

**Propputref** C++属性には、 [propputref](/windows/win32/Midl/propputref) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Propputref**の使用例については、[バインド](bindable.md)可能なの例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|メソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|`propget`, `propput`|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[propget](propget.md)<br/>
[propput](propput.md)