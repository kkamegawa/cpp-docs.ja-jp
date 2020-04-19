---
title: '方法: カスタム ツールをプロジェクトのプロパティに統合する'
ms.date: 05/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: integrate custom tools'
ms.assetid: f32d91a4-44e9-4de3-aa9a-1c7f709ad2ee
ms.openlocfilehash: 0c0233ad6715a3adb7d47f021a87207f288d5139
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837028"
---
# <a name="how-to-integrate-custom-tools-into-the-project-properties"></a>方法: カスタム ツールをプロジェクトのプロパティに統合する

基になる XML スキーマ ファイルを作成することにより、Visual Studio の **[プロパティ ページ]** ウィンドウにカスタム ツール オプションを追加できます。

**[プロパティ ページ]** ウィンドウの **[構成プロパティ]** セクションには、"*ルール*" と呼ばれる設定グループが表示されます。 すべてのルールには、ツールまたは機能のグループの設定が含まれています。 たとえば、 **[リンカー]** ルールには、リンカー ツールの設定が含まれています。 ルールの設定は、"*カテゴリ*" に分かれている場合があります。

このドキュメントでは、カスタム ツールのプロパティが含まれるファイルを設定ディレクトリに作成して、Visual Studio の起動時にプロパティが読み込まれるようにする方法について説明します。 ファイルを変更する方法については、Visual Studio プロジェクト チーム ブログの「[Platform Extensibility Part 2 (プラットフォームの機能性第 2 部)](https://blogs.msdn.microsoft.com/vsproject/2009/06/18/platform-extensibility-part-2/)」をご覧ください。

### <a name="to-add-or-change-project-properties"></a>プロジェクトのプロパティを追加または変更するには

1. XML エディターで XML ファイルを作成します。

1. Visual Studio の `VCTargets\1033` フォルダーにファイルを保存します。 インストールされている Visual Studio のエディションおよび言語ごとにパスが異なります。 たとえば、Visual Studio 2019 Community Edition 英語版の既定のフォルダー パスは `C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\Common7\IDE\VC\VCTargets` になります。 言語と Visual Studio のエディションに合わせてパスを調整します。 **[プロパティ ページ]** ウィンドウのすべてのルールは、このフォルダー内の XML ファイルによって表されます。 ファイルの名前がフォルダー内で一意になっていることを確認します。

1. `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>\cl.xml` (またはお使いのパス) の内容をコピーし、変更を保存しないで閉じた後、その内容を新しい XML ファイルに貼り付けます。 任意の XML スキーマ ファイルを使用できます。これは、作業を始めるときのテンプレートとして使うだけです。

1. 新しい XML ファイルで、必要に応じて内容を変更します。 ファイルの先頭にある **Rule Name** と **Rule.DisplayName** を必ず変更します。

1. 変更を保存してファイルを閉じます。

1. `%ProgramFiles%\Microsoft Visual Studio\2019\<VS Edition>\Common7\IDE\VC\VCTargets\<LCID>` (またはお使いの保存場所) の XML ファイルは、Visual Studio の起動時に読み込まれます。 そのため、新しいファイルをテストするには、Visual Studio を再起動します。

1. **ソリューション エクスプローラー**で、プロジェクトを右クリックして、 **[プロパティ]** をクリックします。 **[プロパティ ページ]** ウィンドウの左側のウィンドウで、ご自分のルールの名前を持つ新しいノードがあることを確認します。

## <a name="see-also"></a>関連項目

[コマンド ラインでの MSBuild - C++](msbuild-visual-cpp.md)
