---
title: '方法: カスタム ビルド ツール MSBuild プロジェクトを追加します。'
ms.date: 11/04/2016
helpviewer_keywords:
- 'msbuild (c++), howto: add custom build tools'
ms.assetid: de03899a-371d-4396-9bf9-34f45a65e909
ms.openlocfilehash: 812932d9e668ab5ee0eb75eadbf75be3d791cddb
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220719"
---
# <a name="how-to-add-custom-build-tools-to-msbuild-projects"></a>方法: カスタム ビルド ツール MSBuild プロジェクトを追加します。

カスタム ビルド ツールは、特定のファイルに関連付けられているユーザー定義のコマンド ライン ツールです。

特定のファイルを実行するには、プロジェクト ファイル (.vcxproj) コマンド ライン、追加の入力または出力ファイル、および表示するメッセージを指定します。 場合**MSBuild**出力ファイルが、入力ファイルのファイルに関する期限切れであるメッセージを表示し、コマンド ライン ツールを実行します。 を決定します。

カスタム ビルド ツールが実行される場合を指定するの一方または両方を使用して、`CustomBuildBeforeTargets`と`CustomBuildAfterTargets`プロジェクト ファイル内の XML 要素。 たとえば後、MIDL コンパイラおよび C と C++ コンパイラの前に、カスタム ビルド ツールを実行するを指定する場合があります。 指定、`CustomBuildBeforeTargets`要素は、特定のターゲット実行前に、ツールを実行する、`CustomBuildAfterTargets`要素は、特定のターゲットの後に、ツールを実行するか、2 つのターゲットの実行の間でツールを実行する両方の要素。 カスタム ビルド ツールを実行する前に、既定の場所にいずれの要素が指定されている場合、 **MIDL**ターゲット。

カスタム ビルド ステップとカスタム ビルド ツールで指定された情報を共有、`CustomBuildBeforeTargets`と`CustomBuildAfterTargets`XML 要素。 プロジェクト ファイル内のそれらのターゲット時間が 1 つを指定します。

### <a name="to-add-a-custom-build-tool"></a>カスタム ビルド ツールを追加するには

1. 項目グループをプロジェクト ファイルに追加し、各入力ファイルの項目を追加します。 次のように、項目メタデータとして、コマンド、追加の入力、出力、およびメッセージを指定します。 この例では、faq.txt「という名前」ファイルがプロジェクトと同じディレクトリに存在する前提としています。

    ```
    <ItemGroup>
      <CustomBuild Include="faq.txt">
        <Message>Copying readme...</Message>
        <Command>copy %(Identity) $(OutDir)%(Identity)</Command>
        <Outputs>$(OutDir)%(Identity)</Outputs>
      </CustomBuild>
    </ItemGroup>
    ```

### <a name="to-define-where-in-the-build-the-custom-build-tools-will-execute"></a>実行するカスタム ビルド ツール、ビルドの場所を定義するには

1. プロジェクト ファイルに次のプロパティ グループを追加します。 少なくとも 1 つのターゲットを指定する必要しますが、場合は、ビルド ステップを実行する前に (または後) には、もう一方を省略できます特定のターゲット。 この例は、コンパイルした後、リンクする前に、カスタムの手順を実行します。

    ```
    <PropertyGroup>
      <CustomBuildAfterTargets>ClCompile</CustomBuildAfterTargets>
      <CustomBuildBeforeTargets>Link</CustomBuildBeforeTargets>
    </PropertyGroup>
    ```

## <a name="see-also"></a>関連項目

[チュートリアル: MSBuild を使用した C++ プロジェクトの作成](walkthrough-using-msbuild-to-create-a-visual-cpp-project.md)<br/>
[方法: MSBuild プロジェクトでビルド イベントを使用する](how-to-use-build-events-in-msbuild-projects.md)<br/>
[方法: MSBuild プロジェクトにカスタム ビルド ステップを追加する](how-to-add-a-custom-build-step-to-msbuild-projects.md)
