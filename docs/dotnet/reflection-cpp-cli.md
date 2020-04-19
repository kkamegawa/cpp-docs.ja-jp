---
title: リフレクション (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- typeid keyword [C++]
- reflection [C++}, about reflection
- metadata, reflection
- GetType method
- .NET Framework [C++], reflection
- data types [C++], reflection
- reflection [C++}
- plug-ins [C++]
- reflection [C++}, plug-ins
- assemblies [C++], enumerating data types in
- public types [C++]
- reflection [C++], external assemblies
- assemblies [C++]
- data types [C++], enumerating
- public members [C++]
ms.assetid: 46b6ff4a-e441-4022-8892-78e69422f230
ms.openlocfilehash: 5f18a7faa4e77571a87cc0d76a43240aaf1fd52c
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65447225"
---
# <a name="reflection-ccli"></a>リフレクション (C++/CLI)

リフレクションでは、既知のデータ型を実行時に調査できます。 リフレクションでは、アセンブリに含まれているデータ型を列挙したり、クラス型や値型のメンバーを探索したりできます。 この処理は、コンパイル時に型が認識または参照された場合のどちらにも対応できます。 そのため、リフレクションは、開発およびコード管理ツール向けの便利な機能です。

指定されたアセンブリ名が厳密な名前に注意してください (を参照してください[の作成と using strong-named Assemblies](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies))、アセンブリのバージョン、カルチャ、および署名情報が含まれます。 また、基底クラスの名前に加えて、データ型が定義されている名前空間の名前も取得できることに注目してください。

リフレクションの機能にアクセスする最も一般的な方法は、<xref:System.Object.GetType%2A> メソッドを使用することです。 このメソッドがによって提供される<xref:System.Object?displayProperty=nameWithType>からガベージ コレクションのすべてのクラスが派生します。

> [!NOTE]
> Microsoft で構築された .exe のリフレクションC++コンパイラは、.exe に組み込まれている場合にのみ使用できます、 **/clr: 純粋な**または **/clr:safe**コンパイラ オプション。 **/Clr: 純粋な**と **/clr:safe**コンパイラ オプションは、Visual Studio 2015 で非推奨と Visual Studio 2017 では使用できません。 参照してください[/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)詳細についてはします。

詳細については、「<xref:System.Reflection>」を参照してください。

## <a name="example-gettype"></a>例:GetType

`GetType` メソッドは、オブジェクトが基になっている場合は型を表す <xref:System.Type> クラス オブジェクトへのポインターを返します。 (、**型**オブジェクトには、インスタンス固有の情報が含まれていない)。このメソッドで取得できる項目には、型の完全名があります。完全名は、次のように表示できます。

型名には、型が定義されている完全なスコープ (名前空間も含む) が含まれています。また、.NET 構文でスコープ解決演算子としてドット (.) が付けられている点にも注意してください。

```cpp
// vcpp_reflection.cpp
// compile with: /clr
using namespace System;
int main() {
   String ^ s = "sample string";
   Console::WriteLine("full type name of '{0}' is '{1}'", s, s->GetType());
}
```

```Output
full type name of 'sample string' is 'System.String'
```

## <a name="example-boxed-value-types"></a>例: ボックス化された値の型

値型を `GetType` 関数で使用する場合も、最初にボックス化する必要があります。

```cpp
// vcpp_reflection_2.cpp
// compile with: /clr
using namespace System;
int main() {
   Int32 i = 100;
   Object ^ o = i;
   Console::WriteLine("type of i = '{0}'", o->GetType());
}
```

```Output
type of i = 'System.Int32'
```

## <a name="example-typeid"></a>例: typeid

同様、`GetType`メソッド、 [typeid](../extensions/typeid-cpp-component-extensions.md)演算子へのポインターを返します、**型**オブジェクト、このコードは型名を示すため**System.Int32**します。 型名を表示することは、リフレクションの最も基本的な機能ですが、より便利であると思われるのが、列挙型の有効な値を調査または探索できる点です。 これを行う静的**enum::getnames**関数は、テキスト形式での列挙値を含む各文字列の配列で返します。  次の例の値の列挙値を表す文字列の配列を取得する、**オプション**(CLR) 列挙され、ループに表示されます。

4 番目のオプションを追加する場合、**オプション**列挙型では、このコードには、列挙体が別のアセンブリで定義されている場合でも、再コンパイルなしの新しいオプションが報告されます。

```cpp
// vcpp_reflection_3.cpp
// compile with: /clr
using namespace System;

enum class Options {   // not a native enum
   Option1, Option2, Option3
};

int main() {
   array<String^>^ names = Enum::GetNames(Options::typeid);

   Console::WriteLine("there are {0} options in enum '{1}'",
               names->Length, Options::typeid);

   for (int i = 0 ; i < names->Length ; i++)
      Console::WriteLine("{0}: {1}", i, names[i]);

   Options o = Options::Option2;
   Console::WriteLine("value of 'o' is {0}", o);
}
```

```Output
there are 3 options in enum 'Options'
0: Option1
1: Option2
2: Option3
value of 'o' is Option2
```

## <a name="example-gettype-members-and-properties"></a>例:GetType メンバーとプロパティ

`GetType` オブジェクトは、型を調べるために使用できる多くのメンバーとプロパティをサポートします。 次のコードは、この情報の一部を取得して表示します。

```cpp
// vcpp_reflection_4.cpp
// compile with: /clr
using namespace System;
int main() {
   Console::WriteLine("type information for 'String':");
   Type ^ t = String::typeid;

   String ^ assemblyName = t->Assembly->FullName;
   Console::WriteLine("assembly name: {0}", assemblyName);

   String ^ nameSpace = t->Namespace;
   Console::WriteLine("namespace: {0}", nameSpace);

   String ^ baseType = t->BaseType->FullName;
   Console::WriteLine("base type: {0}", baseType);

   bool isArray = t->IsArray;
   Console::WriteLine("is array: {0}", isArray);

   bool isClass = t->IsClass;
   Console::WriteLine("is class: {0}", isClass);
}
```

```Output
type information for 'String':
assembly name: mscorlib, Version=1.0.5000.0, Culture=neutral,
PublicKeyToken=b77a5c561934e089
namespace: System
base type: System.Object
is array: False
is class: True
```

## <a name="example-enumeration-of-types"></a>型の例: 列挙型

リフレクションを使用すると、アセンブリ内の型とクラス内のメンバーも列挙できます。 この機能の例を示すために、次のような単純なクラスを定義します。

```cpp
// vcpp_reflection_5.cpp
// compile with: /clr /LD
using namespace System;
public ref class TestClass {
   int m_i;
public:
   TestClass() {}
   void SimpleTestMember1() {}
   String ^ SimpleMember2(String ^ s) { return s; }
   int TestMember(int i) { return i; }
   property int Member {
      int get() { return m_i; }
      void set(int i) { m_i = i; }
   }
};
```

## <a name="example-inspection-of-assemblies"></a>アセンブリの例: 検査

このコードを vcpp_reflection_6.dll という DLL にコンパイルすると、リフレクションを使用してアセンブリの内容を確認できます。 これは、静的リフレクション API 関数 xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType を使用してアセンブリを読み込む必要があります。 この関数のアドレスを返します、**アセンブリ**モジュールと内の型について、クエリを実行できるオブジェクト。

リフレクション システムが、アセンブリの配列を正常に読み込まれたら**型**でオブジェクトを取得、<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=nameWithType>関数。 各配列要素には、異なる型の情報が含まれています。ただし、この例で定義されているクラスは 1 つだけです。 ループを使用して各**型**型のメンバーを使用してこの配列をクエリ、 **:getmembers**関数。 この関数の配列を返します**MethodInfo**オブジェクト、メンバー関数は、データ メンバー、または型のプロパティに関する情報を格納している各オブジェクト。

定義されているメソッドの一覧が、関数には明示的に含まれているメモ**TestClass**関数が暗黙的に継承し、 **system::object**クラス。 Visual C++ 構文ではなく .NET で記述されている部分では、プロパティは get 関数と set 関数でアクセスする基底のデータ メンバーとして表示されます。 get 関数と set 関数は、通常のメソッドとしてこのリストに表示されています。 リフレクションは、マイクロソフトではなく、共通言語ランタイムを通じてサポートC++コンパイラ。

このコードを使用すると、定義したアセンブリを調べるだけでなく、.NET アセンブリを調べることもできます。 たとえば、TestAssembly を mscorlib に置き換えると、mscorlib.dll に定義されているすべての型とメソッドのリストが表示されます。

```cpp
// vcpp_reflection_6.cpp
// compile with: /clr
using namespace System;
using namespace System::IO;
using namespace System::Reflection;
int main() {
   Assembly ^ a = nullptr;
   try {
      // load assembly -- do not use file extension
      // will look for .dll extension first
      // then .exe with the filename
      a = Assembly::Load("vcpp_reflection_5");
   }
   catch (FileNotFoundException ^ e) {
      Console::WriteLine(e->Message);
      return -1;
   }

   Console::WriteLine("assembly info:");
   Console::WriteLine(a->FullName);
   array<Type^>^ typeArray = a->GetTypes();

   Console::WriteLine("type info ({0} types):", typeArray->Length);

   int totalTypes = 0;
   int totalMembers = 0;
   for (int i = 0 ; i < typeArray->Length ; i++) {
      // retrieve array of member descriptions
      array<MemberInfo^>^ member = typeArray[i]->GetMembers();

      Console::WriteLine("  members of {0} ({1} members):",
      typeArray[i]->FullName, member->Length);
      for (int j = 0 ; j < member->Length ; j++) {
         Console::Write("       ({0})",
         member[j]->MemberType.ToString() );
         Console::Write("{0}  ", member[j]);
         Console::WriteLine("");
         totalMembers++;
      }
      totalTypes++;
   }
   Console::WriteLine("{0} total types, {1} total members",
   totalTypes, totalMembers);
}
```

## <a name="implement"></a>方法: リフレクションを使用してプラグイン コンポーネント アーキテクチャを実装します。

次のコード例では、単純な「プラグイン」アーキテクチャを実装するためにリフレクションを使用を示します。 最初のリストは、アプリケーションと、2 番目のプラグインです。 アプリケーションは、コマンドライン引数として指定されたプラグイン DLL 内のフォーム ベースのクラスを使用して自身を設定する複数のドキュメント形式です。

使用して、指定されたアセンブリの読み込みを試行、<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>メソッド。 成功すると、アセンブリ内で型が列挙を使用して、<xref:System.Reflection.Assembly.GetTypes%2A?displayProperty=fullName>メソッド。 互換性を使用して各型をチェックしてから、<xref:System.Type.IsAssignableFrom%2A?displayProperty=fullName>メソッド。 この例で指定されたアセンブリ内で見つかったクラスをから派生する必要があります、<xref:System.Windows.Forms.Form>クラスをプラグインとして修飾します。

互換性のあるクラスがインスタンス化し、<xref:System.Activator.CreateInstance%2A?displayProperty=fullName>を受け入れ、メソッド、<xref:System.Type>を引数として、新しいインスタンスにポインターを返します。 それぞれの新しいインスタンスは、フォームにアタッチされ、表示されます。

なお、<xref:System.Reflection.Assembly.Load%2A>メソッドは、ファイル拡張子を含むアセンブリ名を受け付けません。 アプリケーションでは、メインの関数は、次のコード例は、いずれの場合も動作するように指定された拡張子をトリムします。

### <a name="example"></a>例

次のコードをプラグインを受け付けるアプリケーションを定義します。アセンブリ名は、最初の引数として指定する必要があります。 このアセンブリは、少なくとも 1 つのパブリックを含める必要があります<xref:System.Windows.Forms.Form>派生型。

```cpp
// plugin_application.cpp
// compile with: /clr /c
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;

ref class PluggableForm : public Form  {
public:
   PluggableForm() {}
   PluggableForm(Assembly^ plugAssembly) {
      Text = "plug-in example";
      Size = Drawing::Size(400, 400);
      IsMdiContainer = true;

      array<Type^>^ types = plugAssembly->GetTypes( );
      Type^ formType = Form::typeid;

      for (int i = 0 ; i < types->Length ; i++) {
         if (formType->IsAssignableFrom(types[i])) {
            // Create an instance given the type description.
            Form^ f = dynamic_cast<Form^> (Activator::CreateInstance(types[i]));
            if (f) {
               f->Text = types[i]->ToString();
               f->MdiParent = this;
               f->Show();
            }
         }
      }
   }
};

int main() {
   Assembly^ a = Assembly::LoadFrom("plugin_application.exe");
   Application::Run(gcnew PluggableForm(a));
}
```

### <a name="example"></a>例

次のコードから派生した 3 つのクラスを定義する<xref:System.Windows.Forms.Form>します。 結果として得られるアセンブリ名の名前が前の一覧で、実行可能ファイルに渡されると、これら 3 つのクラスの各が検出され、コンパイル時に、ホスト アプリケーションに認識されているすべてがされていないことにもかかわらず、インスタンス化します。

```cpp
// plugin_assembly.cpp
// compile with: /clr /LD
#using <system.dll>
#using <system.drawing.dll>
#using <system.windows.forms.dll>

using namespace System;
using namespace System::Windows::Forms;
using namespace System::Reflection;
using namespace System::Drawing;

public ref class BlueForm : public Form {
public:
   BlueForm() {
      BackColor = Color::Blue;
   }
};

public ref class CircleForm : public Form {
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      args->Graphics->FillEllipse(Brushes::Green, ClientRectangle);
   }
};

public ref class StarburstForm : public Form {
public:
   StarburstForm(){
      BackColor = Color::Black;
   }
protected:
   virtual void OnPaint(PaintEventArgs^ args) override {
      Pen^ p = gcnew Pen(Color::Red, 2);
      Random^ r = gcnew Random( );
      Int32 w = ClientSize.Width;
      Int32 h = ClientSize.Height;
      for (int i=0; i<100; i++) {
         float x1 = w / 2;
         float y1 = h / 2;
         float x2 = r->Next(w);
         float y2 = r->Next(h);
         args->Graphics->DrawLine(p, x1, y1, x2, y2);
      }
   }
};
```

## <a name="enumerate"></a>方法: リフレクションを使用してアセンブリ内のデータ型を列挙します。

次の例では、パブリック型とメンバーを使用しての列挙体<xref:System.Reflection>します。

次のコードは、ローカル ディレクトリまたは GAC にアセンブリの名前を指定、アセンブリを開くし、説明の取得を試行します。 成功した場合は、種類ごとに、そのパブリック メンバーが表示されます。

なお<xref:System.Reflection.Assembly.Load%2A?displayProperty=fullName>ファイル拡張子が使用されていないことが必要です。 そのため、コマンドライン引数として"mscorlib.dll"を使用して、失敗しますだけ"mscorlib"を使用すると、.NET Framework 型の表示中。 アセンブリ名が指定されていない場合、コードが検出し、現在のアセンブリ内の型 (このコードから生成された EXE) を報告します。

### <a name="example"></a>例

```cpp
// self_reflection.cpp
// compile with: /clr
using namespace System;
using namespace System::Reflection;
using namespace System::Collections;

public ref class ExampleType {
public:
   ExampleType() {}
   void Func() {}
};

int main() {
   String^ delimStr = " ";
   array<Char>^ delimiter = delimStr->ToCharArray( );
   array<String^>^ args = Environment::CommandLine->Split( delimiter );

// replace "self_reflection.exe" with an assembly from either the local
// directory or the GAC
   Assembly^ a = Assembly::LoadFrom("self_reflection.exe");
   Console::WriteLine(a);

   int count = 0;
   array<Type^>^ types = a->GetTypes();
   IEnumerator^ typeIter = types->GetEnumerator();

   while ( typeIter->MoveNext() ) {
      Type^ t = dynamic_cast<Type^>(typeIter->Current);
      Console::WriteLine("   {0}", t->ToString());

      array<MemberInfo^>^ members = t->GetMembers();
      IEnumerator^ memberIter = members->GetEnumerator();
      while ( memberIter->MoveNext() ) {
         MemberInfo^ mi = dynamic_cast<MemberInfo^>(memberIter->Current);
         Console::Write("      {0}", mi->ToString( ) );
         if (mi->MemberType == MemberTypes::Constructor)
            Console::Write("   (constructor)");

         Console::WriteLine();
      }
      count++;
   }
   Console::WriteLine("{0} types found", count);
}
```

## <a name="see-also"></a>関連項目

- [C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)
