---
title: directory_entry クラス
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- filesystem/std::experimental::filesystem::directory_entry::directory_entry
- filesystem/std::experimental::filesystem::directory_entry::operator=
- filesystem/std::experimental::filesystem::directory_entry::assign
- filesystem/std::experimental::filesystem::directory_entry::replace_filename
- filesystem/std::experimental::filesystem::directory_entry::path
- filesystem/std::experimental::filesystem::directory_entry::status
- filesystem/std::experimental::filesystem::directory_entry::symlink_status
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;
- filesystem/std::experimental::filesystem::directory_entry::operator==
- filesystem/std::experimental::filesystem::directory_entry::operator!=
- filesystem/std::experimental::filesystem::directory_entry::operator&lt;=
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;
- filesystem/std::experimental::filesystem::directory_entry::operator&gt;=
ms.assetid: 1827c67b-4137-4548-adb0-f955f7acaf08
helpviewer_keywords:
- std::experimental::filesystem::directory_entry
- std::experimental::filesystem::directory_entry::operator const std::experimental::filesystem::path &
- std::experimental::filesystem::directory_entry::directory_entry
- std::experimental::filesystem::directory_entry::operator=
- std::experimental::filesystem::directory_entry::assign
- std::experimental::filesystem::directory_entry::replace_filename
- std::experimental::filesystem::directory_entry::path
- std::experimental::filesystem::directory_entry::status
- std::experimental::filesystem::directory_entry::symlink_status
- std::experimental::filesystem::directory_entry::operator&lt;
- std::experimental::filesystem::directory_entry::operator==
- std::experimental::filesystem::directory_entry::operator!=
- std::experimental::filesystem::directory_entry::operator&lt;=
- std::experimental::filesystem::directory_entry::operator&gt;
- std::experimental::filesystem::directory_entry::operator&gt;=
ms.openlocfilehash: 35b0dc55bf5db2f799d9ade28cd5968ceab3332b
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458959"
---
# <a name="directory_entry-class"></a>directory_entry クラス

`*X` によって返されるオブジェクトを表します。*X* は、[directory_iterator](../standard-library/directory-iterator-class.md) または [recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) です。

## <a name="syntax"></a>構文

```cpp
class directory_entry;
```

## <a name="remarks"></a>Remarks

このクラスは、[path](../standard-library/path-class.md) 型のオブジェクトを格納します。 格納できる `path` は、[path クラス](../standard-library/path-class.md)のインスタンスまたは `path` の派生型のインスタンスです。 また、2 つの [file_type](../standard-library/filesystem-enumerations.md#file_type) 値も格納します。1 つは格納されたファイル名の状態に関する既知の情報を表し、もう 1 つはファイル名のシンボリック リンクの状態に関する既知の情報を表します。

詳細およびコード例については、「[ファイル システムのナビゲーション (C++)](../standard-library/file-system-navigation.md)」を参照してください。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[directory_entry](#directory_entry)|既定のコンストラクターは想定どおりの動作をします。 4番目の`mypath`コンストラクターは、 `mystat` *pval*、 *stat_arg*、 `mysymstat`および*symstat_arg*に初期化します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[assign](#assign)|このメンバー関数は 、pval `mypath`to 、stat `mystat`to、および*symstat*をに`mysymstat`割り当てます。|
|[path](#path)|このメンバー関数は、`mypath` を返します。|
|[replace_filename](#replace_filename)|このメンバー関数は`mypath` 、 `mypath.parent_path()`  /  *pval*、 `mysymstat` stat_arg、および symstat_arg を使用して置き換えます。 `mystat`|
|[status](#status)|どちらのメンバー関数`mystat`も、最初に変更された可能性があるものを返します。|
|[symlink_status](#symlink_status)|どちらのメンバー関数`mysymstat`も、最初に変更された可能性があるものを返します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator!=](#op_neq)|別のリストのコピーでリストの要素を置き換えます。|
|[operator=](#op_as)|この既定のメンバー代入演算子は想定どおりに動作します。|
|[operator==](#op_eq)|`mypath == right.mypath` を返します。|
|[operator<](#op_lt)|`mypath < right.mypath` を返します。|
|[operator<=](#op_lteq)|`!(right < *this)` を返します。|
|[operator>](#op_gt)|`right < *this` を返します。|
|[operator>=](#op_gteq)|`!(*this < right)` を返します。|
|[operator const path_type &](#path_type)|`mypath` を返します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<試験的/ファイルシステム&gt;

**名前空間:** std::experimental::filesystem

## <a name="assign"></a>割り当てる

このメンバー関数は 、pval `mypath`to 、stat_arg `mystat`to、および symstat_arg `mysymstat`をに割り当てます。

```cpp
void assign(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>パラメーター

*pval*\
格納されているファイル名のパス。

*stat_arg*\
格納されているファイル名の状態。

*symstat_arg*\
格納されているファイル名のシンボリックリンクの状態。

## <a name="directory_entry"></a>directory_entry

既定のコンストラクターは想定どおりの動作をします。 4番目の`mypath`コンストラクターは、 `mystat` *pval*、 *stat_arg*、 `mysymstat`および*symstat_arg*に初期化します。

```cpp
directory_entry() = default;
directory_entry(const directory_entry&) = default;
directory_entry(directory_entry&&) noexcept = default;
explicit directory_entry(const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>パラメーター

*pval*\
格納されているファイル名のパス。

*stat_arg*\
格納されているファイル名の状態。

*symstat_arg*\
格納されているファイル名のシンボリックリンクの状態。

## <a name="op_neq"></a> operator!=

このメンバー関数は、`!(*this == right)` を返します。

```cpp
bool operator!=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>パラメーター

*そうです*\
と比較する`directory_entry`[directory_entry](../standard-library/directory-entry-class.md)。

## <a name="op_as"></a>operator =

この既定のメンバー代入演算子は想定どおりに動作します。

```cpp
directory_entry& operator=(const directory_entry&) = default;
directory_entry& operator=(directory_entry&&) noexcept = default;
```

### <a name="parameters"></a>パラメーター

*そうです*\
に`directory_entry`コピーされる[directory_entry](../standard-library/directory-entry-class.md) 。

## <a name="op_eq"></a>operator = =

このメンバー関数は、`mypath == right.mypath` を返します。

```cpp
bool operator==(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>パラメーター

*そうです*\
と比較する`directory_entry`[directory_entry](../standard-library/directory-entry-class.md)。

## <a name="op_lt"></a> 演算子&lt;

このメンバー関数は、`mypath < right.mypath` を返します。

```cpp
bool operator<(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>パラメーター

*そうです*\
と比較する`directory_entry`[directory_entry](../standard-library/directory-entry-class.md)。

## <a name="op_lteq"></a>operator&lt;=

このメンバー関数は、`!(right < *this)` を返します。

```cpp
bool operator&lt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>パラメーター

*そうです*\
と比較する`directory_entry`[directory_entry](../standard-library/directory-entry-class.md)。

## <a name="op_gt"></a> 演算子&gt;

このメンバー関数は、`right < *this` を返します。

```cpp
bool operator&gt;(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>パラメーター

*そうです*\
と比較する`directory_entry`[directory_entry](../standard-library/directory-entry-class.md)。

## <a name="op_gteq"></a>operator&gt;=

このメンバー関数は、`!(*this < right)` を返します。

```cpp
bool operator&gt;=(const directory_entry& right) const noexcept;
```

### <a name="parameters"></a>パラメーター

*そうです*\
と比較する`directory_entry`[directory_entry](../standard-library/directory-entry-class.md)。

## <a name="path_type"></a>operator const path_type &

このメンバー演算子は、 `mypath`を返します。

```cpp
operator const std::experimental::filesystem::path&() const;
```

## <a name="path"></a>道

このメンバー関数は、`mypath` を返します。

```cpp
const std::experimental::filesystem::path& path() const noexcept;
```

## <a name="replace_filename"></a>replace_filename

このメンバー関数は`mypath` 、 `mypath.parent_path()`  /  *pval*、 `mysymstat` stat_arg、および symstat_arg を使用して置き換えます。 `mystat`

```cpp
void replace_filename(
    const std::experimental::filesystem::path& pval,
    file_status stat_arg = file_status(),
    file_status symstat_arg = file_status());
```

### <a name="parameters"></a>パラメーター

*pval*\
格納されているファイル名のパス。

*stat_arg*\
格納されているファイル名の状態。

*symstat_arg*\
格納されているファイル名のシンボリックリンクの状態。

## <a name="status"></a>オンライン

どちらのメンバー関数`mystat`も、最初に次のように変更される可能性があります。

1. の`status_known(mystat)`場合は、何も実行しません。

1. それ以外の`!status_known(mysymstat) && !is_symlink(mysymstat)`場合`mystat = mysymstat`は。

```cpp
file_status status() const;
file_status status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>パラメーター

*c*\
ステータスエラーコード。

## <a name="symlink_status"></a>symlink_status

どちらのメンバー関数`mysymstat`も、最初に次のように変更される可能性があります。の`status_known(mysymstat)`場合は、何も実行しません。 それ以外の場合は `mysymstat = symlink_status(mypval)`。

```cpp
file_status symlink_status() const;
file_status symlink_status(error_code& ec) const noexcept;
```

### <a name="parameters"></a>パラメーター

*c*\
ステータスエラーコード。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem&gt;](../standard-library/filesystem.md)
