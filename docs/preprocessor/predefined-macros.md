---
title: 定義済みマクロ
description: Microsoft C++コンパイラの定義済みプリプロセッサマクロについて説明します。
ms.custom: update_every_version
ms.date: 11/20/2019
f1_keywords:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- __AVX512BW__
- __AVX512CD__
- __AVX512DQ__
- __AVX512F__
- __AVX512VL__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
helpviewer_keywords:
- timestamps, preprocessor macro
- cl.exe compiler, version number
- version numbers, C/C++ compiler (cl.exe)
- macros, predefined C++
- preprocessor, macros
- predefined macros
- _ATL_VER macro
- __ATOM__ macro
- __AVX__ macro
- __AVX2__ macro
- __AVX512BW__ macro
- __AVX512CD__ macro
- __AVX512DQ__ macro
- __AVX512F__ macro
- __AVX512VL__ macro
- _CHAR_UNSIGNED macro
- __CLR_VER macro
- _CONTROL_FLOW_GUARD macro
- __COUNTER__ macro
- __cplusplus macro
- __cplusplus_cli macro
- __cplusplus_winrt macro
- _CPPRTTI macro
- _CPPUNWIND macro
- __DATE__ macro
- _DEBUG macro
- _DLL macro
- __FILE__ macro
- __FUNCDNAME__ macro
- __FUNCSIG__ macro
- __FUNCTION__ macro
- _INTEGRAL_MAX_BITS macro
- _ISO_VOLATILE macro
- _KERNEL_MODE macro
- __LINE__ macro
- _M_AMD64 macro
- _M_ARM macro
- _M_ARM_ARMV7VE macro
- _M_ARM_FP macro
- _M_ARM64 macro
- _M_CEE macro
- _M_CEE_PURE macro
- _M_CEE_SAFE macro
- _M_FP_EXCEPT macro
- _M_FP_FAST macro
- _M_FP_PRECISE macro
- _M_FP_STRICT macro
- _M_IX86 macro
- _M_IX86_FP macro
- _M_X64 macro
- _MANAGED macro
- _MFC_VER macro
- _MSC_BUILD macro
- _MSC_EXTENSIONS macro
- _MSC_FULL_VER macro
- _MSC_VER macro
- _MSVC_LANG macro
- __MSVC_RUNTIME_CHECKS macro
- _MT macro
- _NATIVE_WCHAR_T_DEFINED macro
- _NO_SIZED_DEALLOCATION macro
- _OPENMP macro
- _PREFAST_ macro
- _RESUMABLE_FUNCTIONS_SUPPORTED macro
- _RTC_CONVERSION_CHECKS_ENABLED macro
- __STDC__ macro
- __STDC_HOSTED__ macro
- __STDCPP_THREADS__ macro
- __TIME__ macro
- __TIMESTAMP__ macro
- __VA_ARGS__ macro
- _VC_NODEFAULTLIB macro
- _WCHAR_T_DEFINED macro
- _WIN32 macro
- _WIN64 macro
- _WINRT_DLL macro
- __func__ identifier
ms.assetid: 1cc5f70a-a225-469c-aed0-fe766238e23f
no-loc:
- _ATL_VER
- __ATOM__
- __AVX__
- __AVX2__
- __AVX512BW__
- __AVX512CD__
- __AVX512DQ__
- __AVX512F__
- __AVX512VL__
- _CHAR_UNSIGNED
- __CLR_VER
- _CONTROL_FLOW_GUARD
- __COUNTER__
- __cplusplus
- __cplusplus_cli
- __cplusplus_winrt
- _CPPRTTI
- _CPPUNWIND
- __DATE__
- _DEBUG
- _DLL
- __FILE__
- __FUNCDNAME__
- __FUNCSIG__
- __FUNCTION__
- _INTEGRAL_MAX_BITS
- _ISO_VOLATILE
- _KERNEL_MODE
- __LINE__
- _M_AMD64
- _M_ARM
- _M_ARM_ARMV7VE
- _M_ARM_FP
- _M_ARM64
- _M_CEE
- _M_CEE_PURE
- _M_CEE_SAFE
- _M_FP_EXCEPT
- _M_FP_FAST
- _M_FP_PRECISE
- _M_FP_STRICT
- _M_IX86
- _M_IX86_FP
- _M_X64
- _MANAGED
- _MFC_VER
- _MSC_BUILD
- _MSC_EXTENSIONS
- _MSC_FULL_VER
- _MSC_VER
- _MSVC_LANG
- __MSVC_RUNTIME_CHECKS
- _MT
- _NATIVE_WCHAR_T_DEFINED
- _NO_SIZED_DEALLOCATION
- _OPENMP
- _PREFAST_
- _RESUMABLE_FUNCTIONS_SUPPORTED
- _RTC_CONVERSION_CHECKS_ENABLED
- __STDC__
- __STDC_HOSTED__
- __STDCPP_THREADS__
- __TIME__
- __TIMESTAMP__
- __VA_ARGS__
- _VC_NODEFAULTLIB
- _WCHAR_T_DEFINED
- _WIN32
- _WIN64
- _WINRT_DLL
- __func__
ms.openlocfilehash: ff3945fa9476e090f26ce029c63b1813401082e0
ms.sourcegitcommit: f38f770bfda1c174d2b81fabda7c893b15bd83a1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/20/2020
ms.locfileid: "77473845"
---
# <a name="predefined-macros"></a>定義済みマクロ

Microsoft C/C++コンパイラ (MSVC) は、言語 (C またはC++)、コンパイルターゲット、および選択されたコンパイラオプションに応じて、特定のプリプロセッサマクロを事前します。

MSVC は、ANSI/ISO C99 標準および ISO C++ 14 および C++ 17 標準で必要とされる定義済みのプリプロセッサマクロをサポートしています。 実装では、いくつかの Microsoft 固有のプリプロセッサマクロもサポートされています。 一部のマクロは、特定のビルド環境またはコンパイラオプションに対してのみ定義されています。 メモしている場合を除き、マクロは、 **/d**コンパイラオプションの引数として指定されているかのように、翻訳単位全体を通じて定義されます。 定義されている場合、コンパイルの前にプリプロセッサによって、マクロが指定された値に拡張されます。 定義済みマクロは引数を取らず、再定義することはできません。

## <a name="standard-predefined-identifier"></a>標準の定義済み識別子

コンパイラは、ISO C99 および ISO C++ 11 によって指定された定義済みの識別子をサポートしています。

- 外側の関数の修飾されていないと非修飾の名前を、 **char**の関数ローカルの**静的な定数**配列として `__func__` します。

    ```cpp
    void example(){
        printf("%s\n", __func__);
    } // prints "example"
    ```

## <a name="standard-predefined-macros"></a>標準の定義済みマクロ

コンパイラは、ISO C99 および ISO C++ 17 標準によって指定されたこれらの定義済みマクロをサポートしています。

- 翻訳単位をとC++してコンパイルするときに整数リテラル値として定義さ `__cplusplus`。 それ以外の場合、定義されていません。

- 現在のソースファイルのコンパイル日を `__DATE__` します。 日付は、 *Mmm dd yyyy*という形式の定数長の文字列リテラルです。 月の名前*Mmm*は、C ランタイムライブラリ (CRT) の[asctime](../c-runtime-library/reference/asctime-wasctime.md)関数によって生成される月の省略名と同じです。 日付*dd*の最初の文字は、値が10未満の場合は空白になります。 このマクロは常に定義します。

- 現在のソースファイルの名前 `__FILE__` ます。 `__FILE__` 文字列リテラルに展開されます。 ファイルへの完全パスが表示されるようにするには、 [/fc (診断でソースコードファイルの完全パス)](../build/reference/fc-full-path-of-source-code-file-in-diagnostics.md)を使用します。 このマクロは常に定義します。

- 現在のソースファイルの整数行番号として定義された `__LINE__` ます。 `__LINE__` マクロの値は、`#line` ディレクティブを使用して変更できます。 このマクロは常に定義します。

- `__STDC__` C としてコンパイルされた場合にのみ1として定義され、 [/za](../build/reference/za-ze-disable-language-extensions.md)コンパイラオプションが指定されている場合はです。 それ以外の場合、定義されていません。

- 実装が、必要な標準ライブラリ全体をサポートするホストされた*実装*である場合、`__STDC_HOSTED__` は1として定義されます。 それ以外の場合は0として定義されます。

- プログラムが1つ以上の実行スレッドを持つことができ、としてC++コンパイルできる場合にのみ、1として定義さ `__STDCPP_THREADS__` ます。 それ以外の場合、定義されていません。

- 前処理された翻訳単位の変換時間を `__TIME__` します。 時刻は*hh: mm: ss*形式の文字列リテラルで、CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md)関数によって返される時刻と同じです。 このマクロは常に定義します。

## <a name="microsoft-specific-predefined-macros"></a>Microsoft 固有の定義済みマクロ

MSVC では、これらの追加の定義済みマクロがサポートされます。

- [/favor: ATOM](../build/reference/favor-optimize-for-architecture-specifics.md)コンパイラオプションが設定されており、コンパイラターゲットが x86 または x64 の場合、`__ATOM__` は1として定義されます。 それ以外の場合、定義されていません。

- [/arch: AVX](../build/reference/arch-x86.md)、 [/arch: AVX2](../build/reference/arch-x86.md) 、または[/arch: AVX512](../build/reference/arch-x86.md)コンパイラオプションが設定され、コンパイラターゲットが x86 または x64 の場合、`__AVX__` は1として定義されます。 それ以外の場合、定義されていません。

- [/arch: AVX2](../build/reference/arch-x86.md)または[/arch: AVX512](../build/reference/arch-x86.md)コンパイラオプションが設定されており、コンパイラターゲットが x86 または x64 の場合、`__AVX2__` は1として定義されます。 それ以外の場合、定義されていません。

- [/arch: AVX512](../build/reference/arch-x86.md)コンパイラオプションが設定されており、コンパイラターゲットが x86 または x64 の場合、`__AVX512BW__` は1として定義されます。 それ以外の場合、定義されていません。

- [/arch: AVX512](../build/reference/arch-x86.md)コンパイラオプションが設定されており、コンパイラターゲットが x86 または x64 の場合、`__AVX512CD__` は1として定義されます。 それ以外の場合、定義されていません。

- [/arch: AVX512](../build/reference/arch-x86.md)コンパイラオプションが設定されており、コンパイラターゲットが x86 または x64 の場合、`__AVX512DQ__` は1として定義されます。 それ以外の場合、定義されていません。

- [/arch: AVX512](../build/reference/arch-x86.md)コンパイラオプションが設定されており、コンパイラターゲットが x86 または x64 の場合、`__AVX512F__` は1として定義されます。 それ以外の場合、定義されていません。

- [/arch: AVX512](../build/reference/arch-x86.md)コンパイラオプションが設定されており、コンパイラターゲットが x86 または x64 の場合、`__AVX512VL__` は1として定義されます。 それ以外の場合、定義されていません。

- 既定の**char**型が符号なしの場合、`_CHAR_UNSIGNED` は1として定義されます。 この値が定義されているときに、 [/J (既定の char 型の unsigned)](../build/reference/j-default-char-type-is-unsigned.md)コンパイラ オプションを設定します。 それ以外の場合、定義されていません。

- `__CLR_VER`、アプリのコンパイルに使用される共通言語ランタイム (CLR) のバージョンを表す整数リテラルとして定義されます。 値は`Mmmbbbbb`、と`mm` `M` いう`bbbbb`形式でエンコードされます。ここで、はランタイムのメジャーバージョン、はランタイムのマイナーバージョン、はビルド番号です。 [/clr](../build/reference/clr-common-language-runtime-compilation.md)コンパイラオプションが設定されている場合、`__CLR_VER` が定義されます。 それ以外の場合、定義されていません。

    ```cpp
    // clr_ver.cpp
    // compile with: /clr
    using namespace System;
    int main() {
       Console::WriteLine(__CLR_VER);
    }
    ```

- [/ガード: cf (制御フローガードを有効にする)](../build/reference/guard-enable-control-flow-guard.md)コンパイラオプションが設定されている場合、`_CONTROL_FLOW_GUARD` は1として定義されます。 それ以外の場合、定義されていません。

- `__COUNTER__` は、0から始まる整数リテラルに展開されます。 たびに、ソース ファイルで使用が含まれているソース ファイルのヘッダーまたは 1 で、値が増加します。 プリコンパイル済みヘッダーを使用すると、`__COUNTER__` はその状態を記憶します。 このマクロは常に定義します。

  この例では、`__COUNTER__` を使用して、同じ型の3つの異なるオブジェクトに一意の識別子を割り当てます。 `exampleClass` コンストラクターは、パラメーターとして整数を受け取ります。 `main`では、アプリケーションは `__COUNTER__` を一意の識別子パラメーターとして使用して、`exampleClass`型の3つのオブジェクトを宣言します。

    ```cpp
    // macro__COUNTER__.cpp
    // Demonstration of __COUNTER__, assigns unique identifiers to
    // different objects of the same type.
    // Compile by using: cl /EHsc /W4 macro__COUNTER__.cpp
    #include <stdio.h>

    class exampleClass {
        int m_nID;
    public:
        // initialize object with a read-only unique ID
        exampleClass(int nID) : m_nID(nID) {}
        int GetID(void) { return m_nID; }
    };

    int main()
    {
        // __COUNTER__ is initially defined as 0
        exampleClass e1(__COUNTER__);

        // On the second reference, __COUNTER__ is now defined as 1
        exampleClass e2(__COUNTER__);

        // __COUNTER__ is now defined as 2
        exampleClass e3(__COUNTER__);

        printf("e1 ID: %i\n", e1.GetID());
        printf("e2 ID: %i\n", e2.GetID());
        printf("e3 ID: %i\n", e3.GetID());

        // Output
        // ------------------------------
        // e1 ID: 0
        // e2 ID: 1
        // e3 ID: 2

        return 0;
    }
    ```

- としてコンパイルされ、 [/clr](../build/reference/clr-common-language-runtime-compilation.md)コンパイラオプションがC++設定されている場合、`__cplusplus_cli` 整数リテラル値200406として定義されます。 それ以外の場合、定義されていません。 定義した場合、`__cplusplus_cli` は翻訳単位全体を通じて有効になります。

    ```cpp
    // cplusplus_cli.cpp
    // compile by using /clr
    #include "stdio.h"
    int main() {
       #ifdef __cplusplus_cli
          printf("%d\n", __cplusplus_cli);
       #else
          printf("not defined\n");
       #endif
    }
    ```

- としてC++コンパイルされ、 [/ZW (Windows ランタイムコンパイル)](../build/reference/zw-windows-runtime-compilation.md)コンパイラオプションが設定されている場合、`__cplusplus_winrt` 整数リテラル値201009として定義されます。 それ以外の場合、定義されていません。

- [/gr (実行時の型情報の有効化)](../build/reference/gr-enable-run-time-type-information.md)コンパイラオプションが設定されている場合、`_CPPRTTI` は1として定義されます。 それ以外の場合、定義されていません。

- 1つ以上の[/gx (例外処理の有効化)](../build/reference/gx-enable-exception-handling.md)、 [/Clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)、または[/EH (例外処理モデル)](../build/reference/eh-exception-handling-model.md)コンパイラオプションが設定されている場合、`_CPPUNWIND` は1として定義されます。 それ以外の場合、定義されていません。

- `_DEBUG` 1 として定義されている、 [/LDd](../build/reference/md-mt-ld-use-run-time-library.md)、[/MDd](../build/reference/md-mt-ld-use-run-time-library.md)、または [/MTd](../build/reference/md-mt-ld-use-run-time-library.md) コンパイラ オプションを設定します。 それ以外の場合、定義されていません。

- [/md](../build/reference/md-mt-ld-use-run-time-library.md)または[/Mdd](../build/reference/md-mt-ld-use-run-time-library.md) (マルチスレッド DLL) コンパイラオプションが設定されている場合、`_DLL` は1として定義されます。 それ以外の場合、定義されていません。

- `__FUNCDNAME__`、外側の関数の[装飾名](../build/reference/decorated-names.md)を格納する文字列リテラルとして定義されます。 マクロは、関数内でのみ定義されます。 [/Ep](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)または[/p](../build/reference/p-preprocess-to-a-file.md)コンパイラオプションを使用する場合、`__FUNCDNAME__` マクロは展開されません。

   この例では、`__FUNCDNAME__`、`__FUNCSIG__`、および `__FUNCTION__` マクロを使用して、関数の情報を表示します。

   [!code-cpp[NVC_Predefined_Macros_Examples#1](../preprocessor/codesnippet/CPP/predefined-macros_1.cpp)]

- `__FUNCSIG__`、外側の関数のシグネチャを格納する文字列リテラルとして定義されます。 マクロは、関数内でのみ定義されます。 [/Ep](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)または[/p](../build/reference/p-preprocess-to-a-file.md)コンパイラオプションを使用する場合、`__FUNCSIG__` マクロは展開されません。 64ビットターゲット用にコンパイルされた場合、呼び出し規約は既定で `__cdecl` ます。 使用状況の例は、次を参照してください、`__FUNCDNAME__`マクロ。

- `__FUNCTION__`、外側の関数の非装飾名を含む文字列リテラルとして定義されます。 マクロは、関数内でのみ定義されます。 [/Ep](../build/reference/ep-preprocess-to-stdout-without-hash-line-directives.md)または[/p](../build/reference/p-preprocess-to-a-file.md)コンパイラオプションを使用する場合、`__FUNCTION__` マクロは展開されません。 使用状況の例は、次を参照してください、`__FUNCDNAME__`マクロ。

- `_INTEGRAL_MAX_BITS` 整数リテラル値64として定義されます。これは、非ベクター整数型の最大サイズ (ビット単位) です。 このマクロは常に定義します。

   ```cpp
   // integral_max_bits.cpp
   #include <stdio.h>
   int main() {
      printf("%d\n", _INTEGRAL_MAX_BITS);
   }
   ```

- IntelliSense コンパイラの実行中に1として定義された `__INTELLISENSE__` Visual Studio IDE に渡されます。 それ以外の場合、定義されていません。 このマクロを使用して、IntelliSense コンパイラで認識されないコードを保護したり、ビルドと IntelliSense のコンパイラを切り替えるために使用したりできます。 詳細については、「 [IntelliSense のパフォーマンス低下のトラブルシューティングのヒント](https://devblogs.microsoft.com/cppblog/troubleshooting-tips-for-intellisense-slowness/)」を参照してください。

- [/volatile: iso](../build/reference/volatile-volatile-keyword-interpretation.md)コンパイラオプションが設定されている場合、`_ISO_VOLATILE` は1として定義されます。 それ以外の場合、定義されていません。

- [/kernel (カーネルモードバイナリの作成)](../build/reference/kernel-create-kernel-mode-binary.md)コンパイラオプションが設定されている場合、`_KERNEL_MODE` は1として定義されます。 それ以外の場合、定義されていません。

- `_M_AMD64` x64 プロセッサを対象とするコンパイルの整数リテラル値100として定義されます。 それ以外の場合、定義されていません。

- `_M_ARM` ARM プロセッサを対象とするコンパイルの整数リテラル値7として定義されます。 それ以外の場合、定義されていません。

- [ARMv7VE](../build/reference/arch-arm.md)コンパイラオプションが ARM プロセッサを対象とするコンパイルに対して設定されている場合、`_M_ARM_ARMV7VE` は1として定義されます。 それ以外の場合、定義されていません。

- `_M_ARM_FP` ARM プロセッサターゲットに設定されている[/arch](../build/reference/arch-arm.md)コンパイラオプションを示す整数リテラル値として定義されます。 それ以外の場合、定義されていません。

  - `/arch` ARM オプションが指定されていない場合は30-39 の範囲の値。 ARM の既定のアーキテクチャ (`VFPv3`) が設定されていることを示します。

  - `/arch:VFPv4` が設定されている場合は、40-49 の範囲の値。

  - 詳細については、[/arch (ARM)](../build/reference/arch-arm.md)を参照してください。

- 64ビット ARM プロセッサを対象とするコンパイルの場合は、1として定義さ `_M_ARM64` ます。 それ以外の場合、定義されていません。

- `_M_CEE` [/clr (共通言語ランタイムのコンパイル)](../build/reference/clr-common-language-runtime-compilation.md)コンパイラオプションが設定されている場合は、001として定義されます。 それ以外の場合、定義されていません。

- `_M_CEE_PURE` Visual Studio 2015 以降では非推奨とされます。 場合は 001 として定義されている、 [/clr:pure](../build/reference/clr-common-language-runtime-compilation.md)コンパイラ オプションを設定します。 それ以外の場合、定義されていません。

- `_M_CEE_SAFE` Visual Studio 2015 以降では非推奨とされます。 場合は 001 として定義されている、 [/clr:safe](../build/reference/clr-common-language-runtime-compilation.md)コンパイラ オプションを設定します。 それ以外の場合、定義されていません。

- [/fp: except](../build/reference/fp-specify-floating-point-behavior.md)または[/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)コンパイラオプションが設定されている場合、`_M_FP_EXCEPT` は1として定義されます。 それ以外の場合、定義されていません。

- [/fp: fast](../build/reference/fp-specify-floating-point-behavior.md)コンパイラオプションが設定されている場合、`_M_FP_FAST` は1として定義されます。 それ以外の場合、定義されていません。

- [/fp: 精密](../build/reference/fp-specify-floating-point-behavior.md)コンパイラオプションが設定されている場合、`_M_FP_PRECISE` は1として定義されます。 それ以外の場合、定義されていません。

- [/fp: strict](../build/reference/fp-specify-floating-point-behavior.md)コンパイラオプションが設定されている場合、`_M_FP_STRICT` は1として定義されます。 それ以外の場合、定義されていません。

- `_M_IX86`、x86 プロセッサを対象とするコンパイルの整数リテラル値600として定義されます。 このマクロは、x64、または ARM コンパイル ターゲット定義されていません。

- `_M_IX86_FP` 設定されている[/arch](../build/reference/arch-arm.md)コンパイラオプションまたは既定値を示す整数リテラル値として定義されます。 コンパイル ターゲットが x86 の場合このマクロが常に定義されているプロセッサ。 それ以外の場合、定義されていません。 定義されているときに、値には。

  - `/arch:IA32` コンパイラオプションが設定されている場合は0。

  - `/arch:SSE` コンパイラオプションが設定されている場合は1。

  - `/arch:SSE2`、`/arch:AVX`、`/arch:AVX2`、または `/arch:AVX512` コンパイラオプションが設定されている場合は2。 この値は、`/arch` コンパイラオプションが指定されていない場合の既定値です。 `/arch:AVX` が指定されている場合、マクロ `__AVX__` も定義されます。 `/arch:AVX2` が指定されている場合、`__AVX__` と `__AVX2__` の両方も定義されます。 `/arch:AVX512` が指定されている場合、`__AVX__`、`__AVX2__`、`__AVX512BW__`、`__AVX512CD__`、`__AVX512DQ__`、`__AVX512F__`、`__AVX512VL__` も定義されます。

  - 詳細については、「[/arch (x86)](../build/reference/arch-x86.md)」を参照してください。

- `_M_X64` x64 プロセッサを対象とするコンパイルの整数リテラル値100として定義されます。 それ以外の場合、定義されていません。

- [/clr](../build/reference/clr-common-language-runtime-compilation.md)コンパイラオプションが設定されている場合、`_MANAGED` は1として定義されます。 それ以外の場合、定義されていません。

- `_MSC_BUILD`、コンパイラのバージョン番号のリビジョン番号要素を含む整数リテラルとして定義されます。 リビジョン番号は、ピリオド区切りのバージョン番号の 4 番目の要素です。 たとえば、Microsoft C/C++コンパイラのバージョン番号が15.00.20706.01 ある場合の場合、`_MSC_BUILD` マクロは1と評価されます。 このマクロは常に定義します。

- 既定の[/ze (Enable Language extension)](../build/reference/za-ze-disable-language-extensions.md)コンパイラオプションが設定されている場合、`_MSC_EXTENSIONS` は1として定義されます。 それ以外の場合、定義されていません。

- コンパイラのバージョン番号のメジャー、マイナー、およびビルド番号要素をエンコードする整数リテラルとして定義された `_MSC_FULL_VER`。 メジャー番号はピリオド区切りのバージョン番号の最初の要素、マイナー番号が 2 番目の要素、およびビルド番号が 3 番目の要素。 たとえば、Microsoft C/C++コンパイラのバージョン番号が15.00.20706.01 ある場合の場合、`_MSC_FULL_VER` マクロは150020706と評価されます。 入力`cl /?`コンパイラのバージョン番号を表示するのには、コマンドラインでします。 このマクロは常に定義します。

- コンパイラのバージョン番号のメジャー要素とマイナー番号要素をエンコードする整数リテラルとして定義された `_MSC_VER`。 メジャー番号はピリオド区切りのバージョン番号の最初の要素と、マイナー番号は 2 番目の要素。 たとえば、Microsoft C/C++コンパイラのバージョン番号が17.00.51106.1 の場合、`_MSC_VER` マクロは1700と評価されます。 入力`cl /?`コンパイラのバージョン番号を表示するのには、コマンドラインでします。 このマクロは常に定義します。

   |Visual Studio のバージョン|`_MSC_VER`|
   |-|-|
   |Visual Studio 6.0|1200|
   |Visual Studio .NET 2002 (7.0)|1300|
   |Visual Studio .NET 2003 (7.1)|1310|
   |Visual Studio 2005 (8.0)|1400|
   |Visual Studio 2008 (9.0)|1500|
   |Visual Studio 2010 (10.0)|1600|
   |Visual Studio 2012 (11.0)|1700|
   |Visual Studio 2013 (12.0)|1800|
   |Visual Studio 2015 (14.0)|1900|
   |Visual Studio 2017 RTW (15.0)|1910|
   |Visual Studio 2017 バージョン 15.3|1911|
   |Visual Studio 2017 バージョン 15.5|1912|
   |Visual Studio 2017 バージョン 15.6|1913|
   |Visual Studio 2017 バージョン 15.7|1914|
   |Visual Studio 2017 バージョン 15.8|1915|
   |Visual Studio 2017 バージョン 15.9|1916|
   |Visual Studio 2019 RTW (16.0)|1920|
   |Visual Studio 2019 バージョン 16.1|1921|
   |Visual Studio 2019 バージョン 16.2|1922|
   |Visual Studio 2019 バージョン16.3|1923|
   |Visual Studio 2019 バージョン16.4|1924|
   |Visual Studio 2019 バージョン16.5|1925|
   |Visual Studio 2019 バージョン16.6|1926|

   特定のバージョンの Visual Studio またはその後に、コンパイラのリリースまたは更新プログラムをテストするには、`>=` 演算子を使用します。 条件付きディレクティブで使用して、その既知のバージョンとの `_MSC_VER` を比較することができます。 比較対象として相互に排他的な複数のバージョンがある場合は、バージョン番号の降順で比較します。 たとえば、このコードは Visual Studio 2017 以降でリリースされたコンパイラをチェックします。 次に、Visual Studio 2015 以降でリリースされたコンパイラがあるかどうかを確認します。 次に、Visual Studio 2015 より前にリリースされたすべてのコンパイラがあるかどうかを確認します。

   ```cpp
   #if _MSC_VER >= 1910
   // . . .
   #elif _MSC_VER >= 1900
   // . . .
   #else
   // . . .
   #endif
   ```

   詳細については、Microsoft C++チームブログの「 [Visual C++ Compiler Version](https://devblogs.microsoft.com/cppblog/visual-c-compiler-version/) 」を参照してください。

- `_MSVC_LANG`、コンパイラが対象とC++する言語標準を指定する整数リテラルとして定義されます。 C++ としてコンパイルされたコードでのみ設定されます。 マクロは、整数リテラル 201402 L を既定では、値とき、または、 [/std:c++14](../build/reference/std-specify-language-standard-version.md)コンパイラ オプションを指定します。 場合 201703 L にマクロが設定されて、 [/std:c++17](../build/reference/std-specify-language-standard-version.md)コンパイラ オプションを指定します。 高い、指定されていない値に設定されているときに、 [/std:c++latest](../build/reference/std-specify-language-standard-version.md)オプションを指定します。 それ以外の場合、マクロは定義されません。 `_MSVC_LANG` マクロと、 [(言語標準バージョンの指定)](../build/reference/std-specify-language-standard-version.md)コンパイラオプションは、Visual Studio 2015 Update 3 以降で使用できます。

- [/rtc](../build/reference/rtc-run-time-error-checks.md)コンパイラオプションのいずれかが設定されている場合、`__MSVC_RUNTIME_CHECKS` は1として定義されます。 それ以外の場合、定義されていません。

- プリプロセッサ準拠モード[/実験的: プリプロセッサ](../build/reference/experimental-preprocessor.md)コンパイラオプションが設定されている場合、`_MSVC_TRADITIONAL` は0として定義されます。 既定では1として定義されます。または、 [/実験的: プリ](../build/reference/experimental-preprocessor.md)プロセッサコンパイラオプションが設定されている場合は、従来のプリプロセッサが使用されていることを示します。 `_MSVC_TRADITIONAL` マクロと[/実験的: プリプロセッサ (プリプロセッサ準拠モードの有効化)](../build/reference/experimental-preprocessor.md)コンパイラオプションは、Visual Studio 2017 バージョン15.8 以降で使用できます。

   ```cpp
   #if defined(_MSVC_TRADITIONAL) && _MSVC_TRADITIONAL
   // Logic using the traditional preprocessor
   #else
   // Logic using cross-platform compatible preprocessor
   #endif
   ```

- [/md または/mdd](../build/reference/md-mt-ld-use-run-time-library.md) (マルチスレッド DLL) または[/Mt または/MTd](../build/reference/md-mt-ld-use-run-time-library.md) (マルチスレッド) が指定されている場合、`_MT` は1として定義されます。 それ以外の場合、定義されていません。

- [/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)コンパイラオプションが設定されている場合、`_NATIVE_WCHAR_T_DEFINED` は1として定義されます。 それ以外の場合、定義されていません。

- [/openmp (openmp 2.0 のサポートを有効にする)](../build/reference/openmp-enable-openmp-2-0-support.md)コンパイラオプションが設定されている場合、`_OPENMP` は整数リテラル200203として定義されます。 この値は、MSVC によって実装される OpenMP 仕様の日付を表します。 それ以外の場合、定義されていません。

   ```cpp
   // _OPENMP_dir.cpp
   // compile with: /openmp
   #include <stdio.h>
   int main() {
      printf("%d\n", _OPENMP);
   }
   ```

- [/analyze](../build/reference/analyze-code-analysis.md)コンパイラオプションが設定されている場合、`_PREFAST_` は1として定義されます。 それ以外の場合、定義されていません。

- `__TIMESTAMP__` は、現在のソースファイルが最後に変更された日時を含む文字列リテラルとして定義されます。これには、`Fri 19 Aug 13:32:58 2016`のように、CRT [asctime](../c-runtime-library/reference/asctime-wasctime.md)関数によって返される、省略形の定数長が含まれます。 このマクロは常に定義します。

- [/zl (既定のライブラリ名の省略)](../build/reference/zl-omit-default-library-name.md)コンパイラオプションが設定されている場合、`_VC_NODEFAULTLIB` は1と定義されます。 それ以外の場合、定義されていません。

- 既定の[/zc: wchar_t](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)コンパイラオプションが設定されている場合、`_WCHAR_T_DEFINED` は1として定義されます。 `_WCHAR_T_DEFINED` マクロは定義されていますが、`/Zc:wchar_t-` コンパイラオプションが設定されていて**wchar_t**がプロジェクトに含まれるシステムヘッダーファイルで定義されている場合は、値がありません。 それ以外の場合、定義されていません。

- コンパイルターゲットが 32-bit ARM、64-bit ARM、x86、または x64 の場合、`_WIN32` は1として定義されます。 それ以外の場合、定義されていません。

- コンパイルターゲットが64ビット ARM または x64 の場合、`_WIN64` は1として定義されます。 それ以外の場合、定義されていません。

- としてC++コンパイルされ、 [/ZW (Windows ランタイムコンパイル)](../build/reference/zw-windows-runtime-compilation.md)と[/ld または/LDd](../build/reference/md-mt-ld-use-run-time-library.md)コンパイラオプションの両方が設定されている場合、`_WINRT_DLL` は1として定義されます。 それ以外の場合、定義されていません。

ATL または MFC ライブラリのバージョンを識別するプリプロセッサマクロは、コンパイラによって事前に定義されていません。 ATL および MFC ライブラリヘッダーは、これらのバージョンマクロを内部で定義します。 必須のヘッダーが含まれる前に作成されたプリプロセッサディレクティブには定義されていません。

- \<atldef. h > で定義されている `_ATL_VER`、ATL のバージョン番号をエンコードする整数リテラルとしてます。

- \<afxver_ > で定義されている `_MFC_VER`、MFC のバージョン番号をエンコードする整数リテラルとして指定します。

## <a name="see-also"></a>関連項目

[マクロ (C/C++)](../preprocessor/macros-c-cpp.md)<br/>
[プリプロセッサ演算子](../preprocessor/preprocessor-operators.md)<br/>
[プリプロセッサディレクティブ](../preprocessor/preprocessor-directives.md)
