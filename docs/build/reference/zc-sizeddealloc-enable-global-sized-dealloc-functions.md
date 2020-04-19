---
title: '/Zc: sizeddealloc (グローバル サイズ割り当て解除関数の有効化)'
ms.date: 03/06/2018
f1_keywords:
- sizedDealloc
- /Zc:sizedDealloc
helpviewer_keywords:
- -Zc compiler options (C++)
- sizedDealloc
- Enable Global Sized Deallocation Functions
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 3a73ace0-4d36-420a-b699-0ca6fc0dd134
ms.openlocfilehash: dc381058c6a2ef84542be1d3cdd00c410aa51c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315483"
---
# <a name="zcsizeddealloc-enable-global-sized-deallocation-functions"></a>/Zc: sizeddealloc (グローバル サイズ割り当て解除関数の有効化)

**/Zc: sizeddealloc**コンパイラ オプションを優先的に呼び出すグローバル コンパイラに指示`operator delete`または`operator delete[]`を型の 2 番目のパラメーターを持つ関数`size_t`オブジェクトのサイズが使用可能な場合。 これらの関数を使用して、可能性があります、`size_t`デアロケーターのパフォーマンスを最適化するパラメーター。

## <a name="syntax"></a>構文

> **/Zc:sizedDealloc**[**-**]

## <a name="remarks"></a>Remarks

C++ 11 標準で静的メンバー関数を定義することがあります`operator delete`と`operator delete[]`秒かかる`size_t`パラメーター。 通常と組み合わせて使用されます[演算子 new](../../cpp/new-operator-cpp.md)より効率的なアロケーターとオブジェクトのデアロケーターを実装する関数。 ただし、c++ 11 では、グローバル スコープで割り当て解除関数の同等のセットは定義しませんでした。 C++ 11、グローバル割り当て解除関数の型の 2 番目のパラメーターを持つで`size_t`配置 delete 関数と見なされます。 必要があります明示的に呼び出すことがサイズの引数を渡すことによって。

標準の c++ 14 では、コンパイラの動作を変更します。 グローバル定義するときに`operator delete`と`operator delete[]`型の 2 番目のパラメーターを受け取る`size_t`メンバーのスコープのバージョンが呼び出されないと、オブジェクトのサイズが使用可能なときに、これらの関数を呼び出す、コンパイラが優先されます。 コンパイラでは、サイズ引数が暗黙的に渡します。 1 つの引数のバージョンには、コンパイラは、割り当てが解除されないオブジェクトのサイズを判断できない場合は呼び出されます。 それ以外の場合を呼び出す、deallocation 関数のバージョンを選択するため、通常のルールが引き続き適用されます。 スコープ解決演算子を付けることによって、グローバル関数への呼び出しを明示的に指定することがあります (`::`) の割り当て解除関数の呼び出しにします。

既定では、Visual Studio 2015 以降では、Visual C は、この c++ 14 標準動作を実装します。 設定してこの明示的に指定することがあります、 **/zc: sizeddealloc**コンパイラ オプション。 これは表します可能性がある重大な変更。 使用して、 **/Zc:sizedDealloc-** 、コードが型の 2 番目のパラメーターを使用する配置 delete 演算子を定義する際に、古い動作を保持するオプション`size_t`します。 既定の Visual Studio ライブラリの実装を型の 2 番目のパラメーターを持つグローバル割り当て解除関数の`size_t`1 つのパラメーターのバージョンを呼び出します。 コードがのみ 1 つのパラメーターのグローバルを指定する場合は、delete 演算子と演算子の delete、グローバル サイズ割り当て解除関数の既定のライブラリの実装は、グローバル関数を呼び出します。

**/Zc: sizeddealloc**コンパイラ オプションが既定でオンです。 [/Permissive -](permissive-standards-conformance.md)オプションには影響しません **/zc: sizeddealloc**します。

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **構成**ドロップダウン メニューで、**すべて構成**します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/zc: sizeddealloc**または **/Zc:sizedDealloc-** 選び、 **OK**します。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/Zc (準拠)](zc-conformance.md)<br/>
