---
title: コードの最適化
ms.date: 05/06/2019
helpviewer_keywords:
- performance, optimizing code
- optimization
- cl.exe compiler, performance
- optimization, C++ code
- code, optimizing
- performance, compiler
ms.openlocfilehash: f44fb734c8441e10b656c5326c8df4bf6879499a
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220183"
---
# <a name="optimizing-your-code"></a>コードの最適化

実行可能ファイルを最適化することによって、高速に実行速度とサイズの小さなコード間のバランスを実現できます。 このトピックでは、コードを最適化するために Visual Studio が提供されているメカニズムについて説明します。

## <a name="language-features"></a>言語機能

次のトピックでは、C と C++ 言語の最適化機能の一部について説明します。

[最適化のプラグマおよびキーワード](optimization-pragmas-and-keywords.md) \
一連のキーワードとプラグマのパフォーマンスを向上させるために、コードで使用できます。

[コンパイラ オプションのカテゴリ別一覧](reference/compiler-options-listed-by-category.md) \
一連の **/O**コンパイラ オプションが具体的には実行の速度やコードのサイズに影響します。

[右辺値参照宣言子: & &](../cpp/rvalue-reference-declarator-amp-amp.md) \
右辺値参照の実装をサポートする*移動セマンティクス*します。 移動セマンティクスをテンプレート ライブラリでは、これらのテンプレートを使用するアプリケーションのパフォーマンスを実装するために使用が大幅に向上させることができます。 場合、

### <a name="the-optimize-pragma"></a>Optimize プラグマ

コードの最適化のセクションでは、エラーやパフォーマンスが低下が発生する場合は使用できます、[最適化](../preprocessor/optimize.md)プラグマに、そのセクションの最適化をオフにします。

次に示すように、2 つのプラグマ コードを囲みます。

```cpp
#pragma optimize("", off)
// some code here
#pragma optimize("", on)
```

## <a name="programming-practices"></a>プログラミング手法

最適化したコードをコンパイルするときに、追加の警告メッセージがわかります。 いくつかの警告が最適化されたコードにのみ関連しているために、この動作が必要です。 これらの警告の注意を払わない場合は、多くの最適化問題を回避できます。

皮肉にも、速度のためのプログラムを最適化することにより、実行速度が低下するためのコード。 これは、最適化の方法によっては、コードのサイズを増やすためです。 たとえば、関数をインライン展開関数呼び出しのオーバーヘッドがなくなります。 ただし、インライン コードが多すぎることは、プログラム非常に大きいため、仮想メモリのページの数が増加をフォールトします。 そのため、関数呼び出しを排除することから得られた速度は、メモリ スワップ失わ可能性があります。

次のトピックでは、適切なプログラミング方法について説明します。

[タイム クリティカル コードを改善するためのヒント](tips-for-improving-time-critical-code.md) \
適切なコーディング テクニックと、パフォーマンスを向上できます。 このトピックでは、コーディング、コードの時間が重要な部分が満足することを確認するのに役立つ手法を提案します。

[最適化のベスト プラクティス](optimization-best-practices.md) \
アプリケーションを最適化する最善の方法に関する一般的なガイドラインを提供します。

## <a name="debugging-optimized-code"></a>最適化されたコードのデバッグ

最適化は、コンパイラによって作成されたコードに変わる可能性がある、アプリケーションをデバッグして、パフォーマンスの測定をコードを最適化し、お勧めします。

次のトピックでは、ビルドのリリースをデバッグする方法についての情報を提供します。

- [Visual Studio でのデバッグ](/visualstudio/debugger/debugging-in-visual-studio)

- [方法: 最適化されたコードをデバッグする](/visualstudio/debugger/how-to-debug-optimized-code)

- [浮動小数点数の精度の低下](why-floating-point-numbers-may-lose-precision.md)


次のトピックでは、構築、読み込み、およびコードの実行を最適化する方法に関する情報を提供します。

- [コンパイラのスループットの向上](improving-compiler-throughput.md)

- [() のない関数名とコードの生成](using-function-name-without-parens-produces-no-code.md)

- [インライン アセンブリの最適化](../assembler/inline/optimizing-inline-assembly.md)

- [ATL プロジェクトのコンパイラ最適化の指定](../atl/reference/specifying-compiler-optimization-for-an-atl-project.md)

- [どのような最適化手法を読み込むときに、クライアント アプリケーションのパフォーマンスを向上させるために使用する必要がありますか。](../build/dll-frequently-asked-questions.md#mfc_optimization)


## <a name="in-this-section"></a>このセクションの内容

[最適化のプラグマおよびキーワード](optimization-pragmas-and-keywords.md) \
[コンパイラのスループットの向上](improving-compiler-throughput.md) \
[なぜ浮動小数点数が有効桁数を失う可能性があります。](why-floating-point-numbers-may-lose-precision.md) \
[IEEE 浮動小数点表現](ieee-floating-point-representation.md) \
[タイム クリティカル コードを改善するためのヒント](tips-for-improving-time-critical-code.md) \
[() のない関数名を使用してコードを生成します。](using-function-name-without-parens-produces-no-code.md) \
[最適化のベスト プラクティス](optimization-best-practices.md) \
[プロファイル ガイド付き最適化](profile-guided-optimizations.md) \
[プロファイル ガイド付き最適化のための環境変数](environment-variables-for-profile-guided-optimizations.md) \
[しています](pgoautosweep.md) \
[pgomgr](pgomgr.md) \
[pgosweep](pgosweep.md) \
[方法: 複数の PGO プロファイルを単一のプロファイルにマージする](how-to-merge-multiple-pgo-profiles-into-a-single-profile.md)

## <a name="see-also"></a>関連項目

[C/C++ ビルドのリファレンス](reference/c-cpp-building-reference.md)
