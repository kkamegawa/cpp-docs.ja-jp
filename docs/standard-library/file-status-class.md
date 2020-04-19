---
title: file_status クラス
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 60ced1f60c811f585928f47c6cfd5e695d0c4085
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457754"
---
# <a name="filestatus-class"></a>file_status クラス

[file_type](../standard-library/filesystem-enumerations.md#file_type) とファイルの [perms](../standard-library/filesystem-enumerations.md#perms) をラップします。

## <a name="syntax"></a>構文

```cpp
class file_status;
```

### <a name="constructors"></a>コンストラクター

|コンストラクター|説明|
|-|-|
|[file_status](#file_status)|[File_type](../standard-library/filesystem-enumerations.md#file_type)とファイル[perms](../standard-library/filesystem-enumerations.md#perms)のラッパーを構築します。|

### <a name="member-functions"></a>メンバー関数

|メンバー関数|説明|
|-|-|
|[type](#type)|`file_type` を取得または設定します。|
|[permissions](#permissions)|ファイルのアクセス許可を取得または設定します。|

### <a name="operators"></a>演算子

|演算子|説明|
|-|-|
|[operator=](#op_as)|この既定のメンバー代入演算子は想定どおりに動作します。|

## <a name="requirements"></a>必要条件

**ヘッダー:** \<ファイルシステム >

**名前空間:** std:: 実験的:: filesystem、std:: 実験的:: filesystem

## <a name="file_status"></a>file_status::file_status

[File_type](../standard-library/filesystem-enumerations.md#file_type)とファイル[perms](../standard-library/filesystem-enumerations.md#perms)のラッパーを構築します。

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>パラメーター

*ftype*\
指定`file_type`した場合`file_type::none`、既定値はになります。

*隠す*\
指定さ`perms`れたファイル`perms::unknown`、既定値はです。

*file_status*\
格納されているオブジェクト。

## <a name="op_as"></a>file_status:: operator =

この既定のメンバー代入演算子は想定どおりに動作します。

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>パラメーター

*file_status*\
に`file_status`コピーされる[file_status](../standard-library/file-status-class.md) 。

## <a name="type"></a>各種

`file_type` を取得または設定します。

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>パラメーター

*ftype*\
`file_type` と指定します。

## <a name="permissions"></a>許可

ファイルのアクセス許可を取得または設定します。

Setter を使用してファイル`readonly`を作成するか、 `readonly`属性を削除します。

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>パラメーター

*隠す*\
`perms` と指定します。

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[path クラス](../standard-library/path-class.md)\
[\<filesystem>](../standard-library/filesystem.md)
