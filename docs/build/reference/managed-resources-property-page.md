---
title: '[マネージド リソース] プロパティ ページ'
ms.date: 08/28/2019
f1_keywords:
- VC.Project.VCManagedResourceCompilerTool.ResourceFileName
- VC.Project.VCManagedResourceCompilerTool.OutputFileName
- VC.Project.VCManagedResourceCompilerTool.DefaultLocalizedResources
helpviewer_keywords:
- Managed Resources property page
ms.assetid: 80b80384-ee55-494d-9f0e-907bb98cfc19
ms.openlocfilehash: 14802996e63392bfb5fcc22096ef5f3d9db197c2
ms.sourcegitcommit: e10a5feea193c249ddc5a6faba48e7c6d8784e73
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2019
ms.locfileid: "70177527"
---
# <a name="managed-resources-property-page"></a>[マネージド リソース] プロパティ ページ

**[マネージリソース]** プロパティページでは、/cli プログラムでC++.net リソースを使用するときに、マネージリソースコンパイラ[resgen.exe](/dotnet/framework/tools/resgen-exe-resource-file-generator)の次のプロパティが公開されます。

- **リソース論理名**

   生成された中間 .resources ファイルの*論理名* を指定します。 論理名は、リソースの読み込みに使用される名前です。 論理名が指定されていない場合は、リソース (.resx) ファイル名が論理名として使用されます。

- **出力ファイル名**

   リソース (.resx) ファイルによって決定する最終出力ファイルの名前を指定します。

- **既定のローカライズされたリソース**

   特定の .resx ファイルが既定のリソースまたはサテライト .dll に変更を与えるかどうかを指定します。

**[マネージリソース]** プロパティページにアクセスする方法の詳細については、「 [Visual Studio でのコンパイラおよびビルドプロパティの設定C++ ](../working-with-project-properties.md)」を参照してください。

## <a name="see-also"></a>関連項目

[RC の使用 (RC コマンドライン)](/windows/win32/menurc/using-rc-the-rc-command-line-)<br>
[C++プロジェクトプロパティページのリファレンス](property-pages-visual-cpp.md)<br>
[/ASSEMBLYRESOURCE (マネージド リソースの埋め込み)](assemblyresource-embed-a-managed-resource.md)
