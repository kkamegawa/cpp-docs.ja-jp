---
title: BSCMAKE オプション
description: Microsoft BSCMAKE ユーティリティのコマンドラインオプションへの参照。
ms.date: 02/09/2020
f1_keywords:
- VC.Project.VCBscMakeTool.OutputFile
- VC.Project.VCBscMakeTool.SuppressStartupBanner
- VC.Project.VCBscMakeTool.PreserveSBR
helpviewer_keywords:
- /v BSCMAKE option
- Iu BSCMAKE option
- browse information files (.bsc), content
- /Er BSCMAKE option
- NOLOGO BSCMAKE option
- /s BSCMAKE option
- /Ei BSCMAKE option
- /o BSCMAKE option
- /NOLOGO BSCMAKE option
- /Iu BSCMAKE option
- s BSCMAKE option (/s)
- /Em BSCMAKE option
- Em BSCMAKE option
- Es BSCMAKE option
- files [C++], BSCMAKE
- Er BSCMAKE option
- BSCMAKE, options for controlling files
- controlling BSCMAKE options
- El BSCMAKE option
- /El BSCMAKE option
- /Es BSCMAKE option
- Ei BSCMAKE option
ms.assetid: fa2f1e06-c684-41cf-80dd-6a554835ebd2
ms.openlocfilehash: f0fd0e01d3325267ac175435aab65b5d0a9d47ea
ms.sourcegitcommit: 8414cd91297dea88c480e208c7b5301db9972f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/14/2020
ms.locfileid: "77257794"
---
# <a name="bscmake-options"></a>BSCMAKE オプション

> [!WARNING]
> BSCMAKE は、現在も Visual Studio と共にインストールされていますが、IDE では使用されなくなりました。 Visual Studio 2008 以降、参照情報とシンボル情報は、ソリューションフォルダー内の SQL Server *`.sdf`* ファイルに自動的に格納されます。

ここでは、BSCMAKE を制御するためのオプションを説明します。 一部のオプションでは、特定の情報を除外するか、または含めることによってブラウザー情報ファイルの内容を制御できます。 除外オプションを使用すると、BSCMAKE の実行時間が短縮され、 *`.bsc`* ファイルが小さくなることがあります。 オプション名では大文字と小文字が区別されます ( **/help**と **/nologo**を除く)。

Visual Studio 開発環境内から使用できるのは、 **/nologo**と **/o**だけです。  プロジェクトのプロパティページにアクセスする方法の詳細については、「 [Visual Studio でのC++コンパイラとビルドのプロパティの設定](../working-with-project-properties.md)」を参照してください。

**/Ei (** _ファイル名_... **)** \
指定したインクルード ファイルの内容をブラウザー情報ファイルから除外します。 複数のファイルを指定する場合は、スペースで名前を区切り、名前のリストをかっこで囲みます。 *ファイル名*を1つだけ指定した場合、かっこは必要ありません。 **/Ei**を **/Es**オプションと共に使用して、 **/Es**によって除外されていないファイルを除外します。

**/El**\
ローカル シンボルを除外します。 既定では、ローカル シンボルは含まれます。 ローカルシンボルの詳細については、「 [.Sbr ファイルの作成](creating-an-dot-sbr-file.md)」を参照してください。

**/Em**\
マクロの本体のシンボルを除外します。 ブラウザー情報ファイルにマクロの名前のみを含めるには、 **/Em**を使用します。 既定では、マクロ名とマクロの展開の結果の両方が含められます。

**/Er (** _記号_... **)** \
指定したシンボルをブラウザー情報ファイルから除外します。 複数のシンボル名を指定する場合は、スペースで名前を区切り、名前のリストをかっこで囲みます。 *記号*を1つだけ指定した場合、かっこは不要です。

**/Es**\
絶対パスで指定されたすべてのインクルードファイルを除外するか、INCLUDE 環境変数で指定された絶対パスに格納します。 (通常、これらのファイルはシステムインクルードファイルであり、参照情報ファイルに必要でない可能性のある多くの情報が含まれています)。このオプションでは、パスを指定せず、相対パスを使用して指定したファイル、またはインクルード内の相対パスに存在するファイルは除外されません。 **/Es**と共に **/Ei**オプションを使用して、 **/Es**で除外されないファイルを除外できます。 一部のファイルのみを除外する場合は、 **/Es**ではなく **/Ei**を使用して、除外するファイルを一覧表示します。

**/errorreport:** [**none** &#124; **prompt** &#124; **queue** &#124; **send**] \
このオプションは非推奨とされます。 Windows Vista 以降では、エラー報告は[Windows エラー報告 (WER)](/windows/win32/wer/windows-error-reporting)設定によって制御されます。

**/Help**\
BSCMAKE コマンド ライン構文の簡単な説明を表示します。

**/Iu**\
未参照シンボルを含めます。 既定では、BSCMAKE では、定義されているが参照されていないシンボルは記録されません。 *`.sbr`* ファイルがパックされている場合、コンパイラは参照されていないシンボルを既に削除しているため、このオプションはその入力ファイルには効果がありません。

**/n**\
ノンインクリメンタル ビルドを強制的に実行します。 **/N**を使用して、 *`.bsc`* ファイルが存在するかどうかにかかわらず、ブラウザー情報ファイルの完全なビルドを強制的に実行し、 *`.sbr`* ファイルが切り捨てられないようにします。 「 [BSCMAKE による .Bsc ファイルのビルド方法」を](how-bscmake-builds-a-dot-bsc-file.md)参照してください。

**/Nologo**\
BSCMAKE の著作権メッセージが表示されなくなります。

**/o** *ファイル名*\
ブラウザー情報ファイルの名前を指定します。 既定では、BSCMAKE によって、最初の *`.sbr`* ファイルのベース名と *`.bsc`* の拡張子がブラウザー情報ファイルに付与されます。

**/S (** _ファイル名_... **)** \
指定されたインクルードファイルが最初に検出されたときにそのファイルを処理し、それ以外の場合は除外するように BSCMAKE に指示します。 このオプションを使用すると、ファイル (ヘッダー、 *`.h`* 、 *`.c`* または *`.cpp`* ソースファイルのファイル) がいくつかのソースファイルに含まれているが、毎回プリプロセスディレクティブによって変更されていない場合の処理時間を節約できます。 このオプションは、作成するブラウザー情報ファイルにとって重要ではない方法でファイルが変更された場合に使用します。 複数のファイルを指定するには、名前をスペースで区切り、リストをかっこで囲みます。 *ファイル名*を1つだけ指定した場合、かっこは必要ありません。 インクルードするたびにファイルを除外する場合は、 **/Ei**または **/Es**オプションを使用します。

**/v**\
詳細出力を提供します。これには、処理される各 *`.sbr`* ファイルの名前と、BSCMAKE の完全実行に関する情報が含まれます。

**/?** \
BSCMAKE コマンド ライン構文の簡単な説明を表示します。

次のコマンドラインは、3つの *`.sbr`* ファイルからのメイン .bsc の完全ビルドを実行するよう BSCMAKE に指示します。 このコマンド ラインでは、TOOLBOX.h の重複インスタンスが除外されます。

```cmd
BSCMAKE /n /S toolbox.h /o main.bsc file1.sbr file2.sbr file3.sbr
```

## <a name="see-also"></a>参照

[BSCMAKE リファレンス](bscmake-reference.md)
