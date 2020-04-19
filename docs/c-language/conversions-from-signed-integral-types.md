---
title: 符号付き整数型からの変換
ms.date: 10/02/2019
helpviewer_keywords:
- integral conversions, from signed
- integers, converting
- conversions [C++], integral
- data type conversion [C++], signed and unsigned integers
- type conversion [C++], signed and unsigned integers
ms.assetid: 5eea32f8-8b14-413d-acac-c063b3d118d7
ms.openlocfilehash: 79608b5ca4335ee3c30bdab27e7efade5b7e2f54
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998724"
---
# <a name="conversions-from-signed-integral-types"></a>符号付き整数型からの変換

符号付き整数が整数または浮動小数点型に変換されるときに、元の値が結果の型で表現可能な場合、値は変更されません。

符号付き整数が大きなサイズの整数に変換されると、その値は符号拡張になります。 小さいサイズの整数に変換されると、上位ビットは切り捨てられます。 結果は、次の例に示すように、結果の型を使用して解釈されます。

```C
int i = -3;
unsigned short u;

u = i;
printf_s( "%hu\n", u );  // Prints 65533
```

符号付き整数を浮動小数点型に変換するときに、元の値が結果の型で正確に表現できない場合、結果は次の上位または小さい表現可能な値になります。

整数型と浮動小数点型のサイズの詳細については、「[基本型の格納](../c-language/storage-of-basic-types.md)」を参照してください。

次の表は、符号付き整数型からの変換をまとめたものです。 **Char**型が既定で符号付きであることを前提としています。 コンパイル時オプションを使用して**char**型の既定値を unsigned に変更すると、このテーブルの変換ではなく、符号なし[整数型](../c-language/conversions-from-unsigned-integral-types.md)のテーブルから**unsigned char**型への変換で指定された変換が適用されます。

**Microsoft 固有の仕様**

Microsoft コンパイラでは、 **int**と**long**は異なるが等価な型です。 **Int**値の変換は、 **long**の変換と同じ方法で行われます。

**Microsoft 固有の仕様はここまで**

## <a name="table-of-conversions-from-signed-integral-types"></a>符号付き整数型からの変換のテーブル

|From|目的|メソッド|
|----------|--------|------------|
|**char**<sup>1</sup>|**short**|符号拡張。|
|**char**|**long**|符号拡張。|
|**char**|**long long**|符号拡張。|
|**char**|**unsigned char**|パターンを維持、上位ビットは符号ビットとしての機能を失う。|
|**char**|**unsigned short**|**short** への符号拡張、**short** から **unsigned short** への変換|
|**char**|**unsigned long**|**long** への符号拡張、**long** から **unsigned long** への変換|
|**char**|**unsigned long long**|**Long long**への符号拡張。long **long から** **unsigned long** long への変換|
|**char**|**float**|**long** への符号拡張、**long** から **float** への変換|
|**char**|**double**|**long** への符号拡張、**long** から **double** への変換|
|**char**|**long double**|**long** への符号拡張、**long** から **double** への変換|
|**short**|**char**|下位バイトを維持。|
|**short**|**long**|符号拡張。|
|**short**|**long long**|符号拡張。|
|**short**|**unsigned char**|下位バイトを維持。|
|**short**|**unsigned short**|ビット パターンを維持、上位ビットは符号ビットとしての機能を失う。|
|**short**|**unsigned long**|**long** への符号拡張、**long** から **unsigned long** への変換|
|**short**|**unsigned long long**|**Long long**への符号拡張。long **long から** **unsigned long** long への変換|
|**short**|**float**|**long** への符号拡張、**long** から **float** への変換|
|**short**|**double**|**long** への符号拡張、**long** から **double** への変換|
|**short**|**long double**|**long** への符号拡張、**long** から **double** への変換|
|**long**|**char**|下位バイトを維持。|
|**long**|**short**|下位ワードを維持。|
|**long**|**long long**|符号拡張。|
|**long**|**unsigned char**|下位バイトを維持。|
|**long**|**unsigned short**|下位ワードを維持。|
|**long**|**unsigned long**|ビット パターンを維持、上位ビットは符号ビットとしての機能を失う。|
|**long**|**unsigned long long**|**Long long**への符号拡張。long **long から** **unsigned long** long への変換|
|**long**|**float**|**float** として表される。 **Long**を正確に表すことができない場合、精度が失われます。|
|**long**|**double**|**double** として表される。 **Long**を**double**として正確に表すことができない場合、精度が低下する可能性があります。|
|**long**|**long double**|**double** として表される。 **Long**を**double**として正確に表すことができない場合、精度が低下する可能性があります。|
|**long long**|**char**|下位バイトを維持。|
|**long long**|**short**|下位ワードを維持。|
|**long long**|**long**|下位 dword の保持|
|**long long**|**unsigned char**|下位バイトを維持。|
|**long long**|**unsigned short**|下位ワードを維持。|
|**long long**|**unsigned long**|下位 dword の保持|
|**long long**|**unsigned long long**|ビット パターンを維持、上位ビットは符号ビットとしての機能を失う。|
|**long long**|**float**|**float** として表される。 **Long long**を正確に表すことができない場合、精度が失われます。|
|**long long**|**double**|**double** として表される。 **Long long**を**double**として正確に表すことができない場合、精度が低下する可能性があります。|
|**long long**|**long double**|**double** として表される。 **Long long**を**double**として正確に表すことができない場合、精度が低下する可能性があります。|

<sup>1</sup>すべての**char**エントリは、 **char**型が既定で符号付きであることを前提としています。

## <a name="see-also"></a>関連項目

[割り当ての変換](../c-language/assignment-conversions.md)
