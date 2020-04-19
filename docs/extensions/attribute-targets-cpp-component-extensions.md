---
title: 属性のターゲット (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, targets
ms.assetid: b4e6e224-da77-4520-b6e6-b96846e0ebc1
ms.openlocfilehash: 502f5ba2e5bbb5bd5a5fcceca16acaa3987db4bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516147"
---
# <a name="attribute-targets-ccli-and-ccx"></a>属性のターゲット (C++/CLI および C++/CX)

属性使用指定子を指定して、属性のターゲットを指定できます。  各属性は、特定の言語要素に適用するように定義されます。 たとえば、クラスと構造体にのみ適用するように属性を定義できます。  カスタム属性を使用できる可能性がある構文要素を次に示します。 これらの値の組み合わせを使用できます (論理演算子などを使用します)。

複数の属性のターゲットを指定するには、属性を定義するときに 1 つまたは複数の <xref:System.AttributeTargets> 列挙子を <xref:System.AttributeUsageAttribute> 属性に渡します。

有効な属性ターゲットの一覧を次に示します。

- `All` (すべての構成要素に適用します)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::All)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Assembly` (全体としてのアセンブリに適用します)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Assembly)]
    ref class Attr : public Attribute {};

    [assembly:Attr];
    ```

- `Module` (全体としてのモジュールに適用します)

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Module)]
    ref class Attr : public Attribute {};

    [module:Attr];
    ```

- `Class`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Class)]
    ref class Attr : public System::Attribute {};

    [Attr]   // same as [class:Attr]
    ref class MyClass {};
    ```

- `Struct`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Struct)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [struct:Attr]
    value struct MyStruct{};
    ```

- `enum`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Enum)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [enum:Attr]
    enum struct MyEnum{e, d};
    ```

- `Constructor`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Constructor)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] MyStruct(){}   // same as [constructor:Attr]
    };
    ```

- `Method`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Method)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] void Test(){}   // same as [method:Attr]
    };
    ```

- `Property`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Property)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] property int Test;   // same as [property:Attr]
    };
    ```

- `Field`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Field)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    [Attr] int Test;   // same as [field:Attr]
    };
    ```

- `Event`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Event)]
    ref class Attr : public Attribute {};

    delegate void ClickEventHandler(int, double);

    ref struct MyStruct{
    [Attr] event ClickEventHandler^ OnClick;   // same as [event:Attr]
    };
    ```

- `Interface`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Interface)]
    ref class Attr : public Attribute {};

    [Attr]   // same as [event:Attr]
    interface struct MyStruct{};
    ```

- `Parameter`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Parameter)]
    ref class Attr : public Attribute {};

    ref struct MyStruct{
    void Test([Attr] int i);
    void Test2([parameter:Attr] int i);
    };
    ```

- `Delegate`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::Delegate)]
    ref class Attr : public Attribute {};

    [Attr] delegate void Test();
    [delegate:Attr] delegate void Test2();
    ```

- `ReturnValue`

    ```cpp
    using namespace System;
    [AttributeUsage(AttributeTargets::ReturnValue)]
    ref class Attr : public Attribute {};

    ref struct MyStruct {
    // Note required specifier
    [returnvalue:Attr] int Test() { return 0; }
    };
    ```

通常、属性は、それが適用される言語要素の直前に配置します。 ただし、場合によっては、意図された属性のターゲットを決定するには属性の位置では不十分です。 次の例について考えます。

```cpp
[Attr] int MyFn(double x)...
```

構文上は、この属性の意図された適用先がメソッドであるかメソッドが返す値であるかを知る方法はありません (この場合は既定値であるメソッドが使用されます)。 このような場合に、属性使用指定子を使用できます。 たとえば、属性を戻り値に適用するには、次のように `returnvalue` 指定子を使用します。

```cpp
[returnvalue:Attr] int MyFn(double x)... // applies to return value
```

属性使用量指定子は、次の状況で必要になります。

- アセンブリまたはモジュール レベルの属性を指定するため。

- 属性が、メソッドではなくメソッドの戻り値に適用されることを指定するため。

    ```cpp
    [method:Attr] int MyFn(double x)...     // Attr applies to method
    [returnvalue:Attr] int MyFn(double x)...// Attr applies to return value
    [Attr] int MyFn(double x)...            // default: method
    ```

- 属性が、プロパティではなくプロパティのアクセサーに適用されることを指定するため。

    ```cpp
    [method:MyAttr(123)] property int Property()
    [property:MyAttr(123)] property int Property()
    [MyAttr(123)] property int get_MyPropy() // default: property
    ```

- 属性が、イベントではなくイベントのアクセサーに適用されることを指定するため。

    ```cpp
    delegate void MyDel();
    ref struct X {
       [field:MyAttr(123)] event MyDel* MyEvent;   //field
       [event:MyAttr(123)] event MyDel* MyEvent;   //event
       [MyAttr(123)] event MyDel* MyEvent;   // default: event
    }
    ```

属性使用指定子は、その直後にある属性にのみ適用されます。つまり、

```cpp
[returnvalue:Attr1, Attr2]
```

は、次の例とは異なります。

```cpp
[returnvalue:Attr1, returnvalue:Attr2]
```

## <a name="example"></a>例

### <a name="description"></a>説明

この例では、複数のターゲットを指定する方法を示します。

### <a name="code"></a>コード

```cpp
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Struct, AllowMultiple = true )]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};

[Attr]
[Attr(true)]
value struct MyStruct {};
```

## <a name="see-also"></a>関連項目

[ユーザー定義の属性](user-defined-attributes-cpp-component-extensions.md)