---
title: 数値演算と浮動小数点のサポート
ms.date: 01/31/2019
f1_keywords:
- c.math
helpviewer_keywords:
- floating-point numbers, math routines
- math routines
- floating-point numbers
ms.assetid: e4fcaf69-5c8e-4854-a9bb-1f412042131e
ms.openlocfilehash: a0ee21378a6feb7ada39dc00f0e181672470e231
ms.sourcegitcommit: b8c22e6d555cf833510753cba7a368d57e5886db
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/29/2020
ms.locfileid: "76821513"
---
# <a name="math-and-floating-point-support"></a>数値演算と浮動小数点のサポート

ユニバーサル C ランタイム ライブラリ (UCRT) では、ISO C99 で必要とされる関数をすべて含む、多数の整数値および浮動小数点数値演算ライブラリ関数を提供しています。 浮動小数点関数は、正確性とパフォーマンスのバランスをとるために実装されます。 正確に丸めた結果を生成するには非常にコストがかかる場合があるため、正確に丸めた結果の近似値を効率的に生成できるように当該関数が設計されました。 ほとんどのケースでは、生成される結果は正確に丸めた結果の +/- 1 ulp の誤差範囲内に収まります。ただし、不正確さがそれより大きくなる場合もあります。

浮動小数点数値演算ライブラリ関数の多くは、CPU アーキテクチャの種類に応じて実装の種類も異なります。 たとえば、32 ビット x86 CRT の実装は、64 ビット x64 CRT の実装とは異なります。 さらに、関数の中には特定の CPU アーキテクチャに対して複数の実装が用意されているものもあります。 CPU でサポートされている命令セットに応じて実行時に動的に実装を選択するのが最も効率的な方法です。 たとえば、32 ビット x86 CRT で、一部の関数には x87 実装と SSE2 実装の両方が用意されています。 SSE2 をサポートしている CPU で実行すると、速い方の SSE2 実装が使用されます。 SSE2 をサポートしていない CPU で実行すると、遅い方の x87 実装が使用されます。 数値演算ライブラリ関数の実装の種類が異なると、結果を生成するために使用する CPU 命令およびアルゴリズムも異なる場合があります。このため、CPU 間で、関数の生成する結果が異なる場合があります。 ほとんどの場合、結果は正確に丸めた結果の +/- 1 ulp の誤差範囲内に収まります。ただし、実際の結果は、CPU 間で異なる場合があります。

以前の 16 ビット バージョンの Microsoft C/C++ および Microsoft Visual C++ では、80 ビット精度浮動小数点データ型として **long double** 型をサポートしていました。 最近のバージョンの Visual C++ では、**long double** データ型は、**double** 型と同じ 64 ビット精度浮動小数点データ型となっています。 コンパイラは **long double** と **double** を個別の型として扱いますが、**long double** 関数はそれに対応する **double** 関数と同じです。 CRT では、ISO C99 ソース コードの互換性を維持するために **long double** バージョンの数値演算関数を提供しています。ただし、そのバイナリ表現は他のコンパイラと異なる場合があるので注意してください。

## <a name="supported-math-and-floating-point-routines"></a>サポートされている数値演算と浮動小数点のルーチン

|ルーチンによって返される値|[使用]|
|-|-|
[abs、labs、llabs、_abs64](../c-runtime-library/reference/abs-labs-llabs-abs64.md)|整数型の絶対値を計算します
[acos、acosf、acosl](../c-runtime-library/reference/acos-acosf-acosl.md)|アーク コサインを計算します
[acosh、acoshf、acoshl](../c-runtime-library/reference/acosh-acoshf-acoshl.md)|双曲線アーク コサインを計算します
[asin、asinf、asinl](../c-runtime-library/reference/asin-asinf-asinl.md)|アーク サインを計算します
[asinh、asinhf、asinhl](../c-runtime-library/reference/asinh-asinhf-asinhl.md)|双曲線アーク サインを計算します
[atan、atanf、atanl、atan2、atan2f、atan2l](../c-runtime-library/reference/atan-atanf-atanl-atan2-atan2f-atan2l.md)|アーク タンジェントを計算します
[atanh、atanhf、atanhl](../c-runtime-library/reference/atanh-atanhf-atanhl.md)|双曲線アーク タンジェントを計算します
[_atodbl、_atodbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|ロケール固有の文字列を **double** に変換します
[atof、_atof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|文字列を **double** に変換します
[_atoflt、_atoflt_l、_atoldbl、_atoldbl_l](../c-runtime-library/reference/atodbl-atodbl-l-atoldbl-atoldbl-l-atoflt-atoflt-l.md)|ロケール固有の文字列を **float** または **long double** に変換します
[cbrt、cbrtf、cbrtl](../c-runtime-library/reference/cbrt-cbrtf-cbrtl.md)|立方根を計算します
[ceil、ceilf、ceill](../c-runtime-library/reference/ceil-ceilf-ceill.md)|切り上げを計算します
[_chgsign、_chgsignf、_chgsignl](../c-runtime-library/reference/chgsign-chgsignf-chgsignl.md)|加法逆元を計算します
[_clear87、_clearfp](../c-runtime-library/reference/clear87-clearfp.md)|浮動小数点ステータス レジスタを取得してクリアします
[_control87、\__control87_2、_controlfp](../c-runtime-library/reference/control87-controlfp-control87-2.md)|浮動小数点制御ワードを取得および設定します
[_controlfp_s](../c-runtime-library/reference/controlfp-s.md)|安全なバージョンの **_controlfp** です
[copysign、copysignf、copysignl、_copysign、_copysignf、_copysignl](../c-runtime-library/reference/copysign-copysignf-copysignl-copysign-copysignf-copysignl.md)|ある引数の絶対値と別の引数の符号を持つ値を返します
[cos、cosf、cosl](../c-runtime-library/reference/cos-cosf-cosl.md)|サインを計算します
[cosh、coshf、coshl](../c-runtime-library/reference/cosh-coshf-coshl.md)|双曲線サインを計算します
[div、ldiv、lldiv](../c-runtime-library/reference/div.md)|2 つの整数値の商と剰余を計算します
[_ecvt](../c-runtime-library/reference/ecvt.md)、[ecvt](../c-runtime-library/reference/posix-ecvt.md)|**double** を文字列に変換します
[_ecvt_s](../c-runtime-library/reference/ecvt-s.md)|安全なバージョンの **_ecvt** です
[erf、erff、erfl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|エラー関数を計算します
[erfc、erfcf、erfcl](../c-runtime-library/reference/erf-erff-erfl-erfc-erfcf-erfcl.md)|相補誤差関数を計算します
[exp、expf、expl](../c-runtime-library/reference/exp-expf.md)|指数 *e*<sup>x</sup> を計算します
[exp2、exp2f、exp2l](../c-runtime-library/reference/exp2-exp2f-exp2l.md)|指数 2<sup>x</sup> を計算します
[expm1、expm1f、expm1l](../c-runtime-library/reference/expm1-expm1f-expm1l.md)|*e*<sup>x</sup>-1 を計算します
[fabs、fabsf、fabsl](../c-runtime-library/reference/fabs-fabsf-fabsl.md)|浮動小数点型の絶対値を計算します
[_fcvt](../c-runtime-library/reference/fcvt.md)、[fcvt](../c-runtime-library/reference/posix-fcvt.md)|浮動小数点数を文字列に変換します。
[_fcvt_s](../c-runtime-library/reference/fcvt-s.md)|安全なバージョンの **_fcvt** です
[fdim、fdimf、fdiml](../c-runtime-library/reference/fdim-fdimf-fdiml.md)|2 つの値の間の正の値の差を求めます
[feclearexcept](../c-runtime-library/reference/feclearexcept1.md)|指定した浮動小数点例外をクリアします
[fegetenv](../c-runtime-library/reference/fegetenv1.md)|現在の浮動小数点環境を格納します
[fegetexceptflag](../c-runtime-library/reference/fegetexceptflag2.md)|指定した浮動小数点例外の状態を取得します
[fegetround](../c-runtime-library/reference/fegetround-fesetround2.md)|浮動小数点丸めモード制御を取得します
[feholdexcept](../c-runtime-library/reference/feholdexcept2.md)|無停止浮動小数点例外モードを設定します
[feraiseexcept](../c-runtime-library/reference/feraiseexcept.md)|指定した浮動小数点例外を発生させます
[fesetenv](../c-runtime-library/reference/fesetenv1.md)|現在の浮動小数点環境を設定します
[fesetexceptflag](../c-runtime-library/reference/fesetexceptflag2.md)|指定した浮動小数点状態フラグを設定します
[fesetround](../c-runtime-library/reference/fegetround-fesetround2.md)|指定した浮動小数点丸めモードを設定します
[fetestexcept](../c-runtime-library/reference/fetestexcept1.md)|設定されている浮動小数点例外状態フラグを確認します
[feupdateenv](../c-runtime-library/reference/feupdateenv.md)|浮動小数点環境を復元してから、前の例外を発生させます
[floor、floorf、floorl](../c-runtime-library/reference/floor-floorf-floorl.md)|切り捨てを計算します
[fma、fmaf、fmal](../c-runtime-library/reference/fma-fmaf-fmal.md)|融合型積和演算を計算します
[fmax、fmaxf、fmaxl](../c-runtime-library/reference/fmax-fmaxf-fmaxl.md)|引数の最大値を計算します
[fmin、fminf、fminl](../c-runtime-library/reference/fmin-fminf-fminl.md)|引数の最小値を計算します。
[fmod、fmodf、fmodl](../c-runtime-library/reference/fmod-fmodf.md)|浮動小数点の剰余を計算します
[_fpclass、_fpclassf](../c-runtime-library/reference/fpclass-fpclassf.md)|浮動小数点値の分類を返します
[fpclassify](../c-runtime-library/reference/fpclassify.md)|浮動小数点値の分類を返します
[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)|浮動小数点例外のハンドラーを設定します
[_fpreset](../c-runtime-library/reference/fpreset.md)|浮動小数点環境をリセットします
[frexp、frexpf、frexpl](../c-runtime-library/reference/frexp.md)|浮動小数点数の仮数と指数を取得します
[_gcvt](../c-runtime-library/reference/gcvt.md)、[gcvt](../c-runtime-library/reference/posix-gcvt.md)|浮動小数点数を文字列に変換します。
[_gcvt_s](../c-runtime-library/reference/gcvt-s.md)|安全なバージョンの **_gcvt** です
[_get_FMA3_enable、_set_FMA3_enable](../c-runtime-library/reference/get-fma3-enable-set-fma3-enable.md)|x64 での FMA3 命令使用フラグを取得または設定します
[hypot、hypotf、hypotl、_hypot、_hypotf、_hypotl](../c-runtime-library/reference/hypot-hypotf-hypotl-hypot-hypotf-hypotl.md)|斜辺を計算します
[ilogb、ilogbf、ilogbl](../c-runtime-library/reference/ilogb-ilogbf-ilogbl2.md)|整数の 2 進数の指数を計算します
[imaxabs](../c-runtime-library/reference/imaxabs.md)|整数型の絶対値を計算します
[imaxdiv](../c-runtime-library/reference/imaxdiv.md)|2 つの整数値の商と剰余を計算します
[isfinite、_finite、_finitef](../c-runtime-library/reference/finite-finitef.md)|ある値が有限かどうかを確認します
[isgreater、isgreaterequal、isless、islessequal、islessgreater、isunordered](../c-runtime-library/reference/floating-point-ordering.md)|2 つの浮動小数点値の順序を比較します
[isinf](../c-runtime-library/reference/isinf.md)|浮動小数点値が無限かどうかを決定します
[isnan、_isnan、_isnanf](../c-runtime-library/reference/isnan-isnan-isnanf.md)|NaN の浮動小数点値をテストします
[isnormal](../c-runtime-library/reference/isnormal.md)|浮動小数点値が有限であり、非正規ではないかどうかをテストします
[_j0、_j1、_jn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Bessel 関数を計算します
[ldexp、ldexpf、ldexpl](../c-runtime-library/reference/ldexp.md)|x*2<sup>n</sup> を計算します
[lgamma、lgammaf、lgammal](../c-runtime-library/reference/lgamma-lgammaf-lgammal.md)|ガンマ関数の絶対値の自然対数を計算します
[llrint、llrintf、llrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|浮動小数点値を最も近い **long long** 値に丸めます
[llround、llroundf、llroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|浮動小数点値を最も近い **long long** 値に丸めます
[log、logf、logl、log10、log10f、log10l](../c-runtime-library/reference/log-logf-log10-log10f.md)|自然対数または 10 を底とする対数を計算します
[log1p、log1pf、log1pl](../c-runtime-library/reference/log1p-log1pf-log1pl2.md)|1+x の自然対数を計算します
[log2、log2f、log2l](../c-runtime-library/reference/log2-log2f-log2l.md)|2 を底とする対数を計算します
[logb、logbf、logbl、_logb、_logbf](../c-runtime-library/reference/logb-logbf-logbl-logb-logbf.md)|浮動小数点値の指数を返します
[lrint、lrintf、lrintl](../c-runtime-library/reference/lrint-lrintf-lrintl-llrint-llrintf-llrintl.md)|浮動小数点値を最も近い **long** 値に丸めます
[_lrotl、_lrotr](../c-runtime-library/reference/lrotl-lrotr.md)|整数値を左または右に回転します
[lround、lroundf、lroundl](../c-runtime-library/reference/lround-lroundf-lroundl-llround-llroundf-llroundl.md)|浮動小数点値を最も近い **long** 値に丸めます
[_matherr](../c-runtime-library/reference/matherr.md)|既定の数値演算エラー ハンドラーです
[__max](../c-runtime-library/reference/max.md)|2 つの値の大きい方を返すマクロです
[__min](../c-runtime-library/reference/min.md)|2 つの値の小さい方を返すマクロです
[modf、modff、modfl](../c-runtime-library/reference/modf-modff-modfl.md)|浮動小数点値を小数部と整数部に分割します
[nan、nanf、nanl](../c-runtime-library/reference/nan-nanf-nanl.md)|簡易な NaN 値を返します
[nearbyint、nearbyintf、nearbyintl](../c-runtime-library/reference/nearbyint-nearbyintf-nearbyintl1.md)|丸められた値を返します
[nextafter、nextafterf、nextafterl、_nextafter、_nextafterf](../c-runtime-library/reference/nextafter-functions.md)|次の表現可能な浮動小数点値を返します
[nexttoward、nexttowardf、nexttowardl](../c-runtime-library/reference/nextafter-functions.md)|次の表現可能な浮動小数点値を返します
[pow、powf、powl](../c-runtime-library/reference/pow-powf-powl.md)|*x*<sup>*y*</sup> の値を返します
[remainder、remainderf、remainderl](../c-runtime-library/reference/remainder-remainderf-remainderl.md)|2 つの浮動小数点値の商の剰余を計算します
[remquo、remquof、remquol](../c-runtime-library/reference/remquo-remquof-remquol.md)|2 つの整数値の剰余を計算します
[rint、rintf、rintl](../c-runtime-library/reference/rint-rintf-rintl.md)|浮動小数点値を丸めます
[_rotl、_rotl64、_rotr、_rotr64](../c-runtime-library/reference/rotl-rotl64-rotr-rotr64.md)|整数型のビットを回転します
[round、roundf、roundl](../c-runtime-library/reference/round-roundf-roundl.md)|浮動小数点値を丸めます
[_scalb、_scalbf](../c-runtime-library/reference/scalb.md)|引数を 2 のべき乗の倍率で増減させます
[scalbn、scalbnf、scalbnl、scalbln、scalblnf、scalblnl](../c-runtime-library/reference/scalbn-scalbnf-scalbnl-scalbln-scalblnf-scalblnl.md)|浮動小数点数に整数である **FLT_RADIX** の累乗を乗算します
[_set_controlfp](../c-runtime-library/reference/set-controlfp.md)|浮動小数点制御ワードを設定します
[_set_SSE2_enable](../c-runtime-library/reference/set-sse2-enable.md)|SSE2 命令を有効または無効にします
[signbit](../c-runtime-library/reference/signbit.md)|浮動小数点値の符号ビットをテストします
[sin、sinf、sinl](../c-runtime-library/reference/sin-sinf-sinl.md)|サインを計算します
[sinh、sinhf、sinhl](../c-runtime-library/reference/sinh-sinhf-sinhl.md)|双曲線サインを計算します
[sqrt、sqrtf、sqrtl](../c-runtime-library/reference/sqrt-sqrtf-sqrtl.md)|平方根を計算します
[_status87、_statusfp、_statusfp2](../c-runtime-library/reference/status87-statusfp-statusfp2.md)|浮動小数点ステータス ワードを取得します
[strtof、_strtof_l](../c-runtime-library/reference/strtof-strtof-l-wcstof-wcstof-l.md)|文字列を **float** に変換します
[strtold、_strtold_l](../c-runtime-library/reference/strtold-strtold-l-wcstold-wcstold-l.md)|文字列を**long** **double**に変換します。
[tan、tanf、tanl](../c-runtime-library/reference/tan-tanf-tanl.md)|タンジェントを計算します
[tanh、tanhf、tanhl](../c-runtime-library/reference/tanh-tanhf-tanhl.md)|双曲線タンジェントを計算します
[tgamma、tgammaf、tgammal](../c-runtime-library/reference/tgamma-tgammaf-tgammal.md)|ガンマ関数を計算します
[trunc、truncf、truncl](../c-runtime-library/reference/trunc-truncf-truncl.md)|小数部を切り捨てます
[_wtof、_wtof_l](../c-runtime-library/reference/atof-atof-l-wtof-wtof-l.md)|ワイド文字列を **double** に変換します
[_y0、_y1、_yn](../c-runtime-library/reference/bessel-functions-j0-j1-jn-y0-y1-yn.md)|Bessel 関数を計算します

## <a name="see-also"></a>関連項目

[カテゴリ別ユニバーサル C ランタイム ルーチン](../c-runtime-library/run-time-routines-by-category.md)<br/>
[浮動小数点プリミティブ](../c-runtime-library/reference/floating-point-primitives.md)<br/>
