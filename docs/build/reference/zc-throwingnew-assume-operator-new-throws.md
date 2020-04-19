---
title: /Zc:throwingNew (演算子の新しいスロー)
ms.date: 03/01/2018
f1_keywords:
- throwingNew
- /Zc:throwingNew
helpviewer_keywords:
- -Zc compiler options (C++)
- throwingNew
- Assume operator new Throws
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 20ff0101-9677-4d83-8c7b-8ec9ca49f04f
ms.openlocfilehash: c8c7b4e7246cc3bb1b3a73cde4f6830eb7178dd2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315990"
---
# <a name="zcthrowingnew-assume-operator-new-throws"></a>/Zc:throwingNew (演算子の新しいスロー)

ときに、 **/Zc:throwingNew**オプションを指定すると、コンパイラでの呼び出しの最適化`operator new`戻り値の null ポインターのチェックをスキップします。 このオプションにより、すべての実装がリンクされていることを想定するコンパイラ`operator new`とカスタム アロケーターは、C++ 標準に準拠しているし、割り当てエラーをスローします。 Visual Studio で既定では、排他生成 null チェック (**/Zc:throwingNew-**) の実装をスローしないとリンクできるため、これら呼び出しに対する`operator new`ルーチンのカスタム アロケーターを記述またはnull ポインターが返されます。

## <a name="syntax"></a>構文

> **/Zc:throwingNew**[**-**]

## <a name="remarks"></a>Remarks

ISO c++ 98 以降、標準が指定される既定の[new 演算子](../../standard-library/new-operators.md#op_new)をスローします`std::bad_alloc`メモリの割り当てに失敗するとします。 バージョンの Visual Studio 6.0 までの Visual C では、割り当ての失敗時に null ポインターが返されます。 以降では、Visual Studio 2002、`operator new`標準に準拠しているし、エラーをスローします。 Visual Studio を古い形式の割り当てを使用するコードをサポートするには、リンク可能な実装を提供します`operator new`nothrownew.obj と失敗時に null ポインターを返すにします。 既定では、コンパイラでは、旧式のアロケーターはこれらのエラー発生時の即時のクラッシュの原因を防ぐために防御の null チェックも生成されます。 **/Zc:throwingNew**オプション、コンパイラはこれらの null チェックを除外する、メモリすべてリンクされていることを前提としてのアロケーターは、標準に準拠しています。 これは、明示的なスローしないには適用されません`operator new`オーバー ロードは、型の追加のパラメーターを使用して宣言されて`std::nothrow_t`いて、明示的な`noexcept`仕様。

コンパイラ生成をそのメモリを割り当てるコードをフリー ストアにオブジェクトを作成、概念的をクリックし、メモリを初期化するために、そのコンス トラクターを呼び出します。 MSVC コンパイラ通常判別できないかどうかは、このコードが非準拠、非スローのアロケーターにリンクが、ため、既定でも生成します、コンス トラクターを呼び出す前に null チェックします。 これにより、null ポインターをスローしない割り当てに失敗した場合、コンス トラクターの呼び出しで逆参照します。 ほとんどの場合、これらのチェックは必要ありませんので、既定`operator new`アロケーターが null ポインターを返す代わりにスローします。 チェックには、残念ながらの副作用もがあります。 コード サイズを膨張させるが、分岐予測子で、過負荷になる、および devirtualization または初期化されているオブジェクトから const の伝達などその他の便利なコンパイラの最適化を抑制します。 サポート コードにリンクするだけに存在して、チェック*nothrownew.obj と*か、カスタム非準拠`operator new`実装します。 非準拠を使用しない場合`operator new`を使用することをお勧めします。 **/Zc:throwingNew**コードを最適化します。

**/Zc:throwingNew**オプションは、既定で無効として影響はありません、 [/permissive -](permissive-standards-conformance.md)オプション。

リンク時コード生成 (LTCG) を使用してコンパイルする場合は指定する必要はありません **/Zc:throwingNew**します。 場合に、コンパイラが検出できる LTCG を使用して、コードがコンパイルされると、既定値は、準拠`operator new`実装が使用されます。 そうである場合、コンパイラは自動的に null チェックを残します。 リンカーの **/ThrowingNew**に通知するフラグ場合の実装`operator new`準拠します。 ソースをカスタム演算子の新しい実装でこのディレクティブを含めることによって、リンカーにこのフラグを指定できます。

```cpp
#pragma comment(linker, "/ThrowingNew")
```

Visual C++ の準拠に関する問題について詳しくは、「 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)」をご覧ください。

## <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Visual Studio 開発環境において、このコンパイラ オプションを設定する方法

1. プロジェクトの **[プロパティ ページ]** ダイアログ ボックスを開きます。 詳細については、次を参照してください。 [Visual Studio での設定の C++ コンパイラとビルド プロパティ](../working-with-project-properties.md)します。

1. **構成**ドロップダウン メニューで、**すべて構成**します。

1. 選択、**構成プロパティ** > **C/C++** > **コマンドライン**プロパティ ページ。

1. 変更、**追加オプション**含めるプロパティを **/Zc:throwingNew**または **/Zc:throwingNew-** 選び、 **OK**します。

## <a name="see-also"></a>関連項目

[MSVC コンパイラ オプション](compiler-options.md)<br/>
[MSVC コンパイラ コマンド ラインの構文](compiler-command-line-syntax.md)<br/>
[/Zc (準拠)](zc-conformance.md)<br/>
[noexcept (C++)](../../cpp/noexcept-cpp.md)<br/>
[例外の仕様 (スロー) (C++)](../../cpp/exception-specifications-throw-cpp.md)<br/>
[(例外) を終了します。](../../standard-library/exception-functions.md#terminate)<br/>
