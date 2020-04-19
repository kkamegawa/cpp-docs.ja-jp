---
title: LINK からの出力
ms.date: 11/04/2016
f1_keywords:
- link
helpviewer_keywords:
- mapfiles [C++]
- ILK files
- output files [C++], linker
- files [C++], LINK
- .ilk files
- LINK tool [C++], output
- import libraries [C++], creating
- executable files [C++], as linker output
- mapfiles [C++], LINK output
- linker [C++], output files
- DLLs [C++], as linker output
- LINK tool [C++], mapfile
ms.assetid: a98b557c-1947-447a-be1f-616fb45a9580
ms.openlocfilehash: 183f83501d930188032ec4209623ef7cf1a30efa
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62269177"
---
# <a name="link-output"></a>LINK からの出力

Link からの出力には、.exe ファイル、Dll、マップ ファイル、およびメッセージが含まれています。

##  <a name="_core_output_files"></a> 出力ファイル

既定の出力ファイルのリンクからは、.exe ファイルです。 場合、 [/DLL](dll-build-a-dll.md)オプションを指定すると、リンクは、.dll ファイルをビルドします。 出力ファイル名を指定できます、[出力ファイル名 (/out)](out-output-file-name.md)オプション。

増分モードでは、リンクは、プログラムの以降のインクリメンタル ビルドの状態情報を保持するために、.ilk ファイルを作成します。 .Ilk ファイルに関する詳細については、次を参照してください。 [.ilk ファイル](dot-ilk-files-as-linker-input.md)します。 インクリメンタル リンクの詳細については、次を参照してください。、[インクリメンタル リンクを行う (/incremental)](incremental-link-incrementally.md)オプション。

リンクを作成するときが含まれたプログラム (通常は DLL) をエクスポートします、ビルドで .exp ファイルが使用された場合を除きも .lib ファイルを構築。 インポート ライブラリのファイル名を指定できます、 [/IMPLIB](implib-name-import-library.md)オプション。

場合、[マップ ファイルの生成 (/map)](map-generate-mapfile.md)オプションを指定すると、リンクがマップ ファイルを作成します。

場合、[デバッグ情報の生成 (/debug)](debug-generate-debug-info.md)オプションを指定すると、リンクされたプログラムのデバッグ情報を格納する pdb ファイルを作成します。

##  <a name="_core_other_output"></a> その他の出力

入力すると`link`リンク他のコマンド ライン入力なしには、オプション、使用量明細が表示されます。

リンクは著作権およびバージョン メッセージを表示し、コマンド ファイルからの入力をエコーしない限り、[著作権 (/NOLOGO)](nologo-suppress-startup-banner-linker.md)オプションを使用します。

使用することができます、[進行状況メッセージの出力 (/verbose)](verbose-print-progress-messages.md)ビルドに関する追加情報を表示するオプション。

リンク フォーム LNK でエラーおよび警告のメッセージを発行する*nnnn*します。 このエラーのプレフィックスと番号の範囲は LIB、DUMPBIN、および EDITBIN によっても使用されます。

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
