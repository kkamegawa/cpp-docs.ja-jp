---
title: /Qimprecise_fwaits (try ブロック内部の fwaits を削除する)
ms.date: 11/04/2016
f1_keywords:
- /Qimprecise_fwaits
helpviewer_keywords:
- -Qimprecise_fwaits compiler option (C++)
- /Qimprecise_fwaits compiler option (C++)
ms.assetid: b1501f21-7e08-4fea-95e8-176ec03a635b
ms.openlocfilehash: 40683382686ea64a80563f3f29b7d3523f4144a8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62319591"
---
# <a name="qimprecisefwaits-remove-fwaits-inside-try-blocks"></a>/Qimprecise_fwaits (try ブロック内部の fwaits を削除する)

削除、`fwait`コマンドの内部`try`ブロックを使用する場合、 [/fp: を除く](fp-specify-floating-point-behavior.md)コンパイラ オプション。

## <a name="syntax"></a>構文

```
/Qimprecise_fwaits
```

## <a name="remarks"></a>Remarks

このオプションには効果がない場合は **/fp: 除く**も指定されていません。 指定した場合、 **/fp: を除く**オプション、コンパイラが挿入されます、`fwait`コマンド内のコードの各行の周りを`try`ブロック。 これにより、コンパイラは、特定の例外が発生したコード行を識別できます。 **/Qimprecise_fwaits**内部削除`fwait`手順については、周囲の待機のみを残して、`try`ブロックします。 これは、パフォーマンスは向上しますが、コンパイラは指定できる`try`ブロック、例外では、どの行が発生します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[/Q オプション (低水準の操作)](q-options-low-level-operations.md)<br/>
[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
