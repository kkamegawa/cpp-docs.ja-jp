---
title: recursive_directory_iterator クラス
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::recursive_directory_iterator
ms.assetid: 79a061bd-5b64-404c-97e8-749c888c2ced
ms.openlocfilehash: a5200c030986ebbcfccb1eba2963e8317c879eb6
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686798"
---
# <a name="recursive_directory_iterator-class"></a>recursive_directory_iterator クラス

ディレクトリ内のファイル名をシーケンス処理する入力反復子を記述します。再帰的にサブディレクトリに向かって降順に並べ替えます。 反復子 `X` の場合、式 `*X` は、ファイル名をラップする `directory_entry` クラスのオブジェクトに評価され、その状態に関する既知のものがすべて表示されます。

詳細およびコード例については、「[ファイル システムのナビゲーション (C++)](../standard-library/file-system-navigation.md)」をご覧ください。

## <a name="syntax"></a>構文

```cpp
class recursive_directory_iterator;
```

## <a name="remarks"></a>Remarks

クラステンプレートには、次のものが格納されます。

1. `stack<pair<directory_iterator, path>>` 型のオブジェクト。シーケンス処理するディレクトリの入れ子を表す exposition の目的で、ここ `mystack` 呼び出されます。

1. ここ `myentry` 呼び出さ `directory_entry` 型のオブジェクト。ディレクトリシーケンス内の現在のファイル名を表します。

1. サブディレクトリへの再帰降下が無効になっているかどうかを記録する、 **bool**型のオブジェクト `no_push` ここにあります。

1. 構築時に確立されたオプションを記録する `directory_options` 型のオブジェクト。ここでは `myoptions` と呼ばれます。

@No__t_0 型の構築された既定のオブジェクトは、`mystack.top().first` でシーケンス末尾の反復子を持ち、シーケンスの末尾の反復子を表します。 たとえば、ディレクトリ `abc` `def` (ディレクトリ)、`def/ghi`、および `jkl` のエントリを指定した場合、コードは次のようになります。

```cpp
for (recursive_directory_iterator next(path("abc")), end; next != end; ++next)
    visit(next->path());
```

は、引数 `path("abc/def/ghi")` および `path("abc/jkl")` を指定して visit を呼び出します。 ディレクトリサブツリーの順序付けは、次の2つの方法で修飾できます。

1. ディレクトリシンボリックリンクは、値が `directory_options::follow_directory_symlink` の `directory_options` 引数を持つ `recursive_directory_iterator` を構築する場合にのみスキャンされます。

1. @No__t_0 を呼び出すと、インクリメント中に発生した後続のディレクトリは再帰的にスキャンされません。

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[recursive_directory_iterator](#recursive_directory_iterator)|`recursive_directory_iterator` を構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[デプス](#depth)|は `mystack.size() - 1` を返します。したがって、`pval` は深度0になります。|
|[disable_recursion_pending](#disable_recursion_pending)|@No__t_1 に**true**を格納します。|
|[許容](#increment)|は、次のファイル名に順に進みます。|
|[options](#options)|`myoptions`を返します。|
|[pop](#pop)|次のオブジェクトを返します。|
|[recursion_pending](#recursion_pending)|`!no_push`を返します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator!=](#op_neq)|`!(*this == right)`を返します。|
|[operator=](#op_as)|この既定のメンバー代入演算子は想定どおりに動作します。|
|[operator==](#op_eq)|@No__t_1 と*右辺*の両方がシーケンス末尾の反復子であるか、両方がシーケンス末尾の反復子でない場合にのみ、 **true**を返します。|
|[operator*](#op_multiply)|`myentry`を返します。|
|[operator->](#op_cast)|`&**this`を返します。|
|[operator++](#op_increment)|@No__t_0 をインクリメントします。|

## <a name="requirements"></a>［要件］

**ヘッダー:** \<filesystem >

**名前空間:** std::tr2::sys

## <a name="depth"></a>recursive_directory_iterator::d epth

は `mystack.size() - 1` を返します。したがって、`pval` は深度0になります。

```cpp
int depth() const;
```

## <a name="disable_recursion_pending"></a>recursive_directory_iterator::d isable_recursion_pending

@No__t_1 に**true**を格納します。

```cpp
void disable_recursion_pending();
```

## <a name="increment"></a>recursive_directory_iterator:: increment

は、次のファイル名に順に進みます。

```cpp
recursive_directory_iterator& increment(error_code& ec) noexcept;
```

### <a name="parameters"></a>パラメーター

*ec* \
指定されたエラーコードです。

### <a name="remarks"></a>Remarks

この関数は、ネストされたシーケンス内の次のファイル名に進もうとします。 成功した場合は、そのファイル名が `myentry` に格納されます。それ以外の場合は、シーケンス末尾の反復子を生成します。

## <a name="op_neq"></a>recursive_directory_iterator:: operator! =

`!(*this == right)`を返します。

```cpp
bool operator!=(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>パラメーター

*右*\
比較対象の[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_as"></a>recursive_directory_iterator:: operator =

この既定のメンバー代入演算子は想定どおりに動作します。

```cpp
recursive_directory_iterator& operator=(const recursive_directory_iterator&) = default;
recursive_directory_iterator& operator=(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>パラメーター

*recursive_directory_iterator* \
@No__t_1 にコピーされる[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_eq"></a>recursive_directory_iterator:: operator = =

@No__t_1 と*右辺*の両方がシーケンス末尾の反復子であるか、両方がシーケンス末尾の反復子でない場合にのみ、 **true**を返します。

```cpp
bool operator==(const recursive_directory_iterator& right) const;
```

### <a name="parameters"></a>パラメーター

*右*\
比較対象の[recursive_directory_iterator](../standard-library/recursive-directory-iterator-class.md) 。

## <a name="op_multiply"></a>recursive_directory_iterator:: operator *

`myentry`を返します。

```cpp
const directory_entry& operator*() const;
```

## <a name="op_cast"></a>recursive_directory_iterator:: operator->

`&**this`を返します。

```cpp
const directory_entry * operator->() const;
```

## <a name="op_increment"></a>recursive_directory_iterator:: operator + +

@No__t_0 をインクリメントします。

```cpp
recursive_directory_iterator& operator++();

recursive_directory_iterator& operator++(int);
```

### <a name="parameters"></a>パラメーター

*int* \
指定されたインクリメント。

### <a name="remarks"></a>Remarks

1つ目のメンバー関数は `increment()` を呼び出し、`*this` を返します。 2番目のメンバー関数は、オブジェクトのコピーを作成し、`increment()` を呼び出した後、コピーを返します。

## <a name="options"></a>recursive_directory_iterator:: options

`myoptions`を返します。

```cpp
directory_options options() const;
```

## <a name="pop"></a>recursive_directory_iterator::p op

次のオブジェクトを返します。

```cpp
void pop();
```

### <a name="remarks"></a>Remarks

オブジェクトがシーケンス末尾の反復子になる `depth() == 0` 場合は。 そうでない場合、メンバー関数は現在の (最も深い) ディレクトリのスキャンを中断し、1 つ下の深さから再開します。

## <a name="recursion_pending"></a>recursive_directory_iterator::recursion_pending

`!no_push`を返します。

```cpp
bool recursion_pending() const;
```

## <a name="recursive_directory_iterator"></a>recursive_directory_iterator::recursive_directory_iterator

`recursive_directory_iterator` を構築します。

```cpp
recursive_directory_iterator() noexcept;
explicit recursive_directory_iterator(const path& pval);

recursive_directory_iterator(const path& pval,
    error_code& ec) noexcept;
recursive_directory_iterator(const path& pval,
    directory_options opts);

recursive_directory_iterator(const path& pval,
    directory_options opts,
    error_code& ec) noexcept;
recursive_directory_iterator(const recursive_directory_iterator&) = default;
recursive_directory_iterator(recursive_directory_iterator&&) noexcept = default;
```

### <a name="parameters"></a>パラメーター

*pval* \
指定するパス。

*error_code* \
指定されたエラーコード。

*\ を*する
指定されたディレクトリオプション。

*recursive_directory_iterator* \
構築された `recursive_directory_iterator` のコピー元となる `recursive_directory_iterator`。

### <a name="remarks"></a>Remarks

1 つ目のコンストラクターは、end-of-sequence 反復子を生成します。 2番目と3番目のコンストラクターは `no_push` に**false**を格納し、`myoptions` に `directory_options::none` します。次に、 *pval*をディレクトリとして開き、読み取りを試みます。 成功した場合、`mystack` を初期化し、入れ子になったシーケンス内のディレクトリ以外の最初のファイル名を指定するために `myentry` します。それ以外の場合は、シーケンス末尾の反復子を生成します。

4番目と5番目のコンストラクターは、2番目と3番目のコンストラクターと同じように動作しますが、*最初に、`myoptions` に optin*が格納される点が異なります。 既定のコンストラクターは想定どおりの動作をします。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)\
[ファイル システムのナビゲーション (C++)](../standard-library/file-system-navigation.md)
