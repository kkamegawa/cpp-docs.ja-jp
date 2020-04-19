---
title: 単純変数の宣言
ms.date: 11/04/2016
helpviewer_keywords:
- untyped variables
- declaring variables, simple
ms.assetid: b07adf9d-9e79-4b64-8a34-e6fe1c7eccec
ms.openlocfilehash: 27710dabe512332564ee557a9d022457d9fddc5c
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149987"
---
# <a name="simple-variable-declarations"></a>単純変数の宣言

直接宣言の最も単純な形式である単純変数の宣言は、変数名と型を指定します。 また、変数のストレージ クラスとデータ型を指定します。

ストレージ クラス、型、またはこの両方が変数宣言に必要です。 型指定されていない変数 (`var;` など) は警告を生成します。

## <a name="syntax"></a>構文

*declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*pointer*<sub>opt</sub> *direct-declarator*

*direct-declarator*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier*

*identifier*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *nondigit*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifier* *digit*

演算型、構造体型、共用体型、列挙型、void 型、および `typedef` の名前によって表される型については、型指定子がすべての型情報を提供するため、単純な宣言子を宣言で使用できます。 ポインター型、配列型、および関数型では、より複雑な宣言子が必要です。

同じ宣言で複数の変数を指定するために、コンマ (**,**) で区切られた識別子のリストを使用できます。 宣言で定義されているすべての変数に、同じ基本型があります。 次に例を示します。

```C
int x, y;        /* Declares two simple variables of type int */
int const z = 1; /* Declares a constant value of type int */
```

変数 `x` および `y` は、特定の実装の `int` 型で定義されるセットに任意の値を保持できます。 簡単なオブジェクト `z` は値 1 に初期化され、変更できません。

`z` の宣言の対象が初期化されていない静的変数であるか、宣言がファイル スコープで行われた場合、初期値 0 を受け取り、その値は変更できません。

```C
unsigned long reply, flag; /* Declares two variables
                              named reply and flag     */
```

この例では、両方の変数 (`reply` と `flag`) は `unsigned long` 型を持ち、符号なし整数値を保持します。

## <a name="see-also"></a>関連項目

[宣言子と変数宣言](../c-language/declarators-and-variable-declarations.md)
