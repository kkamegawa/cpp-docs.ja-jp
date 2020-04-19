---
title: '[カスタム ビルド ステップ] プロパティ ページ: 全般'
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCustomBuildStep.AdditionalInputs
- VC.Project.VCCustomBuildStep.CustomBuildAfterTargets
- VC.Project.VCCustomBuildStep.CustomBuildBeforeTargets
- VC.Project.VCCustomBuildStep.Outputs
- VC.Project.VCCustomBuildStep.Message
- VC.Project.VCCustomBuildStep.Command
helpviewer_keywords:
- project properties, custom build step
- custom build step (general)
ms.assetid: bd319741-0491-46c4-a428-7c61b4b46a02
ms.openlocfilehash: 329923140cf5a8f05e5c032ddb9e25c0ea45ec2a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273080"
---
# <a name="custom-build-step-property-page-general"></a>[カスタム ビルド ステップ] プロパティ ページ: 全般

プロジェクトにおけるプロジェクト構成とターゲット プラットフォームの組み合わせごとに、プロジェクトをビルドするときに実行するカスタム ステップを指定できます。

このページの Linux バージョンについては、「[カスタム ビルド ステップのプロパティ (Linux C++)](../../linux/prop-pages/custom-build-step-linux.md)」を参照してください。

## <a name="uielement-list"></a>UIElement の一覧

- **コマンド ライン**

   カスタム ビルド ステップによって実行されるコマンド。

- **説明**

   カスタム ビルド ステップを実行するときに表示されるメッセージ。

- **出力**

   カスタム ビルド ステップが生成する出力ファイル。 この設定は、インクリメンタル ビルドが正しく機能するために必要です。

- **追加の依存ファイル**

   カスタム ビルド ステップで使用する追加の入力ファイルの、セミコロンで区切られた一覧。

- **[以後に実行] および [以前に実行]**

   ビルド プロセスでカスタム ビルド ステップが実行されるタイミングを、表示されているターゲットを基準にして定義します。 最もよく表示されるターゲットは BuildGenerateSources、BuildCompile、および BuildLink です。これらはビルド プロセスの主なステップを表しています。 また、Midl、CLCompile、および Link もよく表示されるターゲットです。

- **出力をコンテンツとして扱う**

   このオプションは、.appx パッケージにすべてのコンテンツ ファイルが含まれるユニバーサル Windows プラットフォームまたは Windows Phone アプリに対してのみ意味を持ちます。

### <a name="to-specify-a-custom-build-step"></a>カスタム ビルド ステップを指定するには

1. メニュー バーで、**[プロジェクト]**、**[プロパティ]** の順に選びます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[プロパティ ページ]** ダイアログ ボックスで、**[構成プロパティ]**、**[カスタム ビルド ステップ]**、**[全般]** ページの順に移動します。

1. 設定を変更します。

## <a name="see-also"></a>関連項目

[C++ プロジェクト プロパティ ページの参照](property-pages-visual-cpp.md)
