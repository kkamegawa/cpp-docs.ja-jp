---
title: return ステートメント (C++)
ms.date: 11/04/2016
f1_keywords:
- return_cpp
helpviewer_keywords:
- return keyword [C++], syntax
- return keyword [C++]
ms.assetid: a498903a-056a-4df0-a6cf-72f633a62210
ms.openlocfilehash: 47bf9c50a2da039b0ffa074796a768290b732bb3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62268539"
---
# <a name="return-statement-c"></a>return ステートメント (C++)

関数の実行を終了し、呼び出し元の関数 (`main` 関数から制御を転送する場合はオペレーティング システム) に制御を返します。 呼び出し直後の位置から、呼び出し元の関数で実行が再開します。

## <a name="syntax"></a>構文

```
return [expression];
```

## <a name="remarks"></a>Remarks

`expression` 句は、存在する場合、初期化が実行されたときと同様に、関数宣言で指定された型に変換されます。 式の型からの変換、**return**関数の型は、一時オブジェクトを作成できます。 一時要素を作成する方法とタイミングの詳細については、次を参照してください。[一時オブジェクト](../cpp/temporary-objects.md)します。

`expression` 句の値が呼び出し元の関数に返されます。 expression が省略されている場合、関数の戻り値は未定義です。 コンス トラクターとデストラクター、および関数型の**void**で式を指定することはできません、**return**ステートメント。 その他のすべての種類の関数で式を指定する必要があります、**return**ステートメント。

コントロールのフローでは、関数定義の外側のブロックを終了すると、結果は同じになること場合、**return**式ステートメントが実行されている必要があります。 これは、値を返すように宣言された関数では無効です。

関数は、任意の数を持つことができます**return**ステートメント。

次の例の式を使用して、**return**最大規模の 2 つの整数を取得するステートメント。

## <a name="example"></a>例

```cpp
// return_statement2.cpp
#include <stdio.h>

int max ( int a, int b )
{
   return ( a > b ? a : b );
}

int main()
{
    int nOne = 5;
    int nTwo = 7;

    printf_s("\n%d is bigger\n", max( nOne, nTwo ));
}
```

## <a name="see-also"></a>関連項目

[ジャンプ ステートメント](../cpp/jump-statements-cpp.md)<br/>
[キーワード](../cpp/keywords-cpp.md)