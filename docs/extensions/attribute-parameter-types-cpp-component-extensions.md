---
title: 属性のパラメーターの型 (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- custom attributes, parameter types
ms.assetid: d9f127a3-7f08-456f-acc6-256805632712
ms.openlocfilehash: fbb2bd68f589630608e341b944b4201c12d67211
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65516177"
---
# <a name="attribute-parameter-types--ccli-and-ccx"></a>属性のパラメーターの型 (C++/CLI および C++/CX)

コンパイル時に、属性に渡される値をコンパイラに通知する必要があります。  属性のパラメーターには、次のいずれかの型を指定できます。

- **bool**

- **char**、**unsigned char**

- **short**、**unsigned short**

- **int**、**unsigned int**

- **long**、**unsigned long**

- **__int64**、**unsigned __int64**

- **float**、**double**

- **wchar_t**

- `char*` または `wchar_t*` または `System::String*`

- `System::Type ^`

- `System::Object ^`

- **enum**

## <a name="example"></a>例

### <a name="code"></a>コード

```cpp
// attribute_parameter_types.cpp
// compile with: /clr /c
using namespace System;
ref struct AStruct {};

[AttributeUsage(AttributeTargets::ReturnValue)]
ref struct Attr : public Attribute {
   Attr(AStruct ^ i){}
   Attr(bool i){}
   Attr(){}
};

ref struct MyStruct {
   static AStruct ^ x = gcnew AStruct;
   [returnvalue:Attr(x)] int Test() { return 0; }   // C3104
   [returnvalue:Attr] int Test2() { return 0; }   // OK
   [returnvalue:Attr(true)] int Test3() { return 0; }   // OK
};
```

## <a name="example"></a>例

### <a name="description"></a>説明

属性を指定するときは、すべての名前付き引数の前に、すべての名前のない (位置) 引数を指定する必要があります。

### <a name="code"></a>コード

```cpp
// extending_metadata_c.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class)]
ref class MyAttr : public Attribute {
public:
   MyAttr() {}
   MyAttr(int i) {}
   property int Priority;
   property int Version;
};

[MyAttr]
ref class ClassA {};   // No arguments

[MyAttr(Priority = 1)]
ref class ClassB {};   // Named argument

[MyAttr(123)]
ref class ClassC {};   // Positional argument

[MyAttr(123, Version = 1)]
ref class ClassD {};   // Positional and named
```

## <a name="example"></a>例

### <a name="description"></a>説明

属性のパラメーターには、前述の型の 1 次元の配列を指定できます。

### <a name="code"></a>コード

```cpp
// extending_metadata_d.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::Class)]
public ref struct ABC : public Attribute {
   ABC(array<int>^){}
   array<double> ^ param;
};

[ABC( gcnew array<int> {1,2,3}, param = gcnew array<double>{2.71, 3.14})]
ref struct AStruct{};
```

## <a name="see-also"></a>関連項目

[ユーザー定義の属性](user-defined-attributes-cpp-component-extensions.md)