---
title: '&lt;complex&gt;'
ms.date: 11/04/2016
f1_keywords:
- <complex>
- std::<complex>
helpviewer_keywords:
- complex header
ms.assetid: 5e728995-3059-496a-9ce9-61d1bfbe4f2b
ms.openlocfilehash: 071e9369cdd0469d8ddc1c6649a3801732d8e23f
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688215"
---
# <a name="ltcomplexgt"></a>&lt;complex&gt;

コンテナークラステンプレート `complex` とそのサポートテンプレートを定義します。

## <a name="requirements"></a>［要件］

**ヘッダー**: \<complex>

**名前空間:** std

## <a name="remarks"></a>Remarks

複素数は、順序付けされた実数のペアです。 純粋に幾何学的な見地からすれば、複素平面は実数からなる 2 次元平面です。 複素平面には代数構造が加えられているため、実数平面とは異なる特殊な性質を持ちます。 この代数構造には次の 2 つの基本的な演算が含まれます。

- (*A*, *b*) + (*c*, *d*) = (*a*  + *c*, *b*  + *d*) として定義された追加

- (*A*, *b*) \* (*c*, *d*) = (*ac*  - *bd*, *ad*  + *bc*) として定義された乗算

複素数の加算や乗算を伴う複素数の集合は、標準の代数学的な意味での体 (field) です。

- 実数の体 (field) における実数の加算や乗算と全く同様、加算や乗算の演算には交換法則や結合法則が成り立ち、加法に対する乗法の分配法則も成り立ちます。

- 複素数 (0, 0) は加法 id、(1, 0) は乗算 id です。

- 複素数 (*a*, *b*) の加法逆関数は (-*a*,-*b*) で、(0, 0) 以外のすべての複素数の乗算逆はです。

   (*a/* (*a*<sup>2</sup>  + *b*<sup>2</sup>)、-*b*/(*a*<sup>2</sup>  + *b*<sup>2</sup>))

@No__t_6*bi*( *i*<sup>2</sup> =-1)  =  *z*形式で複素数*z* = (*a*, *b* *) を表す*ことにより、実数のセットの代数に関するルールを複合のセットに適用できます。数値とそのコンポーネント。 (例:

   (1 + 2*i*) \* (2 *+ 3 i) =* 1 \* (2 *+ 3 i) +* 2*i* \* (2 *+ 3 i*) = (2 + 3*i*) + (4*i* + 6*i*<sup>2</sup>) = (2-6) + (3 + 4)*i* =-4 + 7*i*

複素数系は体 (field) ですが、順序体 (ordered field) ではありません。 実際の数値とそのサブセットのフィールドについては、複素数の順序が指定されていないため、不等ずを実数のように複素数に適用することはできません。

複素数 *z* を表す形式としては、次の 3 つが一般的です。

- @No__t_3*bi*  =  デカルト : *z*

- 極座標: *z*  = *r* (cos *p*  + *i* sin *p*)

- 指数: *z*  = *r* \* *e*<sup>*ip*</sup>

これらの標準的な複素数の表現で使用される用語は、次のように呼ばれます。

- デカルト形式の実数要素、または実数部 *a*。

- デカルト形式の虚数要素、または虚数部 *b*。

- 複素数*r*の剰余または絶対値。

- 引数またはフェーズアングル*p* (ラジアン)。

特に指定しない限り、複数の値を返すことができる関数は、-πより大きく + π以下の引数のプリンシパル値を返して単一の値を保持する必要があります。 すべての角度はラジアンで表現する必要があります。ここで、円には2πラジアン (360 °) があります。

## <a name="members"></a>メンバー

### <a name="functions"></a>関数

|||
|-|-|
|[abs](../standard-library/complex-functions.md#abs)|複素数の係数を計算します。|
|[acos](../standard-library/complex-functions.md#acos)||
|[acosh](../standard-library/complex-functions.md#acosh)||
|[arg](../standard-library/complex-functions.md#arg)|複素数から偏角を抽出します。|
|[asin](../standard-library/complex-functions.md#asin)||
|[asinh](../standard-library/complex-functions.md#asinh)||
|[atan](../standard-library/complex-functions.md#atan)||
|[atanh](../standard-library/complex-functions.md#atanh)||
|[conj](../standard-library/complex-functions.md#conj)|複素数の複素共役を返します。|
|[cos](../standard-library/complex-functions.md#cos)|複素数のコサインを返します。|
|[cosh](../standard-library/complex-functions.md#cosh)|複素数のハイパーボリック コサインを返します。|
|[exp](../standard-library/complex-functions.md#exp)|複素数の指数関数を返します。|
|[imag](../standard-library/complex-functions.md#imag)|複素数の虚数部を抽出します。|
|[log](../standard-library/complex-functions.md#log)|複素数の自然対数を返します。|
|[log10](../standard-library/complex-functions.md#log10)|複素数の底 10 の対数を返します。|
|[norm](../standard-library/complex-functions.md#norm)|複素数のノルムを抽出します。|
|[polar](../standard-library/complex-functions.md#polar)|デカルト形式で、指定した係数と偏角に対応する複素数を返します。|
|[pow](../standard-library/complex-functions.md#pow)|複素数の底を、別の複素数で累乗することによって得られる複素数を評価します。|
|[proj](../standard-library/complex-functions.md#proj)||
|[real](../standard-library/complex-functions.md#real)|複素数の実数部を抽出します。|
|[sin](../standard-library/complex-functions.md#sin)|複素数のサインを返します。|
|[sinh](../standard-library/complex-functions.md#sinh)|複素数のハイパーボリック サインを返します。|
|[sqrt](../standard-library/complex-functions.md#sqrt)|複素数の平方根を返します。|
|[tan](../standard-library/complex-functions.md#tan)|複素数のタンジェントを返します。|
|[tanh](../standard-library/complex-functions.md#tanh)|複素数のハイパーボリック タンジェントを返します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator!=](../standard-library/complex-operators.md#op_neq)|2 つの複素数の間の非同等性をテストします。その一方または両方が実数部と虚数部の型のサブセットに属している場合があります。|
|[operator*](../standard-library/complex-operators.md#op_star)|2 つの複素数を乗算します。その一方または両方が実数部と虚数部の型のサブセットに属している場合があります。|
|[operator+](../standard-library/complex-operators.md#op_add)|2 つの複素数を加算します。その一方または両方が実数部と虚数部の型のサブセットに属している場合があります。|
|[operator-](../standard-library/complex-operators.md#operator-)|2 つの複素数を減算します。その一方または両方が実数部と虚数部の型のサブセットに属している場合があります。|
|[operator/](../standard-library/complex-operators.md#op_div)|2 つの複素数を除算します。その一方または両方が実数部と虚数部の型のサブセットに属している場合があります。|
|[operator<\<](../standard-library/complex-operators.md#op_lt_lt)|出力ストリームに複素数を挿入するテンプレート関数。|
|[operator==](../standard-library/complex-operators.md#op_eq_eq)|2 つの複素数の間の同等性をテストします。その一方または両方が実数部と虚数部の型のサブセットに属している場合があります。|
|[operator>>](../standard-library/complex-operators.md#op_gt_gt)|入力ストリームから複素数を抽出するテンプレート関数。|

### <a name="classes"></a>クラス

|||
|-|-|
|[complex\<double>](../standard-library/complex-double.md)|明示的に特殊化されたクラステンプレートは、順序付けされたオブジェクトのペア ( **double**型) を格納するオブジェクトを記述します。1つ目は複素数の実数部を表し、2番目のオブジェクトは虚数部を表します。|
|[complex\<float>](../standard-library/complex-float.md)|明示的に特殊化されたクラステンプレートは、順序付けされたオブジェクトのペア ( **float**型) を格納するオブジェクトを記述します。最初のオブジェクトは複素数の実数部を表し、2番目のオブジェクトは虚数部を表します。|
|[complex\<long double>](../standard-library/complex-long-double.md)|明示的に特殊化されたクラステンプレートは、 **long double**型の順序付けられたオブジェクトのペアを格納するオブジェクトを記述します。1つ目は、複素数の実数部を表し、2番目のオブジェクトが虚数部を表します。|
|[complex](../standard-library/complex-class.md)|クラステンプレートは、複素数システムを表すために使用されるオブジェクトを表し、複雑な算術演算を実行します。|

### <a name="literals"></a>リテラル

\<complex> ヘッダーでは次の[ユーザー定義リテラル](../cpp/user-defined-literals-cpp.md)が定義されており、実数部が 0 および虚数部が入力パラメーターの値である複素数を作成します。

|||
|-|-|
|`constexpr complex<long double> operator""il(long double d)`<br />`constexpr complex<long double> operator""il(unsigned long long d)`|戻り値: `complex<long double>{0.0L, static_cast<long double>(d)}`|
|`constexpr complex<double> operator""i(long double d)`<br />`constexpr complex<double> operator""i(unsigned long long d)`|`complex<double>{0.0, static_cast<double>(d)}` を返します。|
|`constexpr complex<float> operator""if(long double d)`<br />`constexpr complex<float> operator""if(unsigned long long d)`|`complex<float>{0.0f, static_cast<float>(d)}` を返します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
