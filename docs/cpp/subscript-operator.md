---
title: 添字演算子
ms.date: 11/04/2016
f1_keywords:
- '[]'
helpviewer_keywords:
- operators [C++], subscript
- postfix operators [C++]
- '[] operator'
- subscript operator [C++], syntax
ms.assetid: 69c31494-52da-4dd0-8bbe-6ccbfd50f197
ms.openlocfilehash: 2d55c18d2c9faa1a704bea129f2551937e76133c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266895"
---
# <a name="subscript-operator-"></a>添字演算子

## <a name="syntax"></a>構文

```
postfix-expression [ expression ]
```

## <a name="remarks"></a>Remarks

(どの 1 次式もかまいません)、添字演算子が続く後置式 **[ ]** 配列のインデックスを指定します。

C++ のマネージ配列について/cli CLI を参照してください[配列](../extensions/arrays-cpp-component-extensions.md)します。

によって表される値は、通常、*後置式*配列識別子などのポインター値と*式*(列挙型を含む)、整数値です。 ただし、構文上必要なのは、一方の式がポインター型で、もう一方が整数型であることです。 整数値可能性がありますので、*後置式*位置とポインター値が角かっこ内にある可能性があります、*式*または添字の位置。 次のコードがあるとします。

```cpp
int nArray[5] = { 0, 1, 2, 3, 4 };
cout << nArray[2] << endl;            // prints "2"
cout << 2[nArray] << endl;            // prints "2"
```

上の例では、式 `nArray[2]` は `2[nArray]` と同じです。 理由の添字式は、結果は`e1[e2]`で指定されます。

`*((e2) + (e1))`

式によって見つかったアドレスが*e2*アドレスからのバイト*e1*します。 配列内の次のオブジェクトを生成するアドレスのスケールではなく、 *e2*します。 例:

```cpp
double aDbl[2];
```

アドレス`aDb[0]`と`aDb[1]`は 8 バイトを離れた-型のオブジェクトのサイズ**double**します。 オブジェクトの種類に基づくこのスケーリングは、C++ 言語によって自動的に行われで定義されている[加法演算子](../cpp/additive-operators-plus-and.md)ポインター型のオペランドの加算と減算が説明されています。

添字式には、次のように複数の添字がある場合があります。

*expression1* **[** *expression2* **] [** *expression3* **]** ...

添字式は、左から右へ関連付けられます。 左端の添字式、*expression1* **[** *expression2* **]** が最初に評価されます。 *expression1* と *expression2* を加算した結果として得られるアドレスからポインター式が形成され、次にこのポインター式に *expression3* が加算されて新しいポインター式が形成されます。このようにして、最後の添字式が加算されるまで処理が行われます。 間接演算子 (<strong>\*</strong>) 最終的なポインター値が配列型に対応しない限り、最後の添字式が評価された後に適用します。

複数の添字を持つ式は、多次元配列の要素を参照します。 多次元配列は、要素が配列である配列です。 たとえば、3 次元配列の最初の要素は 2 次元配列です。 次の例では、文字の単純な 2 次元配列を宣言して初期化しています。

```cpp
// expre_Subscript_Operator.cpp
// compile with: /EHsc
#include <iostream>

using namespace std;
#define MAX_ROWS 2
#define MAX_COLS 2

int main() {
  char c[ MAX_ROWS ][ MAX_COLS ] = { { 'a', 'b' }, { 'c', 'd' } };
  for ( int i = 0; i < MAX_ROWS; i++ )
     for ( int j = 0; j < MAX_COLS; j++ )
        cout << c[ i ][ j ] << endl;
}
```

## <a name="positive-and-negative-subscripts"></a>正と負の添字

配列の最初要素は要素 0 です。 範囲をC++配列*配列*[0] に*配列*[*サイズ*- 1] です。 ただし、C++ は、正の数の添字と負の数の添字をサポートします。 負の添字は配列の範囲内になる必要があり、そうでない場合、結果は予測不能となります。 次のコードは正および負の配列添字を示します。

```cpp
#include <iostream>
using namespace std;

int main() {
    int intArray[1024];
    for (int i = 0, j = 0; i < 1024; i++)
    {
        intArray[i] = j++;
    }

    cout << intArray[512] << endl;   // 512

    cout << 257[intArray] << endl;   // 257

    int *midArray = &intArray[512];  // pointer to the middle of the array

    cout << midArray[-256] << endl;  // 256

    cout << intArray[-256] << endl;  // unpredictable, may crash
}
```

最後の行の負の添字が 256 のアドレスを指しているため、実行時エラーを生成できる**int**配列の元よりもメモリに低い位置。 ポインター`midArray`の中央に初期化されます`intArray`; はそのためできます (ただし、危険な) 両方正と負の値の配列のインデックスを使用します。 配列添字のエラーは、コンパイル時のエラーを生成しませんが、予測できない結果になります。

添字演算子は可換です。 したがって、式*配列*[*インデックス*] と*インデックス*[*配列*]、添字限り等価であることが保証されます演算子はオーバー ロードされない (を参照してください[オーバー ロードされた演算子](../cpp/operator-overloading.md))。 最初の形式は、共通のコーディングの推奨事項ですが、どちらの方法でも動作します。

## <a name="see-also"></a>関連項目

[後置式](../cpp/postfix-expressions.md)<br/>
[C++ の組み込み演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)<br/>
[配列](../cpp/arrays-cpp.md)<br/>
[1 次元配列](../c-language/one-dimensional-arrays.md)<br/>
[多次元配列](../c-language/multidimensional-arrays-c.md)<br/>
