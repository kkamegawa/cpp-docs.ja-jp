---
title: /Gs (スタック チェック呼び出しの制御)
ms.date: 10/25/2018
f1_keywords:
- /GS
helpviewer_keywords:
- disabling stack probes
- GS compiler option [C++]
- /GS compiler option [C++]
- stack, stack probes
- stack probes
- -GS compiler option [C++]
- stack checking calls
ms.assetid: 40daed7c-f942-4085-b872-01e12b37729e
ms.openlocfilehash: e31b42c1d9422d44c5f106f40c4a60a38f23425b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62270849"
---
# <a name="gs-control-stack-checking-calls"></a>/Gs (スタック チェック呼び出しの制御)

スタック プローブのしきい値を制御します。

## <a name="syntax"></a>構文

> **/Gs**[*size*]

## <a name="arguments"></a>引数

*size*<br/>
(オプション) スタック プローブが開始される前にローカル変数が占有することのできるバイト数。 間にスペースは入れません **/Gs**と*サイズ*します。

## <a name="remarks"></a>Remarks

A*スタック プローブ*コンパイラは関数呼び出しの先頭に挿入するコードのシーケンスです。 スタック プローブを開始すると、関数のローカル変数を保存するのに必要なスペースの量に応じてメモリに作用します。 これにより、関数の残りの部分を実行する前に、必要な場合、追加のスタック メモリで透過的にページに、オペレーティング システムです。

既定で、関数に 1 ページを超えるスタック領域が必要な場合、コンパイラはスタック プローブを開始するコードを生成します。 これはのコンパイラ オプションに相当 **/Gs4096** x86、x64、ARM、ARM64 プラットフォーム。 この値により、アプリケーションと Windows メモリ マネージャーは、実行時に動的にプログラム スタックにコミットされるメモリの量を増やすことができます。

> [!NOTE]
> 既定値 **/Gs4096**により、実行時に正常に増加する Windows 用のアプリケーションのプログラム スタック。 既定値は、変更理由が明確でない限り変えないことをお勧めします。

仮想デバイス ドライバーなど一部のプログラムでは、この既定のスタック増加メカニズムは必要ありません。 このような場合、スタック プローブは必要ありませんし、コンパイラからの設定の生成を停止する*サイズ*任意の関数はローカル変数の記憶域の必要がありますよりも大きい値にします。

**/Gs0**ローカル変数のストレージを必要とされるすべての関数呼び出しのプローブのスタックを開始します。 これはパフォーマンスに対して悪影響を及ぼす可能性があります。

X64 の場合を対象と、 **/Gs**オプションを指定することがなく、*サイズ*引数が同じ **/Gs0**。 場合、*サイズ*D9014 の警告が生成されます、効果は、指定した場合と同じ引数が 1 ~ 9 **/Gs0**します。

X86、ARM、ARM64 ターゲット、および、 **/Gs**なしオプション、*サイズ*引数は、同じ **/Gs4096**。 場合、*サイズ*D9014 の警告が生成されます、効果は、指定した場合と同じ引数が 1 ~ 9 **/Gs4096**します。

すべてのターゲットを*サイズ*10 と 2147485647 の引数が指定された値で、しきい値を設定します。 A*サイズ*2147485648 以上の原因の致命的なエラー C1049 の。

使用してスタック プローブをオンまたはオフを有効にすることができます、 [check_stack](../../preprocessor/check-stack.md)ディレクティブ。 **/Gs** 、`check_stack`プラグマは標準 C ライブラリ ルーチンに影響を持ちません。 コンパイルする関数のみに影響します。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 入力、 **/Gs**コンパイラ オプションと、省略可能なサイズで**追加オプション**します。 選択**OK**または**適用**変更を保存します。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
