---
title: MASM オペレーターリファレンス
ms.date: 12/17/2019
helpviewer_keywords:
- MASM (Microsoft Macro Assembler), operators reference
- operators [MASM]
ms.assetid: c069cab7-d6b0-4f82-a6ce-0ca3fc7e6428
ms.openlocfilehash: c0059ab1b0204b79e040d18bd5aa88145775ebcd
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318762"
---
# <a name="masm-operators-reference"></a>MASM オペレーターリファレンス

## <a name="arithmetic"></a>算術

||||
|-|-|-|
|[* (乗算)](operator-multiply.md)|[+ (追加)](operator-add.md)|[-(減算または反転)](operator-subtract-2.md)|
|[.分野](operator-dot.md)|[/(除算)](operator-subtract-1.md)|[&#91;&#93;化](operator-brackets.md)|
|[MOD (剰余)](operator-mod.md)|||

## <a name="control-flow"></a>制御フロー

||||
|-|-|-|
|[\! (ランタイム論理 not)](operator-logical-not-masm-run-time.md)|[\!= (ランタイムが等しくない)](operator-not-equal-masm.md)|[&#124;&#124;(ランタイム論理 or)](operator-logical-or.md)|
|[& & (ランタイム論理 and)](operator-logical-and-masm-run-time.md)|[< (ランタイムよりも小さい)](operator-less-than-masm-run-time.md)|[\<= (ランタイムの値が少ないか等しい)](operator-less-or-equal-masm-run-time.md)|
|[= = (ランタイム equal)](operator-equal-masm-run-time.md)|[> (ランタイムより大きい)](operator-greater-than-masm-run-time.md)|[> = (実行時以上)](operator-greater-or-equal-masm-run-time.md)|
|[& (ランタイムビットごとの and)](operator-bitwise-and.md)|||
|[実行?(ランタイムのキャリーテスト)](operator-carry-q.md)|[超え?(ランタイムオーバーフローテスト)](operator-overflow-q.md)|[なし?(ランタイムパリティテスト)](operator-parity-q.md)|
|[シャープ?(ランタイム署名テスト)](operator-sign-q.md)|[回?(ランタイムゼロテスト)](operator-zero-q.md)||

## <a name="logical-and-shift"></a>論理 and シフト

||||
|-|-|-|
|[AND (ビットごとの and)](operator-and.md)|[NOT (ビットごとの not)](operator-not.md)|[または (ビットごとの or)](operator-or.md)|
|[SHL (左にシフトするビット)](operator-shl.md)|[SHR (ビットシフト右)](operator-shr.md)|[XOR (ビットごとの排他的 or)](operator-xor.md)|

## <a name="macro"></a>マクロ

||||
|-|-|-|
|[\! (文字リテラル)](operator-logical-not-masm.md)|[% (テキストとして扱う)](operator-percent.md)||
|[;;(コメントとして扱う)](operator-semicolons.md)|[&lt; &gt; (1 つのリテラルとして扱う)](operator-literal.md)|[& & (代替パラメーター値)](operator-logical-and-masm.md)|

## <a name="miscellaneous"></a>その他の指定

||||
|-|-|-|
|[' ' (文字列として扱う)](operator-single-quote.md)|["" (文字列として扱う)](operator-double-quote.md)||
|: (ローカルラベル定義)|:: (レジスタセグメントとオフセット)|:: (グローバルラベル定義)|
|[;(コメントとして扱う)](operator-semicolon.md)|[DUP (繰り返し宣言)](operator-dup.md)||

## <a name="record"></a>レコード

|||
|-|-|
|[MASK (レコードまたはフィールドのビットマスクを取得)](operator-mask.md)|[WIDTH (レコードまたはフィールドの幅を取得)](operator-width.md)|

## <a name="relational"></a>関係

||||
|-|-|-|
|[EQ (等しい)](operator-eq.md)|[GE (より大きいまたは等しい)](operator-ge.md)|[GT (より大きい)](operator-gt.md)|
|[LE (以下)](operator-le.md)|[LT (より小さい)](operator-lt.md)|[NE (等しくない)](operator-ne.md)|

## <a name="segment"></a>Segment

|||
|-|-|
|[: (セグメントオーバーライド)](operator-colon.md)|:: (レジスタセグメントとオフセット)|
|[IMAGEREL (画像の相対オフセット)](operator-imagerel.md)|[LROFFSET (ローダーによって解決されたオフセット)](operator-lroffset.md)|
|[オフセット (セグメントの相対オフセット)](operator-offset.md)|[SECTIONREL (セクション相対オフセット)](operator-sectionrel.md)|
|[SEG (セグメントの取得)](operator-seg.md)||

## <a name="type"></a>の型

||||
|-|-|-|
|[高 (16 ビット以上の上位8ビット)](operator-high.md)|[HIGH32 (64 ビットの上位32ビット)](operator-high32.md)|[HIGHWORD (最低32ビットの上位16ビット)](operator-highword.md)|
|[LENGTH (配列内の要素の数)](operator-length.md)|[の長さ (配列内の要素数)](operator-lengthof.md)|[低 (低8ビット)](operator-low.md)|
|[LOW32 (低32ビット)](operator-low32.md)|[LOWWORD (16 ビット下位)](operator-lowword.md)|[OPATTR (引数の型情報の取得)](operator-opattr.md)|
|[PTR (型としてのポインター)](operator-ptr.md)|[SHORT (マークの短いラベルの種類)](operator-short.md)|[サイズ (型または変数のサイズ)](operator-size.md)|
|[SIZEOF (型または変数のサイズ)](operator-sizeof.md)|[この (現在の場所)](operator-this.md)|[型 (式の型の取得)](operator-type.md)|
|[.型 (引数の型の情報を取得)](operator-dot-type.md)|||

## <a name="see-also"></a>関連項目

[Microsoft マクロアセンブラーリファレンス](microsoft-macro-assembler-reference.md)\
[MASM BNF 文法](masm-bnf-grammar.md)
