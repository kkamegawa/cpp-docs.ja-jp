---
title: 非拡張 (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.nonextensible
helpviewer_keywords:
- nonextensible attribute
ms.assetid: c7ef1554-809f-4ea0-a7cd-dc7786d40c3e
ms.openlocfilehash: f2947e223d068ea6cc92a41abe19cb7f920112b2
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514399"
---
# <a name="nonextensible"></a>nonextensible

実装に`IDispatch` 、インターフェイスの説明に示されているプロパティとメソッドのみが含まれ、実行時に追加のメンバーで拡張できないことを指定します。

## <a name="syntax"></a>構文

```cpp
[nonextensible]
```

## <a name="remarks"></a>Remarks

**非拡張** C++属性には、[非拡張](/windows/win32/Midl/nonextensible)MIDL 属性と同じ機能があります。

**非拡張**を使用する場合は、 [oleautomation](oleautomation.md)属性も必要です。

## <a name="example"></a>例

次のコードは、**非拡張**属性の使用方法を示しています。

```cpp
// cpp_attr_ref_nonextensible.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="ATLFIRELib")];
[export] typedef long HRESULT;

[dual, nonextensible, ms_union, oleautomation,
uuid("00000000-0000-0000-0000-000000000001")]
__interface IFireTabCtrl
{
   HRESULT procedure (int i);
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**interface**|
|**反復可能**|いいえ|
|**必要な属性**|`dual`and `oleautomation`、or`dispinterface`|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)