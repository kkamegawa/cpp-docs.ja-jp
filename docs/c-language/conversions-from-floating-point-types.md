---
title: 浮動小数点型からの変換
ms.date: 10/02/2019
helpviewer_keywords:
- converting floating point
- floating-point conversion
ms.assetid: 96804c8e-fa3b-4742-9006-0082ed9e57f2
ms.openlocfilehash: c2f7c25015b36545f969796a1f85d355d715427a
ms.sourcegitcommit: c51b2c665849479fa995bc3323a22ebe79d9d7ce
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/07/2019
ms.locfileid: "71998715"
---
# <a name="conversions-from-floating-point-types"></a>浮動小数点型からの変換

別の浮動小数点型に変換された浮動小数点値では、元の値が結果の型で正確に表現できる場合、値が変更されることはありません。 元の値が数値であっても、正確に表現できない場合、結果は、次に大きい方または次に表現可能な値のいずれかになります。 浮動小数点型の範囲については、「[浮動小数点定数の制限](../c-language/limits-on-floating-point-constants.md)」を参照してください。

整数型に変換される浮動小数点値は、小数値を破棄することによって最初に切り捨てられます。 この切り捨てられた値が結果の型で表現できる場合、結果はその値である必要があります。 表現できない場合、結果の値は未定義になります。

**Microsoft 固有の仕様**

Microsoft コンパイラは、 **float**値に対して IEEE-754 binary32 表現を使用し、 **long double**と**double**の binary64 表現を使用します。 **Long double**と**double**では同じ表現が使用されるため、同じ範囲と有効桁数が使用されます。

コンパイラは、 **double**または**long double**浮動小数点数を**float**に変換するときに、浮動小数点環境コントロールに従って結果を丸めます。既定では、"近似値への丸めが行われます" になります。 数値の**浮動小数点**値として表現できない数値が大きすぎるか小さすぎる場合、変換結果は、元の値の符号に従って正または負の無限大になり、オーバーフロー例外が発生します (有効になっている場合)。

整数型に変換する場合、 **long**よりも小さい型への変換の結果は、値を**long**に変換してから結果の型に変換した結果になります。

少なくとも1つの整数型に変換する**場合、結果**の型で表現できない値を変換すると、次のいずれかの値が返される可能性があります。

- 結果は、0から最も遠い表現可能な値である*sentinel 値*である可能性があります。 符号付きの型の場合、これは最も低い表現可能な値 (0x800...0)。 符号なしの型の場合は、表現可能な最大値 (0xFF...F)。

- 結果は*飽和*状態になる可能性があります。値が大きすぎて表すことができる最大値に変換され、表現するには小さすぎる値が表現可能な最も小さい値に変換されます。 これら2つの値のいずれかが、sentinel 値としても使用されます。

- **Unsigned** long または**unsigned long long 型**に変換する場合、範囲外の値を変換した結果として、表現可能な値の上限または下限以外の値が使用されることがあります。 結果が sentinel または飽和値であるかどうかは、コンパイラオプションとターゲットアーキテクチャによって異なります。 将来のコンパイラリリースでは、飽和状態または sentinel 値が返される場合があります。

**Microsoft 固有の仕様はここまで**

次の表は、浮動小数点型から変換をまとめたものです。

## <a name="table-of-conversions-from-floating-point-types"></a>浮動小数点型からの変換の表

|From|目的|メソッド|
|----------|--------|------------|
|**float**|**char**|**long** への変換、**long** から **char** への変換|
|**float**|**short**|**long** への変換、**long** から **short** への変換|
|**float**|**int**|小数点で切り捨てます。 結果が大きすぎて**int**として表現できない場合、結果は未定義になります。|
|**float**|**long**|小数点で切り捨てます。 結果が **long** で表すには大きすぎる場合、結果は未定義になります。|
|**float**|**long long**|小数点で切り捨てます。 結果が大きすぎて**long 型**として表現できない場合、結果は未定義になります。|
|**float**|**unsigned char**|**Long**への変換**long**から**unsigned char**への変換|
|**float**|**unsigned short**|**long** への変換、**long** から **unsigned short** への変換|
|**float**|**unsigned**|小数点で切り捨てます。 結果が大きすぎて**符号なし**として表現できない場合、結果は未定義になります。|
|**float**|**unsigned long**|小数点で切り捨てます。 結果が大きすぎて**unsigned long 型**として表現できない場合、結果は未定義になります。|
|**float**|**unsigned long long**|小数点で切り捨てます。 結果が大きすぎて**unsigned long long 型**として表現できない場合、結果は未定義になります。|
|**float**|**double**|**Double**として表されます。|
|**float**|**long double**|**Long double**として表されます。|
|**double**|**char**|**float** への変換、**float** から **char** への変換|
|**double**|**short**|**float** への変換、**float** から **short** への変換|
|**double**|**int**|小数点で切り捨てます。 結果が大きすぎて**int**として表現できない場合、結果は未定義になります。|
|**double**|**long**|小数点で切り捨てます。 結果が **long** で表すには大きすぎる場合、結果は未定義になります。|
|**double**|**unsigned char**|**Long**への変換**long**から**unsigned char**への変換|
|**double**|**unsigned short**|**long** への変換、**long** から **unsigned short** への変換|
|**double**|**unsigned**|小数点で切り捨てます。 結果が大きすぎて**符号なし**として表現できない場合、結果は未定義になります。|
|**double**|**unsigned long**|小数点で切り捨てます。 結果が大きすぎて**unsigned long 型**として表現できない場合、結果は未定義になります。|
|**double**|**unsigned long long**|小数点で切り捨てます。 結果が大きすぎて**unsigned long long 型**として表現できない場合、結果は未定義になります。|
|**double**|**float**|**float** として表します。 **Double**値を**float**として正確に表すことができない場合、精度が低下します。 値が **float** で表すには大きすぎる場合、結果は未定義になります。|
|**double**|**long double**|**long double** 値は **double** として扱われます。|

**Long double 型**からの変換は、 **double**型からの変換と同じメソッドに従います。

## <a name="see-also"></a>関連項目

[割り当ての変換](../c-language/assignment-conversions.md)
