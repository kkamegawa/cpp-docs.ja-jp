---
title: for ステートメント (C)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C]
ms.assetid: 560a8de4-19db-4868-9f18-dbe51b17900d
ms.openlocfilehash: df00bcab2f9f9e51a6f37e19670b6cd240fa5cc4
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152834"
---
# <a name="for-statement-c"></a>for ステートメント (C)

**for** ステートメントを使用すると、指定したステートメントまたは複合ステートメントを、指定した回数だけ繰り返すことができます。 **for** ステートメントの本体は、省略可能な条件が false になるまで、ゼロ回以上実行されます。 **for** ステートメント内で省略可能な式を使用して、値を初期化し、**for** ステートメントの実行中に値を変更することができます。

## <a name="syntax"></a>構文

*iteration-statement*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;**for** **(** *init-expression*<sub>opt</sub> **;** *cond-expression*<sub>opt</sub> **;** *loop-expression*<sub>opt</sub> **)** *statement*

**for** ステートメントの実行は、次のように進行します。

1. *init-expression* がある場合、それが評価されます。 この式は、ループの初期化を指定します。 *init-expression* の型に制限はありません。

1. *cond-expression* がある場合、それが評価されます。 この式は、演算型またはポインター型である必要があります。 この式は、各イテレーションの前に評価されます。 次の 3 つの結果が発生する可能性があります。

   - *cond-expression* が **true** (0 以外) の場合、*statement* が実行されます。その後、*loop-expression* があれば、それが評価されます。 *loop-expression* は、各イテレーションの後に評価されます。 この式の型に制限はありません。 副作用が順に実行されます。 その後、*cond-expression* の評価から再び処理が開始されます。

   - *cond-expression* を省略すると、*cond-expression* を true と見なして前述の説明どおりに処理が進行します。 *cond-expression* 引数のない **for** ステートメントが終了するのは、ステートメント本体内の **break** ステートメントまたは **return** ステートメントが実行されたときか、(**for** ステートメント本体外にあるラベル付きステートメントへの) **goto** が実行された場合だけです。

   - *cond-expression* が **false** (0) の場合、**for** ステートメントが終了し、制御はプログラムの次のステートメントに渡されます。

**for** ステートメントは、そのステートメント本体内の **break**、**goto**、または **return** ステートメントが実行されたときにも終了します。 **for** ループの **continue** ステートメントにより *loop-expression* が評価されます。 **for** ループ内で **break** ステートメントが実行されると、*loop-expression* は評価されず、実行もされません。 次のステートメント、

```C
for( ; ; )
```

は、**break**、**goto**、**return** のいずれかのステートメントによってしか終了できない無限ループを発生させる、よく使用される方法です。

## <a name="example"></a>例

**for** ステートメントの例を次に示します。

```C
// c_for.c
int main()
{
   char* line = "H e  \tl\tlo World\0";
   int space = 0;
   int tab = 0;
   int i;
   int max = strlen(line);
   for (i = 0; i < max; i++ )
   {
      if ( line[i] == ' ' )
      {
          space++;
      }
      if ( line[i] == '\t' )
      {
          tab++;
      }
   }

   printf("Number of spaces: %i\n", space);
   printf("Number of tabs: %i\n", tab);
   return 0;
}
```

## <a name="output"></a>出力

```Output
Number of spaces: 4
Number of tabs: 2
```

## <a name="see-also"></a>関連項目

[ステートメント](../c-language/statements-c.md)
