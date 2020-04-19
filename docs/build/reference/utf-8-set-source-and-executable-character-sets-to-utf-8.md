---
title: /8 (ソースと実行可能文字セットを UTF-8 に設定する)
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 1ff0f23ad0758642c73b1b35d6d4dd1be20899cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498182"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/8 (ソースと実行可能文字セットを UTF-8 に設定する)

ソース文字セットと実行文字セットの両方を UTF-8 として指定します。

## <a name="syntax"></a>構文

```
/utf-8
```

## <a name="remarks"></a>Remarks

**/-8**オプションを使用すると、utf-8 を使用してエンコードされたソースと実行の両方の文字セットを指定できます。 これは、コマンドラインで **/source-charset: utf-8/executioncharset: utf-8**を指定することと同じです。 これらのオプションのいずれでも、既定では、**文字セット**オプションが有効になります。 サポートされているコードページ識別子と文字セット名の一覧については、「[コードページ識別子](/windows/win32/Intl/code-page-identifiers)」を参照してください。

既定では、Visual Studio は、ソースファイルがエンコードされた Unicode 形式であるかどうかを判断するためにバイト順マークを検出します (UTF-16 や UTF-8 など)。 バイト順マークが見つからない場合は、 **/source-charset**オプションを使用してコードページを指定しない限り、ソースファイルが現在のユーザーコードページを使用してエンコードされているものと見なされます。 Visual Studio では、いくつかC++の文字エンコーディングのいずれかを使用して、ソースコードを保存できます。 ソース文字セットと実行文字セットの詳細については、言語ドキュメントの「[文字セット](../../cpp/character-sets.md)」を参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](../working-with-project-properties.md)」をご覧ください。

1. **[構成プロパティ]** 、 **[CC++/]** 、 **[コマンドライン]** フォルダーの順に展開します。

1. **[追加オプション]** で、使用するエンコードを指定するためのオプションを追加します。

1. **OK** を選択して変更を保存してください。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/文字セット (実行文字セットの設定)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (ソース文字セットの設定)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (互換性のある文字の検証)](validate-charset-validate-for-compatible-characters.md)
