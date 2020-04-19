---
title: /source-charset (ソース文字セットの設定)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: cd3e4eb3fd305ba6bdd298d18b1edb80f2b98343
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498255"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset (ソース文字セットの設定)

実行可能ファイルのソース文字セットを指定できます。

## <a name="syntax"></a>構文

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>引数

**IANA_name**<br/>
IANA によって定義された文字セット名。

**CPID**<br/>
10進数のコードページ識別子。

## <a name="remarks"></a>Remarks

**/Source-charset**オプションを使用して、ソースファイルに基本ソース文字セットで表されない文字が含まれている場合に使用する拡張ソース文字セットを指定できます。 ソース文字セットは、プログラムのソーステキストを、コンパイル前のプリプロセスフェーズへの入力として使用される内部表現として解釈するために使用されるエンコーディングです。 内部表現は、実行可能ファイルに文字列と文字の値を格納するために実行文字セットに変換されます。 使用する文字セットを指定するには、IANA または ISO の文字セット名、またはドット (.) の後に 3 ~ 5 桁の10進数コードページ識別子を使用できます。 サポートされているコードページ識別子と文字セット名の一覧については、「[コードページ識別子](/windows/win32/Intl/code-page-identifiers)」を参照してください。

既定では、Visual Studio は、ソースファイルがエンコードされた Unicode 形式であるかどうかを判断するためにバイト順マークを検出します (UTF-16 や UTF-8 など)。 バイト順マークが見つからない場合は、 **/source-charset**オプションを使用して文字セット名またはコードページを指定しない限り、ソースファイルが現在のユーザーコードページを使用してエンコードされているものと見なされます。 Visual Studio では、いくつかC++の文字エンコーディングのいずれかを使用して、ソースコードを保存できます。 ソース文字セットと実行文字セットの詳細については、言語ドキュメントの「[文字セット](../../cpp/character-sets.md)」を参照してください。

入力するソース文字セットは、7ビットの ASCII 文字を文字セット内の同じコードポイントにマップする必要があります。そうしないと、多くのコンパイルエラーが発生する可能性があります。 また、ソース文字セットは、UTF-8 によって encodable 拡張 Unicode 文字セットにマッピングされている必要があります。 UTF-8 で encodable されていない文字は、実装固有の代替で表されます。 Microsoft コンパイラは、これらの文字に疑問符を使用します。

ソース文字セットと実行文字セットの両方を UTF-8 に設定する場合は、 **8**つのコンパイラオプションをショートカットとして使用できます。 これは、コマンドラインで **/source-charset: utf-8/executioncharset: utf-8**を指定することと同じです。 これらのオプションのいずれでも、既定では、**文字セット**オプションが有効になります。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]** 、 **[CC++/]** 、 **[コマンドライン]** フォルダーの順に展開します。

1. **[追加オプション]** で、 **/source-charset**オプションを追加し、優先するエンコードを指定します。

1. **OK** を選択して変更を保存してください。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/文字セット (実行文字セットの設定)](execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (ソースと実行可能ファイルの文字セットを UTF-8 に設定する)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (互換性のある文字の検証)](validate-charset-validate-for-compatible-characters.md)
