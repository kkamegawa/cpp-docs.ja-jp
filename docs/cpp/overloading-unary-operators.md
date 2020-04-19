---
title: 単項演算子のオーバーロード
ms.date: 11/04/2016
helpviewer_keywords:
- unary operators [C++], plus
- increment operators [C++], overloaded
- unary operators [C++], minus
- operators [C++], unary
- redefinable unary operators [C++]
- unary operators [C++]
- pointer dereference operator overloading
- plus operator
ms.assetid: 7683ef08-42a4-4283-928f-d3dd4f3ab4c0
ms.openlocfilehash: 802380bad59534e8402020142e394b3948032476
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62377232"
---
# <a name="overloading-unary-operators"></a>単項演算子のオーバーロード

オーバーロードできる単項演算子は次のとおりです。

1. `!` ([論理 NOT](../cpp/logical-negation-operator-exclpt.md))

1. `&` ([アドレスの](../cpp/address-of-operator-amp.md))

1. `~` ([1 の補数](../cpp/one-s-complement-operator-tilde.md))

1. `*` ([ポインター逆参照](../cpp/indirection-operator-star.md))

1. `+` ([単項プラス](../cpp/additive-operators-plus-and.md))

1. `-` ([単項マイナス符号](../cpp/additive-operators-plus-and.md))

1. `++` ([インクリメント](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

1. `--` ([デクリメント](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md))

9. 変換演算子

後置インクリメントとデクリメント演算子 (`++`と`--`) で個別に扱われます[インクリメントおよびデクリメント](../cpp/increment-and-decrement-operator-overloading-cpp.md)します。

変換演算子も、別のトピックで説明します。参照してください[ユーザー定義型の変換](../cpp/user-defined-type-conversions-cpp.md)します。

次の規則は他のすべての単項演算子に適用されます。 単項演算子関数を非静的メンバーとして宣言するには、次の形式で宣言する必要があります。

> *ret-type* **operator** *op* **()**

場所*ret 型*は戻り値の型と*op*が演算子の 1 つは、上記の表に表示されています。

単項演算子関数をグローバル関数として宣言するには、次の形式で宣言する必要があります。

> *ret-type* **operator** *op* **(** *arg* **)**

場所*ret 型*と*op*メンバー演算子関数について説明したとおり、 *arg*は操作対象のクラス型の引数です。

> [!NOTE]
>  単項演算子の戻り値の型に制限はありません。 たとえば、論理 NOT (`!`) が整数値を返すのは正しい使い方ですが、強制ではありません。

## <a name="see-also"></a>関連項目

[演算子のオーバーロード](../cpp/operator-overloading.md)