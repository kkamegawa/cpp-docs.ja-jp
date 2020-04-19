---
title: uuid (C++ 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.uuid
helpviewer_keywords:
- uuid attribute
ms.assetid: 90562a94-5e28-451b-a4b0-cadda7f66efe
ms.openlocfilehash: d644f59ac92bf4e39f191c291dd4fef626411c3d
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514953"
---
# <a name="uuid-c-attributes"></a>uuid (C++ 属性)

クラスまたはインターフェイスの一意の ID を指定します。

## <a name="syntax"></a>構文

```cpp
[ uuid(
   "uuid"
) ]
```

### <a name="parameters"></a>パラメーター

*uuid*<br/>
128ビットの一意の識別子。

## <a name="remarks"></a>Remarks

インターフェイスまたはクラスの定義で**uuid** C++属性が指定されていない場合はC++ 、Microsoft コンパイラによって指定されます。 **Uuid**を指定する場合は、引用符を含める必要があります。

**Uuid**を指定しないと、コンピューター上の異なる属性プロジェクトで同じ名前を持つインターフェイスまたはクラスに対して、コンパイラによって同じ GUID が生成されます。

Uuidgen.exe または Guidgen.exe を使用して、独自の一意の Id を生成できます。 (これらのツールのいずれかを実行するには、 **[スタート]** ボタンをクリックし、メニューの **[実行]** をクリックします。 次に、必要なツールの名前を入力します)。

ATL を使用しないプロジェクトで使用する場合、 **uuid**属性を指定することは、 [uuid](../../cpp/uuid-cpp.md) **__declspec**修飾子を指定することと同じです。 クラスの**uuid**を取得するには、 [__uuidof](../../cpp/uuidof-operator.md)を使用します。

## <a name="example"></a>例

**Uuid**の使用例については、[バインド](bindable.md)可能な例を参照してください。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**class**、 **struct**、 **interface**、 **union**、**列挙型**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[インターフェイス属性](interface-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[uuid](/windows/win32/Midl/uuid)