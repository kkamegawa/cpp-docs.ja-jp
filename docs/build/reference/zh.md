---
title: /ZH (デバッグ情報でファイルのチェックサムを計算するためのハッシュアルゴリズム)
description: /ZH コンパイラオプションを使用して、デバッグ情報で MD5、SHA-1、または SHA-256 ソースファイルのチェックサムを有効にします。
ms.date: 09/16/2019
f1_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
helpviewer_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
- /ZH compiler option
- /ZH:MD5 compiler option
- /ZH:SHA1 compiler option
- /ZH:SHA_256 compiler option
- Hash algorithm for file checksum in debug info
ms.openlocfilehash: f05dc2bc3b8ce4502ff16a6e19fdbb10763b34ba
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686936"
---
# <a name="zh-hash-algorithm-for-calculation-of-file-checksum-in-debug-info"></a>/ZH (デバッグ情報でファイルのチェックサムを計算するためのハッシュアルゴリズム)

各ソースファイルのチェックサムを生成するために使用する暗号ハッシュアルゴリズムを指定します。

## <a name="syntax"></a>構文

> **/ZH:** {**MD5**|**SHA1**|**SHA_256**}

## <a name="arguments"></a>引数

**/ZH: MD5**\
チェックサムに MD5 ハッシュを使用します。 これは既定のオプションです。

**/ZH: SHA1**\
チェックサムに SHA-1 ハッシュを使用します。

**/ZH: SHA_256**\
チェックサムには、SHA-256 ハッシュを使用します。

## <a name="remarks"></a>コメント

PDB ファイルは、関連付けられている実行可能ファイルのオブジェクトコードにコンパイルされた各ソースファイルのチェックサムを格納します。 チェックサムにより、デバッガーは、読み込まれたソースコードが実行可能ファイルと一致することを確認できます。 コンパイラとデバッガーは、MD5、SHA-1、および SHA-256 のハッシュアルゴリズムをサポートしています。 既定では、コンパイラは MD5 ハッシュを使用してチェックサムを生成します。 このオプションは、 **/ZH: MD5**オプションを使用して明示的に指定できます。

MD5 および SHA-1 で衝突の問題が発生するリスクがあるため、 **/ZH: SHA_256**オプションを使用することをお勧めします。 SHA-256 ハッシュによって、コンパイル時間がわずかに増加することがあります。

複数の **/ZH**オプションが指定されている場合、最後のオプションが使用されます。

**/ZH**オプションは、Visual Studio 2019 バージョン16.4 以降で使用できます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. **[構成]** ドロップダウンを **[すべての構成]** に設定します。

1. **[構成プロパティ]**  >  **[C/C++]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. "**追加オプション**" プロパティを変更して、 **/ZH: MD5**、 **/ZH: SHA1**、または **/ZH: SHA_256**オプションを追加し、[ **OK]** を選択します。

## <a name="see-also"></a>関連項目

[コンパイラオプション](compiler-options.md)\
[[転送元サーバー]](/windows/win32/debug/source-server-and-source-indexing)
