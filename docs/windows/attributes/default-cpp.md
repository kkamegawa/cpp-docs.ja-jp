---
title: default (C++ COM 属性)
ms.date: 10/02/2018
f1_keywords:
- vc-attr.default
helpviewer_keywords:
- default attribute
- attributes [C#], default attribute
- defaults, default attribute
ms.assetid: 0cdca716-1ba8-46d7-9399-167e55492870
ms.openlocfilehash: 291e16ad0967acd1869874fcc9fa6eb5529e4b44
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69501682"
---
# <a name="default-c"></a>default (C++)

コクラス内で定義されるカスタムまたはディスパッチ インターフェイスが既定のプログラミング インターフェイスを表すことを示します。

## <a name="syntax"></a>構文

```cpp
[ default(interface1, interface2) ]
```

### <a name="parameters"></a>パラメーター

*interface1*<br/>
**default** 属性で定義されているクラスに基づいてオブジェクトを作成するスクリプト環境で使用可能になる既定のインターフェイス。

既定のインターフェイスが指定されていない場合は、最初に見つかったソース以外のインターフェイスが既定値として使用されます。

*interface2*<br/>
Optional既定のソースインターフェイス。 このインターフェイスを指定する場合は、 [source](source-cpp.md) 属性も使用する必要があります。

既定のソース インターフェイスが指定されていない場合は、最初のソース インターフェイスが既定値として使用されます。

## <a name="remarks"></a>Remarks

**default** C++ 属性には、 [default](/windows/win32/Midl/default) MIDL 属性と同じ機能があります。 また、 **default** 属性は、 [case](case-cpp.md) 属性と共に使用されます。

## <a name="example"></a>例

次のコードは、既定のプログラミングインターフェイスとしてを指定`ICustomDispatch`するために、コクラスの定義で default を使用する方法を示しています。

```cpp
// cpp_attr_ref_default.cpp
// compile with: /LD
#include "windows.h"
[module(name="MyLibrary")];

[object, uuid("9E66A290-4365-11D2-A997-00C04FA37DDB")]
__interface ICustom {
   HRESULT Custom([in] long l, [out, retval] long *pLong);
};

[dual, uuid("9E66A291-4365-11D2-A997-00C04FA37DDB")]
__interface IDual {
   HRESULT Dual([in] long l, [out, retval] long *pLong);
};

[object, uuid("9E66A293-4365-11D2-A997-00C04FA37DDB")]
__interface ICustomDispatch : public IDispatch {
   HRESULT Dispatch([in] long l, [out, retval] long *pLong);
};

[   coclass, default(ICustomDispatch), source(IDual), uuid("9E66A294-4365-11D2-A997-00C04FA37DDB")
]
class CClass : public ICustom, public IDual, public ICustomDispatch {
   HRESULT Custom(long l, long *pLong) { return(S_OK); }
   HRESULT Dual(long l, long *pLong) { return(S_OK); }
   HRESULT Dispatch(long l, long *pLong) { return(S_OK); }
};

int main() {
#if 0 // Can't instantiate without implementations of IUnknown/IDispatch
   CClass *pClass = new CClass;

   long llong;

   pClass->custom(1, &llong);
   pClass->dual(1, &llong);
   pClass->dispinterface(1, &llong);
   pClass->dispatch(1, &llong);

   delete pClass;
#endif
   return(0);
}
```

[default](source-cpp.md) の使用例については、「 **source**」も参照してくださいにも含まれています。

## <a name="requirements"></a>必要条件

### <a name="attribute-context"></a>属性コンテキスト

|||
|-|-|
|**対象**|**クラス**、**構造体**、データメンバー|
|**反復可能**|いいえ|
|**必要な属性**|**コクラス**(**クラス**または**構造体**に適用される場合)|
|**無効な属性**|なし|

詳細については、「 [属性コンテキスト](cpp-attributes-com-net.md#contexts)」を参照してください。

## <a name="see-also"></a>関連項目

[IDL 属性](idl-attributes.md)<br/>
[クラス属性](class-attributes.md)<br/>
[coclass](coclass.md)