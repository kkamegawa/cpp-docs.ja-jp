---
title: Conversions to and from Pointer Types (ポインター型との間の変換)
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 2d907dbcf4f826d364fb68ce65f7d44c6cfe97cd
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147244"
---
# <a name="conversions-to-and-from-pointer-types"></a>Conversions to and from Pointer Types (ポインター型との間の変換)

ある型の値へのポインターは、別の型へのポインターに変換できます。 ただし、結果は、各型のストレージのアラインメント要件とサイズの違いにより、未定義になることがあります。 オブジェクトへのポインターは、型のストレージ アラインメントの厳密さが同じか、それ以下のオブジェクトへのポインターに変更でき、変更なしで元に戻すことができます。

`void` へのポインターは、情報の制限や損失なしに任意の型へのポインターとの間で変換できます。 結果が元の型に戻される場合、元のポインターが復元されます。

ポインターが、型は同じでも修飾子が異なるか、修飾子の追加された別のポインターに変換される場合、新しいポインターは、新しい修飾子の制限を除いて、古いポインターと同じになります。

ポインター値は、整数値に変換することもできます。 変換パスは、次の規則に従い、ポインターのサイズと整数型のサイズによって決まります。

- ポインターのサイズが整数型のサイズ以上である場合、ポインターは、浮動小数点型に変換できない点を除けば、変換で符号なしの値と同様の動作をします。

- ポインターが整数型より小さい場合、ポインターは最初に整数型と同じサイズのポインターに変換されてから、整数型に変換されます。

逆に、整数型は、次の規則に従ってポインター型に変換することができます。

- 整数型がポインター型と同じサイズである場合、変換では整数値が単にポインター (符号なし整数) として処理されます。

- 整数型のサイズがポインター型のサイズと異なる場合、整数型は最初に「[符号付き整数型からの変換](../c-language/conversions-from-signed-integral-types.md)」と「[符号なし整数型からの変換](../c-language/conversions-from-unsigned-integral-types.md)」の表で指定された変換パスを使用して、ポインターのサイズに変換されます。 その後、これがポインター値として扱われます。

値 0 の整数定数式、または **void** <strong>\*</strong> 型にキャストされた整数定数式は、型キャスト、代入、または任意の型のポインターとの比較によって変換できます。 これによって、同じ型の別の null ポインターと等しい null ポインターが生成されます。しかし、この null ポインターは、関数またはオブジェクトへのポインターとは等しくありません。 定数 0 以外の整数はポインター型に変換することができますが、結果は移植できません。

## <a name="see-also"></a>関連項目

[代入の変換](../c-language/assignment-conversions.md)
