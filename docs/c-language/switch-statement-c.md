---
title: switch ステートメント (C)
ms.date: 11/04/2016
f1_keywords:
- switch
helpviewer_keywords:
- switch keyword [C]
ms.assetid: fbede014-23bd-4ab1-8094-c8d9d9cb963a
ms.openlocfilehash: 0f781147bf4ed020cf925ca29c2ba1b0f601cde1
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56148193"
---
# <a name="switch-statement-c"></a>switch ステートメント (C)

`switch` および **case** ステートメントを使用すると、複雑な条件付き処理や分岐処理を制御しやすくなります。 `switch` ステートメントは、本体内のステートメントに制御を移します。

## <a name="syntax"></a>構文

*selection-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**switch (** *expression* **)** *statement*

*labeled-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**case**  *constant-expression*  **:**  *statement*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**default :**  *statement*

**case** *constant-expression* が **switch (** *expression* **)** の値と一致するステートメントに制御が移ります。 `switch` ステートメントには、**case** のインスタンスをいくつでも含めることができますが、同じ `switch` ステートメント内の 2 つの case 定数を同じ値にすることはできません。 ステートメント本体の実行は選択されたステートメントで始まり、本体の最後まで、または **break** ステートメントで制御が本体の外部に移されるまで続きます。

通常、`switch` ステートメントは次のように使用します。

```C
switch ( expression )
{
    // declarations
    // . . .
    case constant_expression:
        // statements executed if the expression equals the
        // value of this constant_expression
        break;
    default:
        // statements executed if expression does not equal
        // any case constant_expression
}
```

**break** ステートメントを使用して、`switch` ステートメント内の特定の case の処理を終了したり、`switch` ステートメントの最後に分岐したりすることができます。 **break** がない場合、プログラムは次の case まで続き、**break** またはステートメントの最後に達するまでステートメントが実行されます。 状況によっては、この継続が望ましい場合もあります。

**default** ステートメントは、すべての **case** *constant-expression* が **switch (** *expression* **)** の値と等しくない場合に実行されます。 **default** ステートメントが省略され、**case** の一致が見つからない場合、`switch` 本体のステートメントは実行されません。 **default** ステートメントは、最大で 1 つだけ指定できます。 **default** ステートメントを最後に記述する必要はありません。`switch` ステートメントの本体内の任意の場所で使用できます。 **case** または **default** ラベルは、`switch` ステートメント内でのみ使用できます。

`switch` *expression* および **case** *constant-expression* の型は整数である必要があります。 各 **case** *constant-expression* の値は、ステートメント本体内で一意である必要があります。

`switch` ステートメント本体の **case** および **default** ラベルは、ステートメント本体内のどこで実行が開始されるかが決まる初期テストでのみ重要です。 switch ステートメントは入れ子にすることができます。 静的変数は、`switch` ステートメントの実行前に初期化されます。

> [!NOTE]
> 宣言は、`switch` の本体を構成する複合ステートメントの先頭に記述できますが、宣言に含まれる初期化は行われません。 `switch` ステートメントは、初期化が含まれる行をバイパスして、本体内の実行可能なステートメントに直接制御を移します。

次の例に、`switch` ステートメントを示します。

```C
switch( c )
{
    case 'A':
        capa++;
    case 'a':
        lettera++;
    default :
        total++;
}
```

この例の `switch` 本体の 3 つのステートメントは、`c` が `'A'` と等しい場合にすべて実行されます。**break** ステートメントは次の case の前に出現しないためです。 実行制御は最初のステートメント (`capa++;`) に移動し、本体の残りが順に継続されます。 `c` が `'a'` と等しい場合、`lettera` と `total` がインクリメントされます。 `total` が `c` または `'A'` と等しくない場合、`'a'` だけがインクリメントされます。

```C
switch( i )
{
    case -1:
        n++;
        break;
    case 0 :
        z++;
        break;
    case 1 :
        p++;
        break;
}
```

この例では、**break** ステートメントは `switch` 本体の各ステートメントに続きます。 **break** ステートメントによって、1 つのステートメントの実行後にステートメント本体を終了することが強制されます。 `i` が -1 と等しい場合、`n` だけがインクリメントされます。 `n++;` ステートメントに続く **break** により、残りのステートメントをバイパスして、実行制御をステートメント本体の外部に渡すことが強制されます。 同様に、`i` が 0 と等しい場合は `z` だけがインクリメントされ、`i` が 1 と等しい場合は `p` だけがインクリメントされます。 複合ステートメントの最後に制御は本体の外部に移るため、**break** ステートメントは厳密には必要ありませんが、一貫性を持たせるために含まれています。

次の例に示すように、1 つのステートメントに複数の **case** ラベルを含めることができます。

```C
case 'a' :
case 'b' :
case 'c' :
case 'd' :
case 'e' :
case 'f' :  hexcvt(c);
```

この例では、*constant-expression* が `'a'` から `'f'` の間の文字に等しい場合に `hexcvt` 関数が呼び出されます。

**Microsoft 固有の仕様**

Microsoft C では、`switch` ステートメントの case 値の数を制限していません。 この数は、使用できるメモリによってのみ制限されます。 ANSI C では、1 つの `switch` ステートメント内に 257 個までの case ラベルを使用できます。

Microsoft C の既定では、Microsoft 拡張機能が有効になっています。 これらの拡張機能を無効にするには、/Za コンパイラ オプションを使用します。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[switch ステートメント (C++)](../cpp/switch-statement-cpp.md)
