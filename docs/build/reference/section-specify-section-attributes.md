---
title: /SECTION (セクション属性の指定)
ms.date: 12/29/2017
f1_keywords:
- /section
helpviewer_keywords:
- SECTION linker option
- -SECTION linker option
- section attributes
- /SECTION linker option
ms.openlocfilehash: 0a52e9c9dcd53b01f17dc36825732b34771c75bb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492627"
---
# <a name="section-specify-section-attributes"></a>/SECTION (セクション属性の指定)

> **/SECTION:** _name_, **[!]** {**DEKPRSW**}][ **,ALIGN=** _number_]

## <a name="remarks"></a>Remarks

**/SECTION**オプションは、セクションの属性を変更し、セクションの .obj ファイルがコンパイルされたときに設定された属性をオーバーライドします。

移植可能な実行可能 (PE) ファイルの*セクション*は、コードまたはデータのいずれかを含む、名前の付いた連続したメモリブロックです。 一部のセクションには、プログラムが直接宣言して使用するコードまたはデータが含まれています。また、リンカーとライブラリマネージャー (.lib) によって他のデータセクションが作成され、オペレーティングシステムにとって重要な情報が含まれています。 詳細については、「 [PE 形式](/windows/win32/Debug/pe-format)」を参照してください。

コロン (:) を指定してくださいとセクション*名*を指定します。 *名前*は大文字と小文字が区別されます。

標準名と競合するため、次の名前は使用しないでください。 たとえば、次のように、RISC プラットフォームでは .sdata が使用されます。

- . arch

- bss

- . データ

- ...

- . idata

- pdata

- . .rdata

- . reloc

- rsrc

- . .sbss

- .sdata

- srdata

- . テキスト

- . .xdata

セクションに1つまたは複数の属性を指定します。 次に示す属性文字では、大文字と小文字が区別されません。 セクションに使用するすべての属性を指定する必要があります。属性文字を省略すると、その属性ビットはオフになります。 R、W、または E を指定しない場合、既存の読み取り、書き込み、または実行可能ファイルの状態は変更されません。

属性を否定するには、その文字の前に感嘆符 (!) を付けます。 属性文字の意味を次の表に示します。

|文字|属性|説明|
|---------------|---------------|-------------|
|E|実行|セクションは実行可能です|
|R|読み取り|データの読み取り操作を許可します|
|W|Write|データに対する書き込み操作を許可します|
|S|Shared|イメージを読み込むすべてのプロセス間でセクションを共有します|
|D|アンドゥ|セクションを破棄不可としてマークします|
|K|キャッシュでき|セクションをキャッシュ不可能としてマークします|
|P|ページング可能な|セクションをページング不可としてマークします|

K と P は、これらに対応するセクションフラグが負の意味で使用されるという点では異常です。 **/SECTION:. text, K**オプションを使用して、text セクションでそのうちの1つを指定した場合、 [/HEADERS](headers.md)オプションを指定して[DUMPBIN](dumpbin-options.md)を実行すると、セクションフラグに違いはありません。セクションは既に暗黙的にキャッシュされています。 既定値を削除するには、 **/SECTION:. text,! を指定します。代わりに K**です。 DUMPBIN は、"キャッシュされていません" を含むセクション特性を明らかにします。

E、R、または W が設定されていない PE ファイルのセクションが無効である可能性があります。

**ALIGN =** _number_引数を使用すると、特定のセクションのアラインメント値を指定できます。 _Number_引数はバイト単位で、2の累乗でなければなりません。 詳細については、「 [/align](align-section-alignment.md) 」を参照してください。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ** > ] の [**リンカー** > **コマンドライン**] プロパティページをクリックします。

1. **[追加オプション]** ボックスにオプションを入力します。 **[OK]** または **[適用]** を選択して変更を適用します。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
