---
title: /Zc (準拠)
ms.date: 03/06/2018
f1_keywords:
- /zc
helpviewer_keywords:
- /Zc compiler options [C++]
- -Zc compiler options [C++]
- Conformance compiler options
- Zc compiler options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: e24dd53f9c805f57ce974a81a4963434f1868095
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316211"
---
# <a name="zc-conformance"></a>/Zc (準拠)

使用することができます、 **/Zc**標準または Microsoft 固有コンパイラの動作を指定するコンパイラ オプション。

## <a name="syntax"></a>構文

> **/Zc:**_オプション_{、_オプション_}

## <a name="remarks"></a>Remarks

Visual Studio には、C または C++ 標準と互換性がない拡張機能が実装されているが、ときに使用できます、`/Zc`準拠オプションまたは Microsoft 固有の標準準拠の動作を指定します。 いくつかのオプションを既存のコードに大規模な重大な変更を防ぐために、既定値は Microsoft 固有の動作です。 それ以外の場合は、既定値は、セキュリティ、パフォーマンス、または互換性の強化に重大な変更のコストよりも優先される標準の動作では。 各準拠オプションの既定の設定は、新しいバージョンの Visual Studio に変わる可能性があります。 各準拠オプションの詳細については、特定のオプションのトピックを参照してください。 [/Permissive -](permissive-standards-conformance.md)コンパイラ オプションは、既定では、準拠設定に設定されていない準拠オプションを暗黙的に設定します。

これらは、`/Zc`コンパイラ オプション。

|オプション|動作|
|---|---|
|[alignedNew\[-\]](zc-alignednew.md)|C++ 17 オーバーア ラインされている動的割り当てを有効にする (既定での c++ 17)。|
|[自動\[-\]](zc-auto-deduce-variable-type.md)|新しい標準 C++ の解釈を強制`auto`(で既定)。|
|[__cplusplus\[-\]](zc-cplusplus.md)|有効にする、 **_ _cplusplus**マクロ、サポートされている標準のレポートを (既定ではオフ)。|
|[externConstexpr\[-\]](zc-externconstexpr.md)|外部リンケージを有効にする`constexpr`変数 (既定ではオフ)。|
|[forScope\[-\]](zc-forscope-force-conformance-in-for-loop-scope.md)|C++ の標準を適用する`for`スコープ規則 (で既定)。|
|[implicitNoexcept\[-\]](zc-implicitnoexcept-implicit-exception-specifiers.md)|有効にする暗黙的な`noexcept`で必要な関数 (で既定で)。|
|[inline\[-\]](zc-inline-remove-unreferenced-comdat.md)|COMDAT または内部リンケージのみを持つ場合、参照されていない関数またはデータの削除 (既定ではオフ)。|
|[noexceptTypes\[-\]](zc-noexcepttypes.md)|C++ 17 noexcept ルールを適用 (で既定では c++ 17 以降)。|
|[referenceBinding\[-\]](zc-referencebinding-enforce-reference-binding-rules.md)|非定数の左辺値参照にバインドできません、UDT の一時的な (既定ではオフ)。|
|[rvalueCast\[-\]](zc-rvaluecast-enforce-type-conversion-rules.md)|標準 C++ の明示的な型変換規則を適用する (既定ではオフ)。|
|[sizedDealloc\[-\]](zc-sizeddealloc-enable-global-sized-dealloc-functions.md)|C++ 14 グローバル サイズ割り当て解除機能を有効にする (で既定)。|
|[strictStrings\[-\]](zc-strictstrings-disable-string-literal-type-conversion.md)|文字列リテラルを無効にする`char*`または`wchar_t*`変換 (既定ではオフ)。|
|[三項\[-\]](zc-ternary.md)|オペランドの型で条件演算子ルールを適用する (既定ではオフ)。|
|[threadSafeInit\[-\]](zc-threadsafeinit-thread-safe-local-static-initialization.md)|スレッド セーフなローカルの静的な初期化を有効にする (で既定)。|
|[throwingNew\[-\]](zc-throwingnew-assume-operator-new-throws.md)|想定`operator new`エラーをスローします (既定ではオフ)。|
|[trigraphs\[-\]](zc-trigraphs-trigraphs-substitution.md)|トライグラフ (廃止、オフ既定) を有効にします。|
|[twoPhase-](zc-twophase.md)|非準拠のテンプレートの解析動作 (既定で準拠) を使用します。|
|[wchar_t\[-\]](zc-wchar-t-wchar-t-is-native-type.md)|`wchar_t` ネイティブ型、typedef ではありませんが (で既定)。|

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)
