---
title: switch ステートメント (C++)
ms.date: 11/04/2016
f1_keywords:
- default_cpp
- switch_cpp
- case_cpp
helpviewer_keywords:
- switch keyword [C++]
- case keyword [C++], in switch statements
- default keyword [C++]
ms.assetid: 6c3f3ed3-5593-463c-8f4b-b33742b455c6
ms.openlocfilehash: 67918b7df747d3bee923da500729e60b4fe04336
ms.sourcegitcommit: 1819bd2ff79fba7ec172504b9a34455c70c73f10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/09/2018
ms.locfileid: "51328852"
---
# <a name="switch-statement-c"></a>switch ステートメント (C++)

整数式の値に応じてコードの複数のセクション間を切り替えます。

## <a name="syntax"></a>構文

```
   switch ( init; expression )
   case constant-expression : statement
   [default  : statement]
```

## <a name="remarks"></a>Remarks

*式*または整数型への明確な変換がある対象のクラス型の整数型にする必要があります。 」の説明に従って、整数の上位変換が実行される[標準変換](standard-conversions.md)します。

**切り替える**ステートメント本体内から成る、一連の**ケース**ラベルと省略可能な**既定**ラベル。 2 つの定数式で**ケース**ステートメントが同じ値に評価されることができません。 **既定**ラベルは 1 回だけ出現できます。 ラベル付きステートメントは構文上の要件ではありませんが、**切り替える**ステートメントはせずに意味がありません。   default ステートメントを最後に記述する必要はありません。switch ステートメントの本体内の任意の場所で使用できます。 case ラベルまたは default ラベルは、switch ステートメント内でのみ使用できます。

*定数式*各**ケース**ラベルがの型に変換された*式*と比較*式*の等しいかどうか。 コントロールがあるステートメントに移ります**ケース** *定数式* の値と一致する *式* します。 結果の動作を次の表に示します。

### <a name="switch-statement-behavior"></a>switch ステートメントの動作

|条件|アクション|
|---------------|------------|
|変換後の値は、上位変換された制御式の値と一致します。|制御は、そのラベルの次のステートメントに移ります。|
|含まれている定数に一致、定数のいずれも、**ケース**ラベル、**既定**ラベルが存在します。|制御が移ります、**既定**ラベル。|
|含まれている定数に一致、定数のいずれも、**ケース**ラベル。**既定**ラベルが存在しません。|後のステートメントに制御が移ります、**切り替える**ステートメント。|

コントロールがそれ以降によって妨げられるいない一致する式が見つかった場合**ケース**または**既定**ラベル。 [Break](../cpp/break-statement-cpp.md)ステートメントが実行を停止し、後のステートメントに制御を転送するために使用、**切り替える**ステートメント。 なし、 **break**ステートメントでは、すべてのステートメントから、一致する**ケース**の末尾にラベル、**切り替える**など、**既定**は実行されます。 例えば:

```cpp
// switch_statement1.cpp
#include <stdio.h>

int main() {
   char *buffer = "Any character stream";
   int capa, lettera, nota;
   char c;
   capa = lettera = nota = 0;

   while ( c = *buffer++ )   // Walks buffer until NULL
   {
      switch ( c )
      {
         case 'A':
            capa++;
            break;
         case 'a':
            lettera++;
            break;
         default:
            nota++;
      }
   }
   printf_s( "\nUppercase a: %d\nLowercase a: %d\nTotal: %d\n",
      capa, lettera, (capa + lettera + nota) );
}
```

上の例では、`capa` は `c` が大文字 `A` の場合、インクリメントします。 **Break**後のステートメント`capa++`の実行を終了、**スイッチ**をステートメント本体と制御を渡します、**中**ループします。 なし、 **break**ステートメントでは、実行は「フォール スルー」[次へ] のラベル付きステートメントにように`lettera`と`nota`もインクリメントされます。 目的は同じですが、によって処理される、 **break**ステートメント`case 'a'`。 場合`c`が小文字`a`、`lettera`がインクリメントされます、 **break**ステートメントが終了、**切り替える**ステートメント本体。 場合`c`でない、`a`または`A`、**既定**ステートメントが実行されます。

**Visual Studio 2017 以降:** (で使用可能な[/std:c + + + 17](../build/reference/std-specify-language-standard-version.md))、`[[fallthrough]]`標準の c++ 17 で属性を指定します。 使用できます、**切り替える**ステートメントは、フォールスルー動作を意図 (または、コードを読むすべてのユーザーに) コンパイラにヒントとして。 Visual C コンパイラ現在は、警告、fallthrough 動作ため、この属性はコンパイラの動作に影響を与えません。 属性をラベル付きステートメント内で空のステートメントに適用されるに注意してください。つまり、セミコロンは必要があります。

```cpp
int main()
{
    int n = 5;
    switch (n)
    {

    case 1:
        a();
        break;
    case 2:
        b();
        d();
        [[fallthrough]]; // I meant to do this!
    case 3:
        c();
        break;
    default:
        d();
        break;
    }

    return 0;
}
```

**Visual Studio 2017 バージョン 15.3 以降**(で使用可能な[/std:c + + 17](../build/reference/std-specify-language-standard-version.md)): switch ステートメントが紹介し、スコープは、switch ステートメントのブロックに限定する変数を初期化する場合があります。

```cpp
    switch (Gadget gadget(args); auto s = gadget.get_status())
    {
    case status::good:
        gadget.zip();
        break;
    case status::bad:
        throw BadGadget();
    };
```

内側のブロックを**切り替える**が到達可能な限り、ステートメントで初期化の定義を含めることができます: ないは、すべての実行可能なパスではバイパスされます。 これらの宣言を使用して導入された名前にはローカル スコープがあります。 例えば:

```cpp
// switch_statement2.cpp
// C2360 expected
#include <iostream>
using namespace std;
int main(int argc, char *argv[])
{
    switch( tolower( *argv[1] ) )
    {
        // Error. Unreachable declaration.
        char szChEntered[] = "Character entered was: ";

    case 'a' :
        {
        // Declaration of szChEntered OK. Local scope.
        char szChEntered[] = "Character entered was: ";
        cout << szChEntered << "a\n";
        }
        break;

    case 'b' :
        // Value of szChEntered undefined.
        cout << szChEntered << "b\n";
        break;

    default:
        // Value of szChEntered undefined.
        cout << szChEntered << "neither a nor b\n";
        break;
    }
}
```

A**切り替える**ステートメントは入れ子にできます。 このような場合、**ケース**または**既定**ラベルは、最も近いと関連付ける**切り替える**そのすぐ外側のステートメント。

**Microsoft 固有の仕様**

Microsoft C では、case 値の数は制限されませんが、**切り替える**ステートメント。 この数は、使用できるメモリによってのみ制限されます。 ANSI C には、少なくとも 257 が必要がありますの case ラベルを使用できる、**切り替える**ステートメント。

Microsoft C の既定では、Microsoft 拡張機能が有効になっています。 使用して、 [/Za](../build/reference/za-ze-disable-language-extensions.md)コンパイラ オプションは、これらの拡張機能を無効にします。

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[選択ステートメント](../cpp/selection-statements-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)