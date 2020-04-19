---
title: /H (外部名の長さの制限)
ms.date: 09/05/2018
f1_keywords:
- /h
helpviewer_keywords:
- public name length
- /H compiler option [C++]
- H compiler option [C++]
- external names
- -H compiler option [C++]
ms.assetid: de701dd3-ed04-4c88-8195-960d2520ec2e
ms.openlocfilehash: bdd3da8d3a5165262c00bc3475122e31f5770726
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270394"
---
# <a name="h-restrict-length-of-external-names"></a>/H (外部名の長さの制限)

非推奨。 外部名の長さを制限します。

## <a name="syntax"></a>構文

> **/H**<em>数</em>

## <a name="arguments"></a>引数

*number*<br/>
プログラムで許可される外部名の最大長を指定します。

## <a name="remarks"></a>Remarks

既定では、外部 (パブリック) 名の長さは、2,047 文字です。 これは、C および C++ プログラムの場合は true。 使用して **/H**識別子の最大許容長を短くしたり、長くはできません。 間にスペース **/H**と*数*は省略可能です。

プログラムには、外部名よりも長い時間が含まれている場合*数*、余分な文字は無視されます。 なくプログラムをコンパイルする場合 **/H**識別子に複数の 2,047 文字が含まれている場合、コンパイラが生成および[致命的なエラー C1064](../../error-messages/compiler-errors-1/fatal-error-c1064.md)します。

長さの制限には、コンパイラが作成した先頭にアンダー スコアが含まれています (**\_**) またはアット マーク (**\@**)。 これらの文字は、識別子の一部であるし、意味のある位置を取得します。

- コンパイラは、先頭にアンダー スコアを追加します (**\_**) 名を変更する、 `__cdecl` (既定値) と`__stdcall`アット呼び出し規約、および主要な (**\@**) に、`__fastcall`呼び出し規約。

- コンパイラによって変更された名前を引数のサイズ情報を追加します、`__fastcall`と`__stdcall`呼び出し規則、および C++ の名前に型情報を追加します。

わかります **/H**に便利です。

- 混合言語または移植可能なプログラムを作成する場合。

- 外部識別子の長さに制限を課すツールを使用するとします。

- シンボルは、デバッグ ビルドで使用される領域の量を制限する場合。

次の例を使用する方法 **/H**識別子の長さが制限されていますが多すぎる場合はエラーが発生する実際には。

```cpp
// compiler_option_H.cpp
// compile with: /H5
// processor: x86
// LNK2005 expected
void func1(void);
void func2(void);

int main() { func1(); }

void func1(void) {}
void func2(void) {}
```

使用する場合は注意が必要があります、 **/H**コンパイラの定義済みの識別子のためのオプション。 識別子の最大長が小さすぎる場合は、特定済みの識別子が未解決と特定のライブラリ関数の呼び出しになります。 たとえば場合、`printf`関数を使用してとオプション **/H5**がシンボル、コンパイル時に指定されて **_prin**が参照するために作成されます`printf`、し、これは検出されませんライブラリ。

使用 **/H**と互換性がない[/GL (Whole Program Optimization)](gl-whole-program-optimization.md)します。

**/H**オプションが Visual Studio 2005 以降非推奨です。 最大長の上限が引き上げられましたと **/H**は不要です。 非推奨のコンパイラ オプションの一覧は、次を参照してください。**非推奨とされた削除済みのコンパイラ オプション**で[Compiler Options Listed by Category](compiler-options-listed-by-category.md)します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. コンパイラ オプションを入力して、**追加オプション**ボックス。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
