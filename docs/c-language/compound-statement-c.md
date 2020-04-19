---
title: 複合ステートメント (C)
ms.date: 11/04/2016
helpviewer_keywords:
- compound statements
- statements, compound
ms.assetid: 32d1bf86-cbbc-42a9-ba3a-1be1c6c7754c
ms.openlocfilehash: 42d4c1d21c3e98dfc0281a47a35e033852f8de18
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152158"
---
# <a name="compound-statement-c"></a>複合ステートメント (C)

複合ステートメント ("ブロック" ともいう) は通常、**if** ステートメントなどの別のステートメントの本体として現れます。 「[宣言および型](../c-language/declarations-and-types.md)」では、複合ステートメントの先頭に記述できる宣言の形式とその意味について説明しています。

## <a name="syntax"></a>構文

*compound-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**{** *declaration-list*<sub>opt</sub> *statement-list*<sub>opt</sub> **}**

*declaration-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*declaration-list* *declaration*

*statement-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*statement-list* *statement*

宣言がある場合は、すべてのステートメントの前に記述する必要があります。 複合ステートメントの先頭で宣言された識別子のスコープは、その宣言ポイントからブロックの最後までです。 同じ識別子の宣言が内側のブロック内にない限り、ブロック全体から参照可能です。

複合ステートメントの識別子は、**register**、**static**、または `extern` で明示的に宣言されていない限り、**auto** と想定されます。ただし関数は `extern` にしかできません。 関数宣言で `extern` 指定子の指定を省略できます。それでも、関数は `extern` です。

`extern` ストレージ クラスを指定して複合ステートメント内で変数または関数が宣言されている場合、ストレージは割り当てられず、初期化は許可されません。 宣言は、他の場所で定義された外部変数または関数を参照します。

**auto** または **register** キーワードを使用してブロック内で宣言されている変数は、複合ステートメントに入るたびに再割り当てされ、必要に応じて初期化されます。 これらの変数は、複合ステートメントが終了した後は定義されていません。 ブロック内で宣言された変数が **static** 属性を持つ場合、プログラムの実行が開始されるとその変数が初期化されて、その値がプログラム全体で保持されます。 **static** については、「[ストレージ クラス](../c-language/c-storage-classes.md)」を参照してください。

この例は、複合ステートメントを示しています。

```
if ( i > 0 )
{
    line[i] = x;
    x++;
    i--;
}
```

この例では、`i` が 0 を超える場合、複合ステートメント内のすべてのステートメントが順次実行されます。

## <a name="see-also"></a>関連項目

[ステートメント](../c-language/statements-c.md)
