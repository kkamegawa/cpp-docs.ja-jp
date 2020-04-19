---
title: /Yl (デバッグ ライブラリの PCH 参照の挿入)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: 92e47836e0fdae077defa0fe35b515ab4ca20a66
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316250"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (デバッグ ライブラリの PCH 参照の挿入)

**/Yl**オプションは、プリコンパイル済みヘッダー ファイルで一意のシンボルを生成し、このシンボルへの参照がプリコンパイル済みヘッダーを使用するすべてのオブジェクト ファイルに挿入されます。

## <a name="syntax"></a>構文

>**/Yl**
> **/Yl**_名前_
> **/Yl-**

### <a name="arguments"></a>引数

*name*<br/>
一意のシンボルの一部として使用される、省略可能な名前です。

*\-*<br/>
ダッシュ (-) を明示的に無効にします、 **/Yl**コンパイラ オプション。

## <a name="remarks"></a>Remarks

**/Yl**コンパイラ オプションを使用して作成されたプリコンパイル済みヘッダー ファイルで一意のシンボル定義を作成し、 [/Yc](yc-create-precompiled-header-file.md)オプション。 このシンボルへの参照を使用して、プリコンパイル済みヘッダーを含むすべてのファイルに自動的に挿入された、 [/Yu](yu-use-precompiled-header-file.md)コンパイラ オプション。 **/Yl**オプションが既定で有効になっているときに **/Yc**プリコンパイル済みヘッダー ファイルを作成するために使用します。

**/Yl**_名前_プリコンパイル済みヘッダー ファイルで特定のシンボルを作成するオプションを使用します。 コンパイラを使用して、*名前*を作成するようなシンボルの装飾名の一部として引数`__@@_PchSym_@00@...@name`、省略記号 (...) を表しますが、一意のコンパイラによって生成された文字の文字列。 場合、*名前*引数を省略すると、コンパイラがシンボル名を自動的に生成します。 通常、シンボルの名前を知っている必要はありません。 ただし、プロジェクトが 1 つ以上のプリコンパイル済みヘッダー ファイルを使用する場合、 **/Yl**_名前_オプション オブジェクトのプリコンパイル済みヘッダーを使用してファイルを確認すると役立つ場合があります。 使用することができます*名前*としてダンプ ファイルにシンボル参照を検索する検索文字列。

**/Yl-** 既定の動作を無効にし、プリコンパイル済みヘッダー ファイルで特定のシンボルを配置しません。 このプリコンパイル済みヘッダーが含まれるコンパイル済みのファイルは、共通のシンボル参照を取得できません。

ときに **/Yc**が指定されていない、 **/Yl**オプションは場合は指定のいずれかに一致する必要がありますが、影響を与えません **/Yl**オプションでは、ときに渡される **/Yc**は指定します。

使用する場合 **/Yl-**、 **/Yc**と[/Z7](z7-zi-zi-debug-information-format.md)プリコンパイル済みヘッダー ファイル、デバッグ情報を作成するオプションが作成するために使用するソース ファイルのオブジェクト ファイルに格納されている、プリコンパイル済みヘッダーではなく、個別の .pdb ファイル。 このオブジェクト ファイルに、ライブラリの一部が行われたし場合[LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md)エラーまたは[LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md)ソース ファイルを作成するために使用する場合に、次の警告がこのライブラリと、プリコンパイル済みヘッダー ファイルを使用するビルドで発生する可能性が、プリコンパイル済みヘッダー ファイルは定義されません記号自体。 リンカーが、リンク、関連付けられているデバッグ情報、およびからのオブジェクト ファイルを除外するには、オブジェクト ファイルではありませんが、ライブラリ クライアントで参照されるとします。 この問題を解決するには指定 **/Yl** (または削除、 **/Yl-** オプション) を使用すると **/Yc**プリコンパイル済みヘッダー ファイルを作成します。 これにより、デバッグ情報を含むライブラリからオブジェクト ファイルがビルドでリンクされます。

プリコンパイル済みヘッダーの詳細についてを参照してください。

- [/Y (プリコンパイル済みヘッダー)](y-precompiled-headers.md)

- [プリコンパイル済みヘッダー ファイル](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 追加、 **/Yl**_名前_コンパイラ オプションで、**追加オプション**ボックス。 **OK** を選択して変更を保存してください。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
