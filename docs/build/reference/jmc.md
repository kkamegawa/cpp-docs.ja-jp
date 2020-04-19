---
title: /JMC (マイ コードのみデバッグ)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 90fcad40b3322f8a8ae7ffc58875c2850f143138
ms.sourcegitcommit: 0867d648e0955ebad7260b5fbebfd6cd4d58f3c7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68341010"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (マイ コードのみデバッグ)

Visual Studio デバッガーでのネイティブ*マイコードのみ*デバッグのコンパイラサポートを指定します。 このオプションは、Visual Studio がシステム、フレームワーク、ライブラリ、およびその他の非ユーザーの呼び出しをステップオーバーし、[呼び出し履歴] ウィンドウでそれらの呼び出しを折りたたむことができるようにするユーザー設定をサポートしています。 **/JMC**コンパイラオプションは、Visual Studio 2017 バージョン15.8 以降で使用できます。

## <a name="syntax"></a>構文

> **/JMC**\[ **-** ]

## <a name="remarks"></a>Remarks

Visual studio の[マイコードのみ](/visualstudio/debugger/just-my-code)設定では、visual studio デバッガーがシステム、フレームワーク、ライブラリ、およびその他の非ユーザーの呼び出しをステップオーバーするかどうかを指定します。 **/JMC**コンパイラオプションを使用すると、ネイティブC++コードでマイコードのみデバッグをサポートできます。 **/JMC**が有効になっている場合、コンパイラは、関数プロローグ`__CheckForDebuggerJustMyCode`にヘルパー関数の呼び出しを挿入します。 ヘルパー関数には、Visual Studio デバッガーマイコードのみステップ操作をサポートするフックが用意されています。 Visual Studio デバッガーでマイコードのみを有効にするには、メニューバーで [**ツール** > ] **[オプション]** の順に選択し、[**デバッグ** > ] [**全般** > ] **[マイコードのみの有効化]** のオプションを設定します。

**/JMC**オプションを使用するには、コードが C ランタイムライブラリ (CRT) にリンクされ`__CheckForDebuggerJustMyCode`ている必要があります。 CRT は、ヘルパー関数を提供します。 プロジェクトが CRT にリンクしていない場合は、リンカーエラー **LNK2019: 未解決の外部シンボル __ Checkforデバッガインラインコード**が表示されることがあります。 このエラーを解決するには、CRT にリンクするか、 **/JMC**オプションを無効にします。

既定では、 **/JMC**コンパイラオプションはオフになっています。 ただし、Visual Studio 2017 バージョン15.8 以降では、ほとんどの Visual Studio プロジェクトテンプレートでこのオプションが有効になっています。 このオプションを明示的に無効にするには、コマンドラインで **/JMC-** オプションを使用します。 Visual Studio で、[プロジェクトプロパティページ] ダイアログボックスを開き、[**構成プロパティ** >  > ] **[CC++]** 、 **[全般**] プロパティページの **[サポートマイコードのみデバッグ]** プロパティをに変更します。**いいえ**。

詳細については、「 [visual studio でマイコードのみを使用してユーザーコードのみをデバッグするかどうかを指定](/visualstudio/debugger/just-my-code)する」の[ C++マイコードのみ](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code)を参照してください。 visual [studio でのマイコードのみステップC++ ](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/)実行を発表するビジュアルC++チームのブログ記事も参照してください。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. [**構成プロパティ** > ] [**CC++**  > ]、 **[全般]** プロパティページを選択します。

1. **サポートマイコードのみデバッグ**プロパティを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
