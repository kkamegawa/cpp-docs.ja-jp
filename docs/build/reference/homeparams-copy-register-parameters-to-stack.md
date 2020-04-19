---
title: /homeparams (レジスタ パラメーターのスタックへのコピー)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: a1f9269c7deae6c9ae2e4f198006ad09dd37abc3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62291419"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (レジスタ パラメーターのスタックへのコピー)

強制パラメーターは、その場所に関数の開始時にスタックにも書き込まれるレジスタで渡されます。

## <a name="syntax"></a>構文

> **/homeparams**

## <a name="remarks"></a>Remarks

このコンパイラ オプションでは、ネイティブおよびクロス コンパイラを x64 を対象とするのみです。

X64 呼び出し規則では、レジスタに渡されるパラメーターの場合でも、すべてのパラメーターに割り当てられるスタック領域が必要です。 詳細については、次を参照してください。[パラメーターの引き渡し](../../build/x64-calling-convention.md#parameter-passing)します。 既定では、登録パラメーターは、リリース ビルドに割り当てられたスタック領域にコピーされません。 これにより、プログラム、最適化されたリリース ビルドをデバッグは困難です。

リリース ビルドを使用することができます、 **/homeparams**強制的にコンパイラをコピーするオプションが、アプリケーションをデバッグできるようにする、スタックにパラメーターを登録します。 **/homeparams**余分なサイクルをスタック レジスタ パラメーターの読み込みを必要とするためには、パフォーマンスを示すものでは。

デバッグ ビルドでのレジスタに渡されるパラメーターのスタックは常に設定されます。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 開く、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. コンパイラ オプションを入力して、**追加オプション**ボックス。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
