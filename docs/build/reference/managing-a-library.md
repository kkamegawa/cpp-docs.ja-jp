---
title: ライブラリの管理
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLibrarianTool.OVERWRITEAllDefaultLibraries
- VC.Project.VCLibrarianTool.AdditionalDependencies
- VC.Project.VCLibrarianTool.RemoveObjects
- VC.Project.VCLibrarianTool.LibraryPaths
- VC.Project.VCLibrarianTool.OutputFile
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryNames
- VC.Project.VCLibrarianTool.AdditionalLibraryDirectories
- VC.Project.VCLibrarianTool.ListContentsFile
- VC.Project.VCLibrarianTool.ListContents
- VC.Project.VCLibrarianTool.SubSystemVersion
- VC.Project.VCLibrarianTool.OVERWRITEDefaultLibraryName
- VC.Project.VCLibrarianTool.SubSystem
helpviewer_keywords:
- /LIBPATH library manager option
- OUT library manager option
- CONVERT library manager option
- LIBPATH library manager option
- /LIST library manager option
- object files, building and modifying
- -LINK50COMPAT library manager option
- REMOVE library manager option
- SUBSYSTEM library manager option
- /LINK50COMPAT library manager option
- /OUT library manager option
- LIB [C++], managing COFF libraries
- -CONVERT library manager option
- LINK50COMPAT library manager option
- -OUT library manager option
- -REMOVE library manager option
- -LIST library manager option
- /SUBSYSTEM library manager option
- -SUBSYSTEM library manager option
- /REMOVE library manager option
- -LIBPATH library manager option
- object files
- LIST library manager option
- /CONVERT library manager option
ms.assetid: f56a8b85-fbdc-4c09-8d8e-00f0ffe1da53
ms.openlocfilehash: 74b8cf198d46f83de327c68ac5f883bd75e5db80
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62321450"
---
# <a name="managing-a-library"></a>ライブラリの管理

LIB の既定のモードは、ビルドまたは COFF オブジェクトのライブラリを変更することです。 LIB は、(オブジェクトをファイルにコピー) する/EXTRACT または/DEF (インポート ライブラリをビルドする) を指定しないと、このモードで実行されます。

オブジェクトまたはライブラリからのライブラリをビルドするには、次の構文を使用します。

```
LIB [options...] files...
```

このコマンドは、1 つまたは複数の入力からライブラリを作成します。*ファイル*します。 *ファイル*COFF オブジェクト ファイル、32 ビット OMF オブジェクト ファイル、または既存 COFF ライブラリを指定できます。 LIB は、指定したファイルにすべてのオブジェクトを含む 1 つのライブラリを作成します。 入力ファイルが 32 ビット OMF オブジェクト ファイルの場合に変換された COFF ライブラリを構築する前にします。 LIB は、16 ビット版の LIB によって作成されたライブラリ内の 32 ビット OMF オブジェクトを受け入れることはできません。 まず; オブジェクトを抽出するのに 16 ビットの LIB を使用する必要があります。32 ビットの LIB の入力として抽出されたオブジェクト ファイルを使用できます。

LIB 既定では、最初のオブジェクトまたはライブラリ ファイルと拡張機能の基本名を使用して出力ファイルの名前します。 lib します。 出力ファイルは、現在のディレクトリに置かれます。 同じ名前のファイルが既に存在する場合、出力ファイルには、既存のファイルが置き換えられます。 既存のライブラリを保持するために/OUT オプションを使用して、出力ファイルの名前を指定します。

次のオプションは、ビルドとライブラリの変更に適用されます。

**/LIBPATH:** *dir*<br/>
環境ライブラリ パスをオーバーライドします。 詳細については、リンクの説明を参照してください。 [/LIBPATH](libpath-additional-libpath.md)オプション。

**/LIST**<br/>
標準出力に出力ライブラリに関する情報を表示します。 出力は、ファイルにリダイレクトできます。 /LIST を使用すると、変更せず既存のライブラリの内容を判断します。

**/NAME:** *filename*<br/>
インポート ライブラリを構築する場合は、インポート ライブラリが構築されている DLL の名前を指定します。

**/NODEFAULTLIB**<br/>
外部参照を解決するときに検索するライブラリの一覧から 1 つまたは複数の既定のライブラリを削除します。 参照してください[/NODEFAULTLIB](nodefaultlib-ignore-libraries.md)詳細についてはします。

**/OUT:** *filename*<br/>
既定の出力ファイル名をオーバーライドします。 既定では、出力ライブラリは、コマンドラインと拡張機能では、最初のライブラリまたはオブジェクトの次のファイルの基本名を持つ、現在のディレクトリに作成します。 lib します。

**/REMOVE:** *object*<br/>
指定した*オブジェクト*出力ライブラリから。 LIB は、(オブジェクト ファイルまたはライブラリでか)、すべてのオブジェクトを組み合わせ、/REMOVE で指定されたオブジェクトを削除し、出力ライブラリを作成します。

**/SUBSYSTEM:**{**コンソール** &AMP;#124; **EFI_APPLICATION** &AMP;#124; **EFI_BOOT_SERVICE_DRIVER** &AMP;#124; **EFI_ROM**&AMP;#124; **EFI_RUNTIME_DRIVER** &AMP;#124; **ネイティブ** &AMP;#124; **POSIX** &AMP;#124; **WINDOWS** &AMP;#124; **WINDOWSCE**} [、#[. ##]<br/>
出力ライブラリにリンクすることによって作成されたプログラムを実行する方法をオペレーティング システムに指示します。 詳細については、リンクの説明を参照してください。 [/SUBSYSTEM](subsystem-specify-subsystem.md)オプション。

コマンドラインで指定された LIB オプション小文字は区別されません。

LIB を使用して、次のライブラリ管理タスクを実行できます。

- オブジェクトをライブラリに追加するのには、既存のライブラリのファイル名と新しいオブジェクトのファイル名を指定します。

- ライブラリを結合するには、ライブラリのファイル名を指定します。 オブジェクトを追加し、1 つの LIB コマンドを使用してライブラリを結合できます。

- 新しいオブジェクトを使ってライブラリ メンバーを置換するには、置き換えられるメンバー オブジェクトを格納しているライブラリと、新しいオブジェクト (またはライブラリが含まれる) のファイル名を指定します。 1 つ以上の入力ファイルで同じ名前を持つオブジェクトが存在するライブラリには、最後の LIB コマンドで出力ライブラリに指定されたオブジェクトが保存されます。 ライブラリ メンバーを置換すると、古いオブジェクトが含まれているライブラリの後に、新しいオブジェクトまたはライブラリを指定することを確認します。

- ライブラリからメンバーを削除するには、/remove と入力しオプションを使用します。 LIB のコマンドラインの順序に関係なく、すべての入力オブジェクトを組み合わせると/remove と入力し、すべての仕様を処理します。

> [!NOTE]
>  メンバーを削除両方と同じ手順でファイルに抽出できません。 /EXTRACT を使用して、メンバー オブジェクトを抽出します。 まず、/remove と入力しを使用して、もう一度 LIB の実行する必要があります。 この動作は、他の Microsoft 製品で提供される (OMF ライブラリ) の 16 ビット LIB の動作とは異なります。

## <a name="see-also"></a>関連項目

[LIB リファレンス](lib-reference.md)
