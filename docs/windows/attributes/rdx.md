---
title: rdx (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.rdx
helpviewer_keywords:
- rdx attribute
ms.assetid: ff8e4312-c1ad-4934-bdaa-86f54409651e
ms.openlocfilehash: 2790c3de01d21242daee73fc442ad22d88739355
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62407498"
---
# <a name="rdx"></a>rdx

レジストリ キーを作成または既存のレジストリ キーを変更します。

## <a name="syntax"></a>構文

```cpp
[ rdx(key, valuename=NULL, regtype) ]
```

### <a name="parameters"></a>パラメーター

*key*<br/>
作成または開かれたキーの名前。

*valuename*<br/>
(省略可能)設定する値のフィールドを指定します。 キーにもこの名前の値のフィールドがまだ存在しない場合は、追加されます。

*regtype*<br/>
追加されるレジストリ キーの型。 次のいずれかを指定できます: `text`、 `dword`、 `binary`、または`CString`します。

## <a name="remarks"></a>Remarks

**Rdx** C++ 属性を作成または既存の COM コンポーネントのレジストリ キーを変更します。 属性は、対象のメンバーを実装するオブジェクトに BEGIN_RDX_MAP マクロを追加します。 `RegistryDataExchange`、レジストリおよびデータ メンバーの間でデータを転送する、BEGIN_RDX_MAP マクロした結果、挿入関数を使用できます

この属性を組み合わせて使用することができます、[コクラス](coclass.md)、 [progid](progid.md)、または[vi_progid](vi-progid.md)属性または他の属性をこれらのいずれかを意味します。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**または**構造体**メンバー|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="example"></a>例

次のコードは、CMyClass COM コンポーネントを記述するシステム プロパティと呼ばれるレジストリ キーを追加します。

```cpp
// cpp_attr_ref_rdx.cpp
// compile with: /LD /link /OPT:NOREF
#define _ATL_ATTRIBUTES
#include "atlbase.h"

[module (name="MyLib")];

class CMyClass {
public:
   CMyClass() {
      strcpy_s(m_sz, "SomeValue");
   }

   [ rdx(key = "HKCR\\MyApp.MyApp.1", valuename = "MyValue", regtype = "text")]
   char m_sz[256];
};
```

## <a name="see-also"></a>関連項目

[COM 属性](com-attributes.md)<br/>
[registration_script](registration-script.md)