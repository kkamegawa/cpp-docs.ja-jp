---
title: /openmp (OpenMP のサポートを有効にする)
ms.date: 04/15/2019
f1_keywords:
- /openmp
- VC.Project.VCCLCompilerTool.OpenMP
helpviewer_keywords:
- /openmp compiler option [C++]
- -openmp compiler option [C++]
ms.assetid: 9082b175-18d3-4378-86a7-c0eb95664e13
ms.openlocfilehash: caa06d89c590abd2b3a74a5a6b118d6ba4acd910
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320215"
---
# <a name="openmp-enable-openmp-support"></a>/openmp (OpenMP のサポートを有効にする)

コンパイラで処理する[ `#pragma omp` ](../../preprocessor/omp.md) OpenMP をサポートするためのディレクティブ。

## <a name="syntax"></a>構文

::: moniker range=">= vs-2019"

> **/openmp**\[**:**__experimental__]

::: moniker-end

::: moniker range="<= vs-2017"

> **/openmp**

::: moniker-end

## <a name="remarks"></a>Remarks

`#pragma omp` 指定するために使用[ディレクティブ](../../parallel/openmp/reference/openmp-directives.md)と[句](../../parallel/openmp/reference/openmp-clauses.md)します。 場合 **/openmp**コンパイラは、OpenMP 句とディレクティブは無視されます。 コンパイルで、指定されていません。 [OpenMP 関数](../../parallel/openmp/reference/openmp-functions.md)呼び出しがあっても、コンパイラによって処理される **/openmp**が指定されていません。

::: moniker range=">= vs-2019"

C++コンパイラが現在 OpenMP 2.0 標準をサポートしています。 ただし、Visual Studio 2019 は、SIMD 機能を提供するようになりました。 使用してコンパイルする SIMD を使用する、 **/openmp: 実験**オプション。 このオプションにより、両方の通常 OpenMP の機能、および追加 OpenMP SIMD いない機能を使用する場合、 **/openmp**スイッチします。

::: moniker-end

両方を使用してコンパイルされたアプリケーション **/openmp**と **/clr** 1 つのアプリケーション ドメインのプロセスでのみ実行できます。 複数のアプリケーション ドメインはサポートされていません。 つまり、モジュール コンス トラクター (`.cctor`) を使用して、プロセスをコンパイルするかどうか、検出を実行 **/openmp**、し、アプリが既定以外のランタイムに読み込まれる場合。 詳細については、次を参照してください。 [appdomain](../../cpp/appdomain.md)、 [/clr (共通言語ランタイムのコンパイル)](clr-common-language-runtime-compilation.md)、および[混在アセンブリの初期化](../../dotnet/initialization-of-mixed-assemblies.md)します。

両方を使用してコンパイルされたアプリをロードしようとした場合 **/openmp**と **/clr**を既定以外のアプリケーション ドメインに、 <xref:System.TypeInitializationException> 、デバッガーの外部例外がスローされます、`OpenMPWithMultipleAppdomainsException`例外デバッガーでがスローされます。

これらの例外は、次の状況でも発生します。

- 使用して、アプリケーションがコンパイルされている場合 **/clr**なく **/openmp**、プロセスが使用してコンパイルされたアプリに含まれる場合、既定以外のアプリケーション ドメインに読み込まれると **/openmp**.

- 渡す場合、 **/clr** 、ユーティリティへのアプリなど[regasm.exe](/dotnet/framework/tools/regasm-exe-assembly-registration-tool)、そのターゲット アセンブリを既定以外のアプリケーション ドメインに読み込まれます。

共通言語ランタイムのコード アクセス セキュリティは、OpenMP のリージョンで動作しません。 並列領域の外側 CLR コード アクセス セキュリティ属性を適用する場合、並行領域内有効にはありません。

Microsoft を記述することはお勧めします **/openmp**部分的に許可するアプリには、呼び出し元が信頼されています。 使用しない<xref:System.Security.AllowPartiallyTrustedCallersAttribute>、または任意の CLR コード アクセス セキュリティ属性。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. 展開、**構成プロパティ** > **C/C++** > **言語**プロパティ ページ。

1. 変更、 **OpenMP サポート**プロパティ。

### <a name="to-set-this-compiler-option-programmatically"></a>このコンパイラ オプションをコードから設定するには

- 以下を参照してください。<xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.OpenMP%2A>

## <a name="example"></a>例

次の例では、開始後に、スレッド プールを使用するとスレッド プールの起動時の効果の一部を示します。 X64、1 つのコアのデュアル プロセッサと仮定すると、スレッド プールは約 16 ミリ秒開始します。 その後、費用はもう少し発生のスレッド プール。

使用してコンパイルするときに **/openmp**、test2、2 番目の呼び出しで使用してコンパイルした場合より長い実行されない **/openmp-**、スレッド プールの起動時はありません。 100万回反復、 **/openmp**バージョンがよりも高速、 **/openmp-** test2 の 2 番目の呼び出しのバージョン。 25 のイテレーションで両方 **/openmp-** と **/openmp**クロック粒度よりも小さいバージョン登録します。

アプリケーションに 1 つだけのループがある場合 (コンピューターにオーバーヘッドの概算の調整) 15 ミリ秒未満で実行される **/openmp**適さない場合があります。 使用を検討することがあります高い場合は、 **/openmp**します。

```cpp
// cpp_compiler_options_openmp.cpp
#include <omp.h>
#include <stdio.h>
#include <stdlib.h>
#include <windows.h>

volatile DWORD dwStart;
volatile int global = 0;

double test2(int num_steps) {
   int i;
   global++;
   double x, pi, sum = 0.0, step;

   step = 1.0 / (double) num_steps;

   #pragma omp parallel for reduction(+:sum) private(x)
   for (i = 1; i <= num_steps; i++) {
      x = (i - 0.5) * step;
      sum = sum + 4.0 / (1.0 + x*x);
   }

   pi = step * sum;
   return pi;
}

int main(int argc, char* argv[]) {
   double   d;
   int n = 1000000;

   if (argc > 1)
      n = atoi(argv[1]);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);

   dwStart = GetTickCount();
   d = test2(n);
   printf_s("For %d steps, pi = %.15f, %d milliseconds\n", n, d, GetTickCount() - dwStart);
}
```

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md) \
[MSVC コンパイラ コマンドラインの構文](compiler-command-line-syntax.md) \
[MSVC の OpenMP](../../parallel/openmp/openmp-in-visual-cpp.md)
