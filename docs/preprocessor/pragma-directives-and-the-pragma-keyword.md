---
title: プラグマ ディレクティブと __pragma キーワード
ms.date: 08/29/2019
f1_keywords:
- '#pragma'
helpviewer_keywords:
- '#pragma directives, C/C++'
- __pragma keyword
- pragma directives, C/C++
- pragmas, C/C++
- preprocessor
- pragmas
- preprocessor, pragmas
- pragma directives (#pragma)
ms.assetid: 9867b438-ac64-4e10-973f-c3955209873f
ms.openlocfilehash: 6cfbcd325dc895719bad5dccc9c19bcda90cdaa0
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858075"
---
# <a name="pragma-directives-and-the-__pragma-keyword"></a>プラグマ ディレクティブと __pragma キーワード

プラグマディレクティブは、コンピューターまたはオペレーティングシステム固有のコンパイラ機能を指定します。 Microsoft コンパイラに固有の **__pragma**キーワードを使用すると、マクロ定義内でプラグマディレクティブをコーディングできます。

## <a name="syntax"></a>構文

> **#pragma** *トークン-文字列*\
> **__pragma (** *トークン文字列* **)**

## <a name="remarks"></a>Remarks

C および C++ の各実装は、そのホスト コンピューターまたはオペレーティング システムに固有の機能をいくつかサポートしています。 たとえば、一部のプログラムでは、メモリ内のデータの場所を正確に制御したり、特定の関数がパラメーターを受け取る方法を制御したりする必要があります。 **#Pragma**ディレクティブは、C とC++言語の全体的な互換性を維持しながら、各コンパイラがコンピューターおよびオペレーティングシステム固有の機能を提供する手段を提供します。

プラグマは、コンピューターまたはオペレーティングシステムによって定義によって固有であり、通常、コンパイラごとに異なります。 プラグマは、新しいプリプロセッサ機能を提供するために、またはコンパイラに実装定義情報を提供するために、条件付きディレクティブで使用できます。

*トークン文字列*は、特定のコンパイラ命令と引数 (存在する場合) を与える一連の文字です。 シャープ記号 ( **#** ) は、プラグマを含む行の最初の空白以外の文字である必要があります。 空白文字は、シャープ記号と "pragma" という単語を区切ることができます。 次の **#pragma**に、変換プログラムがプリプロセストークンとして解析できるテキストを記述します。 **#Pragma**する引数は、マクロの展開の対象となります。

コンパイラは、認識できないプラグマを検出してコンパイルを続行すると、警告を発行します。

Microsoft C および C++ コンパイラは、次のプラグマを認識します。

||||
|-|-|-|
|[alloc_text](../preprocessor/alloc-text.md)|[auto_inline](../preprocessor/auto-inline.md)|[bss_seg](../preprocessor/bss-seg.md)|
|[check_stack](../preprocessor/check-stack.md)|[code_seg](../preprocessor/code-seg.md)|[comment](../preprocessor/comment-c-cpp.md)|
|[component](../preprocessor/component.md)|[conform](../preprocessor/conform.md) <sup>1</sup>|[const_seg](../preprocessor/const-seg.md)|
|[data_seg](../preprocessor/data-seg.md)|[非推奨](../preprocessor/deprecated-c-cpp.md)|[detect_mismatch](../preprocessor/detect-mismatch.md)|
|[fenv_access](../preprocessor/fenv-access.md)|[float_control](../preprocessor/float-control.md)|[fp_contract](../preprocessor/fp-contract.md)|
|[function](../preprocessor/function-c-cpp.md)|[hdrstop](../preprocessor/hdrstop.md)|[include_alias](../preprocessor/include-alias.md)|
|[init_seg](../preprocessor/init-seg.md) <sup>1</sup>|[inline_depth](../preprocessor/inline-depth.md)|[inline_recursion](../preprocessor/inline-recursion.md)|
|[intrinsic](../preprocessor/intrinsic.md)|[loop](../preprocessor/loop.md) <sup>1</sup>|[make_public](../preprocessor/make-public.md)|
|[managed](../preprocessor/managed-unmanaged.md)|[message](../preprocessor/message.md)|[omp](../preprocessor/omp.md)|
|[once](../preprocessor/once.md)|[optimize](../preprocessor/optimize.md)|[pack](../preprocessor/pack.md)|
|[pointers_to_members](../preprocessor/pointers-to-members.md) <sup>1</sup>|[pop_macro](../preprocessor/pop-macro.md)|[push_macro](../preprocessor/push-macro.md)|
|[region、endregion](../preprocessor/region-endregion.md)|[runtime_checks](../preprocessor/runtime-checks.md)|[section](../preprocessor/section.md)|
|[setlocale](../preprocessor/setlocale.md)|[strict_gs_check](../preprocessor/strict-gs-check.md)|[unmanaged](../preprocessor/managed-unmanaged.md)|
|[vtordisp](../preprocessor/vtordisp.md) <sup>1</sup>|[warning](../preprocessor/warning.md)||

<sup>1</sup> C++コンパイラでのみサポートされます。

## <a name="pragmas-and-compiler-options"></a>プラグマとコンパイラオプション

一部のプラグマの機能はコンパイラ オプションのものと同じです。 ソース コード内のプラグマは、コンパイラ オプションで指定された動作をオーバーライドします。 たとえば、 [/Zp8](../build/reference/zp-struct-member-alignment.md)を指定した場合、次のコードの特定のセクションについて、このコンパイラ設定を[pack](../preprocessor/pack.md)でオーバーライドできます。

```cmd
cl /Zp8 some_file.cpp
```

```cpp
// some_file.cpp - packing is 8
// ...
#pragma pack(push, 1) - packing is now 1
// ...
#pragma pack(pop) - packing is 8 again
// ...
```

## <a name="the-__pragma-keyword"></a>__Pragma () キーワード

コンパイラは、 **#pragma**ディレクティブと同じ機能を持つ、Microsoft 固有の **__pragma**キーワードもサポートしています。 違いは、 **__pragma**キーワードはマクロ定義でインラインで使用できることです。 **#Pragma**ディレクティブはマクロ定義では使用できません。コンパイラは、ディレクティブのシャープ記号文字 (' # ') を文字列化[演算子 (#)](../preprocessor/stringizing-operator-hash.md)として解釈するためです。

次のコード例は、マクロで **__pragma**キーワードを使用する方法を示しています。 このコードは、「コンパイラ COM サポートのサンプル」の ACDUAL サンプルの mfcdual.h ヘッダーからの抜粋です。

```cpp
#define CATCH_ALL_DUAL \
CATCH(COleException, e) \
{ \
_hr = e->m_sc; \
} \
AND_CATCH_ALL(e) \
{ \
__pragma(warning(push)) \
__pragma(warning(disable:6246)) /*disable _ctlState prefast warning*/ \
AFX_MANAGE_STATE(pThis->m_pModuleState); \
__pragma(warning(pop)) \
_hr = DualHandleException(_riidSource, e); \
} \
END_CATCH_ALL \
return _hr; \
```

## <a name="see-also"></a>参照

[C/C++プリプロセッサ参照](../preprocessor/c-cpp-preprocessor-reference.md)\
[C プラグマ](../c-language/c-pragmas.md)\
[キーワード](../cpp/keywords-cpp.md)
