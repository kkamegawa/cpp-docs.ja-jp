---
title: C++ の組み込み演算子、優先順位と結合規則
ms.date: 11/04/2016
helpviewer_keywords:
- operators (C++), hierarchy
- operator precedence
- precedence, operators
- operators (C++), associativity
- multiple operators [C++]
- associativity of operators [C++]
- operators [C++], precedence
- evaluation order
- hierarchy, operator
ms.assetid: 95c1f0ba-dad8-4034-b039-f79a904f112f
ms.openlocfilehash: 0b560913deb57393a8547f0831e0d987eed41ab7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392350"
---
# <a name="c-built-in-operators-precedence-and-associativity"></a>C++ の組み込み演算子、優先順位と結合規則

C++ 言語には、C のすべての演算子が含まれており、いくつかの新しい演算子が追加されています。 演算子により、1 つまたは複数のオペランドに対して実行される評価が決まります。

演算子*優先順位*を 1 つ以上の演算子を含む式での操作の順序を指定します。 演算子*結合規則*を優先順位が同じ複数の演算子を含む式でオペランドがグループかどうかは、左に 1 つまたはその右に 1 つを指定します。 次の表では、C++ の演算子の優先順位と結合規則を示しています (演算子は優先順位の高いものから低いものの順に並んでいます)。 優先順位番号が同じ演算子は、別の関係がかっこで明示的に適用されない限り、同じ優先順位になります。

### <a name="c-operator-precedence-and-associativity"></a>C++ 演算子の優先順位と結合規則

|演算子の説明|演算子|
|--------------------------|--------------|
|**グループのない結合規則が 1 の優先順位**|
|[スコープ解決](../cpp/scope-resolution-operator.md)|[::](../cpp/scope-resolution-operator.md)|
|**グループ 2 の優先順位、左右の結合規則から**|
|[メンバーの選択 (オブジェクトまたはポインター)](../cpp/member-access-operators-dot-and.md)|[.または ->](../cpp/member-access-operators-dot-and.md)|
|[配列の添字](../cpp/subscript-operator.md)|[&#91;&#93;](../cpp/subscript-operator.md)|
|[関数呼び出し](../cpp/function-call-operator-parens.md)|[()](../cpp/function-call-operator-parens.md)|
|[後置インクリメント](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[後置デクリメント](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/postfix-increment-and-decrement-operators-increment-and-decrement.md)|
|[型名](../cpp/typeid-operator.md)|[typeid](../cpp/typeid-operator.md)|
|[定数の型変換](../cpp/const-cast-operator.md)|[const_cast](../cpp/const-cast-operator.md)|
|[動的な型変換](../cpp/dynamic-cast-operator.md)|[dynamic_cast](../cpp/dynamic-cast-operator.md)|
|[再解釈型変換](../cpp/reinterpret-cast-operator.md)|[reinterpret_cast](../cpp/reinterpret-cast-operator.md)|
|[静的な型変換](../cpp/static-cast-operator.md)|[static_cast](../cpp/static-cast-operator.md)|
|**右左結合規則からのグループ 3 の優先順位**|
|[オブジェクトまたは型のサイズ](../cpp/sizeof-operator.md)|[sizeof](../cpp/sizeof-operator.md)|
|[前置インクリメント](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[++](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[前置デクリメント](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|[--](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)|
|[1 の補数](../cpp/one-s-complement-operator-tilde.md)|[~](../cpp/one-s-complement-operator-tilde.md)|
|[論理 not](../cpp/logical-negation-operator-exclpt.md)|[\!](../cpp/logical-negation-operator-exclpt.md)|
|[単項マイナス符号](../cpp/unary-plus-and-negation-operators-plus-and.md)|[-](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[単項プラス](../cpp/unary-plus-and-negation-operators-plus-and.md)|[+](../cpp/unary-plus-and-negation-operators-plus-and.md)|
|[アドレスの](../cpp/address-of-operator-amp.md)|[&amp;](../cpp/address-of-operator-amp.md)|
|[間接参照](../cpp/indirection-operator-star.md)|[&#42;](../cpp/indirection-operator-star.md)|
|[オブジェクトを作成します。](../cpp/new-operator-cpp.md)|[new](../cpp/new-operator-cpp.md)|
|[オブジェクトを破棄します。](../cpp/delete-operator-cpp.md)|[delete](../cpp/delete-operator-cpp.md)|
|[キャスト](../cpp/cast-operator-parens.md)|[()](../cpp/cast-operator-parens.md)|
|**グループ 4 の優先順位、左右の結合規則から**|
|[メンバーへのポインター-(オブジェクトまたはポインター)](../cpp/pointer-to-member-operators-dot-star-and-star.md)|[.&#42;または ->&#42;](../cpp/pointer-to-member-operators-dot-star-and-star.md)|
|**グループ 5 の優先順位、左右の結合規則から**|
|[乗算](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[&#42;](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[除算](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[/](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|[剰余](../cpp/multiplicative-operators-and-the-modulus-operator.md)|[%](../cpp/multiplicative-operators-and-the-modulus-operator.md)|
|**グループ 6 の優先順位、左右の結合規則から**|
|[加算](../cpp/additive-operators-plus-and.md)|[+](../cpp/additive-operators-plus-and.md)|
|[減算](../cpp/additive-operators-plus-and.md)|[-](../cpp/additive-operators-plus-and.md)|
|**グループ 7 の優先順位、左右の結合規則から**|
|[左シフト](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[<<](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|[右シフト](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|[>>](../cpp/left-shift-and-right-shift-operators-input-and-output.md)|
|**8 のグループの優先順位、左右の結合規則から**|
|[より小さい](../cpp/relational-operators-equal-and-equal.md)|[<](../cpp/relational-operators-equal-and-equal.md)|
|[より大きい](../cpp/relational-operators-equal-and-equal.md)|[>](../cpp/relational-operators-equal-and-equal.md)|
|[以下](../cpp/relational-operators-equal-and-equal.md)|[<=](../cpp/relational-operators-equal-and-equal.md)|
|[以上](../cpp/relational-operators-equal-and-equal.md)|[>=](../cpp/relational-operators-equal-and-equal.md)|
|**9 のグループの優先順位、左右の結合規則から**|
|[等価](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[==](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|[非等価](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|[\!=](../cpp/equality-operators-equal-equal-and-exclpt-equal.md)|
|**10 のグループは、左右の結合規則からよりも優先されます。**|
|[ビットごとの AND](../cpp/bitwise-and-operator-amp.md)|[&amp;](../cpp/bitwise-and-operator-amp.md)|
|**グループ 11 の優先順位、左右の結合規則から**|
|[ビットごとの排他的 OR](../cpp/bitwise-exclusive-or-operator-hat.md)|[^](../cpp/bitwise-exclusive-or-operator-hat.md)|
|**左右の結合規則から 12 の優先順位をグループ化します。**|
|[ビット演算包含的 OR](../cpp/bitwise-inclusive-or-operator-pipe.md)|[&#124;](../cpp/bitwise-inclusive-or-operator-pipe.md)|
|**グループ 13 の優先順位、左右の結合規則から**|
|[論理 AND](../cpp/logical-and-operator-amp-amp.md)|[&amp;&amp;](../cpp/logical-and-operator-amp-amp.md)|
|**グループ 14 の優先順位、左右の結合規則から**|
|[論理 OR](../cpp/logical-or-operator-pipe-pipe.md)|[&#124;&#124;](../cpp/logical-or-operator-pipe-pipe.md)|
|**右から左方向への 15 の優先順位をグループ化します。**|
|[条件付き](../cpp/conditional-operator-q.md)|[? :](../cpp/conditional-operator-q.md)|
|**右から左方向への 16 の優先順位をグループ化します。**|
|[代入](../cpp/assignment-operators.md)|[=](../cpp/assignment-operators.md)|
|[乗算代入](../cpp/assignment-operators.md)|[&#42;=](../cpp/assignment-operators.md)|
|[除算代入](../cpp/assignment-operators.md)|[/=](../cpp/assignment-operators.md)|
|[剰余代入](../cpp/assignment-operators.md)|[%=](../cpp/assignment-operators.md)|
|[加算代入](../cpp/assignment-operators.md)|[+=](../cpp/assignment-operators.md)|
|[減算代入](../cpp/assignment-operators.md)|[-=](../cpp/assignment-operators.md)|
|[左シフト代入](../cpp/assignment-operators.md)|[<<=](../cpp/assignment-operators.md)|
|[右シフト代入](../cpp/assignment-operators.md)|[>>=](../cpp/assignment-operators.md)|
|[ビットごとの AND 代入](../cpp/assignment-operators.md)|[&amp;=](../cpp/assignment-operators.md)|
|[ビット処理包括的 OR 代入](../cpp/assignment-operators.md)|[&#124;=](../cpp/assignment-operators.md)|
|[ビット演算子排他的 OR 代入](../cpp/assignment-operators.md)|[^=](../cpp/assignment-operators.md)|
|**右から左方向への 17 の優先順位をグループ化します。**|
|[スロー式](../cpp/try-throw-and-catch-statements-cpp.md)|[throw](../cpp/try-throw-and-catch-statements-cpp.md)|
|**18 のグループの優先順位、左右の結合規則から**|
|[コンマ](../cpp/comma-operator.md)|[、](../cpp/comma-operator.md)|

## <a name="see-also"></a>関連項目

[演算子のオーバーロード](operator-overloading.md)