---
title: 組み込み型 (C++)
ms.date: 12/11/2019
f1_keywords:
- __int128_cpp
- __wchar_t_cpp
- char_cpp
- double_cpp
- float_cpp
- int_cpp
- long_cpp
- long_double_cpp
- short_cpp
- signed_cpp
- unsigned_cpp
- unsigned_int_cpp
- wchar_t_cpp
helpviewer_keywords:
- specifiers [C++], type
- float keyword [C++]
- char keyword [C++]
- __wchar_t keyword [C++]
- signed types [C++], summary of data types
- Integer data type [C++], C++ data types
- arithmetic operations [C++], types
- int data type
- unsigned types [C++], summary of data types
- short data type [C++]
- double data type [C++], summary of types
- long long keyword [C++]
- long double keyword [C++]
- unsigned types [C++]
- signed types [C++]
- void keyword [C++]
- storage [C++], basic type
- integral types, C++
- wchar_t keyword [C++]
- floating-point numbers [C++], C++ data types
- long keyword [C++]
- type specifiers [C++]
- integral types
- long keyword [C++]
- storing types [C++]
- data types [C++], void
ms.assetid: 58b0106a-0406-4b74-a430-7cbd315c0f89
ms.openlocfilehash: f6bfc72bf279d09e89423866d9cb46ad3496b49c
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301497"
---
# <a name="built-in-types-c"></a>組み込み型 (C++)

組み込み型 (*基本型*とも呼ばれます) は、 C++言語標準によって指定され、コンパイラに組み込まれています。 組み込み型は、どのヘッダーファイルでも定義されていません。 組み込み型は、整数、浮動小数点、および void の3つのカテゴリに分類されます。 整数型は整数を処理できます。 浮動小数点型は小数部分を含む可能性がある値を指定することができます。

[void](void-cpp.md) 型は一連の空の値を示します。 **Void**型の変数は指定できません。これは主に、値を返さない関数を宣言したり、型指定されていないデータまたは任意の型のデータへのジェネリックポインターを宣言したりするために使用されます。 任意の式を明示的に変換するか、 **void**型にキャストできます。 ただし、このような式は次の用途に制限されています。

- 式ステートメント (詳細については、「[式](expressions-cpp.md)」を参照してください)。

- コンマ演算子の左のオペランド (詳細については、「[コンマ演算子](comma-operator.md)」を参照してください)。

- 条件演算子の 2 番目または 3 番目のオペランド (`? :`) (詳細については、「[条件演算子を使用した式](conditional-operator-q.md)」を参照してください)。

次の表では、相互に関連する型サイズの制限について説明します。 これらの制限は、 C++標準によって義務付けられており、Microsoft の実装に依存しません。 特定の組み込み型の絶対サイズが標準で指定されていません。

### <a name="built-in-type-size-restrictions"></a>組み込みの型サイズの制限

|[カテゴリ]|の型|目次|
|--------------|----------|--------------|
|整数型|**char**|型**char**は、通常、基本実行文字セットのメンバーを含む整数型です。既定では、これは Microsoft C++では ASCII です。<br /><br /> コンパイラC++は、 **char**、 **signed char**、 **unsigned char**型の変数を異なる型を持つものとして扱います。 **Char**型の変数は、/j コンパイルオプションが使用されていない限り、既定では**signed char**型であるかのように**int**に昇格されます。 この場合、これらは**unsigned char**型として扱われ、符号拡張なしで**int**に昇格されます。|
||**bool**|型**bool**は、 **true**または**false**の2つの値のいずれかを持つことができる整数型です。 そのサイズは、指定されていません。|
||**short**|型**short int** (または単に**short**) 型のサイズ以上である整数型は、 **char**、および型のサイズ以下**int**します。<br /><br /> 型のオブジェクト**short**として宣言できます**signed**または**unsigned short**します。 **signed short**は**short**のシノニムです。|
||**int**|型**int**型のサイズ以上である整数型は、 **short int**、およびよりもより短い、または型のサイズと等しく**long**します。<br /><br /> **Int**型のオブジェクトは、 **signed int**または**unsigned int**として宣言できます。**Signed int**は**int**のシノニムです。|
||**__int8**、 **__int16**、 **__int32**、 **__int64**|サイズが設定された整数 `__int n`( `n` は整数変数のビット単位のサイズ) **__int8**、 **__int16**、 **__int32** 、および **__int64**は、Microsoft 固有のキーワードです。 すべての型がすべてのアーキテクチャで使用できるわけではありません。 ( **__int128**はサポートされていません)。|
||**long**|**Long**型 (または**long int**) は、 **int**型のサイズ以上の整数型です。(Windows では**long**は**int**と同じサイズです)。<br /><br /> 型のオブジェクト**long**として宣言できます**signed long**または**unsigned long**します。 **signed long**のシノニムです**long**します。|
||**long long**|符号なしのよりも大きい**long**します。<br /><br /> 型のオブジェクト**long**として宣言できます**signed long long**または**unsigned long long**します。 **signed long long**のシノニムです**long**します。|
||**wchar_t**、 **__wchar_t**|**Wchar_t**型の変数はワイド文字またはマルチバイト文字型を指定します。 既定では、 **wchar_t**はネイティブ型ですが、 [/zc: wchar_t-](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)を使用して、 **unsigned short**の typedef **wchar_t**することができます。 **__Wchar_t**型は、ネイティブ**Wchar_t**型の Microsoft 固有のシノニムです。<br /><br /> ワイド文字型を指定するには、文字や文字列リテラルの前に L のプレフィックスを使用します。|
|浮動小数点数|**float**|型**float**は、最小の浮動小数点型です。|
||**double**|型**double**は**float**型以上の浮動小数点型であり、 **long double**型のサイズ以下です (double 型)。<br /><br /> Microsoft 固有: **long double**と**double**の表現は同じです。 ただし、 **long double**と**double**は別個の型です。|
||**long double**|型**long double**が浮動小数点型よりも大きいですまたは型に等しい**double**します。|

**Microsoft 固有の仕様**

次の表に、Microsoft C++の組み込み型に必要なストレージの容量を示します。 特に、64ビットのオペレーティングシステムでは、**長さ**が4バイトであることに注意してください。

### <a name="sizes-of-built-in-types"></a>組み込み型のサイズ

|の型|サイズ|
|----------|----------|
|**bool**、 **char**、 **unsigned char**、 **signed char**、 **_ _int8**|1 バイト|
|**_ _int16**、**short*、 **unsigned short**、 **wchar_t**、 **_ _wchar_t**|2 バイト|
|**float**、 **__int32**、 **int**、 **unsigned int**、 **long**、 **unsigned long**|4 バイト|
|**double**、 **_ _int64**、 **long double**、 **long**|8 バイト|

**END Microsoft 固有の仕様**

型ごとの値の範囲の概要については、「 [データ型の範囲](data-type-ranges.md) 」を参照してください。

型変換の詳細については、「 [標準変換](standard-conversions.md)」を参照してください。

## <a name="see-also"></a>関連項目

[データ型の範囲](data-type-ranges.md)