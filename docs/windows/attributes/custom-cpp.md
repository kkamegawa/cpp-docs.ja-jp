---
title: custom (C++)
ms.date: 11/04/2016
f1_keywords:
- vc-attr.custom
helpviewer_keywords:
- custom attributes, defining
ms.assetid: 3abac928-4d55-4ea6-8cf6-8427a4ad79f1
ms.openlocfilehash: 19f28963a18abf42c6f629ac0f6491628387aa6d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490999"
---
# <a name="custom-c"></a>custom (C++)

タイプライブラリ内のオブジェクトのメタデータを定義します。

## <a name="syntax"></a>構文

```cpp
[ custom(
   uuid,
   value
) ];
```

### <a name="parameters"></a>パラメーター

*uuid*<br/>
一意の ID。

*value*<br/>
バリアントに含めることができる値。

## <a name="remarks"></a>Remarks

**カスタム** C++属性によって、情報がタイプライブラリに配置されます。 タイプライブラリからカスタム値を読み取るツールが必要です。

**カスタム**属性には、[カスタム](/windows/win32/Midl/custom)MIDL 属性と同じ機能があります。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|非 COM**インターフェイス**、**クラス**、**列挙型**、 `idl_module`メソッド、インターフェイスメンバー、インターフェイスパラメーター、 **typedef**s、**共用**体 s、**構造体**|
|**反復可能**|はい|
|**必要な属性**|**コクラス**(クラスで使用される場合)|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[スタンドアロン属性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[パラメーター属性](parameter-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)