---
title: /LINKREPRO (リンク再現ディレクトリ名)
description: リンカーまたはライブラリツールオプションリンクを再現するディレクトリを設定します。
ms.date: 09/24/2019
f1_keywords:
- /LINKREPRO
helpviewer_keywords:
- LINKREPRO linker option
- /LINKREPRO linker option
- -LINKREPRO linker option
- linker repro reporting
ms.openlocfilehash: d81fb529cdbb0741c6dff58032dad97df89b4d4f
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686918"
---
# <a name="linkrepro-link-repro-directory-name"></a>/LINKREPRO (リンク再現ディレクトリ名)

リンカーまたはライブラリツールに対して、指定されたディレクトリでのリンク再現を生成するように指示します。

## <a name="syntax"></a>構文

> **/リンク再現:** _ディレクトリ名_

### <a name="arguments"></a>引数

**/リンク再現:** _ディレクトリ名_\
リンクを格納するユーザー指定のディレクトリを指定します。 スペースを含むディレクトリ名は二重引用符で囲む必要があります。

## <a name="remarks"></a>コメント

**/Link再現**オプションを使用して、*リンク再現*コードを作成します。 これは、Microsoft がリンク時またはライブラリ操作中に発生する問題を再現できるようにする一連のビルド成果物です。 これは、リンク時のコード生成 (LTCG)、LNK1000 リンカーエラー、またはリンカークラッシュを伴うバックエンドクラッシュなどの問題に役立ちます。 このツールでは、 **/link再現**リンカーオプションを指定した場合、またはコマンドラインビルド環境で `link_repro` 環境変数を設定した場合に、リンク再現が生成されます。 詳細については、「 [Microsoft C++ツールセットの問題を報告する方法](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md)」の「[リンク](../../overview/how-to-report-a-problem-with-the-visual-cpp-toolset.md#link-repros)の再現」セクションを参照してください。

**/Link再現**リンカーオプションと `link_repro` 環境変数の両方で、リンク再現用の出力ディレクトリを指定する必要があります。 コマンドラインまたは IDE で、 **/link再現:** _ディレクトリ名_オプションを使用してディレクトリを指定します。 指定する_ディレクトリ名_は絶対パスまたは相対パスにすることができますが、ディレクトリが存在している必要があります。 コマンドラインオプションは、`link_repro` 環境変数で設定されているディレクトリ値よりも優先されます。

リンク再現の生成を特定のターゲットファイル名に制限する方法については、 [/linkreprotarget](linkreprotarget.md)オプションを参照してください。 このオプションを使用して、リンクを生成する特定のターゲットを指定できます。 リンカーまたはライブラリツールを複数回呼び出す複雑なビルドで役に立ちます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

1. **[構成プロパティ]**  >  **[リンカー]**  >  **[コマンド ライン]** プロパティ ページを選択します。

1. **[追加オプション]** ボックスに、 **「/link再現:** _ディレクトリ名_」オプションを入力します。 指定する_ディレクトリ名_の値は、存在している必要があります。 **[OK]** を選択して変更を適用します。

リンク再現コードを生成したら、このプロパティページを再度開いて、ビルドからの **/link再現**オプションを削除します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 「<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>」を参照してください。

## <a name="see-also"></a>参照

[MSVC リンカーリファレンス](linking.md)\
[MSVC リンカーオプション](linker-options.md)\
[/Linkreprotarget](linkreprotarget.md)
