---
title: コクラス (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.coclass
helpviewer_keywords:
- coclass attribute
ms.assetid: 42da6a10-3af9-4b43-9a1d-689d00b61eb3
ms.openlocfilehash: e1f99a2780ab4f451533a3e797e473f60680c6ab
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62148290"
---
# <a name="coclass"></a>coclass

COM インターフェイスを実装できる COM オブジェクトを作成します。

## <a name="syntax"></a>構文

```cpp
[coclass]
```

## <a name="remarks"></a>Remarks

**コクラス**C++ 属性は、生成された .idl ファイルのコクラス構成要素を配置します。

コクラスを定義するときに指定することも、 [uuid](uuid-cpp-attributes.md)、[バージョン](version-cpp.md)、[スレッド](threading-cpp.md)、 [vi_progid](vi-progid.md)、および[progid](progid.md)属性。 いずれかのファイルが指定されていない場合は、それが生成されます。

2 つのヘッダー ファイルには、クラスが含まれている場合、**コクラス**属性し、GUID を指定しない MIDL エラーが発生して、コンパイラが両方のクラスで同じ GUID を使用します。  したがって、使用する必要があります、`uuid`属性を使用するときに**コクラス**します。

**ATL プロジェクト**

この属性は、ATL プロジェクトでは、クラスまたは構造体の定義を前に。

- オブジェクトの自動登録をサポートするコードまたはデータを挿入します。

- オブジェクトの COM クラス ファクトリをサポートするコードまたはデータを挿入します。

- コードまたは実装するためにデータが挿入`IUnknown`と COM で作成可能オブジェクトのオブジェクトを作成します。

具体的には、次の基本クラスは、ターゲット オブジェクトに追加されます。

- [CComCoClass クラス](../../atl/reference/ccomcoclass-class.md)オブジェクトの既定のクラス ファクトリと集計モデルを提供します。

- [CComObjectRootEx クラス](../../atl/reference/ccomobjectrootex-class.md)テンプレートがで指定されたスレッド処理モデル クラスに基づいて、[スレッド](threading-cpp.md)属性。 場合、`threading`属性が指定されていない、既定のスレッド モデルがアパートメント。

- [IProvideClassInfo2Impl](../../atl/reference/iprovideclassinfo2impl-class.md)場合は、追加、 [noncreatable](noncreatable.md)ターゲット オブジェクトの属性が指定されていません。

最後に、埋め込み IDL で定義されていない任意のデュアル インターフェイスは、対応するのに置き換えられます[IDispatchImpl](../../atl/reference/idispatchimpl-class.md)クラス。 デュアル インターフェイスは、埋め込み IDL で定義されているが、基底のリストで特定のインターフェイスは変更されません。

**コクラス**属性もご利用、次の関数またはの場合、挿入されたコードを使用して`GetObjectCLSID`、基底クラスの静的メソッドとして`CComCoClass`:

- `UpdateRegistry` ターゲット クラスのクラス ファクトリを登録します。

- `GetObjectCLSID`、、登録に関連することもでき、ターゲット クラスの CLSID を取得します。

- `GetObjectFriendlyName` 既定の形式の文字列を返します"\<*対象のクラス名*> `Object`"。 この関数が既に存在する場合は追加されません。 自動的に生成されたものよりもわかりやすい名前を返す対象のクラスには、この関数を追加します。

- `GetProgID`、で指定された文字列を返します、登録に関連する、 [progid](progid.md)属性。

- `GetVersionIndependentProgID` 同じ機能を持つ`GetProgID`で指定された文字列を返しますが、 [vi_progid](vi-progid.md)します。

次の変更は、COM マップに関連する、ターゲット クラスに対して与えられます。

- COM マップが追加され、ターゲット クラスから派生するすべてのインターフェイスのエントリとで指定されたすべてのエントリが、 [COM インターフェイス エントリ ポイント](../../mfc/com-interface-entry-points.md)属性またはで必要な[集計](aggregates.md)属性。

- [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto)マクロは、COM マップに挿入されます。

クラスの .idl ファイル内に生成されるコクラスの名前は、クラスと同じ名前になります。  たとえばとをコクラスのクラス ID へのアクセスに、次の例を参照する`CMyClass`、MIDL によって生成されたヘッダー ファイルをクライアントでは、次のように使用します。`CLSID_CMyClass`します。

## <a name="example"></a>例

次のコードを使用する方法を示しています、**コクラス**属性。

```cpp
// cpp_attr_ref_coclass1.cpp
// compile with: /LD
#include "unknwn.h"
[module(name="MyLib")];

[ object, uuid("00000000-0000-0000-0000-000000000001") ]
__interface I {
   HRESULT func();
};

[coclass, progid("MyCoClass.coclass.1"), vi_progid("MyCoClass.coclass"),
appobject, uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")]
class CMyClass : public I {};
```

次の例は、によって挿入されたコードに表示される関数の既定の実装をオーバーライドする方法を示します、**コクラス**属性。 挿入されたコードを参照する方法の詳細については、「 [/Fx](../../build/reference/fx-merge-injected-code.md) 」を参照してください。 すべての基底クラスまたはクラスを使用するインターフェイスは、挿入されたコードに表示されます。 さらに、クラスが挿入されたコードで既定で含まれている、明示的に指定するクラスをベースとして、コクラスの場合は、属性プロバイダーは、コードで指定された形式を使用します。

```cpp
// cpp_attr_ref_coclass2.cpp
// compile with: /LD
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

[module(name="MyLib")];

[object, uuid("00000000-0000-0000-0000-000000000000")]
__interface bb {};

[coclass, uuid("00000000-0000-0000-0000-000000000001")]
class CMyClass : public bb {
public:
   // by adding the definition of UpdateRegistry to your code, // the function will not be included in the injected code
   static HRESULT WINAPI UpdateRegistry(BOOL bRegister) {
      // you can add to the default implementation
      CRegistryVirtualMachine rvm;
      HRESULT hr;
      if (FAILED(hr = rvm.AddStandardReplacements()))
         return hr;
      rvm.AddReplacement(_T("FriendlyName"), GetObjectFriendlyName());
      return rvm.VMUpdateRegistry(GetOpCodes(), GetOpcodeStringVals(),       GetOpcodeDWORDVals(), GetOpcodeBinaryVals(), bRegister);
   }
};
```

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**|
|**反復可能**|いいえ|
|**必要な属性**|なし|
|**無効な属性**|なし|

属性コンテキストの詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[COM 属性](com-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[appobject](appobject.md)