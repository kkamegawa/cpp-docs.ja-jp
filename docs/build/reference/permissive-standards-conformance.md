---
title: /permissive- (標準への準拠)
ms.date: 03/08/2019
f1_keywords:
- /permissive
- VC.Project.VCCLCompilerTool.ConformanceMode
helpviewer_keywords:
- /permissive compiler options [C++]
- -permissive compiler options [C++]
- Standards conformance compiler options
- permissive compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: aca0fbc6a2ca36ceae26ba060b5bf92fea79c32c
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273723"
---
# <a name="permissive--standards-conformance"></a>/permissive- (標準への準拠)

コンパイラに標準準拠モードを指定します。 このオプションを使用すると、コード内の準拠の問題を特定して修正し、より正確で移植性の高いものにすることができます。

## <a name="syntax"></a>構文

> **/permissive-**

## <a name="remarks"></a>Remarks

このオプションは、Visual Studio 2017 以降でサポートされています。

**/Permissive-** コンパイラオプションを使用して、標準に準拠したコンパイラの動作を指定できます。 このオプションは、制限のない動作を無効にし、厳密な準拠のために[/zc](zc-conformance.md)コンパイラオプションを設定します。 IDE では、このオプションを使用すると、IntelliSense エンジンで非準拠コードに下線が引かれます。

既定では、 **/permissive-** オプションは、Visual Studio 2017 バージョン15.5 以降のバージョンで作成された新しいプロジェクトで設定されます。 以前のバージョンでは、既定では設定されていません。 このオプションを設定すると、コンパイラは、非標準の言語構成要素がコードで検出された場合に診断エラーまたは警告を生成します。これには、C++ 11 より前のコードの一般的なバグも含まれます。

**/Permissive-** オプションは、ソフトウェア開発キット (SDK) や Windows Driver KIT (WDK) など、最新の windows キットのほとんどすべてのヘッダーファイルと互換性があります。これは、Windows フォール作成者 SDK (10.0.16299.0) から始まります。 以前のバージョンの SDK は、さまざまなソースコードへの準拠の理由により、 **/permissive-** でのコンパイルに失敗する可能性があります。 コンパイラと Sdk はさまざまなリリースタイムラインで出荷されるため、残りの問題がいくつかあります。 ヘッダーファイルに関する特定の問題については、以下の[Windows ヘッダーに関する問題](#windows-header-issues)を参照してください。

**/Permissive-** オプションは、 [/Zc: referencebinding](zc-referencebinding-enforce-reference-binding-rules.md)、 [/zc: StrictStrings](zc-strictstrings-disable-string-literal-type-conversion.md)、 [/zc: rvaluecast](zc-rvaluecast-enforce-type-conversion-rules.md)オプションを、準拠する動作に設定します。 これらのオプションの既定値は、準拠していない動作です。 この動作をオーバーライドするには、コマンドラインで **/permissive-** の後に特定の **/zc**オプションを渡すことができます。

Visual Studio 2017 バージョン15.3 以降のバージョンのコンパイラでは、 **/permissive-** オプションに[/zc: 三項](zc-ternary.md)オプションが設定されています。 コンパイラは、2フェーズの名前参照に関する要件の多くも実装しています。 **/Permissive-** オプションが設定されている場合、コンパイラは、関数とクラスのテンプレート定義を解析し、テンプレートで使用される依存名と非依存の名前を識別します。 このリリースでは、名前の依存関係の分析だけが実行されます。

標準が実装に残る環境固有の拡張機能と言語領域は、 **/permissive-** の影響を受けません。 たとえば、Microsoft 固有`__declspec`、呼び出し規約、構造化例外処理のキーワード、コンパイラ固有のプラグマディレクティブ、または属性は、コンパイラによって **/permissive-** モードでフラグが設定されません。

**/Permissive-** オプションは、現在のコンパイラバージョンの準拠サポートを使用して、準拠していない言語構成要素を特定します。 オプションでは、コードがC++標準の特定のバージョンに準拠しているかどうかは判断されません。 最新のドラフト標準に対して実装されているすべてのコンパイラサポートを有効にするには、 [/std:latest](std-specify-language-standard-version.md)オプションを使用します。 コンパイラのサポートを現在実装されている C++17 標準に限定するには、 [/std:c++17](std-specify-language-standard-version.md)オプションを使用します。 コンパイラのサポートが C++14 標準に近いものになるように制限するには、既定の [ [/std:c++14](std-specify-language-standard-version.md) ] オプションを使用します。

すべてのバージョンの Visual Studio 2017 で、すべての C++ 11、C++ 14、または C++ 17 標準に準拠するコードが MSVC コンパイラでサポートされているわけではありません。 **/Permissive-** オプションでは、Visual Studio のバージョンに応じて、2フェーズの名前参照のいくつかの側面に関する問題が検出されない場合があります。また、一時的な非 const 参照をバインドして、copy init as direct init を処理し、複数のユーザー定義を許可することもできます。初期化の変換、または論理演算子の代替トークン、およびサポートされていないその他の準拠領域。 Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。 **/Permissive-** を最大限に活用するには、Visual Studio を最新バージョンに更新します。

### <a name="how-to-fix-your-code"></a>コードを修正する方法

ここでは、 **/permissive-** を使用する場合に非準拠として検出されるコードの例と、問題を修正するための推奨される方法を示します。

#### <a name="use-default-as-an-identifier-in-native-code"></a>ネイティブコードの識別子として既定値を使用する

```cpp
void func(int default); // Error C2321: 'default' is a keyword, and
                        // cannot be used in this context
```

#### <a name="look-up-members-in-dependent-base"></a>依存ベースでメンバーを参照する

```cpp
template <typename T>
struct B {
    void f();
};

template <typename T>
struct D : public B<T> // B is a dependent base because its type
                       // depends on the type of T.
{
    // One possible fix is to uncomment the following line.
    // If this is a type, don't forget the 'typename' keyword.
    // using B<T>::f;

    void g() {
        f(); // error C3861: 'f': identifier not found
             // Another fix is to change it to 'this->f();'
    }
};

void h() {
    D<int> d;
    d.g();
}
```

#### <a name="use-of-qualified-names-in-member-declarations"></a>メンバー宣言での修飾名の使用

```cpp
struct A {
    void A::f() { } // error C4596: illegal qualified name in member
                    // declaration.
                    // Remove redundant 'A::' to fix.
};
```

#### <a name="initialize-multiple-union-members-in-a-member-initializer"></a>メンバー初期化子内の複数の共用体メンバーを初期化します

```cpp
union U
{
    U()
        : i(1), j(1) // error C3442: Initializing multiple members of
                     // union: 'U::i' and 'U::j'.
                     // Remove all but one of the initializations to fix.
    {}
    int i;
    int j;
};
```

#### <a name="hidden-friend-name-lookup-rules"></a>非表示のフレンド名の参照規則

```cpp
// Example 1
struct S {
    friend void f(S *);
};
// Uncomment this declaration to make the hidden friend visible:
// void f(S *); // This declaration makes the hidden friend visible

using type = void (*)(S *);
type p = &f; // error C2065: 'f': undeclared identifier.
```

```cpp
// Example 2
struct S {
    friend void f(S *);
};
void g() {
    // Using nullptr instead of S prevents argument dependent lookup in S
    f(nullptr); // error C3861: 'f': identifier not found

    S *p = nullptr;
    f(S); // Hidden friend now found via argument-dependent lookup.
}
```

#### <a name="use-scoped-enums-in-array-bounds"></a>配列の境界でスコープ列挙型を使用する

```cpp
enum class Color {
    Red, Green, Blue
};

int data[Color::Blue]; // error C3411: 'Color' is not valid as the size
                       // of an array as it is not an integer type.
                       // Cast to type size_t or int to fix.
```

#### <a name="use-for-each-in-native-code"></a>ネイティブコードで for each を使用する

```cpp
void func() {
    int array[] = {1, 2, 30, 40};
    for each (int i in array) // error C4496: nonstandard extension
                              // 'for each' used: replace with
                              // ranged-for statement:
                              // for (int i: array)
    {
        // ...
    }
}
```

#### <a name="use-of-atl-attributes"></a>ATL 属性の使用

```cpp
// Example 1
[uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
class A {};
```

```cpp
// Fix for example 1
class __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) B {};
```

```cpp
// Example 2
[emitidl];
[module(name="Foo")];

[object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
__interface ICustom {
    HRESULT Custom([in] longl, [out, retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out, retval] long*pLong);
};

[coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
class CFoo : public ICustom
{};
```

```cpp
// Fix for example 2
// First, create the *.idl file. The vc140.idl generated file can be
// used to automatically obtain a *.idl file for the interfaces with
// annotation. Second, add a midl step to your build system to make
// sure that the C++ interface definitions are outputted.
// Last, adjust your existing code to use ATL directly as shown in
// the atl implementation section.

-- IDL  FILE--
import "docobj.idl";

[object, local, uuid(9e66a290-4365-11d2-a997-00c04fa37ddb)]
interface ICustom : IUnknown {
    HRESULT Custom([in] longl, [out,retval] long*pLong);
    [local] HRESULT CustomLocal([in] longl, [out,retval] long*pLong);
};

[ version(1.0), uuid(29079a2c-5f3f-3325-99a1-3ec9c40988bb) ]
library Foo {
    importlib("stdole2.tlb");
    importlib("olepro32.dll");

    [version(1.0), appobject, uuid(9e66a294-4365-11d2-a997-00c04fa37ddb)]
    coclass CFoo { interface ICustom; };
}

-- ATL IMPLEMENTATION--
#include <idl.header.h>
#include <atlbase.h>

class ATL_NO_VTABLE CFooImpl : public ICustom,
    public ATL::CComObjectRootEx<CComMultiThreadModel>
{
    public:BEGIN_COM_MAP(CFooImpl)
    COM_INTERFACE_ENTRY(ICustom)
    END_COM_MAP()
};
```

#### <a name="ambiguous-conditional-operator-arguments"></a>あいまいな条件演算子引数

Visual Studio 2017 バージョン15.3 より前のバージョンのコンパイラでは、標準によってあいまいであると見なされる条件`?:`演算子 (または三項演算子) に対してコンパイラが引数を受け取りました。 **/Permissive-** モードでは、コンパイラは、以前のバージョンで診断なしにコンパイルされた場合に、1つまたは複数の診断を発行するようになりました。

この変更によって発生する可能性のある一般的なエラーは次のとおりです。

- エラー C2593: ' operator? ' があいまいです

- エラー C2679: binary '? ': 型 ' B ' の右側のオペランドを受け取る演算子が見つかりません (または変換できません)

- エラー C2678: binary '? ': 型 ' A ' の左辺オペランドを受け取る演算子が見つかりません (または変換できません)

- エラー C2446: ': ': ' B ' から ' A ' への変換がありません

この問題を引き起こす可能性がある一般的なコードパターンは、クラス C によって、別の型 T からの非明示的なコンストラクターと、非明示的な変換演算子の両方が T 型に提供されている場合です。この場合、2番目の引数を3番目の引数の型に変換し、3番目の引数を2番目の引数の型に変換することは、有効な変換です。 どちらも有効であるため、標準に従ってあいまいです。

```cpp
// Example 1: class that provides conversion to and initialization from some type T
struct A
{
    A(int);
    operator int() const;
};

extern bool cond;

A a(42);
// Accepted when /Zc:ternary or /permissive- is not used:
auto x = cond ? 7 : a; // A: permissive behavior prefers A(7) over (int)a
// Accepted always:
auto y = cond ? 7 : int(a);
auto z = cond ? A(7) : a;
```

T が null で終わる文字列型 (たとえば`const char *` `const char16_t *`、、など) のいずれかを表し、の実際の引数`?:`が対応する型の文字列リテラルである場合、この共通パターンには重要な例外があります。 C++ 17 では、C++ 14 のセマンティクスが変更されました。 その結果、例2のコードは、 **/std: c++ 14**で受け入れられ、 **/zc: 三項**または **/permissive-** が使用されている場合は、 **/std: c++17**で拒否されます。

```cpp
// Example 2: exception from the above
struct MyString
{
    MyString(const char* s = "") noexcept;  // from char*
    operator const char* () const noexcept; //   to char*
};

extern bool cond;

MyString s;
// Using /std:c++14, /permissive- or /Zc:ternary behavior
// is to prefer MyString("A") over (const char*)s
// but under /std:c++17 this line causes error C2445:
auto x = cond ? "A" : s;
// You can use a static_cast to resolve the ambiguity:
auto y = cond ? "A" : static_cast<const char*>(s);
```

場合によっては、型`void`の引数を1つ持つ条件演算子にエラーが表示されることがあります。 このケースは、ASSERT に似たマクロでよく見られます。

```cpp
// Example 3: void arguments
void myassert(const char* text, const char* file, int line);
// Accepted when /Zc:ternary or /permissive- is not used:
#define ASSERT_A(ex) (void)((ex) ? 1 : myassert(#ex, __FILE__, __LINE__))
// Accepted always:
#define ASSERT_B(ex) (void)((ex) ? void() : myassert(#ex, __FILE__, __LINE__))
```

テンプレートメタプログラミングにエラーが表示される場合もあります。この場合、条件演算子の結果型は **/zc: 三項**および **/permissive-** の下で変更される可能性があります。 この問題を解決する1つの方法は、結果の型で[std:: remove_reference](../../standard-library/remove-reference-class.md)を使用することです。

```cpp
// Example 4: different result types
extern bool cond;
extern int count;
char  a = 'A';
const char  b = 'B';
decltype(auto) x = cond ? a : b; // char without, const char& with /Zc:ternary
const char (&z)[2] = count > 3 ? "A" : "B"; // const char* without /Zc:ternary
```

#### <a name="two-phase-name-look-up"></a>2フェーズの名前の参照

**/Permissive-** オプションが設定されている場合、コンパイラは、関数とクラスのテンプレート定義を解析し、2フェーズの名前の検索に必要なテンプレートで使用されている依存および非依存の名前を識別します。 Visual Studio 2017 バージョン15.3 では、名前の依存関係の分析が実行されます。 特に、テンプレート定義のコンテキストで宣言されていない非依存の名前は、ISO C++標準で必要とされる診断メッセージを発生させます。 Visual Studio 2017 バージョン15.7 では、定義コンテキストで引数依存の参照を必要とする非依存名のバインドも実行されます。

```cpp
// dependent base
struct B {
    void g() {}
};

template<typename T>
struct D : T {
    void f() {
        // The call to g was incorrectly allowed in VS2017:
        g();  // Now under /permissive-: C3861
        // Possible fixes:
        // this->g();
        // T::g();
    }
};

int main()
{
    D<B> d;
    d.f();
}
```

2フェーズ参照の従来の動作が必要であるが、 **/permissive-** の動作が必要な場合は、 **/zc: twoPhase**を追加します。

### <a name="windows-header-issues"></a>Windows ヘッダーに関する問題

Windows フォール作成者更新 SDK (10.0.16299.0) または Windows Driver Kit (WDK) バージョン1709より前のバージョンの Windows キットでは、 **/permissive-** オプションが小さすぎます。 Windows またはデバイスドライバーコードで **/permissive-** を使用するには、最新バージョンの windows キットに更新することをお勧めします。

Windows 4 月 2018 Update SDK (10.0.17134.0)、Windows フォール作成者更新 SDK (10.0.16299.0)、または Windows Driver Kit (WDK) 1709 の特定のヘッダーファイルには、 **/permissive-** の使用との互換性を確保するための問題が残っています。 これらの問題を回避するには、これらのヘッダーの使用を必要とするソースコードファイルのみに制限し、特定のソースコードファイルをコンパイルするときに **/permissive-** オプションを削除することをお勧めします。

Windows 4 月2018更新 SDK (10.0.17134.0) でリリースされたこれらの WinRT WRL ヘッダーは、 **/permissive-** ではクリーンではありません。 これらの問題を回避するには、 **/permissive-** を使用しないか、次のヘッダーを使用するときに **/zc: twoPhase**で **/permissive-** を使用します。

- Winrt/wrl/async. h の問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(483): error C3861: 'TraceDelegateAssigned': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(491): error C3861: 'CheckValidStateForDelegateCall': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(509): error C3861: 'TraceProgressNotificationStart': identifier not found
   C:\Program Files (x86)\Windows Kits\10\Include\10.0.17134.0\winrt\wrl\async.h(513): error C3861: 'TraceProgressNotificationComplete': identifier not found
   ```

- Winrt/wrl/implements の問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\winrt\wrl\implements.h(2086): error C2039: 'SetStrongReference': is not a member of 'Microsoft::WRL::Details::WeakReferenceImpl'
   ```

Windows 4 月2018更新 SDK (10.0.17134.0) でリリースされたこれらのユーザーモードヘッダーは、 **/permissive-** ではクリーンではありません。 これらの問題を回避するには、次のヘッダーを操作するときに **/permissive-** を使用しないでください。

- Um/チューンの問題

   ```Output
   C:\ProgramFiles(x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(139): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(559): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): error C3861: 'Release': identifier not found
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\tune.h(1240): note: 'Release': function declaration must be available as none of the arguments depend on a template parameter
   ```

- Um/spddkhlp. h での問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\spddkhlp.h(759): error C3861: 'pNode': identifier not found
   ```

- Um/refptrco の問題

   ```Output
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(179): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(342): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   C:\Program Files (x86)\Windows Kits\10\include\10.0.17134.0\um\refptrco.h(395): error C2760: syntax error: unexpected token 'identifier', expected 'type specifier'
   ```

これらの問題は、Windows フォール作成者更新 SDK (10.0.16299.0) のユーザーモードヘッダーに固有のものです。

- Um/Query. h での問題

   **/Permissive-** コンパイラスイッチを使用する場合、 `tagRESTRICTION`構造体は、ケース (rtor) メンバー ' または ' によってコンパイルされません。

   ```cpp
   struct tagRESTRICTION
   {
       ULONG rt;
       ULONG weight;
       /* [switch_is][switch_type] */ union _URes
       {
           /* [case()] */ NODERESTRICTION ar;
           /* [case()] */ NODERESTRICTION or;  // error C2059: syntax error: '||'
           /* [case()] */ NODERESTRICTION pxr;
           /* [case()] */ VECTORRESTRICTION vr;
           /* [case()] */ NOTRESTRICTION nr;
           /* [case()] */ CONTENTRESTRICTION cr;
           /* [case()] */ NATLANGUAGERESTRICTION nlr;
           /* [case()] */ PROPERTYRESTRICTION pr;
           /* [default] */  /* Empty union arm */
       } res;
   };
   ```

   この問題に対処するには、 **/permissive-** オプションを指定せずに、Query. h を含むファイルをコンパイルします。

- Um/cellularapi_oem の問題

   **/Permissive-** コンパイラスイッチを使用する場合、の`enum UICCDATASTOREACCESSMODE`事前宣言によって警告が発生します。

   ```cpp
   typedef enum UICCDATASTOREACCESSMODE UICCDATASTOREACCESSMODE; // C4471
   ```

   対象範囲外の列挙型の事前宣言は Microsoft の拡張機能です。 この問題に対処するには、 **/permissive-** オプションを指定せずに cellularapi_oem を含むファイルをコンパイルするか、 [/wd](compiler-option-warning-level.md)オプションを使用して警告 C4471 をサイレント状態にします。

- Um/omscript. h での問題

   C++ 03 では、文字列リテラルから BSTR (' wchar_t * ' への typedef) への変換は非推奨とされますが、使用することはできません。 C++ 11 では、変換は許可されなくなりました。

   ```cpp
   virtual /* [id] */ HRESULT STDMETHODCALLTYPE setExpression(
       /* [in] */ __RPC__in BSTR propname,
       /* [in] */ __RPC__in BSTR expression,
       /* [in][defaultvalue] */ __RPC__in BSTR language = L"") = 0; // C2440
   ```

   この問題に対処するには、 **/permissive-** オプションを指定せずに omscript. h を含むファイルをコンパイルするか、 **/zc: strictStrings**を使用します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

Visual Studio 2017 バージョン15.5 以降のバージョンでは、次の手順を使用します。

1. プロジェクトの **[プロパティページ]** ダイアログボックスを開きます。

1. [**構成プロパティ** > ] [**CC++/**  > **言語**] プロパティページを選択します。

1. "**準拠モード**" プロパティの値を **[はい] (/permissive-)** に変更します。 **[OK]** または **[適用]** を選択して、変更を保存します。

Visual Studio 2017 バージョン15.5 より前のバージョンでは、次の手順を使用します。

1. プロジェクトの **[プロパティページ]** ダイアログボックスを開きます。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[追加オプション]** ボックスに **/permissive-** コンパイラオプションを入力します。 **[OK]** または **[適用]** を選択して、変更を保存します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラオプション](compiler-options.md)\
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
