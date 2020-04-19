---
title: nothrow_t 構造体
ms.date: 11/04/2016
f1_keywords:
- nothrow_t
helpviewer_keywords:
- nothrow_t class
ms.assetid: dc7d5d42-ed5a-4919-88fe-bbad519b7a1d
ms.openlocfilehash: bd65b5006326850522a251cbcf7d655133a1aa8a
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68245576"
---
# <a name="nothrowt-structure"></a>nothrow_t 構造体

この構造体は operator new の関数パラメーターとして使用し、関数に対して、割り当て失敗を報告する際に例外をスローするのではなく Null ポインター を返すように指定します。

## <a name="syntax"></a>構文

```cpp
struct std::nothrow_t {};
```

## <a name="remarks"></a>Remarks

この構造体により、コンパイラが適切なバージョンのコンストラクターを選択できます。 [nothrow](../standard-library/new-functions.md#nothrow) は、`std::nothrow_t` 型のオブジェクトと同義です。

## <a name="example"></a>例

`std::nothrow_t` を関数パラメーターとして使用する方法の例については、[operator new](../standard-library/new-operators.md#op_new) および [operator new&#91;&#93;](../standard-library/new-operators.md#op_new_arr) に関する記事をご覧ください。
