---
title: /Zg (関数プロトタイプの生成)
ms.date: 11/04/2016
f1_keywords:
- /zg
helpviewer_keywords:
- Zg compiler option [C++]
- /Zg compiler option [C++]
- function prototypes, generate function prototypes compiler option
- -Zg compiler option [C++]
- generate function prototypes compiler option
ms.assetid: c8df1b46-24ff-46f2-8356-e0a144b21dd2
ms.openlocfilehash: 591460b78a461aa2e33f873b79d6dcec0277f99f
ms.sourcegitcommit: 7d64c5f226f925642a25e07498567df8bebb00d4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2019
ms.locfileid: "65446201"
---
# <a name="zg-generate-function-prototypes"></a>/Zg (関数プロトタイプの生成)

削除されました。 ソース ファイルで定義された各関数の関数プロトタイプを作成しますが、ソース ファイルはコンパイルされません。

## <a name="syntax"></a>構文

```
/Zg
```

## <a name="remarks"></a>Remarks

このコンパイラ オプションは使用できなくなりました。 Visual Studio 2015 で削除されました。 このページは、古いバージョンの Visual Studio のユーザーのままです。

関数プロトタイプには、この関数の戻り値の型と引数の型リストが含まれます。 引数の型リストは、関数の仮パラメーターの型から作成されます。 ソース ファイル内に既に存在する関数プロトタイプは無視されます。

プロトタイプのリストは、標準出力に書き込まれます。 このリストは、関数の実際の引数と仮パラメーターに互換性があることを確認するのに役立ちます。 標準出力をファイルにリダイレクトすることで、リストを保存できます。 その後 **#include** を使って、関数プロトタイプのリストをソース ファイルの一部にすることができます。 これにより、コンパイラは引数の型チェックを実行できます。

**/Zg** オプションを使っており、構造体型、列挙型、共用体型 (またはそのような型へのポインター) を持つ仮パラメーターがプログラムに含まれる場合、各構造体型、列挙型、共用体型の宣言にはタグ (名前) が必要です。 次の例で、タグ名は `MyStruct`です。

```C
// Zg_compiler_option.c
// compile with: /Zg
typedef struct MyStruct { int i; } T2;
void f2(T2 * t) {}
```

**/Zg**オプションは Visual Studio 2005 で非推奨とされました、Visual Studio 2015 で削除されました。 MSVC コンパイラには、サポート、C スタイルの古いコードが削除されました。 非推奨のコンパイラ オプションの一覧は、次を参照してください。**非推奨とされた削除済みのコンパイラ オプション**で[Compiler Options Listed by Category](compiler-options-listed-by-category.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **[C/C++]** フォルダーをクリックします。

1. **[コマンド ライン]** プロパティ ページをクリックします。

1. **[追加のオプション]** ボックスにコンパイラ オプションを入力します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
