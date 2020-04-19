---
title: com_interface_entry (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.com_interface_entry
helpviewer_keywords:
- com_interface_entry attribute
ms.assetid: 10368f81-b99b-4a0f-ba4f-a142e6911a5c
ms.openlocfilehash: 65d174679f851613e064568b071cfcbdad8f0f06
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148264"
---
# <a name="cominterfaceentry-c"></a>com_interface_entry (C++)

ターゲット クラスの COM マップにインターフェイス エントリを追加します。

## <a name="syntax"></a>構文

```cpp
[ com_interface_entry(
  com_interface_entry) ]
```

### <a name="parameters"></a>パラメーター

*com_interface_entry*<br/>
エントリの実際のテキストを含む文字列。 使用可能な値の一覧は、次を参照してください。 [COM_INTERFACE_ENTRY マクロ](../../atl/reference/com-interface-entry-macros.md)します。

## <a name="remarks"></a>Remarks

**Com_interface_entry** C++属性は、ターゲット オブジェクトの COM インターフェイス マップに unabridged 文字の文字列の内容を挿入します。 属性は、ターゲット オブジェクトに 1 回適用されている場合、エントリは、既存のインターフェイス マップの先頭に挿入されます。 属性は、同じターゲット オブジェクトを繰り返し適用されている場合、エントリが受信される順序でインターフェイス マップの先頭に挿入されます。

この属性を使用するには、 [coclass](coclass.md)、 [progid](progid.md)、または [vi_progid](vi-progid.md) 属性 (または、これらのいずれかを意味する別の属性) も同じ要素に適用する必要があります。 いずれか 1 つの属性を使用すると、他の 2 つも自動的に適用されます。 たとえば場合、`progid`が適用される`vi_progid`と`coclass`も適用されます。

の最初の使用**com_interface_entry**インターフェイス マップの先頭に挿入する新しいインターフェイスにより COM_INTERFACE_ENTRY 種類は次のいずれかの必要があります。

- COM_INTERFACE_ENTRY

- COM_INTERFACE_ENTRY_IID

- COM_INTERFACE_ENTRY2

- COM_INTERFACE_ENTRY2_IID

追加の使用法、 **com_interface_entry**属性はサポートされているすべての COM_INTERFACE_ENTRY 型を使用できます。

この制限は、ATL は、id とインターフェイス マップに最初のエントリを使用するために必要な`IUnknown`。 したがって、エントリは有効なインターフェイスである必要があります。 たとえば、次のコード サンプルがインターフェイス マップの最初のエントリで、実際の COM インターフェイスが指定されていないため無効です。

```cpp
[ coclass, com_interface_entry =
    "COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"
]
   class CMyClass
   {
   };
```

## <a name="example"></a>例

次のコードでは、2 つのエントリを追加するは、既存の COM インターフェイス マップ`CMyBaseClass`します。 1 つは、標準のインターフェイスと、2 つ目の非表示になります、`IDebugTest`インターフェイス。

```cpp
// cpp_attr_ref_com_interface_entry.cpp
// compile with: /LD
#define _ATL_ATTRIBUTES
#include "atlbase.h"
#include "atlcom.h"

[module (name ="ldld")];

[ object,
  uuid("7dbebed3-d636-4917-af62-c767a720a5b9")]
__interface IDebugTest{};

[ object,
  uuid("2875ceac-f94b-4087-8e13-d13dc167fcfc")]
__interface IMyClass{};

[ coclass,
  com_interface_entry ("COM_INTERFACE_ENTRY (IMyClass)"),
  com_interface_entry ("COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)"),
  uuid("b85f8626-e76e-4775-b6a0-4826a9e94af2")
]

class CMyClass: public IMyClass, public IDebugTest
{
};
```

結果として得られる COM オブジェクト マップ`CMyBaseClass`のとおりです。

```cpp
BEGIN_COM_MAP(CMyClass)
    COM_INTERFACE_ENTRY (IMyClass)
    COM_INTERFACE_ENTRY_NOINTERFACE(IDebugTest)
    COM_INTERFACE_ENTRY(IMyClass)
    COM_INTERFACE_ENTRY2(IDispatch, IMyClass)
    COM_INTERFACE_ENTRY(IDebugTest)
    COM_INTERFACE_ENTRY(IProvideClassInfo)
END_COM_MAP()
```

## <a name="requirements"></a>要件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**|
|**反復可能**|はい|
|**必要な属性**|次のいずれかまたは: `coclass`、 `progid`、または`vi_progid`します。|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[COM 属性](com-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)