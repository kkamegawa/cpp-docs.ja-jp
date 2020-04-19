---
title: hidden (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.hidden
helpviewer_keywords:
- hidden attribute
ms.assetid: 199c96dd-fc07-46c7-af93-92020aebebe7
ms.openlocfilehash: 75b03877b1204d6e1c4770f5ba9c8c88338b3394
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501449"
---
# <a name="hidden"></a>hidden

項目が存在するが、ユーザー指向のブラウザーに表示されないことを示します。

## <a name="syntax"></a>構文

```cpp
[hidden]
```

## <a name="remarks"></a>Remarks

**Hidden** C++属性には、[隠し](/windows/win32/Midl/hidden)MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**非表示**の使用方法の例については、[バインド](bindable.md)可能なの例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**interface**、 **class**、 **struct**、method、property|
|**反復可能**|いいえ|
|**必要な属性**|**コクラス**(**クラス**または**構造体**に適用される場合)|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[メソッド属性](method-attributes.md)