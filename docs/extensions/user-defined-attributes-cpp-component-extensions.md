---
title: ユーザー定義属性 (C++/CLI および C++/CX)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- metadata, extending
- custom attributes, extending metadata
ms.assetid: 98b29048-a3ea-4698-8441-f149cdaec9fb
ms.openlocfilehash: 6d200c36946e7bc7d441c2c4db1bdfe96d4aeef9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515997"
---
# <a name="user-defined-attributes--ccli-and-ccx"></a>ユーザー定義属性 (C++/CLI および C++/CX)

C++/CLI とC++/CX では、インターフェイス、クラス、構造体、メソッド、パラメーター、または列挙型のメタデータを拡張するプラットフォーム固有の属性を作成できます。 これらの属性は、[標準 C++ 属性](../cpp/attributes.md)とは異なります。

## <a name="windows-runtime"></a>Windows ランタイム

C++/CX 属性は、プロパティに適用できますが、コンストラクターまたはメソッドには適用できません。

### <a name="requirements"></a>要件

コンパイラ オプション: `/ZW`

## <a name="common-language-runtime"></a>共通言語ランタイム

このトピックに示されている情報と構文は、「[属性](../windows/attributes/attribute.md)」に示されている情報に優先します。

型を定義し、<xref:System.Attribute> をその型の基底クラスにすることで、カスタム属性を定義できます。必要に応じて <xref:System.AttributeUsageAttribute> 属性を適用できます。

詳細については次を参照してください:

- [属性の対象](attribute-targets-cpp-component-extensions.md)

- [属性パラメーターの型](attribute-parameter-types-cpp-component-extensions.md)

Visual C++ でのアセンブリへの署名については、「[厳密名アセンブリ (アセンブリ署名) (C++/CLI)](../dotnet/strong-name-assemblies-assembly-signing-cpp-cli.md)」を参照してください。

### <a name="requirements"></a>要件

コンパイラ オプション: `/clr`

### <a name="examples"></a>使用例

次の例では、カスタム属性を定義する方法を示します。

```cpp
// user_defined_attributes.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
ref struct Attr : public Attribute {
   Attr(bool i){}
   Attr(){}
};

[Attr]
ref class MyClass {};
```

次の例では、カスタム属性のいくつかの重要な機能を示します。 たとえば、この例では、カスタム属性の一般的な使用方法を示しています (クライアントに対して自身を完全に記述できるサーバーをインスタンス化します)。

```cpp
// extending_metadata_b.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;

public enum class Access { Read, Write, Execute };

// Defining the Job attribute:
[AttributeUsage(AttributeTargets::Class, AllowMultiple=true )]
public ref class Job : Attribute {
public:
   property int Priority {
      void set( int value ) { m_Priority = value; }
      int get() { return m_Priority; }
   }

   // You can overload constructors to specify Job attribute in different ways
   Job() { m_Access = Access::Read; }
   Job( Access a ) { m_Access = a; }
   Access m_Access;

protected:
   int m_Priority;
};

interface struct IService {
   void Run();
};

   // Using the Job attribute:
   // Here we specify that QueryService is to be read only with a priority of 2.
   // To prevent namespace collisions, all custom attributes implicitly
   // end with "Attribute".

[Job( Access::Read, Priority=2 )]
ref struct QueryService : public IService {
   virtual void Run() {}
};

// Because we said AllowMultiple=true, we can add multiple attributes
[Job(Access::Read, Priority=1)]
[Job(Access::Write, Priority=3)]
ref struct StatsGenerator : public IService {
   virtual void Run( ) {}
};

int main() {
   IService ^ pIS;
   QueryService ^ pQS = gcnew QueryService;
   StatsGenerator ^ pSG = gcnew StatsGenerator;

   //  use QueryService
   pIS = safe_cast<IService ^>( pQS );

   // use StatsGenerator
   pIS = safe_cast<IService ^>( pSG );

   // Reflection
   MemberInfo ^ pMI = pIS->GetType();
   array <Object ^ > ^ pObjs = pMI->GetCustomAttributes(false);

   // We can now quickly and easily view custom attributes for an
   // Object through Reflection */
   for( int i = 0; i < pObjs->Length; i++ ) {
      Console::Write("Service Priority = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->Priority);
      Console::Write("Service Access = ");
      Console::WriteLine(static_cast<Job^>(pObjs[i])->m_Access);
   }
}
```

```Output
Service Priority = 0

Service Access = Write

Service Priority = 3

Service Access = Write

Service Priority = 1

Service Access = Read
```

`Object^` 型によって、バリアント データ型が置換されます。 次の例では、`Object^` の配列をパラメーターとして受け取るカスタム属性を定義します。

属性の引数はコンパイル時の定数である必要があります。ほとんどの場合、それらは定数リテラルになります。

カスタム属性ブロックから System::Type の値を返す方法については、[typeid](typeid-cpp-component-extensions.md) を参照してください。

```cpp
// extending_metadata_e.cpp
// compile with: /clr /c
using namespace System;
[AttributeUsage(AttributeTargets::Class | AttributeTargets::Method)]
public ref class AnotherAttr : public Attribute {
public:
   AnotherAttr(array<Object^>^) {}
   array<Object^>^ var1;
};

// applying the attribute
[ AnotherAttr( gcnew array<Object ^> { 3.14159, "pi" }, var1 = gcnew array<Object ^> { "a", "b" } ) ]
public ref class SomeClass {};
```

ランタイムでは、カスタム属性クラスのパブリック部分がシリアル化可能である必要があります。  カスタム属性を作成する場合、カスタム属性の名前付き引数はコンパイル時の定数に限定されます  (メタデータのクラスのレイアウトに追加される一連のビットと考えてください)。

```cpp
// extending_metadata_f.cpp
// compile with: /clr /c
using namespace System;
ref struct abc {};

[AttributeUsage( AttributeTargets::All )]
ref struct A : Attribute {
   A( Type^ ) {}
   A( String ^ ) {}
   A( int ) {}
};

[A( abc::typeid )]
ref struct B {};
```

## <a name="see-also"></a>関連項目

[.NET および UWP でのコンポーネント拡張](component-extensions-for-runtime-platforms.md)