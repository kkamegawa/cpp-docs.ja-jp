---
title: /diagnostics (コンパイラの診断オプション)
ms.date: 11/11/2016
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6b7d043e00204fa191530f03bbed069d71a25fc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293824"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/diagnostics (コンパイラの診断オプション)

使用して、 **/diagnostics**コンパイラ オプションをエラーと警告場所の情報の表示形式を指定します。

## <a name="syntax"></a>構文

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>Remarks

Visual Studio 2017 以降、このオプションはサポートされています。

**/Diagnostics**コンパイラ オプションは、エラーおよび警告情報の表示を制御します。

**/Diagnostics:classic**オプションの既定値は、問題が見つかった行番号のみを報告します。

**/Diagnostics:column**オプションにも、問題が検出された場所の列が含まれています。 特定の言語コンストラクトまたは問題の原因となっている文字を特定できます。

**/Diagnostics:caret**オプションには、問題が見つかり、キャレット (^) を行のコードで問題が検出された場所の下に配置場所の列が含まれています。

場合によっては、コンパイラが発生した問題を検出しないください。 たとえば、不足しているセミコロンに検出できない可能性まで、他の予期しないシンボルが発生しました。 列が報告され、キャレットは、コンパイラは検出する何らかの問題がエラーが発生していないことが、修正を行う必要がありますに配置されます。

**/Diagnostics**オプションは、Visual Studio 2017 以降を使用します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの開く**プロパティ ページ** ダイアログ ボックス。

1. **構成プロパティ**、展開、 **C/C++** フォルダーを選択し、**全般**プロパティ ページ。

1. ドロップダウン コントロールを使用して、**診断形式**フィールド、診断を選択するオプションが表示されます。 選択**OK**または**適用**変更を保存します。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
