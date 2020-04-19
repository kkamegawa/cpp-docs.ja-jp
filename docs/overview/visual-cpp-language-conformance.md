---
title: Microsoft C++ 言語の準拠表
ms.date: 10/31/2019
ms.technology: cpp-language
ms.assetid: 475da6e9-0d78-4b4e-bd23-f41c406c4efe
author: corob-msft
ms.author: corob
ms.openlocfilehash: e029752ebaae5debb33d8e4a3920c5572f4d923b
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302147"
---
# <a name="microsoft-c-language-conformance-table"></a>Microsoft C++ 言語の準拠表

Visual Studio での Microsoft C++ コンパイラ (MSVC) の標準への準拠は、進行中の作業です。 ここでは、Visual Studio のバージョン別に、Microsoft の ISO 標準の C++ 言語およびライブラリの準拠についてまとめます。 コンパイラと標準ライブラリの各機能の名前は、その機能を説明する ISO 標準の C++ 提案書にリンクしています (発行時に利用可能な場合)。 **サポート状況**列には、その機能が最初にサポートされた Visual Studio のバージョンが記載されています。

Visual Studio 2017 または Visual Studio 2019 の MSVC の準拠の強化について詳しくは、「[Visual Studio の C++ 準拠の強化](cpp-conformance-improvements.md)」をご覧ください。 その他の変更の一覧については、「[Visual Studio の Visual C++ の新機能](what-s-new-for-visual-cpp-in-visual-studio.md)」をご覧ください。 以前のバージョンにおける準拠の変更点については、[Visual C++ の変更履歴](../porting/visual-cpp-change-history-2003-2015.md)に関するページと「[Visual C++ 2003 ～ 2015 の新機能](../porting/visual-cpp-what-s-new-2003-through-2015.md)」をご覧ください。 C++ チームからの最新情報については、[C++ チームのブログ](https://devblogs.microsoft.com/cppblog/)を参照してください。

> [!NOTE]
> Visual Studio 2015、Visual Studio 2017、Visual Studio 2019 間で、バイナリの破壊的変更はありません。 詳細については、「[Visual Studio 2015、2017、2019 の間の C++ バイナリ互換性](../porting/binary-compat-2015-2017.md)」をご覧ください

## <a name="compiler-features"></a>コンパイラ機能

| | |
|----|---|
|__C++03/11 Core 言語機能__|__サポート状況__|
|&nbsp;&nbsp;その他すべて|VS 2015 <sup>[A](#note_A)</sup>|
|&nbsp;&nbsp;名前の 2 段階参照|VS 2017 15.7 <sup>[B](#note_B)</sup>|
|&nbsp;&nbsp;[N2634 式 SFINAE](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2008/n2634.html)|VS 2017 15.7|
|&nbsp;&nbsp;[N1653 C99 プリプロセッサ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2004/n1653.htm)|部分的 <sup>[C](#note_C)</sup>|
|__C++14 Core 言語機能__|__サポート状況__|
|&nbsp;&nbsp;[N3323 コンテキスト変換での不自然な言い回し](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3323.pdf)|VS 2013|
|&nbsp;&nbsp;[N3472 バイナリ リテラル](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3472.pdf)|VS 2015|
|&nbsp;&nbsp;[N3638 auto と decltype(auto) 戻り値型](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3638.html)|VS 2015|
|&nbsp;&nbsp;[N3648 init キャプチャ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3648.html)|VS 2015|
|&nbsp;&nbsp;[N3649 汎用ラムダ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3649.html)|VS 2015|
|&nbsp;&nbsp;[N3760 \[\[非推奨\]\] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3760.html)|VS 2015|
|&nbsp;&nbsp;[N3778 サイズ割り当て解除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3781 桁区切り文字](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3781.pdf)|VS 2015|
|&nbsp;&nbsp;[N3651 変数テンプレート](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3651.pdf)|VS 2015.2|
|&nbsp;&nbsp;[N3652 拡張された constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3652.html)|VS 2017 15.0|
|&nbsp;&nbsp;[N3653 集計用の既定のメンバー初期化子](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3653.html)|VS 2017 15.0|
|__C++17 Core 言語機能__|__サポート状況__|
|&nbsp;&nbsp;[N4086 トライグラフの削除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4086.html)|VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N3922 かっこ付き初期化リストを持つ auto の新しい規則](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3922.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4051 テンプレートのテンプレート パラメーターの typename](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4051.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4266 名前空間と列挙子の属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4266.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4267 u8 文字リテラル](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4267.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4230 入れ子になった名前空間の定義](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4230.html)|VS 2015.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N3928 簡潔な static_assert](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3928.pdf)|VS 2017 15.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0184R0 範囲ベースの for-loop (汎用)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0184r0.html)|VS 2017 15.0 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0188R1 \[\[fallthrough\]\] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0188r1.pdf)|VS 2017 15.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0001R1 register キーワードを削除する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0001r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0002R1 ブール型の operator++ を削除する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0002r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0018R3 値別に *this をキャプチャする](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0018r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0028R4 繰り返しのない属性名前空間を使用する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0028r4.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0061R1 \_\_has_include](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0061r1.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0138R2 整数の固定列挙型の direct-list-init](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0138r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0170R1 constexpr ラムダ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0170r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0189R1 \[\[nodiscard\]\] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0189r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0212R1 \[\[maybe_unused\]\] 属性](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0212r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0217R3 構造化バインド](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0217r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0292R2 constexpr if-statements](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0292r2.html)|VS 2017 15.3 <sup>[D](#note_D)</sup>|
|&nbsp;&nbsp;[P0305R1 初期化子のある選択ステートメント](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0305r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0245R1 Hexfloat リテラル](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0245r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4268 より多くの非型テンプレート引数の許可](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4268.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4295 フォールド式](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4295.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 dynamic-exception-specifications の削除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0012R1 noexcept を型システムに追加する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0012r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0035R4 オーバーアラインの動的メモリ割り当て](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0035r4.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0386R2 インライン変数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0386r2.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0522R0 テンプレートのパラメーターと互換性のある引数を照合する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0522r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0036R0 空の単項 fold をいくつか削除する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0036r0.pdf)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[N4261 限定変換の修正](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4261.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0017R1 集約の初期化 (拡張)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0017r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0091R3 クラス テンプレートのテンプレート引数の推論](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0091r3.html)<br/>&nbsp;&nbsp;[P0512R0 クラス テンプレートの引数の推論の問題](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0512r0.pdf)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0127R2 auto による非型テンプレート パラメーターの宣言](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0127r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0135R1 コピー省略の保証](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0135r1.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0136R1 コンストラクター継承の言葉の言い換え](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0136r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0137R1 std::launder](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0137r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0145R3 式の評価順序の調整](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0145r3.pdf)<br/>&nbsp;&nbsp;[P0400R0 関数の引数の評価順序](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0400r0.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0195R2 using-declarations のパック拡張](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0195r2.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0283R2 識別できない属性を無視する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0283r2.html)|VS 2015 <sup>[14](#note_14)</sup>|
|__C++17 Core 言語機能 (不具合報告)__|__サポート状況__|
|&nbsp;&nbsp;[P0702R1 初期化子リスト ctors のクラス テンプレート引数の推論の修正](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0702r1.html)|VS 2017 15.7 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0961R1 構造化バインディング カスタマイゼーション ポイントを見つけるルールの緩和](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0961r1.html)|VS 2019 16.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0969R0 アクセス可能なメンバーへの構造化バインディングの許可](http://open-std.org/JTC1/SC22/WG21/docs/papers/2018/p0969r0.pdf)|VS 2019 16.0 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0588R1 暗黙の lambda キャプチャの簡略化](http://wg21.link/p0588r1)|VS 2019 16.4 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P1771R1 コンストラクターの \[\[nodiscard\]\]](https://wg21.link/p1771r1)|VS 2019 16.4 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P1825R0 P0527R1 と P1155R3 (より暗黙的な移動) 用のマージされた言い回し](https://wg21.link/p1825r0)|VS 2019 16.4 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0929R2 抽象クラス型のチェック](https://wg21.link/P0929R2)|いいえ|
|&nbsp;&nbsp;[P0962R2 範囲 for ループのカスタマイゼーション ポイントを見つけるルールの緩和](https://wg21.link/p0962r1)|いいえ|
|&nbsp;&nbsp;[P0859R0 CWG 1581:constexpr メンバー関数を定義するタイミング](https://wg21.link/p0859r0)|いいえ|
|&nbsp;&nbsp;[P1009R2 new 式での配列サイズの推論](https://wg21.link/P1009R2)|いいえ|
|&nbsp;&nbsp;[P1286R2 CWG DR1778 に対する反対](https://wg21.link/P1286R2)|いいえ|
|__C++20 Core 言語機能__|__サポート状況__|
|&nbsp;&nbsp;[P0704R1 メンバーへの const lvalue ref-qualified ポインターの修正](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0704r1.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1041R4 char16_t/char32_t 文字列リテラルを UTF-16/32 にする](https://wg21.link/P1041R4)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1330R0 constexpr 内での共用体のアクティブなメンバーの変更](https://wg21.link/P1330R0)|VS 2017 15.0 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0972R0 \<chrono> zero()、min()、max() の noexcept](https://wg21.link/P0972R0)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0515R3 3 方向 (宇宙船) 比較演算子 <=>](https://wg21.link/P0515R3)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0941R2 機能テストのマクロ](https://wg21.link/P0941R2)|VS 2019 16.0 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1008R1 ユーザー宣言コンストラクターによる集計の禁止](https://wg21.link/P1008R1)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0329R4 指定の初期化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0329r4.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0846R0 ADL と表示されない関数テンプレート](https://wg21.link/P0846R0)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0409R2 ラムダ キャプチャ \[=, this\] の許可](http://open-std.org/JTC1/SC22/WG21/docs/papers/2017/p0409r2.html)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0428R2 汎用ラムダの使い慣れたテンプレート構文](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0428r2.pdf)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0624R2 既定のコンストラクト可能かつ割り当て可能なステートレス ラムダ](https://wg21.link/P0624R2)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0780R2 ラムダ init-capture でのパック展開の許可](https://wg21.link/P0780R2)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0806R2 \[=\] を介した this の暗黙的キャプチャの非推奨化](https://wg21.link/P0806R2)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1120R0 <=> およびその他の比較演算子に対する整合性の改善](https://wg21.link/P1120R0)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1185R2 \<=\> != ==](https://wg21.link/P1185R2)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0734R0 概念](https://wg21.link/P0734R0)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0857R0 制約の機能のギャップの修正](https://wg21.link/P0857R0)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1084R2 現在の戻り値の型の要件は不十分である](https://wg21.link/P1084R2)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0892R2 条件付き explicit](https://wg21.link/P0892R2)|VS 2019 16.4 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1091R3 構造化バインディングを拡張してより変数宣言に近づける](https://wg21.link/P1091R3)|VS 2019 16.4 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1099R5 using enum](https://wg21.link/P1099R5)|VS 2019 16.4 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1186R3 \<=> を実際に使用するタイミング](https://wg21.link/P1186R3)|VS 2019 16.4 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1630R1 宇宙船のチューンアップが必要](https://wg21.link/P1630R1)|VS 2019 16.4 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0641R2 規定化コピー コンストラクターでの const の不一致](https://wg21.link/P0641R2)|部分的|
|&nbsp;&nbsp;[P0306R4 コンマ省略とコンマ削除のための \_\_VA_OPT\_\_ の追加](https://wg21.link/P0306R4)|いいえ|
|&nbsp;&nbsp;[P0315R4 未評価のコンテキストでのラムダの許可](https://wg21.link/P0315R4)|いいえ|
|&nbsp;&nbsp;[P0479R5 \[\[likely\]\] および \[\[unlikely\]\] 属性](https://wg21.link/P0479R5)|いいえ|
|&nbsp;&nbsp;[P0542R5 constract](https://wg21.link/P0542R5)|いいえ|
|&nbsp;&nbsp;[P0614R1 初期化を使う範囲ベースの for-loop](https://wg21.link/P0614R1)|いいえ|
|&nbsp;&nbsp;[P0634R3 不要な typename](https://wg21.link/P0634R3)|いいえ|
|&nbsp;&nbsp;[P0683R1 ビット フィールドの既定のメンバー初期化子](https://wg21.link/P0683R1)|いいえ|
|&nbsp;&nbsp;[P0692R1 特殊化におけるアクセス確認の緩和](https://wg21.link/P0692R1)|いいえ|
|&nbsp;&nbsp;[P0722R3 サイズ変更可能なクラスの効率的なサイズ指定された削除](https://wg21.link/P0722R3)|いいえ|
|&nbsp;&nbsp;[P0732R2 非型テンプレート パラメーターのクラス型](https://wg21.link/P0732R2)|いいえ|
|&nbsp;&nbsp;[P0840R2 \[\[no_unique_address\]\] 属性](https://wg21.link/P0840R2)|いいえ|
|&nbsp;&nbsp;[P0912R5 コルーチン](https://wg21.link/P0912R5)|いいえ|
|&nbsp;&nbsp;[P0960R3 かっこで囲まれた値のリストからの集計の初期化を許可する](https://wg21.link/P0960R3)|いいえ|
|&nbsp;&nbsp;[P1002R1 constexpr 関数での try-catch ブロック](https://wg21.link/P1002R1)|いいえ|
|&nbsp;&nbsp;[P1064R0 定数式での仮想関数呼び出しの許可](https://wg21.link/P1064R0)|いいえ|
|&nbsp;&nbsp;[P1073R3 即時関数](https://wg21.link/P1073R3)|いいえ|
|&nbsp;&nbsp;[P1094R2 入れ子になったインライン名前空間](https://wg21.link/P1094R2)|いいえ|
|&nbsp;&nbsp;[P1103R3 モジュール](https://wg21.link/P1103R3)|いいえ|
|&nbsp;&nbsp;[P1139R2 ISO 10646 に関連する言い回しの問題に対処する](https://wg21.link/P1139R2)|いいえ|
|&nbsp;&nbsp;[P1141R2 制約ありの宣言のもう 1 つの方法](https://wg21.link/P1141R2)|いいえ|
|&nbsp;&nbsp;[P1236R1 符号付き整数は 2 の補数になる](https://wg21.link/P1236R1)|いいえ|
|&nbsp;&nbsp;[P1289R1 contract の条件でのアクセスの制御](https://wg21.link/P1289R1)|いいえ|
|&nbsp;&nbsp;[P1323R2 contract の実行後の状態と戻り値の型の推論](https://wg21.link/P1323R2)|いいえ|
|&nbsp;&nbsp;[P1327R1 constant 式での dynamic_cast ポリモーフィック typeid の許可](https://wg21.link/P1327R1)|いいえ|
|&nbsp;&nbsp;[P1353R0 機能テスト マクロが見つからない](https://wg21.link/P1353R0)|いいえ|
|&nbsp;&nbsp;[P1381R1 構造化バインディングの参照キャプチャ](https://wg21.link/P1381R1)|いいえ|

## <a name="standard-library-features"></a>標準ライブラリの機能

| | |
|---|---|
|__C++20 標準ライブラリの機能__|__サポート状況__|
|&nbsp;&nbsp;[P0809R0 順序なしのコンテナーの比較](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0809r0.pdf)| VS 2010 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0858R0 Constexpr 反復子の要件](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0858r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0777R1 不要な Decay の回避](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0777r1.pdf)|VS 2017 15.7 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P1164R1 create_directory() を直感的にする](https://wg21.link/P1164R1)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0550R2 remove_cvref](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0550r2.pdf)|VS 2019 16.0 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0318R1 unwrap_reference、unwrap_ref_decay](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0318r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0457R2 basic_string/basic_string_view の starts_with()/ends_with()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0457r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0458R2 順序付きおよび順序なし連想コンテナーの contains()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0458r2.html)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0646R1 list/forward_list remove()/remove_if()/unique() Return size_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0646r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0769R2 shift_left()、shift_right()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0769r2.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0887R1 type_identity](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0887r1.pdf)|VS 2019 16.1 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0020R6 atomic\<float>、atomic\<double>、atomic\<long double>](https://wg21.link/p0020r6)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0463R1 エンディアン](https://wg21.link/p0463r1)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0482R6 char8_t:UTF-8 文字と文字列用の型](https://wg21.link/P0482R6)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0600R1 STL の \[\[nodiscard\]\]、パート 1](https://wg21.link/p0600r1)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0653R2 to_address()](https://wg21.link/p0653r2)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0754R2 \<version>](https://wg21.link/p0754r2)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0771R1 std::function の移動コンストラクター用の noexcept](https://wg21.link/P0771R1)|VS 2019 16.2 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0487R1 operator>>(basic_istream&, CharT*) の修正](https://wg21.link/P0487R1)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0616R0 \<<numeric> での move() の使用](https://wg21.link/p0616r0)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0758R1 is_nothrow_convertible](https://wg21.link/P0758R1)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0898R3 標準ライブラリの概念](https://wg21.link/P0898R3)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0919R3 順序なしコンテナーの異種ルックアップ](https://wg21.link/P0919R3)|VS 2019 16.3 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P1754R1 概念の名前を standard_case に変更する](https://wg21.link/P1754R1)|VS 2019 16.4 <sup>[20](#note_20)</sup>|
|&nbsp;&nbsp;[P0019R8 atomic_ref](https://wg21.link/P0019R8)|いいえ|
|&nbsp;&nbsp;[P0053R7 \<syncstream>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0053r7.pdf)<br/>&nbsp;&nbsp;[P0753R2 osyncstream マニピュレーター](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0753r2.pdf)|いいえ|
|&nbsp;&nbsp;[P0122R7 \<span>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0122r7.pdf)|いいえ|
|&nbsp;&nbsp;[P0202R3 \<algorithm> および exchange() に対する constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0202r3.html)|いいえ|
|&nbsp;&nbsp;[P0339R6 polymorphic_allocator<>](https://wg21.link/P0339R6)|いいえ|
|&nbsp;&nbsp;[P0340R3 SFINAE 対応 underlying_type](https://wg21.link/P0340R3)|いいえ|
|&nbsp;&nbsp;[P0355R7 \<chrono> カレンダーおよびタイム ゾーン](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2018/p0355r7.html)|いいえ|
|&nbsp;&nbsp;[P0356R5 bind_front()](https://wg21.link/P0356R5)|いいえ|
|&nbsp;&nbsp;[P0357R3 reference_wrapper での不完全な型のサポート](https://wg21.link/P0357R3)|いいえ|
|&nbsp;&nbsp;[P0415R1 \<complex> に対する constexpr (再度)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0415r1.html)|いいえ|
|&nbsp;&nbsp;[P0439R0 列挙型クラス memory_order](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0439r0.html)|いいえ|
|&nbsp;&nbsp;[P0475R1 区分コンストラクションのコピー省略の保証](https://wg21.link/P0475R1)|いいえ|
|&nbsp;&nbsp;[P0476R2 <bit> bit_cast](https://wg21.link/P0476R2)|いいえ|
|&nbsp;&nbsp;[P0528R3 パディングのビットを使ったアトミックな比較と交換](https://wg21.link/P0528R3)|いいえ|
|&nbsp;&nbsp;[P0556R3 <bit> ispow2()、ceil2()、floor2()、log2p1()](https://wg21.link/P0556R3)|いいえ|
|&nbsp;&nbsp;[P0591R4 uses-allocator コンストラクション用のユーティリティ関数](https://wg21.link/P0591R4)|いいえ|
|&nbsp;&nbsp;[P0608R3 バリアントのコンストラクター/割り当ての変換の強化](https://wg21.link/P0608R3)|いいえ|
|&nbsp;&nbsp;[P0619R4 C++20 の C++17 非推奨機能の削除](https://wg21.link/P0619R4)|いいえ|
|&nbsp;&nbsp;[P0653R2 to_address()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0653r2.html)|いいえ|
|&nbsp;&nbsp;[P0655R1 visit<R>()](https://wg21.link/P0655R1)|いいえ|
|&nbsp;&nbsp;[P0674R1 配列の make_shared()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0674r1.html)|いいえ|
|&nbsp;&nbsp;[P0718R2 atomic\<shared_ptr\<T>>、atomic\<weak_ptr\<T>>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0718r2.html)|いいえ|
|&nbsp;&nbsp;[P0738R2 istream_iterator のクリーンアップ](https://wg21.link/P0738R2)|いいえ|
|&nbsp;&nbsp;[P0767R1 is_pod の非推奨](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0767r1.html)|いいえ|
|&nbsp;&nbsp;[P0768R1 宇宙船比較演算子のライブラリ サポート\<=>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0768r1.pdf)|いいえ|
|&nbsp;&nbsp;[P0811R3 midpoint()、lerp()](https://wg21.link/P0811R3)|いいえ|
|&nbsp;&nbsp;[P0879R0 スワップ関数の constexpr](https://wg21.link/P0879R0)|いいえ|
|&nbsp;&nbsp;[P0896R4 \<ranges\>](https://wg21.link/P0896R4)|いいえ|
|&nbsp;&nbsp;[P0912R5 コルーチンに対するライブラリのサポート](https://wg21.link/P0912R5)|いいえ|
|&nbsp;&nbsp;[P0920R2 計算済みのハッシュ値のルックアップ](https://wg21.link/P0920R2)|いいえ|
|&nbsp;&nbsp;[P0935R0 明示化が不要な既定のコンストラクターをなくす](https://wg21.link/P0935R0)|いいえ|
|&nbsp;&nbsp;[P0966R1 string::reserve() は縮小しない](https://wg21.link/P0966R1)|いいえ|
|&nbsp;&nbsp;[P1001R2 execution::unseq](https://wg21.link/P1001R2)|いいえ|
|&nbsp;&nbsp;[P1006R1 pointer_traits<T*>::pointer_to() の constexpr](https://wg21.link/P1006R1)|いいえ|
|&nbsp;&nbsp;[P1007R3 assume_aligned()](https://wg21.link/P1007R3)|いいえ|
|&nbsp;&nbsp;[P1020R1 既定値初期化を使ったスマート ポインターの作成](https://wg21.link/P1020R1)|いいえ|
|&nbsp;&nbsp;[P1023R0 std::array 比較の constexpr](https://wg21.link/P1023R0)|いいえ|
|&nbsp;&nbsp;[P1032R1 その他の constexpr](https://wg21.link/P1032R1)|いいえ|
|&nbsp;&nbsp;[P1165R1 basic_string の operator+() における一貫して反映されるステートフル アロケーター](https://wg21.link/P1165R1)|いいえ|
|&nbsp;&nbsp;[P1209R0 erase_if()、erase()](https://wg21.link/P1209R0)|いいえ|
|&nbsp;&nbsp;[P1227R2 符合付き std::ssize()、符号なし span::size()](https://wg21.link/P1227R2)|いいえ|
|&nbsp;&nbsp;[P1285R0 型の特徴の完全性の要件の改善](https://wg21.link/P1285R0)|いいえ|
|&nbsp;&nbsp;[P1357R1 is_bounded_array、is_unbounded_array](https://wg21.link/P1357R1)|いいえ|
|__C++17 標準ライブラリの機能__|__サポート状況__|
|&nbsp;&nbsp;[LWG 2221 nullptr の書式付き出力演算子](https://cplusplus.github.io/LWG/issue2221)|VS 2019 16.1|
|&nbsp;&nbsp;[N3911 void_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3911.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4089 unique_ptr\<T[]> の安全な変換](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4089.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4169 invoke()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4169.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4190 auto_ptr、random_shuffle()、および古い \<functional> Stuff の削除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4190.htm)|VS 2015 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[N4258 noexcept クリーンアップ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4258.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4259 uncaught_exceptions()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4259.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4277 普通にコピー可能 reference_wrapper](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4277.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4279 map/unordered_map の insert_or_assign()/try_emplace()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4279.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4280 size()、empty()、data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n4280.pdf)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4366 unique_ptr 割り当ての正確な制約](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4366.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4387 ペアとタプルの改善](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4387.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4389 bool_constant](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4389.html)|VS 2015 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4508 shared_mutex (時間測定なし)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4508.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4510 vector/list/forward_list の不完全な型のサポート](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4510.html)|VS 2013 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<algorithm> sample()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#alg.random.sample)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<any>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#any)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<memory_resource>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#memory.resource.synop)<br/>&nbsp;&nbsp;[P0337R0 polymorphic_allocator 割り当ての削除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0337r0.html)|VS 2017 15.6|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<optional>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#optional)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<string_view>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#string.view)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Library Fundamentals: \<tuple> apply()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#tuple)|VS 2017 15.0|
|&nbsp;&nbsp;[N4562 Library Fundamentals: Boyer-Moore search()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/n4562.html#func.searchers.boyer_moore)<br/>&nbsp;&nbsp;[P0253R1 サーチャーの戻り値の型を修正する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0253r1.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0003R5 動的例外指定の削除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0003r5.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0004R1 使用されていない Iostreams エイリアスの削除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0004r1.html)|VS 2015.2 <sup>[rem](#note_rem)</sup>|
|&nbsp;&nbsp;[P0005R4 not_fn()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0005r4.html)<br/>&nbsp;&nbsp;[P0358R1 not_fn() の修正](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0358r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0006R0 型の特徴の変数テンプレート (is_same_v など)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0006r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0007R1 as_const()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0007r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0013R1 論理演算子の型の特徴 (conjunction など)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0013r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0024R2 並列アルゴリズム](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0024r2.html)<br/>&nbsp;&nbsp;[P0336R1 並列実行ポリシーの名前変更](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0336r1.pdf)<br/>&nbsp;&nbsp;[P0394R4 並列アルゴリズムの例外処理の terminate()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0394r4.html)<br/>&nbsp;&nbsp;[P0452R1 \<numeric> 並列アルゴリズムの統合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0452r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0025R1 clamp()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0025r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0030R1 hypot(x, y, z)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0030r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0031R0 \<array> (再度) と \<iterator> の constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0031r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0032R3 variant/any/optional の同種インターフェイス](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0032r3.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0033R1 enable_shared_from_this の言葉の言い換え](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0033r1.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0040R3 メモリ管理ツールの拡張](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0040r3.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0063R3 C11 標準ライブラリ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0063r3.html)|VS 2015 <sup>[C11](#note_C11)[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0067R5 基本文字列変換](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0067r5.html)|VS 2019 16.4 <sup>[charconv](#note_charconv)</sup>|
|&nbsp;&nbsp;[P0074R0 owner_less\<>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0074r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0077R2 is_callable、is_nothrow_callable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0077r2.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0083R3 マップと設定のスプライス](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0083r3.pdf)<br/>&nbsp;&nbsp;[P0508R0 insert_return_type の明確化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0508r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0084R2 戻り値の型の配置](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0084r2.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0088R3 \<variant>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0088r3.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0092R1 \<chrono> floor()、ceil()、round()、abs()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0092r1.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0152R1 atomic::is_always_lock_free](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0152r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0154R1 hardware_destructive_interference_size など](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0154r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0156R0 可変個引数 lock_guard](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0156r0.html)|VS 2015.2 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0156R2 可変個引数 lock\_guard の名前を scoped\_lock に変更](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0156r2.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0163R0 shared_ptr::weak_type](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2015/p0163r0.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0174R2 残留ライブラリ パーツの廃止](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0174r2.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0185R1 is_swappable、is_nothrow_swappable](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0185r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0209R2 make_from_tuple()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0209r2.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0218R1 \<filesystem>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0218r1.html)<br/>&nbsp;&nbsp;[P0219R1 ファイル システムの相対パス](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0219r1.html)<br/>&nbsp;&nbsp;[P0317R1 ファイル システムのディレクトリ エントリのキャッシュ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0317r1.html)<br/>&nbsp;&nbsp;[P0392R0 ファイル システム パスの string_view のサポート](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0392r0.pdf)<br/>&nbsp;&nbsp;[P0430R2 POSIX 以外のファイル システムのサポート](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0430r2.pdf)<br/>&nbsp;&nbsp;[P0492R2 ファイル システムに関する NB コメントの解決](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0492r2.html)|VS 2017 15.7 <sup>[E](#note_E)</sup>|
|&nbsp;&nbsp;[P0220R1 ライブラリ基礎 V1](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0220r1.html)|VS 2017 15.6|
|&nbsp;&nbsp;[P0226R1 数学的特殊関数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0226r1.pdf)|VS 2017 15.7|
|&nbsp;&nbsp;[P0254R2 string_view と std::string の統合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0254r2.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0258R2 has_unique_object_representations](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0258r2.html)|VS 2017 15.3 <sup>[G](#note_G)</sup>|
|&nbsp;&nbsp;[P0272R1 Non-const basic_string::data()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0272r1.html)|VS 2015.3|
|&nbsp;&nbsp;[P0295R0 gcd()、lcm()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0295r0.pdf)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0298R3 std::byte](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0298r3.pdf)|VS 2017 15.3 <sup>[17](#note_17)、&nbsp;[byte](#note_byte)</sup>|
|&nbsp;&nbsp;[P0302R1 std::function のアロケーター サポートの削除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0302r1.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0307R2 Optional の同等以上 (再度)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0307r2.pdf)|VS 2017 15.0|
|&nbsp;&nbsp;[P0393R3 バリアントの同等以上](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0393r3.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0403R1 \<string_view> の UDL ("meow"sv など)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0403r1.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0414R2 shared_ptr\<T[]>, shared_ptr\<T[N]>](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0414r2.html)<br/>&nbsp;&nbsp;[P0497R0 配列の shared_ptr の修正](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0497r0.html)|VS 2017 15.5 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0418R2 アトミック compare_exchange memory_order 要件](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0418r2.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0426R1 char_traits の constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0426r1.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0433R2 標準ライブラリへの、クラス テンプレートのテンプレートの推論の統合](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0433r2.html)<br/>&nbsp;&nbsp;[P0739R0 標準ライブラリへのクラス テンプレート引数の推論の統合の強化](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0739r0.html)|VS 2017 15.7|
|&nbsp;&nbsp;[P0435R1 common_type の総点検](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0435r1.pdf)<br/>&nbsp;&nbsp;[P0548R1 common\_type と期間の調整](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0548r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0504R0 in_place_t/in_place_type_t\<T>/in_place_index_t\<I> 再考](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0504r0.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0505R0 \<chrono> の constexpr (再度)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0505r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0510R0 Nothing、Arrays、References、Incomplete Types のバリアントを拒否する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0510r0.html)|VS 2017 15.0|
|&nbsp;&nbsp;[P0513R0 ハッシュの汚染](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0513r0.pdf)<br/>&nbsp;&nbsp;[P0599R1 noexcept ハッシュ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0599r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0516R0 shared_future コピーを noexcept としてマークする](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0516r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0517R0 future_errc から future_error を構築する](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0517r0.html)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0521R0 shared_ptr::unique() の廃止](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2016/p0521r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0558R1 atomic\<T> 名前付き基底クラスの不一致の解消](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0558r1.pdf)|VS 2017 15.3 <sup>[14](#note_14)</sup>|
|&nbsp;&nbsp;[P0595R2 std::is_constant_evaluated()](https://wg21.link/P0595R2)|いいえ|
|&nbsp;&nbsp;[P0602R4 variant/optional での Copy/Move の細かな機能の反映](https://wg21.link/P0602R4)|VS 2017 15.3<sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0604R0 is\_callable/result\_of を invoke\_result、is\_invocable、is\_nothrow\_invocable に変更](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0604r0.html)|VS 2017 15.3 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0607R0 標準ライブラリのインライン変数](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0607r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0618R0 \<codecvt> を非推奨にする](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2017/p0618r0.html)|VS 2017 15.5 <sup>[17](#note_17)</sup>|
|&nbsp;&nbsp;[P0682R1 基本文字列変換の修正](https://wg21.link/P0682R1)|VS 2015 15.7 <sup>[17](#note_17)</sup>|
|__C++14 標準ライブラリの機能__|__サポート状況__|
|&nbsp;&nbsp;[N3462 SFINAE 対応 result_of](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3462.html)|VS 2015.2|
|&nbsp;&nbsp;[N3302 \<complex> の constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2011/n3302.html)|VS 2015|
|&nbsp;&nbsp;[N3469 \<chrono> の constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3469.html)|VS 2015|
|&nbsp;&nbsp;[N3470 \<array> の constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3470.html)|VS 2015|
|&nbsp;&nbsp;[N3471 \<initializer_list>、\<tuple>、\<utility> の constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3471.html)|VS 2015|
|&nbsp;&nbsp;[N3545 integral_constant::operator()()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3545.pdf)|VS 2015|
|&nbsp;&nbsp;[N3642 \<chrono>、\<string> の UDL (1729ms、"meow"s など)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3642.pdf)|VS 2015|
|&nbsp;&nbsp;[N3644 Null 前進反復子](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3644.pdf)|VS 2015|
|&nbsp;&nbsp;[N3654 quoted()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3654.html)|VS 2015|
|&nbsp;&nbsp;[N3657 異種連想ルックアップ](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3657.htm)|VS 2015|
|&nbsp;&nbsp;[N3658 integer_sequence](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3658.html)|VS 2015|
|&nbsp;&nbsp;[N3659 shared_mutex (時間計測あり)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3659.html)|VS 2015|
|&nbsp;&nbsp;[N3668 exchange()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3668.html)|VS 2015|
|&nbsp;&nbsp;[N3669 const のない constexpr メンバー関数の修正](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3669.pdf)|VS 2015|
|&nbsp;&nbsp;[N3670 get\<T>()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3670.html)|VS 2015|
|&nbsp;&nbsp;[N3671 デュアルレンジ equal()、is_permutation()、mismatch()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3671.html)|VS 2015|
|&nbsp;&nbsp;[N3778 サイズ割り当て解除](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3778.html)|VS 2015|
|&nbsp;&nbsp;[N3779 \<complex> の UDL (3.14i など)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3779.pdf)|VS 2015|
|&nbsp;&nbsp;[N3789 \<functional> の constexpr](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3789.htm)|VS 2015|
|&nbsp;&nbsp;[N3887 tuple_element_t](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3887.pdf)|VS 2015|
|&nbsp;&nbsp;[N3891 shared_mutex (時間指定あり) の名前を shared_timed_mutex に変更](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2014/n3891.htm)|VS 2015|
|&nbsp;&nbsp;[N3346 コンテナー要素の最小要件](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3346.pdf)|VS 2013|
|&nbsp;&nbsp;[N3421 透過的な演算子のファンクター (less\<> など)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2012/n3421.htm)|VS 2013|
|&nbsp;&nbsp;[N3655 \<type_traits> のエイリアス テンプレート (decay_t など)](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3655.pdf)|VS 2013|
|&nbsp;&nbsp;[N3656 make_unique()](http://www.open-std.org/jtc1/sc22/wg21/docs/papers/2013/n3656.htm)|VS 2013|

複数の提案書がまとめて記載されている箇所は、承認された 1 つ以上の改善または拡張機能と併せた標準機能を示しています。 これらの機能はまとめて実装されます。

### <a name="supported-values"></a>サポート状況の値

__いいえ__は、未実装という意味です。\
__部分的__ は、実装が部分的であるという意味です。 詳細については、「メモ」セクションを参照してください。\
__VS 2010__ は、Visual Studio 2010 でサポートされている機能を示します。\
__VS 2013__ は、Visual Studio 2013 でサポートされている機能を示します。\
__VS 2015__ は、Visual Studio 2015 (RTW) でサポートされている機能を示します。\
__VS 2015.2__ と __VS 2015.3__ はそれぞれ、Visual Studio 2015 更新プログラム 2 と Visual Studio 2015 更新プログラム 3 でサポートされている機能を示します。\
__VS 2017 15.0__ は、Visual Studio 2017 バージョン 15.0 (RTW) でサポートされている機能を示します。\
__VS 2017 15.3__ は、Visual Studio 2017 バージョン 15.3 でサポートされている機能を示します。\
__VS 2017 15.5__ は、Visual Studio 2017 バージョン 15.5 でサポートされている機能を示します。\
__VS 2017 15.7__ は、Visual Studio 2017 バージョン 15.7 でサポートされている機能を示します。\
__VS 2019 16.0__ は、Visual Studio 2019 バージョン 16.0 (RTW) でサポートされている機能を示します。\
__VS 2019 16.1__ は、Visual Studio 2019 バージョン 16.1 でサポートされている機能を示します。\
__VS 2019 16.2__ は、Visual Studio 2019 バージョン 16.2 でサポートされている機能を示します。\
__VS 2019 16.3__ は、Visual Studio 2019 バージョン 16.3 でサポートされている機能を示します。\
__VS 2019 16.4__ は、Visual Studio 2019 バージョン 16.4 でサポートされている機能を示します。

### <a name="notes"></a>メモ

<a name="note_A"></a>__A__[/std:c++14](../build/reference/std-specify-language-standard-version.md) モードには、動的例外指定は実装されておらず、`throw()` は引き続き `__declspec(nothrow)` のシノニムとして扱われています。 C++ 17 では、1 つの形跡を除き、動的例外指定が P0003R5 でほとんど削除されています。`throw()` は廃止され、`noexcept` のシノニムとして動作する必要があります。 [/std:c++17](../build/reference/std-specify-language-standard-version.md) モードの MSVC は、`throw()` に `noexcept` と同じ動作 (つまり、終了を使った強制) を与えることによって、標準に準拠するようになりました。

コンパイラ オプション [/Zc:noexceptTypes](../build/reference/zc-noexcepttypes.md) は、以前の `__declspec(nothrow)` の動作を要求します。 `throw()` は、C++20 で削除される可能性があります。 標準および実装へ、これらの変更に対応するコードを移行するのを支援するために、[/std:c++17](../build/reference/std-specify-language-standard-version.md) と [/permissive-](../build/reference/permissive-standards-conformance.md) に、例外の指定の問題の新しいコンパイラ警告が追加されました。

<a name="note_B"></a>__B__ Visual Studio 2017 バージョン 15.7 の [/permissive-](../build/reference/permissive-standards-conformance.md) モードでサポートされています。 詳細については、「[2 フェーズの名前参照のサポートを MSVC に導入](https://devblogs.microsoft.com/cppblog/two-phase-name-lookup-support-comes-to-msvc/)」を参照してください。

<a name="note_C"></a>__C__ Visual Studio 2017 では、C99 プリプロセッサ ルールはコンパイラで完全にサポートされていません。 プリプロセッサを徹底的に見直し、Visual Studio 2017 バージョン 15.8 で [/experimental:preprocessor](../build/reference/experimental-preprocessor.md) コンパイラ スイッチを使った変更内容の配布を開始しました。

<a name="note_D"></a>__D__[/std:c++14](../build/reference/std-specify-language-standard-version.md) で、非表示にできる警告 [C4984](../error-messages/compiler-warnings/compiler-warning-c4984.md) と共にサポートされています。

<a name="note_E"></a>__E__ これは、完全に新しい実装であり、以前の `std::experimental` バージョンとは対応していません。これは、symlink サポート、バグ修正、標準で要求される動作への変更で必要です。 現在、\<filesystem> を含めると、新しい `std::filesystem` と以前の `std::experimental::filesystem` が提供され、\<experimental/filesystem> を含めると、古い実験的な実装のみが提供されます。 この実験的な実装は、ライブラリの次の ABI の重大なリリースで削除されます。

<a name="note_G"></a>__G__ コンパイラ組み込みでサポートされています。

<a name="note_14"></a>__14__ これらの C++17/20 機能は、[/std:c++14](../build/reference/std-specify-language-standard-version.md) (既定) が指定されているときでも、常に有効です。 その理由は、 **/std** オプションを導入する前にこの機能が実装されたため、または条件付きの実装が不必要に複雑だったためです。

<a name="note_17"></a>__17__ これらの機能は [/std:c++17](../build/reference/std-specify-language-standard-version.md) (または [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) コンパイラ オプションにより保護されています。

<a name="note_20"></a>__20__ これらの機能は [/std:c++latest](../build/reference/std-specify-language-standard-version.md) コンパイラ オプションにより有効化されています。 C++20 の実装が完了すると、新しい **/std:c++20** コンパイラ オプションが追加され、ここでもこれらの機能が使用可能になります。

<a name="note_byte"></a>__byte__ `std::byte` は [/std:c++17](../build/reference/std-specify-language-standard-version.md) (または [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) により有効になっていますが、Windows SDK のヘッダーと競合することがあるため、細かいオプトアウト マクロがあります。 `_HAS_STD_BYTE` を `0` として定義することで無効にできます。

<a name="note_C11"></a>__C11__ ユニバーサル CRT では、C++17 で必要となる C11 標準ライブラリの部分を実装しました。C99 `strftime()` E/O 代替変換指定子、C11 `fopen()` 排他モード、C11 `aligned_alloc()` は除きます。 C11 は `aligned_alloc()` を、Microsoft の `free()` の実装と互換性のない方法で指定したため (つまり、その `free()` は高度にアライメントされた割り当てを処理できる必要があるため)、後者が実装される可能性はほとんどありません。

<a name="note_rem"></a>__rem__ 機能が [/std:c++17](../build/reference/std-specify-language-standard-version.md) (または [/std:c++latest](../build/reference/std-specify-language-standard-version.md)) コンパイラ オプションが指定されたときに削除されます。 次のマクロを使うことで、これらの機能を再び有効化し、新しい言語モードへの移行を容易にすることができます: `_HAS_AUTO_PTR_ETC`、`_HAS_FUNCTION_ALLOCATOR_SUPPORT`、`_HAS_OLD_IOSTREAMS_MEMBERS`、`_HAS_UNEXPECTED`。

<a name="note_charconv"></a>__charconv__ `from_chars()` と `to_chars()` は整数に対して使えます。 浮動小数点の `from_chars()` と浮動小数点の `to_chars()` のタイムラインは次のとおりです。
- VS 2017 15.7:整数の `from_chars()` と `to_chars()`。
- VS 2017 15.8:浮動小数点の `from_chars()`。
- VS 2017 15.9:浮動小数点の `to_chars()` により最短の 10 進数がオーバーロードされます。
- VS 2019 16.0:浮動小数点の `to_chars()` により最短の 16 進数と高精度の 16 進数がオーバーロードされます。
- VS 2019 16.2:浮動小数点の `to_chars()` により高精度の固定値と高精度の科学的表記がオーバーロードされます。
- VS 2019 16.4:浮動小数点の `to_chars()` により高精度の全般がオーバーロードされます。

<a name ="note_parallel"></a> __parallel__ C++17 の並列アルゴリズムのライブラリが完成しました。 完成したというのは、すべてのアルゴリズムがすべてのケースで並列化されるという意味ではありません。 最も重要なアルゴリズムが並列化されていて、アルゴリズムが並列化されていない場所でも実行ポリシーのシグネチャが提供されます。 実装の中央内部ヘッダー yvals_core.h には、次の "並列アルゴリズムのメモ" が含まれています。C++ ではシリアル アルゴリズムへの呼び出しとして並列アルゴリズムを実装することが許可されています。 この実装では、いくつかの一般的なアルゴリズムの呼び出しを並列化しますが、すべては行いません。

並列化されるアルゴリズムは以下のとおりです。

- `adjacent_difference`、`adjacent_find`、`all_of`、`any_of`、`count`、`count_if`、`equal`、`exclusive_scan`、`find`、`find_end`、`find_first_of`、`find_if`、`find_if_not`、`for_each`、`for_each_n`、`inclusive_scan`、`is_heap`、`is_heap_until`、`is_partitioned`、`is_sorted`、`is_sorted_until`、`mismatch`、`none_of`、`partition`、`reduce`、`remove`、`remove_if`、`replace`、`replace_if`、`search`、`search_n`、`set_difference`、`set_intersection`、`sort`、`stable_sort`、`transform`、`transform_exclusive_scan`、`transform_inclusive_scan`、`transform_reduce`

次のものは現在並列化されていません。

- ターゲット ハードウェア上で、並列化による顕著なパフォーマンス改善はありません。要素を単にコピーするか順序を変えるだけの、分岐のないすべてのアルゴリズムは、通常、メモリの帯域幅が制限されます。
  - `copy`, `copy_n`, `fill`, `fill_n`, `move`, `reverse`, `reverse_copy`, `rotate`, `rotate_copy`, `shift_left`, `shift_right`, `swap_ranges`
- ユーザーの並列処理の要件の、おそらく次のカテゴリで (あるいは上記のカテゴリでも) 混乱が生じる可能性があります。
  - `generate`、`generate_n`
- 実行不可能だと思われる有効な並列処理は以下のとおりです。
  - `partial_sort`、`partial_sort_copy`
- まだ評価はされていませんが、次の並列化は今後のリリースで実装される可能性があり、メリットがあると想定されています。
  - `copy_if`、`includes`、`inplace_merge`、`lexicographical_compare`、`max_element`、`merge`、`min_element`、`minmax_element`、`nth_element`、`partition_copy`、`remove_copy`、`remove_copy_if`、`replace_copy`、`replace_copy_if`、`set_symmetric_difference`、`set_union`、`stable_partition`、`unique`、`unique_copy`

## <a name="see-also"></a>関連項目

[C++ 言語リファレンス](../cpp/cpp-language-reference.md)\
[C++ 標準ライブラリ](../standard-library/cpp-standard-library-reference.md)\
[Visual Studio の C++ 準拠の強化](cpp-conformance-improvements.md)\
[Visual Studio の Visual C++ の新機能](what-s-new-for-visual-cpp-in-visual-studio.md)\
[Visual C++ 2003 から 2015 の変更履歴](../porting/visual-cpp-change-history-2003-2015.md)\
[2003 から 2015 の Visual C++ の新機能](../porting/visual-cpp-what-s-new-2003-through-2015.md)\
[C++ チーム ブログ](https://devblogs.microsoft.com/cppblog/)
