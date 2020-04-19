---
title: for ステートメント (C++)
ms.date: 11/04/2016
helpviewer_keywords:
- for keyword [C++]
ms.assetid: 6c7d01b3-c4c1-4c6a-aa58-e2d198f33d4a
ms.openlocfilehash: a6b1823fe93c45abd8dabbd22116924e0a64f19a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154218"
---
# <a name="for-statement-c"></a>for ステートメント (C++)

条件が偽 (false) になるまでステートメントを繰り返し実行します。 範囲ベースの for ステートメントについては、次を参照してください。[ステートメント (C++) の範囲に基づく](../cpp/range-based-for-statement-cpp.md)します。

## <a name="syntax"></a>構文

```
for ( init-expression ; cond-expression ; loop-expression )
    statement;
```

## <a name="remarks"></a>Remarks

使用して、**for**ステートメントを指定した回数だけを実行する必要がありますのあるループを構築します。

**for**次の表に示すように、次の 3 つの省略可能な部分のステートメントで構成されます。

### <a name="for-loop-elements"></a>for ループ要素

|構文の名前|実行タイミング|説明|
|-----------------|-------------------|-----------------|
|`init-expression`|他の要素の前に、**for**ステートメントでは、`init-expression`は一度だけ実行します。 その後、制御は `cond-expression` に渡されます。|ループ インデックスを初期化するためによく使用されます。 式または宣言を含めることができます。|
|`cond-expression`|最初のイテレーションを含む `statement` の各イテレーションの実行前。 `statement` は、`cond-expression` が true (0 以外) に評価された場合にのみ実行されます。|整数型に評価される式、または整数型へのあいまいでない変換が行われるクラス型。 通常、for ループの終了条件をテストするために使用します。|
|`loop-expression`|`statement` の各イテレーションの終了時。 `loop-expression` の実行後に `cond-expression` が実行されます。|通常、ループ インデックスのインクリメントに使用します。|

次の例では、さまざまな方法を使用する、**for**ステートメント。

```cpp
#include <iostream>
using namespace std;

int main() {
    // The counter variable can be declared in the init-expression.
    for (int i = 0; i < 2; i++ ){
       cout << i;
    }
    // Output: 01
    // The counter variable can be declared outside the for loop.
    int i;
    for (i = 0; i < 2; i++){
        cout << i;
    }
    // Output: 01
    // These for loops are the equivalent of a while loop.
    i = 0;
    while (i < 2){
        cout << i++;
    }
}
    // Output: 012
```

`init-expression` と `loop-expression` には、コンマで区切った複数のステートメントを含めることができます。 例えば:

```cpp
#include <iostream>
using namespace std;

int main(){
    int i, j;
    for ( i = 5, j = 10 ; i + j < 20; i++, j++ ) {
        cout << "i + j = " << (i + j) << '\n';
    }
}
    // Output:
    i + j = 15
    i + j = 17
    i + j = 19
```

`loop-expression` はインクリメントまたはデクリメントするか、他の方法で変更することができます。

```cpp
#include <iostream>
using namespace std;

int main(){
for (int i = 10; i > 0; i--) {
        cout << i << ' ';
    }
    // Output: 10 9 8 7 6 5 4 3 2 1
    for (int i = 10; i < 20; i = i+2) {
        cout << i << ' ';
    }
    // Output: 10 12 14 16 18
```

**for**ループが終了したときに、 [break](../cpp/break-statement-cpp.md)、[return](../cpp/return-statement-cpp.md)、または[goto](../cpp/goto-statement-cpp.md) (外側のラベルの付いたステートメントに対する、 **for**ループ) 内で`statement`を実行します。 A[continue](../cpp/continue-statement-cpp.md)内のステートメントを**for**ループは、現在のイテレーションのみを終了します。

`cond-expression`を省略すると true と見なされ、`statement` 内で **break**、**return**、または**goto** をしない限り **for** ループは終了しません。

3 つのフィールドの**for**ステートメントは通常、終了のテストの初期化を使用し、インクリメントはこれらの用途に制限します。 たとえば、次のコードは、数値 0 ～ 4 を出力します。 この場合、`statement` は null ステートメントです。

```cpp
#include <iostream>
using namespace std;

int main()
{
    int i;
    for( i = 0; i < 5; cout << i << '\n', i++){
        ;
    }
}
```

## <a name="for-loops-and-the-c-standard"></a>for ループおよび C++ 標準

C++ 標準で宣言された変数を**for**後にスコープ外に出るループ、**for**ループが終了します。 例えば:

```cpp
for (int i = 0 ; i < 5 ; i++) {
   // do something
}
// i is now out of scope under /Za or /Zc:forScope
```

既定では、 [/Ze](../build/reference/za-ze-disable-language-extensions.md)で宣言された変数を**for**までスコープ内にループが残り、**for**ループの外側のスコープが終了します。

[/Zc:forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)を指定せずに for ループで宣言された変数の標準動作を有効に`/Za`します。

スコープの相違点を使用することも、**for**ループの下で変数を再宣言を`/Ze`次のようにします。

```cpp
// for_statement5.cpp
int main(){
   int i = 0;   // hidden by var with same name declared in for loop
   for ( int i = 0 ; i < 3; i++ ) {}

   for ( int i = 0 ; i < 3; i++ ) {}
}
```

宣言された変数の標準の動作をより正確に模倣これを**for**ループで宣言された変数が必要です、**for**ループを使用して、ループが完了した後にスコープ外に移動します。 変数が宣言されている場合、**for**ループ コンパイラ内部的に引き上げますでローカル変数を**for**ループの外側のスコープと同じ名前のローカル変数が既にある場合でもです。

## <a name="see-also"></a>関連項目

[繰り返しステートメント](../cpp/iteration-statements-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)<br/>
[while ステートメント (C++)](../cpp/while-statement-cpp.md)<br/>
[do-while ステートメント (C++)](../cpp/do-while-statement-cpp.md)<br/>
[範囲ベースの for ステートメント (C++)](../cpp/range-based-for-statement-cpp.md)