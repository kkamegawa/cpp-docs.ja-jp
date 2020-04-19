---
title: size_is (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.size_is
helpviewer_keywords:
- size_is attribute
ms.assetid: 70192d09-f6c5-4d52-b3fe-303f8cb10aa5
ms.openlocfilehash: 504f1bf72b8ffa15e8df50bb00c86ef909688f1e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514033"
---
# <a name="size_is"></a>size_is

サイズ設定されたポインターに割り当てられるメモリのサイズ、サイズポインターへのサイズポインター、および単一または多次元の配列を指定します。

## <a name="syntax"></a>構文

```cpp
[ size_is("expression") ]
```

### <a name="parameters"></a>パラメーター

*式 (expression)*<br/>
サイズ設定されたポインターに割り当てられたメモリのサイズ。

## <a name="remarks"></a>Remarks

**Size_is** C++属性には、 [size_is](/windows/win32/Midl/size-is) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

配列のセクションを指定する方法の例については、 [first_is](first-is.md)の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**struct**または**union**のフィールド、インターフェイスパラメーター、インターフェイスメソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|`max_is`|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[first_is](first-is.md)<br/>
[last_is](last-is.md)<br/>
[max_is](max-is.md)<br/>
[length_is](length-is.md)