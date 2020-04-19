---
title: helpcontext (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.helpcontext
helpviewer_keywords:
- helpcontext attribute
ms.assetid: 6fbb022d-a4b7-4989-a02f-7f18a9b0ad96
ms.openlocfilehash: 8ec13d785ae491a4082d0bbdc908448cb1b8a49c
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69490912"
---
# <a name="helpcontext"></a>helpcontext

**ヘルプ**ファイル内のこの要素に関する情報をユーザーが表示できるようにするコンテキスト ID を指定します。

## <a name="syntax"></a>構文

```cpp
[ helpcontext(id) ]
```

### <a name="parameters"></a>パラメーター

*ID*<br/>
ヘルプトピックのコンテキスト ID。 HTML [ヘルプを参照してください。コンテキスト id の詳細について](../../mfc/html-help-context-sensitive-help-for-your-programs.md)は、プログラムの状況依存のヘルプを参照してください。

## <a name="remarks"></a>Remarks

**Helpcontext** C++属性には、 [helpcontext](/windows/win32/Midl/helpcontext) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

**Helpcontext**の使用例については、 [defaultvalue](defaultvalue.md)の例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**interface**、 **typedef**、 **class**、method、property|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[メソッド属性](method-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[helpfile](helpfile.md)<br/>
[helpstring](helpstring.md)