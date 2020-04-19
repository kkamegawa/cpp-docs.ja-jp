---
title: /O オプション (コードの最適化)
ms.date: 09/25/2017
f1_keywords:
- VC.Project.VCCLCompilerTool.Optimization
- /o
- VC.Project.VCCLWCECompilerTool.Optimization
helpviewer_keywords:
- performance, cle.exe compiler
- cl.exe compiler, performance
ms.assetid: 77997af9-5555-4b3d-aa57-6615b27d4d5d
ms.openlocfilehash: ffd3023120f1d930a24ccef6fa297594062322df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320423"
---
# <a name="o-options-optimize-code"></a>/O オプション (コードの最適化)

**/O**さまざまなオプションを制御する際に役立つ最適化が最高速度またはサイズの最小のコードを作成します。

- [/O1](o1-o2-minimize-size-maximize-speed.md)最小サイズのコードを生成するための最適化の組み合わせを設定します。

- [/O2](o1-o2-minimize-size-maximize-speed.md)最高速度でコードを最適化の最適化の組み合わせを設定します。

- [/Ob](ob-inline-function-expansion.md)関数のインライン展開を制御します。

- [/Od](od-disable-debug.md)をコンパイルが高速化し、デバッグを簡略化の最適化を無効にします。

- [/Og](og-global-optimizations.md)グローバルの最適化を有効します。

- [/Oi](oi-generate-intrinsic-functions.md)適切な関数呼び出し用の組み込み関数が生成されます。

- [/Os](os-ot-favor-small-code-favor-fast-code.md)サイズの最適化の優先順位の速度に関する最適化をコンパイラに指示します。

- [/Ot](os-ot-favor-small-code-favor-fast-code.md) (既定の設定) の速度の最適化の優先順位のサイズの最適化をコンパイラに指示します。

- [/Ox](ox-full-optimization.md)速度を重視した最適化のいくつかを選択する組み合わせのオプションです。 厳密なサブセットが、 **/O2**最適化します。

- [/Oy](oy-frame-pointer-omission.md)関数呼び出しが速くの呼び出し履歴にフレーム ポインターが作成されなくなります。

## <a name="remarks"></a>Remarks

複数を組み合わせることができます **/O**オプションを 1 つのオプションのステートメントにします。 たとえば、 **/Odi**と同じ **/Od/Oi**します。 特定のオプションは相互に排他的で一緒に使用する場合、コンパイラ エラーが発生します。 個々 の **/O**詳細については、オプションです。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
