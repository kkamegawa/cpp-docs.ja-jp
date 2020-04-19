---
title: '方法: MSBuild プロジェクトにカスタム ビルド ステップを追加する'
ms.date: 10/16/2019
helpviewer_keywords:
- 'msbuild (c++), howto: add a custom build step'
ms.assetid: a20a0c47-4df4-4754-a1f0-a94a99958916
ms.openlocfilehash: 78d40a5b4a02fe9b065bbbdde33afc6180d75381
ms.sourcegitcommit: 9aab425662a66825772f091112986952f341f7c8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/16/2019
ms.locfileid: "72444916"
---
# <a name="how-to-add-a-custom-build-step-to-msbuild-projects"></a>方法: MSBuild プロジェクトにカスタム ビルド ステップを追加する

カスタムビルドステップは、ビルド内のユーザー定義の手順です。 カスタムビルドステップは、標準のコンパイルまたはリンクツールのステップなど、他の*コマンドツール*ステップと同様に動作します。

プロジェクトファイル (.vcxproj) でカスタムビルドステップを指定します。 このステップでは、実行するコマンドライン、追加の入力ファイルまたは出力ファイル、および表示するメッセージを指定できます。 入力ファイルに関して、 **MSBuild**によって出力ファイルが古くなっていると判断されると、メッセージが表示され、コマンドが実行されます。

ビルドターゲットのシーケンスにおけるカスタムビルドステップの場所を指定するには、プロジェクトファイルで `CustomBuildAfterTargets` と `CustomBuildBeforeTargets` の両方の XML 要素を使用します。 たとえば、カスタムビルドステップをリンクツールのターゲットの後、マニフェストツールのターゲットの前に実行するように指定できます。 使用可能なターゲットの実際のセットは、特定のビルドによって異なります。

特定のターゲットを実行する前にカスタムビルドステップを実行するには、`CustomBuildBeforeTargets` 要素を指定します。特定のターゲットの実行後にステップを実行する場合は `CustomBuildAfterTargets` 要素、2つの隣接するターゲット間でステップを実行するには、両方の要素を指定します。 どちらの要素も指定されていない場合、カスタムビルドツールは既定の場所 (**リンク**ターゲットの後) で実行されます。

カスタムビルドステップとカスタムビルドツールは、`CustomBuildBeforeTargets` および `CustomBuildAfterTargets` の XML 要素で指定された情報を共有します。 したがって、プロジェクトファイル内でこれらのターゲットを1回だけ指定してください。

### <a name="to-define-what-is-executed-by-the-custom-build-step"></a>カスタムビルドステップによって実行される内容を定義するには

1. プロパティグループをプロジェクトファイルに追加します。 このプロパティグループで、次の例に示すように、コマンド、その入力と出力、およびメッセージを指定します。 この例では、 [「チュートリアル: MSBuild を使用したプロジェクトのC++作成](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)」で作成したメイン .cpp ファイルから .cab ファイルを作成します。

    ```
    <ItemDefinitionGroup>
      <CustomBuildStep>
        <Command>makecab.exe $(ProjectDir)main.cpp $(TargetName).cab</Command>
        <Outputs>$(TargetName).cab</Outputs>
        <Inputs>$(ProjectDir)main.cpp</Inputs>
      </CustomBuildStep>
    </ItemDefinitionGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-step-will-execute"></a>ビルド内でカスタムビルドステップが実行される場所を定義するには

1. 次のプロパティグループをプロジェクトファイルに追加します。 両方のターゲットを指定することも、特定のターゲットの前または後にカスタムステップを実行するだけの場合は、省略することもできます。 この例では、コンパイル手順の後、リンク手順の前にカスタム手順を実行するように**MSBuild**に指示します。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>関連項目

[チュートリアル: MSBuild を使用したC++プロジェクトの作成](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[方法: MSBuild プロジェクトでビルド イベントを使用する](how-to-use-build-events-in-msbuild-projects.md)<br/>
[方法: MSBuild プロジェクトにカスタム ビルド ツールを追加する](how-to-add-custom-build-tools-to-msbuild-projects.md)
