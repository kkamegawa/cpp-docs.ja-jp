---
title: コマンド ライン - C++ での MSBuild
ms.date: 12/12/2018
helpviewer_keywords:
- MSBuild
ms.assetid: 7a1be7ff-0312-4669-adf2-5f5bf507d560
ms.openlocfilehash: e95d99cf5c63c824bb9bade8e76bc3ca99079669
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220566"
---
# <a name="msbuild-on-the-command-line---c"></a>コマンド ライン - C++ での MSBuild

一般に、プロジェクトのプロパティを設定して、MSBuild システムを呼び出すには、Visual Studio を使用することをお勧めします。 ただし、使用することができます、 **MSBuild**コマンド プロンプトから直接ツール。 ビルド プロセスは、作成して編集したプロジェクト ファイル (.vcxproj) の情報は、によって制御されます。 プロジェクト ファイルでは、ステージ、条件、およびイベントに基づくビルド オプションがビルドを指定します。 0 を指定するさらに、以上のコマンドライン*オプション*引数。

> **msbuild.exe** [ *project_file* ] [ *options* ]

使用して、 **/target** (または **/t**) と **/property** (または **/p**) 特定のプロパティとターゲットをオーバーライドするコマンド ライン オプションプロジェクト ファイルで指定します。

プロジェクト ファイルの必須の機能は、指定する、*ターゲット*、これは、プロジェクトと、入力と操作の実行に必要な出力に適用される特定の操作。 プロジェクト ファイルでは 1 つ以上のターゲットを指定でき、既定のターゲットを含めることができます。

各ターゲットの 1 つまたは複数のシーケンスから成る*タスク*します。 各タスクは、実行可能なコマンドを 1 つ含む .NET Framework クラスによって表されます。 たとえば、 [CL タスク](/visualstudio/msbuild/cl-task)が含まれています、 [cl.exe](reference/compiling-a-c-cpp-program.md)コマンド。

A*タスク パラメーター*クラス タスクのプロパティは、通常、実行可能なコマンドのコマンド ライン オプションを表します。 たとえば、`FavorSizeOrSpeed`のパラメーター、`CL`タスクに対応する、 **/Os**と **/Ot**コンパイラ オプション。

追加のタスク パラメーターは、MSBuild インフラストラクチャをサポートします。 たとえば、`Sources` タスク パラメーターは、他のタスクで使用できる一連のタスクを指定します。 MSBuild タスクの詳細については、次を参照してください。[タスク リファレンス](/visualstudio/msbuild/msbuild-task-reference)します。

ほとんどのタスクには入力と出力が必要です。これには、ファイル名、パス、文字列パラメーター、数値パラメーター、ブール値パラメーターなどがあります。 たとえば、一般的な入力は、コンパイルする .cpp ソース ファイルの名前です。 重要な入力パラメーターは、たとえば、ビルド構成とプラットフォームを指定する文字列"デバッグ\|Win32"です。 入力と出力は、`Item` 要素に含まれる 1 つ以上のユーザー定義の XML `ItemGroup` 要素で指定します。

プロジェクト ファイルが、ユーザー定義を指定できますも*プロパティ*と`ItemDefinitionGroup`*項目*します。 プロパティと項目は、ビルドで変数として使用できる名前と値のペアを形成します。 ペアの名前のコンポーネントを定義、*マクロ*、値の構成要素を宣言し、*マクロ値*。 プロパティ マクロ $ を使用してアクセス (*名前*) 表記法、および、項目マクロは %(を使用してアクセス*名前*) 表記法。

プロジェクト ファイル内の他の XML 要素では、マクロをテストし、条件に従ってマクロの値を設定したり、ビルドの実行を制御したりできます。 マクロ名とリテラル文字列を連結して、パスとファイル名などの構成要素を生成することもできます。 コマンドラインで、 **/property**オプションを設定またはプロジェクトのプロパティをオーバーライドします。 コマンド ラインで項目を参照することはできません。

MSBuild システムでは、あるターゲットを、条件に従って別のターゲットの前または後に実行できます。 また、ターゲットで使用されるファイルが出力されるファイルよりも新しいかどうかに基づいて、ターゲットをビルドすることもできます。

MSBuild の詳細についてを参照してください。

- [MSBuild](/visualstudio/msbuild/msbuild)概要の MSBuild の概念です。

- [MSBuild リファレンス](/visualstudio/msbuild/msbuild-reference)MSBuild システムに関する情報を参照します。

- [プロジェクト ファイル スキーマ リファレンス](/visualstudio/msbuild/msbuild-project-file-schema-reference)MSBuild XML スキーマの要素、属性、および親と子要素と共に一覧表示されます。 特に注意してください、 [ItemGroup](/visualstudio/msbuild/itemgroup-element-msbuild)、 [PropertyGroup](/visualstudio/msbuild/propertygroup-element-msbuild)、[ターゲット](/visualstudio/msbuild/target-element-msbuild)、および[タスク](/visualstudio/msbuild/task-element-msbuild)要素。

- [コマンド ライン リファレンス](/visualstudio/msbuild/msbuild-command-line-reference)コマンドライン引数と msbuild.exe で使用できるオプションについて説明します。

- [タスクのリファレンス](/visualstudio/msbuild/msbuild-task-reference)について説明する MSBuild タスク。 これらのタスクでは、Visual C に固有に特に注意してください。[BscMake タスク](/visualstudio/msbuild/bscmake-task)、 [CL タスク](/visualstudio/msbuild/cl-task)、 [CPPClean タスク](/visualstudio/msbuild/cppclean-task)、 [LIB タスク](/visualstudio/msbuild/lib-task)、[タスク リンク](/visualstudio/msbuild/link-task)、 [MIDL タスク](/visualstudio/msbuild/midl-task)、 [MT タスク](/visualstudio/msbuild/mt-task)、 [RC タスク](/visualstudio/msbuild/rc-task)、 [SetEnv タスク](/visualstudio/msbuild/setenv-task)、 [VCMessage タスク](/visualstudio/msbuild/vcmessage-task)

## <a name="in-this-section"></a>このセクションの内容

|用語|定義|
|----------|----------------|
|[チュートリアル: MSBuild を使用した C++ プロジェクトの作成](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)|Visual Studio を作成する方法を示しますC++プロジェクトを使用して**MSBuild**します。|
|[方法: MSBuild プロジェクトでビルド イベントを使用する](how-to-use-build-events-in-msbuild-projects.md)|ビルドのビルド ステージで発生するアクションを指定する方法を示します: ビルドの開始前にリンクの手順を開始する前にまたは、ビルドが終了した後。|
|[方法: MSBuild プロジェクトにカスタム ビルド ステップを追加する](how-to-add-a-custom-build-step-to-msbuild-projects.md)|ビルドのシーケンスにユーザー定義のステージを追加する方法を示します。|
|[方法: MSBuild プロジェクトにカスタム ビルド ツールを追加する](how-to-add-custom-build-tools-to-msbuild-projects.md)|ビルド ツールを特定のファイルに関連付ける方法を示します。|
|[方法: カスタム ツールをプロジェクト プロパティに統合する](how-to-integrate-custom-tools-into-the-project-properties.md)|プロジェクトのプロパティにカスタム ツールのオプションを追加する方法を示します。|
|[方法: ターゲット フレームワークおよびプラットフォームのツールセットを変更する](how-to-modify-the-target-framework-and-platform-toolset.md)|複数のフレームワークまたはツールセットのプロジェクトをコンパイルする方法を示します。|

## <a name="see-also"></a>関連項目

[コマンド ラインから MSVC ツールセットを使用する](building-on-the-command-line.md)
