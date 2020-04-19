---
title: out (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.out
helpviewer_keywords:
- out attribute
ms.assetid: 5051b1bf-4949-4bf1-b82f-35e14f0f244b
ms.openlocfilehash: 11c8e4473f0b849fab7846a825b90da3ed9f036f
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514285"
---
# <a name="out-c"></a>out (C++)

呼び出されたプロシージャから呼び出したプロシージャ (サーバーからクライアント) に返されるポインター パラメーターを示します。

## <a name="syntax"></a>構文

```cpp
[out]
```

## <a name="remarks"></a>Remarks

**out** C++ 属性には、 [propput](/windows/win32/Midl/out-idl) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

[out](bindable.md) の使用サンプルについては、「 **bindable**」の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|インターフェイス パラメーター|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[defaultvalue](defaultvalue.md)<br/>
[ID](id.md)