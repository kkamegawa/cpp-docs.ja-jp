---
title: モジュール (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.module
helpviewer_keywords:
- module attributes
ms.assetid: 02223b2a-62b5-4262-832f-564b1e11e58e
ms.openlocfilehash: bafdb65f255ddf33964d22e5ea80a62446c2ad45
ms.sourcegitcommit: c85c8a1226d8fbbaa29f4691ed719f8e6cc6575c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2019
ms.locfileid: "54893523"
---
# <a name="module-c"></a>module (C++)

.idl ファイルのライブラリ ブロックを定義します。

## <a name="syntax"></a>構文

```cpp
[ module (type=dll, name=string, version=1.0, uuid=uuid, lcid=integer, control=boolean, helpstring=string, helpstringdll=string, helpfile=string, helpcontext=integer, helpstringcontext=integer, hidden=boolean, restricted=boolean, custom=string, resource_name=string,) ];
```

### <a name="parameters"></a>パラメーター

*type*<br/>
(省略可能)次のいずれかを指定できます。

- `dll` 結果の DLL がインプロセス COM サーバーとして機能できるようにする関数およびクラスを追加します。 これが既定値です。

- `exe` 結果を許可する関数およびクラスを追加します。 実行可能ファイルがアウト プロセス COM サーバーとして機能します。

- `service` 結果を許可する関数およびクラスを追加します。 実行可能ファイルが NT サービスとして機能します。

- `unspecified` モジュール属性に関連する ATL コードの挿入を無効にします。 の ATL モジュール クラス、グローバル インスタンス _AtlModule およびエントリ ポイント関数。 プロジェクト内のその他の属性による ATL コードの挿入は無効になりせん。

*name*<br/>
(省略可能)ライブラリ ブロックの名前。

*version*<br/>
(省略可能)ライブラリ ブロックを割り当てるバージョン番号です。 既定値は 1.0 です。

*uuid*<br/>
ライブラリの一意の ID です。 このパラメーターを省略した場合、ライブラリの ID は自動的に生成されます。 取得する必要があります、 *uuid* 、識別子を使用して行うことができます、ライブラリ ブロックの **_ _uuidof (** *libraryname* **)** します。

*lcid*<br/>
ローカリゼーション パラメーターです。 詳細については、「 [lcid](/windows/desktop/Midl/lcid) 」を参照してください。

*control*<br/>
(省略可能)ライブラリ内のすべてのコクラスのコントロールを指定します。

*helpstring*<br/>
タイプ ライブラリを指定します。

*helpstringdll*<br/>
(省略可能)使用してドキュメントの文字列検索を実行する .dll ファイルの名前を設定します。 詳細については、「 [helpstringdll](/windows/desktop/Midl/helpstringdll) 」を参照してください。

*helpfile*<br/>
(省略可能)名前、**ヘルプ**タイプ ライブラリ ファイル。

*helpcontext*<br/>
(省略可能)**ヘルプ ID**このタイプ ライブラリ。

*helpstringcontext*<br/>
(省略可能)参照してください[helpstringcontext](helpstringcontext.md)詳細についてはします。

*hidden*<br/>
(省略可能)ライブラリ全体が表示されないようにします。 これは、コントロールと共に使用します。 ホストは、拡張プロパティを使用し、コントロールをラップする新しいタイプ ライブラリを作成する必要があります。 詳細については、「 [hidden](/windows/desktop/Midl/hidden) 」の MIDL 属性に関する説明を参照してください。

*restricted*<br/>
(省略可能)ライブラリのメンバーは、任意に呼び出すことはできません。 詳細については、「 [restricted](/windows/desktop/Midl/restricted) 」の MIDL 属性に関する説明を参照してください。

*custom*<br/>
(省略可能)1 つまたは複数の属性です。これに似ています、[カスタム](custom-cpp.md)属性。 最初のパラメーター*カスタム*属性の GUID です。 例:

```
[module(custom={guid,1}, custom={guid1,2})]
```

*resource_name*<br/>
DLL、実行可能ファイルまたはサービスの登録に使用される .rgs ファイルの文字列リソース ID です。 モジュールがタイプ サービスである場合、この引数はサービス名を含む文字列の ID の取得にも使用されます。

> [!NOTE]
> .rgs ファイルとサービス名を含む文字列の両方に、同じ数値が必要です。

## <a name="remarks"></a>Remarks

*restricted* パラメーターを [emitidl](emitidl.md)に指定した場合を除き、C++ 属性を使用するすべてのプログラムで **module** が必要です。

ライブラリ ブロックは、ソース コードで、 **module** 属性に加え、 [dispinterface](dispinterface.md)、 [dual](dual.md)、 [object](object-cpp.md)、または [coclass](coclass.md)を意味する属性も使用されている場合に作成されます。

.idl ファイルでは、1 つのライブラリ ブロックが許可されています。 ソース コードに複数のモジュールのエントリがある場合、実装されている最新のパラメーター値と結合されます。

この属性が ATL を使用するプロジェクト内で使用されている場合、属性の動作は変わります。 上記の動作に加え、属性も挿入のグローバル オブジェクト (と呼ばれる`_AtlModule`) の正しい型およびその他のサポート コード。 属性がスタンドアロンの場合、正しいモジュールの種類から派生したクラスが挿入されます。 属性がクラスに適用された場合、正しいモジュールの種類の基本クラスが追加されます。 適切な型がの値によって決まりますが、*型*パラメーター。

- `type` = **dll**

   [CAtlDllModuleT](../../atl/reference/catldllmodulet-class.md) は COM サーバーに必要な基本クラスと標準の DLL エントリ ポイントとして使用されます。 これらのエントリ ポイントは、 [DllMain](/windows/desktop/Dlls/dllmain)、 [DllRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllregisterserver)、 [DllUnRegisterServer](/windows/desktop/api/olectl/nf-olectl-dllunregisterserver)、 [DllCanUnloadNow](/windows/desktop/api/combaseapi/nf-combaseapi-dllcanunloadnow)、および [DllGetClassObject](https://msdn.microsoft.com/library/windows/desktop/dd797891)です。

- `type` = **exe**

   [CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md) は、基本クラスおよび標準の実行可能ファイルのエントリ ポイント [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)として使用されます。

- `type` = **service**

   [CAtlServiceModuleT](../../atl/reference/catlservicemodulet-class.md) は、基本クラスおよび標準の実行可能ファイルのエントリ ポイント [WinMain](/windows/desktop/api/winbase/nf-winbase-winmain)として使用されます。

- `type` = **unspecified**

   モジュール属性と関連する ATL コードの挿入を無効にします。

## <a name="example"></a>例

生成された .idl ファイルにライブラリ ブロックを作成する方法を次のコードで示します。

```cpp
// cpp_attr_ref_module1.cpp
// compile with: /LD
[module(name="MyLibrary", version="1.2", helpfile="MyHelpFile")];
```

次のコードは、 **module**を使用した結果、挿入されたコード内に表示される独自の関数を実装できることを示しています。 挿入されたコードを参照する方法の詳細については、「 [/Fx](../../build/reference/fx-merge-injected-code.md) 」を参照してください。 **module** 属性によって挿入された関数の 1 つをオーバーライドするには、実装した関数を含めるクラスを作成し、そのクラスに **module** 属性を含めます。

```cpp
// cpp_attr_ref_module2.cpp
// compile with: /LD /link /OPT:NOREF
#include <atlbase.h>
#include <atlcom.h>
#include <atlwin.h>
#include <atltypes.h>
#include <atlctl.h>
#include <atlhost.h>
#include <atlplus.h>

// no semicolon after attribute block
[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]
// module attribute now applies to this class
class CMyClass {
public:
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {
   // add your own code here
   return __super::DllMain(dwReason, lpReserved);
   }
};
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
[クラス属性](class-attributes.md)<br/>
[スタンドアロン属性](stand-alone-attributes.md)<br/>
[Typedef、Enum、Union、および Struct 型の属性](typedef-enum-union-and-struct-attributes.md)<br/>
[usesgetlasterror](usesgetlasterror.md)<br/>
[ライブラリ](/windows/desktop/Midl/library)<br/>
[helpcontext](helpcontext.md)<br/>
[helpstring](helpstring.md)<br/>
[helpfile](helpfile.md)<br/>
[version](version-cpp.md)