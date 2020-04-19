---
title: 制御の移動
ms.date: 11/04/2016
helpviewer_keywords:
- control flow, branching
- control flow, transferring control
ms.assetid: aa51e7f2-060f-4106-b0fe-331f04357423
ms.openlocfilehash: 1fc487628f26dcac097109bc71fa960e501d0797
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266817"
---
# <a name="transfers-of-control"></a>制御の移動

使用することができます、 **goto**ステートメントまたは**case**でラベル付け、**switch**初期化子を越えて分岐するプログラムを指定するステートメント。 初期化子を含む宣言がジャンプ ステートメントの発生元のブロックで囲まれたブロックに存在しない限り、このようなコードは無効です。

次の例は、オブジェクト `total`、`ch`、`i` を宣言して初期化するループを示します。 ありますが、不適切なも**goto**初期化子を越えて制御を転送するステートメント。

```cpp
// transfers_of_control.cpp
// compile with: /W1
// Read input until a nonnumeric character is entered.
int main()
{
   char MyArray[5] = {'2','2','a','c'};
   int i = 0;
   while( 1 )
   {
      int total = 0;

      char ch = MyArray[i++];

      if ( ch >= '0' && ch <= '9' )
      {
         goto Label1;

         int i = ch - '0';
      Label1:
         total += i;   // C4700: transfers past initialization of i.
      } // i would be destroyed here if  goto error were not present
   else
      // Break statement transfers control out of loop,
      //  destroying total and ch.
      break;
   }
}
```

上記の例では、 **goto**ステートメントの初期化を越えて制御を転送しようとする`i`します。 ただし、`i` が宣言されていても初期化されていない場合、転送は有効になります。

オブジェクト`total`と`ch`として機能するブロックで宣言された、*ステートメント*for**while**ステートメントを使用して、そのブロックが終了したときに破棄されます、 **break**ステートメント。