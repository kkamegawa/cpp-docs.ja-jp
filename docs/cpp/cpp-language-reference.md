---
title: C++ 言語リファレンス
ms.custom: index-page
ms.date: 12/10/2019
helpviewer_keywords:
- C++, language reference
ms.assetid: 4be9cacb-c862-4391-894a-3a118c9c93ce
ms.openlocfilehash: 8d828c1b151e37380c123003c245f6b83243f84a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301588"
---
# <a name="c-language-reference"></a>C++ 言語リファレンス

このリファレンスではC++ 、Microsoft C++コンパイラに実装されているプログラミング言語について説明します。 組織は、Margaret Ellis および Bjarne Stroustrup、および ANSI/ISO C++国際標準 (ISO/IEC fdis 14882) で、[*注釈付きC++リファレンスマニュアル*](http://www.stroustrup.com/arm.html)に基づいています。 C++ 言語機能の Microsoft 固有実装が含まれます。

最新の C++ プログラミングの概要については、次を参照してください。[C++ へようこそ](welcome-back-to-cpp-modern-cpp.md)に戻ってください。

キーワードまたは演算子をすばやく見つけるには、次の表を参照してください。

- [C++Keywords](../cpp/keywords-cpp.md)

- [C++ 演算子](../cpp/cpp-built-in-operators-precedence-and-associativity.md)

## <a name="in-this-section"></a>このセクションの内容

[構文規則](../cpp/lexical-conventions.md)<br/>
C++ プログラムの基本的な構文の要素: トークン、コメント、演算子、キーワード、区切り記号、リテラル。 また、ファイルの変換、演算子の優先順位/結合規則。

[基本的な概念](../cpp/basic-concepts-cpp.md)<br/>
スコープ、リンケージ、プログラムの起動と終了、ストレージ クラス、および型。

[組み込み型](fundamental-types-cpp.md)C++コンパイラとその値の範囲に組み込まれている基本型。

[標準変換](../cpp/standard-conversions.md)<br/>
組み込み型の間の型変換。 また、ポインター、参照、およびメンバーへのポインター型の間の算術変換および変換。

[宣言と定義](declarations-and-definitions-cpp.md)変数、型、および関数の宣言と定義

[演算子、優先順位、および結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
C++ 言語の演算子。

[式](../cpp/expressions-cpp.md)<br/>
式の型とセマンティクス、演算子の参照トピック、キャスト演算子、実行時の型情報。

[ラムダ式](../cpp/lambda-expressions-in-cpp.md)<br/>
暗黙的に関数オブジェクト クラスを定義し、そのクラス型の関数オブジェクトを生成するプログラミング手法。

[ステートメント](../cpp/statements-cpp.md)<br/>
式、NULL、複合、選択、イテレーション、ジャンプ、および宣言ステートメント。

[クラスと構造体](../cpp/classes-and-structs-cpp.md)<br/>
クラス、構造体、および共用体の概要。 また、メンバー関数、特殊なメンバー関数では、データ メンバー、ビット フィールド、**this**ポインター、入れ子になったクラスです。

[共用体](unions.md)<br/>
すべてのメンバーが同じメモリ位置を共有するユーザー定義型。

[派生クラス](../cpp/inheritance-cpp.md)<br/>
単一および複数の継承、**virtual**関数、複数の基底クラス**抽象**クラス、スコープ規則。 また、 **__super**キーワードと **__interface**キーワードもあります。

[メンバー-Access Control](../cpp/member-access-control-cpp.md)<br/>
クラス メンバーへのアクセス制御:**public**、**private**、および**protected**キーワード。 friend 関数および friend クラス。

[負荷](operator-overloading.md)<br/>
オーバーロードされた演算子、演算子のオーバーロードに関するルール。

[例外処理](../cpp/exception-handling-in-visual-cpp.md)<br/>
例外処理ステートメントの記述に使用される C++ 例外処理、構造化例外処理 (SEH)、キーワード。

[アサーションとユーザー指定のメッセージ](../cpp/assertion-and-user-supplied-messages-cpp.md)<br/>
`#error` ディレクティブ、 **static_assert**キーワード、`assert` マクロ。

[テンプレート](../cpp/templates-cpp.md)<br/>
テンプレートの仕様、関数テンプレート、クラステンプレート、 **typename**キーワード、テンプレートとマクロ、テンプレート、およびスマートポインター。

[イベント処理](../cpp/event-handling.md)<br/>
イベントとイベント ハンドラーの宣言。

[Microsoft 固有の修飾子](../cpp/microsoft-specific-modifiers.md)<br/>
Microsoft C++ 固有の修飾子。 メモリのアドレス指定、呼び出し規則、**生**の関数、拡張ストレージクラス属性 ( **__declspec**)、 **__w64**。

[インライン アセンブラー](../assembler/inline/inline-assembler.md)<br/>
__Asm ブロックでのC++アセンブリ言語との使用。

[コンパイラ COM サポート](../cpp/compiler-com-support.md)<br/>
COM 型をサポートするために使用する Microsoft 固有のクラスとグローバル関数への参照。

[Microsoft 拡張機能](../cpp/microsoft-extensions.md)<br/>
C++ の Microsoft 拡張機能。

[非標準動作](../cpp/nonstandard-behavior.md)<br/>
Microsoft C++コンパイラの非標準動作に関する情報。

[C++ へようこそ](welcome-back-to-cpp-modern-cpp.md)<br/>
安全で正確でC++効率的なプログラムを作成するための最新のプログラミング手法の概要を説明します。

## <a name="related-sections"></a>関連セクション

[ランタイム プラットフォームのコンポーネントの拡張機能](../extensions/component-extensions-for-runtime-platforms.md)<br/>
Microsoft C++コンパイラを使用して .net を対象とする方法に関するリファレンス資料。

[C/C++ ビルドのリファレンス](../build/reference/c-cpp-building-reference.md)<br/>
コンパイラ オプション、リンカー オプション、およびその他のビルド ツール。

[C/C++ プリプロセッサ リファレンス](../preprocessor/c-cpp-preprocessor-reference.md)<br/>
プラグマ、プリプロセッサ ディレクティブ、定義済みマクロ、およびプリプロセッサに関するリファレンス資料。

[Visual C++ ライブラリ](../standard-library/cpp-standard-library-reference.md)<br/>
さまざまな Microsoft C++ライブラリのリファレンススタートページへのリンクの一覧です。

## <a name="see-also"></a>関連項目

[C 言語リファレンス](../c-language/c-language-reference.md)
