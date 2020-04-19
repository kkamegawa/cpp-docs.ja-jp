---
title: /GL (プログラム全体の最適化)
ms.date: 11/04/2016
f1_keywords:
- /gl
- VC.Project.VCCLWCECompilerTool.WholeProgramOptimization
helpviewer_keywords:
- /GL compiler option [C++]
- whole program optimizations and C++ compiler
- -GL compiler option [C++]
- GL compiler option [C++]
ms.assetid: 09d51e2d-9728-4bd0-b5dc-3b8284aca1d1
ms.openlocfilehash: 6251209dac74a504bb0635f0c544c39935090a42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292134"
---
# <a name="gl-whole-program-optimization"></a>/GL (プログラム全体の最適化)

プログラム全体の最適化を有効にします。

## <a name="syntax"></a>構文

```
/GL[-]
```

## <a name="remarks"></a>Remarks

プログラム全体の最適化は、コンパイラが、プログラムのすべてのモジュールの情報を使用した最適化を実行できます。 プログラム全体の最適化されていない場合の最適化の実行、ごとのモジュール (コンパイル単位)。

プログラム全体の最適化は既定で無効と明示的に有効にする必要があります。 ただし、それを明示的に無効にすることがも **/GL-** します。

すべてのモジュールについては、コンパイラでは次のことができます。

- 関数の境界を越えて、レジスタの使用を最適化します。

- グローバル データの読み込みおよび格納の数を減らします変更の追跡の方の操作を行います。

- 読み込みおよび格納の数を減らす、一連の可能なポインターによって変更された項目を逆参照追跡の方の操作を行います。

- インライン関数が別のモジュールで定義されている場合でも、モジュール内の関数。

生成された .obj ファイル **/GL**はこのようなリンカー ユーティリティを使用できません[EDITBIN](editbin-reference.md)と[DUMPBIN](dumpbin-reference.md)します。

プログラムをコンパイルする場合 **/GL**と[/c](c-compile-without-linking.md)、/LTCG リンカー オプションを使用して、出力ファイルを作成する必要があります。

[/ZI](z7-zi-zi-debug-information-format.md)では使用できません **/GL**

生成されたファイルの形式の **/GL**現在のバージョンでできない可能性がありますそれ以降のバージョンの Visual C で読み取ることです。 生成された .obj ファイルから成る .lib ファイルを出荷する必要があります **/GL**ユーザーを現在および将来の使用が予想されるすべてのバージョンの Visual C の .lib ファイルのコピーを同梱する意思がないです。

生成された .obj ファイル **/GL**プリコンパイル済みヘッダー ファイルは .lib ファイルを生成したのと同じコンピューターにリンクする場合を除き、.lib ファイルの作成に使用する必要があります、 **/GL** .obj ファイル。 .Obj ファイルのプリコンパイル済みヘッダー ファイルからの情報は、リンク時に必要になります。

使用可能な最適化と、プログラム全体の最適化の制限事項の詳細については、次を参照してください。 [/LTCG](ltcg-link-time-code-generation.md)します。  **/GL**もでは使用できるガイド付き最適化のプロファイルは、/LTCG を参照してください。  ガイド付き最適化と関数の最適化のプロファイル ガイド付きの順序付けをするかどうかのプロファイルのコンパイルをするときに使用してコンパイルする必要があります[/Gy](gy-enable-function-level-linking.md)またはコンパイラ オプション/Gy ことを意味します。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境でこのリンカー オプションを設定するには

1. 参照してください[/LTCG (リンク時コード生成)](ltcg-link-time-code-generation.md)を指定する方法については **/GL**開発環境。

### <a name="to-set-this-linker-option-programmatically"></a>このリンカーをコードから設定するには

1. 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.WholeProgramOptimization%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
