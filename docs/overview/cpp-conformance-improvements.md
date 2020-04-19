---
title: C++ 準拠の強化
ms.date: 12/04/2019
description: Visual Studio の Microsoft C++ は、C++20 言語標準との完全準拠に向かって進んでいます。
ms.technology: cpp-language
ms.openlocfilehash: e9c2a69c8d33ea692a76a5642a15b581567c2c63
ms.sourcegitcommit: 5f276064779d90a4cfda758f89e0c0f1e4d1a188
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/09/2020
ms.locfileid: "75793844"
---
# <a name="c-conformance-improvements-in-visual-studio"></a>Visual Studio の C++ 準拠の強化

Microsoft C++ では、リリースごとに準拠強化とバグ修正を行っています。 この記事では、機能強化をメジャー リリースごと、バージョンごとに一覧で紹介します。 また、主要なバグ修正もバージョンごとに一覧で紹介します。 特定のバージョンで行われた変更に直接移動するには、**この記事**の一覧を使用します。

::: moniker range="vs-2019"

## <a name="improvements_160"></a> Visual Studio 2019 RTW (バージョン 16.0) の準拠の強化

Visual Studio 2019 RTW には、Microsoft C++ コンパイラ (MSVC) の次の準拠強化、バグ修正、動作変更が含まれます

**注:** C++20 の機能は、コンパイラと IntelliSense の C++20 実装が完了するまで `/std:c++latest` モードで利用できます。 その時点で、`/std:c++20` コンパイラ モードが導入されます。

### <a name="improved-modules-support-for-templates-and-error-detection"></a>改善されたモジュールのテンプレート サポートとエラー検出

モジュールは現在、公式に C++20 標準になりました。 改善されたサポートは、Visual Studio 2017 バージョン 15.9 で追加されました。 詳細については、「[Better template support and error detection in C++ Modules with MSVC 2017 version 15.9](https://devblogs.microsoft.com/cppblog/better-template-support-and-error-detection-in-c-modules-with-msvc-2017-version-15-9/)」 (C++ Modules での、テンプレート サポートとエラー検出に対する MSVC 2017 バージョン 15.9 を使用した改善) を参照してください。

### <a name="modified-specification-of-aggregate-type"></a>集計の種類の変更後の仕様

集計の種類の仕様が C++20 で変更されました (「[Prohibit aggregates with user-declared constructors](https://wg21.link/p1008r1)」 (ユーザー宣言コンストラクターの集計を禁止) を参照してください)。 Visual Studio 2019 の `/std:c++latest` では、ユーザー宣言コンストラクター (たとえば、コンストラクター宣言の `= default` や `= delete` を含む) を含むクラスは集計ではありません。 以前は、ユーザー指定のコンストラクターのみで、集計になる資格がクラスから剥奪されました。 今回の変更により、このような種類の初期化方法に対する制約が追加されました。

次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 の `/std:c++latest` では、C2280 エラーや C2440 エラーが発生します。

```cpp
struct A
{
    A() = delete; // user-declared ctor
};

struct B
{
    B() = default; // user-declared ctor
    int i = 0;
};

A a{}; // ill-formed in C++20, previously well-formed
B b = { 1 }; // ill-formed in C++20, previously well-formed
```

### <a name="partial-support-for-operator-"></a>`operator <=>` の部分的なサポート

[P0515R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0515r3.pdf) C++20 では、3 方向の比較演算子 `<=>` が導入されました。これは "宇宙船演算子" とも呼ばれています。 `/std:c++latest` モードの Visual Studio 2019 では、この演算子の部分的サポートが導入され、現在は許可されていない構文に対してエラーが発生します。 たとえば、次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 の `/std:c++latest` では、複数のエラーが発生します。

```cpp
struct S
{
    bool operator<=(const S&) const { return true; }
};

template <bool (S::*)(const S&) const>
struct U { };

int main(int argc, char** argv)
{
    U<&S::operator<=> u; // In Visual Studio 2019 raises C2039, 2065, 2146.
}
```

エラーを回避するには、`U<&S::operator<= > u;` のように、最後の山かっこの前でエラーを出す行にスペースを挿入します。

### <a name="references-to-types-with-mismatched-cv-qualifiers"></a>cv 修飾子が一致しない型の参照

MSVC では以前、最上位より下で、cv 修飾子が一致しない型から参照を直接バインドすることが許可されました。 このバインドにより、参照により指示されると思われる const データを変更できる場合がありました。 このコンパイラでは現在、標準で要求されるとおり、temporary が作成されます。 Visual Studio 2017 の場合、次のコードは警告なしでコンパイルされます。 Visual Studio 2019 の場合、コンパイラから *警告 C4172: \<func:#1 "?PData@X@@QBEABQBXXZ">* が発行され、ローカル変数または temporary のアドレスが返されます。

```cpp
struct X
{
    const void* const& PData() const
    {
        return _pv;
    }

    void* _pv;
};

int main()
{
    X x;
    auto p = x.PData(); // C4172
}
```

### <a name="reinterpret_cast-from-an-overloaded-function"></a>オーバー ロードした関数からの `reinterpret_cast`

`reinterpret_cast` の引数は、オーバーロードした関数のアドレスが許可されるコンテキストの 1 つではありません。 次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 では *C2440: cannot convert from 'overloaded-function' to 'fp'* ('オーバーロードした関数' を 'fp' に変換できません) が発生します。

```cpp
int f(int) { return 1; }
int f(float) { return .1f; }
using fp = int(*)(int);

int main()
{
    fp r = reinterpret_cast<fp>(&f);
}
```

このエラーを回避するには、このシナリオで許可されるキャストを使用します。

```cpp
int f(int);
int f(float);
using fp = int(*)(int);

int main()
{
    fp r = static_cast<fp>(&f); // or just &f;
}
```

### <a name="lambda-closures"></a>ラムダ クロージャ

C++ 14 では、ラムダ クロージャの型はリテラルではありません。 このルールの最も重要な影響は、ラムダが **constexpr** 変数に割り当てられない可能性があるということです。 次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 では *C2127: 'l': illegal initialization of 'constexpr' entity with a non-constant expression (定数以外の式を持つ 'constexpr' エンティティの初期化が正しくありません)* が発生します。

```cpp
int main()
{
    constexpr auto l = [] {}; // C2127 in VS2019
}
```

エラーを回避するには、**constexpr** 修飾子を削除するか、準拠モードを `/std:c++17` に変更します。

### <a name="stdcreate_directory-failure-codes"></a>`std::create_directory` エラー コード

無条件で C++20 から [P1164](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1164r1.pdf) が実装されました。 これにより、エラー時、ターゲットが既にディレクトリであったかどうかを確認するように `std::create_directory` が変更されます。 以前は、ERROR_ALREADY_EXISTS タイプのエラーはすべて、success-but-directory-not-created コードに変換されました。

### `operator<<(std::ostream, nullptr_t)`

[LWG 2221](https://cplusplus.github.io/LWG/issue2221) に基づき、nullptrs をストリームに書き込むための `operator<<(std::ostream, nullptr_t)` が追加されました。

### <a name="additional-parallel-algorithms"></a>追加の並列アルゴリズム

`is_sorted`、`is_sorted_until`、`is_partitioned`、`set_difference`、`set_intersection`、`is_heap`、`is_heap_until` の新しい並列バージョン。

### <a name="atomic-initialization"></a>アトミック初期化

[P0883 "Fixing atomic initialization"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0883r1.pdf) により、含まれる T を既定初期化せず、値初期化するように `std::atomic` が変更されます。 Clang/LLVM と Microsoft 標準ライブラリが使用されるとき、修正は有効になります。 Microsoft C++ コンパイラでは、**constexpr** 処理のバグに対する回避策としてこれは現在、無効になっています。

### <a name="remove_cvref-and-remove_cvref_t"></a>`remove_cvref` および `remove_cvref_t`

[P0550](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf) から型の特徴、`remove_cvref` と `remove_cvref_t` を実装しました。 それにより、(`std::decay` や `std::decay_t` とは異なり) 関数や配列をポインターに減衰させることなく、reference-ness と cv 修飾が型から削除されます。

### <a name="feature-test-macros"></a>機能テストのマクロ

[P0941R2 - 機能テスト マクロ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0941r2.html)は完全であり、`__has_cpp_attribute` がサポートされています。 機能テスト マクロはすべての標準モードでサポートされています。

### <a name="prohibit-aggregates-with-user-declared-constructors"></a>ユーザー宣言コンストラクターによる集計の禁止

[C++20 P1008R1 - ユーザー宣言コンストラクターによる集計の禁止](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p1008r1.pdf)は完全です。

## <a name="improvements_161"></a> 16.1 の準拠の強化

### <a name="char8_t"></a>char8_t

[P0482r6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html)。 C++20 では、UTF-8 コード単位を表すための新しい文字型が追加されます。 C++20 の `u8` 文字列リテラルには、以前の `const char[N]` に代わり、型 `const char8_t[N]` が与えられます。 [N2231](http://www.open-std.org/jtc1/sc22/wg14/www/docs/n2231.htm) では、C 標準に同様の変更が提案されています。 `char8_t` 下位互換性改善の提案が [P1423r0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1423r0.html) で与えられています。 **/Zc:char8_t** コンパイラ オプションを指定すると、Microsoft C++ コンパイラでは、Visual Studio 2019 バージョン 16.1 の `char8_t` のサポートが追加されます。 将来的にこれは [/std:c++latest](../build/reference/std-specify-language-standard-version.md) でサポートされます。/std:c++latest は、 **/Zc:char8_t-** 経由で C++17 の動作に戻すことができます。 IntelliSense の動力源となる EDG コンパイラではまだそれがサポートされていません。そのため、誤った IntelliSense のみのエラーが表示されますが、それは実際のコンパイルに影響を与えません。

#### <a name="example"></a>例

```cpp
const char* s = u8"Hello"; // C++17
const char8_t* s = u8"Hello"; // C++20
```

### <a name="stdtype_identity-metafunction-and-stdidentity-function-object"></a>std::type_identity メタ関数と std::identity 関数オブジェクト

[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf). 非推奨 `std::identity` クラス テンプレート拡張が削除され、C++20 `std::type_identity` メタ関数と `std::identity` 関数オブジェクトに置換されました。 いずれも [/std:c++latest](../build/reference/std-specify-language-standard-version.md) でのみ利用できます。

次の例では、Visual Studio 2017 の `std::identity` (\<type_traits> に定義) に対して非推奨警告 C4996 が生成されます。

```cpp
#include <type_traits>

using T = std::identity<int>::type;
T x, y = std::identity<T>{}(x);
int i = 42;
long j = std::identity<long>{}(i);
```

次の例では、新しい `std::type_identity` と共に新しい `std::identity` (\<functional> で定義) を使用する方法を確認できます。

```cpp
#include <type_traits>
#include <functional>

using T = std::type_identity<int>::type;
T x, y = std::identity{}(x);
int i = 42;
long j = static_cast<long>(i);
```

### <a name="syntax-checks-for-generic-lambdas"></a>汎用ラムダの構文チェック

新しいラムダ プロセッサにより、汎用ラムダの [/std:c++latest](../build/reference/std-specify-language-standard-version.md) で、あるいは **/experimental:newLambdaProcessor** を含む他の言語モードで、一部の準拠モード構文チェックが有効になります。

Visual Studio 2017 の場合、このコードは警告なくコンパイルされますが、Visual Studio 2019 の場合、*C2760 syntax error: unexpected token '\<id-expr>', expected 'id-expression'* というエラーが出ます。

```cpp
void f() {
    auto a = [](auto arg) {
        decltype(arg)::Type t;
    };
}
```

次の例では、コンパイラから強制されるようになった正しい構文を確認できます。

```cpp
void f() {
    auto a = [](auto arg) {
        typename decltype(arg)::Type t;
    };
}
```

### <a name="argument-dependent-lookup-for-function-calls"></a>関数呼び出しの引数依存検索

[P0846R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0846r0.html) (C++20) 明示的なテンプレート引数を含む関数呼び出し式の引数依存照合を使用する、関数テンプレートの検索機能が強化されました。 **/std:c++latest** を必要とします。

### <a name="designated-initialization"></a>初期化の指定

[P0329R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf) (C++20) 初期化の指定により、集計初期化で、`Type t { .member = expr }` 構文を使用し、特定のメンバーを選択できます。 **/std:c++latest** を必要とします。

### <a name="new-and-updated-standard-library-functions-c20"></a>新規および更新された標準ライブラリ関数 (C++20)

- `basic_string` と `basic_string_view` 向けの `starts_with()` と `ends_with()`。
- 連想コンテナーの `contains()`。
- `list` と `forward_list` の `remove()`、`remove_if()`、および `unique()` で `size_type` が返されるようになりました。
- `shift_left()` と `shift_right()` が \<algorithm> に追加されました。


## <a name="improvements_162"></a> 16.2 の準拠の強化

### <a name="noexcept-constexpr-functions"></a>noexcept constexpr 関数

constexpr 関数では、定数式で使用される場合、既定では **noexcept** が考慮されなくなりました。 この動作変更は、[CWG 1351](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#1351) の解決に由来し、[/permissive-](../build/reference/permissive-standards-conformance.md) で有効になっています。 次の例は、Visual Studio 2019 バージョン 16.1 以前ではコンパイルされますが、Visual Studio 2019 バージョン 16.2 では C2338 が生成されます。

```cpp
constexpr int f() { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept"); // C2338 in 16.2
}
```

このエラーを修正するには、**noexcept** 式を関数宣言に追加します。

```cpp
constexpr int f() noexcept { return 0; }

int main() {
    static_assert(noexcept(f()), "f should be noexcept");
}
```

### <a name="binary-expressions-with-different-enum-types"></a>異なる列挙型を持つバイナリ式

一方が列挙型であり、もう一方が異なる列挙型または浮動小数点型のオペランドに対して通常の算術変換を適用する機能は、C++20 ([P1120R0](https://wg21.link/p1120r0)) では非推奨です。 Visual Studio 2019 バージョン 16.2 以降では、[/std:c++latest](../build/reference/std-specify-language-standard-version.md) コンパイラ オプションが有効になっていると、次のコードでレベル 4 の警告が生成されます。

```cpp
enum E1 { a };
enum E2 { b };
int main() {
    int i = a | b; // warning C5054: operator '|': deprecated between enumerations of different types
}
```

この警告を回避するには、[static_cast](../cpp/static-cast-operator.md) を使用して 2 番目のオペランドを変換します。

```cpp
enum E1 { a };
enum E2 { b };
int main() {
  int i = a | static_cast<int>(b);
}
```

### <a name="binary-expressions-with-enumeration-and-floating-point-types"></a>列挙型と浮動小数点型を含むバイナリ式

一方が列挙型であり、もう一方が異なる列挙型または浮動小数点型のオペランドに対して通常の算術変換を適用する機能は、C++20 ([P1120R0](https://wg21.link/p1120r0)) では非推奨です。 言い換えると、列挙型と浮動小数点型の間で二項演算を使用すると、[/std:c++latest](../build/reference/std-specify-language-standard-version.md) コンパイラ オプションが有効になっているときに警告が発生するようになりました。

```cpp
enum E1 { a };
int main() {
  double i = a * 1.1;
}
```

この警告を回避するには、[static_cast](../cpp/static-cast-operator.md) を使用して 2 番目のオペランドを変換します。

```cpp
enum E1 { a };
int main() {
   double i = static_cast<int>(a) * 1.1;
}
```

### <a name="equality-and-relational-comparisons-of-arrays"></a>配列の等価比較と関係比較

C++20 ([P1120R0](https://wg21.link/p1120r0)) では、配列型の 2 つのオペランドの等価比較と関係比較は非推奨とされます。 言い換えると、2 つの配列間の比較演算は (ランクと範囲の類似性に関係なく) 警告となります。 Visual Studio 2019 バージョン 16.2 以降では、[/std:c++latest](../build/reference/std-specify-language-standard-version.md) コンパイラ オプションが有効になっている場合、次のコードで *C5056: operator '==': deprecated for array types* が生成されます。

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (a == b) { return 1; }
}
```

この警告を回避するには、最初の要素のアドレスを比較します。

```cpp
int main() {
    int a[] = { 1, 2, 3 };
    int b[] = { 1, 2, 3 };
    if (&a[0] == &b[0]) { return 1; }
}
```

2 つの配列の内容が等しいかどうかを判断するには、[std::equal](../standard-library/algorithm-functions.md#equal) 関数を使用します。

```cpp
std::equal(std::begin(a), std::end(a), std::begin(b), std::end(b));
```

### <a name="effect-of-defining-spaceship-operator-on--and-"></a>== と != で宇宙船演算子を定義した場合の効果

宇宙船演算子 ( **<=>** ) のみを定義しても、宇宙船演算子が `= default` ([P1185R2](https://wg21.link/p1185r2)) とマークされていなければ、 **==** または **!=** を伴う式は書き換えられなくなります。 次の例は、Visual Studio 2019 RTW およびバージョン 16.1 ではコンパイルされますが、Visual Studio 2019 バージョン 16.2 では C2678 が生成されます。

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

このエラーを回避するには、演算子 == を定義するか、これを既定値として宣言します。

```cpp
#include <compare>

struct S {
  int a;
  auto operator<=>(const S& rhs) const {
    return a <=> rhs.a;
  }
  bool operator==(const S&) const = default;
};
bool eq(const S& lhs, const S& rhs) {
  return lhs == rhs;
}
bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

### <a name="standard-library-improvements"></a>標準ライブラリの機能強化

- \<charconv>`to_chars()` (固定/科学的表記)。 (16.4 では一般的表記が計画されています。)
- [P0020R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0020r6.html): atomic\<float>、atomic\<double>、atomic\<long double>
- [P0463R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0463r1.html): エンディアン
- [P0482R6](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0482r6.html): char8_t のライブラリ サポート
- [P0600R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0600r1.pdf): [\[nodiscard]] (STL、Part 1)
- [P0653R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html): to_address()
- [P0754R2](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0754r2.pdf): \<version>
- [P0771R1](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0771r1.pdf): std::function の移動コンストラクター用の noexcept

## <a name="improvements_163"></a> Visual Studio 2019 バージョン 16.3 の準拠の強化

### <a name="stream-extraction-operators-for-char-removed"></a>char* のストリーム抽出演算子が削除されました

ポインターから文字へのストリーム抽出演算子が削除され、文字配列の抽出演算子に置き換えられました ([P0487R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0487r1.html) による)。 WG21 では、削除されたオーバーロードは安全でないと見なされます。 [/std:c++latest](../build/reference/std-specify-language-standard-version.md) モードの場合、次の例では *C2679: binary '>>': no operator found which takes a right-hand operand of type 'char\*' (or there is no acceptable conversion)* ('char*' 型の右側のオペランドを受け取る演算子が見つかりません (または変換できません)) が生成されるようになりました。

```cpp
   char x[42];
   char* p = x;
   std::cin >> std::setw(42);
   std::cin >> p;
```

このエラーを回避するには、抽出演算子を char [] 変数と共に使用します。

```cpp
char x[42];
std::cin >> x;
```

### <a name="new-keywords-requires-and-concept"></a>新しいキーワード **requires** と **concept**

Microsoft C++ コンパイラに新しいキーワード **requires** と **concept** が追加されました。 [/std:c++latest](../build/reference/std-specify-language-standard-version.md) モードで識別子としてそのいずれかを使用しようとすると、コンパイラによって *C2059: 構文エラー*が発生します。

### <a name="constructors-as-type-names-disallowed"></a>型名としてのコンストラクターが許可されない

コンストラクター名は、クラス テンプレート特殊化のエイリアスの後に修飾名で表示される場合、挿入されたクラス名とは見なされなくなりました。 これまでは、他のエンティティを宣言するために、コンストラクターを型名として使用することが許可されていました。 次の例では、*C3646:'TotalDuration': unknown override specifier* (不明なオーバーライド指定子) が生成されるようになりました。

```cpp
#include <chrono>

class Foo {
   std::chrono::milliseconds::duration TotalDuration{};
};

```

このエラーを回避するには、次に示すように `TotalDuration` を宣言します。

```cpp
#include <chrono>

class Foo {
  std::chrono::milliseconds TotalDuration {};
};
```

### <a name="stricter-checking-of-extern-c-functions"></a>extern "C" 関数の厳密なチェック

異なる名前空間で **extern "C"** 関数が宣言されている場合、以前のバージョンの Microsoft C++ コンパイラでは、宣言に互換性があるかどうかがチェックされませんでした。 Visual Studio 2019 バージョン 16.3 では、コンパイラによってこのようなチェックが実行されます。 [/permissive-](../build/reference/permissive-standards-conformance.md) モードの場合、次のコードでは *C2371: redefinition; different basic types* (異なる基本型) と *C2733: you cannot overload a function with C linkage* (C リンケージを使用して関数をオーバーロードすることはできません) が生成されます。

```cpp
using BOOL = int;

namespace N
{
   extern "C" void f(int, int, int, bool);
}

void g()
{
   N::f(0, 1, 2, false);
}

extern "C" void f(int, int, int, BOOL){}
```

前の例のエラーを回避するには、`f` の両方の宣言で **BOOL**ではなく **bool** を一貫して使用します。

### <a name="standard-library-improvements"></a>標準ライブラリの機能強化

非標準のヘッダー \<stdexcpt.h> と \<typeinfo.h> が削除されました。 これらが含まれるコードには、代わりに標準ヘッダー \<exception> と \<typeinfo> をそれぞれ含める必要があります。

## <a name="improvements_164"></a> Visual Studio 2019 バージョン 16.4 の準拠の強化

### <a name="better-enforcement-of-two-phase-name-lookup-for-qualified-ids-in-permissive-"></a>/permissive- での修飾 ID に対する 2 フェーズの名前参照の適用の強化

2 フェーズの名前参照では、テンプレートの本文で使用される非依存名が定義時にテンプレートに表示されている必要があります。 以前は、テンプレートがインスタンス化されるときにそのような名前が検索される場合がありました。 この変更により、[/permissive-](../build/reference/permissive-standards-conformance.md) フラグを使用した MSVC で、移植性が高く準拠したコードを記述しやすくなります。

Visual Studio 2019 バージョン 16.4 で **/permissive-** フラグが設定されている場合、次の例ではエラーが発生します。`f<T>` のテンプレートを定義するときに、`N::f` を参照できないためです。

```cpp
template <class T>
int f() {
    return N::f() + T{}; // error C2039: 'f': is not a member of 'N'
}

namespace N {
    int f() { return 42; }
}
```

通常、これは、次の例に示すように、不足しているヘッダーを追加するか、関数または変数を前方宣言することで修正できます。

```cpp
namespace N {
    int f();
}

template <class T>
int f() {
    return N::f() + T{};
}

namespace N {
    int f() { return 42; }
}
```

### <a name="implicit-conversion-of-integral-constant-expressions-to-null-pointer"></a>整数定数式から Null ポインターへの暗黙的な変換

MSVC コンパイラの準拠モード (/permissive-) において、[CWG イシュー 903](http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_defects.html#903) が実装されるようになりました。 このルールにより、整数定数式 (整数リテラル '0' を除く) を Null ポインター定数に暗黙的に変換することが許可されなくなります。 次の例では、準拠モードで C2440 が生成されます。

```cpp
int* f(bool* p) {
    p = false; // error C2440: '=': cannot convert from 'bool' to 'bool *'
    p = 0; // OK
    return false; // error C2440: 'return': cannot convert from 'bool' to 'int *'
}
```

このエラーを修正するには、**false** ではなく **nullptr** を使用します。 リテラル 0 は引き続き許可されることに注意してください。

```cpp
int* f(bool* p) {
    p = nullptr; // OK
    p = 0; // OK
    return nullptr; // OK
}
```

### <a name="standard-rules-for-types-of-integer-literals"></a>整数リテラルの型に関する標準ルール

MSVC の準拠モード ([/permissive-](../build/reference/permissive-standards-conformance.md) で有効) では、整数リテラルの型に対して標準ルールが使用されます。 以前は、大きすぎて符号付き 'int' に入らない 10 進リテラルは 'unsigned int' 型になりました。 そのようなリテラルは、2 番目に大きな符号付き整数型である 'long long' になるようになりました。 また、'll' というサフィックスが付いたリテラルで、大きすぎて符号付きの型に入らないものは、'unsigned long long' 型になります。

これにより、異なる警告の診断が生成され、リテラルに対して実行される算術演算について異なる動作が発生する可能性があります。

次の例は、Visual Studio 2019 バージョン 16.4 での新しい動作を示しています。 `i` 変数は **unsigned int** 型であるため、警告が発生します。 変数 `j` の上位ビットは 0 に設定されます。

```cpp
void f(int r) {
    int i = 2964557531; // warning C4309: truncation of constant value
    long long j = 0x8000000000000000ll >> r; // literal is now unsigned, shift will fill high-order bits with 0
}
```

次の例は、以前の動作を維持することで、警告と実行時の動作の変更を回避する方法を示しています。

```cpp
void f(int r) {
int i = 2964557531u; // OK
long long j = (long long)0x8000000000000000ll >> r; // shift will keep high-order bits
}
```

### <a name="function-parameters-that-shadow-template-parameters"></a>テンプレート パラメーターをシャドウする関数パラメーター

MSVC コンパイラでは、関数パラメーターによってテンプレート パラメーターがシャドウされるとエラーが発生するようになりました。

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T(&buffer)[Size], int& Size) // error C7576: declaration of 'Size' shadows a template parameter
{
    return f(buffer, Size, Size);
}
```

このエラーを修正するには、いずれかのパラメーターの名前を変更します。

```cpp
template<typename T>
void f(T* buffer, int size, int& size_read);

template<typename T, int Size>
void f(T (&buffer)[Size], int& size_read)
{
    return f(buffer, Size, size_read);
}
```

### <a name="user-provided-specializations-of-type-traits"></a>型特性のユーザー指定の特殊化

MSVC コンパイラでは、標準のサブ句 *meta.rqmts* に準拠して、`std` 名前空間で指定された type_traits テンプレートのいずれかに対するユーザー定義の特殊化が検出されると、エラーが発生するようになりました。 特に指定しない限り、このような特殊化によって未定義の動作が発生します。 次の例はこのルールに違反しているため、未定義の動作が発生します。また、`static_assert` はエラー **C2338** によって失敗します。

```cpp
#include <type_traits>
struct S;

template<>
struct std::is_fundamental<S> : std::true_type {};

static_assert(std::is_fundamental<S>::value, "fail");
```

このエラーを回避するには、目的の type_trait を継承する構造体を定義し、それを特殊化します。

```cpp
#include <type_traits>

struct S;

template<typename T>
struct my_is_fundamental : std::is_fundamental<T> {};

template<>
struct my_is_fundamental<S> : std::true_type { };

static_assert(my_is_fundamental<S>::value, "fail");
```

### <a name="changes-to-compiler-provided-comparison-operators"></a>コンパイラによって提供される比較演算子の変更点

MSVC コンパイラでは、[/std:c++latest](../build/reference/std-specify-language-standard-version.md) オプションが有効になっている場合に、[P1630R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2019/p1630r1.html) によって比較演算子に対する次の変更点が実装されるようになりました。

`operator==` を含む式で **bool** ではない戻り値の型が使用されている場合、それがコンパイラによって書き換えられることはなくなりました。 次のコードでは、"*エラー C2088: '!=': struct に対して正しくありません*" が生成されるようになりました。

```cpp
struct U {
  operator bool() const;
};

struct S {
  U operator==(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
  return lhs != rhs;
}
```

このエラーを回避するには、必要な演算子を明示的に定義する必要があります。

```cpp
struct U {
    operator bool() const;
};

struct S {
    U operator==(const S&) const;
    U operator!=(const S&) const;
};

bool neq(const S& lhs, const S& rhs) {
    return lhs != rhs;
}
```

既定化された比較演算子が union-like クラスのメンバーである場合、それがコンパイラによって定義されることはなくなりました。 次の例では、"*C2120: void 型が他の型と同時に使われました*" が生成されるようになりました。

```cpp
#include <compare>

union S {
    int a;
    char b;
    auto operator<=>(const S&) const = default;
};

bool lt(const S& lhs, const S& rhs) {
    return lhs < rhs;
}
```

このエラーを回避するには、演算子の本体を定義します。

```cpp
#include <compare>

union S {
  int a;
  char b;
  auto operator<=>(const S&) const { ... }
}; 

bool lt(const S& lhs, const S& rhs) {
  return lhs < rhs;
}
```

クラスに参照メンバーが含まれている場合、既定化された比較演算子がコンパイラによって定義されることはなくなりました。 次のコードでは、"*エラー C2120: void 型が他の型と同時に使われました*" が生成されるようになりました。

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const = default;
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

このエラーを回避するには、演算子の本体を定義します。

```cpp
#include <compare>

struct U {
    int& a;
    auto operator<=>(const U&) const { ... };
};

bool lt(const U& lhs, const U& rhs) {
    return lhs < rhs;
}
```

## <a name="update_160"></a> Visual Studio 2019 のバグ修正と動作の変更

### <a name="reinterpret_cast-in-a-constexpr-function"></a>constexpr 関数の reinterpret_cast

**constexpr** 関数では **reinterpret_cast** は無効です。 これまでは、Microsoft C++ コンパイラによって **reinterpret_cast** は **constexpr** のコンテキストで使用される場合に限り拒否されていました。 Visual Studio 2019 では、すべての言語標準モードで、コンパイラにより **constexpr** 関数の定義で **reinterpret_cast** が正しく診断されます。 次のコードでは、*C3615: constexpr function 'f' cannot result in a constant expression* (constexpr 関数 'f' の結果が定数式になることはありません) が生成されるようになりました。

```cpp
long long i = 0;
constexpr void f() {
    int* a = reinterpret_cast<int*>(i);
}
```

このエラーを回避するには、関数宣言から **constexpr** 修飾子を削除します。

### <a name="correct-diagnostics-for-basic_string-range-constructor"></a>basic_string 範囲コンストラクターの正しい診断

Visual Studio 2019 では、`basic_string` 範囲コンストラクターで `static_cast` を含むコンパイラ診断が非表示になることがなくなりました。 次のコードは Visual Studio 2017 では、`out` の初期化時、データが失われ、`wchar_t` が **char** になる可能性がありますが、警告なくコンパイルされます。

```cpp
std::wstring ws = /* … */;
std::string out(ws.begin(), ws.end());
```

Visual Studio 2019 の場合、*C4244: 'argument': conversion from 'wchar_t' to 'const _Elem', possible loss of data* が正しく発生します。 この計画を回避するには、この例のように std::string を初期化できます。

```cpp
std::wstring ws = L"Hello world";
std::string out;
for (wchar_t ch : ws)
{
    out.push_back(static_cast<char>(ch));
}
```

### <a name="incorrect-calls-to--and---under-clr-or-zw-are-now-correctly-detected"></a>/clr または /ZW で += や -= の間違った呼び出しを正しく検出できるようになりました

`/clr` または `/ZW` で += や -= の無効な呼び出しに対して、コンパイラが何も表示せずにエラーを無視し、何のコードも生成しないというバグが Visual Studio 2017 にありました。 次のコードは Visual Studio 2017 ではエラーなくコンパイルされますが、Visual Studio 2019 の場合、*error C2845:'System::String ^': pointer arithmetic not allowed on this type* が正しく発生します。

```cpp
public enum class E { e };

void f(System::String ^s)
{
    s += E::e; // C2845 in VS2019
}
```

この例のエラーを回避するには、`s += E::e.ToString();` のように、ToString() で演算子を使用します。

### <a name="initializers-for-inline-static-data-members"></a>インライン静的データ メンバーの初期化子

**インライン constexpr** 初期化子と**静的 constexpr** 初期化子内の無効なメンバー アクセスが正しく検出されるようになりました。 次の例は Visual Studio 2017 ではエラーなくコンパイルされますが、`/std:c++17` モードの Visual Studio 2019 では、*error C2248: cannot access private member declared in class 'X'* が発生します。

```cpp
struct X
{
    private:
        static inline const int c = 1000;
};

struct Y : X
{
    static inline int d = c; // C2248 in Visual Studio 2019
};
```

このエラーを回避するには、メンバー `X::c` を protected として宣言します。

```cpp
struct X
{
    protected:
        static inline const int c = 1000;
};
```

### <a name="c4800-reinstated"></a>C4800 の復帰

MSVC には以前、**bool** への暗黙的変換に関するパフォーマンス警告 C4800 がありました。 これが煩わしく、かつ非表示にできないため、Visual Studio 2017 で削除されました。 しかしながら、Visual Studio 2017 が使用されている間、この警告が役に立った事例についてたくさんのフィードバックがありました。 Visual Studio 2019 では、慎重に調整された C4800 とそれに付属する C4165 を復帰させました。 いずれの警告も、明示的な型変換か該当する型の 0 と比較することで、簡単に非表示にできます。 C4800 は既定でオフのレベル 4 警告であり、C4165 は既定でオフのレベル 3 警告です。 いずれも `/Wall` コンパイラ オプションで検出できます。

次の例では C4800 と C4165 が `/Wall` の下で発生します。

```cpp
bool test(IUnknown* p)
{
    bool valid = p; // warning C4800: Implicit conversion from 'IUnknown*' to bool. Possible information loss
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return hr; // warning C4165: 'HRESULT' is being converted to 'bool'; are you sure this is what you want?
}
```

前の例の警告を回避する目的で、コードを次のように記述できます。

```cpp
bool test(IUnknown* p)
{
    bool valid = p != nullptr; // OK
    IDispatch* d = nullptr;
    HRESULT hr = p->QueryInterface(__uuidof(IDispatch), reinterpret_cast<void**>(&d));
    return SUCCEEDED(hr);  // OK
}
```

### <a name="local-class-member-function-doesnt-have-a-body"></a>ローカル クラスのメンバー関数に本体がない

Visual Studio 2017 では、*C4822:Local class member function doesn't have a body* は、コンパイラ オプション `/w14822` が明示的に設定されている場合にのみ発生します。`/Wall` で表示されることはありません。 Visual Studio 2019 では、C4822 はデフォルトでオフの警告であり、`/w14822` を明示的に設定しなくても `/Wall` の下で見つかります。

```cpp
void example()
{
    struct A
        {
            int boo(); // warning C4822
        };
}
```

### <a name="function-template-bodies-containing-constexpr-if-statements"></a>constexpr if ステートメントを含む関数テンプレートの本体

**if constexpr** ステートメントを含むテンプレート関数の本体では、一部の [/permissive-](../build/reference/permissive-standards-conformance.md) 解析関連チェックが有効になっています。 たとえば、Visual Studio 2017 では、*C7510:'Type': use of dependent type name must be prefixed with 'typename'* (依存型名は先頭を 'typename' にする必要があります) は **/permissive-** オプションが設定されていない場合にのみ、次のコードで発生します。 Visual Studio 2019 の場合、 **/permissive-** オプションが設定されていても、同じコードでエラーが発生します。

```cpp
template <typename T>

int f()
{
    T::Type a; // error C7510

    if constexpr (T::val)
    {
        return 1;
    }
    else
    {
        return 2;
    }
}

struct X
{
    using Type = X;
    constexpr static int val = 1;
};

int main()
{
    return f<X>();
}
```

このエラーを回避するには、`typename T::Type a;` のように、**typename** キーワードを `a` の宣言に追加します。

### <a name="inline-assembly-code-isnt-supported-in-a-lambda-expression"></a>インライン アセンブリ コードがラムダ式でサポートされない

Microsoft C++ チームは最近、ラムダ内のインライン アセンブラーが実行時、`ebp` (リターン アドレス レジスタ) の破損につながる可能性があるセキュリティ上の問題を発見しました。 悪意のある攻撃者は、このシナリオを活用できる可能性があります。 問題の性質、インライン アセンブラーが x86 でのみサポートされるという事実、インライン アセンブラーとコンパイラの残りの部分の対話が乏しいことを考慮すると、この問題の最も安全な解決策は、ラムダ式内でインライン アセンブラーを禁止することでした。

ラムダ式内でのインライン アセンブラーの唯一の使い方として出回っていたのは、リターン アドレスをキャプチャすることを目的としたものでした。 このシナリオでは、コンパイラ固有の `_ReturnAddress()` を使用し、すべてのプラットフォームでリターン アドレスをキャプチャできます。

次のコードでは、*C7552: inline assembler is not supported in a lambda* が Visual Studio 2017 15.9 と Visual Studio 2019 の両方で発生します。

```cpp
#include <cstdio>

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;

    auto lambda = [&]
    {
        __asm {

            mov eax, x
            mov y, eax
        }
    };

    lambda();
    return y;
}
```

このエラーを回避するには、次の例のように、名前付きの関数にアセンブリ コードを移動します。

```cpp
#include <cstdio>

void g(int& x, int& y)
{
    __asm {
        mov eax, x
        mov y, eax
    }
}

int f()
{
    int y = 1724;
    int x = 0xdeadbeef;
    auto lambda = [&]
    {
        g(x, y);
    };
    lambda();
    return y;
}

int main()
{
    std::printf("%d\n", f());
}
```

### <a name="iterator-debugging-and-stdmove_iterator"></a>反復子のデバッグと `std::move_iterator`

`std::move_iterator` のラッピングを正しく解除する目的で反復子のデバッグ機能が導入されました。 たとえば、`std::copy(std::move_iterator<std::vector<int>::iterator>, std::move_iterator<std::vector<int>::iterator>, int*)` では、`memcpy` 高速パスを作動させることができるようになりました。

### <a name="fixes-for-xkeycheckh-keyword-enforcement"></a>\<xkeycheck.h> キーワード強制の修正

標準ライブラリのマクロを置換するキーワード強制 \<xkeycheck.h> が汎用的なメッセージではなく、検出された実際に問題となるキーワードを表示するように修正されました。 また、C++ 20 キーワード対応となり、IntelliSense でランダムのキーワードがマクロであるととらえられることがなくなりました。

### <a name="allocator-types-no-longer-deprecated"></a>非推奨でなくなったアロケーター型

`std::allocator<void>`、`std::allocator::size_type`、および `std::allocator::difference_type` が非推奨でなくなりました。

### <a name="correct-warning-for-narrowing-string-conversions"></a>文字列変換を絞り込むための正しい警告

C4244 絞り込み警告を間違って非表示にした、標準では呼び出されない不適切な `static_cast` が `std::string` から削除されました。 `std::string::string(const wchar_t*, const wchar_t*)` を呼び出そうとすると、*C4244 "narrowing a wchar_t into a char"* が正しく表示されるようになりました。

### <a name="various-filesystem-correctness-fixes"></a>\<filesystem> のさまざまな正確性修正

- ディレクトリの最後の書き込み時刻を変更しようとすると失敗する `std::filesystem::last_write_time` が修正されました。
- `std::filesystem::directory_entry` コンストラクターには、存在しないターゲット パスが指定されたとき、例外をスローせず、エラー結果が格納されるようになりました。
- `existing_p` がシンボリック リンクのとき、基礎となる `CreateDirectoryExW` 関数で `copy_symlink` が使用されるため、`std::filesystem::create_directory` の 2 パラメーター バージョンが 1 パラメーター バージョンを呼び出すように変更されました。
- 壊れたシンボリック リンクが見つかっても `std::filesystem::directory_iterator` ではエラーを出さなくなりました。
- `std::filesystem::space` で相対パスを受け取るようになりました。
- [LWG 3096](https://cplusplus.github.io/LWG/issue3096) で報告されていた末尾のスラッシュと `std::filesystem::path::lexically_relative` が混同されることがなくなりました。
- `std::filesystem::create_symlink` にスラッシュを含むパスを拒否する `CreateSymbolicLinkW` の回避策が考案されました。
- Windows 10 LTSB 1609 に存在するが、実際にはファイルを削除できない POSIX 削除モード `delete` 関数の回避策が考案されました。
- `std::boyer_moore_searcher` と `std::boyer_moore_horspool_searcher` のコピー コンストラクターとコピー代入演算子で実際にコピーできるようになりました。

### <a name="parallel-algorithms-on-windows-8-and-later"></a>Windows 8 以降の並列アルゴリズム

並列アルゴリズム ライブラリでは、Windows 7 以前のフェイク バージョンを常時使用せず、Windows 8 以降の実際の `WaitOnAddress` ファミリが正しく使用されるようになりました。

### <a name="stdsystem_categorymessage-whitespace"></a>`std::system_category::message()` のスペース

`std::system_category::message()` では、返されたメッセージから末尾のスペースが削除されるようになりました。

### <a name="stdlinear_congruential_engine-divide-by-zero"></a>`std::linear_congruential_engine` のゼロ除算

`std::linear_congruential_engine` のゼロ除算を誘発していたいくつかの条件が修正されました。

### <a name="fixes-for-iterator-unwrapping"></a>反復子ラッピング解除の修正

C++ チームのブログ記事「[STL Features and Fixes in VS 2017 15.8 (VS 2017 15.8 での STL の機能と修正)](https://devblogs.microsoft.com/cppblog/stl-features-and-fixes-in-vs-2017-15-8/)」で説明されているように、Visual Studio 2017 15.8 におけるプログラマ/ユーザー統合を目的として最初に公開された反復子ラッピング解除機構で、標準ライブラリ反復子から派生する反復子のラッピングが解除されなくなりました。 たとえば、`std::vector<int>::iterator` から派生し、動作をカスタマイズしようとするユーザーには、標準ライブラリ アルゴリズムを呼び出すとき、ポインターの動作ではなく、カスタマイズされた動作が与えられるようになりました。

順序付けられていないコンテナー `reserve` 関数は、[LWG 2156](https://cplusplus.github.io/LWG/issue2156) に説明があるように、N 要素に予約されるようになりました。

### <a name="time-handling"></a>時間の処理

- 以前は、`condition_variable::wait_for(seconds::max())` など、同時実行ライブラリに渡されていた一部の時間値がオーバーフローしていました。 このようなオーバーフローが解消され、うわべではランダムの 29 日周期で動作が変わりました (基礎となる Win32 API で受け取られる uint32_t ミリ秒がオーバーフローしたとき)。

- \<ctime> ヘッダーでは、グローバル名前空間で `timespec` と `timespec_get` を宣言することに加え、名前空間 `std` でそれらを正しく宣言できるようになりました。

### <a name="various-fixes-for-containers"></a>コンテナーのさまざまな修正

- 標準ライブラリのさまざまな内部コンテナー関数がプライベートになり、IntelliSense が使いやすくなりました。 MSVC の今後のリリースでは、メンバーをプライベートにする修正が追加される予定です。

- `list`、`map`、`unordered_map` のようなノードベース コンテナーが破損する、例外の安全性における正確性の問題が解消されました。 `propagate_on_container_copy_assignment` または `propagate_on_container_move_assignment` の再代入演算の間、古いアロケーターを持つコンテナーのセンチネル ノードを解放し、古いアロケーターで POCCA/POCMA 代入を行い、新しいアロケーターからセンチネル ノードの取得を試みました。 この代入に失敗した場合、コンテナーは破損し、さらには破棄できなくなります。センチネル ノードを持つと、データ構造を変えられなくなるためです。 このコードは、既存のセンチネル ノードを破棄する前に、ソース コンテナーのアロケーターから新しいセンチネル ノードを割り当てるように修正されました。

- `is_always_equal` が宣言されたアロケーターの場合でも、常に `propagate_on_container_copy_assignment`、`propagate_on_container_move_assignment`、`propagate_on_container_swap` に基づいてアロケーターをコピー、移動、スワップするようにコンテナーが修正されました。

- [P0083 "Splicing Maps And Sets"](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) に基づき右辺値コンテナーを受け取るコンテナーの結合および抽出メンバー関数向けのオーバーロードが追加されました。

### <a name="stdbasic_istreamread-processing-of-rn--n"></a>`std::basic_istream::read` での \\r\\n => \\n の処理

\\r\\n => \\n 処理の一環として、与えられたバッファーの一部を一時的に書き込まないよう、`std::basic_istream::read` が修正されました。 この変更により、Visual Studio 2017 15.8 において 4K を超える読み込みで得られるパフォーマンス上のいくつかの長所を放棄することになります。 ただし、文字ごとに 3 つの仮想呼び出しを回避することから得られる効率性の改善が残されています。

### <a name="stdbitset-constructor"></a>`std::bitset` コンストラクター

`std::bitset` のコンストラクターで、大きなビットセットの 1 と 0 が逆の順序で読み取られることがなくなりました。

### <a name="stdpairoperator-regression"></a>`std::pair::operator=` 回帰

[LWG 2729 "Missing SFINAE on std::pair::operator=";](https://cplusplus.github.io/LWG/issue2729) の導入時に見つかった `std::pair` の代入演算子の回帰が修正されました。 再び `std::pair` に変換できる型を正しく受け取るようになりました。

### <a name="non-deduced-contexts-for-add_const_t"></a>`add_const_t` の非推定コンテキスト

`add_const_t` や関連関数が非推定コンテキストであることが求められる、型の特徴の軽微なバグが修正されました。 言い換えると、`add_const_t` は `const T` ではなく、`typename add_const<T>::type` のエイリアスにする必要があります。

## <a name="update_162"></a> 16.2 のバグ修正と動作の変更

### <a name="const-comparators-for-associative-containers"></a>連想コンテナーの const 比較子

[set](../standard-library/set-class.md)、[map](../standard-library/map-class.md)、[multiset](../standard-library/multiset-class.md)、[multimap](../standard-library/multimap-class.md) の検索と挿入のコードは、コード サイズの削減のためにマージされました。 検索操作で以前に実行されたのと同じように、挿入操作によって **const** 比較ファンクターで小なり比較が呼び出されるようになりました。 次のコードは、Visual Studio 2019 バージョン 16.1 以前ではコンパイルされますが、Visual Studio 2019 バージョン 16.2 では C3848 が生成されます。

```cpp
#include <iostream>
#include <map>

using namespace std;

struct K
{
   int a;
   string b = "label";
};

struct Comparer  {
   bool operator() (K a, K b) {
      return a.a < b.a;
   }
};

map<K, double, Comparer> m;

K const s1{1};
K const s2{2};
K const s3{3};

int main() {

   m.emplace(s1, 1.08);
   m.emplace(s2, 3.14);
   m.emplace(s3, 5.21);

}
```

このエラーを回避するには、次のように比較演算子 **const** を使用します。

```cpp
struct Comparer  {
   bool operator() (K a, K b) const {
      return a.a < b.a;
   }
};

```

::: moniker-end

::: moniker range="vs-2017"

## <a name="improvements_150"></a> Visual Studio 2017 RTW (バージョン 15.0) の準拠の強化

Visual Studio 2017 の Microsoft C++ コンパイラは、汎用の **constexpr** および集計用の非静的データ メンバーの初期化 (NSDMI) のサポートと共に、C++ 14 標準で追加されたすべての機能に対応するようになりました。 ただし、コンパイラには、C++11 標準および C++98 標準の一部の機能がありません。 コンパイラの現在の状態については、「[Microsoft C++ 言語の準拠表](../visual-cpp-language-conformance.md)」を参照してください。

### <a name="c11-expression-sfinae-support-in-more-libraries"></a>C++11:より多くのライブラリでの SFINAE 式のサポート

Visual C コンパイラは、SFINAE 式のサポートを継続的に向上させています。これは、**decltype** および **constexpr** 式がテンプレート パラメーターとして使用されるテンプレート引数の推論と代替のために必要です。 詳細については、「[Expression SFINAE improvements in Visual Studio 2017 RC](https://blogs.msdn.microsoft.com/vcblog/2016/06/07/expression-sfinae-improvements-in-vs-2015-update-3)」 (Visual Studio 2017 RC での SFINAE 式の機能拡張) を参照してください。

### <a name="c14-nsdmi-for-aggregates"></a>C++14:集計用の NSDMI

集計は、クラスの配列であり、ユーザー指定のコンストラクターがなく、プライベートまたは保護された非静的データ メンバーを持たず、基底クラスや仮想関数もありません。 C++ 14 以降、集計にメンバーの初期化子を含めることができます。 詳細については、「[Member initializers and aggregates](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3605.html)」 (メンバー初期化子と集計) を参照してください。

### <a name="c14-extended-constexpr"></a>C++14:拡張された **constexpr**

**constexpr** として宣言された式には、特定の種類の宣言、if および switch ステートメント、loop ステートメント、constexpr 式の評価内で有効期間が開始されたオブジェクトの変異を含めることができます。 さらに、**constexpr** の非静的メンバー関数を暗黙的に**構築する**という要件はなくなりました。 詳細については、「[Relaxing constraints on constexpr functions](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)」 (constexpr 関数に対する制約の緩和) を参照してください。

### <a name="c17-terse-static_assert"></a>C++17:簡易 `static_assert`

`static_assert` のメッセージ パラメーターは省略可能です。 詳細については、「[Extending static_assert, v2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)」 (static_assert, v2 の拡張) を参照してください。

### <a name="c17-fallthrough-attribute"></a>C++17: `[[fallthrough]]` 属性

**/std:c++17** モードで、`[[fallthrough]]` 属性は、フォールスルー動作を意図するコンパイラに対するヒントとして switch ステートメントのコンテキスト内で使用できます。 この属性により、コンパイラがこのような場合に警告を発行することを防止できます。 詳細については、「[Wording for \[\[fallthrough\]\] attribute ([[fallthrough]] 属性の用語)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r0.pdf)」を参照してください。

### <a name="generalized-range-based-for-loops"></a>範囲ベースの for-loop (汎用)

範囲ベースの for ループでは、`begin()` および `end()` が同じ型のオブジェクトを返す必要はなくなりました。 この変更により、`end()` で [range-v3](https://github.com/ericniebler/range-v3) および completed-but-not-quite-published 範囲の技術仕様で使用される sentinel を返すことができます。 詳細については、「[Generalizing the Range-Based For Loop](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)」 (範囲ベースの for loop の汎用化) を参照してください。

## <a name="improvements_153"></a> 15.3 の準拠の強化

### <a name="constexpr-lambdas"></a>constexpr ラムダ

定数式でラムダ式を使用できるようになりました。 詳細については、「[constexpr lambda expressions in C++](../cpp/lambda-expressions-constexpr.md)」(C++ での constexpr ラムダ式) をご覧ください。

### <a name="if-constexpr-in-function-templates"></a>関数テンプレートでの **if constexpr**

関数テンプレートに、**if constexpr** ステートメントを含めてコンパイル時の分岐を有効にできます。 詳細については、「[if constexpr statements](../cpp/if-else-statement-cpp.md#if_constexpr)」(if constexpr 式) をご覧ください。

### <a name="selection-statements-with-initializers"></a>初期化子を含む選択ステートメント

**if** ステートメントには、ステートメント自体のブロック スコープで変数を導入する初期化子を含めることができます。 詳細については、「[if statements with initializer](../cpp/if-else-statement-cpp.md#if_with_init)」(初期化子を含む if 式) をご覧ください。

### <a name="maybe_unused-and-nodiscard-attributes"></a>`[[maybe_unused]]` 属性および `[[nodiscard]]` 属性

新しい属性 `[[maybe_unused]]` は、エンティティが使用されていない場合に警告を発生させません。 `[[nodiscard]]` 属性は、関数呼び出しの戻り値が破棄された場合に警告を発生させます。 詳しくは、「[Attributes in C++ (C++ における属性)](../cpp/attributes.md)」をご覧ください。

### <a name="using-attribute-namespaces-without-repetition"></a>繰り返しのない属性名前空間の使用

1 つの属性リストで 1 つの名前空間の識別子のみを有効にする新しい構文です。 詳しくは、「[Attributes in C++ (C++ における属性)](../cpp/attributes.md)」をご覧ください。

### <a name="structured-bindings"></a>構造化バインド

値が、配列、`std::tuple`、`std::pair` のいずれかであるか、すべてのパブリックの非静的データ メンバーを持つときに、1 つの宣言で、そのコンポーネントの個別の名前を持つ値を格納できるようになりました。 詳細については、「[Structured Bindings](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0144r0.pdf)」(構造化バインド) と「[Returning multiple values from a function](../cpp/functions-cpp.md#multi_val)」(関数から複数の値を返す) をご覧ください。

### <a name="construction-rules-for-enum-class-values"></a>**列挙型クラス**の値の構築ルール

定義で列挙子を導入せず、ソースがリスト初期化構文を使用している場合に、スコープ列挙の基になる型から列挙型自体への、暗黙的な/非縮小の変換が使用できるようになりました。 詳細については、「[Construction Rules for enum class Values](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)」(列挙型クラスの値の構築ルール) と[列挙](../cpp/enumerations-cpp.md#no_enumerators)に関する記事をご覧ください。

### <a name="capturing-this-by-value"></a>`*this` の値によるキャプチャ

ラムダ式の `*this` オブジェクトが値でキャプチャできるようになりました。 この変更により、特に新しいコンピューター アーキテクチャで、並列で非同期の操作でラムダが呼び出されるシナリオを実現できます。 詳しくは、「[Lambda Capture of \*this by Value as \[=,\*this\] (*this の [=,*this] としての値によるラムダ キャプチャ)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)」をご覧ください。

### <a name="removing-operator-for-bool"></a>**bool** の `operator++` の削除

`operator++` は **bool** 型でサポートされなくなりました。 詳しくは、「[Remove Deprecated operator++(bool) (非推奨の operator++(bool) の削除)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)」をご覧ください。

### <a name="removing-deprecated-register-keyword"></a>非推奨の **register** キーワードの削除

**register** キーワードは、以前は非推奨でしたが (コンパイラでは無視される)、言語から削除されました。 詳しくは、「[Remove Deprecated Use of the register Keyword (register キーワードの非推奨の使用の削除)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)」をご覧ください。

## <a name="improvements_155"></a> 15.5 の準拠の強化

\[14] でマークされた機能は、 **/std:c++14** モードでも無条件で使用できます。

### <a name="new-compiler-switch-for-extern-constexpr"></a>**extern constexpr** の新しいコンパイラ スイッチ

Visual Studio の以前のバージョンでは、変数が **extern** としてマークされている場合でも、コンパイラは常に **constexpr** 変数を提供しました。 Visual Studio 2017 バージョン 15.5 では、新しいコンパイラ スイッチ [/Zc:externConstexpr](../build/reference/zc-externconstexpr.md) により、正しい標準準拠の動作が可能になります。 詳細については、[extern constexpr のリンク](#extern_linkage)を参照してください。

### <a name="removing-dynamic-exception-specifications"></a>動的例外指定の削除

[P0003R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html) C++11 では動的な例外の指定は非推奨となりました。 C++17 から機能が削除されますが、(引き続き) `noexcept(true)` のエイリアスとして非推奨の `throw()` 仕様が維持されます。 詳細については、「[動的例外指定の削除と noexcept](#noexcept_removal)」を参照してください。

### `not_fn()`

[P0005R4](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html) `not_fn` は `not1` と `not2` の置き換えです。

### <a name="rewording-enable_shared_from_this"></a>`enable_shared_from_this` の新しい表現

[P0033R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html) C++ 11 で `enable_shared_from_this` が追加されました。 C++ 17 標準では、特殊なケースの処理を改善するために仕様を更新します。 [14]

### <a name="splicing-maps-and-sets"></a>マップと設定のスプライス

[P0083R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf) この機能により、ノードを連想コンテナー (たとえば、`map`、`set`、`unordered_map`、`unordered_set`) から抽出し、それを変更して同じコンテナーまたは同じノード型を使用する別のコンテナーに挿入することができます (一般的なユース ケースでは、`std::map` からノードを抽出し、キーを変更して再挿入します)。

### <a name="deprecating-vestigial-library-parts"></a>残留ライブラリ パーツの廃止

[P0174R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html) C++ 標準ライブラリのいくつかの機能は、長年にわたって新しい機能で置き換えられました。そうでないものは、あまり便利ではないか、または問題があることがわかっています。 これらの機能は、c++ 17 で正式に非推奨とされます。

### <a name="removing-allocator-support-in-stdfunction"></a>`std::function` のアロケーター サポートの削除

[P0302R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html) C++17 の前には、クラス テンプレート `std::function` に、アロケーター引数を取るいくつかのコンストラクターがありました。 ただし、このコンテキストでのアロケーターの使用には問題があり、セマンティクスが不明確でした。 問題のコントラクターは削除されました。

### <a name="fixes-for-not_fn"></a>`not_fn()` の修正

[P0358R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)`std::not_fn` の新しい表現は、ラッパー呼び出し時の値のカテゴリの伝達をサポートします。

### <a name="shared_ptrt-shared_ptrtn"></a>`shared_ptr<T[]>`、`shared_ptr<T[N]>`

[P0414R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html) ライブラリ基盤から C++ 17 への `shared_ptr` の変更のマージ。 [14]

### <a name="fixing-shared_ptr-for-arrays"></a>配列の `shared_ptr` の修正

[P0497R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html) 配列の shared_ptr のサポートを修正します。 [14]

### <a name="clarifying-insert_return_type"></a>`insert_return_type` の明確化

[P0508R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html) 固有のキーを持つ関連するコンテナー、固有ではないキーを持つ順序付けられていないコンテナーには、入れ子になった型 `insert_return_type` を返すメンバー関数 `insert` があります。 戻りの型は、コンテナーの反復子と NodeType でパラメーター化された型の特殊な形式として定義されるようになりました。

### <a name="inline-variables-for-the-standard-library"></a>標準ライブラリのインライン変数

[P0607R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)

### <a name="annex-d-features-deprecated"></a>非推奨になった Annex D 機能

C++ 標準の Annex D は、`shared_ptr::unique()`、`<codecvt>`、`namespace std::tr1` を含む非推奨になったすべての機能を含んでいます。 **/std:c++17** コンパイラ スイッチが設定されている場合、Annex D のほとんどすべての標準ライブラリの機能は非推奨としてマークされます。 詳細については、「[非推奨としてマークされた Annex D の標準ライブラリの機能](#annex_d)」を参照してください。

`<experimental/filesystem>` の `std::tr2::sys` 名前空間は、 **/std:c++14** の下では既定で非推奨の警告を出し、 **/std:c++17** では既定で削除されました。

非標準の拡張 (クラス内の明示的な特殊化) を回避することで `<iostream>` の適合性を向上させます。

標準ライブラリでは、変数テンプレートを内部で使用するようになりました。

C++17 コンパイラの変更に応じて、型システムへの **noexcept** の追加や、dynamic-exception-specifications の削除などの標準ライブラリの更新が行われました。

## <a name="improvements_156"></a> 15.6 の準拠の強化

### <a name="c17-library-fundamentals-v1"></a>C++17: ライブラリ基礎 V1

[P0220R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html): C++17 用のライブラリ基礎技術仕様が標準に組み込まれています。 \<experimental/tuple>、\<experimental/optional>、\<experimental/functional>、\<experimental/any>、\<experimental/string_view>、\<experimental/memory>、\<experimental/memory_resource>、\<experimental/algorithm> の更新内容が含まれています。

### <a name="c17-improving-class-template-argument-deduction-for-the-standard-library"></a>C++17:標準ライブラリのクラス テンプレート引数の推論の機能強化

[P0739R0](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html): `scoped_lock` を一貫して使用できるように、`adopt_lock_t` を `scoped_lock` のパラメーター リストの先頭に移動します。 コピー割り当てを有効にするために、`std::variant` コンストラクターがオーバーロードの解決法に関与することを許可します。

## <a name="improvements_157"></a> 15.7 の準拠の強化

### <a name="c17-rewording-inheriting-constructors"></a>C++17:コンストラクター継承の新しい表現

[P0136R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html): コンストラクターに名前を付ける **using** 宣言では、追加の派生クラス コンストラクターを宣言するのでなく、派生クラスの初期化において対応する基本クラスのコンストラクターを表示できるようにしました。 この新しい表現は、C++14 からの変更です。 Visual Studio 2017 バージョン 15.7 以降の **/std:c++17** モードでは、C++14 において有効であり、かつ継承中のコンストラクターを使用するコードが、無効である場合もあれば、異なるセマンティクスを持つ場合もあります。

次の例では C++14 のビヘイビアーを示します。

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n) = delete; // Error C2280
};

B b(42L); // Calls B<long>(long), which calls A(int)
          //  due to substitution failure in A<long>(long).
```

次の例では、Visual Studio 15.7 での **/std:c++17** のビヘイビアーを示します。

```cpp
struct A {
    template<typename T>
    A(T, typename T::type = 0);
    A(int);
};

struct B : A {
    using A::A;
    B(int n)
    {
        //do something
    }
};

B b(42L); // now calls B(int)
```

詳細については、「[コンストラクター](../cpp/constructors-cpp.md#inheriting_constructors)」を参照してください。

### <a name="c17-extended-aggregate-initialization"></a>C++17:集約の初期化 (拡張)

[P0017R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)

基底クラスのコンストラクターがパブリックではないが、派生クラスからアクセスできる場合、Visual Studio 2017 バージョン 15.7 の **/std:c++17** モードでは、空のかっこを使用して派生型のオブジェクトを初期化することができなくなりました。
次の例では、C++14 の準拠ビヘイビアーを示します。

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};

struct Derived : Base {};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // OK in C++14: Calls Derived::Derived()
               // which can call Base ctor.
```

C++17 で、`Derived` は集約型と見なされるようになりました。 つまり、既定のプライベート コンストラクターによる `Base` の初期化は、集約初期化ルールの一部として直接実行されます。 以前、`Base` プライベート コンストラクターは `Derived` コンストラクターを介して呼び出され、friend 宣言があるために成功していました。
次の例では、Visual Studio バージョン 15.7 の C++17 ビヘイビアーを **/std:c++17** モードで示しまています。

```cpp
struct Derived;
struct Base {
    friend struct Derived;
private:
    Base() {}
};
struct Derived : Base {
    Derived() {} // add user-defined constructor
                 // to call with {} initialization
};
Derived d1; // OK. No aggregate init involved.
Derived d2 {}; // error C2248: 'Base::Base': cannot access
               // private member declared in class 'Base'
```

### <a name="c17-declaring-non-type-template-parameters-with-auto"></a>C++17:auto による非型テンプレート パラメーターの宣言

[P0127R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)

**/std:c++17** モードで、コンパイラは、**auto** によって宣言されている非型テンプレート引数の型を推測できるようになりました。

```cpp
template <auto x> constexpr auto constant = x;

auto v1 = constant<5>;      // v1 == 5, decltype(v1) is int
auto v2 = constant<true>;   // v2 == true, decltype(v2) is bool
auto v3 = constant<'a'>;    // v3 == 'a', decltype(v3) is char
```

この新しい機能の影響の 1 つとして、有効な C++14 コードが無効になったり、異なるセマンティクスを持つようになったりする場合があることが挙げられます。 たとえば、以前は無効であったオーバーロードの一部が有効になりました。 次の例では、`example(p)` の呼び出しが `example(void*);` にバインドされているためにコンパイルされる C++14 コードを示します。 Visual Studio 2017 バージョン 15.7 の **/std:c++17** モードでは、`example` 関数テンプレートが最も適しています。

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*) = delete;

void example(void *);

void sample(A<0> *p)
{
    example(p); // OK in C++14
}
```

次の例では、Visual Studio 15.7 の C++17 コードを **/std:c++17** モードで示します。

```cpp
template <int N> struct A;
template <typename T, T N> int example(A<N>*);

void example(void *);

void sample(A<0> *p)
{
    example(p); // C2280: 'int example<int,0>(A<0>*)': attempting to reference a deleted function
}
```

### <a name="c17-elementary-string-conversions-partial"></a>C++17:基本文字列変換 (部分的)

[P0067R5](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html): 整数と文字列の間、および浮動小数点数と文字列の間の変換ためのロケールに依存しない低レベルの機能

### <a name="c20-avoiding-unnecessary-decay-partial"></a>C++20:不要な decay の回避 (部分的)

[P0777R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf): "decay" の概念と const 修飾子または reference 修飾子の単純な削除の概念との区別を追加します。  一部のコンテキストでは、新しい型の特性 `remove_reference_t` が `decay_t` に置き換えられます。 `remove_cvref_t` のサポートは Visual Studio 2019 で実装されます。

### <a name="c17-parallel-algorithms"></a>C++17:並列アルゴリズム

[P0024R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html): 並列 TS は、若干の変更が加えられて、標準に組み込まれます。

### <a name="c17-hypotx-y-z"></a>C++17: `hypot(x, y, z)`

[P0030R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf): **float** 型、**double** 型、**long double** 型について、`std::hypot` に 3 つの新しいオーバーロードを追加します。それぞれが 3 つの入力パラメーターを持っています。

### <a name="c17-filesystem"></a>C++17: \<filesystem>

[P0218R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html): ファイル システム TS を、表現に少し変更を加えて、標準に採用します。

### <a name="c17-mathematical-special-functions"></a>C++17:数学的特殊関数

[P0226R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html): 数学的特殊関数に関する以前の技術仕様を標準的な \<cmath> ヘッダーに採用します。

### <a name="c17-deduction-guides-for-the-standard-library"></a>C++17:標準ライブラリの推論ガイド

[P0433R2](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html): [P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) (クラス テンプレート引数の推論に対するサポートを追加) の C++17 採用の利点を活用するための、STL の更新。

### <a name="c17-repairing-elementary-string-conversions"></a>C++17:基本文字列変換の修正

[P0682R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0682r1.html): 基本文字列変換の新しい関数を P0067R5 から新しいヘッダー \<charconv> に移動します。さらに、`std::error_code` ではなく `std::errc` を使用するようにエラー処理を変更するなど、他の機能強化も行います。

### <a name="c17-constexpr-for-char_traits-partial"></a>C++17: `char_traits` の **constexpr** (部分的)

[P0426R1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html): `std::string_view` を定数式で使用できるようにするために、`std::traits_type` のメンバー関数である `length`、`compare`、`find` に変更します。 (Visual Studio 2017 バージョン 15.6 では、Clang/LLVM のみがサポートされました。 バージョン 15.7 Preview 2 では、ClXX についてもサポートはほぼ完全です。)

## <a name="improvements_159"></a> 15.9 の準拠の強化

### <a name="left-to-right-evaluation-order-for-operators-----and-"></a>演算子 `->*`、`[]`、`>>`、`<<` での左から右の評価順序

C++ 17 以降、演算子`->*`、`[]`、`>>`、`<<` のオペランドは必ず左から右の順序で評価されます。 コンパイラでこの順序を保証できないケースが 2 つあります。

- オペランド式の 1 つが値渡しされるオブジェクトであるか、値渡しされるオブジェクトを含んでいる場合、または

- **/clr** を使ってコンパイルされ、かつオペランドの 1 つがオブジェクトのフィールドか配列要素である場合。

コンパイラで左から右の評価を保証できない場合、警告 [C4866](https://docs.microsoft.com/cpp/error-messages/compiler-warnings/c4866?view=vs-2017) が生成されます。 これらの演算子に対する左から右の順序の要件は C++ 17 で導入されたため、コンパイラでこの警告が生成されるのは **/std:c++17** 以降を指定した場合のみです。

この警告を解決するには、まず左から右にオペランドを評価することが必要かどうかを検討します (オペランドの評価によって順序に依存した副作用が生成される場合など)。 多くの場合、オペランドが評価される順序により目に見える影響が生じることはありません。 必ず左から右の順序で評価する必要がある場合は、代わりに定数参照でオペランドを渡すことができるかどうかを検討します。 この変更により、次のコード サンプルにおける警告がなくなります。

```cpp
// C4866.cpp
// compile with: /w14866 /std:c++17

class HasCopyConstructor
{
public:
    int x;

    HasCopyConstructor(int x) : x(x) {}
    HasCopyConstructor(const HasCopyConstructor& h) : x(h.x) { }
};

int operator>>(HasCopyConstructor a, HasCopyConstructor b) { return a.x >> b.x; }

// This version of operator>> does not trigger the warning:
// int operator>>(const HasCopyConstructor& a, const HasCopyConstructor& b) { return a.x >> b.x; }

int main()
{
    HasCopyConstructor a{ 1 };
    HasCopyConstructor b{ 2 };

    a>>b;        // C4866 for call to operator>>
};
```

## <a name="update_150"></a> Visual Studio 2017 RTW (バージョン 15.0) でのバグ修正

### <a name="copy-list-initialization"></a>Copy-list-initialization

Visual Studio 2017 は、初期化子リストを使用したオブジェクト作成に関連するコンパイラ エラーを正しく発生させます。このエラーは、Visual Studio 2015 でキャッチされず、そのためにクラッシュや未定義の実行時の動作の原因になることがありました。 N4594 13.3.1.7p1 のとおり、copy-list-initialization で、コンパイラは、オーバーロードの解決のために明示的なコンストラクターを考慮する必要がありますが、その特定のオーバーロードが選択された場合にエラーを発生させる必要があります。

次の 2 つの例は、Visual Studio 2017 ではなく Visual Studio 2015 でコンパイルします。

```cpp
struct A
{
    explicit A(int) {}
    A(double) {}
};

int main()
{
    A a1 = { 1 }; // error C3445: copy-list-initialization of 'A' cannot use an explicit constructor
    const A& a2 = { 1 }; // error C2440: 'initializing': cannot convert from 'int' to 'const A &'

}
```

このエラーを修正するには、直接の初期化を使用します。

```cpp
A a1{ 1 };
const A& a2{ 1 };
```

Visual Studio 2015 では、コンパイラは、誤って copy-list-initialization を通常の copy-initialization と同じ方法で処理しました。これは、単なるオーバーロードの解決のためのコンストラクターの変換と見なされます。 次の例では、Visual Studio 2015 は、MyInt(23) を選択しましたが、Visual Studio 2017 は正しくエラーを発生させます。

```cpp
// From http://www.open-std.org/jtc1/sc22/wg21/docs/cwg_closed.html#1228
struct MyStore {
    explicit MyStore(int initialCapacity);
};

struct MyInt {
    MyInt(int i);
};

struct Printer {
    void operator()(MyStore const& s);
    void operator()(MyInt const& i);
};

void f() {
    Printer p;
    p({ 23 }); // C3066: there are multiple ways that an object of this type can be called with these arguments
}
```

この例は、前に似ていますが、別のエラーを発生させます。 Visual Studio 2015 では成功し、Visual Studio 2017 と C2668 では失敗します。

```cpp
struct A {
    explicit A(int) {}
};

struct B {
    B(int) {}
};

void f(const A&) {}
void f(const B&) {}

int main()
{
    f({ 1 }); // error C2668: 'f': ambiguous call to overloaded function
}
```

### <a name="deprecated-typedefs"></a>非推奨の typedef

Visual Studio 2017 は、クラスまたは構造体で宣言されている非推奨の typedef に関する正しい警告を発行するようになりました。 次の例では、Visual Studio 2015 では警告なしでコンパイルしますが、Visual Studio 2017 は C4996 を生成します。

```cpp
struct A
{
    // also for __declspec(deprecated)
    [[deprecated]] typedef int inttype;
};

int main()
{
    A::inttype a = 0; // C4996 'A::inttype': was declared deprecated
}
```

### <a name="constexpr"></a>**constexpr**

Visual Studio 2017 では、条件付きで評価する演算の左のオペランドが constexpr コンテキストで無効である場合、正しくエラーが発生します。 次のコードは、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではコンパイルされません (C3615 constexpr 関数 'f' の結果が定数式になることはありません)。

```cpp
template<int N>
struct array
{
    int size() const { return N; }
};

constexpr bool f(const array<1> &arr)
{
    return arr.size() == 10 || arr.size() == 11; // C3615
}
```

エラーを修正するには、`array::size()` 関数を **constexpr** として宣言するか、`f` から **constexpr** 修飾子を削除します。

### <a name="class-types-passed-to-variadic-functions"></a>可変個引数関数に渡されるクラス型

Visual Studio 2017 では、printf などの可変個引数関数に渡されるクラスまたは構造体は普通にコピー可能である必要があります。 このようなオブジェクトを渡すときには、コンパイラは単にビットごとのコピーを作成し、コンストラクターまたはデストラクターを呼び出しません。

```cpp
#include <atomic>
#include <memory>
#include <stdio.h>

int main()
{
    std::atomic<int> i(0);
    printf("%i\n", i); // error C4839: non-standard use of class 'std::atomic<int>'
                        // as an argument to a variadic function.
                        // note: the constructor and destructor will not be called;
                        // a bitwise copy of the class will be passed as the argument
                        // error C2280: 'std::atomic<int>::atomic(const std::atomic<int> &)':
                        // attempting to reference a deleted function

    struct S {
        S(int i) : i(i) {}
        S(const S& other) : i(other.i) {}
        operator int() { return i; }
    private:
        int i;
    } s(0);
    printf("%i\n", s); // warning C4840 : non-portable use of class 'main::S'
                      // as an argument to a variadic function
}
```

エラーを解決するために、普通にコピー可能な型を返すメンバー関数を呼び出すことができます。

```cpp
    std::atomic<int> i(0);
    printf("%i\n", i.load());
```

または、オブジェクトを渡す前にオブジェクトを変換するための静的キャストを実行します。

```cpp
    struct S {/* as before */} s(0);
    printf("%i\n", static_cast<int>(s))
```

CString を使用して構築および管理される文字列の場合、指定されている `operator LPCTSTR()` を使用して、書式設定文字列によって予期されている C ポインターに CString オブジェクトをキャストする必要があります。

```cpp
CString str1;
CString str2 = _T("hello!");
str1.Format(_T("%s"), static_cast<LPCTSTR>(str2));
```

### <a name="cv-qualifiers-in-class-construction"></a>クラス コンストラクションの cv 修飾子

Visual Studio 2015 では、コンストラクターを呼び出してクラス オブジェクトを生成するときに、コンパイラが誤って cv 修飾子を無視することがあります。 この問題により、クラッシュまたは予期しない実行時動作が発生する可能性があります。 次の例は、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではコンパイラ エラーが発生します。

```cpp
struct S
{
    S(int);
    operator int();
};

int i = (const S)0; // error C2440
```

このエラーを解決するには、`operator int()` を **const** として宣言します。

### <a name="access-checking-on-qualified-names-in-templates"></a>テンプレートの修飾名のアクセス確認

以前のバージョンのコンパイラでは、一部のテンプレートのコンテキストで修飾名へのアクセスが確認されませんでした。 この問題により、名前にアクセスできないために置換が失敗すると予想される場合に、予期される SFINAE の動作に干渉する可能性があります。 コンパイラが演算子の誤ったオーバーロードを誤って呼び出すために、これが原因でクラッシュまたは実行時に予期しない動作が発生する可能性があります。 Visual Studio 2017 年では、コンパイラ エラーが発生します。 特定のエラーは異なる場合がありますが、通常は、"C2672: 一致するオーバーロードされた関数が見つかりませんでした。" が表示されます。 次のコードは、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではエラーが発生します。

```cpp
#include <type_traits>

template <class T> class S {
    typedef typename T type;
};

template <class T, std::enable_if<std::is_integral<typename S<T>::type>::value, T> * = 0>
bool f(T x);

int main()
{
    f(10); // C2672: No matching overloaded function found.
}
```

### <a name="missing-template-argument-lists"></a>見つからないテンプレート引数リスト

Visual Studio 2015 以前では、テンプレートがテンプレート パラメーター リストに (たとえば、既定のテンプレート引数または非型テンプレート パラメーターの一部として) 表示されるときに、見つからないテンプレート引数リストの診断が行われませんでした。 この問題により、コンパイラのクラッシュや実行時の予期しない動作などの予期しない動作が発生する可能性があります。 次のコードは、Visual Studio 2015 ではコンパイルされますが、Visual Studio 2017 ではエラーが発生します。

```cpp
template <class T> class ListNode;
template <class T> using ListNodeMember = ListNode<T> T::*;
template <class T, ListNodeMember M> class ListHead; // C2955: 'ListNodeMember': use of alias
                                                     // template requires template argument list

// correct:  template <class T, ListNodeMember<T> M> class ListHead;
```

### <a name="expression-sfinae"></a>SFINAE 式

SFINAE 式をサポートするために、コンパイラでは、テンプレートがインスタンス化されるときではなく宣言されるときに、**decltype** 引数が解析されるようになりました。 その結果、decltype 引数に非依存の特殊化が見つかった場合、インスタンス化時まで遅延されません。 すぐに処理され、結果として発生したエラーは、その時点で診断されます。

次の例は、宣言時に発生するこのようなコンパイラ エラーを示しています。

```cpp
#include <utility>
template <class T, class ReturnT, class... ArgsT>
class IsCallable
{
public:
    struct BadType {};

    template <class U>
    static decltype(std::declval<T>()(std::declval<ArgsT>()...)) Test(int); //C2064. Should be declval<U>

    template <class U>
    static BadType Test(...);

    static constexpr bool value = std::is_convertible<decltype(Test<T>(0)), ReturnT>::value;
};

constexpr bool test1 = IsCallable<int(), int>::value;
static_assert(test1, "PASS1");
constexpr bool test2 = !IsCallable<int*, int>::value;
static_assert(test2, "PASS2");
```

### <a name="classes-declared-in-anonymous-namespaces"></a>匿名の名前空間で宣言されたクラス

C++ 標準によると、匿名の名前空間内で宣言されたクラスは内部リンケージがあるため、エクスポートすることができません。 Visual Studio 2015 以前のバージョンでは、この規則は適用されませんでした。 Visual Studio 2017 では、この規則は部分的に適用されます。 次の例は、Visual Studio 2017 で発生したエラーを表します: "エラー C2201: const anonymous namespace::S1::vftable:ブロック内に関数の宣言がありますが、extern を宣言していません。"

```cpp
struct __declspec(dllexport) S1 { virtual void f() {} }; //C2201
```

### <a name="default-initializers-for-value-class-members-ccli"></a>値クラス メンバー (C++/CLI) の既定の初期化子

Visual Studio 2015 以前では、コンパイラは、値クラスのメンバーの既定のメンバーの初期化子を許可しました (ただし無視しました)。 値クラスの既定の初期化子は、常にメンバーを 0 に初期化します。 既定のコンストラクターは許可されません。 Visual Studio 2017 年では、この例に示すように、既定メンバー初期化子は、コンパイラ エラーを発生させます。

```cpp
value struct V
{
    int i = 0; // error C3446: 'V::i': a default member initializer
               // isn't allowed for a member of a value class
};
```

### <a name="default-indexers-ccli"></a>既定のインデクサー (C++/CLI)

Visual Studio 2015 以前では、場合によっては、コンパイラは、既定のプロパティを誤って既定のインデクサーとして識別します。 識別子 **default** を使用してプロパティにアクセスすることで、この問題を回避できました。 C++11 で **default** がキーワードとして導入された後は、この回避策自体が問題になりました。 Visual Studio 2017 では、この回避策を必要とするバグが修正され、クラスの既定のプロパティにアクセスするために **default** が使用された場合は、コンパイラによってエラーが発生するようになりました。

```cpp
//class1.cs

using System.Reflection;
using System.Runtime.InteropServices;

namespace ClassLibrary1
{
    [DefaultMember("Value")]
    public class Class1
    {
        public int Value
        {
            // using attribute on the return type triggers the compiler bug
            [return: MarshalAs(UnmanagedType.I4)]
            get;
        }
    }
    [DefaultMember("Value")]
    public class Class2
    {
        public int Value
        {
            get;
        }
    }
}

// code.cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value; // error
       r1->default;
       r2->Value;
       r2->default; // error
}
```

Visual Studio 2017 年では、名前を指定して両方の Value プロパティにアクセスできます。

```cpp
#using "class1.dll"

void f(ClassLibrary1::Class1 ^r1, ClassLibrary1::Class2 ^r2)
{
       r1->Value;
       r2->Value;
}
```

## <a name="update_153"></a> 15.3 のバグ修正

### <a name="calls-to-deleted-member-templates"></a>削除されたメンバー テンプレートへの呼び出し

Visual Studio の以前のバージョンでは、実行時のクラッシュの原因になる可能性がある、削除されたメンバー テンプレートの不適切な形式の呼び出しに対して、コンパイラがエラーの生成に失敗する場合がありました。 次のコードに対しては、C2280, "'int S\<int>::f\<int>(void)': 削除された関数を参照しようとしています" が生成されるようになりました。

```cpp
template<typename T>
struct S {
   template<typename U> static int f() = delete;
};

void g()
{
   decltype(S<int>::f<int>()) i; // this should fail
}
```

このエラーを解決するには、`i` を **int** として宣言します。

### <a name="pre-condition-checks-for-type-traits"></a>型の特徴に対する前提条件の確認

Visual Studio 2017 バージョン 15.3 では、型の特徴の前提条件の確認が向上し、標準にいっそう厳密に準拠するようになりました。 そのような確認の 1 つは割り当て可能に関するものです。 Visual Studio 2017 バージョン 15.3 では、次のコードに対して C2139 が生成されます。

```cpp
struct S;
enum E;

static_assert(!__is_assignable(S, S), "fail"); // C2139 in 15.3
static_assert(__is_convertible_to(E, E), "fail"); // C2139 in 15.3
```

### <a name="new-compiler-warning-and-runtime-checks-on-native-to-managed-marshaling"></a>コンパイラの新しい警告と、ネイティブからマネージへのマーシャリングの実行時チェック

マネージド関数からネイティブ関数を呼び出すには、マーシャリングが必要です。 CLR はマーシャリングを実行しますが、C++ のセマンティクスを理解していません。 ネイティブ オブジェクトを値で渡した場合、CLR はオブジェクトのコピー コンストラクターを呼び出すか、または `BitBlt` を使いますが、それによって実行時に未定義の動作が発生する可能性があります。

今後は、削除されたコピー コンストラクターを含むネイティブ オブジェクトがネイティブとマネージドの境界を越えて値で渡されることをコンパイル時に認識すると、コンパイラは警告を生成します。 コンパイル時に認識できない場合のためには、実行時チェックが挿入されて、不適切な形式のマーシャリングが発生すると直ちにプログラムが `std::terminate` を呼び出せるようにします。 Visual Studio 2017 バージョン 15.3 では、次のようなコードを実行すると、警告 C4606 "'A': ネイティブとマネージドの境界を越えて値渡しで引数を渡すには、有効なコピー コンストラクターが必要です。 それがない場合、ランタイムの動作は定義されていません" が発生します。

```cpp
class A
{
public:
   A() : p_(new int) {}
   ~A() { delete p_; }

   A(A const &) = delete;
   A(A &&rhs) {
   p_ = rhs.p_;
}

private:
   int *p_;
};

#pragma unmanaged

void f(A a)
{
}

#pragma managed

int main()
{
    f(A()); // This call from managed to native requires marshaling. The CLR doesn't understand C++ and uses BitBlt, which results in a double-free later.
}
```

このエラーを解決するには、`#pragma managed` ディレクティブを削除し、呼び出し元をネイティブとしてマークして、マーシャリングを回避します。

### <a name="experimental-api-warning-for-winrt"></a>WinRT に対する実験用 API の警告

実験とフィードバックのためにリリースされている WinRT API は、`Windows.Foundation.Metadata.ExperimentalAttribute` で修飾されます。 Visual Studio 2017 バージョン 15.3 のコンパイラは、この属性を検出すると警告 C4698 を生成します。 以前のバージョンの Windows SDK に含まれる一部の API は、この属性で既に修飾されており、これらの API を呼び出すとこのコンパイラ警告がトリガーされるようになりました。 新しい Windows SDK では、付属するすべての型からこの属性が削除されていますが、古い SDK を使っている場合は、付属する型のすべての呼び出しでこの警告を抑制する必要があります。

次のようなコードを実行すると、警告 C4698: "'Windows::Storage::IApplicationDataStatics2::GetForUserAsync' は、評価の目的でのみ提供されています。将来の更新で変更または削除されることがあります" が発生します。

```cpp
Windows::Storage::IApplicationDataStatics2::GetForUserAsync(); //C4698
```

警告を無効にするには、#pragma を追加します。

```cpp
#pragma warning(push)
#pragma warning(disable:4698)

Windows::Storage::IApplicationDataStatics2::GetForUserAsync();

#pragma warning(pop)
```

### <a name="out-of-line-definition-of-a-template-member-function"></a>テンプレート メンバー関数のアウトオブライン定義

Visual Studio 2017 バージョン 15.3 では、クラスで宣言されていないテンプレート メンバー関数のアウトオブライン定義を検出すると、エラーが生成されます。 次のようなコードに対しては、エラー C2039: "'f': 'S' のメンバーではありません" が発生します。

```cpp
struct S {};

template <typename T>
void S::f(T t) {} //C2039: 'f': is not a member of 'S'
```

このエラーを解決するには、次の宣言をクラスに追加します。

```cpp
struct S {
    template <typename T>
    void f(T t);
};
template <typename T>
void S::f(T t) {}
```

### <a name="attempting-to-take-the-address-of-this-pointer"></a>**this** ポインターのアドレスを取得する試み

C++ では、**this** は X へのポインター型の prvalue です。**this** のアドレスを取得すること、または左辺値参照にバインドすることはできません。 前のバージョンの Visual Studio では、キャストを使用することにより、この制限を回避できました。 Visual Studio 2017 バージョン 15.3 では、コンパイラはエラー C2664 を生成します。

### <a name="conversion-to-an-inaccessible-base-class"></a>アクセスできない基底クラスへの変換

Visual Studio 2017 バージョン 15.3 では、アクセスできない基底クラスに型を変換しようとすると、エラーになります。 コンパイラによって "エラー C2243: 'type cast': 'D *' から 'B *' の変換は存在しますが、アクセスできません" が生成されます。 次のコードは形式が不適切であり、実行時にクラッシュが発生する可能性があります。 コンパイラは、このようなコードを検出すると、C2243 を生成するようになりました。

```cpp
#include <memory>

class B { };
class D : B { }; // C2243. should be public B { };

void f()
{
   std::unique_ptr<B>(new D());
}
```

### <a name="default-arguments-arent-allowed-on-out-of-line-definitions-of-member-functions"></a>メンバー関数のアウトオブライン定義で既定の引数が許可されない

テンプレート クラスのメンバー関数のアウトオブライン定義では、既定の引数が許可されません。 コンパイラは **/permissive** では警告を発し、[/permissive-](../build/reference/permissive-standards-conformance.md) ではハード エラーを発します。

Visual Studio の以前のバージョンでは、形式が間違っている次のコードでランタイム クラッシュが発生する可能性がありました。 Visual Studio 2017 バージョン 15.3 では次の警告 C5034 が発生します。'A\<T>::f': クラス テンプレートのメンバーのアウトオブライン定義において既定の引数を使用することはできません。

```cpp
template <typename T>
struct A {
    T f(T t, bool b = false);
};

template <typename T>
T A<T>::f(T t, bool b = false) // C5034
{
    // ...
}
```

このエラーを解決するには、既定の引数 `= false` を削除します。

### <a name="use-of-offsetof-with-compound-member-designator"></a>複合メンバー指定子での `offsetof` の使用

Visual Studio 2017 バージョン 15.3 では、*m* が "複合メンバー指定子" である `offsetof(T, m)` を使用して、 **/Wall** オプションを指定してコンパイルすると、警告が発生します。 次のコードは形式が不適切であり、実行時にクラッシュが発生する可能性があります。 Visual Studio 2017 バージョン 15.3 では、"警告 C4841: 非標準の拡張機能が使用されています:複合メンバー指定子が offsetof で使用されています" が生成されます。

```cpp
struct A {
   int arr[10];
};

// warning C4841: non-standard extension used: compound member designator in offsetof
constexpr auto off = offsetof(A, arr[2]);
```

コードを修正するには、プラグマで警告を無効にするか、`offsetof` を使わないようにコードを変更します。

```cpp
#pragma warning(push)
#pragma warning(disable: 4841)
constexpr auto off = offsetof(A, arr[2]);
#pragma warning(pop)
```

### <a name="using-offsetof-with-static-data-member-or-member-function"></a>静的なデータ メンバーまたはメンバー関数での `offsetof` の使用

Visual Studio 2017 バージョン 15.3 では、*m* が静的なデータ メンバーまたはメンバー関数である `offsetof(T, m)` を使うと、エラーになります。 以下のコードでは、"error C4597: undefined behavior: offsetof applied to member function 'example'" (エラー C4597: 定義されていない動作: offsetof がメンバー関数 'example' に適用されています) および "error C4597: undefined behavior: offsetof applied to static data member 'sample'" (エラー C4597: 定義されていない動作: offsetof が静的データ メンバー 'sample' に適用されています) が発生します。

```cpp
#include <cstddef>

struct A {
   int ten() { return 10; }
   static constexpr int two = 2;
};

constexpr auto off = offsetof(A, ten);
constexpr auto off2 = offsetof(A, two);
```

このコードは形式が不適切であり、実行時にクラッシュが発生する可能性があります。 このエラーを解決するには、定義されていない動作を呼び出さないようにコードを変更します。 これは、C++ 標準で許可されていない移植性のないコードです。

### <a name="declspec"></a>`__declspec` 属性についての新しい警告

Visual Studio 2017 バージョン 15.3 では、`extern "C"` リンケージ指定の前に `__declspec(...)` を適用した場合、コンパイラは属性を無視しないようになりました。 以前のコンパイラは属性を無視し、実行時に影響する可能性がありました。 **/Wall** と **/WX** オプションが設定されている場合、次のコードでは、"warning C4768: リンケージ指定子の前の __declspec 属性は無視されます" が発生します。

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

この警告を解決するには、`extern "C"` を先頭に配置します。

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

15.3 では既定でこの警告はオフになっており (15.5 では既定でオン)、 **/Wall** **/WX** を指定してコンパイルされたコードにのみ影響します。

### <a name="decltype-and-calls-to-deleted-destructors"></a>**decltype** と削除されたデストラクターの呼び出し

以前のバージョンの Visual Studio では、**decltype** と関連付けられた式での削除されたデストラクターの呼び出しが、コンパイラにより検出されませんでした。 Visual Studio 2017 バージョン 15.3 では、次のコードに対して "エラー C2280: 'A\<T>::~A(void)': 削除された関数を参照しようとしています" が発生します。

```cpp
template<typename T>
struct A
{
   ~A() = delete;
};

template<typename T>
auto f() -> A<T>;

template<typename T>
auto g(T) -> decltype((f<T>()));

void h()
{
   g(42);
}
```

### <a name="uninitialized-const-variables"></a>初期化されていない const 変数

Visual Studio 2017 RTW リリースには、**const** 変数が初期化されていないと C++ コンパイラにより診断が生成されないという回帰がありました。 この回帰は、Visual Studio 2017 バージョン 15.3 で修正されました。 次のコードに対しては、"警告 C4132: 'Value': const オブジェクトは初期化しなければなりません" が発生するようになりました。

```cpp
const int Value; //C4132
```

このエラーを解決するに、`Value` に値を割り当てます。

### <a name="empty-declarations"></a>空の宣言

Visual Studio 2017 バージョン 15.3 では、組み込み型だけでなくすべての型で、空の宣言が警告されるようになりました。 次のコードでは、4 つの宣言すべてに対し、レベル 2 の警告 C4091 が生成されます。

```cpp
struct A {};
template <typename> struct B {};
enum C { c1, c2, c3 };

int;    // warning C4091 : '' : ignored on left of 'int' when no variable is declared
A;      // warning C4091 : '' : ignored on left of 'main::A' when no variable is declared
B<int>; // warning C4091 : '' : ignored on left of 'B<int>' when no variable is declared
C;      // warning C4091 : '' : ignored on left of 'C' when no variable is declared
```

警告を解決するには、空の宣言をコメントにするか、削除します。 名前のないオブジェクトが副作用 (RAII など) を意図したものである場合、名前を指定する必要があります。

警告は、 **/Wv:18** では除外され、警告レベル W2 では既定で有効になります。

### <a name="stdis_convertible-for-array-types"></a>配列型の `std::is_convertible`

以前のバージョンのコンパイラでは、配列型の [std::is_convertible](../standard-library/is-convertible-class.md) で正しい結果が得られませんでした。 そのため、ライブラリの作成者は `std::is_convertible<...>` 型の特徴を使用する場合に、Microsoft C++ コンパイラを特例処理する必要がありました。 次の例では、静的アサートは以前のバージョンの Visual Studio では成功しますが、Visual Studio 2017 バージョン 15.3 では失敗します。

```cpp
#include <type_traits>

using Array = char[1];

static_assert(std::is_convertible<Array, Array>::value);
static_assert(std::is_convertible<const Array, const Array>::value, "");
static_assert(std::is_convertible<Array&, Array>::value, "");
static_assert(std::is_convertible<Array, Array&>::value, "");
```

`std::is_convertible<From, To>` は、以下のように、虚数関数定義の形式が適切であるかどうかを確認して計算されます。

```cpp
   To test() { return std::declval<From>(); }
```

### <a name="private-destructors-and-stdis_constructible"></a>プライベート デストラクターと `std::is_constructible`

以前のバージョンのコンパイラでは、[std::is_constructible](../standard-library/is-constructible-class.md) の結果の判定時にデストラクターがプライベートかどうかは無視されていました。 ここではこれについて考えます。 次の例では、静的アサートは以前のバージョンの Visual Studio では成功しますが、Visual Studio 2017 バージョン 15.3 では失敗します。

```cpp
#include <type_traits>

class PrivateDtor {
   PrivateDtor(int) { }
private:
   ~PrivateDtor() { }
};

// This assertion used to succeed. It now correctly fails.
static_assert(std::is_constructible<PrivateDtor, int>::value);
```

プライベート デストラクターの場合、型が構成不可となります。 `std::is_constructible<T, Args...>` は、以下の宣言が書き込まれているかのように計算されます。

```cpp
   T obj(std::declval<Args>()...)
```

この呼び出しはデストラクターの呼び出しを意味します。

### <a name="c2668-ambiguous-overload-resolution"></a>C2668: あいまいなオーバーロードの解決

以前のバージョンのコンパイラでは、宣言と引数依存の参照の両方を使用して、複数の候補が見つかったときに、あいまいさを検出できない場合がありました。 この問題により、誤ったオーバーロードが選択され、ランタイムが予期しない動作になることがあります。 次の例では、Visual Studio 2017 バージョン 15.3 で適切に "C2668 'f': オーバーロードされた関数への呼び出しがあいまいです" と示されます。

```cpp
namespace N {
   template<class T>
   void f(T&, T&);

   template<class T>
   void f();
}

template<class T>
void f(T&, T&);

struct S {};
void f()
{
   using N::f;

   S s1, s2;
   f(s1, s2); // C2668
}
```

このコードを修正するには、`::f()` の呼び出しを意図していた場合は using `N::f` ステートメントを削除します。

### <a name="c2660-local-function-declarations-and-argument-dependent-lookup"></a>C2660: ローカル関数宣言と引数依存の参照

ローカル関数宣言では、外側のスコープ内の関数が非表示になり、引数依存の参照が無効になります。 ただし、以前のバージョンのコンパイラでは引数依存の参照が実行され、誤ったオーバーロードが選択されて、ランタイムが予期しない動作になる可能性がありました。 通常、このエラーは、ローカル関数宣言のシグネチャが正しくないことが原因で発生します。 次の例では、Visual Studio 2017 バージョン 15.3 で "C2660 'f': 関数に 2 個の引数を指定できません" というエラーが正しく発生します。

```cpp
struct S {};
void f(S, int);

void g()
{
   void f(S); // C2660 'f': function does not take 2 arguments:
   // or void f(S, int);
   S s;
   f(s, 0);
}
```

問題を修正するには、`f(S)` シグネチャを変更するか、削除します。

### <a name="c5038-order-of-initialization-in-initializer-lists"></a>C5038: 初期化子リストの初期化の順序

クラス メンバーは、初期化子リストに表示される順序ではなく、宣言される順序で初期化されます。 以前のバージョンのコンパイラでは、初期化子リストの順序が宣言の順序と異なる場合に警告されませんでした。 この問題により、あるメンバーの初期化が、既に初期化されている、リスト内の別のメンバーに依存していた場合に、ランタイム動作が未定義になることがありました。 次の例では、Visual Studio 2017 バージョン 15.3 ( **/Wall** を使用) は、"警告 C5038: データ メンバー 'A::x' の後にデータ メンバー 'A::y' が初期化されます" という警告を出します。

```cpp
struct A
{
    A(int a) : y(a), x(y) {} // Initialized in reverse, y reused
    int x;
    int y;
};
```

この問題を解決するには、宣言と同じ順序になるように初期化子リストを整列します。 初期化子のいずれかまたは両方で基底クラス メンバーが参照される場合に同様の警告が発生します。

警告は既定ではオフになっており、 **/Wall** でコンパイルされたコードにのみ影響します。

## <a name="update_155"></a> 15.5 のバグ修正とその他の動作の変更

### <a name="partial-ordering-change"></a>部分的な順序の変更

コンパイラは次のコードを正しく拒否し、正しいエラー メッセージを表示するようになりました。

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(const T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);    // C2668
}
```

```Output
t161.cpp
t161.cpp(16): error C2668: 'f': ambiguous call to overloaded function
t161.cpp(8): note: could be 'int f<int*>(const T &)'
        with
        [
            T=int*
        ]
t161.cpp(2): note: or       'int f<int>(int*)'
t161.cpp(16): note: while trying to match the argument list '(int*)'
```

上記の例での問題は型の 2 つの違い (定数と否定数およびパックと非パック) があることです。 コンパイラ エラーを回避するには、相違点の 1 つを削除します。 これにより、コンパイラが関数を明確に順序付けることができます。

```cpp
template<typename... T>
int f(T* ...)
{
    return 1;
}

template<typename T>
int f(T&)
{
    return 2;
}

int main()
{
    int i = 0;
    f(&i);
}
```

### <a name="exception-handlers"></a>例外ハンドラー

配列または関数型への参照のハンドラーは、どの例外オブジェクトとも一致することはできません。 コンパイラは、このルールを正しく優先し、レベル 4 の警告を発生させるようになりました。 **/Zc:strictStrings** を使用するときに `char*` または `wchar_t*` のハンドラーを文字列リテラルと一致させることもできなくなりました。

```cpp
int main()
{
    try {
        throw "";
    }
    catch (int (&)[1]) {} // C4843 (This should always be dead code.)
    catch (void (&)()) {} // C4843 (This should always be dead code.)
    catch (char*) {} // This should not be a match under /Zc:strictStrings
}
```

```Output
warning C4843: 'int (&)[1]': An exception handler of reference to array or function type is unreachable, use 'int*' instead
warning C4843: 'void (__cdecl &)(void)': An exception handler of reference to array or function type is unreachable, use 'void (__cdecl*)(void)' instead
```

次のコードでは、エラーが回避されます。

```cpp
catch (int (*)[1]) {}
```

### <a name="tr1"></a>非推奨となった `std::tr1` 名前空間

非標準 `std::tr1` 名前空間は、c++ 14 と c++ 17 の両方のモードで非推奨とマークされるようになりました。 Visual Studio 2017 バージョン 15.5 では、次のコードは C4996: を発生させます。

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::tr1::function<int (int, int)> f = std::plus<int>(); //C4996
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

```Output
warning C4996: 'std::tr1': warning STL4002: The non-standard std::tr1 namespace and TR1-only machinery are deprecated and will be REMOVED. You can define _SILENCE_TR1_NAMESPACE_DEPRECATION_WARNING to acknowledge that you have received this warning.
```

エラーを解決するには、`tr1` 名前空間への参照を削除します。

```cpp
#include <functional>
#include <iostream>
using namespace std;

int main() {
    std::function<int (int, int)> f = std::plus<int>();
    cout << f(3, 5) << std::endl;
    f = std::multiplies<int>();
    cout << f(3, 5) << std::endl;
}
```

### <a name="annex_d"></a>非推奨としてマークされた Annex D の標準ライブラリの機能

**/std:c++17** モード コンパイラ スイッチが設定されている場合、Annex D のほとんどすべての標準ライブラリの機能は非推奨としてマークされます。

Visual Studio 2017 バージョン 15.5 では、次のコードは C4996: を発生させます。

```cpp
#include <iterator>

class MyIter : public std::iterator<std::random_access_iterator_tag, int> {
public:
    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

```Output
warning C4996: 'std::iterator<std::random_access_iterator_tag,int,ptrdiff_t,_Ty*,_Ty &>::pointer': warning STL4015: The std::iterator class template (used as a base class to provide typedefs) is deprecated in C++17. (The <iterator> header is NOT deprecated.) The C++ standard has never required user-defined iterators to derive from std::iterator. To fix this warning, stop deriving from std::iterator and start providing publicly accessible typedefs named iterator_category, value_type, difference_type, pointer, and reference. Note that value_type is required to be non-const, even for constant iterators. You can define _SILENCE_CXX17_ITERATOR_BASE_CLASS_DEPRECATION_WARNING or _SILENCE_ALL_CXX17_DEPRECATION_WARNINGS to acknowledge that you have received this warning.
```

エラーを解決するには、次のコードに示すように、警告テキストの指示に従います。

```cpp
#include <iterator>

class MyIter {
public:
    typedef std::random_access_iterator_tag iterator_category;
    typedef int value_type;
    typedef ptrdiff_t difference_type;
    typedef int* pointer;
    typedef int& reference;

    // ... other members ...
};

#include <type_traits>

static_assert(std::is_same<MyIter::pointer, int*>::value, "BOOM");
```

### <a name="unreferenced-local-variables"></a>参照されていないローカル変数

Visual Studio 15.5 では、次のコードに示すように、多くの場合、警告 C4189 が生成されます。

```cpp
void f() {
    char s[2] = {0}; // C4189. Either use the variable or remove it.
}
```

```Output
warning C4189: 's': local variable is initialized but not referenced
```

このエラーを解決するには、使用されていない変数を削除します。

### <a name="single-line-comments"></a>単一行コメント

Visual Studio 2017 バージョン 15.5 では、警告 C4001 と C4179 が、C コンパイラで生成されなくなりました。 以前は、それらは、 **/Za**コンパイラ スイッチでのみ生成されていました。  C99 以降、単一行のコメントが C 標準の一部になったため、警告は必要なくなりました。

```cpp
/* C only */
#pragma warning(disable:4001) //C4619
#pragma warning(disable:4179)
// single line comment
//* single line comment */
```

```Output
warning C4619: #pragma warning: there is no warning number '4001'
```

コードに下位互換性が必要ではない場合、C4001/C4179 抑制を削除して、警告を回避できます。 コードに下位互換性が必要な場合は、C4619 のみを抑制します。

```C

/* C only */

#pragma warning(disable:4619)
#pragma warning(disable:4001)
#pragma warning(disable:4179)

// single line comment
/* single line comment */
```

### <a name="__declspec-attributes-with-extern-c-linkage"></a>`extern "C"` リンケージを持つ `__declspec` 属性

Visual Studio の以前のバージョンでは、`extern "C"` リンケージの指定の前に `__declspec(...)`が適用された場合、コンパイラは `__declspec(...)` を無視しました。 この動作によりユーザーが意図しないコードが生成され、ランタイムに影響する可能性がありました。 Visual Studio バージョン 15.3 で警告が追加されましたが、既定でオフになっていました。 Visual Studio 2017 バージョン 15.5 では、警告は既定で有効になっています。

```cpp
__declspec(noinline) extern "C" HRESULT __stdcall //C4768
```

```Output
warning C4768: __declspec attributes before linkage specification are ignored
```

エラーを解決するには、__declspec 属性の前に、リンケージの指定を配置します。

```cpp
extern "C" __declspec(noinline) HRESULT __stdcall
```

この新しい警告 C4768 は、Visual Studio 2017 15.3 以前 (たとえば、バージョン 10.0.15063.0、RS2 SDK とも呼ばれます) に付属していたいくつかの Windows SDK ヘッダーで指定されます。 ただし、この警告を生成しないように以降のバージョンの Windows SDK のヘッダー (具体的には、ShlObj.h および ShlObj_core.h) が修正されました。 Windows SDK のヘッダーからこの警告が表示される場合は、次の操作を実行できます。

1. Visual Studio 2017 バージョン 15.5 リリースに付属している最新の Windows SDK に切り替えます。

1. Windows SDK のヘッダー ステートメントの #include に関する警告をオフにします。

```cpp
   #pragma warning (push)
   #pragma warning(disable:4768)
   #include <shlobj.h>
   #pragma warning (pop)
   ```

### <a name="extern_linkage"></a>Extern constexpr リンケージ

Visual Studio の以前のバージョンでは、変数が **extern** としてマークされている場合でも、コンパイラは常に **constexpr** 変数を提供しました。 Visual Studio 2017 バージョン 15.5 では、新しいコンパイラ スイッチ ( **/Zc:externConstexpr**) により、正しい標準準拠の動作が可能になります。 最終的にこの動作は既定値になります。

```cpp
extern constexpr int x = 10;
```

```Output
error LNK2005: "int const x" already defined
```

ヘッダー ファイルには、宣言された変数 **extern constexpr** が含まれている場合、重複する宣言を正しく組み合わせるために、`__declspec(selectany)` のマークを付ける必要があります。

```cpp
extern constexpr __declspec(selectany) int x = 10;
```

### <a name="typeid-cant-be-used-on-incomplete-class-type"></a>不完全なクラス型で **typeid** を使用することはできません

Visual Studio の以前のバージョンでは、コンパイラ誤って次のコードを許可し、その結果正しくない型情報になる可能性がありました。 Visual Studio 2017 バージョン 15.5 では、コンパイラは正しくエラーを生成します。

```cpp
#include <typeinfo>

struct S;

void f() { typeid(S); } //C2027 in 15.5
```

```Output
error C2027: use of undefined type 'S'
```

### <a name="stdis_convertible-target-type"></a>`std::is_convertible` のターゲットの型

`std::is_convertible` では、ターゲットの型が有効な戻り値の型になっている必要があります。 Visual Studio の以前のバージョンでは、コンパイラが誤って抽象型を許可し、そのために、正しくないオーバーロードの解決や意図しない実行時の動作につながる可能性がありました。  次のコードは、C2338 を正しく発生させるようになりました。

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D, B>::value, "fail"); // C2338 in 15.5
```

1 つの型が抽象型の場合、non-pointer-type の比較が失敗する場合があるので、エラー回避するには、`is_convertible` を使用するときにポインター型を比較する必要があります。

```cpp
#include <type_traits>

struct B { virtual ~B() = 0; };
struct D : public B { virtual ~D(); };

static_assert(std::is_convertible<D *, B *>::value, "fail");
```

### <a name="noexcept_removal"></a>動的例外指定の削除と **noexcept**

C++ 17 では、`throw()` は **noexcept** のエイリアスで、`throw(<type list>)` と `throw(...)` は削除されているので、特定の型に **noexcept** が含まれる場合があります。 この変更により、C++14 またはそれ以前に準拠したコードのソース互換性の問題が生じる可能性があります。 **/Zc:noexceptTypes-** スイッチを利用すれば、全般的に C++17 モードを使用しながら、C++14 バージョンの **noexcept** に戻すことができます。 これでソース コードを更新し、C++17 に準拠できます。すべての `throw()` コードを同時に書き直す必要がありません。

コンパイラは、C++ 17 モードの宣言で、または新しい警告 C5043 と [/permissive-](../build/reference/permissive-standards-conformance.md) を使用して、より多くの一致しない例外の指定を診断するようになりました。

次のコードは、Visual Studio 2017 バージョン 15.5 で **/std:c++17** スイッチを適用するときに、C5043 および C5040 を生成します。

```cpp
void f() throw(); // equivalent to void f() noexcept;
void f() {} // warning C5043
void g() throw(); // warning C5040

struct A {
    virtual void f() throw();
};

struct B : A {
    virtual void f() { } // error C2694
};
```

**/std:c++17** の使用中にエラーを削除するには、 **/Zc:noexceptTypes-** スイッチをコマンド ラインに追加するか、次の例のように、**noexcept** を使用するようにコードを更新します。

```cpp
void f() noexcept;
void f() noexcept { }
void g() noexcept(false);

struct A {
    virtual void f() noexcept;
};

struct B : A {
    virtual void f() noexcept { }
};
```

### <a name="inline-variables"></a>インライン変数

静的 Constexpr データ メンバーは、暗黙的にインラインになり、クラス内でその宣言がそれらの定義になるようになりました。 静的 Constexpr データ メンバーのアウトオブライン定義は、冗長であり、現在は非推奨とされます。 Visual Studio 2017 バージョン 15.5 では、 **/std:c++17**スイッチが適用される場合、次のコードは、警告 C5041 " *'size': constexpr 静的データ メンバーのアウトオブライン定義は不要で、C++17 では使用されていません*" を生成するようになりました。

```cpp
struct X {
    static constexpr int size = 3;
};
const int X::size; // C5041
```

### <a name="extern-c-__declspec-warning-c4768-now-on-by-default"></a>`extern "C" __declspec(...)` の警告 C4768 が既定でオンになる

Visual Studio 2017 バージョン 15.3 で警告が追加されましたが、既定でオフになっていました。 Visual Studio 2017 バージョン 15.5 では、警告は既定でオンになっています。 詳細については、「[New warning on \_\_declspec attributes (declspec 属性の新しい警告)](#declspec)」を参照してください。

### <a name="defaulted-functions-and-__declspecnothrow"></a>既定の関数と `__declspec(nothrow)`

コンパイラは以前、対応する base/member 関数で例外が許可されている場合、`__declspec(nothrow)` を使用した既定の関数の宣言を許可していました。 この動作は、C++ 標準に反しており、実行時に未定義の動作が発生することがあります。 標準では、例外の指定の不一致がある場合、そのような関数は削除済みとして定義する必要があります。  **/std:c++17** で、次のコードに対して、C2280 "*削除された関数を参照しようとしています" が発生します。明示的な例外の指定にその暗黙の宣言と互換性がないために、関数は暗黙的に削除されました。*

```cpp
struct A {
    A& operator=(const A& other) { // No exception specification; this function may throw.
        ...
    }
};

struct B : public A {
    __declspec(nothrow) B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1; // error C2280
}
```

このコードを修正するには、__declspec(nothrow) を既定値の関数から削除するか、`= default` を削除して、必要な例外処理と共に関数の定義を提供します。

```cpp
struct A {
    A& operator=(const A& other) {
        // ...
    }
};

struct B : public A {
    B& operator=(const B& other) = default;
};

int main()
{
    B b1, b2;
    b2 = b1;
}
```

### <a name="noexcept-and-partial-specializations"></a>**noexcept** と部分的な特殊化

型システムで **noexcept** を使用すると、特定の "呼び出し可能な" 型と一致させるための部分的な特殊化で、pointers-to-noexcept-functions の部分的な特殊化がないために、コンパイルまたはプライマリ テンプレートの選択に失敗することがあります。

このような場合は、**noexcept** 関数ポインターおよびメンバー関数への **noexcept** ポインターを処理するために、部分的な特殊化を追加する必要があります。 これらのオーバーロードは、 **/std:c++17** モードでのみ有効です。 C++ 14 との下位互換性を維持する必要があるときに、他のユーザーが使用するコードを記述している場合、`#ifdef` ディレクティブ内でこれらの新しいオーバーロードを保護する必要があります。 自己完結型のモジュールを使用している場合、`#ifdef` ガードを使用する代わりに、 **/Zc:noexceptTypes-** スイッチを使用してコンパイルすることができます。

次のコードは **/std:c++14** ではコンパイルされますが、 **/std:c++17** では、"エラー C2027: 認識できない型 'A\<T>' が使用されています" で失敗します。

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // C2027
}
```

次のコードは、コンパイラが新しい部分的な特殊化 `A<void (*)() noexcept>` を選択するので、 **/std:c++17** で成功します。

```cpp
template <typename T> struct A;

template <>
struct A<void(*)()>
{
    static const bool value = true;
};

template <>
struct A<void(*)() noexcept>
{
    static const bool value = true;
};

template <typename T>
bool g(T t)
{
    return A<T>::value;
}

void f() noexcept {}

int main()
{
    return g(&f) ? 0 : 1; // OK
}
```

## <a name="update_157"></a> 15.7 のバグ修正とその他の動作の変更

### <a name="c17-default-argument-in-the-primary-class-template"></a>C++17:プライマリ クラス テンプレートでの既定の引数

この動作の変更は、[クラス テンプレートのテンプレート引数の推論 - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) の前提条件です。

以前、コンパイラでは、プライマリ クラス テンプレート内の既定の引数は無視されていました。

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int = 0) {} // Re-definition necessary
```

Visual Studio 2017 バージョン 15.7 の **/std:c++17** モードでは、既定の引数は無視されません。

```cpp
template<typename T>
struct S {
    void f(int = 0);
};

template<typename T>
void S<T>::f(int) {} // Default argument is used
```

### <a name="dependent-name-resolution"></a>依存名の解決

この動作の変更は、[クラス テンプレートのテンプレート引数の推論 - P0091R3](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html) の前提条件です。

次の例では、Visual Studio 15.6 以前のコンパイラが、プライマリ クラス テンプレート内で `D::type` を `B<T>::type` に変換しています。

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = B<T*>::type;
};
```

Visual Studio 2017 バージョン 15.7 の **/std:c++17** モードでは、D の **using** ステートメントにキーワード **typename** が必要です。**typename** がないと、コンパイラで警告 C4346: *'B<T\*>::type': 依存名は型ではありません*、およびエラー C2061: *構文エラー: 識別子 'type'* が発生します。

```cpp
template<typename T>
struct B {
    using type = T;
};

template<typename T>
struct D : B<T*> {
    using type = typename B<T*>::type;
};
```

### <a name="c17-nodiscard-attribute---warning-level-increase"></a>C++ 17 `[[nodiscard]]` 属性 - 警告レベルの引き上げ

**/std:c++17** モードの Visual Studio 2017 バージョン 15.7 では、C4834 (" 'nodiscard' 属性を持つ関数の戻り値が破棄される") の警告レベルが W3 から W1 に引き上げられます。 **void** へのキャストによって、または **/wd:4834** をコンパイラに渡すことにより、警告を無効にすることができます。

```cpp
[[nodiscard]] int f() { return 0; }

int main() {
    f(); // warning: discarding return value
         // of function with 'nodiscard'
}
```

### <a name="variadic-template-constructor-base-class-initialization-list"></a>可変個引数テンプレート コンストラクター ベース クラス初期化リスト

Visual Studio の以前のエディションでは、テンプレート引数のない可変個引数テンプレート コンストラクター ベース クラス初期化リストが誤ってエラーなしで許可されていました。 Visual Studio 2017 バージョン 15.7 では、コンパイラ エラーが発生します。

Visual Studio 2017 バージョン 15.7 の次のコード例では、*エラー C2614: D\<int>: イニシャライズ リスト内の 'B' が基底クラスでもメンバーでもありません* が発生します

```cpp
template<typename T>
struct B {};

template<typename T>
struct D : B<T>
{

    template<typename ...C>
    D() : B() {} // C2614. Missing template arguments to B.
};

D<int> d;
```

このエラーを解決するには、B() 式を B\<T>() に変更します。

### <a name="constexpr-aggregate-initialization"></a>**constexpr** の集約の初期化

C++ コンパイラの以前のバージョンでは、**constexpr** の集約の初期化を正しく処理することができませんでした。集約初期化リストの要素が多すぎる無効なコードが受け入れられ、不適切な codegen が生成されていました。 次にそのようなコードの例を示します。

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {
        { 1, 2 },
        { 3, 4 }
    };
    return 0;
}
```

Visual Studio 2017 バージョン 15.7 Update 3 以降では、前の例に対して "*C2078 初期化子の数が多すぎます*" が生成されます。 次に、コードを修正する方法の例を示します。 入れ子になった中かっこの初期化リストを使用して `std::array` を初期化する場合、内側の配列に独自の中かっこのリストを指定します。

```cpp
#include <array>
struct X {
    unsigned short a;
    unsigned char b;
};

int main() {
    constexpr std::array<X, 2> xs = {{ // note double braces
        { 1, 2 },
        { 3, 4 }
    }}; // note double braces
    return 0;
}
```

## <a name="update_158"></a> 15.8 のバグ修正と動作の変更

Visual Studio 2017 バージョン 15.8 のコンパイラの変更は、すべてバグの修正と動作の変更のカテゴリに分類されています。変更点の一覧を次に示します。

###<a name="typename-on-unqualified-identifiers"></a>非限定識別子の **typename**

[/permissive-](../build/reference/permissive-standards-conformance.md) モードでは、エイリアス テンプレート定義の非限定識別子に使用される疑似の **typename** キーワードがコンパイラで受け入れられなくなりました。 次のコードでは C7511 *'T': 'typename' keyword must be followed by a qualified name\('T': 'typename' キーワードの後に修飾名が続く必要があります\)* が生成されます:

```cpp
template <typename T>
using  X = typename T;
```

このエラーを解決するには、2 行目を `using  X = T;` に変更します。

### <a name="__declspec-on-right-side-of-alias-template-definitions"></a>エイリアス テンプレート定義の右側の `__declspec()`

[__declspec](../cpp/declspec.md) はエイリアス テンプレート定義の右側で使用できなくなりました。 これは以前はコンパイラによって受け入れられても完全に無視されていたため、エイリアスが使用されたときに非推奨化の警告が発生することはありませんでした。

標準の C++ 属性 [\[\[deprecated\]\]](../cpp/attributes.md) を代わりに使用できますが、適用されるのは Visual Studio 2017 バージョン 15.6 以降です。 次のコードでは C2760 *syntax error: unexpected token '__declspec', expected 'type specifier'\(構文エラー: 予期しないトークン '__declspec'、予期 'type specifier'\)* が生成されます。

```cpp
template <typename T>
using X = __declspec(deprecated("msg")) T;
```

このエラーを解決するには、コードを次のように変更します (属性はエイリアス定義の '=' の前に置く)。

```cpp
template <typename T>
using  X [[deprecated("msg")]] = T;
```

### <a name="two-phase-name-lookup-diagnostics"></a>2 フェーズの名前参照の診断

2 フェーズの名前参照では、テンプレートの本文で使用される非依存名が定義時にテンプレートに表示されている必要があります。 以前の Microsoft C++ コンパイラでは、インスタンス化されるまで、見つからない名前は参照対象外のままになっていました。 現在は、非依存名がテンプレートの本文にバインドされている必要があります。

これにより、マニフェストで依存する基底クラスを参照できるようになります。 以前は、すべての型が解決されている場合、依存する基底クラスで定義されている名前をコンパイラで使用することが許可されていました。これは、そのような名前がインスタンス化のときに参照されるためです。 現在は、そのようなコードはエラーとして扱われます。 このような場合、変数を基底クラス型で修飾するか、`this->` ポインターを使用するなどして依存させることで、インスタンス化のときに変数が参照されるように強制できます。

[/permissive-](../build/reference/permissive-standards-conformance.md) モードでは、次のコードによって C3861: *'base_value': 識別子が見つかりませんでした*が発生します。

```cpp
template <class T>
struct Base {
    int base_value = 42;
};

template <class T>
struct S : Base<T> {
    int f() {
        return base_value;
    }
};
```

このエラーを解決するには、`return` ステートメントを `return this->base_value;` に変更します。

**注:** Boost python ライブラリの [unwind_type.hpp](https://github.com/boostorg/python/blame/develop/include/boost/python/detail/unwind_type.hpp) には、テンプレートの事前宣言のための MSVC 固有の回避策が長い間存在していました。 Visual Studio 2017 バージョン 15.8 以降の [/permissive-](../build/reference/permissive-standards-conformance.md) モード (_MSC_VER=1915) では、MSVC コンパイラは、他のコンパイラとの一貫性を保ち、引数依存の名前検索 (ADL) を正しく実行します。これにより、この回避策のガードが不要になります。 このエラー "*C3861: 'unwind_type': 識別子が見つかりませんでした*" を回避するには、Boost のリポジトリの [PR 229](https://github.com/boostorg/python/pull/229) を参照して、ヘッダー ファイルを更新します。 [vcpkg](../build/vcpkg.md) Boost パッケージには既に修正プログラムが適用されているため、vcpkg から Boost のソースを取得するかアップグレードする場合は、修正プログラムを個別に適用する必要はありません。

### <a name="forward-declarations-and-definitions-in-namespace-std"></a>名前空間 `std` での事前宣言と定義

C++ 標準では、ユーザーが事前宣言または定義を名前空間 `std` に追加することができません。 名前空間 `std` または名前空間 `std` 内の名前空間に宣言または定義を追加すると、定義されていない動作が発生するようになりました。

Microsoft は今後どこかの時点で、一部の標準ライブラリ型を定義する場所を移動します。 この変更が行われると、名前空間 `std` に事前宣言を追加する既存のコードが破損します。 新しい警告 C4643 は、このようなソースの問題の特定に役立ちます。 この警告は **/default** モードでは有効に、既定では無効になっています。 **/Wall** または **/WX** でコンパイルされるプログラムに影響があります。

次のコードで C4643: *名前空間 std での 'vector' の事前宣言は C++ 標準では許可されていません* が発生するようになりました。

```cpp
namespace std {
    template<typename T> class vector;
}
```

このエラーを解決するには、事前宣言ではなく **include** ディレクティブを使用します。

```cpp
#include <vector>
```

### <a name="constructors-that-delegate-to-themselves"></a>それ自体にデリゲートするコンストラクター

C++ 標準では、コンストラクターがそれ自体にデリゲートするときにはコンパイラで診断を出力することを提案しています。 Microsoft C++ コンパイラの [/std:c++17](../build/reference/std-specify-language-standard-version.md) モードと [/std:c++latest](../build/reference/std-specify-language-standard-version.md) モードで、C7535: *'X::X': デリゲート コンストラクターはそのコンストラクター自体を呼び出します* が発生するようになりました。

このエラーがないと、次のプログラムでコンパイルされますが、無限ループが生成されます。

```cpp
class X {
public:
    X(int, int);
    X(int v) : X(v){}
};
```

無限ループを避けるには、別のコンストラクターにデリゲートしてください。

```cpp
class X {
public:

    X(int, int);
    X(int v) : X(v, 0) {}
};
```

### <a name="offsetof-with-constant-expressions"></a>定数式を含む `offsetof`

[offsetof](../c-runtime-library/reference/offsetof-macro.md) は従来から [reinterpret_cast](../cpp/reinterpret-cast-operator.md) を必要とするマクロを使用して実装されています。 この用法は、定数式を必要とするコンテキストでは正しくありませんが、Microsoft C++ コンパイラではこれまで許可されていました。 標準ライブラリの一部としてリリースされている `offsetof` マクロはコンパイラ組み込み型 ( **__builtin_offsetof**) が正しく使用されますが、多くのユーザーはマクロのトリックを使用して独自の `offsetof` を定義しています。

Visual Studio 2017 バージョン 15.8 では、コードが標準の C++ の動作に準拠するように、これらの `reinterpret_cast` 演算子が既定のモードで表示される領域を制約します。 [/permissive-](../build/reference/permissive-standards-conformance.md) の下では、制約がさらに厳しくなります。 定数式を必要とする場所で `offsetof` の結果を使用すると、警告 C4644 *usage of the macro-based offsetof pattern in constant expressions is non-standard; use offsetof defined in the C++ standard library instead (定数式でマクロに基づく offsetof パターンを使用することは標準ではありません。C++ 標準ライブラリで定義された offsetof を使用してください)* または C2975 *invalid template argument, expected compile-time constant expression (無効なテンプレート引数です。予期されたコンパイル時の定数式です)* を発行するコードが生成される場合があります。

次のコードにより **/default** モードと **/std:c++17** モードで C4644 が、[/permissive-](../build/reference/permissive-standards-conformance.md) モードで C2975 が発生します。

```cpp
struct Data {
    int x;
};

// Common pattern of user-defined offsetof
#define MY_OFFSET(T, m) (unsigned long long)(&(((T*)nullptr)->m))

int main()

{
    switch (0) {
    case MY_OFFSET(Data, x): return 0;
    default: return 1;
    }
}
```

このエラーを解決するには、\<cstddef> を使用して定義された `offsetof` を使用します。

```cpp
#include <cstddef>

struct Data {
    int x;
};

int main()
{
    switch (0) {
    case offsetof(Data, x): return 0;
    default: return 1;
    }
}
```

### <a name="cv-qualifiers-on-base-classes-subject-to-pack-expansion"></a>パック拡張の対象になっている基底クラスの cv 修飾子

以前のバージョンの Microsoft C++ コンパイラでは、基底クラスがパック拡張の対象でもあった場合、cv 修飾子が含まれることを検出しませんでした。

Visual Studio 2017 バージョン 15.8 の [/permissive-](../build/reference/permissive-standards-conformance.md) モードでは次のコードにより C3770 *'const S': is not a valid base class\('const S': 有効な基底クラスではありません\)* が発生します。

```cpp
template<typename... T>
class X : public T... { };

class S { };

int main()
{
    X<const S> x;
}
```

### <a name="template-keyword-and-nested-name-specifiers"></a>**template** キーワードと nested-name-specifier

[/permissive-](../build/reference/permissive-standards-conformance.md) モードでは、コンパイラが依存する nested-name-specifier の後にある場合にテンプレート名が優先されるためには、コンパイラで **template** キーワードが必要になりました。

[/permissive-](../build/reference/permissive-standards-conformance.md) モードでは次のコードにより、C7510 *'example': use of dependent template name must be prefixed with 'template'. note: see reference to class template instantiation 'X<T>' being compiled ('example': 依存するテンプレート名を使用する場合は 'template' のプレフィックスが必要です。注: コンパイルされているクラス テンプレートのインスタンス化 ’X<T>’ のリファレンスを参照してください)* が発生します。

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        Base<T>::example<int>();
    }
};
```

このエラーを解決するには、次の例で示すように、**template** キーワードを `Base<T>::example<int>();` ステートメントに追加します。

```cpp
template<typename T> struct Base
{
    template<class U> void example() {}
};

template<typename T>
struct X : Base<T>
{
    void example()
    {
        // Add template keyword here:
        Base<T>::template example<int>();
    }
};
```

## <a name="update_159"></a> 15.9 のバグ修正と動作の変更

### <a name="identifiers-in-member-alias-templates"></a>メンバーのエイリアス テンプレート内の識別子

メンバーのエイリアス テンプレート定義で使用される識別子は、使用前に宣言する必要があります。

以前のバージョンのコンパイラでは、次のコードが許可されていました。

```cpp
template <typename... Ts>
struct A
{
  public:
    template <typename U>
    using from_template_t = decltype(from_template(A<U>{}));

  private:
    template <template <typename...> typename Type, typename... Args>
    static constexpr A<Args...> from_template(A<Type<Args...>>);
};

A<>::from_template_t<A<int>> a;
```

Visual Studio 2017 バージョン 15.9 の [/permissive-](../build/reference/permissive-standards-conformance.md) モードでは、コンパイラで C3861: *'from_template': 識別子が見つかりませんでした*が発生します。

このエラーを解決するには、`from_template_t` の前に `from_template` を宣言します。

### <a name="modules-changes"></a>モジュールの変更

Visual Studio 2017 のバージョン 15.9 では、モジュールのコマンド ライン オプションがモジュールの作成側とモジュールの使用側で一貫していない場合に必ず、コンパイラで C5050 が発生します。 次の例には、2 つの問題があります。

- 使用側 (main.cpp) で、オプション **/EHsc** が指定されていません。

- C++ のバージョンは作成側が **/std:c++17**、使用側が **/std:c++14** です。

```cmd
cl /EHsc /std:c++17 m.ixx /experimental:module
cl /experimental:module /module:reference m.ifc main.cpp /std:c++14
```

このどちらの場合でも、コンパイラで次の C5050 が発生します。*警告 C5050: モジュール 'm' のインポート中に互換性のない環境が発生する可能性があります: C++ のバージョンが一致しません。Current "201402" module version "201703"\(C++ のバージョンが一致せず環境に互換性がないためモジュール 'm' をインポートできない可能性があります: 現在 "201402" モジュール バージョン "201703"\)* .

.ifc ファイルが改ざんされている場合には必ずコンパイラで C7536 が発生します。 モジュール インターフェイスのヘッダーの下には、コンテンツの SHA2 ハッシュが含まれています。 インポート時に .ifc ファイルが同じようにハッシュされ、ヘッダーに提供されたハッシュと照合されます。 これらが一致しない場合は C7536: *ifc が整合性チェックに失敗しました。SHA2: '66d5c8154df0c71d4cab7665bab4a125c7ce5cb9a401a4d8b461b706ddd771c6' が必要です* が発生します。

### <a name="partial-ordering-involving-aliases-and-non-deduced-contexts"></a>別名と非推定コンテキストが含まれる部分的な順序付け

非推定コンテキストに別名が含まれる部分的な順序付けルールには実装方法に違いがあります。 次の例では、GCC と Microsoft C++ コンパイラ ([/permissive-](../build/reference/permissive-standards-conformance.md) モード) ではエラーが発生しますが、Clang ではコードが受け入れられます。

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <class T, class Alloc>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

前述の例では、C2668 が発生します。

```Output
partial_alias.cpp(32): error C2668: 'f': ambiguous call to overloaded function
partial_alias.cpp(18): note: could be 'int f<Alloc,void>(A<void> &,const AlignedBuffer<10,4> &)'
partial_alias.cpp(12): note: or       'int f<Alloc,A<void>>(Alloc &,const AlignedBuffer<10,4> &)'
        with
        [
            Alloc=A<void>
        ]
partial_alias.cpp(32): note: while trying to match the argument list '(A<void>, AlignedBuffer<10,4>)'
```

実装方法が異なる原因は、C++ 標準の表現の回帰です。 核となる問題 2235 の解決により、これらのオーバーロードの順序付けを許可する一部のテキストが削除されました。 現在の C++ 標準ではこれらの関数を部分的に並べ替えるメカニズムを提供していないため、関数があいまいであると見なされます。

回避策として、部分的な順序付けに頼らずにこの問題を解決することをお勧めします。 または、SFINAE を使用して特定のオーバーロードを削除します。 次の例では、`Alloc` が `A` の特殊化である場合にヘルパー クラス `IsA` を使用して最初のオーバーロードを削除しています。

```cpp
#include <utility>
using size_t = std::size_t;

template <typename T>
struct A {};
template <size_t, size_t>
struct AlignedBuffer {};
template <size_t len>
using AlignedStorage = AlignedBuffer<len, 4>;

template <typename T> struct IsA : std::false_type {};
template <typename T> struct IsA<A<T>> : std::true_type {};

template <class T, class Alloc, typename = std::enable_if_t<!IsA<Alloc>::value>>
int f(Alloc &alloc, const AlignedStorage<T::size> &buffer)
{
    return 1;
}

template <class T, class Alloc>
int f(A<Alloc> &alloc, const AlignedStorage<T::size> &buffer)
{
    return 2;
}

struct Alloc
{
    static constexpr size_t size = 10;
};

int main()
{
    A<void> a;
    AlignedStorage<Alloc::size> buf;
    if (f<Alloc>(a, buf) != 2)
    {
        return 1;
    }

    return 0;
}
```

### <a name="illegal-expressions-and-non-literal-types-in-templated-function-definitions"></a>テンプレート関数定義の不正な式と非リテラルの型

不正な式と非リテラルの型が、明示的に特化されているテンプレート関数の定義で正しく診断されるようになりました。 以前は、このようなエラーは関数定義で発生しませんでした。 ただし、定数式の一部として評価される場合は、不正な式も非リテラルの型も診断されることがありました。

前のバージョンの Visual Studio では、次のコードが警告なしでコンパイルされます。

```cpp
void g();

template<typename T>
struct S
{
    constexpr void f();
};

template<>
constexpr void S<int>::f()
{
    g(); // C3615 in 15.9
}
```

Visual Studio 2017 バージョン 15.9 では、このコードは次のエラーを発生させます。

```Output
error C3615: constexpr function 'S<int>::f' cannot result in a constant expression.
note: failure was caused by call of undefined function or one not declared 'constexpr'
note: see usage of 'g'.
```

このエラーを回避するには、関数 `f()` の明示的なインスタンス化から **constexpr** 修飾子を削除します。

::: moniker-end

::: moniker range="vs-2015"

## <a name="c-conformance-improvements-in-visual-studio-2015"></a>Visual Studio 2015 の C++ 準拠の強化

Visual Studio 2015 更新プログラム 3 での準拠の機能強化の完全な一覧については、「[Visual C++ What's New 2003 through 2015](/cpp/porting/visual-cpp-what-s-new-2003-through-2015)」(Visual C++ 2003 から 2015 の新機能) を参照してください。

::: moniker-end

## <a name="see-also"></a>関連項目

[Microsoft C++ 言語の準拠表](../visual-cpp-language-conformance.md)
