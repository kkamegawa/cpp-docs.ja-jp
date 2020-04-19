---
title: /Wp64 (64 ビット移植性の問題の検出)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
ms.openlocfilehash: 5a3cdaf85fa4dc05ece54fc630cb69fc93650e6b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316549"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (64 ビット移植性の問題の検出)

このコンパイラ オプションは廃止されました。 Visual Studio 2013 より前の Visual Studio のバージョンでは、このオプションは、 [__w64](../../cpp/w64.md) キーワードでもマークされている型の 64 ビット移植性の問題を検出します。

## <a name="syntax"></a>構文

```
/Wp64
```

## <a name="remarks"></a>Remarks

既定では、Visual Studio 2013、Visual Studio のバージョンでは、 **/Wp64** 32 ビット x86 ビルド MSVC コンパイラでコンパイラ オプションはオフです、コードの MSVC コンパイラでビルドする 64 ビット、x64 およびコード。

> [!IMPORTANT]
>  [/Wp64](wp64-detect-64-bit-portability-issues.md) コンパイラ オプションと [__w64](../../cpp/w64.md) キーワードは、Visual Studio 2010 および Visual Studio 2012 で非推奨となり、Visual Studio 2013 以降ではサポートされません。 このスイッチを使用するプロジェクトを変換すると、変換中にスイッチは移行されません。 このオプションを Visual Studio 2010 または Visual Studio 2012 で使用するには、プロジェクト プロパティの **[コマンド ライン]** セクションの **[追加オプション]** で、コンパイラ スイッチを入力する必要があります。 コマンド ラインから **/Wp64** コンパイラ オプションを使用すると、コンパイラはコマンド ラインの警告 D9002 を発行します。 64 ビット移植に関する問題を検出するためにこのオプションとキーワードを使用する代わりに、64 ビット プラットフォームを対象とする MSVC コンパイラを使用し、指定、 [/W4](compiler-option-warning-level.md)オプション。 詳細については、次を参照してください。 [64 ビット、x64 ターゲットで構成する C++ プロジェクト](../configuring-programs-for-64-bit-visual-cpp.md)します。

次の型の変数は、64 ビット オペレーティング システムで使用されている場合と同様に、32 ビットのオペレーティング システムでテストされます。

- int

- long

- pointer

通常 64 ビット、x64 を構築するコンパイラを使用して、アプリケーションをコンパイルする場合、コードだけを無効にできます **/Wp64** 32 ビットのコンパイル時に、64 ビット コンパイラでは、すべての問題を検出するためです。 対象の Windows の 64 ビットのオペレーティング システムをする方法の詳細については、次を参照してください。 [64 ビット、x64 ターゲットで構成する C++ プロジェクト](../configuring-programs-for-64-bit-visual-cpp.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。

   詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **/Wp64** を含めるよう **[詳細オプション]** ボックスを変更します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[64 ビット、x64 用の C++ プロジェクトの構成のターゲット](../configuring-programs-for-64-bit-visual-cpp.md)
