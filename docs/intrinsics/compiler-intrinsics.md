---
title: コンパイラの組み込み
ms.date: 09/02/2019
helpviewer_keywords:
- intrinsics, compiler
- compiler intrinsics
- cl.exe compiler, performance
- cl.exe compiler, intrinsics
ms.assetid: 48bb9929-7d78-4fd8-a092-ae3c9f971858
ms.openlocfilehash: 61fc825e333b8d839d15752ce737dfc6d3980809
ms.sourcegitcommit: e805200eaef4fe7a65a00051bbd305273af94fe7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/18/2019
ms.locfileid: "74163488"
---
# <a name="compiler-intrinsics"></a>コンパイラの組み込み

ほとんどの関数はライブラリに含まれますが、関数によっては、コンパイラに組み込まれているものもあります。 これらは、組み込み関数または組み込みと呼ばれます。

## <a name="remarks"></a>Remarks

関数が組み込みの場合、その関数のコードは通常、インラインで挿入されます。これにより、関数呼び出しのオーバーヘッドを回避し、その関数の非常に効率的なマシン語命令が生成されるようにします。 組み込みは通常、同等のインライン アセンブリよりも高速です。これは、オプティマイザーに組み込み関数の動作数に関する組み込まれた知識があるため、インライン アセンブリが使用できない最適化を使用できるためです。 また、オプティマイザーは、組み込みの展開、バッファーの配置、その他の調節を、呼び出しのコンテキストと引数に応じて行うことができます。

組み込みの使用はコードの移植性に影響します。これは、Visual C++ で使用できる組み込み関数が、コードが他のコンパイラでコンパイルされた場合には利用できない場合があったり、また、あるターゲット アーキテクチャで使用できる組み込みが、すべてのアーキテクチャで使用できるとは限らないためです。 ただし、組み込みは通常、インライン アセンブリよりも移植性があります。 組み込みはインライン アセンブリがサポートされていない 64 ビット アーキテクチャに必要です。

`__assume` や `__ReadWriteBarrier` などの組み込みは、オプティマイザーの動作に影響を与える情報をコンパイラを提供します。

組み込み関数としてのみ使用できる組み込みもあり、また関数および組み込み実装の両方で使用できる組み込みもあります。 特定の関数のみを有効化するか、またはすべての組み込みを有効化するかによって、2 つのうちの 1 つの方法で組み込みの実装を使用するようにコンパイラに指示を与えることができます。 最初の方法は *、`#pragma intrinsic(``)`* を使用することです。 プラグマを使用して、コンマで区切った 1 つの組み込みまたは複数の組み込みを指定することができます。 2つ目の方法では、 [/Oi (組み込み関数の生成)](../build/reference/oi-generate-intrinsic-functions.md)コンパイラオプションを使用します。これにより、特定のプラットフォーム上のすべての組み込みを使用できるようになります。 **/Oi**を使用して、組み込み*関数*の代わりに関数呼び出しを強制的に使用するには `#pragma function(``)` を使用します。 ルーチンが組み込みとしてのみ使用可能であることを示す特定の組み込みメモのドキュメントでは、 **/Oi**または `#pragma intrinsic` が指定されているかどうかに関係なく、組み込み実装が使用されます。 どのような場合でも、 **/Oi**または `#pragma intrinsic` では、オプティマイザーが組み込みのを使用することはできますが、強制されません。 オプティマイザーは、関数を呼び出すことも可能です。

いくつかの標準 C/C++ ライブラリ関数は、いくつかのアーキテクチャの組み込み実装で使用できます。 CRT 関数を呼び出す場合、 **/Oi**がコマンドラインで指定されている場合、組み込み実装が使用されます。

共通の組み込み関数のプロトタイプを宣言するヘッダーファイル (\<は、.h > にあります) を使用できます。 製造元固有の組み込みは、\<immintrin .h > と \<ammintrin .h > ヘッダーファイルで使用できます。 さらに、特定の Windows ヘッダーは、コンパイラの組み込みにマップする関数を宣言します。

次のセクションでは、さまざまなアーキテクチャで使用できるすべての組み込みを示します。 特定のターゲット プロセッサでの組み込みの動作の詳細については、開発元のリファレンス ドキュメントを参照してください。

- [ARM 組み込み](../intrinsics/arm-intrinsics.md)

- [ARM64 組み込み](../intrinsics/arm64-intrinsics.md)

- [x86 組み込みリスト](../intrinsics/x86-intrinsics-list.md)

- [x64 (amd64) 組み込み一覧](../intrinsics/x64-amd64-intrinsics-list.md)

- [すべてのアーキテクチャで使用可能な組み込み](../intrinsics/intrinsics-available-on-all-architectures.md)

- [組み込み関数のアルファベット順の一覧](../intrinsics/alphabetical-listing-of-intrinsic-functions.md)

## <a name="see-also"></a>関連項目

[ARM アセンブラーリファレンス](../assembler/arm/arm-assembler-reference.md)<br/>
[Microsoft マクロアセンブラーリファレンス](../assembler/masm/microsoft-macro-assembler-reference.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[C ランタイムライブラリリファレンス](../c-runtime-library/c-run-time-library-reference.md)