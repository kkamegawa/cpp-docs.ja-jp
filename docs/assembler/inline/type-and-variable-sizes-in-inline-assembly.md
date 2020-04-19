---
title: インライン アセンブリでの型と変数サイズ
ms.date: 08/30/2018
ms.topic: reference
f1_keywords:
- length
- Type
helpviewer_keywords:
- variables, length
- size, getting in inline assembly
- size
- LENGTH operator
- TYPE operator
- SIZE operator
- inline assembly, operators
- variables, type
- variables, size
ms.assetid: b62c2f2b-a7ad-4145-bae4-d890db86d348
ms.openlocfilehash: 36c97ee866ca449e9bbcf514e464a13f24f12cd9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62166894"
---
# <a name="type-and-variable-sizes-in-inline-assembly"></a>インライン アセンブリでの型と変数サイズ

**Microsoft 固有の仕様**

**LENGTH**、**SIZE**、および**TYPE**演算子は、インライン アセンブリで制限の意味を持ちます。 まったく使用できません、`DUP`演算子 (MASM ディレクティブまたは演算子を使用してデータを定義することはできません) ためです。 ただし、それらを使用して、C または C++ の変数または型のサイズを確認することができます。

- **LENGTH**演算子は、配列内の要素の数を返すことができます。 配列でない変数の場合値 1 を返します。

- **SIZE**演算子は、C または C++ の変数のサイズを返すことができます。 変数のサイズは、**LENGTH**と**TYPE**の積です。

- **TYPE**演算子は、C または C++ の型または変数のサイズを返すことができます。 変数が配列では、**TYPE**配列の 1 つの要素のサイズを返します。

たとえば、プログラムに 8-要素**int**配列

```cpp
int arr[8];
```

C およびアセンブリの式は次のサイズの返さ`arr`とその要素。

|__asm|C|サイズ|
|-------------|-------|----------|
|**LENGTH** arr|`sizeof`(arr)/`sizeof`(arr[0])|8|
|**SIZE** arr|`sizeof`(arr)|32|
|**TYPE** arr|`sizeof`(arr[0])|4|

**Microsoft 固有の仕様はここまで**

## <a name="see-also"></a>関連項目

[__asm ブロックでのアセンブリ言語の使用](../../assembler/inline/using-assembly-language-in-asm-blocks.md)<br/>
