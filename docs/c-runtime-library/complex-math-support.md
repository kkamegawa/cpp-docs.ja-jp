---
title: C の複雑な数値演算のサポート
ms.date: 05/14/2019
f1_keywords:
- c.complex
helpviewer_keywords:
- complex numbers, math routines
- math routines
- complex numbers
ms.openlocfilehash: 493886fcf1dbfd3dc16487dd8650206c428bb06d
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/15/2019
ms.locfileid: "66186093"
---
# <a name="c-complex-math-support"></a>C の複雑な数値演算のサポート

Microsoft C ランタイム ライブラリ (CRT) では、ISO C99 で必要とされる関数をすべて含む、複雑な数値演算ライブラリ関数を提供しています。 コンパイラは **complex** または **_Complex** のキーワードを直接にはサポートしないため、Microsoft の実装では構造体型を使って複素数を表します。

これらの関数は、正確性とパフォーマンスのバランスをとるために実装されます。 正確に丸めた結果を生成するには非常にコストがかかる場合があるため、正確に丸めた結果の近似値を効率的に生成できるように当該関数が設計されました。 ほとんどのケースでは、生成される結果は正確に丸めた結果の +/- 1 ulp の誤差範囲内に収まります。ただし、不正確さがそれより大きくなる場合もあります。

複雑な数値演算ルーチンはその実装において、浮動小数点数値演算ライブラリ関数に依存します。 この関数は、CPU アーキテクチャの種類に応じて実装の種類も異なります。 たとえば、32 ビット x86 CRT の実装は、64 ビット x64 CRT の実装とは異なります。 さらに、関数の中には特定の CPU アーキテクチャに対して複数の実装が用意されているものもあります。 CPU でサポートされている命令セットに応じて実行時に動的に実装を選択するのが最も効率的な方法です。 たとえば、32 ビット x86 CRT で、一部の関数には x87 実装と SSE2 実装の両方が用意されています。 SSE2 をサポートしている CPU で実行すると、速い方の SSE2 実装が使用されます。 SSE2 をサポートしていない CPU で実行すると、遅い方の x87 実装が使用されます。 数値演算ライブラリ関数の実装の種類が異なると、結果を生成するために使用する CPU 命令およびアルゴリズムも異なる場合があります。このため、CPU 間で、関数の生成する結果が異なる場合があります。 ほとんどの場合、結果は正確に丸めた結果の +/- 1 ulp の誤差範囲内に収まります。ただし、実際の結果は、CPU 間で異なる場合があります。

## <a name="types-used-in-complex-math"></a>複雑な数値演算で使用される型

complex.h ヘッダーの Microsoft 実装では、次の型が C99 標準ネイティブの複合型と同等として定義されます。

|標準の型|Microsoft の型|
|-|-|
|**float complex** または **float _Complex**|**_Fcomplex**|
|**double complex** または **double _Complex**|**_Dcomplex**|
|**long double complex** または **long double _Complex**|**_Lcomplex**|

math.h ヘッダーは個別の型 **struct _complex** を定義します。これは [_cabs](../c-runtime-library/reference/cabs.md) 関数で使用されます。 **struct _complex** 型は同等の複雑な数値演算関数 [cabs、cabsf、cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md) では使用されません。

## <a name="complex-constants-and-macros"></a>複雑な定数とマクロ

**I** は `{ 0.0f, 1.0f }` で初期化された **float** 複合型の **_Fcomplex** として定義されます。

## <a name="trigonometric-functions"></a>三角関数

|関数|説明|
|-|-|
|[cacos、cacosf、cacosl](../c-runtime-library/reference/cacos-cacosf-cacosl.md)|複素数の複雑な逆余弦を計算する|
|[casin、casinf、casinl](../c-runtime-library/reference/casin-casinf-casinl.md)|複素数の複雑な逆正弦を計算する|
|[catan、catanf、catanl](../c-runtime-library/reference/catan-catanf-catanl.md)|複素数の複雑な逆正接を計算する|
|[ccos、ccosf、ccosl](../c-runtime-library/reference/ccos-ccosf-ccosl.md)|複素数の複雑な余弦を計算する|
|[csin、csinf、csinl](../c-runtime-library/reference/csin-csinf-csinl.md)|複素数の複雑な正弦を計算する|
|[ctan、ctanf、ctanl](../c-runtime-library/reference/ctan-ctanf-ctanl.md)|複素数の複雑な正接を計算する|

## <a name="hyperbolic-functions"></a>ハイパーボリック関数

|関数|説明|
|-|-|
|[cacosh、cacoshf、cacoshl](../c-runtime-library/reference/cacosh-cacoshf-cacoshl.md)|複素数の複雑な逆双曲線余弦を計算する|
|[casinh、casinhf、casinhl](../c-runtime-library/reference/casinh-casinhf-casinhl.md)|複素数の複雑な逆双曲線正弦を計算する|
|[catanh、catanhf、catanhl](../c-runtime-library/reference/catanh-catanhf-catanhl.md)|複素数の複雑な逆双曲線正接を計算する|
|[ccosh、ccoshf、ccoshl](../c-runtime-library/reference/ccosh-ccoshf-ccoshl.md)|複素数の複雑な双曲線余弦を計算する|
|[csinh、csinhf、csinhl](../c-runtime-library/reference/csinh-csinhf-csinhl.md)|複素数の複雑な双曲線正弦を計算する|
|[ctanh、ctanhf、ctanhl](../c-runtime-library/reference/ctanh-ctanhf-ctanhl.md)|複素数の複雑な双曲線正接を計算する|

## <a name="exponential-and-logarithmic-functions"></a>指数関数と対数関数

|関数|説明|
|-|-|
|[cexp、cexpf、cexpl](../c-runtime-library/reference/cexp-cexpf-cexpl.md)|複素数の *e* を底とする複素指数関数を計算する|
|[clog、clogf、clogl](../c-runtime-library/reference/clog-clogf-clogl.md)|複素数の *e* を底とする複素自然対数を計算する|
|[clog10、clog10f、clog10l](../c-runtime-library/reference/clog10-clog10f-clog10l.md)|複素数の 10 を底とする複素対数函数を計算する|

## <a name="power-and-absolute-value-functions"></a>べき関数と絶対値関数

|関数|説明|
|-|-|
|[cabs、cabsf、cabsl](../c-runtime-library/reference/cabs-cabsf-cabsl.md)|複素数の絶対値 (ノルム、係数、大きさとも呼ばれる) を計算する|
|[cpow、cpowf、cpowl](../c-runtime-library/reference/cpow-cpowf-cpowl.md)|複合べき関数 x<sup>y</sup> を計算する|
|[csqrt、csqrtf、csqrtl](../c-runtime-library/reference/csqrt-csqrtf-csqrtl.md)|複素数の複雑な平方根を計算する|

## <a name="manipulation-functions"></a>データ操作関数

|関数|説明|
|-|-|
|[_Cbuild、_FCbuild、_LCbuild](../c-runtime-library/reference/cbuild-fcbuild-lcbuild.md)|実数部と虚数部から複素数を構築する|
|[carg、cargf、cargl](../c-runtime-library/reference/carg-cargf-cargl.md)|複素数の引数 (位相角とも呼ばれる) を計算する|
|[cimag、cimagf、cimagl](../c-runtime-library/reference/cimag-cimagf-cimagl.md)|複素数の虚数部を計算する|
|[conj、conjf、conjl](../c-runtime-library/reference/conj-conjf-conjl.md)|複素数の複素共役を計算する|
|[cproj、cprojf、cprojl](../c-runtime-library/reference/cproj-cprojf-cprojl.md)|リーマン球面上への複素数の射影を計算する|
|[creal、crealf、creall](../c-runtime-library/reference/creal-crealf-creall.md)|複素数の実数部を計算する|
|[norm、normf、norml](../c-runtime-library/reference/norm-normf-norml1.md)|複素数の 2 乗の絶対値を計算する|

## <a name="operation-functions"></a>操作関数

複素数は Microsoft コンパイラでネイティブな型ではないため、標準の算術演算子は複合型に定義されていません。 便宜上、次の複雑な数値演算ライブラリ関数は、ユーザー コードでの複素数の限られた操作を有効にするために提供されています。

|関数|説明|
|-|-|
|[_Cmulcc、_FCmulcc、_LCmulcc](../c-runtime-library/reference/cmulcc-fcmulcc-lcmulcc.md)|2 つの複素数を乗算する|
|[_Cmulcr、_FCmulcr、_LCmulcr](../c-runtime-library/reference/cmulcr-fcmulcr-lcmulcr.md)|複雑な浮動小数を乗算する|

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
