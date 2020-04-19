---
title: Microsoft 固有の修飾子
ms.date: 08/16/2018
ms.assetid: 22c7178c-f854-47fa-9de6-07d23fda58e1
ms.openlocfilehash: 2d65c0fe99895949d537ccf4368df2add3ff91ad
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857425"
---
# <a name="microsoft-specific-modifiers"></a>Microsoft 固有の修飾子

このセクションでは、次の領域での C++ への Microsoft 固有の拡張について説明します。

- [ベースとなるアドレス指定](based-addressing.md)(ポインターをベースとして使用し、他のポインターをオフセットできること)

- [関数呼び出し規約](calling-conventions.md)

- [__Declspec](declspec.md)キーワードを使用して宣言された拡張ストレージクラス属性

- [__W64](w64.md)キーワード

## <a name="microsoft-specific-keywords"></a>Microsoft 固有キーワード

Microsoft 固有キーワードの多くは、宣言子を変更して派生型を作成する際に使用できます。 宣言子の詳細については、[宣言子](overview-of-declarators.md)を参照してください。

|キーワード|説明|派生型を作成するために使用しますか?|
|-------------|-------------|---------------------------------|
|[__based](based-grammar.md)|これに続く名前は、宣言に含まれている 32 ビット ベースへの 32 ビット オフセットを宣言します。|○|
|[__cdecl](cdecl.md)|これに続く名前は、C の命名規約と呼び出し規則を使用します。|○|
|[__declspec](declspec.md)|これに続く名前は、Microsoft 固有のストレージ クラス属性を指定します。|いいえ|
|[__fastcall](fastcall.md)|これに続く名前は、引数を渡すためのスタックの代わりに、レジスタ (使用できる場合) を使用できる関数を宣言します。|○|
|[__restrict](extension-restrict.md)|__Declspec ([制限](restrict.md)) に似ていますが、変数に使用します。|いいえ|
|[__stdcall](stdcall.md)|これに続く名前は、標準呼び出し規約を順守する関数を指定します。|○|
|[__w64](w64.md)|64 ビット コンパイラでより大きいデータ型としてマークします。|いいえ|
|[__unaligned](unaligned.md)|型またはその他のデータへのポインターが配置されていないことを指定します。|いいえ|
|[__vectorcall](vectorcall.md)|これに続く名前は、引数を渡すためのスタックの代わりに、SSE レジスタを含むレジスタ (使用できる場合) を使用できる関数を宣言します。|○|

## <a name="see-also"></a>参照

[C++ 言語リファレンス](cpp-language-reference.md)
