---
title: path クラス
ms.date: 09/27/2018
f1_keywords:
- filesystem/std::experimental::filesystem::path
ms.assetid: 8a1227ca-aeb2-4e0e-84aa-86e34e4f4fe8
ms.openlocfilehash: 0bc26bb04464c52ed08d46e6a12c12cae6909d6f
ms.sourcegitcommit: 6ddfb8be5e5923a4d90a2c0f93f76a27ce7ac299
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/06/2019
ms.locfileid: "74898805"
---
# <a name="path-class"></a>path クラス

**Path**クラスは `string_type`型のオブジェクトを格納します。これは、パス名として使用するのに適した、exposition の目的で `myname` と呼ばれます。 `string_type` は `basic_string<value_type>`のシノニムです。 `value_type` は、Windows の場合は**wchar_t**シノニム、POSIX の場合は**char**です。

詳細およびコード例については、[ファイル システムのナビゲーション (C++)](../standard-library/file-system-navigation.md) に関する記事を参照してください。

## <a name="syntax"></a>構文

```cpp
class path;
```

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[path](#path)|`path` を構築します。|

### <a name="typedefs"></a>Typedef

|型名|説明|
|-|-|
|[const_iterator](#const_iterator)|`iterator` と同義。|
|[Iterator](#iterator)|`myname`の `path` コンポーネントを指定する双方向定数反復子。|
|[string_type](#string_type)|この型は `basic_string<value_type>`の同意語です。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[append](#append)|必要に応じて、preferred_separator を `mypath`、変換、および挿入するように、指定したシーケンスを追加します。|
|[assign](#assign)|必要に応じて変換された、`mypath` を指定したシーケンスに置き換えます。|
|[begin](#begin)|パス名の最初のパス要素 (存在する場合) を指定する `path::iterator` を返します。|
|[c_str](#c_str)|`mypath`内の最初の文字へのポインターを返します。|
|[clear](#clear)|`mypath.clear()`を実行します。|
|[compare](#compare)|比較値を返します。|
|[concat](#compare)|必要に応じて、指定したシーケンスを `mypath`に追加し、変換します (区切り記号は挿入しません)。|
|[empty](#empty)|`mypath.empty()` が返されます。|
|[end](#end)|`iterator`型のシーケンスの末尾の反復子を返します。|
|[extension](#extension)|`filename()`のサフィックスを返します。|
|[ファイル名](#filename)|myname のルート ディレクトリ コンポーネント (具体的には、 `empty() path() : *--end()`」を参照してください。 このコンポーネントは、空になることもあります。|
|[generic_string](#generic_string)|すべての円記号がスラッシュに変換された `this->string<Elem, Traits, Alloc>(al)` を返します (Windows の場合)。|
|[generic_u16string](#generic_u16string)|すべての円記号がスラッシュに変換された `u16string()` を返します (Windows の場合)。|
|[generic_u32string](#generic_u32string)|すべての円記号がスラッシュに変換された `u32string()` を返します (Windows の場合)。|
|[generic_u8string](#generic_u8string)|すべての円記号がスラッシュに変換された `u8string()` を返します (Windows の場合)。|
|[generic_wstring](#generic_wstring)|すべての円記号がスラッシュに変換された `wstring()` を返します (Windows の場合)。|
|[has_extension](#has_extension)|`!extension().empty()` が返されます。|
|[has_filename](#has_filename)|`!filename().empty()` が返されます。|
|[has_parent_path](#has_parent_path)|`!parent_path().empty()` が返されます。|
|[has_relative_path](#has_relative_path)|`!relative_path().empty()` が返されます。|
|[has_root_directory](#has_root_directory)|`!root_directory().empty()` が返されます。|
|[has_root_name](#has_root_name)|`!root_name().empty()` が返されます。|
|[has_root_path](#has_root_path)|`!root_path().empty()` が返されます。|
|[has_stem](#has_stem)|`!stem().empty()` が返されます。|
|[is_absolute](#is_absolute)|Windows の場合、関数は `has_root_name() && has_root_directory()`を返します。 POSIX の場合、関数は `has_root_directory()`を返します。|
|[is_relative](#is_relative)|`!is_absolute()` が返されます。|
|[make_preferred](#make_preferred)|各区切り記号を必要に応じて preferred_separator に変換します。|
|[native](#native)|`myname` が返されます。|
|[parent_path](#parent_path)|`myname`の親パスコンポーネントを返します。|
|[preferred_separator](#preferred_separator)|この定数オブジェクトでは、パスのコンポーネントを区切るために推奨される文字を指定します。この文字は、ホスト オペレーティング システムによって異なります。 |
|[relative_path](#relative_path)|`myname`の相対パスコンポーネントを返します。 |
|[remove_filename](#remove_filename)|ファイル名を削除します。|
|[replace_extension](#replace_extension)|`myname`の拡張機能を置き換えます。 |
|[replace_filename](#replace_filename)|ファイル名を置き換えます。|
|[root_directory](#root_directory)|`myname`のルートディレクトリコンポーネントを返します。 |
|[root_name](#root_name)|`myname`のルート名コンポーネントを返します。 |
|[root_path](#root_path)|`myname`のルートパスコンポーネントを返します。|
|[生じ](#stem)|`myname`の `stem` コンポーネントを返します。|
|[string](#string)|`mypath`に格納されているシーケンスを変換します。|
|[swap](#swap)|`swap(mypath, right.mypath)`を実行します。|
|[u16string](#u16string)|`mypath` に格納されているシーケンスを UTF-16 に変換し、`u16string`型のオブジェクトに格納して返します。|
|[u32string](#u32string)|`mypath` に格納されているシーケンスを 32 UTF-8 に変換し、`u32string`型のオブジェクトに格納されているを返します。|
|[u8string](#u8string)|`mypath` に格納されているシーケンスを UTF-8 に変換し、`u8string`型のオブジェクトに格納して返します。|
|[value_type](#value_type)|この型は、ホスト オペレーティング システムに適したパス要素を表します。|
|[wstring](#wstring)|`mypath` に格納されているシーケンスを、`wchar_t` シーケンスのホストシステムによって優先されるエンコーディングに変換し、`wstring`型のオブジェクトに格納して返します。|

### <a name="operators"></a>演算子

|[演算子]|説明|
|-|-|
|[operator=](#op_as)|パスの要素を別のパスのコピーで置き換えます。|
|[operator+=](#op_add)|さまざまな `concat` 式。|
|[operator/=](#op_divide)|さまざまな `append` 式。|
|[string_type 演算子](#op_string)|`myname` が返されます。|

## <a name="requirements"></a>要件

**ヘッダー:** \<ファイルシステム >

**名前空間:** std::experimental::filesystem

## <a name="append"></a>path:: append

必要に応じて、`preferred_separator` を `mypath`、変換、および挿入するように、指定したシーケンスを追加します。

```cpp
template <class Source>
path& append(const Source& source);

template <class InIt>
path& append(InIt first, InIt last);
```

### <a name="parameters"></a>パラメーター

*ソース*\
指定されたシーケンス。

*最初*の\
指定されたシーケンスの開始。

*最後*の\
指定されたシーケンスの最後。

## <a name="assign"></a>パス:: assign

必要に応じて変換された、`mypath` を指定したシーケンスに置き換えます。

```cpp
template <class Source>
path& assign(const Source& source);

template <class InIt>
path& assign(InIt first, InIt last);
```

### <a name="parameters"></a>パラメーター

*ソース*\
指定されたシーケンス。

*最初*の\
指定されたシーケンスの開始。

*最後*の\
指定されたシーケンスの最後。

## <a name="begin"></a>path:: begin

パス名の最初のパス要素 (存在する場合) を指定する `path::iterator` を返します。

```cpp
iterator begin() const;
```

## <a name="c_str"></a>パス:: c_str

`mypath`内の最初の文字へのポインターを返します。

```cpp
const value_type& *c_str() const noexcept;
```

## <a name="clear"></a>パス:: clear

`mypath.clear()`を実行します。

```cpp
void clear() noexcept;
```

## <a name="compare"></a>path:: compare

最初の関数は `mypath.compare(pval.native())` を返します。 2 番目の関数は `mypath.compare(str)` を返します。 3番目の関数は、`mypath.compare(ptr)`を返します。

```cpp
int compare(const path& pval) const noexcept;
int compare(const string_type& str) const;
int compare(const value_type *ptr) const;
```

### <a name="parameters"></a>パラメーター

*pval*\
比較するパス。

*str*\
比較する文字列。

*ptr*\
比較するポインター。

## <a name="concat"></a>path:: concat

必要に応じて、指定したシーケンスを `mypath`に追加し、変換します (区切り記号は挿入しません)。

```cpp
template <class Source>
path& concat(const Source& source);

template <class InIt>
path& concat(InIt first, InIt last);
```

### <a name="parameters"></a>パラメーター

*ソース*\
指定されたシーケンス。

*最初*の\
指定されたシーケンスの開始。

*最後*の\
指定されたシーケンスの最後。

## <a name="const_iterator"></a>パス:: const_iterator

`iterator` と同義。

```cpp
typedef iterator const_iterator;
```

## <a name="empty"></a>path:: empty

`mypath.empty()` が返されます。

```cpp
bool empty() const noexcept;
```

## <a name="end"></a>パス:: 終了

`iterator`型のシーケンスの末尾の反復子を返します。

```cpp
iterator end() const;
```

## <a name="extension"></a>path:: extension

`filename()`のサフィックスを返します。

```cpp
path extension() const;
```

### <a name="remarks"></a>Remarks

次のような `filename() X` のサフィックスを返します。

`X == path(".") || X == path("..")` した場合、または `X` にドットが含まれていない場合、サフィックスは空になります。

それ以外の場合、サフィックスは一番右にあるドットから始まります (このドットも含む)。

## <a name="filename"></a>パス:: ファイル名

myname のルート ディレクトリ コンポーネント (具体的には、 `empty() path() : *--end()`」を参照してください。 このコンポーネントは、空になることもあります。

```cpp
path filename() const;
```

## <a name="generic_string"></a>パス:: generic_string

すべての円記号がスラッシュに変換された `this->string<Elem, Traits, Alloc>(al)` を返します (Windows の場合)。

```cpp
template <class Elem,
    class Traits = char_traits<Elem>,
    class Alloc = allocator<Elem>>
  basic_string<Elem, Traits, Alloc>
    generic_string(const Alloc& al = Alloc()) const;

string generic_string() const;
```

## <a name="generic_u16string"></a>パス:: generic_u16string

すべての円記号がスラッシュに変換された `u16string()` を返します (Windows の場合)。

```cpp
u16string generic_u16string() const;
```

## <a name="generic_u32string"></a> path::generic_u32string

すべての円記号がスラッシュに変換された `u32string()` を返します (Windows の場合)。

```cpp
u32string generic_u32string() const;
```

## <a name="generic_u8string"></a> path::generic_u8string

すべての円記号がスラッシュに変換された `u8string()` を返します (Windows の場合)。

```cpp
string generic_u8string() const;
```

## <a name="generic_wstring"></a>パス:: generic_wstring

すべての円記号がスラッシュに変換された `wstring()` を返します (Windows の場合)。

```cpp
wstring generic_wstring() const;
```

## <a name="has_extension"></a>パス:: has_extension

`!extension().empty()` が返されます。

```cpp
bool has_extension() const;
```

## <a name="has_filename"></a>パス:: has_filename

`!filename().empty()` が返されます。

```cpp
bool has_filename() const;
```

## <a name="has_parent_path"></a>パス:: has_parent_path

`!parent_path().empty()` が返されます。

```cpp
bool has_parent_path() const;
```

## <a name="has_relative_path"></a>パス:: has_relative_path

`!relative_path().empty()` が返されます。

```cpp
bool has_relative_path() const;
```

## <a name="has_root_directory"></a>パス:: has_root_directory

`!root_directory().empty()` が返されます。

```cpp
bool has_root_directory() const;
```

## <a name="has_root_name"></a>パス:: has_root_name

`!root_name().empty()` が返されます。

```cpp
bool has_root_name() const;
```

## <a name="has_root_path"></a>パス:: has_root_path

`!root_path().empty()` が返されます。

```cpp
bool has_root_path() const;
```

## <a name="has_stem"></a>パス:: has_stem

`!stem().empty()` が返されます。

```cpp
bool has_stem() const;
```

## <a name="is_absolute"></a>パス:: is_absolute

Windows の場合、関数は `has_root_name() && has_root_directory()`を返します。 POSIX の場合、関数は `has_root_directory()`を返します。

```cpp
bool is_absolute() const;
```

## <a name="is_relative"></a>パス:: is_relative

`!is_absolute()` が返されます。

```cpp
bool is_relative() const;
```

## <a name="iterator"></a>path:: iterator

`myname`のパス要素を指定する双方向定数反復子。

```cpp
class iterator
   {
   // bidirectional iterator for path
   typedef bidirectional_iterator_tag iterator_category;
   typedef path_type value_type;
   typedef ptrdiff_t difference_type;
   typedef const value_type *pointer;
   typedef const value_type& reference;
   // ...
   };
```

### <a name="remarks"></a>Remarks

このクラスは、シーケンス内の `myname` の `path` コンポーネントを指定する双方向定数反復子を表します。

1. ルート名 (存在する場合)

1. ルート ディレクトリ (存在する場合)

1. 親 `path`の残りのディレクトリ要素 (存在する場合) は、ファイル名で終わります (存在する場合)。

`path`型のオブジェクトの `pval`:

1. `path::iterator X = pval.begin()` は、パス名の最初の `path` 要素 (存在する場合) を指定します。

1. `X == pval.end()` は、`X` がコンポーネントのシーケンスの末尾の直後を指している場合に true になります。

3. `*X` は、現在のコンポーネントと一致する文字列を返します。

1. `++X` は、シーケンス内に次のコンポーネントが存在する場合に、そのコンポーネントを指定します。

1. `--X` は、シーケンス内に前のコンポーネントが存在する場合に、そのコンポーネントを指定します。

1. `myname` を変更すると、`myname`内の要素を指定するすべての反復子が無効になります。

## <a name="make_preferred"></a>パス:: make_preferred

各区切り記号を必要に応じて `preferred_separator` に変換します。

```cpp
path& make_preferred();
```

## <a name="native"></a>パス:: native

`myname` が返されます。

```cpp
const string_type& native() const noexcept;
```

## <a name="op_as"></a>path:: operator =

パスの要素を別のパスのコピーで置き換えます。

```cpp
path& operator=(const path& right);
path& operator=(path&& right) noexcept;

template <class Source>
path& operator=(const Source& source);
```

### <a name="parameters"></a>パラメーター

*右*\
`path`にコピーされる[パス](../standard-library/path-class.md)。

*ソース*\
ソースパス。

### <a name="remarks"></a>Remarks

最初のメンバー演算子は `right.myname` を `myname`にコピーします。 2番目のメンバー演算子は、`right.myname` を `myname`に移動します。 3番目のメンバー演算子は `*this = path(source)`と同じように動作します。

## <a name="op_add"></a>path:: operator + =

さまざまな `concat` 式。

```cpp
path& operator+=(const path& right);
path& operator+=(const string_type& str);
path& operator+=(const value_type *ptr);
path& operator+=(value_type elem);

template <class Source>
path& operator+=(const Source& source);

template <class Elem>
path& operator+=(Elem elem);
```

### <a name="parameters"></a>パラメーター

*右*\
追加されたパス。

*str*\
追加された文字列。

*ptr*\
追加されたポインター。

*elem*\
追加された `value_type` または `Elem`。

*ソース*\
追加されたソース。

### <a name="remarks"></a>Remarks

このメンバー関数には、次の対応する式と同じ効果があります。

1. `concat(right);`

1. `concat(path(str));`

1. `concat(ptr);`

1. `concat(string_type(1, elem));`

1. `concat(source);`

1. `concat(path(basic_string<Elem>(1, elem)));`

## <a name="op_divide"></a>path:: operator/=

さまざまな `append` 式。

```cpp
path& operator/=(const path& right);

template <class Source>
path& operator/=(const Source& source);
```

### <a name="parameters"></a>パラメーター

*右*\
追加されたパス。

*ソース*\
追加されたソース。

### <a name="remarks"></a>Remarks

このメンバー関数には、次の対応する式と同じ効果があります。

1. `append(right);`

1. `append(source);`

## <a name="op_string"></a>path:: operator string_type

`myname` が返されます。

```cpp
operator string_type() const;
```

## <a name="parent_path"></a>パス::p arent_path

`myname`の親パスコンポーネントを返します。

```cpp
path parent_path() const;
```

### <a name="remarks"></a>Remarks

`myname`の親パスコンポーネントを返します。具体的には、`filename().native()` を削除した後の `myname` のプレフィックス、およびディレクトリの区切り記号を直前に指定したものです。 (同様に、`begin() != end()`場合、`operator/=`を連続して適用することによって `[begin(), --end())` 範囲内のすべての要素を結合します)。コンポーネントが空である可能性があります。

## <a name="path"></a>パス::p a

さまざまな方法で `path` を構築します。

```cpp
path();

path(const path& right);
path(path&& right) noexcept;

template <class Source>
path(const Source& source);

template <class Source>
path(const Source& source, const locale& loc);

template <class InIt>
path(InIt first, InIt last);

template <class InIt>
path(InIt first, InIt last, const locale& loc);
```

### <a name="parameters"></a>パラメーター

*右*\
構築されたパスがコピーされるパス。

*ソース*\
構築されたパスがコピーされるソース。

*loc*\
指定されたロケール。

*最初*の\
コピーされる最初の要素の位置。

*最後*の\
コピーされる最後の要素の位置。

### <a name="remarks"></a>Remarks

すべてのコンストラクターは、さまざまな方法で `myname` を構築します。

`path()` は `myname()`です。

`path(const path& right`) は `myname(right.myname)`です。

`path(path&& right)` は `myname(right.myname)`です。

`template<class Source> path(const Source& source)` は `myname(source)`です。

`myname(source)``template<class Source> path(const Source& source, const locale& loc)` には `loc`から必要な codecvt ファセットを取得します。

`template<class InIt> path(InIt first, InIt last)` は `myname(first, last)`です。

`myname(first, last)``template<class InIt> path(InIt first, InIt last, const locale& loc)` には `loc`から必要な codecvt ファセットを取得します。

## <a name="preferred_separator"></a>パス::p referred_separator

この定数オブジェクトでは、パスのコンポーネントを区切るために推奨される文字を指定します。この文字は、ホスト オペレーティング システムによって異なります。

```cpp
#if _WIN32_C_LIB
static constexpr value_type preferred_separator == L'\\';
#else // assume POSIX
static constexpr value_type preferred_separator == '/';
#endif // filesystem model now defined
```

### <a name="remarks"></a>Remarks

Windows では、ほとんどのコンテキストで、L'/' の代用が許容されます。

## <a name="relative_path"></a>パス:: relative_path

`myname`の相対パスコンポーネントを返します。

```cpp
path relative_path() const;
```

### <a name="remarks"></a>Remarks

`myname`の相対パスコンポーネントを返します。具体的には、`root_path().native()` を削除した後の `myname` のサフィックスと、その直後に続く余分なディレクトリ区切り記号を返します。 このコンポーネントは、空になることもあります。

## <a name="remove_filename"></a>パス:: remove_filename

ファイル名を削除します。

```cpp
path& remove_filename();
```

## <a name="replace_extension"></a>パス:: replace_extension

`myname`の拡張機能を置き換えます。

```cpp
path& replace_extension(const path& newext = path());
```

### <a name="parameters"></a>パラメーター

*newext*\
新しい拡張機能。

### <a name="remarks"></a>Remarks

最初に `myname`から `extension().native()` サフィックスを削除します。 `!newext.empty() && newext[0] != dot` (`dot` が `*path(".").c_str()`) の場合、`dot` が `myname`に追加されます。 次に、 *newext*が `myname`に追加されます。

## <a name="replace_filename"></a>パス:: replace_filename

ファイル名を置き換えます。

```cpp
path& replace_filename(const path& pval);
```

### <a name="parameters"></a>パラメーター

*pval*\
ファイル名のパス。

### <a name="remarks"></a>Remarks

このメンバー関数は、次のコードを実行します。

```cpp
remove_filename();

*this /= pval;
return (*this);
```

## <a name="root_directory"></a>パス:: root_directory

`myname`のルートディレクトリコンポーネントを返します。

```cpp
path root_directory() const;
```

### <a name="remarks"></a>Remarks

このコンポーネントは、空になることもあります。

## <a name="root_name"></a>パス:: root_name

`myname`のルート名コンポーネントを返します。

```cpp
path root_name() const;
```

### <a name="remarks"></a>Remarks

このコンポーネントは、空になることもあります。

## <a name="root_path"></a>パス:: root_path

`myname`のルートパスコンポーネントを返します。

```cpp
path root_path() const;
```

### <a name="remarks"></a>Remarks

`myname`のルートパスコンポーネントを返します。具体的には、 / `root_directory``root_name()`ます。 このコンポーネントは、空になることもあります。

## <a name="stem"></a>パス:: ステム

`myname`の `stem` コンポーネントを返します。

```cpp
path stem() const;
```

### <a name="remarks"></a>Remarks

`myname`の `stem` コンポーネントを返します。具体的には `filename().native()` 末尾の `extension().native()` 削除されます。 このコンポーネントは、空になることもあります。

## <a name="string"></a>path:: string

`mypath`に格納されているシーケンスを変換します。

```cpp
template \<class Elem, class Traits = char_traits\<Elem>, class Alloc = allocator\<Elem>>
basic_string\<Elem, Traits, Alloc> string(const Alloc& al = Alloc()) const;
string string() const;
```

### <a name="remarks"></a>Remarks

最初の (テンプレート) メンバー関数は、次のように `mypath` に格納されているシーケンスを変換します。

1. `string<char, Traits, Alloc>()` の場合 `string()`

1. `string<wchar_t, Traits, Alloc>()` の場合 `wstring()`

1. `string<char16_t, Traits, Alloc>()` の場合 `u16string()`

1. `string<char32_t, Traits, Alloc>()` の場合 `u32string()`

2番目のメンバー関数は、`mypath` に格納されているシーケンスを、 **char**シーケンスのホストシステムによって優先されるエンコーディングに変換し、`string`型のオブジェクトに格納します。

## <a name="string_type"></a>パス:: string_type

この型は `basic_string<value_type>`の同意語です。

```cpp
typedef basic_string<value_type> string_type;
```

## <a name="swap"></a>path:: swap

`swap(mypath, right.mypath)`を実行します。

```cpp
void swap(path& right) noexcept;
```

## <a name="u16string"></a>パス:: u16string

`mypath` に格納されているシーケンスを UTF-16 に変換し、`u16string`型のオブジェクトに格納して返します。

```cpp
u16string u16string() const;
```

## <a name="u32string"></a>パス:: u32string

`mypath` に格納されているシーケンスを 32 UTF-8 に変換し、`u32string`型のオブジェクトに格納されているを返します。

```cpp
u32string u32string() const;
```

## <a name="u8string"></a>パス:: u8string

`mypath` に格納されているシーケンスを UTF-8 に変換し、`u8string`型のオブジェクトに格納して返します。

```cpp
string u8string() const;
```

## <a name="value_type"></a>パス:: value_type

この型は、ホストオペレーティングシステムによって優先される `path` 要素を記述します。

```cpp
#if _WIN32_C_LIB
typedef wchar_t value_type;
#else // assume POSIX
typedef char value_type;
#endif // filesystem model now defined
```

## <a name="wstring"></a>path:: wstring

`mypath` に格納されているシーケンスを、 **wchar_t**シーケンスのホストシステムによって優先されるエンコーディングに変換し、`wstring`型のオブジェクトに格納して返します。

```cpp
wstring wstring() const;
```

## <a name="see-also"></a>参照

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
