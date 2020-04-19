---
title: __interface
ms.date: 05/07/2019
f1_keywords:
- __interface_cpp
helpviewer_keywords:
- __interface keyword [C++]
ms.assetid: ca5d400b-d6d8-4ba2-89af-73f67e5ec056
ms.openlocfilehash: 7c95e3700b4124c4793e0214ed3b06ecfeee72f1
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65222081"
---
# <a name="interface"></a>__interface

**Microsoft 固有の仕様**

MicrosoftC++インターフェイスは、次のように定義できます。

- 0 個以上の基本インターフェイスから継承できます。

- 基底クラスから継承することはできません。

- パブリックな純粋仮想メソッドのみを含めることができます。

- コンストラクター、デストラクター、または演算子を含めることはできません。

- 静的メソッドを含めることはできません。

- データ メンバーを含めることはできません。プロパティは使用できます。

## <a name="syntax"></a>構文

```
modifier __interface interface-name {interface-definition};
```

## <a name="remarks"></a>Remarks

A C++ [クラス](../cpp/class-cpp.md)または[構造体](../cpp/struct-cpp.md)これらの規則を実装できますが、 **_ _interface**それらを適用します。

次にインターフェイスの定義例を示します。

```cpp
__interface IMyInterface {
   HRESULT CommitX();
   HRESULT get_X(BSTR* pbstrName);
};
```

マネージ インターフェイスについては、次を参照してください。[インターフェイス クラス](../extensions/interface-class-cpp-component-extensions.md)します。

`CommitX` 関数と `get_X` 関数が純粋仮想関数であることを明示的に示す必要がないことに注意してください。 最初の関数の同等の宣言は次のとおりです。

```cpp
virtual HRESULT CommitX() = 0;
```

**_ _interface**意味、 [novtable](../cpp/novtable.md) **_ _declspec**修飾子。

## <a name="example"></a>例

次の例では、インターフェイスで宣言されたプロパティを使用する方法を示します。

```cpp
// deriv_interface.cpp
#define _ATL_ATTRIBUTES 1
#include <atlbase.h>
#include <atlcom.h>
#include <string.h>
#include <comdef.h>
#include <stdio.h>

[module(name="test")];

[ object, uuid("00000000-0000-0000-0000-000000000001"), library_block ]
__interface IFace {
   [ id(0) ] int int_data;
   [ id(5) ] BSTR bstr_data;
};

[ coclass, uuid("00000000-0000-0000-0000-000000000002") ]
class MyClass : public IFace {
private:
    int m_i;
    BSTR m_bstr;

public:
    MyClass()
    {
        m_i = 0;
        m_bstr = 0;
    }

    ~MyClass()
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
    }

    int get_int_data()
    {
        return m_i;
    }

    void put_int_data(int _i)
    {
        m_i = _i;
    }

    BSTR get_bstr_data()
    {
        BSTR bstr = ::SysAllocString(m_bstr);
        return bstr;
    }

    void put_bstr_data(BSTR bstr)
    {
        if (m_bstr)
            ::SysFreeString(m_bstr);
        m_bstr = ::SysAllocString(bstr);
    }
};

int main()
{
    _bstr_t bstr("Testing");
    CoInitialize(NULL);
    CComObject<MyClass>* p;
    CComObject<MyClass>::CreateInstance(&p);
    p->int_data = 100;
    printf_s("p->int_data = %d\n", p->int_data);
    p->bstr_data = bstr;
    printf_s("bstr_data = %S\n", p->bstr_data);
}
```

```Output
p->int_data = 100
bstr_data = Testing
```

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[キーワード](../cpp/keywords-cpp.md)<br/>
[インターフェイス属性](../windows/attributes/interface-attributes.md)