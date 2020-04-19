---
title: /VERBOSE (進行状況メッセージの出力)
ms.date: 06/13/2019
f1_keywords:
- /verbose
- VC.Project.VCLinkerTool.ShowProgress
helpviewer_keywords:
- -VERBOSE linker option
- linking [C++], session progress information
- Print Progress Messages linker option
- linker [C++], output dependency information
- /VERBOSE linker option
- dependencies [C++], dependency information in linker output
- VERBOSE linker option
ms.assetid: 9c347d98-4c37-4724-a39e-0983934693ab
ms.openlocfilehash: bbf7b5966c741535f26202979cbfd71f839cc537
ms.sourcegitcommit: e79188287189b76b34eb7e8fb1bfe646bdb586bc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/14/2019
ms.locfileid: "67141663"
---
# <a name="verbose-print-progress-messages"></a>/VERBOSE (進行状況メッセージの出力)

リンク プロセス中に進行状況メッセージを出力します。

## <a name="syntax"></a>構文

> **/VERBOSE**\[ **:** {**CLR**|**ICF**|**INCR** | **LIB**|**REF**|**SAFESEH**|**UNUSEDDELAYLOAD**| **UNUSEDLIBS**}\]

## <a name="remarks"></a>Remarks

リンカーへのリンクのセッションの進行状況に関する情報を送信する、**出力**ウィンドウ。 、コマンドラインでは、情報は、を標準出力に送信され、ファイルにリダイレクトできます。

| オプション | 説明 |
| ------------ | ----------------- |
| /VERBOSE | リンク プロセスに関する詳細情報を表示します。 |
| /VERBOSE:CLR | オブジェクトとメタデータを使用してコンパイルする特定のリンカー動作についての情報を表示します。 [/clr](clr-common-language-runtime-compilation.md)します。 |
| /VERBOSE:ICF | 使用に起因するリンカー動作についての情報が表示されます[/OPT:ICF](opt-optimizations.md)します。 |
| /VERBOSE:INCR | インクリメンタル リンク プロセスに関する情報を表示します。 |
| /VERBOSE:LIB | 検索されたライブラリだけを示す進行状況メッセージを表示します。<br/> 表示される情報には、ライブラリの検索のプロセスが含まれています。 ライブラリ、およびシンボルを参照するオブジェクトの一覧から各ライブラリとオブジェクト名 (完全パス) が一覧表示、シンボルを解決します。 |
| /VERBOSE:REF | 使用に起因するリンカー動作についての情報が表示されます[/OPT:REF](opt-optimizations.md)します。 |
| /VERBOSE:SAFESEH | 安全なの構造化例外処理と互換性があるモジュールに関する情報が表示されます[/SAFESEH](safeseh-image-has-safe-exception-handlers.md)が指定されていません。 |
| /VERBOSE: UNUSEDDELAYLOAD | 遅延に関する情報を表示には、イメージが作成されるときに使用されるシンボルを持たない Dll が読み込まれます。 |
| /VERBOSE:UNUSEDLIBS | イメージの作成時に使用されていないライブラリ ファイルに関する情報を表示します。 |

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、[Visual Studio での C++ コンパイラとビルド プロパティの設定](../working-with-project-properties.md)に関するページを参照してください。

1. 選択、**構成プロパティ** > **リンカー** > **コマンドライン**プロパティ ページ。

1. 追加するには、オプション、**追加オプション**ボックス。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ShowProgress%2A>

## <a name="see-also"></a>関連項目

[MSVC リンカーのリファレンス](linking.md)<br/>
[MSVC リンカー オプション](linker-options.md)
