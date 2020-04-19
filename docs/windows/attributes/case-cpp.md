---
title: ケース (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.case
helpviewer_keywords:
- case attribute
ms.assetid: 6fb883c3-0526-4932-a901-b4564dcaeb7d
ms.openlocfilehash: b3058f2fe6f35e1b11d4790780cb0fcdcaada706
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148446"
---
# <a name="case-c"></a>case (C++)

使用される、 [switch_type](switch-type.md)属性、**union**します。

## <a name="syntax"></a>構文

```cpp
[ case(value) ]
```

#### <a name="parameters"></a>パラメーター

*value*<br/>
入力の処理を提供する値。 型**値**次の種類のいずれかを指定できます。

- `int`

- `char`

- `boolean`

- `enum`

または、このような種類の識別子。

## <a name="remarks"></a>Remarks

**ケース**C++ 属性と同じ機能を持つ、**ケース**MIDL 属性。 この属性でのみ使用、 [switch_type](switch-type.md)属性。

## <a name="example"></a>例

次のコードの使い方を示しています、**ケース**属性。

```cpp
// cpp_attr_ref_case.cpp
// compile with: /LD
#include <unknwn.h>
[export]
struct SizedValue2 {
   [switch_type(char), switch_is(kind)] union {
      [case(1), string]
          wchar_t* wval;
      [default, string]
          char* val;
   };
    char kind;
};
[module(name="ATLFIRELib")];
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|メンバー、**クラス**または**構造体**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[クラス属性](class-attributes.md)