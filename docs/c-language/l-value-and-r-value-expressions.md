---
title: 左辺値と右辺値の式
ms.date: 11/04/2016
helpviewer_keywords:
- L-values
- member-selection expressions
- R-value expressions
- subscript expressions
ms.assetid: b790303e-ec6f-4d0d-bc55-df42da267172
ms.openlocfilehash: bd5f702588a11b7841f77de539d113206833cde9
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56150221"
---
# <a name="l-value-and-r-value-expressions"></a>左辺値と右辺値の式

メモリ位置を示す式は「左辺値」式と呼ばれます。 左辺値は記憶領域の "ロケーター" 値や、等号 (**=**) の左側に表示されることを意味する "左" 値を表します。 多くの場合、左辺値は識別子です。

変更可能な場所を示す式は、「変更可能な左辺値」と呼ばれます。 変更可能な左辺値は、配列型、不完全な型、または **const** 属性を持つ型を含むことはできません。 構造体や共用体が変更可能な左辺値となるためには、**const** 属性を持つメンバーを含んでいない必要があります。 識別子の名前は記憶領域の場所を表します。また、変数の値はその場所に格納されている値です。

識別子がメモリ位置を示し、演算型、構造体型、共用体型、またはポインター型である場合、その識別子は変更可能な左辺値です。 たとえば、`ptr` が記憶領域へのポインターである場合、`*ptr` は、`ptr` が指す記憶領域を指定する変更可能な左辺値です。

次のいずれの C 式も、左辺値の式となることができます。

- 整数型、浮動型、ポインター型、構造体型、または共用体型の識別子

- 配列に評価されない添字 (**[ ]**) 式

- メンバー選択式 (**->** または **.**)

- 配列を示さない単項間接 (<strong>\*</strong>) 式

- かっこ内の左辺値式

- **const** オブジェクト (変更不可能な左辺値)

式の値について説明し、左辺値と区別するために、「右辺値」という用語が使用されることがあります。 すべての左辺値は右辺値ですが、すべての右辺値が左辺値というわけではありません。

**Microsoft 固有の仕様**

Microsoft C には、オブジェクトのサイズがキャストで延長されない限り、左辺値のキャストを左辺値として使用できるようにする ANSI C 標準規格の拡張機能が備わっています。 (詳細については、「[型キャスト変換](../c-language/type-cast-conversions.md)」を参照してください)。この機能を説明する例を次に示します。

```
char *p ;
short  i;
long l;

(long *) p = &l ;       /* Legal cast   */
(long) i = l ;          /* Illegal cast */
```

Microsoft C の既定では、Microsoft 拡張機能が有効になっています。 これらの拡張機能を無効にするには、/Za コンパイラ オプションを使用します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[オペランドおよび式](../c-language/operands-and-expressions.md)
