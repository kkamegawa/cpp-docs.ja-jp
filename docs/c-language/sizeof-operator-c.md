---
title: sizeof 演算子 (C)
ms.date: 11/04/2016
f1_keywords:
- sizeof
helpviewer_keywords:
- sizeof operator
ms.assetid: 70826d03-3451-41e4-bebb-a820ae66d53f
ms.openlocfilehash: 0bc0de5481cade10f89634d9e4ec78f4ec7b09f6
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149558"
---
# <a name="sizeof-operator-c"></a>sizeof 演算子 (C)

`sizeof` 演算子はオペランドの型のオブジェクトを格納するために必要なストレージの量をバイト単位で示します。 この演算子を使うと、コンピューターに依存するデータ サイズをプログラムで指定せずに済みます。

## <a name="syntax"></a>構文

```
sizeof unary-expression
sizeof ( type-name )
```

## <a name="remarks"></a>解説

オペランドは、*unary-expression* の識別子、または型のキャスト式 (つまり、かっこで囲まれた型指定子) のいずれかです。 *unary-expression* は、ビット フィールド オブジェクト、不完全な型、または関数指定子を表すことはできません。 結果は、符号なしの整数定数です。 標準ヘッダー STDDEF.H は、この型を **size_t** として定義します。

配列識別子に `sizeof` 演算子を適用した場合、結果は配列識別子によって表されるポインターのサイズではなく、配列全体のサイズとなります。

構造体/共用体の型名または構造体/共用体の ID に `sizeof` 演算子を適用した場合、結果は内部と末尾の埋め込みを含む構造体/共用体のバイト数となります。 このサイズには、構造体または共用体のメンバーをメモリ境界に配置するために使用される内部および末尾の埋め込みが含まれる場合があります。 したがって、結果は、個々のメンバーのストレージ要件を加算して計算されたサイズには必ずしも対応しません。

可変長配列が構造の最後の要素である場合、`sizeof` 演算子は配列のない構造体のサイズを返します。

```
buffer = calloc(100, sizeof (int) );
```

この例では、コンピューターごとに異なる `sizeof` のサイズを `int` という名前のランタイム関数に引数として渡すために、`calloc` 演算子を使用します。 関数によって返された値は `buffer` に格納されます。

```
static char *strings[] = {
      "this is string one",
      "this is string two",
      "this is string three",
   };
const int string_no = ( sizeof strings ) / ( sizeof strings[0] );
```

この例では、`strings` は  `char` へのポインターの配列です。 ポインターの数は、配列の要素の数ですが、指定されていません。 配列の要素数を計算するために `sizeof` 演算子を使用して、ポインターの数を決定する方が簡単です。 **const** の整数値 `string_no` は、この数に初期化されます。 これは **const** 値であるため、`string_no` は変更できません。

## <a name="see-also"></a>関連項目

[C 演算子](c-operators.md)<br/>
[C++ の演算子、優先順位と結合規則](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
