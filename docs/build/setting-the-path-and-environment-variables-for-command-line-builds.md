---
title: コマンドラインビルドのパスと環境変数を設定する
ms.custom: conceptual
ms.date: 07/24/2019
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
ms.openlocfilehash: 6e7882b169805e3c62596341986a83d476ac5ec1
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492147"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>コマンドラインビルドのパスと環境変数を設定する

Microsoft C++ (MSVC) コマンドラインビルドツールには、インストールとビルド構成用にカスタマイズされたいくつかの環境変数が必要です。 Visual Studio C++インストーラーによってワークロードがインストールされると、必要な環境変数を設定するカスタマイズされたコマンドファイル (バッチファイル) が作成されます。 インストーラーは、これらのコマンドファイルを使用して、Windows の [スタート] メニューのショートカットを作成し、開発者コマンドプロンプトウィンドウを開きます。 これらのショートカットでは、特定のビルド構成の環境変数を設定します。 コマンドラインツールを使用する場合は、これらのショートカットのいずれかを実行するか、プレーンコマンドプロンプトウィンドウを開き、カスタムコマンドファイルの1つを実行してビルド構成環境を自分で設定できます。 詳細については、「[コマンドラインからの MSVC ツールセットの使用](building-on-the-command-line.md)」を参照してください。 コマンドファイルをプレーンコマンドプロンプトで使用するには、「[開発者コマンドファイルの場所](building-on-the-command-line.md#developer_command_file_locations)」セクションを参照してください。

MSVC コマンドラインツールは、PATH、TMP、INCLUDE、LIB、および LIBPATH 環境変数を使用します。また、インストールされているツール、プラットフォーム、および Sdk に固有の他の環境変数も使用します。 単純な Visual Studio のインストールでも、20以上の環境変数を設定できます。 これらの環境変数の値はインストールと選択したビルド構成に固有であり、製品の更新プログラムまたはアップグレードによって変更できます。そのため、開発者コマンドプロンプトのショートカットまたは次のいずれかを使用することを強くお勧めします。Windows 環境で自分で設定するのではなく、カスタマイズされたコマンドファイルを設定します。

開発者コマンドプロンプトのショートカットで設定されている環境変数を確認するには、SET コマンドを使用します。 プレーンコマンドプロンプトウィンドウを開き、ベースラインの SET コマンドの出力をキャプチャします。 [開発者コマンドプロンプト] ウィンドウを開き、比較用の SET コマンドの出力をキャプチャします。 Visual Studio IDE に組み込まれているような diff ツールは、環境変数を比較し、開発者コマンドプロンプトで設定されている内容を確認するのに役立ちます。 コンパイラとリンカーによって使用される特定の環境変数の詳細については、「 [CL 環境変数](reference/cl-environment-variables.md)」を参照してください。

> [!NOTE]
>  いくつかのコマンドラインツールまたはツールオプションでは、管理者権限が必要になる場合があります。 使用時にアクセス許可の問題が発生した場合は、**管理者として実行** オプションを使用して 開発者コマンドプロンプト ウィンドウを開くことをお勧めします。 Windows 10 では、右クリックしてコマンドプロンプトウィンドウのショートカットメニューを開き、 **[詳細]** 、 **[管理者として実行]** の順に選択します。

## <a name="see-also"></a>関連項目

[コマンド ラインから MSVC ツールセットを使用する](building-on-the-command-line.md)<br/>
[MSVC リンカーのリファレンス](reference/linking.md)<br/>
[MSVC リンカー オプション](reference/linker-options.md)<br/>
[MSVC コンパイラ リファレンス](reference/compiling-a-c-cpp-program.md)<br/>
[MSVC コンパイラ オプション](reference/compiler-options.md)
