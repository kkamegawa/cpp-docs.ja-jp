---
title: /文字セット (実行文字セットの設定)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 44e83524867bc8a914706e1f5b45b61bc4a48087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492911"
---
# <a name="execution-charset-set-execution-character-set"></a>/文字セット (実行文字セットの設定)

実行可能ファイルの実行文字セットを指定できます。

## <a name="syntax"></a>構文

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>引数

*IANA_name*<br/>
IANA によって定義された文字セット名。

*CPID*<br/>
コードページ識別子。

## <a name="remarks"></a>Remarks

**/Executioncharset**オプションを使用すると、実行文字セットを指定できます。 実行文字セットは、すべての前処理手順の後にコンパイルフェーズに入力されるプログラムのテキストに使用されるエンコーディングです。 この文字セットは、コンパイルされたコード内の任意の文字列リテラルまたは文字リテラルの内部表現に使用されます。 基本実行文字セットで表現できない文字がソースファイルに含まれる場合に使用する拡張実行文字セットを指定するには、このオプションを設定します。 使用する文字セットを指定するには、IANA または ISO の文字セット名、またはドット (.) の後に 3 ~ 5 桁の10進数コードページ識別子を使用できます。 サポートされているコードページ識別子と文字セット名の一覧については、「[コードページ識別子](/windows/win32/Intl/code-page-identifiers)」を参照してください。

既定では、Visual Studio は、ソースファイルがエンコードされた Unicode 形式であるかどうかを判断するためにバイト順マークを検出します (UTF-16 や UTF-8 など)。 バイト順マークが見つからない場合、 **/source-charset**オプションまたは **/utf8**オプションを使用して文字セット名またはコードページを指定していない限り、現在のユーザーコードページを使用してソースファイルがエンコードされているものと見なされます。 Visual Studio では、いくつかC++の文字エンコーディングのいずれかを使用して、ソースコードを保存できます。 ソース文字セットと実行文字セットの詳細については、言語ドキュメントの「[文字セット](../../cpp/character-sets.md)」を参照してください。

ソース文字セットと実行文字セットの両方を UTF-8 に設定する場合は、 **8**つのコンパイラオプションをショートカットとして使用できます。 これは、コマンドラインで **/source-charset: utf-8/executioncharset: utf-8**を指定することと同じです。 これらのオプションのいずれでも、既定では、**文字セット**オプションが有効になります。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]** 、 **[CC++/]** 、 **[コマンドライン]** フォルダーの順に展開します。

1. **[追加オプション]** で、 **[文字セット]** オプションを追加し、任意のエンコードを指定します。

1. **OK** を選択して変更を保存してください。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/source-charset (ソース文字セットの設定)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (ソースと実行可能ファイルの文字セットを UTF-8 に設定する)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (互換性のある文字の検証)](validate-charset-validate-for-compatible-characters.md)
