---
title: '&lt;filesystem&gt; 列挙体'
ms.date: 11/04/2016
f1_keywords:
- filesystem/std::filesystem::copy_options
- filesystem/std::experimental::filesystem::copy_options
- filesystem/std::filesystem::directory_options
- filesystem/std::experimental::filesystem::directory_options
- filesystem/std::filesystem::file_type
- filesystem/std::experimental::filesystem::file_type
- filesystem/std::filesystem::perms
- filesystem/std::experimental::filesystem::perms
ms.assetid: 0096c046-d101-464c-8259-b878a48280b0
ms.openlocfilehash: f148347cd132a604622415c65bb3e0352f5308eb
ms.sourcegitcommit: 069e3833bd821e7d64f5c98d0ea41fc0c5d22e53
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2019
ms.locfileid: "74303497"
---
# <a name="ltfilesystemgt-enumerations"></a>&lt;filesystem&gt; 列挙体

このトピックでは、filesystem ヘッダーの列挙体について説明します。

## <a name="requirements"></a>要件

**ヘッダー:** \<experimental/filesystem>

**名前空間:** std::experimental::filesystem

## <a name="copy_options"></a>  copy_options

動作を指定するために [copy](filesystem-functions.md#copy) および [copy_file](filesystem-functions.md#copy_file) 関数で使用されるビットマスク値の列挙体。

### <a name="syntax"></a>構文

```cpp
enum class copy_options {
   none = 0,
   skip_existing = 1,
   overwrite_existing = 2,
   update_existing = 4,
   recursive = 8,
   copy_symlinks = 16,
   skip_symlinks = 32,
   directories_only = 64,
   create_symlinks = 128,
   create_hard_links = 256
};
```

### <a name="values"></a>値

|`Name`|説明|
|------------|-----------------|
|`none`|演算の既定の動作を実行します。|
|`skip_existing`|ファイルが既に存在する場合はコピーしません。エラーをレポートしません。|
|`overwrite_existing`|ファイルが既に存在する場合、ファイルを上書きします。|
|`update_existing`|ファイルが既に存在し、そのファイルの方が古い場合、ファイルを上書きします。|
|`recursive`|サブディレクトリとその内容を再帰的にコピーします。|
|`copy_symlinks`|シンボリック リンクが示すファイルをコピーするのではなく、シンボリック リンクをシンボリック リンクとしてコピーします。|
|`skip_symlinks`|シンボリック リンクを無視します。|
|`directories_only`|ディレクトリに対してのみ反復処理を実行します。ファイルを無視します。|
|`create_symlinks`|ファイルをコピーするのではなく、シンボリック リンクを作成します。 対象がカレント ディレクトリではない場合、ソース パスとして絶対パスを使用する必要があります。|
|`create_hard_links`|ファイルをコピーするのではなく、ハード リンクを作成します。|

## <a name="directory_options"></a> directory_options

ディレクトリへのシンボリック リンクに従うか、無視するかを指定します。

### <a name="syntax"></a>構文

```cpp
enum class directory_options {
   none = 0,
   follow_directory_symlink
};
```

### <a name="values"></a>値

|Name|説明|
|----------|-----------------|
|`none`|既定の動作: ディレクトリへのシンボリック リンクを無視します。 アクセス許可の拒否はエラーです。|
|`follow_directory_symlink`|ディレクトリへのシンボリック リンクを実際のディレクトリとして処理します。|

## <a name="file_type"></a>  file_type

ファイルの種類の列挙型。 サポートされる値は、regular、directory、not_found、および unknown です。

### <a name="syntax"></a>構文

```cpp
enum class file_type {
    not_found = -1,
    none,
    regular,
    directory,
    symlink,
    block,
    character,
    fifo,
    socket,
    unknown
};
```

### <a name="values"></a>値

|Name|値|説明|
|----------|-----------|-----------------|
|`not_found`|-1|存在しないファイルを表します。|
|`none`|0|type 属性を持たないファイルを表します (サポートされていません)。|
|`regular`|1|従来のディスク ファイルを表します。|
|`directory`|2|ディレクトリを表します。|
|`symlink`|3|シンボリック リンクを表します (サポートされていません)。|
|`block`|4|UNIX ベースのシステム上のブロック型特殊ファイルを表します (サポートされていません)。|
|`character`|5|UNIX ベースのシステム上の文字型特殊ファイルを表します (サポートされていません)。|
|`fifo`|6|UNIX ベースのシステム上の FIFO ファイルを表します (サポートされていません)。|
|`socket`|7|UNIX ベースのシステム上のソケットを表します (サポートされていません)。|
|`unknown`|8|状態が確認できないファイルを表します。|

## <a name="perm_options"></a>perm_options

`replace`、`add`、`remove`、および `nofollow`の値が含まれます。

```cpp
enum class perm_options;
```

## <a name="perms"></a>  perms

ファイルのアクセス許可のフラグを設定します。 サポートされる値は、基本的に "readonly" と all です。 readonly ファイルの場合、*_write ビットは設定されません。 それ以外の場合、 `all` ビット (0x0777) が設定されます。

### <a name="syntax"></a>構文

```cpp
enum class perms {// names for permissions
   none = 0,
   owner_read = 0400,  // S_IRUSR
   owner_write = 0200, // S_IWUSR
   owner_exec = 0100,  // S_IXUSR
   owner_all = 0700,   // S_IRWXU
   group_read = 040,   // S_IRGRP
   group_write = 020,  // S_IWGRP
   group_exec = 010,   // S_IXGRP
   group_all = 070,    // S_IRWXG
   others_read = 04,   // S_IROTH
   others_write = 02,  // S_IWOTH
   others_exec = 01,   // S_IXOTH
   others_all = 07,    // S_IRWXO
   all = 0777,
   set_uid = 04000,    // S_ISUID
   set_gid = 02000,    // S_ISGID
   sticky_bit = 01000, // S_ISVTX
   mask = 07777,
   unknown = 0xFFFF,
   add_perms = 0x10000,
   remove_perms = 0x20000,
   resolve_symlinks = 0x40000
};
```

## <a name="see-also"></a>参照

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[\<filesystem>](../standard-library/filesystem.md)
