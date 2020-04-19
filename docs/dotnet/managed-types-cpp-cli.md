---
title: マネージド型 (C++/CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- data types [C++], managed
- managed data types [C++]
- .NET Framework [C++], managed types
- data types [C++], .NET feature access
- main function, in managed applications
- managed code, main() function
- .NET Framework [C++], C++ equivalents
- __nogc type declarations
- __value keyword, issues when nesting
- equality, testing for
- versioning, diagnosing conflicts
- versioning
- exceptions, diagnosing odd behavior
- compatibility, between assemblies
ms.assetid: 679b8ed3-d966-4a0c-b627-2a3f3ec96b74
ms.openlocfilehash: b91918d526d83d4cf47436d02b7c67038576bafb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62152775"
---
# <a name="managed-types-ccli"></a>マネージド型 (C++/CLI)

Visual C では、共通言語ランタイムの機能のサポートを提供し、利点、およびランタイムの制限を マネージ型を使用して .NET 機能へのアクセスを許可します。

## <a name="main_functions"></a> マネージ型と main 関数

使用して、アプリケーションの書き込み時に **/clr**の引数、 **main()** 関数をマネージ型にすることはできません。

適切な署名の例を示します。

```cpp
// managed_types_and_main.cpp
// compile with: /clr
int main(int, char*[], char*[]) {}
```

## <a name="dotnet"></a> C++ ネイティブ型に対応する .NET framework

次の表は、定義済みの型のエイリアスである組み込みの Visual C 型のキーワードで、**システム**名前空間。

|C++ のビジュアルの種類|.NET Framework 型|
|-----------------------|-------------------------|
|**void**|<xref:System.Void?displayProperty=nameWithType>|
|**bool**|<xref:System.Boolean?displayProperty=nameWithType>|
|**signed char** |<xref:System.SByte?displayProperty=nameWithType>|
|**unsigned char**|<xref:System.Byte?displayProperty=nameWithType>|
|**wchar_t**|<xref:System.Char?displayProperty=nameWithType>|
|**short**と**signed short**|<xref:System.Int16?displayProperty=nameWithType>|
|**unsigned short**|<xref:System.UInt16?displayProperty=nameWithType>|
|**int**、 **signed int**、**long**、および**signed long**|<xref:System.Int32?displayProperty=nameWithType>|
|**符号なし int**と**unsigned long**|<xref:System.UInt32?displayProperty=nameWithType>|
|**_ _int64**と **_ _int64 の署名**|<xref:System.Int64?displayProperty=nameWithType>|
|**unsigned __int64**|<xref:System.UInt64?displayProperty=nameWithType>|
|**float**|<xref:System.Single?displayProperty=nameWithType>|
|**double**と**long double**|<xref:System.Double?displayProperty=nameWithType>|

既定の符号付きまたは符号なしにするコンパイラ オプションの詳細については**char**を参照してください[/J (既定の char 型は符号付き)](../build/reference/j-default-char-type-is-unsigned.md)します。

## <a name="version_issues"></a> ネイティブ型に入れ子になった値の型のバージョンの問題

クライアント アセンブリをビルドするために使用する署名 (厳密な名前) アセンブリのコンポーネントを検討してください。 コンポーネントには、ネイティブの共用体、クラス、または配列のメンバーの種類として、クライアントで使用される値の型が含まれています。 コンポーネントの将来のバージョンでは、サイズまたは値型のレイアウトを変更する場合、クライアントが再コンパイルする必要があります。

キー ファイルを作成[sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) (`sn -k mykey.snk`)。

### <a name="example"></a>例

次の例は、コンポーネントです。

```cpp
// nested_value_types.cpp
// compile with: /clr /LD
using namespace System::Reflection;
[assembly:AssemblyVersion("1.0.0.*"),
assembly:AssemblyKeyFile("mykey.snk")];

public value struct S {
   int i;
   void Test() {
      System::Console::WriteLine("S.i = {0}", i);
   }
};
```

### <a name="example"></a>例

このサンプルでは、クライアントです。

```cpp
// nested_value_types_2.cpp
// compile with: /clr
#using <nested_value_types.dll>

struct S2 {
   S MyS1, MyS2;
};

int main() {
   S2 MyS2a, MyS2b;
   MyS2a.MyS1.i = 5;
   MyS2a.MyS2.i = 6;
   MyS2b.MyS1.i = 10;
   MyS2b.MyS2.i = 11;

   MyS2a.MyS1.Test();
   MyS2a.MyS2.Test();
   MyS2b.MyS1.Test();
   MyS2b.MyS2.Test();
}
```

### <a name="output"></a>出力

```Output
S.i = 5
S.i = 6
S.i = 10
S.i = 11
```

### <a name="comments"></a>コメント

ただし、する別のメンバーを追加する場合`struct S`nested_value_types.cpp で (たとえば、 `double d;`) と、クライアントを再コンパイルしなくても、コンポーネントを再コンパイル、ハンドルされない例外になります (型の<xref:System.IO.FileLoadException?displayProperty=fullName>)。

## <a name="test_equality"></a>方法: 等しいかどうかをテストします。

次の例では、c++ マネージ拡張を使用して等しいかどうかのテストはハンドルの参照先に基づいています。

### <a name="example"></a>例

```cpp
// mcppv2_equality_test.cpp
// compile with: /clr /LD
using namespace System;

bool Test1() {
   String ^ str1 = "test";
   String ^ str2 = "test";
   return (str1 == str2);
}
```

このプログラムの IL では、戻り値が op_Equality への呼び出しを使用して実装されることを示します。

```MSIL
IL_0012:  call       bool [mscorlib]System.String::op_Equality(string,
                                                               string)
```

## <a name="diagnose_fix"></a>方法: 診断し、アセンブリの互換性の問題を修正

このトピックでは、コンパイル時に参照されるアセンブリのバージョンは、実行時に参照されるアセンブリのバージョンと一致しないときに生じると、問題を回避する方法。

その他のアセンブリを参照するアセンブリをコンパイルすると、`#using`構文。 、コンパイル時にこれらのアセンブリは、コンパイラによってアクセスします。 これらのアセンブリからの情報は、最適化の決定に使用されます。

ただし、参照アセンブリが変更され、再コンパイルし、それに依存する参照元のアセンブリを再コンパイルしないで、アセンブリが可能性がありますいない互換性のあるものです。 有効だった最適化処理を行う最初できないアセンブリの新しいバージョンに対して適切です。 これらの非互換性による、さまざまなのランタイム エラーが発生する可能性があります。 このような場合に生成される特定の例外はありません。 実行時に、エラーを報告する方法は、問題の原因となったコードの変更の性質によって異なります。

アプリケーション全体が、製品のリリース版の再構築する限り、これらのエラーは、最終的な運用環境のコードで問題をしないでください。 これらの問題を回避することにより、正式なバージョン番号では、パブリックにリリースされているアセンブリをマークする必要があります。 詳細については、「[アセンブリのバージョン管理](/dotnet/framework/app-domains/assembly-versioning)」を参照してください。

### <a name="diagnosing-and-fixing-an-incompatibility-error"></a>診断と非互換性エラーを修正

1. ランタイムの例外や、別のアセンブリを参照しているコードで発生するその他のエラー条件が発生し、その他の原因がある場合、古いアセンブリを扱って可能性があります。

1. 最初に、分離し、例外またはその他のエラー状態を再現します。 期限切れの例外のために発生する問題を再現可能なことがあります。

1. アプリケーションで参照されるアセンブリのタイムスタンプを確認します。

1. 参照先アセンブリのタイムスタンプが、アプリケーションの最後のコンパイルのタイムスタンプより後の場合は、アプリケーションが期限切れです。 このような場合、最新のアセンブリを使用してアプリケーションを再コンパイルし、必要なコード変更を行います。

1. アプリケーションを再実行で問題を再現して、例外が発生しないことを確認する手順を実行します。

### <a name="example"></a>例

次のプログラムでは、メソッドのアクセシビリティを削減し、再コンパイルしなくても、別のアセンブリには、そのメソッドにアクセスしようとして問題を示しています。 コンパイルしてみてください`changeaccess.cpp`最初。 これは、参照アセンブリが変更されます。 コンパイルし、`referencing.cpp`します。 コンパイルは成功します。 次に、呼び出されたメソッドのアクセシビリティを削減します。 再コンパイル`changeaccess.cpp`フラグ`/DCHANGE_ACCESS`します。 これにより、メソッド、プライベートではなく、保護されているため、合法的に呼び出すになったことができます。 再コンパイルしなくても`referencing.exe`アプリケーションを再実行します。 例外<xref:System.MethodAccessException>になります。

```cpp
// changeaccess.cpp
// compile with: /clr:safe /LD
// After the initial compilation, add /DCHANGE_ACCESS and rerun
// referencing.exe to introduce an error at runtime. To correct
// the problem, recompile referencing.exe

public ref class Test {
#if defined(CHANGE_ACCESS)
protected:
#else
public:
#endif

  int access_me() {
    return 0;
  }

};
```

```cpp
// referencing.cpp
// compile with: /clr:safe
#using <changeaccess.dll>

// Force the function to be inline, to override the compiler's own
// algorithm.
__forceinline
int CallMethod(Test^ t) {
  // The call is allowed only if access_me is declared public
  return t->access_me();
}

int main() {
  Test^ t = gcnew Test();
  try
  {
    CallMethod(t);
    System::Console::WriteLine("No exception.");
  }
  catch (System::Exception ^ e)
  {
    System::Console::WriteLine("Exception!");
  }
  return 0;
}
```

## <a name="see-also"></a>関連項目

[C++/CLI (Visual C++) による .NET プログラミング](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)<br/>
[他の .NET 言語との相互運用性 (C++/CLI)](../dotnet/interoperability-with-other-dotnet-languages-cpp-cli.md)<br/>
[マネージド型 (C++/CLI)](../dotnet/managed-types-cpp-cli.md)<br/>
[#using ディレクティブ](../preprocessor/hash-using-directive-cpp.md)
