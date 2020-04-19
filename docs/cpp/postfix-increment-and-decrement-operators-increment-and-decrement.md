---
title: '後置インクリメント演算子と後置デクリメント演算子: ++ および --'
ms.date: 11/04/2016
f1_keywords:
- --
- ++
helpviewer_keywords:
- increment operators [C++], syntax
- member-selection operators [C++]
- -- operator [C++], postfix decrement operators
- postfix operators [C++]
- ++ operator [C++], postfix increment operators
- decrement operators [C++], syntax
- operators [C++], postfix
- decrement operators [C++]
ms.assetid: 0204d5c8-51b0-4108-b8a1-074c5754d89c
ms.openlocfilehash: e1a87fe4815a75b97616d7b11a4b9aa4ae65eb9f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62392142"
---
# <a name="postfix-increment-and-decrement-operators--and---"></a>後置インクリメント演算子と後置デクリメント演算子: ++ および --

## <a name="syntax"></a>構文

```
postfix-expression ++
postfix-expression --
```

## <a name="remarks"></a>Remarks

C++ には、前置および後置のインクリメント演算子およびデクリメント演算子が用意されています。このセクションでは、後置インクリメント演算子および後置デクリメント演算子についてのみ説明します (詳細については、次を参照してください[前置インクリメント演算子と前置デクリメント演算子](../cpp/prefix-increment-and-decrement-operators-increment-and-decrement.md)。)。2 つの違いは、後置表記法で、演算子が後に表示される*後置式*プレフィックス表記法では演算子が前に対し、*式。* 次の例は、後置インクリメント演算子を示しています。

```cpp
i++;
```

後置のインクリメント演算子を適用する効果 ( **++** )、オペランドの値が、適切な型の 1 つの単位で増加したことができます。 同様に、後置デクリメント演算子を適用する効果 ( **--** ) で、適切な型の 1 つの単位、オペランドの値が減少したことができます。

後置のインクリメントを確認することが重要デクリメント式は、式の値に評価または*より前のバージョン*各演算子のアプリケーション。 インクリメントまたはデクリメント操作が行われる*後*オペランドが評価されます。 この問題は、後置インクリメントまたはデクリメント演算が、より大きな式のコンテキストで行われる場合にのみ発生します。

後置演算子を関数の引数に適用した場合、引数の値が関数に渡される前にインクリメントまたはデクリメントされる保証はありません。  詳細については、C++ 標準のセクション 1.9.17 を参照してください。

型のオブジェクトの配列へのポインターに後置のインクリメント演算子を適用する**long**実際には、ポインターの内部表現に 4 つ追加します。 この動作により、ポインターは、以前の管理、 *n*番目の要素を指すため、配列の (*n*+1) 番目の要素。

置インクリメント演算子と前置デクリメント演算子を後置のオペランドは変更可能である必要があります (いない**const**) 演算またはポインター型の左辺値です。 結果の型はいるのと同じ、*後置式*が左辺値ではなくなりました。

**Visual Studio 2017 バージョン 15.3 以降**(で使用可能な[/std:c++17](../build/reference/std-specify-language-standard-version.md))。オペランドの後置インクリメントまたはデクリメント演算子できない可能性があります型の**bool**します。

次のコードは、後置インクリメント演算子を示しています。

```cpp
// expre_Postfix_Increment_and_Decrement_Operators.cpp
// compile with: /EHsc
#include <iostream>
using namespace std;

int main() {
   int i = 10;
   cout << i++ << endl;
   cout << i << endl;
}
```

列挙型に対する後置インクリメント演算および後置デクリメント演算はサポートされていません。

```cpp
enum Compass { North, South, East, West );
Compass myCompass;
for( myCompass = North; myCompass != West; myCompass++ ) // Error
```

## <a name="see-also"></a>関連項目

[後置式](../cpp/postfix-expressions.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[C 後置インクリメント演算子と後置デクリメント演算子](../c-language/c-postfix-increment-and-decrement-operators.md)