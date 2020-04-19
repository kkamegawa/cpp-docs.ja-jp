---
title: C++ ビット フィールド
ms.date: 11/19/2018
helpviewer_keywords:
- bitfields [C++]
- fields [C++], bit
- bit fields
ms.assetid: 6f4b62e3-cc1d-4e5d-bf34-05904104f71a
ms.openlocfilehash: bba57d495553e9622fcece9d036fc4f6eff3fa04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301601"
---
# <a name="c-bit-fields"></a>C++ ビット フィールド

クラスと構造体には、整数型よりも記憶領域の占有率が少ないメンバーを含めることができます。 これらのメンバーは、ビット フィールドとして指定されます。 ビットフィールド*メンバー宣言子*の指定の構文は次のとおりです。

## <a name="syntax"></a>構文

*declarator* **:** *constant-expression*

## <a name="remarks"></a>コメント

(省略可能)*宣言子*は、プログラム内でメンバーにアクセスするときに使用する名前です。 整数型 (列挙型を含む) である必要があります。 *定数式*は、メンバーが構造体で占有するビット数を指定します。 匿名ビット フィールド (つまり、識別子のないビット フィールド メンバー) はパディング用に使用できます。

> [!NOTE]
> 名前のないビットフィールド width 0 は、次のビットフィールドを次の**型**境界に強制的にアラインメントします。ここで、 **type**はメンバーの型です。

次の例では、ビット フィールドを持つ構造体を宣言します。

```cpp
// bit_fields1.cpp
// compile with: /LD
struct Date {
   unsigned short nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned short nMonthDay : 6;    // 0..31  (6 bits)
   unsigned short nMonth    : 5;    // 0..12  (5 bits)
   unsigned short nYear     : 8;    // 0..100 (8 bits)
};
```

`Date` 型のオブジェクトの概念的なメモリ レイアウトを次の図に示します。

![日付オブジェクトのメモリレイアウト](../cpp/media/vc38uq1.png "データ オブジェクトのメモリ レイアウト") <br/>
データ オブジェクトのメモリ レイアウト

なお`nYear`8 ビット長であり、宣言型のワード境界をオーバーフローする**unsigned** **short**します。 そのため、新しいの先頭で開始されます**unsigned** **short**します。 すべてのビット フィールドが基になる型の 1 つのオブジェクトに収まる必要はありません。宣言で要求されたビット数に従って、ストレージの新しい単位が割り当てられます。

**Microsoft 固有の仕様**

ビット フィールドとして宣言されたデータの順序は、上の図に示すように、下位から上位のビットへ向います。

**END Microsoft 固有の仕様**

構造体の宣言に、次の例のように、名前の付いていない長さが 0 のフィールドが含まれている場合、

```cpp
// bit_fields2.cpp
// compile with: /LD
struct Date {
   unsigned nWeekDay  : 3;    // 0..7   (3 bits)
   unsigned nMonthDay : 6;    // 0..31  (6 bits)
   unsigned           : 0;    // Force alignment to next boundary.
   unsigned nMonth    : 5;    // 0..12  (5 bits)
   unsigned nYear     : 8;    // 0..100 (8 bits)
};
```

その後、メモリレイアウトは次の図のようになります。

![長さが 0&#45;のビットフィールドを持つ日付オブジェクトのレイアウト](../cpp/media/vc38uq2.png "長さが 0&#45;のビットフィールドを持つ日付オブジェクトのレイアウト") <br/>
長さ 0 のビット フィールドを持つデータ オブジェクトのレイアウト

ビットフィールドの基になる型は、「[組み込み型](../cpp/fundamental-types-cpp.md)」で説明されているように、整数型である必要があります。

`const T&` 型の参照の初期化子が `T`型のビットフィールドを参照する左辺値の場合、その参照はビットフィールドに直接バインドされません。 代わりに、この参照は、ビットフィールドの値を保持するために、一時的に初期化されたにバインドされます。

## <a name="restrictions-on-bit-fields"></a>ビット フィールドの制約

次の一覧は、ビット フィールドの不適切な操作を詳述します。

- ビット フィールドのアドレスの取得。

- ビットフィールドを使用した非**定数**参照の初期化。

## <a name="see-also"></a>関連項目

[クラスと構造体](../cpp/classes-and-structs-cpp.md)