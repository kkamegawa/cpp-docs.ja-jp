---
title: ビルド イベントの指定
ms.date: 12/28/2017
f1_keywords:
- VC.Project.IVCEventTool.CommandLine
- VC.Project.IVCEventTool.ExcludedFromBuild
- VC.Project.IVCEventTool.Description
helpviewer_keywords:
- Pre-Link event
- build events [C++], specifying
- custom build steps [C++], build events
- builds [C++], events
- events [C++], build
- builds [C++], customizing C++
- build events [C++]
- post-build events
ms.assetid: 788a6c18-2dbe-4a49-8cd6-86c1ad7a95cc
ms.openlocfilehash: c8097e013f934c45b8e3860b8377bdb2bdb9d9a0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315236"
---
# <a name="specifying-build-events"></a>ビルド イベントの指定

ビルド開始前、リンク プロセス前、ビルド終了後に実行するコマンドを指定する目的で、ビルド イベントを使用できます。

ビルド イベントは、ビルド プロセスにおいてビルドがこれらのポイントに正常に達した場合にのみ実行されます。 ビルドでエラーが発生した場合、*ビルド後*イベントは発生しません。リンク段階前にエラーが発生した場合、*リンク前*イベントも*ビルド後*イベントも発生しません。 また、ファイルをリンクする必要がない場合、*リンク前*イベントは発生しません。 リンク手順が含まれないプロジェクトでも、*リンク前*イベントを利用できません。

ファイルをビルドする必要がない場合、ビルド イベントは発生しません。

ビルド イベントに関する全般情報については、「[カスタム ビルド ステップとビルド イベントについて](understanding-custom-build-steps-and-build-events.md)」を参照してください。

### <a name="to-specify-a-build-event"></a>ビルド イベントを指定するには

1. **ソリューション エクスプローラー**で、ビルド イベントを指定するプロジェクトを選択します。

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](working-with-project-properties.md)します。

1. **[ビルド イベント]** フォルダーで、ビルド イベント プロパティ ページを選択します。

1. ビルド イベントに関連付けられたプロパティを指定します。

   - **[コマンド ライン]** で、コマンド プロンプトの場合と同様にコマンドを指定します。 有効なコマンドまたはバッチ ファイルと必要な入力ファイルまたは出力ファイルがあればそれを指定します。 後続のコマンドがすべて確実に実行されるように、バッチ ファイル名の前に **call** バッチ コマンドを指定します。

      MSBuild マクロを利用すれば、複数の入力ファイルと出力ファイルを数式で指定できます。 ファイルの場所または一連のファイルの名前を指定する方法については、次を参照してください。[用マクロの一般的なコマンドとプロパティのビルド](reference/common-macros-for-build-commands-and-properties.md)します。

      '%' は MSBuild に予約されている文字です。環境変数を指定する場合、エスケープ文字 **%** をそれぞれ、16 進数エスケープ シーケンス **%25** に変更してください。 たとえば、**%WINDIR%** を **%25WINDIR%25** に変更します。 MSBuild は **%25** シーケンスをそれぞれ **%** 文字に変更し、それから環境変数にアクセスします。

   - **[説明]** には、このイベントの説明を入力します。 このイベントが発生したとき、**[出力]** ウィンドウにこの説明が表示されます。

   - **[ビルドから除外]** には、イベントを実行しない場合、**[はい]** を指定します。

## <a name="see-also"></a>関連項目

[カスタム ビルド ステップとビルド イベントについて](understanding-custom-build-steps-and-build-events.md)<br>
[ビルドのコマンドとプロパティの共通マクロ](reference/common-macros-for-build-commands-and-properties.md)<br>
[ビルドのカスタマイズのトラブルシューティング](troubleshooting-build-customizations.md)
