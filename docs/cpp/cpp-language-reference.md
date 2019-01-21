---
title: C++ 言語リファレンス
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- language reference
- C++, language reference
- language reference, Visual C++
- Visual C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
ms.openlocfilehash: 4d184e70e6a7284d07e706ce8b8c247c96442750
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031266"
---
# <a name="c-language-reference"></a>C++ 言語リファレンス

このリファレンスでは、Microsoft Visual C++ に実装されている C++ プログラミング言語について説明します。 組織がに基づいて[ *The Annotated C Reference Manual* ](http://www.stroustrup.com/arm.html) Margaret Ellis と Bjarne Stroustrup と、ANSI/ISO C 国際規格 (ISO/IEC FDIS 14882)。 Microsoft 固有の C++ 言語機能の実装も含まれます。

最新の C++ プログラミングの概要については、次を参照してください。[C++ へようこそ](welcome-back-to-cpp-modern-cpp.md)に戻ってください。

キーワードまたは演算子をすばやく見つけるには、次の表を参照してください。

- [C++ のキーワード](../cpp/keywords-cpp.md)

- [C++ 演算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>このセクションの内容

[構文規則](../cpp/lexical-conventions.md)<br/>
C++ プログラムの基本的な構文の要素: トークン、コメント、演算子、キーワード、区切り記号、リテラル。 また、ファイルの変換、演算子の優先順位/結合規則。

[基本的な概念](../cpp/basic-concepts-cpp.md)<br/>
スコープ、リンケージ、プログラムの起動と終了、ストレージ クラス、および型。

[標準変換](../cpp/standard-conversions.md)<br/>
組み込み型 (基本型) 間の型変換。 また、ポインター、参照、およびメンバーへのポインター型の間の算術変換および変換。

[演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
C++ 言語の演算子。

[式](../cpp/expressions-cpp.md)<br/>
式の型とセマンティクス、演算子の参照トピック、キャスト演算子、実行時の型情報。

[ラムダ式](../cpp/lambda-expressions-in-cpp.md)<br/>
暗黙的に関数オブジェクト クラスを定義し、そのクラス型の関数オブジェクトを生成するプログラミング手法。

[ステートメント](../cpp/statements-cpp.md)<br/>
式、NULL、複合、選択、イテレーション、ジャンプ、および宣言ステートメント。

[宣言と定義](declarations-and-definitions-cpp.md)<br/>
ストレージ クラス指定子、関数定義、初期化、列挙型、**クラス**、**構造体**、および**共用体**宣言、および**typedef**宣言します。 また、**インライン**関数、 **const**キーワード、名前空間。

[クラス、構造、および共用体](../cpp/classes-and-structs-cpp.md)<br/>
クラス、構造体、および共用体の概要。 また、メンバー関数、特殊なメンバー関数では、データ メンバー、ビット フィールド、**この**ポインター、入れ子になったクラスです。

[派生クラス](../cpp/inheritance-cpp.md)<br/>
単一および複数の継承、**仮想**関数、複数の基底クラス**抽象**クラス、スコープ規則。 また、 **_ _super**と **_ _interface**キーワード。

[メンバー アクセス コントロール](../cpp/member-access-control-cpp.md)<br/>
クラス メンバーへのアクセス制御:**パブリック**、**プライベート**、および**保護**キーワード。 friend 関数および friend クラス。

[オーバー ロード](operator-overloading.md)<br/>
オーバー ロードされた演算子、演算子のオーバー ロードの規則。

[例外処理](../cpp/exception-handling-in-visual-cpp.md)<br/>
例外処理ステートメントの記述に使用される C++ 例外処理、構造化例外処理 (SEH)、キーワード。

[アサーションとユーザー指定のメッセージ](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error` ディレクティブ、 **static_assert** 、キーワード、`assert`マクロ。

[テンプレート](../cpp/templates-cpp.md)<br/>
テンプレートの仕様、関数テンプレート、クラス テンプレート、 **typename**キーワード、テンプレートとマクロ、テンプレートとスマート ポインター。

[イベント処理](../cpp/event-handling.md)<br/>
イベントとイベント ハンドラーの宣言。

[Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)<br/>
Microsoft C++ 固有の修飾子。 メモリをアドレス指定、呼び出し規則、 **naked**関数、拡張ストレージ クラス属性 (**_ _declspec**)、 **_ _w64**します。

[インライン アセンブラー](../assembler/inline/inline-assembler.md)<br/>
アセンブリ言語および C++ で使用して **_ _asm**ブロックします。

[コンパイラ COM サポート](../cpp/compiler-com-support.md)<br/>
COM 型をサポートするために使用する Microsoft 固有のクラスとグローバル関数への参照。

[Microsoft 拡張機能](../cpp/microsoft-extensions.md)<br/>
C++ の Microsoft 拡張機能。

[非標準動作](../cpp/nonstandard-behavior.md)<br/>
Visual C++ コンパイラの非標準動作に関する情報。

[C++ へようこそ](welcome-back-to-cpp-modern-cpp.md)<br/>
最新の C++ プログラミングの概要については、安全な正確で効率的なプログラムの記述のベスト プラクティスです。

## <a name="related-sections"></a>関連項目

[ランタイム プラットフォームのコンポーネントの拡張機能](../windows/component-extensions-for-runtime-platforms.md)<br/>
共通言語ランタイムを対象とするための Visual C++ の使用に関するリファレンス資料。

[C/C++ ビルドのリファレンス](../build/reference/c-cpp-building-reference.md)<br/>
コンパイラ オプション、リンカー オプション、およびその他のビルド ツール。

[C/C++ プリプロセッサ リファレンス](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
プラグマ、プリプロセッサ ディレクティブ、定義済みマクロ、およびプリプロセッサに関するリファレンス資料。

[Visual C++ ライブラリ](../standard-library/cpp-standard-library-reference.md)<br/>
Visual C++ のさまざまなライブラリの参照のスタート ページへのリンクの一覧。

## <a name="see-also"></a>関連項目

[C 言語リファレンス](../c-language/c-language-reference.md)
