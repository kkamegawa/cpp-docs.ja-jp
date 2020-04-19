---
title: コンパイラ エラー C2440
ms.date: 03/28/2017
f1_keywords:
- C2440
helpviewer_keywords:
- C2440
ms.assetid: 36e6676c-f04f-4715-8ba1-f096c4bf3b44
ms.openlocfilehash: 8de433361901b5d247616c154afc48d637373d43
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65448030"
---
# <a name="compiler-error-c2440"></a>コンパイラ エラー C2440

'変換' : 'type1' から 'type2' に変換できません。

型にキャストできません`type1`に`type2`します。

## <a name="example"></a>例

C2440 は非定数の初期化しようとした場合に発生`char*`(または`wchar_t*`)、C++ コード内の文字列リテラルを使用して、ときに、コンパイラ準拠オプション[/Zc:strictStrings](../../build/reference/zc-strictstrings-disable-string-literal-type-conversion.md)設定されています。 C では、文字列リテラルの型が配列の`char`がの配列は C++ では、`const char`します。 次の例では C2440 エラーが生成されます。

```cpp
// C2440s.cpp
// Build: cl /Zc:strictStrings /W3 C2440s.cpp
// When built, the compiler emits:
// error C2440: 'initializing' : cannot convert from 'const char [5]'
// to 'char *'
//        Conversion from string literal loses const qualifier (see
// /Zc:strictStrings)

int main() {
   char* s1 = "test"; // C2440
   const char* s2 = "tests"; // OK
}
```

## <a name="example"></a>例

C2440 は、メンバーへのポインターを void* に変換しようとして発生することもあります。 次の例では C2440 が生成されます。

```cpp
// C2440.cpp
class B {
public:
   void  f(){;}

   typedef void (B::*pf)();

   void f2(pf pf) {
       (this->*pf)();
       void* pp = (void*)pf;   // C2440
   }

   void f3() {
      f2(f);
   }
};
```

## <a name="example"></a>例

C2440 は、事前宣言するだけで定義されていない型をキャストしようとした場合にも発生することがあります。 次の例では C2440 エラーが生成されます。

```cpp
// c2440a.cpp
struct Base { }; // Defined

struct Derived; // Forward declaration, not defined

Base * func(Derived * d) {
    return static_cast<Base *>(d); // error C2440: 'static_cast' : cannot convert from 'Derived *' to 'Base *'
}
```

## <a name="example"></a>例

次の例の 15 行目と 16 行目の C2440 エラーには、"`Incompatible calling conventions for UDT return value` (UDT 戻り値の呼び出し規約に互換性がありません)" というメッセージが表示されます。 A *UDT*クラス、構造体、共用体などのユーザー定義型です。 このような種類の非互換性エラーが発生するのは、事前宣言の戻り値の型で指定された UDT の呼び出し規約が UDT の実際の呼び出し規約と競合する場合や、関数ポインターが関連する場合です。

この例では、最初に、構造体およびその構造体を返す関数の事前宣言があります。コンパイラでは、この構造体で C++ 呼び出し規則が使用されると仮定します。 次に、構造体の定義があります。既定では、この定義は C 呼び出し規則を使用します。 コンパイラでは、構造体全体の読み込みが完了するまでは、その構造体の呼び出し規則がわからないため、`get_c2` の戻り値の型での構造体の呼び出し規則も C++ であると仮定します。

構造体の後には構造体を返す別の関数宣言が続きますが、この時点では、コンパイラは構造体の呼び出し規則が C++ であることを認識しています。 同様に、構造体を返す関数ポインターは構造体定義の後に定義されているため、コンパイラはその構造体で C++ 呼び出し規則が使用されることを認識します。

互換性のない 2 つの呼び出し規則が原因で発生する C2440 エラーを解決するには、UDT の定義の後にその UDT を返す関数を宣言します。

```cpp
// C2440b.cpp
struct MyStruct;

MyStruct get_c1();

struct MyStruct {
   int i;
   static MyStruct get_C2();
};

MyStruct get_C3();

typedef MyStruct (*FC)();

FC fc1 = &get_c1;   // C2440, line 15
FC fc2 = &MyStruct::get_C2;   // C2440, line 16
FC fc3 = &get_C3;

class CMyClass {
public:
   explicit CMyClass( int iBar)
      throw()   {
   }

   static CMyClass get_c2();
};

int main() {
   CMyClass myclass = 2;   // C2440
   // try one of the following
   // CMyClass myclass{2};
   // CMyClass myclass(2);

   int *i;
   float j;
   j = (float)i;   // C2440, cannot cast from pointer to int to float
}
```

## <a name="example"></a>例

C2440 は、内部ポインターに 0 を割り当てた場合にも発生することがあります。

```cpp
// C2440c.cpp
// compile with: /clr
int main() {
   array<int>^ arr = gcnew array<int>(100);
   interior_ptr<int> ipi = &arr[0];
   ipi = 0;   // C2440
   ipi = nullptr;   // OK
}
```

## <a name="example"></a>例

C2440 は、ユーザー定義の規約の使用方法が間違っている場合にも発生することがあります。 たとえば、ときに、変換演算子として定義された`explicit`コンパイラが暗黙的な変換で使用できません。 ユーザー定義の変換の詳細については、次を参照してください。[ユーザー定義の変換 (C +/cli CLI)](../../dotnet/user-defined-conversions-cpp-cli.md))。 次の例では C2440 エラーが生成されます。

```cpp
// C2440d.cpp
// compile with: /clr
value struct MyDouble {
   double d;
   // convert MyDouble to Int32
   static explicit operator System::Int32 ( MyDouble val ) {
      return (int)val.d;
   }
};

int main() {
   MyDouble d;
   int i;
   i = d;   // C2440
   // Uncomment the following line to resolve.
   // i = static_cast<int>(d);
}
```

## <a name="example"></a>例

C2440 は、型が <xref:System.Array> である Visual C++ 配列のインスタンスを作成しようとした場合にも発生することがあります。  詳細については、次を参照してください。[配列](../../extensions/arrays-cpp-component-extensions.md)します。  次の例では C2440 が生成されます。

```cpp
// C2440e.cpp
// compile with: /clr
using namespace System;
int main() {
   array<int>^ intArray = Array::CreateInstance(__typeof(int), 1);   // C2440
   // try the following line instead
   // array<int>^ intArray = safe_cast<array<int> ^>(Array::CreateInstance(__typeof(int), 1));
}
```

## <a name="example"></a>例

C2440 は、属性機能の変更が原因で発生することもあります。  次の例では C2440 エラーが生成されます。

```cpp
// c2440f.cpp
// compile with: /LD
[ module(name="PropDemoLib", version=1.0) ];   // C2440
// try the following line instead
// [ module(name="PropDemoLib", version="1.0") ];
```

## <a name="example"></a>例

MicrosoftC++コンパイラことはできなくなりました、 [const_cast 演算子](../../cpp/const-cast-operator.md)ダウン キャストするときに使用するソース コード **/clr**プログラミングがコンパイルされます。

この C2440 エラーを解決するには、正しいキャスト演算子を使用します。 詳細については、次を参照してください。[キャスト演算子](../../cpp/casting-operators.md)します。

次の例では C2440 エラーが生成されます。

```cpp
// c2440g.cpp
// compile with: /clr
ref class Base {};
ref class Derived : public Base {};
int main() {
   Derived ^d = gcnew Derived;
   Base ^b = d;
   d = const_cast<Derived^>(b);   // C2440
   d = dynamic_cast<Derived^>(b);   // OK
}
```

## <a name="example"></a>例

C2440 は、Visual Studio 2015 Update 3 でコンパイラの準拠に関する変更のため発生します。 以前は、コンパイラ正しくとして扱われますしない特定個別の式と同じ型の一致するテンプレートを識別するときに、`static_cast`操作。 前に依存していましたが、コンパイラが型を正しく区別し、コードのようになりました`static_cast`動作が壊れています。 この問題を解決するを使用して、テンプレート パラメーターの型を検索するテンプレート引数を変更、`reinterpret_cast`または C スタイルのキャスト。

次の例では C2440 エラーが生成されます。

```cpp
// c2440h.cpp

template<int *a>
struct S1 {};

int g;
struct S2 : S1<&g> {
};

int main()
{
    S2 s;
    static_cast<S1<&*&g>>(s); // C2440 in VS 2015 Update 3
    // This compiles correctly:
    // static_cast<S1<&g>>(s);
}

This error can appear in ATL code that uses the SINK_ENTRY_INFO macro defined in <atlcom.h>.
```

## <a name="example"></a>例

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 およびそれ以降は、Visual Studio 2015 でキャッチされず、クラッシュする可能性がある初期化子リストを使用するオブジェクトの作成に関連するコンパイラ エラーを正しく発生させるか、実行時の動作は未定義です。 C++ 17 コピー リストの初期化、コンパイラは明示的なコンス トラクターのオーバー ロードの解決を考慮する必要が、そのオーバー ロードを実際に選択した場合、エラーが発生する必要があります。

次の例は、Visual Studio 2017 ではなく Visual Studio 2015 でコンパイルします。

```cpp
// C2440j.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot
                         // convert from 'int' to 'const A &'
}
```

このエラーを修正するには、直接の初期化を使用します。

```cpp
// C2440k.cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    const A& a2{ 1 };
}
```

## <a name="example"></a>例

### <a name="cv-qualifiers-in-class-construction"></a>クラス コンストラクションの cv 修飾子

Visual Studio 2015 では、コンストラクターを呼び出してクラス オブジェクトを生成するときに、コンパイラが誤って cv 修飾子を無視することがあります。 これにより、クラッシュまたは予期しない実行時動作が発生する可能性があります。 次の例では、Visual Studio 2015 でコンパイルされますが、Visual Studio 2017 以降は、コンパイラ エラーが発生します。

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

エラーを解決するには、operator int() を定数として宣言します。
