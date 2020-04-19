---
title: '方法: 64ビット、 C++ x64 プラットフォームを対象とするように Visual Studio プロジェクトを構成する'
ms.date: 11/04/2016
helpviewer_keywords:
- platforms [C++], 64-bit
- 64-bit programming [C++], configuring projects
- project configurations [C++]
ms.assetid: 2b9ae001-df36-4750-83b2-982145d632ad
ms.openlocfilehash: 762fd5d6ddbb55713cf2fc5e34cb33fb91b08eb9
ms.sourcegitcommit: ce3393846c86e7905ff0c86e4cd6610476809585
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68492235"
---
# <a name="how-to-configure-visual-studio-c-projects-to-target-64-bit-x64-platforms"></a>方法: 64ビット、 C++ x64 プラットフォームを対象とするように Visual Studio プロジェクトを構成する

Visual Studio IDE のプロジェクト構成を使用して、64ビットのC++ x64 プラットフォームを対象とするようにアプリケーションを設定できます。 Win32 プロジェクトの設定を 64 ビットのプロジェクト構成に移行することもできます。

### <a name="to-set-up-c-applications-to-target-64-bit-platforms"></a>64 ビットのプラットフォームを対象とするように C++ アプリケーションを設定するには

1. 構成する C++ プロジェクトを開きます。

1. そのプロジェクトのプロパティ ページが開きます。 詳しくは、「[Visual Studio で C++ コンパイラとビルド プロパティを設定する](working-with-project-properties.md)」をご覧ください。

   > [!NOTE]
   > .Net プロジェクトの場合は、[プロジェクト名 **\<> プロパティページ**] ダイアログボックスで **[構成プロパティ]** ノードまたはその子ノードの1つが選択されていることを確認します。それ以外の場合は、 **[Configuration Manager]** ボタンがそのまま使用されます。なく.

1. **[構成マネージャー]** ボタンを選択して **[構成マネージャー]** ダイアログ ボックスを開きます。

1. **[アクティブソリューションプラットフォーム]** ドロップダウンリストで、[  **\<新規] を選択します。>** オプションを選択すると、 **[新しいソリューションプラットフォーム]** ダイアログボックスが開きます。

1. **[新しいプラットフォーム]** ボックスの一覧で、64ビットのターゲットプラットフォームを選択します。

   > [!NOTE]
   > **[新しいソリューション プラットフォーム]** ダイアログ ボックスで、 **[設定のコピー元]** オプションを使用して、既存のプロジェクト設定を新しい 64 ビットのプロジェクト構成にコピーします。

1. **[OK]** を選択します。 前の手順で選択したプラットフォームが **[構成マネージャー]** ダイアログ ボックスの **[アクティブ ソリューション プラットフォーム]** の下に表示されます。

1. **[Configuration Manager]** ダイアログボックスの **[閉じる]** ボタンをクリックし、[  **\<Projectname > プロパティページ**] ダイアログボックスの **[OK]** をクリックします。

### <a name="to-copy-win32-project-settings-into-a-64-bit-project-configuration"></a>Win32 プロジェクトの設定を 64 ビットのプロジェクト構成に移行するには

- 64 ビットのプラットフォームを対象とするプロジェクトの設定中に **[新しいソリューション プラットフォーム]** ダイアログ ボックスが開いたら、 **[設定のコピー元]** ドロップダウン リストで **[Win32]** を選択します。 これらのプロジェクト設定は、プロジェクト レベルで自動的に更新されます。

  - [/MACHINE](reference/machine-specify-target-platform.md) リンカー オプションは **/MACHINE:X64**に設定されます。

  - **[出力の登録]** はオフにされます。 詳細については、「 [Linker Property Pages](reference/linker-property-pages.md)」を参照してください。

  - **[ターゲット環境]** は **/env x64**に設定されます。 詳細については、「 [MIDL プロパティページ](reference/midl-property-pages.md)」を参照してください。

  - **[パラメーターの確認]** はクリアされ、既定値にリセットされます。 詳細については、「 [MIDL プロパティページ](reference/midl-property-pages.md)」を参照してください。

  - **[デバッグ情報の形式]** が Win32 プロジェクト構成で **/ZI** に設定された場合、64 ビットのプロジェクト構成では **/Zi** に設定されます。 詳細については、「[/Z7、/Zi、/ZI (デバッグ情報の形式)](reference/z7-zi-zi-debug-information-format.md)」を参照してください。

  > [!NOTE]
  > プロジェクトのプロパティは、ファイル レベルでオーバーライドされる場合、いずれも変更されません。

## <a name="see-also"></a>関連項目

[64 ビットの x64 ターゲット用に C++ プロジェクトを構成する](configuring-programs-for-64-bit-visual-cpp.md)<br/>
[64 ビット アプリケーションをデバッグする](/visualstudio/debugger/debug-64-bit-applications)
