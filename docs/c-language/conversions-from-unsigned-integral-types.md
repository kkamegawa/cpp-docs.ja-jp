---
title: 符号なし整数型からの変換
ms.date: 10/02/2019
helpviewer_keywords:
- integers, converting
- type casts, involving integers
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
- integral conversions, from unsigned
ms.assetid: 60fb7e10-bff9-4a13-8a48-e19f25a36a02
ms.openlocfilehash: 3099f0113103223e392dc20560899b4a6e3ebf20
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998789"
---
# <a name="conversions-from-unsigned-integral-types"></a>符号なし整数型からの変換

符号なし整数を整数または浮動小数点型に変換すると、元の値が結果の型で表現可能な場合、値は変更されません。

符号なし整数を大きなサイズの整数に変換する場合、値はゼロ拡張になります。 小さいサイズの整数に変換する場合、上位ビットは切り捨てられます。 結果は、次の例に示すように、結果の型を使用して解釈されます。

```C
unsigned k = 65533;
short j;

j = k;
printf_s( "%hd\n", j );   // Prints -3
```

符号なし整数を浮動小数点型に変換するとき、元の値を結果の型で正確に表すことができない場合、結果は次の上位または小さい表現可能な値になります。

整数型と浮動小数点型のサイズについては、「[基本型の格納](../c-language/storage-of-basic-types.md)」を参照してください。

**Microsoft 固有の仕様**

Microsoft コンパイラでは、**符号**なし (符号**なし int**) と**unsigned long**は区別されますが、同等の型です。 **unsigned int** 値の変換は、**unsigned long** の変換と同様に実行されます。

**Microsoft 固有の仕様はここまで**

次の表は、符号なし整数型からの変換をまとめたものです。

## <a name="table-of-conversions-from-unsigned-integral-types"></a>符号なし整数型からの変換のテーブル

|From|目的|メソッド|
|----------|--------|------------|
|**unsigned char**|**char**|ビット パターンを維持、上位ビットが符号ビットになる。|
|**unsigned char**|**short**|ゼロ拡張。|
|**unsigned char**|**long**|ゼロ拡張。|
|**unsigned char**|**long long**|ゼロ拡張。|
|**unsigned char**|**unsigned short**|ゼロ拡張。|
|**unsigned char**|**unsigned long**|ゼロ拡張。|
|**unsigned char**|**unsigned long long**|ゼロ拡張。|
|**unsigned char**|**float**|**long** への変換、**long** から **float** への変換。|
|**unsigned char**|**double**|**long** への変換、**long** から **double** への変換。|
|**unsigned char**|**long double**|**long** への変換、**long** から **double** への変換。|
|**unsigned short**|**char**|下位バイトを維持。|
|**unsigned short**|**short**|ビット パターンを維持、上位ビットが符号ビットになる。|
|**unsigned short**|**long**|ゼロ拡張。|
|**unsigned short**|**long long**|ゼロ拡張。|
|**unsigned short**|**unsigned char**|下位バイトを維持。|
|**unsigned short**|**unsigned long**|ゼロ拡張。|
|**unsigned short**|**unsigned long long**|ゼロ拡張。|
|**unsigned short**|**float**|**long** への変換、**long** から **float** への変換。|
|**unsigned short**|**double**|**long** への変換、**long** から **double** への変換。|
|**unsigned short**|**long double**|**long** への変換、**long** から **double** への変換。|
|**unsigned long**|**char**|下位バイトを維持。|
|**unsigned long**|**short**|下位ワードを維持。|
|**unsigned long**|**long**|ビット パターンを維持、上位ビットが符号ビットになる。|
|**unsigned long**|**long long**|ゼロ拡張。|
|**unsigned long**|**unsigned char**|下位バイトを維持。|
|**unsigned long**|**unsigned short**|下位ワードを維持。|
|**unsigned long**|**unsigned long long**|ゼロ拡張。|
|**unsigned long**|**float**|**long** への変換、**long** から **float** への変換。|
|**unsigned long**|**double**|**double** への直接変換。|
|**unsigned long**|**long double**|**long** への変換、**long** から **double** への変換。|
|**unsigned long long**|**char**|下位バイトを維持。|
|**unsigned long long**|**short**|下位ワードを維持。|
|**unsigned long long**|**long**|下位 dword の保持|
|**unsigned long long**|**long long**|ビット パターンを維持、上位ビットが符号ビットになる。|
|**unsigned long long**|**unsigned char**|下位バイトを維持。|
|**unsigned long long**|**unsigned short**|下位ワードを維持。|
|**unsigned long long**|**unsigned long**|下位 dword の保持|
|**unsigned long long**|**float**|**long** への変換、**long** から **float** への変換。|
|**unsigned long long**|**double**|**double** への直接変換。|
|**unsigned long long**|**long double**|**long** への変換、**long** から **double** への変換。|

## <a name="see-also"></a>関連項目

[割り当ての変換](../c-language/assignment-conversions.md)
