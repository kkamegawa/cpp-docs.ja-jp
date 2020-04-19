---
title: '&lt;filesystem&gt;'
description: 標準C++ライブラリの filesystem ヘッダーに含まれるクラス、関数、および型について説明します。
ms.date: 01/22/2020
f1_keywords:
- filesystem/std::experimental::filesystem::directory_entry
- filesystem/std::experimental::filesystem::recursive_directory_iterator
- filesystem/std::experimental::filesystem::path
- filesystem/std::experimental::filesystem::filesystem_error
- filesystem/std::experimental::filesystem::directory_iterator
- <filesystem>
ms.assetid: 5005753b-46fa-43e1-8d4e-1b38617d3cfd
no-loc:
- filesystem
- experimental
- char
- wchar_t
- char16_t
- char32_t
ms.openlocfilehash: dbe6dc89d5460a08ffafd86aa3fcd01222c82166
ms.sourcegitcommit: b67b08472b6f1ee8f1c5684bba7056d3e0fc745f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/24/2020
ms.locfileid: "76725683"
---
# &lt;filesystem&gt;

パス、ファイル、およびディレクトリに関する情報を操作および取得するクラスおよび関数にアクセスするために、ヘッダー &lt;filesystem> を含めます。

## <a name="syntax"></a>構文

```cpp
#include <filesystem> // C++17 standard header file name
#include <experimental/filesystem> // Header file for pre-standard implementation
using namespace std::experimental::filesystem::v1;
```

> [!IMPORTANT]
> Visual Studio 2017 のリリースでは、\<filesystem> ヘッダーは、まだC++標準ではありませんでした。 C++Visual Studio 2017 RTW では、 [ISO/IEC JTC 1/SC 22/WG 21 N4100](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4100.pdf)にある最終ドラフト標準が実装されています。 Visual Studio 2017 バージョン15.7 以降では、> standard filesystem新しい C++ 17 \<がサポートされています。
> これはまったく新しい実装であり、以前の `std::experimental` バージョンと互換性がありません。 これは、シンボリックリンクのサポート、バグの修正、標準の必須動作の変更によって必要になりました。 現時点では、\<filesystem> を含む新しい `std::filesystem` と前の `std::experimental::filesystem`が提供されています。 \<experimental/filesystem> は、古い experimental 実装のみを提供します。 experimental の実装は、ライブラリの次の ABI リリースで削除される予定です。

このヘッダーは、2つの広範なホストオペレーティングシステム (Microsoft Windows と POSIX) のいずれかのファイルシステムをサポートしています。

ほとんどの機能が両方のオペレーティング システムに共通していますが、このドキュメントではそれらの相違点について説明します。 例:

- Windows では、`c:` や `\\network_name`などの複数のルート名がサポートされています。 ファイルシステムは、ツリーのフォレストで構成されます。各ツリーには、`c:\` または `\\network_name\`のような独自のルートディレクトリがあり、それぞれに固有のディレクトリがあり、相対パス名 (絶対パス名ではないもの) を完了します。

- POSIX は、ルート名のない単一のツリー、単一のルートディレクトリ `/`、および1つの現在のディレクトリをサポートします。

もう 1 つの大きな違いは、パス名のネイティブな表現です。

- Windows では、UTF-16 (文字ごとに1つ以上の要素) としてエンコードされた **wchar_t** の null 終端シーケンスを使用します。

- POSIX では、UTF-8 (文字ごとに1つ以上の要素) としてエンコードされた、null で終わる **char** のシーケンスを使用します。

- クラス `path` のオブジェクトは、パス名をネイティブ形式で格納しますが、この格納形式といくつかの外部形式の間の簡単な変換をサポートします。

  - オペレーティングシステムで優先されるようにエンコードされた、null で終わる **char** のシーケンス。

  - UTF-8 としてエンコードされた **char** の null で終わるシーケンス。

  - オペレーティングシステムで優先されるようにエンコードされた、null で終わる **wchar_t** のシーケンス。

  - UTF-16 としてエンコードされた **char16_t** の null で終わるシーケンス。

  - 32 UTF-8 としてエンコードされた **char32_t** の null で終わるシーケンス。

  必要に応じて、1 つまたは複数の `codecvt` ファセットを使用することによって、これらの表現の相互変換が実施されます。 特定のロケールオブジェクトが指定されていない場合、これらのファセットはグローバルロケールから取得されます。

もう 1 つの相違点は、オペレーティング システムで指定可能なファイルまたはディレクトリのアクセス許可の詳細です。

- Windows は、ファイルが読み取り専用であるか書き込み可能であるかを記録します。この属性は、ディレクトリに対して意味がありません。

- POSIX は、ファイルの読み取り、書き込み、または実行 (ディレクトリの場合はスキャン) が可能かどうかを記録します。 また、各操作を所有者、所有者のグループ、またはすべての人に許可し、他のいくつかのアクセス許可を許可するかどうかも指定します。

両方のシステムに共通しているのは、ルート名に到達するまでのパス名に適用される構造です。 パス名 `c:/abc/xyz/def.ext`:

- ルート名が `c:`。

- ルートディレクトリが `/`。

- ルートパスが `c:/`。

- 相対パスは `abc/xyz/def.ext`。

- 親パスが `c:/abc/xyz`。

- ファイル名が `def.ext` です。

- ステムは `def`です。

- 拡張機能が `.ext`。

軽微な違いは、パス名にあるディレクトリのシーケンス間の推奨される区切り記号です。 どちらのオペレーティングシステムでもスラッシュ `/`を記述できますが、一部のコンテキストでは、Windows では円記号 `\`が優先されます。 実装では、`path`のデータメンバー `preferred_separator` に、優先する区切り記号が格納されます。

最後に、`path` のオブジェクトには重要な機能があります。ヘッダー [\<fstream >](fstream.md)で定義されているクラスで filename 引数が必要な場所であれば、それらを使用できます。

詳細とコード例については、「[ファイルシステムC++のナビゲーション」 ()](../standard-library/file-system-navigation.md)を参照してください。

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|||
|-|-|
|[directory_entry クラス](../standard-library/directory-entry-class.md)|`directory_iterator` または `recursive_directory_iterator` によって返され、`path`を含むオブジェクトを表します。|
|[directory_iterator クラス](../standard-library/directory-iterator-class.md)|ファイル システム ディレクトリのファイル名をシーケンス処理する入力反復子を表します。|
|[filesystem_error クラス](../standard-library/filesystem-error-class.md)|低レベル システム オーバーフローをレポートするためにスローされる例外のための基底クラス。|
|[path クラス](../standard-library/path-class.md)|ファイル名として使用するのに適したテンプレート型 `String` のオブジェクトを格納するクラスを定義します。|
|[recursive_directory_iterator クラス](../standard-library/recursive-directory-iterator-class.md)|ファイル システム ディレクトリのファイル名をシーケンス処理する入力反復子を表します。 反復子はサブディレクトリに下りることもできます。|
|[file_status クラス](../standard-library/file-status-class.md)|`file_type`をラップします。|

### <a name="structs"></a>構造体

|||
|-|-|
|[space_info 構造体](../standard-library/space-info-structure.md)|ボリュームに関する情報を保持します。|

## <a name="functions"></a>関数

[\<filesystem> 関数](../standard-library/filesystem-functions.md)

## <a name="operators"></a>演算子

[\<filesystem> 演算子](../standard-library/filesystem-operators.md)

## <a name="enumerations"></a>列挙

|||
|-|-|
|[copy_options](../standard-library/filesystem-enumerations.md#copy_options)|[copy_file](../standard-library/filesystem-functions.md#copy_file) と共に使用され、コピー先ファイルが既に存在する場合の動作を決定する列挙体です。|
|[directory_options](../standard-library/filesystem-enumerations.md#directory_options)|ディレクトリ反復子のオプションを指定する列挙体。|
|[file_type](../standard-library/filesystem-enumerations.md#file_type)|ファイルの種類の列挙型。|
|[perm_options](../standard-library/filesystem-enumerations.md#perm_options)| `permissions` 関数のオプションを列挙します。 |
|[perms](../standard-library/filesystem-enumerations.md#perms)|アクセス許可とアクセス許可に対するオプションを伝達するために使用されるビットマスク型|

## <a name="see-also"></a>関連項目

[ヘッダーファイルのリファレンス](../standard-library/cpp-standard-library-header-files.md)
