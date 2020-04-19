---
title: include (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.include
helpviewer_keywords:
- include attribute
ms.assetid: d23f8b91-fe5b-48fa-9371-8bd73af7b8e3
ms.openlocfilehash: ece88ebd7b5d9d81beb871427b58a72b2cf02022
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69514556"
---
# <a name="include-c"></a>include (C++)

生成される .idl ファイルに含める1つ以上のヘッダーファイルを指定します。

## <a name="syntax"></a>構文

```cpp
[ include(header_file) ];
```

### <a name="parameters"></a>パラメーター

*header_file*<br/>
生成された .idl ファイルに追加するファイルの名前。

## <a name="remarks"></a>Remarks

**Include** C++ `import "docobj.idl"`属性を指定すると、ステートメントが生成された.idlファイル内のステートメントの下に配置されます。`#include`

**Include** C++属性には、 [include](/windows/win32/Midl/include) MIDL 属性と同じ機能があります。

## <a name="example"></a>例

次のコードは、 **include**を使用する方法の例を示しています。 この例では、ファイルには`#include`ステートメントだけが含まれています。

```cpp
// cpp_attr_ref_include.cpp
// compile with: /LD
[module(name="MyLib")];
[include(cpp_attr_ref_include.h)];
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|任意の場所|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[スタンドアロン属性](stand-alone-attributes.md)<br/>
[import](import.md)<br/>
[importidl](importidl.md)<br/>
[includelib](includelib-cpp.md)<br/>
[importlib](importlib.md)