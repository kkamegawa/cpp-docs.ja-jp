---
title: イミディエイトの atebindC++ (COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.immediatebind
helpviewer_keywords:
- immediatebind attribute
ms.assetid: 186d40e6-9166-4d0c-9853-4e7e4d25226f
ms.openlocfilehash: 8c659f23d6828616c4a48522b61330336e994cbb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514653"
---
# <a name="immediatebind"></a>immediatebind

データバインドオブジェクトのプロパティに対するすべての変更が、すぐにデータベースに通知されることを示します。

## <a name="syntax"></a>構文

```cpp
[immediatebind]
```

## <a name="remarks"></a>Remarks

**イミディエイトの atebind** C++属性には、[イミディエイトの atebind](/windows/win32/Midl/immediatebind) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

直**ちに atebind**を使用する方法の例については、「[バインド](bindable.md)可能」を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|インターフェイス メソッド|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[defaultbind](defaultbind.md)<br/>
[displaybind](displaybind.md)<br/>
[requestedit](requestedit.md)