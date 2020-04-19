---
title: 関数呼び出し (C)
ms.date: 11/04/2016
helpviewer_keywords:
- function calls, C functions
- functions [C], calling
- function calls
ms.assetid: 35c66719-3f15-4d3b-97da-4e19dc97b308
ms.openlocfilehash: d22bdebc8fa832afb14a2cc09e6a441b7b9e8a5a
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147413"
---
# <a name="function-call-c"></a>関数呼び出し (C)

"*関数呼び出し*" は、呼び出される関数の名前または関数ポインターの値と、必要に応じて関数に渡される引数を含む式です。

## <a name="syntax"></a>構文

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **(**  *argument-expression-list*<sub>opt</sub> **)**

*argument-expression-list*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*assignment-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*argument-expression-list* **,** *assignment-expression*

*postfix-expression* は、関数アドレス (たとえば、関数の識別子または関数ポインターの値) に評価される必要があります。*argument-expression-list* は、式の (コンマ区切りの) リストで、各式の値 ("引数") が関数に渡されます。 *argument-expression-list* 引数は空の場合もあります。

関数呼び出しの式は、関数の戻り値の値と型を持ちます。 関数は配列型のオブジェクトを返すことができません。 関数の戻り値の型が `void` (つまり、値を返さない関数であると宣言されている) の場合、関数呼び出し式も `void` 型になります  (詳細については、「[関数呼び出し](../c-language/function-calls.md)」を参照してください)。

## <a name="see-also"></a>関連項目

[関数呼び出し演算子: ()](../cpp/function-call-operator-parens.md)
