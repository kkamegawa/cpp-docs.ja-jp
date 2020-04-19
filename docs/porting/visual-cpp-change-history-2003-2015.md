---
title: Visual C++ 2003 ～ 2015 の変更履歴
ms.date: 10/21/2019
helpviewer_keywords:
- breaking changes [C++]
ms.assetid: b38385a9-a483-4de9-99a6-797488bc5110
ms.openlocfilehash: 335db55f3b181021f4deb391358df5bbfb607815
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/17/2020
ms.locfileid: "77415694"
---
# <a name="visual-c-change-history-2003---2015"></a>Visual C++ 2003 ～ 2015 の変更履歴

この記事では、Visual Studio 2003 から Visual Studio 2015 の互換性に影響する変更についてすべて説明します。この記事の「新しい動作」や「現在」という語は、Visual Studio 2015 以降を指します。 「従来の動作」や「以前」という語は、Visual Studio 2013 以前のリリースを指します。

最新版の Visual Studio については、「[What's new for Visual C++ in Visual Studio](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)」 (Visual Studio における Visual C++ の新機能) と「[Conformance Improvements in Visual C++ in Visual Studio](../overview/cpp-conformance-improvements.md)」 (Visual Studio における Visual C++ の準拠の強化) を参照してください。

> [!NOTE]
> Visual Studio 2015 と Visual Studio 2017 では、バイナリに関して重大な変更はありません。

Visual Studio の新しいバージョンにアップグレードすると、以前にコンパイルと動作が正常に行えたコードでコンパイルやランタイム エラーが発生する場合があります。 新しいバージョンでこのような問題を引き起こす変更は *互換性に影響する変更*と呼ばれ、通常は C++ 言語の基準、関数シグネチャ、またはメモリ オブジェクトのレイアウトの変更によって必要となります。

検出や診断が難しいランタイム エラーを回避するには、異なるバージョンのコンパイラを使用してコンパイルされたバイナリには静的にリンクしないことをお勧めします。 また、EXE または DLL プロジェクトをアップグレードする場合、リンクするライブラリもアップグレードします。 異なるバージョンのコンパイラを使用してコンパイルされたバイナリ間 (DLL を含む) で CRT (C Runtime) または C++ 標準ライブラリ (C++ Standard Library) 型を渡さないようにしてください。 詳細については、「 [Potential Errors Passing CRT Objects Across DLL Boundaries](../c-runtime-library/potential-errors-passing-crt-objects-across-dll-boundaries.md)」を参照してください。

COM インターフェイスまたは POD オブジェクトではないオブジェクトで、特定のレイアウトに依存するコードを記述しないでください。 このようなコードを記述している場合、アップグレード後に動作することを確認する必要があります。 詳細については、「[ABI の境界での移植性](../cpp/portability-at-abi-boundaries-modern-cpp.md)」を参照してください。

また、コンパイラの準拠に関する継続的な強化によって、コンパイラが既存のソース コードを認識する方法が変わる可能性があります。 たとえば、以前にビルドして問題なく実行できていたコードでも、ビルド時に新しいエラーや異なるエラーが発生したり、動作が変わったりする可能性があります。 これらの機能強化は、このドキュメントで説明しているような破壊的変更ではありませんが、問題を解決するためにソース コードの変更が必要な場合があります。

- [C ランタイム (CRT) ライブラリの互換性に影響する変更点](#BK_CRT)

- [標準 C++ と C++ 標準ライブラリの互換性に影響する変更](#BK_STL)

- [MFC と ATL の互換性に影響する変更点](#BK_MFC)

- [コンカレンシー ランタイムの互換性に影響する変更点](#BK_ConcRT)

## <a name="VC_2015"></a> Visual Studio 2015 の準拠に関する変更

###  <a name="BK_CRT"></a> C ランタイム ライブラリ (CRT)

#### <a name="general-changes"></a>一般的な変更

- **リファクタリング バイナリ**

   CRT ライブラリは 2 つの異なるバイナリにリファクタリングされています。その 1 つはユニバーサル CRT (ucrtbase) で、標準機能のほとんどが含まれています。もう 1 つは VC ランタイム ライブラリ (vcruntime) です。 vcruntime ライブラリには、例外処理や組み込み関数などのコンパイラ関連の機能が含まれています。 既定のプロジェクト設定を使用している場合は、この変更による影響は受けません。リンカーは、新しい既定のライブラリを自動的に使用するためです。 プロジェクトの **[リンカー]** プロパティの **[すべての既定のライブラリの無視]** を **[はい]** に設定するか、コマンドラインで `/NODEFAULTLIB` リンカー オプションを使用する場合、( **[追加の依存ファイル]** プロパティの) ライブラリのリストを更新して、新しいリファクタリング ライブラリを組み込む必要があります。 古い CRT ライブラリ (libcmt.lib、libcmtd.lib、msvcrt.lib、msvcrtd.lib) をリファクタリングした同等のライブラリで置き換えます。 2 つのリファクタリング ライブラリのそれぞれについて、静的 (.lib) バージョンと動的 (.dll) バージョンがあり、リリース (サフィックスなし) バージョンとデバッグ (サフィックス "d" を持つ) バージョンがあります。 動的バージョンには、リンク先インポート ライブラリがあります。 2 つのリファクタリング ライブラリとは、ユニバーサル CRT (具体的には ucrtbase.dll または ucrtbase.lib、ucrtbased.dll または ucrtbased.lib)、と VC ランタイム ライブラリ (libvcruntime.lib、vcruntime*version*.dll、libvcruntimed.lib、vcruntimed*version*.dll) です。 Visual Studio 2015 と Visual Studio 2017 における*バージョン*は 140 です。 「 [CRT Library Features](../c-runtime-library/crt-library-features.md)」を参照してください。

#### <a name="localeh"></a>\<locale.h>

- **localeconv**

   現在、locale.h で宣言される [localeconv](../c-runtime-library/reference/localeconv.md) 関数は、[スレッドごとのロケール](../parallel/multithreading-and-locales.md)が有効なときに正常に機能します。 以前のバージョンのライブラリでは、この関数はスレッドのロケールではなくグローバル ロケールの `lconv` データを返していました。

   スレッドごとのロケールを使用する場合は、`localeconv` の使用を確認する必要があります。 コードで、返される `lconv` データがグローバル ロケール用であることを前提とする場合は、それを修正する必要があります。

#### <a name="mathh"></a>\<math.h>

- **数値演算ライブラリ関数の C++ のオーバーロード**

   以前のバージョンでは、\<math.h> は、数値演算ライブラリ関数の C++ オーバーロードのいくつか (すべてではない) を定義していました。 残りのオーバーロードは、\<cmath > ヘッダーにありました。 \<math.h> だけしか組み込まれていないコードでは、関数のオーバーロードの解決方法に問題が生じていました。 現在は、C++ オーバーロードが \<math.h> から削除されており、\<cmath> にのみ存在しています。

   エラーを解決するには、\<math.h> から削除された関数の宣言を取得する \<cmath> を組み込んでください。 次の関数は移動されました。

  - `double abs(double)` および `float abs(float)`

  - `double pow(double, int)`、`float pow(float, float)`、`float pow(float, int)`、`long double pow(long double, long double)`、`long double pow(long double, int)`

  - `float` および `long double` バージョンの浮動小数点関数 `acos`、`acosh`、`asin`、`asinh`、`atan`、`atanh`、`atan2`、`cbrt`、`ceil`、`copysign`、`cos`、`cosh`、`erf`、`erfc`、`exp`、`exp2`、`expm1`、`fabs`、`fdim`、`floor`、`fma`、`fmax`、`fmin`、`fmod`、`frexp`、`hypot`、`ilogb`、`ldexp`、`lgamma`、`llrint`、`llround`、`log`、`log10`、`log1p`、`log2`、`lrint`、`lround`、`modf`、`nearbyint`、`nextafter`、`nexttoward`、`remainder`、`remquo`、`rint`、`round`、`scalbln`、`scalbn`、`sin`、`sinh`、`sqrt`、`tan`、`tanh`、`tgamma`、および `trunc`

  `abs`math.h> ヘッダーだけが組み込まれている浮動小数点型の \< を使用するコードがある場合、浮動小数点バージョンは使用できなくなります。 エラーを生成する浮動小数点引数を持つ場合でも、現在は `abs(int)` の呼び出しで解決します。

    ```Output
    warning C4244: 'argument' : conversion from 'float' to 'int', possible loss of data
    ```

  この警告の修正方法は、`abs` の呼び出しを、`abs` の浮動小数点バージョン (double 引数の場合は `fabs`、float 引数の場合は `fabsf`) で置き換えるか、\<cmath> ヘッダーを組み込んで `abs` を引き続き使用するかのどちらかです。

- **浮動小数点の準拠**

   NaNs 値や無限大値などの特殊なケースの入力に関する IEEE-754 仕様および C11 Annex F 仕様に対する準拠を改善するために、多くの変更が数値演算ライブラリに対して加えられています。 たとえば、簡易な NaN 入力 (以前のバージョンのライブラリでは、多くの場合、エラーとして扱われていた) はエラーとして扱われなくなりました。 [IEEE 754 標準](https://standards.ieee.org/standard/754-2008.html) と [C11 標準](http://www.iso-9899.info/wiki/The_Standard)の付録 F をご覧ください。

   これらの変更によってコンパイル時エラーが発生することはありませんが、プログラムの動作が変わる可能性はあり、標準に従ってより正確に動作するようになる可能性があります。

- **FLT_ROUNDS**

   Visual Studio 2013 で FLT_ROUNDS マクロは定数式に拡張されましたが、これは正しくありませんでした。丸めモードは実行時に (たとえば、fesetround を呼び出すことにより) 構成することができるからです。 FLT_ROUNDS マクロは動的になり、現在の丸めモードを正確に反映します。

#### <a name="new-and-newh"></a>\<new> と \<new.h>

- **new と delete**

   以前のバージョンのライブラリでは、実装定義演算子の new 関数と delete 関数は、ランタイム ライブラリ DLL (たとえば、msvcr120.dll) からエクスポートされていました。 現在、これらの演算子関数は常に (ランタイム ライブラリ DLL を使用する場合でも) 静的にバイナリにリンクされています。

   これはネイティブ コードまたは混合コード (`/clr`) の破壊的変更ではありませんが、[/clr:pure](../build/reference/clr-common-language-runtime-compilation.md) としてコンパイルされるコードでは、この変更によってコードのコンパイルが失敗する可能性があります。 コードを `/clr:pure` としてコンパイルする場合、`#include <new>` または `#include <new.h>` を追加してこの変更によるビルド エラーを回避する必要があります。 Visual Studio 2015 では `/clr:pure` オプションは非推奨とされており、Visual Studio 2017 ではサポートされていません。 "ピュア" でなければならないコードは C# に移植する必要があります。

#### <a name="processh"></a>\<process.h>

- **_beginthread および _beginthreadex**

   現在、[_beginthread](../c-runtime-library/reference/beginthread-beginthreadex.md) 関数と [_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md) 関数には、モジュールへの参照が含まれています。そのモジュールで、スレッドの期間に関するスレッド プロシージャが定義されています。 これは、スレッドの実行が完了するまでモジュールが確実にアンロードされないようにするのに役立ちます。

#### <a name="stdargh"></a>\<stdarg.h>

- **va_start と参照型**

   C++ コードをコンパイルするときに、渡される引数が参照型でないことが、現在 [va_start](../c-runtime-library/reference/va-arg-va-copy-va-end-va-start.md) によりコンパイル時に検証されるようになりました。 参照型の引数は、C++ 標準では禁止されています。

#### <a name="stdio_and_conio"></a>\<stdio > と \<conio .h >

- **現在、関数の printf ファミリと scanf ファミリは、インラインで定義されています。**

   `printf` 関数と `scanf` 関数すべての定義は、\<stdio.h>、\<conio.h>、およびその他の CRT ヘッダーにインラインで移動されました。 この破壊的変更は、プログラムで適切な CRT ヘッダーが組み込まれずにこれらの関数をローカルで宣言した場合にリンカー エラー (LNK2019、外部シンボルは未解決です) につながります。 可能な場合、CRT ヘッダーが組み込まれるよう (つまり、`#include <stdio.h>` を追加するよう) またインライン関数が組み込まれるようコードを更新してください。これらのヘッダー ファイルが組み込まれるようコードを変更しない場合、別の方法として、付加的なライブラリをリンカー入力 legacy_stdio_definitions.lib に追加することもできます。

   このライブラリを IDE のリンカー入力に追加するには、プロジェクト ノードのコンテキスト メニューを開き、 **[プロパティ]** を選択し、 **[プロジェクトのプロパティ]** ダイアログ ボックスで **[リンカー]** を選択し、 **[リンカー入力]** を編集して `legacy_stdio_definitions.lib` をセミコロン区切りリストに追加します。

   プロジェクトが、2015 より前のリリースの Visual Studio でコンパイルされた静的ライブラリとリンクする場合、リンカーによって、未解決の外部シンボルが報告される可能性があります。 これらのエラーは、`_iob`、`_iob_func`、または \<imp 形式の特定の \*stdio.h> 関数の関連インポートの内部定義を参照する可能性があります。 Microsoft は、プロジェクトをアップグレードするときに、最新バージョンの C++ コンパイラおよびライブラリですべての静的ライブラリを再コンパイルすることを推奨しています。 ライブラリが、ソースを使用できないサード パーティ ライブラリである場合、更新されたバイナリをサード パーティから要求するか、そのライブラリの使用を、古いバージョンのコンパイラおよびライブラリでコンパイルする別個の DLL にカプセル化する必要があります。

    > [!WARNING]
    > Windows SDK 8.1 以前とリンクする場合、これらの未解決外部シンボル エラーが発生する可能性があります。 その場合、前述のように、legacy_stdio_definitions.lib をリンカー入力に追加することにより、エラーを解決する必要があります。

   未解決シンボル エラーのトラブルシューティングを実行するには、[dumpbin.exe](../build/reference/dumpbin-reference.md) を使用して、バイナリで定義されているシンボルを調べることができます。 次のコマンド ラインを試行して、ライブラリで定義されているシンボルを表示してください。

    ```cpp
    dumpbin.exe /LINKERMEMBER somelibrary.lib
    ```

- **gets および _getws**

   [gets](../c-runtime-library/gets-getws.md) 関数と [_getws](../c-runtime-library/gets-getws.md) 関数が削除されました。 gets 関数は、安全に使用できないため、C11 の標準ライブラリから削除されました。 _getws 関数は、gets に相当する Microsoft 拡張です (ただしワイド文字列)。 これらの関数の代わりとして、[fgets](../c-runtime-library/reference/fgets-fgetws.md)、[fgetws](../c-runtime-library/reference/fgets-fgetws.md)、[gets_s](../c-runtime-library/reference/gets-s-getws-s.md)、および [_getws_s](../c-runtime-library/reference/gets-s-getws-s.md) の使用を検討してください。

- **_cgets および _cgetws**

   [_cgets](../c-runtime-library/cgets-cgetws.md) 関数と [_cgetws](../c-runtime-library/cgets-cgetws.md) 関数は削除されました。 これらの関数の代わりに、[_cgets_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) と [_cgetws_s](../c-runtime-library/reference/cgets-s-cgetws-s.md) の使用を検討してください。

- **無限大および NaN の書式設定**

   以前のバージョンでは、無限大および NaNs は、MSVC 固有の sentinel 文字列のセットを使用して書式設定されていました。

  - 無限大: 1.#INF

  - 簡易な NaN: 1.#QNAN

  - シグナリング NaN: 1.#SNAN

  - 無限大 NaN: 1.#IND

  これらの書式設定にはすべて、プレフィックスとして符号が付けられていた可能性があります。また、書式設定はフィールドの幅と精度に応じて若干異なる可能性があります (まれな例として、`printf("%.2f\n", INFINITY)` は 1.#J と出力されます。これは、#INF が 2 桁の精度に "丸められた" ためです)。 C99 で、無限大と NaNs の書式設定の方法に関して新たな要件が導入されました。 現在、MSVC の実装は、これらの要件に準拠しています。 新しい文字列は、次のとおりです。

  - 無限台: inf

  - 簡易な NaN: nan

  - シグナリング NaN: nan(snan)

  - 不定値 NaN: nan(ind)

  これらにはすべて、プレフィックスとして符号が付けられます。 大文字の書式指定子が使用される場合 (%f ではなく %F)、文字列は大文字で出力されます (`INF` ではなく `inf`)。これは必須です。

  [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md) 関数はこれらの新しい文字列を解析するよう変更され、これらの文字列は、`printf` および `scanf` によってラウンド トリップされます。

- **浮動小数点の書式設定と解析**

   新しい浮動小数点の書式設定と解析のアルゴリズムが導入され、正確性が向上しました。 この変更は、関数ファミリ [printf](../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md) や [scanf](../c-runtime-library/reference/scanf-scanf-l-wscanf-wscanf-l.md)、[strtod](../c-runtime-library/reference/strtod-strtod-l-wcstod-wcstod-l.md) などの関数に影響を与えます。

   従来の書式設定アルゴリズムでは、限られた桁数のみを生成し、残りの小数点以下表示桁数はゼロで埋められていました。 通常は、元の浮動小数点の値にラウンドトリップする文字列を生成できましたが、正確な値 (またはそれに最も近い 10 進表現) が必要な場合は十分ではありませんでした。 新しい書式設定アルゴリズムでは、値を表す (または指定された有効桁数を埋める) ために必要な桁数が生成されます。 改善の一例として、大きな 2 の冪の出力結果をご覧ください。

    ```cpp
    printf("%.0f\n", pow(2.0, 80))
    ```

   古い出力:

    ```Output
    1208925819614629200000000
    ```

   新しい出力:

    ```Output
    1208925819614629174706176
    ```

   従来の解析アルゴリズムでは、入力文字列の最大 17 桁の有効桁数のみが考慮され、残りの桁は破棄されていました。 文字列によって表される値に近い概算値を生成するにはこれで十分であり、結果は通常、正しく丸められた結果に非常に近い値になっていました。 新しい実装では、存在するすべての桁数を考慮に入れ、すべての入力を正しく丸めた結果が生成されます (最大長 768 桁)。 加えて、現在、これらの関数は丸めモードを採用しています (fesetround によって制御可能)。  これらの関数は異なる結果を出力する可能性があるため、これは動作の破壊的変更になります。 新しい結果は常に、古い結果より正しくなります。

- **16 進数および無限大/NaN 浮動小数点の解析**

   前述のとおり、現在、浮動小数点の解析アルゴリズムは、16 進数の浮動小数点文字列 (%a および %A printf 書式指定子によって生成されるものなど) および `printf` 関数によって生成されるすべての無限大および NaN 文字列を解析します。

- **%A および %a のゼロ パディング**

   %a および %A 書式指定子は、浮動小数点の数値を、16 進数の仮数部およびバイナリの指数として書式設定します。 以前のバージョンでは、`printf` 関数は文字列をゼロで埋め込んでいましたが、それは正しくありませんでした。 たとえば、`printf("%07.0a\n", 1.0)` は 00x1p+0 と出力されますが、本来、print 0x01p+0 と出力されるべきです。 この問題は修正されました。

- **%A と %a の有効桁数**

   %A と %a の書式指定子の既定の有効桁数は、以前のバージョンのライブラリでは 6 桁でした。 現在、既定の有効桁数は、C 標準に準拠して 13 桁です。

   これは、%A または %a を持つ書式文字列を使用する関数の出力におけるランタイム動作の変更です。 従来の動作では、%A 指定子を使用する出力は "1.1A2B3Cp+111" でした。 現在、同じ値の出力は "1.1A2B3C4D5E6F7p+111" です。 従来の動作を取得するには、有効桁数を指定します (たとえば %.6A)。 「[精度指定](../c-runtime-library/format-specification-syntax-printf-and-wprintf-functions.md#precision)」を参照してください。

- **%F 指定子**

   現在、%F 書式/変換指定子がサポートされています。 無限大と NaNs が大文字で書式設定される点を除き、機能的には %f 書式指定子と同等です。

   以前のバージョンでは、実装で F と N を長さの修飾子として使用していました。 この動作は、アドレス空間がセグメント化されていた時代に由来するもので、これらの長さ修飾子は、遠近ポインター (それぞれ %Fp、%Ns) を示すために使用されていました。 この動作は削除されました。 現在、%F を検出した場合、%F 書式指定子として扱われます。%N を検出した場合、無効なパラメーターとして扱われます。

- **指数の書式設定**

   %e および %E 書式指定子は、浮動小数点の数値を、10 進数の仮数部および指数として書式設定します。 場合によっては、%g および %G 書式指定子もこの形式で数値を書式設定します。 以前のバージョンでは、CRT は 3 桁の指数部を持つ文字列を常に生成していました。 たとえば、`printf("%e\n", 1.0)` により 1.000000e+000 が出力されていましたが、これは正しくありませんでした。 C では、指数部を 1 桁または 2 桁のみを使って表すことができる場合、2 桁のみを出力する必要があります。

   Visual Studio 2005 では、グローバル準拠スイッチ [_set_output_format](../c-runtime-library/set-output-format.md) が追加されました。 プログラムは、この関数を引数 _TWO_DIGIT_EXPONENT を使って呼び出し、指数部出力の準拠を有効にすることができました。 既定の動作が変更され、標準に準拠する指数印刷モードに変更なりました。

- **書式文字列の検証**

   以前のバージョンでは、`printf` 関数と `scanf` 関数により、多くの無効な書式文字列が自動的に受け入れられていました。ただし、ときどき普通でない影響が生じていました。 たとえば、%hlhlhld は %d として扱われていました。 現在、無効な書式文字列はすべて、無効なパラメーターとして扱われます。

- **fopen モードの文字列の検証**

   以前のバージョンでは、`fopen` 関数ファミリにより、一部の無効なモード文字列が自動的に受け入れられていました (`r+b+`など)。 現在、無効なモード文字列は検出され、無効なパラメーターとして扱われます。

- **_O_U8TEXT モード**

   現在、[_setmode](../c-runtime-library/reference/setmode.md) 関数は、_O_U8TEXT モードで開かれるストリームのモードを正しく報告します。 以前のバージョンのライブラリでは、そのようなストリームは _O_WTEXT で開かれるものとして報告されていました。

   エンコードが UTF-8 のストリームの _O_WTEXT モードをコードが解釈する場合、これは互換性に影響する変更です。 アプリケーションで UTF_8 がサポートされていない場合、増加するこの共通エンコードのサポートを追加することを検討してください。

- **snprintf および vsnprintf**

   現在、[snprintf](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md) 関数と [vsnprintf](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md) 関数が実装されています。 古いコードは CRT ライブラリによって実装されていなかったため、これらの関数の定義マクロ バージョンを提供していました。しかし、新しいバージョンではこれらが不要になりました。 [stdio.h> を組み込む前に ](../c-runtime-library/reference/snprintf-snprintf-snprintf-l-snwprintf-snwprintf-l.md)snprintf[ または ](../c-runtime-library/reference/vsnprintf-vsnprintf-vsnprintf-l-vsnwprintf-vsnwprintf-l.md)vsnprintf\< がマクロとして定義されている場合、現在コンパイルは、マクロが定義された場所を示すエラーとともに失敗します。

   通常、この問題は、ユーザー コードの `snprintf` または `vsnprintf` の宣言を削除することによって修正されます。

- **tmpnam は使用可能なファイル名を生成する**

   以前のバージョンでは、`tmpnam` 関数および `tmpnam_s` 関数は、ドライブのルートにファイル名を生成していました (\sd3c など)。 現在、これらの関数は、一時ディレクトリに使用可能なファイル名パスを生成します。

- **FILE カプセル化**

   以前のバージョンでは、完全なファイルの種類は \<stdio > でパブリックに定義されているので、ユーザーコードはファイルに接続してその内部を変更することができました。 ライブラリが変更され、実装に関する詳細が隠されるようになりました。 この変更の一環として、現在、\<stdio.h> で定義される FILE は不透明な型であり、そのメンバーは、CRT 自体の外部からアクセスできません。

- **_outp および _inp**

   関数 [_outp](../c-runtime-library/outp-outpw-outpd.md)、[_outpw](../c-runtime-library/outp-outpw-outpd.md)、[_outpd](../c-runtime-library/outp-outpw-outpd.md)、[_inp](../c-runtime-library/inp-inpw-inpd.md)、[_inpw](../c-runtime-library/inp-inpw-inpd.md)、および [_inpd](../c-runtime-library/inp-inpw-inpd.md) が削除されました。

#### <a name="stdlibh-malloch-and-sysstath"></a>\<stdlib.h>、\<malloc.h>、および \<sys/stat.h>

- **strtof および wcstof**

   値を float として表せない場合に、`strtof` 関数および `wcstof` 関数で `errno` を ERANGE に設定できませんでした。 このエラーはこれら 2 つの関数に固有のものでした。`strtod` 関数、`wcstod` 関数、`strtold` 関数、および `wcstold` 関数は影響を受けませんでした。 この問題は修正されており、ランタイムの破壊的変更です。

- **整列された割り当て関数**

   以前のバージョンでは、整列された割り当て関数 (`_aligned_malloc`、`_aligned_offset_malloc` など) は、整列が 0 のブロックに関する要求を自動的に受け入れていました。 要求された整列は 2 のべき乗でなければならず、ゼロは不可でした。 整列が 0 の要求は現在、無効なパラメーターとして扱われます。 この問題は修正されており、ランタイムの破壊的変更です。

- **ヒープ関数**

   `_heapadd` 関数、`_heapset` 関数、および `_heapused` 関数は削除されました。 Windows ヒープを使用するよう CRT が更新されたため、これらの関数は機能しなくなりました。

- **smallheap**

   `smallheap` リンク オプションは削除されました。 「 [Link Options](../c-runtime-library/link-options.md)」を参照してください。

#### <a name="stringh"></a>\<string.h>

- **wcstok**

   `wcstok` 関数のシグネチャが変更され、C 標準で必要なものと一致するようになりました。 以前のバージョンのライブラリでは、この関数のシグネチャは次のとおりでした。

    ```cpp
    wchar_t* wcstok(wchar_t*, wchar_t const*)
    ```

   `strtok` と同様、これはスレッドごとの内部コンテキストを使用して、呼び出しの状態を追跡していました。 現在、この関数のシグネチャは `wchar_t* wcstok(wchar_t*, wchar_t const*, wchar_t**)` になり、呼び出し元は関数に対する 3 番目の引数としてコンテキストを渡すことが必須になりました。

   古いシグネチャとともに新しい `_wcstok` 関数が追加され、移植が簡単になりました。 C++ コードをコンパイルする際にも、古いシグネチャを持つ `wcstok` のインライン オーバーロードが存在します。 このオーバーロードは、非推奨として宣言されます。 C コードでは、_CRT_NON_CONFORMING_WCSTOK を定義し、`_wcstok` の代わりに `wcstok` が使用されるようにすることもできます。

#### <a name="timeh"></a>\<time.h>

- **clock**

   以前のバージョンでは、Windows API [GetSystemTimeAsFileTime](../c-runtime-library/reference/clock.md) を使用して [clock](/windows/win32/api/sysinfoapi/nf-sysinfoapi-getsystemtimeasfiletime) 関数が実装されていました。 この実装により、clock 関数はシステム時刻の影響を受け、単調になることがありませんでした。 現在は、 [QueryPerformanceCounter](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) によって clock 関数が再実装されたため、単調になっています。

- **fstat および _utime**

   以前のバージョンでは、[_stat](../c-runtime-library/reference/stat-functions.md) 関数、[fstat](../c-runtime-library/reference/fstat-fstat32-fstat64-fstati64-fstat32i64-fstat64i32.md)関数、および [_utime](../c-runtime-library/reference/utime-utime32-utime64-wutime-wutime32-wutime64.md) 関数での夏時間の処理が正しくありませんでした。 Visual Studio 2013 より前では、これらの関数はすべて、標準時刻をあたかも夏時間にあるかのようにに調整していましたが、これは正しい処理ではありませんでした。

   Visual Studio 2013 では、 **_stat** 関数ファミリでは問題が解決されましたが、**fstat** 関数ファミリと **_utime** 関数ファミリでは修正されていませんでした。 この部分的な修正は、関数間の不整合による問題につながっていました。 **fstat** および **_utime** の関数ファミリは現在修正され、これらすべての関数が、正確かつ一貫して夏時間を処理できるようになりました。

- **asctime**

   以前のバージョンでは、[asctime](../c-runtime-library/reference/asctime-wasctime.md) 関数は、1 桁の日の先頭をゼロで埋めていました (たとえば、`Fri Jun 06 08:00:00 2014`)。 この仕様では、そのような日の先頭を空白で埋める必要があります (たとえば、`Fri Jun  6 08:00:00 2014`)。 この問題は修正されています。

- **strftime および wcsftime**

   `strftime` 関数と `wcsftime` 関数は、書式指定子として %C、%D、%e、%F、%g、%G、%h、%n、%r、%R、%t、%T、%u、および %V をサポートしています。 さらに、E 修飾子と O 修飾子は、解析はされますが、無視されます。

   %c 書式指定子は、現行ロケールの "適切な日時の表記" を生成するものとして指定されます。 C ロケールでは、`%a %b %e %T %Y` で生成されるのと同じ書式である `asctime` と同じになるよう、この表記が必要です。 以前のバージョンでは、%c 書式指定子は `MM/DD/YY HH:MM:SS` 表記を使用して時刻を書式設定していましたが、これは正しくありませんでした。 この問題は修正されています。

- **timespec および TIME_UTC**

   \<time.h> ヘッダーは、C11 標準の `timespec` 型と `timespec_get` 関数を定義します。 さらに、現在、`timespec_get` 関数で使用する TIME_UTC マクロが定義されています。 この更新は、その識別子のいずれかの定義が競合しているコードに関して、破壊的変更です。

- **CLOCKS_PER_SEC**

   現在、CLOCKS_PER_SEC マクロは `clock_t` 型の整数に拡張されており、これは C 言語で必要です。

####  <a name="BK_STL"></a> C++ 標準ライブラリ

新しい最適化とデバッグのチェックを有効にするために、C++ 標準ライブラリの Visual Studio の実装では、バイナリの互換性がバージョンごとに意図的に保たれていません。 そのため、C++ 標準ライブラリを使用すると、異なるバージョンを使用してコンパイルされたオブジェクト ファイルとスタティック ライブラリは 1 つのバイナリ (EXE または DLL) に混在させることができず、C++ 標準ライブラリ オブジェクトは異なるバージョンを使用してコンパイルされたバイナリ間で渡すことができません。 混在があると、_MSC_VER の不一致に関するリンカー エラーが発生します (_MSC_VER は、コンパイラのメジャーバージョンを含むマクロです。たとえば、Visual Studio 2013 の場合は1800です)。このチェックでは、DLL の混在を検出できず、Visual Studio 2008 以前のバージョンを含む混在を検出することはできません。

- **C++ 標準ライブラリ インクルード ファイル**

   C++ 標準ライブラリのヘッダーのインクルード構造に対していくつかの変更が加えられました。 C++ 標準ライブラリ ヘッダーは、指定されていない方法での相互インクルードを許可されています。 一般に、C++ 標準に応じて必要なすべてのヘッダーを注意深くインクルードし、どの C++ 標準ライブラリ ヘッダーにどの C++ 標準ライブラリ ヘッダーが含まれるかは関係ないようにするようコードを記述する必要があります。 これにより、バージョン間およびプラットフォーム間でのコードの移植が可能になります。 少なくとも Visual Studio 2015 でのヘッダーに関する 2 つの変更がユーザー コードに影響を与えます。 1 つ目として、\<string> に \<iterator> が含まれなくなりました。 2 つ目として、現在、\<tuple> は、すべての `std::array`array> は含まない \< を宣言します。これは、次のコード構成体の組み合わせによってコードに障害を起こす可能性があります。コードに "array" という名前の変数があり、using-directive "using namespace std;" があります。\<tuple> を含む C++ 標準ライブラリ ヘッダー (\<functional> など) を組み込みますが、これは現在、`std::array` を宣言します。

- **steady_clock**

   \<steady_clock[ の ](../standard-library/steady-clock-struct.md)chrono> 実装が変更され、安定性と単調性のための C++ 標準の要件を満たすようになりました。 現在、`steady_clock` は [QueryPerformanceCounter()](/windows/win32/api/profileapi/nf-profileapi-queryperformancecounter) に基づき、`high_resolution_clock` は `steady_clock` の typedef です。 結果として、Visual Studio では現在、`steady_clock::time_point` は `chrono::time_point<steady_clock>` の typedef です。ただし、他の実装では異なる場合があります。

- **アロケーターおよび const**

   現在、両サイドで const 引数を受け入れるには、アロケーターの等価/非等価の比較が必要です。 アロケーターがこれらの演算子をこのように定義する場合、

    ```cpp
    bool operator==(const MyAlloc& other)
    ```

   それを更新して、const メンバーとして宣言する必要があります。

    ```cpp
    bool operator==(const MyAlloc& other) const
    ```

- **const 要素**

   C++ 標準では常に const 要素のコンテナーが禁止されてきました (vector\<const T> or set\<const T> など)。 Visual Studio 2013 以前では、そのようなコンテナーが受け入れられていました。 現在のバージョンでは、そのようなコンテナーをコンパイルすることはできません。

- **std::allocator::deallocate**

   Visual Studio 2013 以前では、`std::allocator::deallocate(p, n)` は、*n* に対して渡されていた引数を無視していました。  C++ 標準では常に、*p* を返した `allocate` の呼び出しに最初の引数として渡される値と *n* が同等である必要がありました。 しかし、現在のバージョンでは、*n* の値は検査されます。 標準で必要なものとは異なる引数を *n* に渡すコードは、ランタイムにクラッシュする可能性があります。

- **hash_map および hash_set**

   非標準ヘッダー ファイルの \<hash_map> と \<hash_set> は Visual Studio 2015 では非推奨とされており、将来のリリースでは削除されます。 代わりに \<unordered_map> と \<unordered_set> を使用してください。

- **比較子および operator()**

   現在、関連コンテナー (\<map> ファミリー) では、比較子に const を呼び出せる関数呼び出し演算子が必要です。 比較子クラス宣言の次のコードは現在、コンパイルに失敗します。

    ```cpp
    bool operator()(const X& a, const X& b)
    ```

   このエラーを解決するには、関数の宣言を次のように変更します。

    ```cpp
    bool operator()(const X& a, const X& b) const
    ```

- **型の特徴**

   以前のバージョンの C++ ドラフト標準の型の特徴の古い名前が削除されました。 これらは C++11 で変更されており、Visual Studio 2015 では C++11 値に更新されました。 古い名前と新しい名前を次の表に示します。

   |以前の名前|新しい名前|
   |--------------|--------------|
   |add_reference|add_lvalue_reference|
   |has_default_constructor|is_default_constructible|
   |has_copy_constructor|is_copy_constructible|
   |has_move_constructor|is_move_constructible|
   |has_nothrow_constructor|is_nothrow_default_constructible|
   |has_nothrow_default_constructor|is_nothrow_default_constructible|
   |has_nothrow_copy|is_nothrow_copy_constructible|
   |has_nothrow_copy_constructor|is_nothrow_copy_constructible|
   |has_nothrow_move_constructor|is_nothrow_move_constructible|
   |has_nothrow_assign|is_nothrow_copy_assignable|
   |has_nothrow_copy_assign|is_nothrow_copy_assignable|
   |has_nothrow_move_assign|is_nothrow_move_assignable|
   |has_trivial_constructor|is_trivially_default_constructible|
   |has_trivial_default_constructor|is_trivially_default_constructible|
   |has_trivial_copy|is_trivially_copy_constructible|
   |has_trivial_move_constructor|is_trivially_move_constructible|
   |has_trivial_assign|is_trivially_copy_assignable|
   |has_trivial_move_assign|is_trivially_move_assignable|
   |has_trivial_destructor|is_trivially_destructible|

- **launch::any ポリシーと launch::sync ポリシー**

   非標準の `launch::any` と `launch::sync` のポリシーが削除されました。 代わりに、`launch::any` に対して、`launch:async | launch:deferred` を使用します。 `launch::sync` では `launch::deferred` を使用します。 「[launch 列挙型](../standard-library/future-enums.md#launch)」を参照してください。

####  <a name="BK_MFC"></a> MFC と ATL

- **Microsoft Foundation Classes (MFC)**

   はサイズが大きすぎるため、Visual Studio の "標準" インストールから除外されました。 MFC をインストールするには、Visual Studio 2015 セットアップで**カスタム** インストール オプションを選択します。 既に Visual Studio 2015 がインストールされている場合は、**Visual Studio** セットアップを再度実行して MFC をインストールできます。 **カスタム** インストール オプションを選択してから、**Microsoft Foundation Classes** を選択します。 **Visual Studio** セットアップの実行は、**コントロール パネル**のコントロールである**プログラムと機能**か、インストール メディアからすることができます。

   Visual C++ 再頒布可能パッケージにも、引き続きこのライブラリが含まれています。

####  <a name="BK_ConcRT"></a> コンカレンシー ランタイム

- **concurrency::Context::Yield と競合する Windows.h の Yield マクロ**

   以前、同時実行ランタイムは `#undef` を使用して Yield マクロの定義を解除し、Windows.h h で定義されている Yield マクロと `concurrency::Context::Yield` 関数の間の競合を回避していました。 この `#undef` は削除され、競合しない同等の新しい API 呼び出し [concurrency::Context::YieldExecution](../parallel/concrt/reference/context-class.md#yieldexecution) が追加されました。 Yield との競合を回避するには、コードを更新して代わりに `YieldExecution` 関数を呼び出すか、次の例に示すように、呼び出しサイトで `Yield` 関数名をかっこで囲みます。

    ```cpp
    (concurrency::Context::Yield)();
    ```

## <a name="compiler-conformance-improvements-in-visual-studio-2015"></a>Visual Studio 2015 のコンパイラ準拠の強化

以前のバージョンからコードをアップグレードすると、Visual Studio 2015 の準拠に関する強化によるコンパイラ エラーが生じる可能性があります。 これらの強化は、旧バージョンの Visual Studio からのバイナリの互換性に影響する変更ではありませんが、以前にはないコンパイラ エラーが発生する可能性があります。 詳細については、「[Visual C++ 2003 ～ 2015 の新機能](../porting/visual-cpp-what-s-new-2003-through-2015.md)」を参照してください。

Visual Studio 2015 では、コンパイラの準拠に関する継続的な強化によって、コンパイラが既存のソース コードを認識する方法が変わる可能性があります。 その結果、以前にビルドして問題なく実行できていたコードでも、ビルド時に新しいエラーや異なるエラーが発生したり、動作が変わったりする可能性があります。

さいわい、これらの相違点は、ほとんどのソース コードにおいて、ほとんどまたは全く影響を与えません。 これらの相違点に対処するためにソース コードまたはその他の変更が必要な場合、修正は小さく簡単なものになる傾向があります。 以前は問題がなかったソース コードで、変更が必要な *(修正前の)* コード例と、正しい *(修正後の)* コード例を多数紹介します。

これらの変更点はソース コードや他のビルド成果物に影響はあっても、Visual Studio の異なるバージョン間のバイナリの互換性には影響がありません。 *破壊的変更*はより重大で、バイナリの互換性に影響が及ぶ可能性がありますが、このようなバイナリの互換性に影響する変更は、Visual Studio 2013 と Visual Studio 2015 など、Visual Studio のメジャー バージョンが異なる場合にのみ発生します。 Visual Studio 2013 と Visual Studio 2015 の間の互換性に影響する変更点については、「[Visual Studio 2015 の準拠に関する変更](#VC_2015)」を参照してください。

- [Visual Studio 2015 の準拠の強化](#VS_RTM)

- [更新プログラム 1 の準拠の強化](#VS_Update1)

- [更新プログラム 2 の準拠の強化](#VS_Update2)

- [更新プログラム 3 の準拠の強化](#VS_Update3)

###  <a name="VS_RTM"></a> Visual Studio 2015 の準拠の強化

- /Zc:forScope - オプション

   コンパイラ オプション `/Zc:forScope-` は非推奨となりました。今後のリリースからは削除されます。

    ```cpp
    Command line warning  D9035: option 'Zc:forScope-' has been deprecated and will be removed in a future release
    ```

   このオプションは通常、標準ではスコープから外れるポイントの後のループ変数を使用する、非標準のコードを許可するために使用されていました。 これは `/Za` オプションを使ってコンパイルするときにのみ必要でした。`/Za` がない場合は、ループの後でも常に for ループ変数が使用できるからです。 標準への準拠を考慮しない場合 (たとえば、コードを他のコンパイラに移植しない場合)、`/Za` オプションをオフにする (または、 **[言語拡張機能の無効化]** プロパティを **[いいえ]** に設定する) こともできます。 移植可能で標準に準拠したコードの記述を考慮する場合、標準に準拠するようコードを再記述する必要があります。そのためには、変数の宣言をループの外側に移動します。

    ```cpp
    // C2065 expected
    int main() {
        // Uncomment the following line to resolve.
        // int i;
        for (int i = 0; i < 1; i++);
        i = 20;   // i has already gone out of scope under /Za
    }
    ```

- `/Zg` コンパイラ オプション

   `/Zg` コンパイラ オプション (関数プロトタイプの生成) は使用できなくなりました。 前バージョンで、このコンパイラ オプションは非推奨とされました。

- mstest.exe のコマンド ラインから C++/CLI で単体テストを実行できなくなりました。 代わりに、vstest.console.exe を使用します。 「[VSTest.Console.exe のコマンド ライン オプション](/visualstudio/test/vstest-console-options)」を参照してください。

- **mutable キーワード**

   **mutable** ストレージ クラス指定子は、エラーなしで以前コンパイルされていた場所で使用できなくなりました。 現在、コンパイラによってエラー C2071 (無効なストレージ クラス) が出されます。 標準では、**mutable** 指定子はクラスのデータ メンバーの名前にのみ適用でき、const または static として宣言された名前には適用できません。また、参照メンバーにも適用できません。

   次に例を示します。

    ```cpp
    struct S
    {
        mutable int &r;
    };
    ```

   以前のバージョンのコンパイラはこれを受け入れていましたが、現在のコンパイラでは次のエラーが出されます。

    ```Output
    error C2071: 'S::r': illegal storage class
    ```

   エラーを修正するには、冗長な **mutable** キーワードを削除します。

- **char_16_t と char32_t**

   `char16_t` または `char32_t` を **typedef** の別名として使用できなくなりました。これらの型は現在、組み込みとして扱われているからです。 ユーザーやライブラリ作成者は、`char16_t` および `char32_t` を `uint16_t` および `uint32_t` の別名として定義するのが一般的でした。

    ```cpp
    #include <cstdint>

    typedef uint16_t char16_t; //C2628
    typedef uint32_t char32_t; //C2628

    int main(int argc, char* argv[])
    {
        uint16_t x = 1; uint32_t y = 2;
        char16_t a = x;
        char32_t b = y;
        return 0;
    }
    ```

   コードを更新するには、**typedef** 宣言を削除してこれらの名前と競合するその他の ID の名前を変更します。

- **非型テンプレート パラメーター**

   非型テンプレート パラメーターを含む特定のコードは現在、明示的なテンプレート引数を指定すると、型の互換性について正しくチェックされます。 たとえば、次のコードは、以前のバージョンの Visual Studio でエラーなしでコンパイルしたものです。

    ```cpp
    struct S1
    {
        void f(int);
        void f(int, int);
    };

    struct S2
    {
        template <class C, void (C::*Function)(int) const> void f() {}
    };

    void f()
    {
        S2 s2;
        s2.f<S1, &S1::f>();
    }
    ```

   現在のコンパイラは、正しくエラーを出します。テンプレート パラメーターの型がテンプレートの引数と一致しないからです (パラメーターは const メンバーへのポインターですが、関数 f は非 const です)。

    ```Output
    error C2893: Failed to specialize function template 'void S2::f(void)'note: With the following template arguments:note: 'C=S1'note: 'Function=S1::f'
    ```

   コードのこのエラーに対処するには、使用するテンプレート引数の型が、テンプレート パラメーターの宣言された型と一致することを確認してください。

- **__declspec(align)**

   コンパイラは関数で `__declspec(align)` を受け入れなくなりました。 このコンストラクトは常に無視されていましたが、コンパイラ エラーを生成するようになりました。

    ```cpp
    error C3323: 'alignas' and '__declspec(align)' are not allowed on function declarations
    ```

   この問題を修正するには、関数の宣言から `__declspec(align)` を削除してください。 これは影響がなかったため、削除しても何も変わりません。

- **例外処理**

   例外処理への変更がいくつかあります。 まず、例外オブジェクトはコピー可能または移動可能にする必要があります。 次のコードは、Visual Studio 2013 ではコンパイルされますが、Visual Studio 2015 ではコンパイルされません。

    ```cpp
    struct S
    {
    public:
        S();
    private:
        S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   問題は、コピー コンストラクターはプライベートであるために通常の例外処理とは異なりオブジェクトをコピーできないことです。 コピー コンストラクターが **explicit** として宣言されている場合も同じことが当てはまります。

    ```cpp
    struct S
    {
        S();
        explicit S(const S &);
    };

    int main()
    {
        throw S(); // error
    }
    ```

   コードを更新するには、例外オブジェクトのコピー コンストラクターが **public** であり、**explicit** とマークされていないことを確認します。

   値によって例外をキャッチする場合も、例外オブジェクトをコピー可能にする必要があります。 次のコードは、Visual Studio 2013 ではコンパイルされますが、Visual Studio 2015 ではコンパイルされません。

    ```cpp
    struct B
    {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {};

    int main()
    {
        try
        {
        }
        catch (D d) // error
        {
        }
    }
    ```

   この問題を解決するには、**catch** のパラメーターの型を参照に変更します。

    ```cpp
    catch (D& d)
    {
    }
    ```

- **マクロに続く文字列リテラル**

   このバージョンでは、コンパイラはユーザー定義リテラルをサポートするようになりました。 その結果、空白文字の介入がないマクロに続く文字列リテラルはユーザー定義のリテラルとして解釈されます。これにより、エラーまたは予期しない結果が起こる可能性があります。 たとえば、以前のコンパイラでは次のコードが正常にコンパイルされていました。

    ```cpp
    #define _x "there"
    char* func() {
        return "hello"_x;
    }
    int main()
    {
        char * p = func();
        return 0;
    }
    ```

   コンパイラはこのコードを、マクロに続く "hello" というリテラル文字列として解釈していました。これは "there" に拡張され、2 つの文字列リテラルが 1 つに連結されていました。 Visual Studio 2015 では、コンパイラはこのシーケンスをユーザー定義リテラルと解釈しますが、一致するユーザー定義リテラル `_x` が定義されていないため、エラーになります。

    ```Output
    error C3688: invalid literal suffix '_x'; literal operator or literal operator template 'operator ""_x' not found
    note: Did you forget a space between the string literal and the prefix of the following string literal?
    ```

   この問題を解決するには、文字列リテラルとマクロの間に空白に追加します。

- **隣接する文字列リテラル**

   以前と同様、文字列の解析に関連する変更のため、空白なしの隣接する文字列リテラル (ワイド文字列リテラルまたはナロー文字列リテラルのいずれか) は、以前のバージョンの Visual C++ では、単一の連結文字列と解釈されていました。 Visual Studio 2015 では、2 つの文字列間に空白を追加する必要があります。 たとえば、次のコードを変更する必要があります。

    ```cpp
    char * str = "abc""def";
    ```

   この問題を修正するには、2 つの文字列間に空白を追加します。

    ```cpp
    char * str = "abc" "def";
    ```

- **placement new と delete**

   C++14 標準に準拠させるために **delete** 演算子に対して変更が加えられました。 標準の変更について詳しくは、「 [C++ サイズの割り当て解除](https://isocpp.org/files/papers/n3778.html)」をご覧ください。 変更により、size パラメーターを取るグローバルな **delete** 演算子のフォームが追加されます。 互換性に影響する変更は、(**placement new** 演算子と一致させるために) 以前同じシグネチャで **delete** 演算子を使用していた場合、コンパイラ エラーを受け取ります (これは C2956 というエラーで、placement new が使用されるポイントで発生します。それは、一致する適切な **delete** 演算子の識別をコンパイラが試行するコードの場所だからです)。

   関数 `void operator delete(void *, size_t)` は、C++11 の **placement new** 関数 **に対応する**placement delete`void * operator new(size_t, size_t)` 演算子でした。 現在、C++14 サイズの割り当て解除では、この delete 関数は "*通常の解放関数*" (グローバルな **delete** 演算子) です。 標準では、placement new の使用で対応する delete 関数を検索し、通常の解放関数を見つけた場合、プログラムの形式が不適切である必要があります。

   たとえば、コードで **placement new** と **placement delete** の両方を定義するとします。

    ```cpp
    void * operator new(std::size_t, std::size_t);
    void operator delete(void*, std::size_t) noexcept;
    ```

   この問題は、定義した **placement delete** 演算子と新しいグローバル サイズの **delete** 演算子の間の関数シグネチャの一致により発生します。 `size_t`placement new**演算子および**delete**演算子で** とは異なる型を使用できるかどうかを検討してください。 `size_t` **typedef**の型はコンパイラに依存します。MSVC の**符号なし整数**の**typedef**です。 適切なソリューションでは、次のように列挙型を使用します。

    ```cpp
    enum class my_type : size_t {};
    ```

   次に、**placement new** と **delete** の定義を変更し、`size_t` の代わりにこの型を 2 番目の引数として使用します。 placement new の呼び出しを更新して新しい型を渡したり (たとえば、`static_cast<my_type>` を使用することにより整数値から変換する)、**new** と **delete** の定義を更新して整数型にキャスト バックしたりする必要もあります。 これに対して **enum** を使用する必要はありません。`size_t` メンバーを持つクラス型も機能します。

   代わりの方法として、**placement new** を完全に除去することもできます。 コードで **placement new** を使用してメモリ プールを実装する場合 (placement 引数が割り振られるまたは削除されるオブジェクトのサイズである)、独自のカスタム メモリ プール コードをサイズ割り当て解除機能で置き換えるほうが良い可能性があります。配置関数を削除でき、配置関数の代わりに独自の 2 つの引数 **delete** 演算子だけを使用することができます。

   コードを即時に更新しない場合は、コンパイラ オプション `/Zc:sizedDealloc-` を使用して、従来の動作に戻すことができます。 このオプションを使用すると、2 つの引数を持つ delete 関数が存在せず、**placement delete** 演算子との競合は発生しません。

- **共用体データ メンバー**

   共用体データ メンバーで参照型を使用することはできなくなりました。 次のコードは Visual Studio 2013 では正常にコンパイルされますが、Visual Studio 2015 ではエラーになります。

    ```cpp
    union U1
    {
        const int i;
    };
    union U2
    {
        int & i;
    };
    union U3
    {
        struct { int & i; };
    };
    ```

   上のコードを実行すると、次のエラーが生成されます。

    ```Output
    test.cpp(67): error C2625: 'U2::i': illegal union member; type 'int &' is reference type
    test.cpp(70): error C2625: 'U3::i': illegal union member; type 'int &' is reference type
    ```

   この問題に対処するには、参照型をポインターか値に変更します。 ポインターに型を変更する場合、共用体フィールドを使用するコードでの変更が必要です。 コードを値に変更すると、共用体に格納されているデータが変更されます。これは、他のフィールドに影響を与えます。共用体型のフィールドは同じメモリを共有するからです。 値のサイズによっては、共用体のサイズも変更される場合があります。

- 匿名共用体の標準への適合が改善されました。 以前のバージョンのコンパイラでは、匿名共用体に対して明示的なコンストラクターとデストラクターが生成されていました。 これらのコンパイラで生成される関数は、Visual Studio 2015 で削除されます。

    ```cpp
    struct S
    {
        S();
    };

    union
    {
        struct
        {
            S s;
        };
    } u; // C2280
    ```

   上のコードを実行すると、Visual Studio 2015 で次のエラーが生成されます。

    ```cpp
    error C2280: '<unnamed-type-u>::<unnamed-type-u>(void)': attempting to reference a deleted function
    note: compiler has generated '<unnamed-type-u>::<unnamed-type-u>' here
    ```

   この問題を解決するには、コンストラクターおよび/またはデストラクターの独自の定義を提供してください。

    ```cpp
    struct S
    {
        // Provide a default constructor by adding an empty function body.
        S() {}
    };

    union
    {
        struct
        {
            S s;
        };
    } u;
    ```

- **匿名構造体を持つ共用体**

   標準と準拠させるために、共用体の匿名構造体メンバーのランタイムの動作が変更されました。 共用体の匿名構造体のメンバーのコンストラクターは、そのような共用体の作成時に暗黙的に呼び出されなくなりました。 また、共用体の匿名構造体のメンバーのデストラクターも、共用体がスコープから外れたときに暗黙的に呼び出されなくなりました。 次のコードを検討します。共用体 U に匿名構造体が含まれています。この匿名構造体には、名前付きメンバー構造体 S が含まれており、その構造体にはデストラクターが含まれています。

    ```cpp
    #include <stdio.h>
    struct S
    {
        S() { printf("Creating S\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct {
            S s;
        };
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
        // Destructor implicitly called here.
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   Visual Studio 2013 では、S のコンストラクターは共用体の作成時に呼び出され、S のデストラクターは関数 f のスタックがクリーンアップされるときに呼び出されます。 しかし、Visual Studio 2015 では、コンストラクターとデストラクターは呼び出されません。 コンパイラによって、この動作の変更に関する警告が出されます。

    ```Output
    warning C4587: 'U::s': behavior change: constructor is no longer implicitly calledwarning C4588: 'U::s': behavior change: destructor is no longer implicitly called
    ```

   元の動作を復元するには、匿名構造体に名前を付けます。 非匿名構造体の実行時の動作は、コンパイラのバージョンに関係なく、同じです。

    ```cpp
    #include <stdio.h>

    struct S
    {
        S() { printf("Creating S.\n"); }
        ~S() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        } namedStruct;
        U() {}
        ~U() {}
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

   別の方法として、新しい関数にコンストラクターとデストラクターのコードを移動し、共用体のコンストラクターおよびデストラクターからこれらの関数の呼び出しを追加します。

    ```cpp
    #include <stdio.h>

    struct S
    {
        void Create() { printf("Creating S.\n"); }
        void Destroy() { printf("Destroying S\n"); }
    };
    union U
    {
        struct
        {
            S s;
        };
        U() { s.Create(); }
        ~U() { s.Destroy(); }
    };

    void f()
    {
        U u;
    }

    int main()
    {
        f();

        char s[1024];
        printf("Press any key.\n");
        gets_s(s);
        return 0;
    }
    ```

- **テンプレートの解決**

   テンプレートの名前解決に変更が加えられています。 C++ では、名前解決の候補を検討する場合、一致の可能性として検討されている 1 つ以上の名前により、無効なテンプレート インスタンス化が生成される可能性があります。 これらの無効なインスタンス化は通常、それ自体はコンパイラ エラーの原因にはなりません。これは SFINAE (Substitution Failure Is Not An Error: 置き換えの失敗はエラーではない) と呼ばれます。

   SFINAE のコンパイラがクラス テンプレートの特殊化のインスタンス化を必要とする場合は、この処理中に発生したエラーはコンパイラ エラーです。 以前のバージョンでは、コンパイラはこのようなエラーを無視していました。 次に例を示します。

    ```cpp
    #include <type_traits>

    template< typename T>
    struct S
    {
        S() = default;
        S(const S&);
        S(S& &);

        template< typename U, typename = typename std::enable_if< std::is_base_of< T, U> ::value> ::type>
        S(S< U> & &);
    };

    struct D;

    void f1()
    {
        S< D> s1;
        S< D> s2(s1);
    }

    struct B
    {
    };

    struct D : public B
    {
    };

    void f2()
    {
        S< D> s1;
        S< D> s2(s1);
    }
    ```

   現在のコンパイラでコンパイルすると、次のエラーが表示されます。

    ```Output
    type_traits(1110): error C2139: 'D': an undefined class is not allowed as an argument to compiler intrinsic type trait '__is_base_of'
    ..\t331.cpp(14): note: see declaration of 'D'
    ..\t331.cpp(10): note: see reference to class template instantiation 'std::is_base_of<T,U>' being compiled
    with
    [
        T=D,
        U=D
    ]
    ```

   これは、is_base_of の最初の呼び出しの時点でクラス `D` がまだ定義されていないためです。

   この場合の修正は、クラスが定義されるまでそのような型の特徴を使用しないことです。 `B` と `D` の定義をコード ファイルの先頭に移動すると、エラーが解決されます。 定義がヘッダー ファイルにある場合、ヘッダー ファイルの include ステートメントの順序を確認し、問題のあるテンプレートが使用される前にクラス定義がコンパイルされるようにしてください。

- **コピー コンストラクター**

   Visual Studio 2013 と Visual Studio 2015 の両方において、コンパイラは、クラスにユーザー定義の移動コンストラクターがあり、ユーザー定義のコピー コンストラクターはない場合に、そのクラスのコピー コンストラクターを生成します。 Dev14 では、この暗黙的に生成されたコピー コンストラクターは "= delete" とマークされています。

<!--From here to VS_Update1 added 04/21/2017-->

- **extern "C" として宣言される main に戻り値の型が必要になった**

   次のコードに対しては、C4430 が発生するようになりました。

    ```cpp
    extern "C" __cdecl main(){} // C4430
    ```

   このエラーを解決するには、戻り値の型を追加します。

    ```cpp
    extern "C" int __cdecl main(){} // OK
    ```

- **メンバーの初期化子では typename を使用できない**

   次のコードに対しては、C2059 が発生するようになりました。

    ```cpp
    template<typename T>
    struct S1 : public T::type
    {
        S1() : typename T::type() // C2059
        {
        }
    };

    struct S2 {
        typedef S2 type;
    };

    S1<S2> s;
    ```

   このエラーを解決するには、初期化子から `typename` を削除します。

    ```cpp
    S1() : T::type() // OK
    ...
    ```

- **明示的な特殊化でのストレージ クラスは無視される**

   次のコードに対しては、静的ストレージ クラスの指定子は無視されます。

    ```cpp
    template <typename T>
    void myfunc(T h)
    {
    }

    template<>
    static void myfunc(double h) // static is ignored
    {
    }
    ```

- **クラス テンプレート内部の static_assert で定数を使うと常にエラーになる**

   次のコードに対しては、`static_assert` は常にエラーになります。

    ```cpp
    template <size_t some_value>
    struct S1
    {
        static_assert(false, "default not valid"); // always invoked

    };

    //other partial specializations here
    ```

   この問題を回避するには、値を **struct** 内にラップします。

    ```cpp
    template <size_t some_value>
    struct constant_false {
        static const bool value = false;
    };

    template <size_t some_value>
    struct S1
    {
        static_assert(constant_false<some_value>::value, "default not valid");
    };

    //other partial specializations here
    ```

- **事前宣言に適用される規則。(C にのみ適用されます)。**

   次のコードに対しては、C2065 が発生するようになりました。

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT); // C2065: 'PTOKEN' : undeclared identifier
    ```

   この問題を修正するには、適切な事前宣言を追加します。

    ```cpp
    struct token_s;
    typedef int BOOL;
    typedef int INT;

    // forward declarations:
    typedef struct token_s TOKEN;
    typedef TOKEN *PTOKEN;

    typedef int(*PFNTERM)(PTOKEN, BOOL, INT);
    ```

- **関数ポインター型のより一貫した適用**

   次のコードに対しては、C2197 が発生するようになりました。

    ```cpp
    typedef int(*F1)(int);
    typedef int(*F2)(int, int);

    void func(F1 f, int v1, int v2)
    {
        f(v1, v2); // C2197
    }
    ```

- **オーバーロード関数のあいまいな呼び出し**

   次のコードに対しては、C266: "'N::bind': オーバーロード関数の呼び出しを解決することができません" が発生するようになりました。

    ```cpp
    template<typename R, typename T, typename T1, typename A1>
    void bind(R(T::*)(T1), A1&&);

    namespace N
    {
        template <typename T, typename R, typename ... Tx>
        void bind(R(T::*)(Tx...), T* ptr);
    }

    using namespace N;

    class Manager
    {
    public:
        void func(bool initializing);

        void mf()
        {
            bind(&Manager::func, this); //C2668
        }
    };
    ```

   このエラーを解決するには、`bind: N::bind(...)` への呼び出しを完全修飾します。 ただし、この変更が宣言されていない識別子によるマニフェストの場合は (C2065)、代わりに **using** 宣言で解決するのが適切な場合があります。

   このパターンは、ComPtr および `Microsoft::WRL` 名前空間内の他の型で頻繁に発生します。

- **不適切なアドレス指定の修正**

   次のコードに対しては、C2440: "'=': 'type *' から 'type' に変換できません" が発生するようになりました。 このエラーを解決するには、&(type) を (type) に、また (&f()) を (f()) に変更します。

    ```cpp
    // C
    typedef void (*type)(void);

    void f(int i, type p);
    void g(int);
    void h(void)
    {
        f(0, &(type)g);
    }

    // C++
    typedef void(*type)(void);

    type f();

    void g(type);

    void h()
    {
        g(&f());
    }
    ```

- **文字列リテラルは定数配列である**

   次のコードに対しては、"C2664: 'void f(void *)': 引数 1 を 'const char (* )[2]' から 'void *' へ変換できません" が発生します。

    ```cpp
    void f(void *);

    void h(void)
    {
        f(&__FUNCTION__);
        void *p = &"";
    }
    ```

   このエラーを解決するには、関数パラメーターの型を `const void*` に変更するか、または `h` の本体を次の例のように変更します。

    ```cpp
    void h(void)
    {
        char name[] = __FUNCTION__;
        f( name);
        void *p = &"";
    }
    ```

- **C++ 11 の UDL の文字列**

   次のコードに対しては、エラー C3688: "リテラル サフィックス 'L' が無効です。リテラル演算子またはリテラル演算子テンプレート 'operator ""L' が見つかりません" が発生するようになりました。

    ```cpp
    #define MACRO

    #define STRCAT(x, y) x\#\#y

    int main(){

        auto *val1 = L"string"MACRO;
        auto *val2 = L"hello "L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   このエラーを解決するには、スペースを追加するようにコードを変更します。

    ```cpp
    #define MACRO

    // Remove ##. Strings are automatically
    // concatenated so they aren't needed
    #define STRCAT(x, y) x y

    int main(){
        //Add space after closing quote
        auto *val1 = L"string" MACRO;
        auto *val2 = L"hello " L"world";

        std::cout << STRCAT(L"hi ", L"there");
    }
    ```

   上記の例で、`MACRO` は 2 つのトークン (文字列に続くマクロ) として解析されなくなります。 今度は、1 つのトークン UDL として解析されます。 同じことが L""L"" にも当てはまり、以前は L"" および L"" として解析されていたものが、L""L および "" として解析されるようになります。

   文字列連結の規則も標準への準拠に取り込まれました。つまり、L"a" "b" は L"ab" と同じです。 以前のエディションの Visual Studio では、文字幅の異なる文字列の連結は受け入れられませんでした。

- **C++11 の空の文字の削除**

   次のコードに対しては、エラー C2137: "空の文字定数" が発生するようになりました。

    ```cpp
    bool check(wchar_t c){
        return c == L''; //implicit null character
    }
    ```

   このエラーを解決するには、null を明示するようにコードを変更します。

    ```cpp
    bool check(wchar_t c){
        return c == L'\0';
    }
    ```

- **MFC の例外はコピーできないため値によってキャッチできない**

   MFC アプリケーションの次のコードに対しては、エラー C2316: "'D' がデストラクターとしてキャッチできない、またはコピー コンストラクターがアクセスできないか削除されています" が発生するようになりました。

    ```cpp
    struct B {
    public:
        B();
    private:
        B(const B &);
    };

    struct D : public B {
    };

    int main()
    {
        try
        {
        }
        catch (D) // C2316
        {
        }
    }
    ```

   コードを修正するには、catch ブロックを `catch (const D &)` に変更してもかまいませんが、一般にもっとよい解決策は、MFC TRY/CATCH マクロを使うことです。

- **alignof がキーワードになった**

   次のコードに対しては、エラー C2332: "'class': タグ名がありません" が発生するようになりました。 コードを修正するには、クラスの名前を変更するか、または、クラスが **alignof** と同じ処理を実行している場合は、単にクラスを新しいキーワードに置き換えます。

    ```cpp
    class alignof{}
    ```

- **constexpr がキーワードになった**

   次のコードに対しては、エラー C2059: "構文エラー: ')'" が発生するようになりました。 コードを修正するには、"constexpr" という名前の関数または変数の名前をすべて変更する必要があります。

    ```cpp
    int constexpr() {return 1;}
    ```

- **移動可能な型は const にできない**

   関数が移動することを意図した型を返す場合、その戻り値の型を **const** にすることはできません。

- **削除されたコピー コンストラクター**

   次のコードに対しては、C2280: "'S::S(S &&)': 削除された関数を参照しようとしています" が発生するようになりました。

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = S(2, 3); //C2280
    ```

   このエラーを修正するには、`S2` に対して直接の初期化を使います。

    ```cpp
    struct S{
        S(int, int);
        S(const S&) = delete;
        S(S&&) = delete;
    };

    S s2 = {2,3}; //OK
    ```

- **関数ポインターへの変換は、ラムダ キャプチャがない場合にのみ生成される**

   Visual Studio 2015 では、次のコードに対しては C2664 が発生します。

    ```cpp
    void func(int(*)(int)) {}

    int main() {

        func([=](int val) { return val; });
    }
    ```

   このエラーを解決するには、キャプチャ リストから `=` を削除します。

- **変換演算子を含むあいまいな呼び出し**

   次のコードに対しては、エラー C2440: "'type cast': 'S2' から 'S1' に変換できません" が発生するようになりました。

    ```cpp
    struct S1 {
        S1(int);
    };

    struct S2 {
        operator S1();
        operator int();
    };

    void f(S2 s2)
    {
        (S1)s2;
    }
    ```

   このエラーを解決するには、変換演算子を明示的に呼び出します。

    ```cpp
    void f(S2 s2)
    {
        //Explicitly call the conversion operator
        s2.operator S1();
        // Or
        S1((int)s2);
    }
    ```

   次のコードに対しては、エラー C2593: "'operator =' があいまいです" が発生するようになりました。

    ```cpp
    struct S1 {};

    struct S2 {
        operator S1&();
        operator S1() const;
    };

    void f(S1 *p, S2 s)
    {
        *p = s;
    }
    ```

   このエラーを解決するには、変換演算子を明示的に呼び出します。

    ```cpp
    void f(S1 *p, S2 s)
    {
        *p = s.operator S1&();
    }
    ```

- **非静的データ メンバーの初期化 (NSDMI) での無効なコピー初期化の修正**

   次のコードに対しては、エラー C2664: "'S1::S1(S1 &&)': 引数 1 を 'bool' から 'const S1 &' へ変換できません" が発生するようになりました。

    ```cpp
    struct S1 {
        explicit S1(bool);
    };

    struct S2 {
        S1 s2 = true; // error
    };
    ```

   このエラーを修正するには、直接の初期化を使います。

    ```cpp
    struct S2 {
    S1 s1{true}; // OK
    };
    ```

- **decltype ステートメント内のコンストラクターへのアクセス**

   次のコードに対しては、C2248: 'S::S': "クラス 'S' で宣言されているプライベート メンバーにアクセスできません" が発生するようになりました。

    ```cpp
    class S {
        S();
    public:
        int i;
    };

    class S2 {
        auto f() -> decltype(S().i);
    };
    ```

   このエラーを解決するには、`S2` に `S` のフレンド宣言を追加します。

    ```cpp
    class S {
        S();
        friend class S2; // Make S2 a friend
    public:
        int i;
    };
    ```

- **ラムダの既定のコンストラクターが暗黙的に削除される**

   次のコードに対しては、エラー C3497: "ラムダのインスタンスは作成できません" が発生するようになりました。

    ```cpp
    void func(){
        auto lambda = [](){};

        decltype(lambda) other;
    }
    ```

   このエラーを解決するには、既定のコンストラクターを呼び出す必要がないようにします。 ラムダが何もキャプチャしない場合は、関数ポインターにキャストできます。

- **削除された代入演算子でのラムダ**

   次のコードに対しては、エラー C2280 が発生するようになりました。

    ```cpp
    #include <memory>
    #include <type_traits>

    template <typename T, typename D>
    std::unique_ptr<T, typename std::remove_reference<D &&>::type> wrap_unique(T *p, D &&d);

    void f(int i)
    {
        auto encodedMsg = wrap_unique<unsigned char>(nullptr, [i](unsigned char *p) {
        });
        encodedMsg = std::move(encodedMsg);
    }
    ```

   このエラーを解決するには、ラムダをファンクター クラスに置き換えるか、代入演算子を使う必要がないようにします。

- **削除されたコピー コンストラクターでのオブジェクト移動の試み**

   次のコードに対しては、エラー C2280: "'moveable::moveable(const moveable &)': 削除された関数を参照しようとしています" が発生するようになりました。

    ```cpp
    struct moveable {

        moveable() = default;
        moveable(moveable&&) = default;
        moveable(const moveable&) = delete;
    };

    struct S {
        S(moveable && m) :
            m_m(m)//copy constructor deleted
        {}
        moveable m_m;
    };
    ```

   エラーを解決するには、代わりに `std::move` を使用します。

    ```cpp
    S(moveable && m) :
        m_m(std::move(m))
    ```

- **ローカル クラスは、同じ関数で後に定義されている他のローカル クラスを参照できない**

   次のコードに対しては、エラー C2079: "'s' が未定義の struct 'main::S2' で使用しています" が発生するようになりました。

    ```cpp
    int main()
    {
        struct S2;
        struct S1 {
            void f() {
                S2 s;
            }
        };
        struct S2 {};
    }
    ```

   このエラーを解決するには、`S2` の定義を上に移動します。

    ```cpp
    int main()
    {
        struct S2 { //moved up
        };

    struct S1 {
        void f() {
            S2 s;
            }
        };
    }
    ```

- **派生コンストラクターの本体内の保護された既定コンストラクターは呼び出すことができない**

   次のコードに対しては、エラー C2248: "'S1::S1': クラス 'S1' で宣言されている保護されているメンバーにアクセスできません" が発生するようになりました。

    ```cpp
    struct S1 {
    protected:
        S1();
    };

    struct S2 : public S1 {
        S2() {
            S1();
        }
    };
    ```

   このエラーを解決するには、`S2` でコンストラクターから `S1()` の呼び出しを削除し、必要がある場合は別の関数に配置します。

- **{} がポインターへの変換を妨げる**

   次のコードに対しては、C2439: "'S::p': 指定されたメンバーは初期化できません" が発生するようになりました。

    ```cpp
    struct S {
        S() : p({ 0 }) {}
        void *p;
    };
    ```

   このエラーを解決するには、`0` を囲む中かっこを削除するか、または次の例で示すように代わりに **nullptr** を使います。

    ```cpp
    struct S {
        S() : p(nullptr) {}
        void *p;
    };
    ```

- **正しくないマクロ定義とかっこ付きの使用法**

   次の例に対しては、エラー C2008: "';': マクロ定義内で指定された文字の使い方が間違っています" が発生するようになりました。

    ```cpp
    #define A; //cause of error

    struct S {
        A(); // error
    };
    ```

   この問題を解決するには、先頭の行を `#define A();` に変更します。

   次のコードに対しては、エラー C2059: "構文エラー: ')'" が発生します。

    ```cpp
    //notice the space after 'A'
    #define A () ;

    struct S {
        A();
    };
    ```

   このコードを修正するには、A と () の間のスペースを削除します。

   次のコードに対しては、エラー C2091: "関数は関数を返せません" が発生します。

    ```cpp
    #define DECLARE void f()

    struct S {
        DECLARE();
    };
    ```

   このエラーを解決するには、S の DECLARE の後のかっこを削除して、`DECLARE;` にします。

   次のコードに対しては、エラー C2062: "型 'int' は予期されていません" が発生します。

    ```cpp
    #define A (int)

    struct S {
        A a;
    };
    ```

   この問題を解決するには、`A` を次のように定義します。

    ```cpp
    #define A int
    ```

- **宣言内の余分なかっこ**

   次のコードに対しては、エラー C2062: "型 'int' は予期されていません" が発生します。

    ```cpp
    struct S {
        int i;
        (int)j;
    };
    ```

   このエラーを解決するには、`j` を囲むかっこを削除します。 明確にするためにかっこが必要な場合は、**typedef** を使います。

- **コンパイラで生成されるコンストラクターと __declspec(novtable)**

   Visual Studio 2015 では、仮想基底クラスを使う抽象クラスのコンパイラによって生成されるインライン コンストラクターで、`__declspec(novtable)` と組み合わせて使うと `__declspec(dllimport)` の不適切な使用が公開される可能性が高くなっています。

- **auto では初期化子リストの直接適用に含まれる式が 1 つでなければならない**

   次のコードに対しては、エラー C3518: "'testPositions': 初期化子リストを直接適用するコンテキストでは、'auto' の型は、単一の初期化子式からのみ推測できます" が発生するようになりました。

    ```cpp
    auto testPositions{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

   このエラーを解決する 1 つの可能性は、`testPositions` を次のように初期化することです。

    ```cpp
    std::tuple<int, int> testPositions[]{
        std::tuple<int, int>{13, 33},
        std::tuple<int, int>{-23, -48},
        std::tuple<int, int>{38, -12},
        std::tuple<int, int>{-21, 17}
    };
    ```

- **is_convertible に対する型のチェックと型へのポインター**

   次のコードでは、静的アサーションが失敗するようになりました。

    ```cpp
    struct B1 {
    private:
        B1(const B1 &);
    };
    struct B2 : public B1 {};
    struct D : public B2 {};

    static_assert(std::is_convertible<D, B2>::value, "fail");
    ```

   このエラーを解決するには、`static_assert` および `D` へのポインターを比較するように `B2` を変更します。

    ```cpp
    static_assert(std::is_convertible<D*, B2*>::value, "fail");
    ```

- **__declspec(novtable) 宣言が一貫している必要がある**

   `__declspec` 宣言は、すべてのライブラリで一貫している必要があります。 次のコードに対しては、単一定義規則 (ODR) 違反が発生するようになりました。

    ```cpp
    //a.cpp
    class __declspec(dllexport)
        A {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };

    A::A() {}
    A::~A() {}
    A::A(const A&) {}

    //b.cpp
    // compile with cl.exe /nologo /LD /EHsc /Osx b.cpp
    #pragma comment(lib, "A")
    class __declspec(dllimport) A
    {
    public: A();
            A(const A&);
            virtual ~A();
    private:
        int i;
    };

    struct __declspec(novtable) __declspec(dllexport) B
        : virtual public A {
        virtual void f() = 0;
    };

    //c.cpp
    #pragma comment(lib, "A")
    #pragma comment(lib, "B")
    class __declspec(dllimport) A
    {
    public:
        A();
        A(const A&);
        virtual ~A();
    private:
        int i;
    };
    struct  /* __declspec(novtable) */ __declspec(dllimport) B // Error. B needs to be novtable here also.
        : virtual public A
    {
        virtual void f() = 0;
    };

    struct C : virtual B
    {
        virtual void f();
    };

    void C::f() {}
    C c;
    ```

###  <a name="VS_Update1"></a>更新プログラム 1 の準拠の強化

- **プライベートの仮想基底クラスと間接継承**

   以前のバージョンのコンパイラでは、派生クラスは間接的に派生した`private virtual`基底クラスのメンバー関数を呼び出すことができました。 この従来の動作は正しい動作ではなく、C++ 標準に準拠していません。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。その結果、コンパイラ エラー C2280 を発行します。

    ```Output
    error C2280: 'void *S3::__delDtor(unsigned int)': attempting to reference a deleted function
    ```

   例 (変更前)

    ```cpp
    class base
    {
    protected:
        base();
        ~base();
    };

    class middle : private virtual base {}; class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;  //
    }
    ```

   例 (変更後)

    ```cpp
    class base;  // as above

    class middle : protected virtual base {};
    class top : public virtual middle {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

   \- - または -

    ```cpp
    class base;  // as above

    class middle : private virtual base {};
    class top : public virtual middle, private virtual bottom {};

    void destroy(top *p)
    {
        delete p;
    }
    ```

- **オーバーロードされた operator new と operator delete**

   以前のバージョンのコンパイラでは、メンバー以外の **operator new** とメンバー以外の **operator delete** を static として宣言することや、グローバル名前空間以外の名前空間で宣言することが許可されていました。  この従来の動作のせいで、プログラマが意図した **new** または **delete** 演算子の実装がプログラムによって呼び出されないという危険性が生じ、結果として、問題のあるランタイム動作が警告なしに生じていました。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。代わりにコンパイラ エラー C2323 を発行します。

    ```Output
    error C2323: 'operator new': non-member operator new or delete functions may not be declared static or in a namespace other than the global namespace.
    ```

   例 (変更前)

    ```cpp
    static inline void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // error C2323
    ```

   例 (変更後)

    ```cpp
    void * __cdecl operator new(size_t cb, const std::nothrow_t&)  // removed 'static inline'
    ```

   また、コンパイラは特定の診断を行いませんが、インラインの operator **new** の形式は不適切であると見なされます。

- **非クラス型で 'operator *type*()' (ユーザー定義の変換) を呼び出す**

   以前のバージョンのコンパイラでは 'operator *type*()' を非クラス型で呼び出すことが許可されていましたが、それは何の警告もなく無視されていました。 この従来の動作のせいで、問題のあるコードが警告なしに生成される危険性が生じ、結果として、予期しないランタイム動作の原因となっていました。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。代わりにコンパイラ エラー C2228 を発行します。

    ```Output
    error C2228: left of '.operator type' must have class/struct/union
    ```

   例 (変更前)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column.operator index_t());  // error C2228
    }
    ```

   例 (変更後)

    ```cpp
    typedef int index_t;
    void bounds_check(index_t index);
    void login(int column)
    {
        bounds_check(column);  // removed cast to 'index_t', 'index_t' is an alias of 'int'
    }
    ```

- **詳細な型指定子の冗長な typename**

   以前のバージョンのコンパイラでは、詳細な型指定子内で **typename** を指定できましたが、この方法で記述されたコードは意味的に正しくありません。 コンパイラはこの方法で記述されたコードを受け入れなくなりました。代わりにコンパイラ エラー C3406 を発行します。

    ```Output
    error C3406: 'typename' cannot be used in an elaborated type specifier
    ```

   例 (変更前)

    ```cpp
    template <typename class T>
    class container;
    ```

   例 (変更後)

    ```cpp
    template <class T>  // alternatively, could be 'template <typename T>'; 'typename' is not elaborating a type specifier in this case
    class container;
    ```

- **初期化子リストからの配列の型推論**

   以前のバージョンのコンパイラでは、初期化子リストからの配列の型推論はサポートされていませんでした。 コンパイラでこの形式の型推論がサポートされるようになりました。その結果、初期化子リストを使用した関数テンプレートへの呼び出しがあいまいになったり、以前のバージョンのコンパイラとは異なるオーバーロードが選ばれたりする可能性があります。 これらの問題を解決するには、プログラマの意図したオーバーロードをプログラムが明示的に指定する必要があります。

   この新しい動作により、オーバーロードの解決で過去の候補と同程度に優れた追加候補が検討されると、呼び出しはあいまいになり、結果としてコンパイラはコンパイラ エラー C2668 を発行します。

    ```Output
    error C2668: 'function' : ambiguous call to overloaded function.
    ```

   例 1: オーバーロード関数のあいまいな呼び出し (変更前)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(int, Args...)
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // The compiler now considers this call ambiguous, and issues a compiler error
         f({ 3 });   error C2668 : 'f' ambiguous call to overloaded function
    }
    ```

   例 1: オーバーロード関数のあいまいな呼び出し (変更後)

    ```cpp
    template < typename... Args>
    void f(int, Args...);  //

    template < int N, typename... Args>
    void f(const int(&)[N], Args...);

    int main()
    {
        // To call f(int, Args...) when there is just one expression in the initializer list, remove the braces from it.
        f(3);
    }
    ```

   この新しい動作により、オーバーロードの解決で過去の候補よりも適合度の高い追加候補が検討されると、呼び出しはあいまいにならずに新しい候補に解決され、プログラムの動作は変化します。これはプログラマの意図した動作とは異なる場合があります。

   例 2: オーバーロードの解決の変更 (変更前)

    ```cpp
    // In previous versions of the compiler, code written in this way would unambiguously call f(S, Args...)
    struct S
    {
        int i;
        int j;
    };

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // The compiler now resolves this call to f(const int (&)[N], Args...) instead
         f({ 1, 2 });
    }
    ```

   例 2: オーバーロードの解決の変更 (変更後)

    ```cpp
    struct S;  // as before

    template < typename... Args>
    void f(S, Args...);

    template < int N, typename... Args>
    void f(const int *&)[N], Args...);

    int main()
    {
        // To call f(S, Args...), perform an explicit cast to S on the initializer list.
        f(S{ 1, 2 });
    }
    ```

- **switch ステートメントの警告の復元**

   前のバージョンのコンパイラで、**switch** ステートメント関連のいくつかの警告が削除されました。今ではこれらの警告は復元されています。 コンパイラは復元された警告を発行するようになり、特定の case (既定の case を含む) に関連する警告が、switch ステートメントの最後の行ではなく、問題のある case を含む行で発行されるようになりました。 この結果、以前とは異なる行でそれらの警告が発行されるようになり、以前は `#pragma warning(disable:####)` を使用して抑制できていた警告も、意図どおりに抑制できなくなる可能性があります。 意図どおりにこれらの警告を抑制するには、問題がある最初の case の上の行まで `#pragma warning(disable:####)` ディレクティブを移動しなければならない場合があります。 復元された警告を次に示します。

    ```Output
    warning C4060: switch statement contains no 'case' or 'default' labels
    ```

    ```Output
    warning C4061: enumerator 'bit1' in switch of enum 'flags' is not explicitly handled by a case label
    ```

    ```Output
    warning C4062: enumerator 'bit1' in switch of enum 'flags' is not handled
    ```

    ```Output
    warning C4063: case 'bit32' is not a valid value for switch of enum 'flags'
    ```

    ```Output
    warning C4064: switch of incomplete enum 'flags'
    ```

    ```Output
    warning C4065: switch statement contains 'default' but no 'case' labels
    ```

    ```Output
    warning C4808: case 'value' is not a valid value for switch condition of type 'bool'
    ```

    ```Output
    Warning C4809: switch statement has redundant 'default' label; all possible 'case' labels are given
    ```

   C4063 の例 (変更前)

    ```cpp
    class settings
    {
    public:
        enum flags
        {
            bit0 = 0x1,
            bit1 = 0x2,
            ...
        };
        ...
    };

    int main()
    {
        auto val = settings::bit1;

        switch (val)
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

             case settings::bit0 | settings::bit1:  // warning C4063
                break;
        }
    };
    ```

   C4063 の例 (変更後)

    ```cpp
    class settings { ... };  // as above
    int main()
    {
        // since C++11, use std::underlying_type to determine the underlying type of an enum
        typedef std::underlying_type< settings::flags> ::type flags_t;

            auto val = settings::bit1;

        switch (static_cast< flags_t> (val))
        {
        case settings::bit0:
            break;

        case settings::bit1:
            break;

        case settings::bit0 | settings::bit1:  // ok
            break;
        }
    };
    ```

   その他の復元の警告の例については、それらのドキュメントをご覧ください。

- **#include: パス名に親ディレクトリの指定子 '.. ' を使用します**(`/Wall` `/WX`のみに影響します)

   以前のバージョンのコンパイラでは、親ディレクトリの指定子の使用が検出されませんでした '… ' パス名で `#include` ディレクティブです。 この方法で記述されたコードは通常、プロジェクトの相対パスが正しく使用されていないためにプロジェクトの外部に存在するヘッダーをインクルードすることを目的としています。 この従来の動作のせいで、プログラマが意図したものとは異なるソース ファイルをインクルードしてプログラムがコンパイルされる危険性や、これらの相対パスを他のビルド環境に移植できない危険性が生じました。 コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合にはオプションのコンパイラ警告 C4464 を発行するようになりました。

    ```Output
    warning C4464: relative include path contains '..'
    ```

   例 (変更前)

    ```cpp
    #include "..\headers\C4426.h"  // emits warning C4464
    ```

   例 (変更後)

    ```cpp
    #include "C4426.h"  // add absolute path to 'headers\' to your project's include directories
    ```

   さらに、コンパイラは特定の診断を示しませんが、プロジェクトのインクルード ディレクトリを指定する場合、親ディレクトリの指定子 ".." を使用することもお勧めします。

- **#pragma optimize () は、ヘッダーファイルの終わりを**超えています (`/Wall` `/WX`にのみ影響します)

   以前のバージョンのコンパイラでは、翻訳単位内に含まれるヘッダー ファイルをエスケープする最適化フラグの設定の変更は検出されませんでした。 コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合には、問題のある `#include`の位置でオプションのコンパイラ警告 C4426 を発行するようになりました。 この警告が発行されるのは、この変更が、コンパイラに対するコマンドライン引数によって設定された最適化フラグと競合する場合のみです。

    ```Output
    warning C4426: optimization flags changed after including header, may be due to #pragma optimize()
    ```

   例 (変更前)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
    ...
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"  // warning C4426
    ```

   例 (変更後)

    ```cpp
    // C4426.h
    #pragma optimize("g", off)
                ...
    #pragma optimize("", on)  // restores optimization flags set via command-line arguments
    // C4426.h ends

    // C4426.cpp
    #include "C4426.h"
    ```

- **#Pragma 警告 (プッシュ)** と **#pragma 警告 (Pop)** が一致しません (`/Wall` `/WX`にのみ影響します)

   以前のバージョンのコンパイラでは、`#pragma warning(push)` の状態の変更が、異なるソース ファイルの `#pragma warning(pop)` 状態の変更とペアになっていても (故意であることはまれですが)、それを検出しませんでした。 この従来の動作のせいで、プログラマの意図と異なる一連の警告が有効な状態でプログラムがコンパイルされる危険性が生じ、結果として、問題のあるランタイム動作が警告なしに発生する原因となっていました。 コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合には、一致する `#pragma warning(pop)` の位置でオプションのコンパイラの警告 C5031 を発行するようになりました。 この警告には、対応する #pragma warning(push) の場所を参照するメモが含まれます。

    ```Output
    warning C5031: #pragma warning(pop): likely mismatch, popping warning state pushed in different file
    ```

   例 (変更前)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    ...
    #pragma warning(pop)  // pops a warning state not pushed in this source file
    ...
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // leaves #pragma warning(push) 'dangling'
    ...
    #include "C5031_part2.h" // matches 'dangling' #pragma warning(push), resulting in warning C5031
    ...
    ```

   例 (変更後)

    ```cpp
    // C5031_part1.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)  // pops the warning state pushed in this source file
    // C5031_part1.h ends without #pragma warning(pop)

    // C5031_part2.h
    #pragma warning(push)  // pushes the warning state pushed in this source file
    #pragma warning(disable:####)
    ...
    #pragma warning(pop)
    // C5031_part1.h ends

    // C5031.cpp
    #include "C5031_part1.h" // #pragma warning state changes are self-contained and independent of other source files or their #include order.
    ...
    #include "C5031_part2.h"
    ...
    ```

   一般的ではありませんが、意図的にこの方法でコードを記述する場合があります。 この方法で記述されたコードは `#include` の順序の変更の影響を受けます。可能な場合は、自己完結型の方法を使用してソース コード ファイルで警告状態を管理することをお勧めします。

- **一致しない #pragma 警告 (プッシュ)** (`/Wall` `/WX`にのみ影響)

   以前のバージョンのコンパイラでは、翻訳単位の末尾で一致していない `#pragma warning(push)` の状態の変更は検出されませんでした。 コンパイラは、この方法で書かれたコードを検出してプログラマに通知し、有効な場合には、一致していない `#pragma warning(push)` の位置でオプションのコンパイラ警告 C5032 を発行するようになりました。 この警告が発行されるのは、翻訳単位にコンパイル エラーがない場合のみです。

    ```Output
    warning C5032: detected #pragma warning(push) with no corresponding #pragma warning(pop)
    ```

   例 (変更前)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    // C5032.h ends without #pragma warning(pop)

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without #pragma warning(pop), resulting in warning C5032 on line 1 of C5032.h
    ```

   例 (変更後)

    ```cpp
    // C5032.h
    #pragma warning(push)
    #pragma warning(disable:####)
    ...
    #pragma warning(pop) // matches #pragma warning (push) on line 1
    // C5032.h ends

    // C5032.cpp
    #include "C5032.h"
    ...
    // C5032.cpp ends -- the translation unit is completed without unmatched #pragma warning(push)
    ```

- **#pragma 警告状態の追跡が強化された結果、追加の警告が発行される場合があります。**

   以前のバージョンのコンパイラでは、#pragma 警告状態の変化の追跡が不十分なため、すべての意図された警告を発行できませんでした。 この動作により、プログラマの意図したものとは異なる状況で、事実上、特定の警告が抑制される危険性がありました。 コンパイラにより `#pragma warning` 状態がより確実に追跡されるようになりました (特にテンプレート内部での `#pragma warning` 状態の変化に関連するもの)。また `#pragma warning(push)` と `#pragma warning(pop)` の意図しない使用をプログラマが特定する助けになるように、新しい警告 C5031 と C5032 を必要に応じて発行されるようになりました。

   `#pragma warning` 状態の変更の追跡が強化された結果、以前は誤って抑制されていた警告、または以前は誤って診断されていた問題に関連する警告が発行されるようになる場合があります。

- **制御が渡らないコードの識別の強化**

   C++ 標準ライブラリが変更されたり、以前のバージョンのコンパイラよりも関数呼び出しのインライン化機能が強化されたりしたため、コンパイラは特定のコードに制御が渡らないことを示せるようになりました。 この新しい動作の結果、警告 C4720 のインスタンスが新しく、あるいはより頻繁に発行される可能性があります。

    ```Output
    warning C4720: unreachable code
    ```

   多くの場合、この警告が発行されるのは、最適化を有効にしてコンパイルするときだけです。最適化により、より多くの関数呼び出しがインライン化されたり、冗長なコードが削除されたり、コードに制御が渡っていないことを他の方法で判別できるようになったりするためです。 警告 C4720 の新しいインスタンスが **try/catch** ブロックで頻繁に発生 (特に [std::find](assetId:///std::find?qualifyHint=False&autoUpgrade=True) の使用に関連して) していることが確認されています。

   例 (変更前)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // ok
    }
    ```

   例 (変更後)

    ```cpp
    try
    {
        auto iter = std::find(v.begin(), v.end(), 5);
    }
    catch (...)
    {
        do_something();   // warning C4702: unreachable code
    }
    ```

###  <a name="VS_Update2"></a> 更新プログラム 2 の準拠の強化

- **SFINAE 式の部分的なサポートの結果として、追加の警告とエラーが発行される場合がある**

   以前のバージョンのコンパイラは、SFINAE 式のサポートがなかったため、**decltype** 指定子内の特定の種類の式を解析しませんでした。 この従来の動作は正しい動作ではなく、C++ 標準に準拠していません。 コンパイラは、継続的な適合性の向上により、これらの式を解析し、SFINAE 式を部分的にサポートするようになりました。 その結果、コンパイラは、以前のバージョンのコンパイラが解析しなかった式で検出された警告とエラーを発行します。

   この新しい動作が、まだ宣言されていない型を含む **decltype** 式を解析するとき、コンパイラは結果としてコンパイラ エラー C2039 を発行します。

    ```Output
    error C2039: 'type': is not a member of '`global namespace''
    ```

   例 1: 宣言されていない型の使用 (変更前)

    ```cpp
    struct s1
    {
        template < typename T>
        auto f() - > decltype(s2< T> ::type::f());  // error C2039

        template< typename>
        struct s2 {};
    }
    ```

   例 1 (変更後)

    ```cpp
    struct s1
    {
        template < typename>  // forward declare s2struct s2;

            template < typename T>
        auto f() - > decltype(s2< T> ::type::f());

        template< typename>
        struct s2 {};
    }
    ```

   依存名が型であることを指定するために必要な **typename** キーワードが欠落している **decltype** 式がこの新しい動作によって解析されると、コンパイラは、コンパイラ エラー C2923 と共にコンパイラの警告 C4346 を発行します。

    ```Output
    warning C4346: 'S2<T>::Type': dependent name is not a type
    ```

    ```Output
    error C2923: 's1': 'S2<T>::Type' is not a valid template type argument for parameter 'T'
    ```

   例 2: 依存名が型ではない (変更前)

    ```cpp
    template < typename T>
    struct s1
    {
        typedef T type;
    };

    template < typename T>
    struct s2
    {
        typedef T type;
    };

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< S2< T> ::type> ::type> ()));  // warning C4346, error C2923
    };
    ```

   例 2 (変更後)

    ```cpp
    template < typename T> struct s1 { ... };  // as above
    template < typename T> struct s2 { ... };  // as above

    template < typename T>
    T declval();

    struct s
    {
        template < typename T>
        auto f(T t) - > decltype(t(declval< S1< typename S2< T> ::type> ::type> ()));
    };
    ```

- `volatile`**メンバー変数は、暗黙的に定義されたコンストラクターと代入演算子を禁止し**ます

   以前のバージョンのコンパイラは、**volatile** メンバー変数を持つクラスが、自動的に生成された既定のコピー/移動コンストラクターと既定のコピー/移動代入演算子を持つことを許可していました。 この従来の動作は正しい動作ではなく、C++ 標準に準拠していません。 コンパイラは、**volatile** メンバー変数を持つクラスが、非単純コンストラクションと代入演算子を持つと見なすようになりました。それにより、これらの演算子の既定の実装が自動的に生成されることを防止します。 そのようなクラスが共用体 (またはクラス内の匿名共用体) のメンバーである場合は、共用体のコピー/移動コンストラクターとコピー/移動代入演算子 (または匿名共用体を含むクラス) は、暗黙的に削除済みとして定義されます。 明示的に定義することなく、共用体 (または無名共用体を含むクラス) を構築またはコピーしようとするとエラーとなり、結果として、コンパイラはコンパイラ エラー C2280 を発行します。

    ```Output
    error C2280: 'B::B(const B &)': attempting to reference a deleted function
    ```

   例 (変更前)

    ```cpp
    struct A
    {
        volatile int i;
        volatile int j;
    };

    extern A* pa;

    struct B
    {
        union
        {
            A a;
            int i;
        };
    };

    B b1{ *pa };
    B b2(b1);  // error C2280
    ```

   例 (変更後)

    ```cpp
    struct A
    {
        int i; int j;
    };

    extern volatile A* pa;

    A getA()  // returns an A instance copied from contents of pa
    {
        A a;
        a.i = pa - > i;
        a.j = pa - > j;
        return a;
    }

    struct B;  // as above

    B b1{ GetA() };
    B b2(b1);  // error C2280
    ```

- **静的メンバー関数は、CV 修飾子をサポートしていません。**

   以前のバージョンの Visual Studio 2015 は、静的メンバー関数が CV 修飾子を持つことを許可していました。 この動作は、Visual Studio 2015 および Visual Studio 2015 Update 1 での回帰が原因です。Visual Studio 2013 および以前のバージョンのコンパイラは、この方法で記述されたコードを拒否します。 Visual Studio 2015 および Visual Studio 2015 Update 1 の動作は正しいものではなく、C++ 標準に準拠していません。  Visual Studio 2015 Update 2 は、この方法で記述されたコードを拒否し、コンパイラ エラー C2511 を代わりに発行します。

    ```Output
    error C2511: 'void A::func(void) const': overloaded member function not found in 'A'
    ```

   例 (変更前)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() const {}  // C2511
    ```

   例 (変更後)

    ```cpp
    struct A
    {
        static void func();
    };

    void A::func() {}  // removed const
    ```

- **列挙型の事前宣言は、WinRT コードでは許可されていません** (`/ZW` にのみ影響)

   マネージド C++ コードが  **コンパイラ スイッチを使用して .Net Framework 用にコンパイルされる場合と同様に、Windows ランタイム (WinRT) 用にコンパイルされたコードは、** enum`/clr` 型が事前に宣言されることを許可しません。 この動作により、確実に列挙型のサイズがわかり、WinRT 型システムに正しくプロジェクションを実行することができます。 コンパイラは、この方法で記述されたコードを拒否し、コンパイラ エラー C3197 と共にコンパイラ エラー C2599 を発行します。

    ```Output
    error C2599: 'CustomEnum': the forward declaration of a WinRT enum is not allowed
    ```

    ```Output
    error C3197: 'public': can only be used in definitions
    ```

   例 (変更前)

    ```cpp
    namespace A {
        public enum class CustomEnum : int32;  // forward declaration; error C2599, error C3197
    }

    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

   例 (変更後)

    ```cpp
              // forward declaration of CustomEnum removed
    namespace A {
        public enum class CustomEnum : int32
        {
            Value1
        };
    }

    public ref class Component sealed
    {
    public:
        CustomEnum f()
        {
            return CustomEnum::Value1;
        }
    };
    ```

- **オーバーロードされた非メンバー operator new と operator delete をインラインで宣言できない** (レベル 1 (`/W1`) 既定で有効)

   以前のバージョンのコンパイラは、非メンバー operator new と operator delete 関数がインラインで宣言されるときに警告を発行しません。 この方法で記述されたコードは、形式が正しくなく (診断は必要なし)、new 演算子と delete 演算子の不一致 (特に、サイズ割り当て解除と共に使用された場合) から生じるメモリの問題を引き起こす可能性があります。この問題を診断するのは難しい場合があります。 コンパイラは警告 C4595 を発行するようになったので、この方法で記述されたコードを識別しやすくなりました。

    ```Output
    warning C4595: 'operator new': non-member operator new or delete functions may not be declared inline
    ```

   例 (変更前)

    ```cpp
    inline void* operator new(size_t sz)  // warning C4595
    {
        ...
    }
    ```

   例 (変更後)

    ```cpp
    void* operator new(size_t sz)  // removed inline
    {
        ...
    }
    ```

   この方法で記述されたコードを修正するには、演算子の定義をヘッダー ファイルから対応するソース ファイルに移動することが必要な場合があります。

###  <a name="VS_Update3"></a> 更新プログラム 3 の準拠の強化

- **std::is_convertable は self-assignment** (標準ライブラリ) を検出するようになりました

   以前のバージョンの `std::is_convertable` type-trait は、コピー コンストラクターが削除済みまたはプライベートの場合、クラス型の自己代入を正しく検出していませんでした。 コピー コンストラクターが削除済みまたはプライベートの場合でも、クラス型の自己代入時にも `std::is_convertable<>::value` が正しく **false** に設定されるようになりました。

   この変更に関連するコンパイラの診断はありません。

   例

    ```cpp
    #include <type_traits>

    class X1
    {
                public:
                X1(const X1&) = delete;
                };

    class X2
    {
                private:
                X2(const X2&);
                };

    static_assert(std::is_convertible<X1&, X1>::value, "BOOM");static_assert(std::is_convertible<X2&, X2>::value, "BOOM");
    ```

   以前のバージョンのコンパイラでは、`std::is_convertable<>::value` が不適切に **true** に設定されているため、この例の一番下にある静的なアサーションは成功します。 新しいバージョンでは、`std::is_convertable<>::value` は正しく **false** に設定され、静的なアサーションが失敗するようになりました。

- **既定値にされた、または削除された単純なコピー コンストラクターと移動コンストラクターのアクセス指定子の尊重**

   以前のバージョンのコンパイラは、既定値にされた、または削除された単純なコピー コンストラクターと移動コンストラクターを呼び出し前に確認していませんでした。 この従来の動作は正しい動作ではなく、C++ 標準に準拠していません。 場合によっては、この従来の動作のせいで、問題のあるコードが警告なしに生成される危険性が生じ、結果として、予期しないランタイム動作の原因となっていました。 コンパイラは、既定値に指定された、または削除された単純なコピー コンストラクターと移動コンストラクターをチェックし、呼び出し可能かどうかを判断し、呼び出し不能と判断した場合に、コンパイラの警告 C2248 を結果として返します。

    ```Output
    error C2248: 'S::S' cannot access private member declared in class 'S'
    ```

   例 (変更前)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(S);  // pass S by value

    int main()
    {
        S s;
        f(s);  // error C2248, can't invoke private copy constructor
    }
    ```

   例 (変更後)

    ```cpp
    class S {
    public:
        S() = default;
    private:
        S(const S&) = default;
    };

    void f(const S&);  // pass S by reference

    int main()
    {
        S s;
        f(s);
    }
    ```

- **属性が指定された ATL コードのサポートの非推奨化** (デフォルトでレベル 1 (`/W1`))

   以前のバージョンのコンパイラは、属性が指定された ATL コードをサポートしていました。 [Visual Studio 2008 から始まった](../porting/visual-cpp-what-s-new-2003-through-2015.md#whats-new-for-c-in-visual-studio-2008)、属性が指定された ATL コードのサポートを停止する次のフェーズとして、属性が指定された ATL コードは非推奨になりました。 コンパイラは、非推奨になったこの種類のコードを特定するために、コンパイラの警告 C4467 を発行するようになりました。

    ```Output
    warning C4467: Usage of ATL attributes is deprecated
    ```

   コンパイラからサポートが削除されるまで、属性が指定された ATL コードを今後も使い続ける場合は、`/Wv:18` または `/wd:4467` コマンド ライン引数をコンパイラに渡すことで、またはソース コードに `#pragma warning(disable:4467)` を追加することで、この警告を無効にすることができます。

   例 1 (変更前)

    ```cpp
              [uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")]
    class A {};
    ```

   例 1 (変更後)

    ```cpp
    __declspec(uuid("594382D9-44B0-461A-8DE3-E06A3E73C5EB")) A {};
    ```

   非推奨になった ATL 属性の使用を防ぐために、次のコード例のように、IDL ファイルを作成する場合があります

   例 2 (変更後)

    ```cpp
    [emitidl];
    [module(name = "Foo")];

    [object, local, uuid("9e66a290-4365-11d2-a997-00c04fa37ddb")]
    __interface ICustom {
        HRESULT Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [coclass, appobject, uuid("9e66a294-4365-11d2-a997-00c04fa37ddb")]
    class CFoo : public ICustom
    {
        // ...
    };
    ```

   まず、*.idl ファイルを作成します。vc140.idl で生成されるファイルを使用して、インターフェイスと注釈を含む \*.idl ファイルを取得することができます。

   次に、MIDL 手順をビルドに追加し、C++ インターフェイス定義が生成されるようにします。

   例 2 IDL (変更後)

    ```cpp
    import "docobj.idl";

    [
        object, local, uuid(9e66a290 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    interface ICustom : IUnknown {
        HRESULT  Custom([in] long l, [out, retval] long *pLong);
        [local] HRESULT  CustomLocal([in] long l, [out, retval] long *pLong);
    };

    [version(1.0), uuid(29079a2c - 5f3f - 3325 - 99a1 - 3ec9c40988bb)]
    library Foo
    {
        importlib("stdole2.tlb");
    importlib("olepro32.dll");
    [
        version(1.0),
        appobject,uuid(9e66a294 - 4365 - 11d2 - a997 - 00c04fa37ddb)
    ]

    coclass CFoo {
        interface ICustom;
    };
    }
    ```

   次に、以下のコード例のように、実装ファイルで ATL を直接使用します。

   例 2 実装 (変更後)

    ```cpp
    #include <idl.header.h>
    #include <atlbase.h>

    class ATL_NO_VTABLE CFooImpl :
        public ICustom,
        public ATL::CComObjectRootEx< CComMultiThreadModel>
    {
    public:
        BEGIN_COM_MAP(CFooImpl)
            COM_INTERFACE_ENTRY(ICustom)
        END_COM_MAP()
    };
    ```

- **プリコンパイル済みヘッダー (PCH) ファイルと一致しない #include ディレクティブ**(`/Wall` `/WX`にのみ影響)

   以前のバージョンのコンパイラは、プリコンパイル済みヘッダー (PCH) ファイルの使用時に、`#include` と `-Yc` のコンパイル間のソース ファイルの `-Yu` ディレクティブ一致しない場合でも、受け入れていました。 この方法で記述されたコードは、コンパイラで処理できなくなります。   コンパイラは、PCH ファイルの使用時に `#include` ディレクティブの不一致を特定できるようにコンパイラの警告 CC4598 を発行するようになりました。

    ```Output
    warning C4598: 'b.h': included header file specified for Ycc.h at position 2 does not match Yuc.h at that position
    ```

   例 (変更前):

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "b.h"
    #include "a.h"  // mismatched order relative to X.cpp
    #include "c.h"
    ```

   例 (変更後)

   X.cpp (-Ycc.h)

    ```cpp
    #include "a.h"
    #include "b.h"
    #include "c.h"
    ```

   Z.cpp (-Yuc.h)

    ```cpp
    #include "a.h"
    #include "b.h" // matched order relative to X.cpp
    #include "c.h"
    ```

- **プリコンパイル済みヘッダー (PCH) ファイルと一致しないインクルードディレクトリ**(`/Wall` `/WX`のみに影響します)

   プリコンパイル済みヘッダー (PCH) ファイルの使用時に、以前のバージョンのコンパイラは、コンパイラ `-I` と `-Yc` のコンパイルで一致しない include ディレクトリ (`-Yu`) コマンド ライン引数を受け入れていました。 この方法で記述されたコードは、コンパイラで処理できなくなります。 コンパイラは、PCH ファイルの使用時に include ディレクトリ (`-I`) コマンド ライン引数を特定できるコンパイラの警告 CC4599 を発行するようになりました。

    ```Output
    warning C4599: '-I..' : specified for Ycc.h at position 1 does not match Yuc.h at that position
    ```

   例 (変更前)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h Z.cpp
    ```

   例 (変更後)

    ```ms-dos
    cl /c /Wall /Ycc.h -I.. X.cpp
    cl /c /Wall /Yuc.h -I.. Z.cpp
    ```

## <a name="visual-studio-2013-conformance-changes"></a>Visual Studio 2013 の準拠に関する変更

### <a name="compiler"></a>コンパイラ

- **final** のキーワードは、以前はコンパイルできましたが、現在は未解決のシンボル エラーを生成します。

    ```cpp
    struct S1 {
        virtual void f() = 0;
    };

    struct S2 final : public S1 {
        virtual void f();
    };

    int main(S2 *p)
    {
        p->f();
    }
    ```

   呼び出しが**仮想**呼び出しであったことが原因で、以前のバージョンではエラーは発生しませんでした。とはいえ、このプログラムは実行時にクラッシュする結果になりました。 現在は、クラスが final であると認識されるため、リンカー エラーが発生します。 この例でエラーを解決するには、`S2::f` の定義を含む obj に対してリンクを行うことになります。

- コンパイラは現在 ISO C++ 標準に準拠しているため、名前空間の中でフレンド関数を使用する場合は、そのフレンド関数を参照する前に再宣言する必要があります。そうしない場合は、エラーが発生します。 たとえば、次の例はコンパイルされなくなります。

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void C::func(int) {
            NS::func(this);  // error
        }
    }
    ```

   このコードを修正するには、次のように **friend** 関数を宣言します。

    ```cpp
    namespace NS {
        class C {
            void func(int);
            friend void func(C* const) {}
        };

        void func(C* const);  // conforming fix

        void C::func(int) {
            NS::func(this);
        }
    ```

- C++ 標準では、クラス内で明示的な特殊化は許可されません。 Microsoft C++ コンパイラでは、特定の状況でこの作業を実行できますが、次の例のような状況では、現在はエラーが生成されます。コンパイラが、2 番目の関数が最初の関数の特殊化であることを認識しないことが原因です。

    ```cpp
    template < int N>
    class S {
    public:
        template  void f(T& val);
        template < > void f(char val);
    };

    template class S< 1>;
    ```

   このコードを修正するには、2 番目の関数を変更します。

    ```cpp
    template <> void f(char& val);
    ```

- コンパイラでは、次の例に示す 2 つの関数のあいまいさの解消が行われなくなりました。現在ではエラーが出力されます。

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(); // error
    }
    ```

   このコードを修正するには、呼び出しを明確にします。

    ```cpp
    template< typename T> void Func(T* t = nullptr);
    template< typename T> void Func(...);

    int main() {
        Func< int>(nullptr); // ok
    }
    ```

- コンパイラが ISO C++11 に準拠するまで次のコードはコンパイルされ、`x` を **int** 型に解決していました。

    ```cpp
    auto x = {0};
    int y = x;
    ```

   このコードでは、`x` を `std::initializer_list<int>` の型に解決し、 **int**型に `x` を割り当てようとする次の行でエラーが発生するようになりました。(既定では変換は行われません)。このコードを修正するには、 **int**を使用して**auto**を置き換えます。

    ```cpp
    int x = {0};
    int y = x;
    ```

- 初期化の際に右辺値の型が左辺値の型と一致しない場合、集約の初期化は許可されなくなり、ISO C++11 標準では縮小変換を使用しない場合は均一な初期化が必要なためエラーが発行されます。 以前は、縮小変換が使用できる場合、エラーの代わりに[コンパイラの警告 (レベル 4) C4242](../error-messages/compiler-warnings/compiler-warning-level-4-c4242.md) 警告が発行されていました。

    ```cpp
    int i = 0;
    char c = {i}; // error
    ```

   このコードを修正するには、明示的な縮小変換を追加します。

    ```cpp
    int i = 0;
    char c = {static_cast<char>(i)};
    ```

- 次の初期化は、もう許可されません。

    ```cpp
    void *p = {{0}};
    ```

   このコードを修正するには、次の形式のどちらかを使用します。

    ```cpp
    void *p = 0;
    // or
    void *p = {0};
    ```

- 名前参照が変更されました。 次のコードは、Visual Studio 2012 の C++ コンパイラと Visual Studio 2013 の C++ コンパイラで結果が異なります。

    ```cpp
    enum class E1 { a };
    enum class E2 { b };

    int main()
    {
        typedef E2 E1;
        E1::b;
    }
    ```

   Visual Studio 2012 では、式 `E1` に含まれる `E1::b` は、グローバル スコープ内の `::E1` に解決されていました。 Visual Studio 2013 では、式 `E1` に含まれる `E1::b` は `typedef E2` 内で `main()` 定義に解決され、型は `::E2` になります。

- オブジェクトのレイアウトが変更されました。 x64 では、クラスのオブジェクト レイアウトが以前のリリースから変更される場合があります。 **virtual** 関数が存在するものの **virtual** 関数を持つ基底クラスがない場合は、コンパイラのオブジェクト モデルは、データ メンバーのレイアウトの後で **virtual** 関数テーブルにポインターを挿入します。 これは、レイアウトがすべての場合に最適となるわけではないことを意味します。 以前のリリースでは、x64 の最適化によってレイアウトが調整されましたが、複雑なコードでは正常に機能しなかったため、Visual Studio 2013 では削除されました。 たとえば、次のコードを検討してみましょう。

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

- Visual Studio 2013 では、x64 の `sizeof(S2)` の結果は 48 ですが、以前のリリースでは 32 に評価されます。 これを x64 の Visual Studio 2013 の C++ コンパイラで 32 と評価されるようにするには、**virtual** 関数があるダミー基底クラスを追加します。

    ```cpp
    __declspec(align(16)) struct S1 {
    };

    struct dummy {
        virtual ~dummy() {}
    };
    struct S2 : public dummy {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   以前のリリースで最適化しようとしたコード内の場所を検索するには、そのリリースのコンパイラを `/W3` コンパイラオプションと共に使用し、警告 C4370 を有効にします。 次に例を示します。

    ```cpp
    #pragma warning(default:4370)

    __declspec(align(16)) struct S1 {
    };

    struct S2 {
        virtual ~S2();
        void *p;
        S1 s;
    };
    ```

   Visual Studio 2013 以前のバージョンでは、このコードで "C4370: 'S2': パッキングの改善のために、前バージョンのコンパイラからクラスのレイアウトが変更されました" というメッセージが出力されます。

   x86 コンパイラでは、すべてのバージョンのコンパイラで同じ標準以下のレイアウト問題があります。 たとえば、次のコードが x86 でコンパイルされた場合を考えます。

    ```cpp
    struct S {
        virtual ~S();
        int i;
        double d;
    };
    ```

   `sizeof(S)` の結果は 24 です。 しかし、これは、説明した x64 の代替手段を使用すると 16 に減らせます。

    ```cpp
    struct dummy {
        virtual ~dummy() {}
    };

    struct S : public dummy {
        virtual ~S();
        int i;
        double d;
    };
    ```

### <a name="standard-library"></a>標準ライブラリ

Visual Studio 2013 の C++ コンパイラは、Visual Studio 2010 で実装された _ITERATOR_DEBUG_LEVEL の不一致を検出し、RuntimeLibrary の不一致も検出します。 これらの不一致は、コンパイラ オプション `/MT` (静的なリリース)、`/MTd` (静的なデバッグ)、`/MD` (動的なリリース)、および `/MDd` (動的なデバッグ) が混在する場合に発生します。

- コードが、以前のリリースのシミュレートされたエイリアスのテンプレートを検出した場合、変更する必要があります。 たとえば、`allocator_traits<A>::rebind_alloc<U>::other` の代わりに、`allocator_traits<A>::rebind_alloc<U>` と指定する必要があります。 `ratio_add<R1, R2>::type` は必要でなくなり、`ratio_add<R1, R2>` を使うことが勧められていますが、前者でもコンパイルは可能です。これは、`ratio<N, D>` を使用して圧縮するには、typedef "型" が必要であるためです (既に圧縮されている場合も同じ型を使用します)。

- `#include <algorithm>` または `std::min()`を呼び出すときに、`std::max()` を使用する必要があります。

- 既存のコードが、以前のリリースのシミュレートされたスコープを指定された列挙型、つまり名前空間の中でラップされている、スコープを指定されていない従来の列挙型を使用している場合は、そのコードを変更する必要があります。 たとえば、型 `std::future_status::future_status` を参照していた場合は、`std::future_status` を指定する必要があります。 ただし、ほとんどのコードは影響を受けません。たとえば、`std::future_status::ready` は引き続きコンパイルされます。

- `explicit operator bool()` は、演算子 unspecified-bool-type() よりも厳格です。 `explicit operator bool()` を使用すると、bool に明示的に変換できます。たとえば、`shared_ptr<X> sp` を使用している場合、`static_cast<bool>(sp)` と `bool b(sp)` の両方が有効です。また、`if (sp)`、`!sp`、`sp &&` などのブール値検証可能な bool への "状況依存型変換" も用意されています。 ただし、`explicit operator bool()` は bool への暗黙の変換を禁止するため、`bool b = sp;` と指定することはできません。また bool を戻り値の型として指定したり、`return sp` を指定したりすることもできません。

- 現在は、実際の可変個引数テンプレートが実装されているため、_VARIADIC_MAX と関連マクロは何の影響も及ぼしません。 依然として _VARIADIC_MAX を定義している場合は、無視されます。 シミュレートされた可変個引数テンプレートを他の方法でサポートすることを意図して Microsoft のマクロ メカニズムを活用していた場合は、コードを変更する必要があります。

- 通常のキーワードに加えて、C++ 標準ライブラリ ヘッダーは状況依存のキーワード **override** と **final** のマクロ置換を禁止するようになりました。

- `reference_wrapper`、`ref()`、および `cref()` は、一時オブジェクトへのバインディングを禁止するようになります。

- \<random> は、コンパイル時の事前条件を厳密に実装するようになりました。

- さまざまな C++ 標準ライブラリ型の特徴は、"T は完全な型であるものとする" という事前条件を持つことです。 コンパイラは、この事前条件をより厳密に実装するようになりましたが、あらゆる状況でこのことを強制するとは限りません。 (C++ 標準ライブラリ事前条件に違反すると、未定義の動作がトリガーされるため、標準では、強制を保証していません)。

- C++ 標準ライブラリは `/clr:oldSyntax` をサポートしていません。

- C++11 仕様の common_type では、予期しない結果が生じることがありました。特に、common_type\<int, int>::type が int&& を返すことは問題でした。 そこで、コンパイラでは「Proposed Resolution for Library Working Group issue 2141 (ライブラリ ワークグループの懸案事項 2141 に対して推奨される解決)」が実装され、common_type\<int, int="">::type が int を返すようになりました。

   この変更の副作用として、ID の場合に機能しなくなりました (common_type\<T> が常に型 T になるとは限らないからです)。 この動作は、上記の「推奨される解決」に準拠していますが、コードの互換性に影響があります。

   ID 型の特徴が必要な場合、`std::identity`type_traits> で定義された非標準の \< は \<void> で機能しないので使用しないでください。 代わりに、要件に応じた独自の ID 対応の動作を実装します。 次に例を示します。

    ```cpp
    template < typename T> struct Identity {
        typedef T type;
    };
    ```

### <a name="mfc-and-atl"></a>MFC と ATL

- **Visual Studio 2013 のみ**: Unicode が広く使用されていて、MBCS の使用が大幅に拒否されたため、MFC MBCS ライブラリは Visual Studio に含まれていません。 この変更により、新しいコントロールとメッセージの多くは Unicode 専用になったため、MFC は Windows SDK 自体により緊密に整合するようになりました。 ただし、MFC の MBCS ライブラリを引き続き使用する必要がある場合は、MSDN ダウンロード センター ([Visual Studio 2013 のマルチバイト MFC ライブラリ](https://www.microsoft.com/download/details.aspx?id=40770)) からダウンロードできます。 Visual C++ 再頒布可能パッケージにも、引き続きこのライブラリが含まれています。  (注: MBCS DLL は Visual Studio 2015 以降の C++ セットアップ コンポーネントに含まれています。)

- MFC リボンのアクセシビリティが変更されました。  1 レベルのアーキテクチャではなく、階層的なアーキテクチャが用意されました。 `CRibbonBar::EnableSingleLevelAccessibilityMode()` を呼び出して、引き続き古い動作を使用することもできます。

- `CDatabase::GetConnect` メソッドは削除されました。 セキュリティを改善するために、接続文字列は暗号化された状態で格納され、必要な場合にのみ復号化されるようになりました。プレーンテキストとして返すことはできません。  この文字列を取得するには、`CDatabase::Dump` メソッドを使用します。

- `CWnd::OnPowerBroadcast` のシグネチャが変更されました。 このメッセージ ハンドラーのシグネチャは、2 番目のパラメーターとして LPARAM を受け取るように変更されました。

- メッセージ ハンドラーに対応するためにシグネチャが変更されました。 新しく追加された ON_WM_* メッセージ ハンドラーを使用するために、次の関数のパラメーター リストが変更されました。

   - `CWnd::OnDisplayChange` は (WPARAM, LPARAM) から (UINT, int, int) に変更され、メッセージ マップに新しい ON_WM_DISPLAYCHANGE マクロを使用できるようになりました。

   - `CFrameWnd::OnDDEInitiate` は (WPARAM, LPARAM) から (CWnd*, UINT, UNIT) に変更され、メッセージ マップに新しい ON_WM_DDE_INITIATE マクロを使用できるようになりました。

   - `CFrameWnd::OnDDEExecute` は (WPARAM, LPARAM) から (CWnd*, HANDLE) に変更され、メッセージ マップに新しい ON_WM_DDE_EXECUTE マクロを使用できるようになりました。

   - `CFrameWnd::OnDDETerminate` のパラメーターは (WPARAM, LPARAM) から (CWnd*) に変更され、メッセージ マップに新しい ON_WM_DDE_TERMINATE マクロを使用できるようになりました。

   - `CMFCMaskedEdit::OnCut` は (WPARAM, LPARAM) からパラメーターなしに変更され、メッセージ マップで新しい ON_WM_CUT マクロを使用できるようになりました。

   - `CMFCMaskedEdit::OnClear` は (WPARAM, LPARAM) からパラメーターなしに変更され、メッセージ マップで新しい ON_WM_CLEAR マクロを使用できるようになりました。

   - `CMFCMaskedEdit::OnPaste` は (WPARAM, LPARAM) からパラメーターなしに変更され、メッセージ マップで新しい ON_WM_PASTE マクロを使用できるようになりました。

- `#ifdef` ディレクティブは MFC ヘッダー ファイル内から削除されました。 MFC ヘッダー ファイル内に存在していた、サポートされていないバージョンの Windows (WINVER `#ifdef` 0x0501) に関連する多数の &lt; ディレクティブが削除されました。

- ATL DLL (atl120.dll) が削除されました。 ATL は、ヘッダーおよび 1 つのスタティック ライブラリ (atls.lib) として提供されるようになりました。

- atlsd.lib、atlsn.lib、および atlsnd.lib が削除されました。 atls.lib は、文字セットに対する依存関係を持たず、デバッグ/リリースに固有のコードも含まなくなりました。 これは、Unicode/ANSI のどちらでも、またデバッグ/リリースのどちらでも同じ動作をするため、このライブラリのただ 1 つのバージョンが必要とされるようになりました。

- ATL DLL と共に ATL/MFC Trace Tool が削除され、トレース機構が簡略化されました。 `CTraceCategory` コンストラクターは 1 つのパラメーター (カテゴリ名) を受け取り、TRACE マクロは CRT のデバッグ レポート関数を呼び出します。

## <a name="visual-studio-2012-breaking-changes"></a>Visual Studio 2012 の重要な変更点

### <a name="compiler"></a>コンパイラ

- `/Yl` コンパイラ オプションは変更されました。 コンパイラは既定でこのオプションを使用しますが、状況によっては LNK2011 エラーが発生する可能性があります。 詳細については、「[/Yl (Inject PCH Reference for Debug Library)](../build/reference/yl-inject-pch-reference-for-debug-library.md)」(/Yl (デバッグ ライブラリの PCH 参照の挿入)) を参照してください。

- `/clr` を使用してコンパイルするコードでは、**enum** クラス キーワードで、共通言語ランタイム (CLR) enum ではなく C++11 enum を定義します。 CLR enum を定義するには、アクセシビリティを明示する必要があります。

- 依存名を明確に区別するには、テンプレート キーワードを使用します (C++ 言語標準の準拠)。 次の例では、あいまいさを解決するために、強調表示されたテンプレート キーワードを使用する必要があります。 詳細については、「[Name Resolution for Dependent Types](../cpp/name-resolution-for-dependent-types.md)」(依存する型の名前解決) を参照してください。

    ```cpp
    template < typename X = "", typename = "" AY = "">
    struct Container { typedef typename AY::template Rebind< X> ::Other AX; };
    ```

- float 型の定数式は、次の例のようにテンプレート引数として使用できなくなりました。

    ```cpp
    template<float n=3.14>
    struct B {};  // error C2993: 'float': illegal type for non-type template parameter 'n'
    ```

- `/GS` コマンドライン オプションを使用してコンパイルし、off-by-one の脆弱性があるコードの場合、次の疑似コード例で示すように、実行時にプロセスが停止する可能性があります。

    ```cpp
    char buf[MAX]; int cch; ManipulateString(buf, &cch); // ... buf[cch] = '\0'; // if cch >= MAX, process will terminate
    ```

- x86 ビルドの既定のアーキテクチャは SSE2 に変更されたため、コンパイラから SSE 命令が発せられる可能性があります。その結果、XMM レジスタを使用して浮動小数点演算が実行されます。 以前の動作に戻すには、`/arch:IA32` コンパイラ フラグを使用してアーキテクチャを IA32 と指定します。

- コンパイラから、以前は発行されなかった[コンパイラの警告 (レベル 4) C4703](../error-messages/compiler-warnings/compiler-warning-level-4-c4703.md) と C4701 が発行される可能性があります。 コンパイラでは、ポインター型の初期化されていないローカル変数の使用がより厳格にチェックされるようになりました。

- 新しいリンカー フラグ `/HIGHENTROPYVA` を指定すると、通常 Windows 8 では、メモリの割り当てが実行され、64 ビット アドレスが返されます (Windows 8 より前の場合、このような割り当てでは、2 GB 未満のアドレスが返されることが多くなります)。この変更により、既存のコードでポインターの切り捨てのバグが発生する可能性があります。 既定では、このスイッチはオンです。 この動作を無効にするには、`/HIGHENTROPYVA:NO` を指定します。

- マネージド コンパイラ (Visual Basic/C#) は、マネージド ビルドの場合に `/HIGHENTROPYVA` もサポートしています。  ただし、この場合、`/HIGHENTROPYVAswitch` は既定でオフです。

### <a name="ide"></a>IDE

- C++/CLI で Windows フォーム アプリケーションを作成しないことをお勧めしますが、既存の C++/CLI UI アプリケーションの保守はサポートされます。 Windows フォーム アプリケーションやその他の .NET UI アプリケーションを作成する必要がある場合は、C# または Visual Basic を使用してください。 C++/CLI は、相互運用性の目的でのみ使用してください。

### <a name="parallel-patterns-library-and-concurrency-runtime-library"></a>並列パターン ライブラリとコンカレンシー ランタイム ライブラリ

`SchedulerType` の `UmsThreadDefault` 列挙体は非推奨です。 `UmsThreadDefault` を指定すると、非推奨の警告が生成され、内部的に `ThreadScheduler` にマップされます。

### <a name="standard-library"></a>標準ライブラリ

- C++98/03 標準と C++11 標準間の破壊的変更に伴い、明示的なテンプレート引数を使用して (`make_pair()` のように) `make_pair<int, int>(x, y)` を呼び出しても、一般的に Visual Studio 2012 の Visual C++ ではコンパイルされなくなりました。 この問題を解決するには、`make_pair() ` のように明示的なテンプレート引数を指定せずに常に `make_pair(x, y)` を呼び出す必要があります。 明示的なテンプレート引数を指定すると、この関数の目的を達成できません。 結果の型を正確に制御する必要がある場合は、`pair` のように `make_pair` ではなく `pair<short, short>(int1, int2)` を使用します。

- C++ 98/03 と C++ 11 標準の間のもう1つの重大な変更: が暗黙的に B に変換可能であり、B が暗黙的に C に変換可能ではありませんが、が C に暗黙的に変換可能ではありません。 C++ 98/03 および Visual Studio 2010 は、暗黙的または明示 `pair<C, X>`的に変換でき `pair<A, X>`。 (もう1つの型である X は、ここでは重要ではなく、ペアの最初の型に固有ではありません)。Visual C++ Studio 2012 のコンパイラは、が暗黙的に C に変換できないことを検出し、オーバーロードの解決からペアの変換を削除します。 この変更は、多くのシナリオでは、よい結果になります。 たとえば、この変更で、`func(const pair<int, int>&)` と `func(const pair<string, string>&)` のオーバーロードと、`func()` を指定した `pair<const char *, const char *>` の呼び出しはコンパイルされるようになります。 ただし、積極的なペアの変換に依存するコードの場合、これは互換性に影響する変更です。 通常、このようなコードを修正するには、変換の一部を明示的に実行します。たとえば、`make_pair(static_cast<B>(a), x)` を `pair<C, X>` を受け取る関数に渡します。

- Visual Studio 2010 では、プリプロセッサのメカニズムでオーバーロードと特殊化を排除することで、引数の上限が 10 個の可変個引数テンプレート (たとえば、`make_shared<T>(arg1, arg2, argN)`) のシミュレーションが行われていました。 Visual Studio 2012 では、引数の上限は 5 個まで減ったので、多くのユーザーは、コンパイル時間とコンパイラのメモリ使用量が改善されました。 ただし、プロジェクト全体で _VARIADIC_MAX を 10 と明示的に定義することで、以前の上限を設定できます。

- C++ 標準ライブラリのヘッダーを含める場合、C++11 17.6.4.3.1 [macro.names]/2 では、キーワードのマクロ置換が禁止されるようになりました。 マクロ置換されたキーワードが検出されると、ヘッダーからコンパイラ エラーが発行されます (_ALLOW_KEYWORD_MACROS を定義すると、そのようなコードをコンパイルできますが、その使用は強くお勧めしません)。例外として、マクロ形式の `new` は既定で許可されています。これは、ヘッダーが `#pragma push_macro("new")`/`#undef new`/`#pragma pop_macro("new")`を使用して包括的に保護するためです。 _ENFORCE_BAN_OF_MACRO_NEW を定義すると、その名前が示すとおりの処理が実行されます。

- 多様な最適化とデバッグのチェックを実装するために、C++ 標準ライブラリの実装では、バイナリの互換性が Visual Studio のバージョン (2005、2008、2010、2012) ごとに意図的に保たれていません。 C++ 標準ライブラリを使用すると、異なるバージョンを使用してコンパイルされたオブジェクト ファイルとスタティック ライブラリは 1 つのバイナリ (EXE または DLL) に混在させることができず、C++ 標準ライブラリ オブジェクトは異なるバージョンを使用してコンパイルされたバイナリ間で渡すことができません。 Visual Studio 2010 を使用してコンパイルした (C++ 標準ライブラリを使用する) オブジェクト ファイルとスタティック ライブラリと、Visual Studio 2012 の C++ コンパイラを使用してコンパイルしたものが混在すると、_MSC_VER の不一致に関するリンカー エラーが発生します。この _MSC_VER は、コンパイラのメジャー バージョン (Visual Studio 2012 の Visual C++ の場合は 1700) を含むマクロです。 このチェックでは、DLL の混在を検出できず、Visual Studio 2008 以前のバージョンが関係する混在も検出できません。

- Visual Studio 2012 の C++ コンパイラでは、Visual Studio 2010 で実装された _ITERATOR_DEBUG_LEVEL の不一致の検出に加え、ランタイム ライブラリの不一致も検出します。 これらの不一致は、コンパイラ オプション `/MT` (静的なリリース)、`/MTd` (静的なデバッグ)、`/MD` (動的なリリース)、および `/MDd` (動的なデバッグ) が混在する場合に発生します。

- `operator<()`、`operator>()`、`operator<=()`、および `operator>=()` は、以前はコンテナーの `std::unordered_map` および `stdext::hash_map` ファミリに使用できましたが、実装しても役に立っていませんでした。 これらの標準ではない演算子は、Visual Studio 2012 の Visual C++ から削除されました。 また、`operator==()` ファミリの `operator!=()` および `std::unordered_map` の実装は、`stdext::hash_map` ファミリも対象にするように拡張されました (新しいコードでは、`stdext::hash_map` ファミリを使用しないことをお勧めします)。

- C++11 22.4.1.4 [locale.codecvt] では、変更可能な `codecvt::length()`パラメーターが `codecvt::do_length()` と `stateT&` によって取得されるように指定されていましたが、Visual Studio 2010 によって `const stateT&` が取得されました。 Visual Studio 2012 の C++ コンパイラは、標準で必須のパラメーターとして `stateT&` を受け取ります。 この違いは、仮想関数 `do_length()` をオーバーライドする場合に重要になります。

### <a name="crt"></a>CRT

- C ランタイム (CRT) ヒープは new と malloc() に使用されますが、プライベートではなくなりました。 CRT はプロセス ヒープを使用するようになりました。 つまり、DLL がアンロードされてもヒープは破棄されないので、CRT に静的にリンクされている DLL は、DLL コードで割り当てられたメモリがアンロード前に確実にクリーンアップされるようにする必要があります。

- `iscsymf()` 関数は負の値でアサートします。

- `threadlocaleinfostruct` 構造体は、ロケール関数の変更に対応するために変更されました。

- `memxxx()`、`strxxx()` などの対応する組み込みがある CRT 関数は intrin.h から削除されました。 これらの関数のためにのみ intrin.h を含めた場合、今後は対応する CRT ヘッダーも含める必要があります。

### <a name="mfc-and-atl"></a>MFC と ATL

- Fusion のサポート (afxcomctl32.h) が削除されました。そのため、\<afxcomctl32.h> に定義されているすべてのメソッドは削除されました。 ヘッダー ファイル \<afxcomctl32.h> と \<afxcomctl32.inl> は削除されました。

- `CDockablePane::RemoveFromDefaultPaneDividier` の名前は `CDockablePane::RemoveFromDefaultPaneDivider` に変更されました。

- LPCTSTR を使用するように `CFileDialog::SetDefExt` のシグネチャは変更されました。そのため、Unicode のビルドに影響があります。

- 互換性のために残されていた ATL トレース カテゴリは削除されました。

- `CBasePane::MoveWindow` を受け取るように `const CRect` のシグネチャは変更されました。

- `CMFCEditBrowseCtrl::EnableBrowseButton` のシグネチャは変更されました。

- `m_fntTabs` から `m_fntTabsBold` および `CMFCBaseTabCtrl` を削除しました。

- `CMFCRibbonStatusBarPane` コンストラクターにパラメーターが追加されました (これは既定のパラメーターなので、ソースの重大な変更ではありません)。

- `CMFCRibbonCommandsListBox` コンストラクターにパラメーターが追加されました (これは既定のパラメーターなので、ソースの重大な変更ではありません)。

- `AFXTrackMouse` API (と関連する timer proc) が削除されました。 代わりに、Win32 API `TrackMouseEvent`を使用します。

- `CFolderPickerDialog` コンストラクターにパラメーターが追加されました (これは既定のパラメーターなので、ソースの重大な変更ではありません)。

- `CFileStatus` 構造体のサイズは変更されました。`m_attribute` のメンバーは、(`GetFileAttributes` から返される値に合わせて) BYTE から DWORD に変更されました。

- Unicode ビルドの場合、`CRichEditCtrl` と `CRichEditView` は、RICHEDIT_CLASS (RichEdit 3.0 コントロール) ではなく MSFTEDIT_CLASS (RichEdit 4.1 コントロール) を使用します。

- Windows Vista、Windows 7、Windows 8 では、`AFX_GLOBAL_DATA::IsWindowsThemingDrawParentBackground` は常に TRUE なので、削除されました。

- Windows Vista、Windows 7、Windows 8 では、`AFX_GLOBAL_DATA::IsWindowsLayerSupportAvailable` は常に TRUE なので、削除されました。

- `AFX_GLOBAL_DATA::DwmExtendFrameIntoClientArea` は削除されました。 Windows Vista、Windows 7、Windows 8 では、Windows API を直接呼び出してください。

- `AFX_GLOBAL_DATA::DwmDefWindowProc` は削除されました。 Windows Vista、Windows 7、Windows 8 では、Windows API を直接呼び出してください。

- 名前の競合を排除するために、`AFX_GLOBAL_DATA::DwmIsCompositionEnabled` の名前は `IsDwmCompositionEnabled` に変更されました。

- 複数の MFC の内部タイマーの識別子を変更し、定義を afxres.h (AFX_TIMER_ID_*) に移動しました。

- ON_WM_EXITSIZEMOVE マクロに合わせて `OnExitSizeMove` メソッドのシグネチャは変更されました。

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- ON_WM_DWMCOMPOSITIONCHANGED マクロに合わせて `OnDWMCompositionChanged` の名前とシグネチャは変更されました。

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

   - `CPaneFrameWnd`

- ON_WM_MOUSELEAVE マクロに合わせて `OnMouseLeave` メソッドのシグネチャは変更されました。

   - `CMFCCaptionBar`

   - `CMFCColorBar`

   - `CMFCHeaderCtrl`

   - `CMFCProperySheetListBox`

   - `CMFCRibbonBar`

   - `CMFCRibbonPanelMenuBar`

   - `CMFCRibbonRichEditCtrl`

   - `CMFCSpinButtonCtrl`

   - `CMFCToolBar` ReplaceThisText

   - `CMFCToolBarComboBoxEdit`

   - `CMFCToolBarEditCtrl`

   - `CMFCAutoHideBar`

- ON_WM_POWERBROADCAST マクロに合わせて `OnPowerBroadcast` のシグネチャは変更されました。

   - `CFrameWndEx`

   - `CMDIFrameWndEx`

- ON_WM_STYLECHANGED マクロに合わせて `OnStyleChanged` のシグネチャは変更されました。

   - `CMFCListCtrl`

   - `CMFCStatusBar`

- 内部メソッド `FontFamalyProcFonts` の名前は `FontFamilyProcFonts` に変更されました。

- 一部の状況で発生するメモリ リークを排除するために、多数のグローバル静的 `CString` オブジェクトが削除されました (#defines に置き換えられました)。また、次のクラス メンバー変数が削除されました。

   - `CKeyBoardManager::m_strDelimiter`

   - `CMFCPropertyGridProperty::m_strFormatChar`

   - `CMFCPropertyGridProperty::m_strFormatShort`

   - `CMFCPropertyGridProperty::m_strFormatLong`

   - `CMFCPropertyGridProperty::m_strFormatUShort`

   - `CMFCPropertyGridProperty::m_strFormatULong`

   - `CMFCPropertyGridProperty::m_strFormatFloat`

   - `CMFCPropertyGridProperty::m_strFormatDouble`

   - `CMFCToolBarImages::m_strPngResType`

   - `CMFCPropertyGridProperty::m_strFormat`

- `CKeyboardManager::ShowAllAccelerators` のシグネチャが変更されました。また、アクセラレータの区切り文字パラメーターが削除されました。

- `CPropertyPage::GetParentSheet` が追加されました。`CPropertyPage` クラスで `GetParent` の代わりに呼び出して、正しい親シート ウィンドウを取得してください。これは `CPropertyPage` の親ウィンドウまたは親の親ウィンドウの場合があります。 必要に応じて、`GetParentSheet` ではなく `GetParent` を呼び出すようにコードを変更します。

- バランスが取れておらず、誤って無効になる警告を引き起こす ATLBASE.H の #pragma warning(push) が修正されました。 ATLBASE.H が解析された後、警告は適切に有効になるようになりました。

- D2D に関連するメソッドが AFX_GLOBAL_DATA から _AFX_D2D_STATE に移動されました。

   - `GetDirectD2dFactory`

   - `GetWriteFactory`

   - `GetWICFactory`

   - `InitD2D`

   - `ReleaseD2DRefs`

   - `IsD2DInitialized`

   - `D2D1MakeRotateMatrix`

   - たとえば、`afxGlobalData.IsD2DInitialized` を呼び出す代わりに `AfxGetD2DState->IsD2DInitialized` を呼び出します。

- 互換性のために残されていた ATL*.CPP ファイルが \atlmfc\include\ フォルダーから削除されました。

- `afxGlobalData` の要件を満たすために、`DLLMain` の初期化は CRT の初期化時ではなくオンデマンドに移動されました。

- `RemoveButtonByIndex` メソッドが `CMFCOutlookBarPane` クラスに追加されました。

- `CMFCCmdUsageCount::IsFreqeuntlyUsedCmd` は `IsFrequentlyUsedCmd` に修正されました。

- `RestoreOriginalstate` のいくつかのインスタンスは `RestoreOriginalState (CMFCToolBar, CMFCMenuBar, CMFCOutlookBarPane)` に修正されました。

- 使用されていないメソッド (`CDockablePane`、`SetCaptionStyle`、`IsDrawCaption`、`IsHideDisabledButtons`、`GetRecentSiblingPaneInfo`) が `CanAdjustLayout` から削除されました。

- `CDockablePane` の静的メンバー変数 `m_bCaptionText` と `m_bHideDisabledButtons` が削除されました。

- オーバーライド `DeleteString` メソッドが `CMFCFontComboBox` に追加されました。

- 使用されていないメソッド (`CPane` および `GetMinLength`) が `IsLastPaneOnLastRow` から削除されました。

- 名前が `CPane::GetDockSiteRow(CDockingPanesRow *)` から `CPane::SetDockSiteRow` に変更されました。

## <a name="visual-studio-2010-breaking-changes"></a>Visual Studio 2010 の重要な変更点

### <a name="compiler"></a>コンパイラ

- **auto** キーワードの既定の意味が変更されました。 古い意味はまれにしか使用されないので、ほとんどのアプリケーションはこの変更の影響を受けません。

- 新しい **static_assert** キーワードが導入されました。コード内で既にこの名前の識別子がある場合は、名前の競合が発生します。

- 新しいラムダ表記をサポートすると、IDL uuid 属性の引用符なしの GUID のコーディングはサポートされなくなります。

- .NET Framework 4 では、破損状態例外という概念を導入しました。これは、プロセスが回復不能な破損状態のままになる例外です。 既定では、他のすべての例外をキャッチする /EHa コンパイラ オプションを使用しても、破損状態例外をキャッチできません。                 破損状態例外を明示的にキャッチするには、__try-\__except ステートメントを使用します。 または、[HandledProcessCorruptedStateExceptions] 属性を適用して、破損状態例外をキャッチする関数を有効にします。  この変更は、主に、破損状態例外をキャッチする必要があるシステム プログラマに影響があります。 8 つの例外として、STATUS_ACCESS_VIOLATION、STATUS_STACK_OVERFLOW、EXCEPTION_ILLEGAL_INSTRUCTION、EXCEPTION_IN_PAGE_ERROR、EXCEPTION_INVALID_DISPOSITION、EXCEPTION_NONCONTINUABLE_EXCEPTION、EXCEPTION_PRIV_INSTRUCTION、STATUS_UNWIND_CONSOLIDATE があります。                 これらの例外の詳細については、[GetExceptionCode](/windows/win32/Debug/getexceptioncode) マクロを参照してください。

- `/GS` コンパイラ オプションは改善され、以前のバージョンよりも包括的にバッファー オーバーランを防ぐことができるようになりました。 このバージョンでは、スタックに追加のセキュリティ チェックが挿入され、パフォーマンスが低下する可能性があります。 特定の関数についてセキュリティ チェックを挿入しないようにコンパイラに指示するには、新しい `__declspec(safebuffers)` キーワードを使用します。

- `/GL` (プログラム全体の最適化) と `/clr` (共通言語ランタイムのコンパイル) という 2 つのコンパイラ オプションを指定してコンパイルすると、`/GL` オプションは無視されます。 この組み合わせのコンパイラ オプションではほとんどメリットがないため、この変更が加えられました。 この変更の結果、ビルドのパフォーマンスは改善されました。

- 既定では、Visual Studio 2010 でのトライグラフのサポートは無効です。 トライグラフのサポートを有効にするには、`/Zc:trigraphs` コンパイラ オプションを使用します。 トライグラフは、2 つの連続する疑問符 ("??") と、一意の 3 番目の文字で構成されます。 コンパイラはトライグラフを対応する区切り文字に置き換えます。 たとえば、`??=` というトライグラフは '#' という文字に置き換えられます。 トライグラフは、一部の区切り文字に対応する適切なグラフィック表示がない文字セットを含む C ソース ファイルで使用できます。

- リンカーは Windows 98 の最適化をサポートしなくなりました。 `/OPT` (最適化) オプションで `/OPT:WIN98` または `/OPT:NOWIN98` を指定すると、コンパイル時エラーが発生します。

- RuntimeLibrary および DebugInformationFormat ビルド システム プロパティで指定されている既定のコンパイラ オプションは変更されました。 これらのプロパティは、既定で、Visual C++ リリース 7.0 ～ 10.0 で作成されたプロジェクトで指定されます。 Visual C++ 6.0 で作成したプロジェクトを移行する場合は、これらのプロパティの値を指定するかどうかを検討してください。

- Visual Studio 2010 では、RuntimeLibrary = MultiThreaded (`/MD`)、DebugInformationFormat = ProgramDatabase (`/Zi`) です。 Visual C++ 9.0 では、RuntimeLibrary = MultiThreaded (`/MT`)、DebugInformationFormat = Disabled です。

### <a name="clr"></a>CLR

- Microsoft C# と Visual Basic のコンパイラから、非プライマリ相互運用機能アセンブリ (非 PIA) を生成できるようになりました。 非 PIA アセンブリは、関連するプライマリ相互運用機能アセンブリ (PIA) を展開しなくても COM 型を使用できます。 Visual C# または Visual Basic で生成された非 PIA アセンブリを使用する場合は、コンパイル コマンドで PIA アセンブリを参照してから、ライブラリを使用する非 PIA アセンブリを参照する必要があります。

### <a name="visual-studio-c-projects-and-msbuild"></a>Visual Studio C++ プロジェクトと MSBuild

- Visual Studio C++ プロジェクトは MSBuild ツールに基づくようになりました。 その結果、プロジェクト ファイルでは、新しい XML ファイル形式と .vcxproj ファイルのサフィックスを使用します。 Visual Studio 2010 は、プロジェクト ファイルを以前のバージョンの Visual Studio から新しいファイル形式に自動的に変換します。 以前のビルド ツールの VCBUILD.exe、またはプロジェクト ファイルのサフィックス .vcproj に依存している場合、既存のプロジェクトは影響を受けます。

- 以前のリリースの Visual C++ では、プロパティ シートの遅延評価をサポートしていました。 たとえば、親プロパティ シートが子プロパティ シートをインポートし、子に定義されている変数を親が使用して他の変数を定義することができます。 遅延評価によって、子プロパティ シートがインポートされる前であっても、親が子の変数を使用できるようになります。 MSBuild では早期評価のみがサポートされるため、Visual Studio 2010 では、プロジェクト シート変数は定義前に使用できません。

### <a name="ide"></a>IDE

- アプリケーションの終了ダイアログ ボックスで、アプリケーションは終了しなくなります。 以前のリリースでは、`abort()` または `terminate()` 関数でアプリケーションの製品版ビルドを閉じると、C ランタイム ライブラリのコンソール ウィンドウまたはダイアログ ボックスにアプリケーションの終了メッセージが表示されていました。 メッセージの一部を引用すると、"このアプリケーションは、通常と異なる方法でランタイムにアプリケーションを中止するように要求しました。 詳細については、アプリケーションのサポート チームに問い合わせてください" と表示されていました。 Windows によって現在の終了ハンドラー (通常は Windows エラー報告 (ワトソン博士) ダイアログボックスまたは Visual Studio デバッガー) が表示されたため、アプリケーション終了メッセージは冗長でした。 Visual Studio 2010 以降、C ランタイム ライブラリではこのメッセージが表示されなくなりました。 また、ランタイムでは、デバッガーの起動前にアプリケーションが終了しなくなりました。 アプリケーションの終了メッセージの以前の動作に依存している場合にのみ、これは互換性に影響する変更です。

- 特に Visual Studio 2010 では、IntelliSense は C++/CLI コードまたは属性に使用できません。 **[すべての参照の検索]** はローカル変数には使用できません。また、コード モデルでは、インポートしたアセンブリから型名を取得したり、型を完全修飾名に解決したりすることはできません。

### <a name="libraries"></a>ライブラリ

- SafeInt クラスは Visual C++ に含まれていません。また、別のダウンロードにも含まれなくなりました。 "SafeInt" という名前のクラスを開発した場合にのみ、これは破壊的変更です。

- ライブラリ展開モデルは、特定バージョンのダイナミック リンク ライブラリを検索するためにマニフェストを使用しなくなりました。 各ダイナミック リンク ライブラリの名前にはバージョン番号が含まれているので、その名前を使用してライブラリを特定してください。

- 以前のバージョンの Visual Studio では、ランタイム ライブラリを再ビルドできます。 Visual Studio 2010 では、C ランタイム ライブラリ ファイルの独自のコピーのビルドがサポートされなくなりました。

### <a name="standard-library"></a>標準ライブラリ

- \<iterator> ヘッダーは、他の多くのヘッダー ファイルに自動的に含まれなくなりました。 代わりに、ヘッダーで定義されているスタンドアロンの反復子のサポートが必要な場合は、そのヘッダーを明示的に含めます。 以前のビルド ツールの VCBUILD.exe、またはプロジェクト ファイルのサフィックス .vcproj.iterator に依存している場合、既存のプロジェクトは影響を受けます。

- \<algorithm> ヘッダーの checked_* 関数と unchecked_\* 関数は削除されました。 また、\<iterator>> ヘッダーの `checked_iterator` が削除され、`unchecked_array_iterator` クラスが追加されました。

- `CComPtr::CComPtr(int)` コンストラクターは削除されました。 このコンストラクターを使用すると、NULL マクロから `CComPtr` オブジェクトを構築できますが、必須ではなく、ゼロ以外の整数から無意味な構造を構築できます。

   `CComPtr` は NULL から構築できます。これは 0 と定義されますが、リテラル 0 以外の整数から構築されると失敗します。 代わりに **nullptr** を使用してください。

- 次の `ctype` メンバー関数 (`ctype::_Do_narrow_s`、`ctype::_Do_widen_s`、`ctype::_narrow_s`、`ctype::_widen_s`) は削除されました。 これらのメンバー関数のいずれかをアプリケーションで使用する場合は、対応するセキュリティで保護されていないバージョン (`ctype::do_narrow`、`ctype::do_widen`、`ctype::narrow`、`ctype::widen`) に置き換えます。

### <a name="crt-mfc-and-atl-libraries"></a>CRT、MFC、ATL ライブラリ

- CRT、MFC、および ATL ライブラリをビルドするために、ユーザー サポートは削除されました。 たとえば、適切な NMAKE ファイルが指定されていないとします。 一方、ユーザーは、これらのライブラリのソース コードに対してアクセス権を持っています。 また、Microsoft がこれらのライブラリのビルドに使用する MSBuild オプションについて説明したドキュメントが、Visual C++ チーム ブログに投稿される可能性があります。

- IA64 の MFC のサポートは削除されました。 ただし、IA64 の CRT と ATL のサポートはまだ提供されています。

- MFC モジュール定義 (.def) ファイルでは序数が再利用されなくなりました。 この変更は、マイナー バージョン間で序数の違いがないことを示します。また、サービス パックとクイック修正エンジニアリング リリースのバイナリの互換性は改善される予定です。

- 新しい仮想関数が `CDocTemplate` クラスに追加されました。 この新しい仮想関数は [CDocTemplate Class](../mfc/reference/cdoctemplate-class.md) です。 以前のバージョンの `OpenDocumentFile` には 2 つのパラメーターがありました。 新しいバージョンのパラメーターは 3 つです。 再起動マネージャーをサポートするには、`CDocTemplate` から派生したクラスで、3 つのパラメーターがあるバージョンを実装する必要があります。 新しいパラメーターは `bAddToMRU` です。

### <a name="macros-and-environment-variables"></a>マクロと環境変数

- 環境変数 __MSVCRT_HEAP_SELECT はサポートされなくなりました。 この環境変数は削除されました。これに代わる機能はありません。

### <a name="microsoft-macro-assembler-reference"></a>Microsoft Macro Assembler リファレンス

- Microsoft Macro Assembler リファレンス コンパイラからいくつかのディレクティブが削除されました。 削除されたディレクティブは、`.186`、`.286`、`.286P`、`.287`、`.8086`、`.8087`、および `.NO87` です。

## <a name="visual-studio-2008-breaking-changes"></a>Visual Studio 2008 の重要な変更点

### <a name="compiler"></a>コンパイラ

- Windows 95、Windows 98、Windows ME、および Windows NT プラットフォームはサポートされなくなりました。 これらのオペレーティング システムは対象のプラットフォーム一覧から削除されました。

- コンパイラは、ATL サーバーと直接関連する複数の属性をサポートしなくなりました。 次の属性はサポートされなくなりました。

   - perf_counter

   - perf_object

   - perfmon

   - request_handler

   - soap_handler

   - soap_header

   - soap_method

   - tag_name

### <a name="visual-studio-c-projects"></a>Visual Studio C++ のプロジェクト

- 以前のバージョンの Visual Studio からプロジェクトをアップグレードする場合、必要に応じて 0x0500 以上になるように WINVER マクロと _WIN32_WINNT マクロを変更します。

- Visual Studio 2008 以降、新しいプロジェクト ウィザードでは C++ SQL Server プロジェクトを作成するオプションがなくなりました。 以前のバージョンの Visual Studio を使用して作成した SQL Server プロジェクトは、今後も適切にコンパイルされ、動作します。

- Windows API ヘッダー ファイル Winable.h は削除されました。 代わりに Winuser.h をインクルードしてください。

- Windows API ライブラリ Rpcndr.lib は削除されました。 代わりに rpcrt4.lib とリンクしてください。

### <a name="crt"></a>CRT

- Windows 95、Windows 98、Windows Millennium Edition、および Windows NT 4.0 のサポートは削除されました。

- 次のグローバル変数は削除されました。

   - _osplatform

   - _osver

   - _winmajor

   - _winminor

   - _winver

- 次の関数は削除されました。 代わりに Windows API 関数 `GetVersion` または `GetVersionEx` を使用してください。

   - _get_osplatform

   - _get_osver

   - _get_winmajor

   - _get_winminor

   - _get_winver

- SAL 注釈の構文は変更されました。 詳細については、「[SAL 注釈](../c-runtime-library/sal-annotations.md)」を参照してください。

- IEEE フィルターは SSE 4.1 命令セットをサポートするようになりました。 詳細については、「[_fpieee_flt](../c-runtime-library/reference/fpieee-flt.md)_fpieee_flt」を参照してください。

- Visual Studio に付属する C ランタイム ライブラリは、システム DLL msvcrt.dll に依存しなくなりました。

### <a name="standard-library"></a>標準ライブラリ

- Windows 95、Windows 98、Windows Millennium Edition、および Windows NT 4.0 のサポートは削除されました。

- _HAS_ITERATOR_DEBUGGING を定義してデバッグ モードでコンパイルすると (Visual Studio 2010 以降は [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) に置き換えられます)、反復子が基礎となるコンテナーの境界を越えて増加または減少しようとしたときに、アプリケーションはアサートするようになりました。

- スタック クラスのメンバー変数 c は保護済みと宣言されるようになりました。 以前は、このメンバー変数はパブリックと宣言されていました。

- `money_get::do_get` の動作が変更されました。 以前は、`frac_digits` で呼び出されたよりも多くの小数点以下桁数で金額を解析すると、`do_get` はすべてを使用していました。 現在は、最高でも `do_get` 文字まで使用すると、`frac_digits` は解析を停止します。

### <a name="atl"></a>ATL

- CRT に依存することなく ATL をビルドすることはできません。 以前のバージョンの Visual Studio では、#define ATL_MIN_CRT を使用して、ATL プロジェクトの CRT への依存を最小限にすることができます。 Visual Studio 2008 では、ATL_MIN_CRT が定義されているかどうかにかかわらず、すべての ATL プロジェクトの CRT への依存は最小限です。

- ATL サーバーのコードベースは、CodePlex の共有ソース プロジェクトとしてリリースされており、Visual Studio の一部としてはインストールされません。 atlenc.h のクラスのデータ エンコードとデコード、および atlutil.h と atlpath のユーティリティ関数とクラスは残され、ATL ライブラリの一部になりました。 ATL サーバーに関連する一部のファイルは、Visual Studio に含まれなくなりました。

- 一部の関数は DLL に含まれなくなりました。 これらの関数はインポート ライブラリに含まれています。 これは、関数を静的に使用するコードには影響がありません。 これらの関数を動的に使用するコードにのみ影響があります。

- マクロ PROP_ENTRY と PROP_ENTRY_EX は非推奨になり、セキュリティ上の理由からマクロ PROP_ENTRY_TYPE と PROP_ENTRY_TYPE_EX に置き換えられました。

### <a name="atlmfc-shared-classes"></a>ATL/MFC 共有クラス

- CRT に依存することなく ATL をビルドすることはできません。 以前のバージョンの Visual Studio では、`#define ATL_MIN_CRT` を使用して、ATL プロジェクトの CRT への依存を最小限にすることができます。 Visual Studio 2008 では、ATL_MIN_CRT が定義されているかどうかにかかわらず、すべての ATL プロジェクトの CRT への依存は最小限です。

- ATL サーバーのコードベースは、CodePlex の共有ソース プロジェクトとしてリリースされており、Visual Studio の一部としてはインストールされません。 atlenc.h のクラスのデータ エンコードとデコード、および atlutil.h と atlpath のユーティリティ関数とクラスは残され、ATL ライブラリの一部になりました。 ATL サーバーに関連する一部のファイルは、Visual Studio に含まれなくなりました。

- 一部の関数は DLL に含まれなくなりました。 これらの関数はインポート ライブラリに含まれています。 これは、関数を静的に使用するコードには影響がありません。 これらの関数を動的に使用するコードにのみ影響があります。

### <a name="mfc"></a>MFC

- `CTime` クラス: `CTime` クラスは西暦 1900 年 1 月 1 日以降の日付を使用できるようになりました (以前は西暦 1970 年 1 月 1 日以降でした)。

- MFC ダイアログのコントロールのタブ オーダー: タブ オーダーに MFC ActiveX コントロールが挿入されている場合、MFC ダイアログに含まれる複数のコントロールは正しいタブ オーダーになりません。 今回の変更で、この問題は解決します。

   たとえば、ActiveX コントロールといくつかの編集コントロールがある MFC ダイアログ アプリケーションを作成します。 ActiveX コントロールを編集コントロールのタブ オーダーの中間に配置します。 アプリケーションを起動して、タブオーダーが ActiveX コントロールの後にある編集コントロールをクリックし、次に tab キーを押します。この変更を行う前に、タブオーダーの次の編集コントロールではなく、ActiveX コントロールの次の編集コントロールにフォーカスを移動します。

- `CFileDialog` クラス: `CFileDialog` クラスのカスタムテンプレートを Windows Vista に自動的に移植することはできません。 使用することはできますが、Windows Vista スタイルのダイアログの機能や外観を追加することはできません。

- `CWnd` クラスと `CFrameWnd` クラス: `CWnd::GetMenuBarInfo` メソッドは削除されました。

   `CFrameWnd::GetMenuBarInfo` メソッドは仮想メソッドではなくなりました。 詳細については、Windows SDK の **GetMenuBarInfo 関数**を参照してください。

- MFC ISAPI のサポート: MFC は、Internet Server Application Programming Interface (ISAPI) を使用したアプリケーションのビルドをサポートしなくなりました。 ISAPI アプリケーションをビルドするには、ISAPI 拡張機能を直接呼び出してください。

- 非推奨になった ANSI API: ANSI バージョンの一部の MFC メソッドは非推奨になりました。 今後のアプリケーションでは、これらのメソッドの Unicode バージョンを使用してください。 詳細については、「**Windows Vista コモン コントロールの作成要件**」を参照してください。

## <a name="visual-studio-2005-breaking-changes"></a>Visual Studio 2005 の重要な変更点

### <a name="crt"></a>CRT

- 多くの関数は非推奨になりました。 「**Deprecated CRT Functions**」(非推奨の CRT 関数) を参照してください。

- 多くの関数はパラメーターを検証し、パラメーターが無効な場合は実行を停止するようになりました。 無効なパラメーターを渡しているコードで、無効なパラメーターを無視するか単にエラー コードを返すだけの関数に依存しているコードの場合、この検証によってコードに障害を起こす可能性があります。 「**Parameter Validation**」(パラメーターの検証) を参照してください。

- ファイル記述子の値 -2 は、出力に `stdout` と `stderr` を使用できないことを示すために使用されるようになりました。たとえば、コンソール ウィンドウがない Windows アプリケーションで使用されます。 以前に使用されていた値は -1 でした。 詳細については、「[_fileno](../c-runtime-library/reference/fileno.md)」を参照してください

- シングルスレッドの CRT ライブラリ libc.lib と libcd.lib は削除されました。 マルチスレッドの CRT ライブラリを使用してください。 `/ML` コンパイラ フラグはサポートされなくなりました。 マルチスレッドのコードとシングルスレッドのコード間のパフォーマンスの違いが重要な問題になる場合に、一部の関数のロックなしバージョンが追加されました。

- pow のオーバーロードである double pow(int, int) は、標準への準拠を改善するために削除されました。

- %n 書式指定子は、安全性に欠ける性質があるので、どの printf ファミリの関数でも既定でサポートされなくなりました。 %n が指定された場合、既定の動作は無効なパラメーター ハンドラーを呼び出すことです。 %n のサポートを有効にするには、`_set_printf_count_output` を使用します (`_get_printf_count_output` も参照してください)。

- `sprintf` は、符号付きゼロの負の符号を出力するようになりました。

- 標準への準拠のために `swprintf` は変更され、size パラメーターが必須になりました。 size パラメーターを指定しない `swprintf` の形式は非推奨になりました。

- `_set_security_error_handler` は削除されました。 その関数の呼び出しは削除してください。既定のハンドラーの方がはるかに安全にセキュリティ エラーを処理できます。

- `time_t` は 64 ビット値です (_USE_32BIT_TIME_T が定義されていない場合)。

- `_spawn` 関数、`_wspawn` 関数は、C 標準の規定に従い、成功時には `errno` が変更されません。

- RTC は既定でワイド文字を使用するようになりました。

- 浮動小数点制御ワードのサポート関数は、`/CLR` または `/CLR:PURE` を指定してコンパイルしたアプリケーションの場合に非推奨になりました。 影響を受ける関数は `_clear87`、`_clearfp`、`_control87`、`_controlfp`、`_fpreset`、`_status87`、`_statusfp` です。 _CRT_MANAGED_FP_NO_DEPRECATE を定義して、非推奨の警告を無効にすることができます。ただし、マネージド コードでこれらの関数を使用することは予測不能でサポートされません。

- 一部の関数は定数ポインターを返すようになりました。 古い定数ではない動作は、_CONST_RETURN を定義して復元することができます。 影響を受ける関数は次のとおりです。

   - memchr、wmemchr

   - strchr、wcschr、_mbschr、_mbschr_l

   - strpbrk、wcspbrk、_mbspbrk、_mbspbrk_l

   - strrchr、wcsrchr、_mbsrchr、_mbsrchr_l

   - strstr、wcsstr、_mbsstr、_mbsstr_l

- Setargv.obj または Wsetargv.obj とリンクするときに、コマンド ラインのワイルドカード文字を二重引用符で囲んでワイルドカード文字の展開を抑制できなくなりました。 詳細については、「[ワイルドカード引数の展開](../c-language/expanding-wildcard-arguments.md)」を参照してください。

### <a name="standard-library-2005"></a>標準ライブラリ (2005)

- (\<exception> ヘッダーにある) 例外クラスは `std` 名前空間に移動されました。 以前のバージョンでは、このクラスはグローバル名前空間に含まれていました。 例外クラスが見つからないというエラーを解決するには、次の using ステートメントをコードに追加します。`using namespace std;`

- `valarray::resize()` を呼び出すと、`valarray` の内容は失われ、既定値で置き換えられます。 `resize()` メソッドは、ベクターのように動的に増加するのではなく、`valarray` を再初期化するためのものです。

- デバッグ反復子: デバッグ バージョンの C ランタイム ライブラリを使用してビルドし、反復子を正しく使用していないアプリケーションは、実行時にアサートが表示されるようになることがあります。 これらのアサートを無効にするには、_HAS_ITERATOR_DEBUGGING (Visual Studio 2010 以降は [_ITERATOR_DEBUG_LEVEL](../standard-library/iterator-debug-level.md) に置き換えられます) を 0 に定義する必要があります。 詳細については、「[Debug Iterator Support](../standard-library/debug-iterator-support.md)」(反復子のデバッグのサポート) を参照してください。

## <a name="visual-c-net-2003-breaking-changes"></a>Visual C++ .NET 2003 の互換性に影響する変更

### <a name="compiler"></a>コンパイラ

- 定義済みプリプロセッサ ディレクティブ (C2004) には閉じかっこが必須になりました。

- 明示的な特殊化では、プライマリ テンプレートからテンプレート パラメーターを検索できなくなりました ([コンパイラ エラー C2146](../error-messages/compiler-errors-1/compiler-error-c2146.md))。

- 保護されたメンバー (n) には、(n) がメンバーであるクラス (A) から継承されたクラス (B) のメンバー関数経由でアクセスする必要があります ([コンパイラ エラー C2247](../error-messages/compiler-errors-1/compiler-error-c2247.md))。

- コンパイラのアクセシビリティ チェックが改善され、アクセスできない基底クラスが検出されるようになりました ([コンパイラ エラー C2248](../error-messages/compiler-errors-1/compiler-error-c2248.md))。

- デストラクターまたはコピー コンストラクターにアクセスできない場合、例外をキャッチできません (C2316)。

- 関数に対するポインターの既定の引数は使用できなくなりました ([コンパイラ エラー C2383](../error-messages/compiler-errors-1/compiler-error-c2383.md))。

- 静的データ メンバーは派生クラスを使って初期化できません ([コンパイラ エラー C2477](../error-messages/compiler-errors-1/compiler-error-c2477.md))。

- **typedef** の初期化は標準で許可されておらず、コンパイラ エラーが生成されるようになりました ([コンパイラ エラー C2513](../error-messages/compiler-errors-2/compiler-error-c2513.md))。

- **bool** は適切な型になりました ([コンパイラ エラー C2632](../error-messages/compiler-errors-2/compiler-error-c2632.md))。

- オーバーロードされた演算子がある場合、UDC であいまいさが生じるようになりました ([C2666](../error-messages/compiler-errors-2/compiler-error-c2666.md))。

- 多くの式が Null ポインター定数と見なされるようになりました ([コンパイラ エラー C2668](../error-messages/compiler-errors-2/compiler-error-c2668.md))。

- 以前にコンパイラが暗示していた位置に template<> の指定が必須になりました ([コンパイラ エラー C2768](../error-messages/compiler-errors-2/compiler-error-c2768.md))。

- テンプレート クラスの特殊化で関数が既に明示的に特殊化されている場合、クラス外でのメンバー関数の明示的な特殊化は有効ではなくなりました ([コンパイラ エラー C2910](../error-messages/compiler-errors-2/compiler-error-c2910.md))。

- 浮動小数点の非型テンプレート パラメーターは使用できなくなりました ([コンパイラ エラー C2993](../error-messages/compiler-errors-2/compiler-error-c2993.md))。

- クラス テンプレートはテンプレート型引数として使用できなくなりました (C3206)。

- フレンド関数名は、含まれる名前空間に導入されなくなりました ([コンパイラ エラー C3767](../error-messages/compiler-errors-2/compiler-error-c3767.md))。

- コンパイラでは、マクロ内の余分なコンマが使用できなくなります (C4002)。

- 形式 () の初期化子で構築される POD 型のオブジェクトは既定初期化されます (C4345)。

- 依存する名前を型として扱う場合、typename は必須になりました ([コンパイラの警告 (レベル 1) C4346](../error-messages/compiler-warnings/compiler-warning-level-1-c4346.md))。

- 誤ってテンプレートの特殊化と見なされていた関数は、そのように見なされなくなりました (C4347)。

- 静的データ メンバーは派生クラスを使って初期化できません (C4356)。

- 戻り値の型で使用する前に、クラス テンプレートの特殊化を定義する必要がなくなりました ([コンパイラの警告 (レベル 3) C4686](../error-messages/compiler-warnings/compiler-warning-level-3-c4686.md))。

- コンパイラは到達不能なコードをレポートするようになりました (C4702)。

## <a name="see-also"></a>参照

[Visual Studio における Visual C++ の新機能](../overview/what-s-new-for-visual-cpp-in-visual-studio.md)
