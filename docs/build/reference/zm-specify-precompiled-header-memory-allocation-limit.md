---
title: /Zm (プリコンパイル済みヘッダーのメモリ割り当て制限の指定)
ms.date: 03/08/2019
f1_keywords:
- /zm
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
ms.openlocfilehash: 09df8e1ee9a97289e29e1191e8c1585580435b79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315275"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (プリコンパイル済みヘッダーのメモリ割り当て制限の指定)

コンパイラがプリコンパイル済みヘッダーを構築するために割り当てるメモリの量を決定します。

## <a name="syntax"></a>構文

```
/Zmfactor
```

## <a name="arguments"></a>引数

*factor*<br/>
コンパイラがプリコンパイル済みヘッダーを構築するために使用するメモリの量を決定するスケール ファクター。

*係数*引数がコンパイラによって定義された作業バッファーの既定のサイズの割合。 既定値*係数*100 (パーセント) は拡大または縮小の量を指定することができます。

## <a name="remarks"></a>Remarks

Visual Studio 2015 より前に、のバージョンでは、C コンパイラは、いくつかの独立したヒープを使用し、大きさの限界をそれぞれがありました。 現時点では、コンパイラは動的に、ヒープの総サイズの上限に達するまで、必要に応じてヒープを拡大し、により、複数のアドレス範囲を構成するプリコンパイル済みヘッダー。 その結果、 **/Zm**コンパイラ オプションが必要なことはほとんどありません。

かどうか、コンパイラはヒープ領域が不足し、出力、 [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md)を使用すると、エラー メッセージ、 **/Zm**コンパイラ オプション、過度のメモリを予約した可能性があります。 削除を検討して、 **/Zm**オプション。

コンパイラが出力する場合、 [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) 、付随するエラー メッセージは、 [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md)メッセージを指定します、*係数*を使用して再コンパイルするときに使用する引数 **/Zm**コンパイラ オプション。 このメッセージは、プリコンパイル済みヘッダーを使用する場合にのみ重要な`#pragma hdrstop`します。 それ以外の場合は、Windows 仮想メモリ不足の問題とを使用する推奨設定が原因で誤ったエラー、 **/Zm**オプションを無視する必要があります。 代わりを使用する場合は、並列処理の数を減らすことを検討、 **/maxcpucount** msbuild オプション。実行可能ファイルと組み合わせて、 **/MP** CL するオプション。実行可能ファイルです。 詳細については、次を参照してください。[プリコンパイル済みヘッダー (PCH) の問題と推奨事項](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/)します。

次の表は、*要素*引数は、既定のプリコンパイル済みヘッダーのバッファーのサイズが 75 MB と仮定した場合にメモリ割り当て制限に影響します。

|値*要素*|メモリ割り当て制限|
|-----------------------|-----------------------------|
|10|7.5 MB|
|100|75 MB|
|200|150 MB|
|1000|750 MB|
|2000|1500 MB|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>メモリ割り当て制限を設定する別の方法

### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境で /Zm コンパイラ オプションを設定するには

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. ナビゲーション ウィンドウで選択**構成プロパティ** > **C/C++** > **コマンドライン**します。

1. 入力、 **/Zm**コンパイラ オプションで、**追加オプション**ボックス。

### <a name="to-set-the-zm-compiler-option-programmatically"></a>/Zm コンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
