---
title: /DEBUG (デバッグ情報の生成)
ms.date: 05/16/2019
f1_keywords:
- VC.Project.VCLinkerTool.GenerateDebugInformation
- /debug
helpviewer_keywords:
- DEBUG linker option
- /DEBUG linker option
- -DEBUG linker option
- PDB files
- debugging [C++], debug information files
- generate debug info linker option
- pdb files, generating debug info
- .pdb files, generating debug info
- debugging [C++], linker option
- program databases [C++]
ms.assetid: 1af389ae-3f8b-4d76-a087-1cdf861e9103
ms.openlocfilehash: 2ec466a6356ace437d32eb517bf2da291938f5db
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837141"
---
# <a name="debug-generate-debug-info"></a>/DEBUG (デバッグ情報の生成)

```
/DEBUG[:{FASTLINK|FULL|NONE}]
```

## <a name="remarks"></a>解説

**/DEBUG** オプションにより、実行可能ファイルのデバッグ情報が作成されます。

リンカーによって、デバッグ情報がプログラム データベース (PDB) ファイルに入ります。 それにより、プログラムの後続のビルド中、PDB が更新されます。

デバッグ用に作成された実行可能ファイル (.exe ファイルまたは DLL) には、対応する PDB の名前とパスが含まれます。 デバッガーでは、組み込まれた名前が読み取られ、プログラムのデバッグ時に PDB が使用されます。 リンカーによって、プログラムの基本名と拡張子 .pdb が使用され、プログラム データベースに名前が付けられ、それが作成されたパスが埋め込まれます。 この既定をオーバーライドするには、[/PDB](pdb-use-program-database.md) を設定し、別のファイル名を指定します。

**/DEBUG:FASTLINK** オプションは、Visual Studio 2017 以降で使用できます。 このオプションは、実行可能ファイルの構築に使用される個々のコンパイル製品にプライベート シンボル情報を残します。 それにより、完全なコピーを作成する代わりに、実行可能ファイルの構築に使用されるオブジェクト ファイルとライブラリのデバッグ情報にインデックスを作成する制限付き PDB が生成されます。 このオプションでは、PDB の完全生成と比較して 2 倍から 4 倍速くリンクできるため、ローカルでデバッグするとき、ビルド製品を利用できるときに推奨されます。 この制限付き PDB は、実行可能ファイルが別のコンピューターに配置されているなど、必要なビルド製品が利用できないときはデバッグに使用できません。 開発者コマンド プロンプトで、mspdbcmf.exe ツールを使用し、この制限付き PDB から完全 PDB を生成できます。 Visual Studio で、完全 PDB ファイルを生成するためのプロジェクトまたはビルド メニュー アイテムを使用し、プロジェクトまたはソリューションの完全 PDB を作成します。

**/DEBUG:FULL** オプションでは、個々のコンパイル製品 (オブジェクト ファイルとライブラリ) から 1 個の PDB にプライベート シンボル情報がすべて移動します。これはリンクの中で最も時間がかかる部分になる可能性があります。 ただし、完全な PDB を使用することで、実行可能ファイルが展開されているときなど、他のビルド製品が利用できないとき、実行可能ファイルをデバッグできます。

**/DEBUG:NONE** オプションで PDB が生成されることはありません。

追加のオプションなしで **/DEBUG** を指定すると、リンカーでは既定で、コマンド ラインとメイクファイル ビルド、Visual Studio IDE のリリース ビルド、Visual Studio 2015 以前のバージョンのデバッグおよびリリース ビルドの両方に対して、 **/DEBUG:FULL** が設定されます。 Visual Studio 2017 以降では、IDE のビルド システムでは、デバッグ ビルドに **/DEBUG** オプションを指定したとき、既定で **/DEBUG:FASTLINK** に設定されます。 下位互換性を維持する目的で他の既定値は変更されません。

コンパイラの [C7 Compatible](z7-zi-zi-debug-information-format.md) (/Z7) オプションにより、コンパイラは .obj ファイルにデバッグ情報を残します。 [Program Database](z7-zi-zi-debug-information-format.md) (/Zi) コンパイラ オプションを使用し、.obj ファイルの PDB にデバッグ情報を保存することもできます。 このリンカーでは最初に、.obj ファイルに書き込まれている絶対パスでオブジェクトの PDB が検索されます。次に、.obj ファイルが含まれているディレクトリで検索されます。 オブジェクトの PDB ファイル名または場所をリンカーに指定することはできません。

/DEBUG を指定すると [/INCREMENTAL](incremental-link-incrementally.md) も指定されます。

/DEBUG により [/OPT](opt-optimizations.md) オプションの既定値が REF から NOREF に、ICF から NOICF に変更されます。そのため、元の既定値を使用する場合、明示的に /OPT:REF または /OPT:ICF を指定する必要があります。

デバッグ情報が含まれる .exe または .dll を作成することはできません。 デバッグ情報は常に .obj または .pdb ファイルに置かれます。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関する記事を参照してください。

1. **[リンカー]** フォルダーをクリックします。

1. **[デバッグ]** プロパティ ページをクリックします。

1. **[デバッグ情報の生成]** プロパティを変更し、PDB 生成を有効にします。 これにより、Visual Studio 2017 以降で /DEBUG:FASTLINK が有効になります。

1. **[完全なプログラム データベース ファイルを生成]** プロパティを変更し、すべてのインクリメンタル ビルドの完全 PDB 生成に対して /DEBUG:FULL を有効にします。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.GenerateDebugInformation%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
