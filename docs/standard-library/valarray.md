---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: ed90273fe293ae2e08c3c91762c12c42bb368c16
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688763"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

クラステンプレート valarray および多数のサポートクラステンプレートと関数を定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<valarray>

**名前空間:** std

> [!NOTE]
> @No__t_0valarray > ライブラリでは、' #include < initializer_list > ' ステートメントが使用されます。

## <a name="remarks"></a>Remarks

これらのクラステンプレートと関数は、パフォーマンスの向上を目的として、通常とは異なる緯度を許可します。 具体的には、`valarray<T1>` 型を返す関数は、他の型 T2 のオブジェクトを返す場合があります。 この場合、`valarray<T2>` 型の1つ以上の引数を受け取る関数は、これらの引数の任意の組み合わせを受け入れるオーバーロードを持つ必要があります。これらの引数はそれぞれ、T2 型の引数で置き換えられます。

## <a name="members"></a>メンバー

### <a name="functions"></a>関数

|||
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|入力 valarray の要素を演算し、入力 valarray の要素の絶対値と等しい要素を持つ valarray を返します。|
|[acos](../standard-library/valarray-functions.md#acos)|入力 valarray の要素を演算し、入力 valarray の要素のアークコサインと等しい要素を持つ valarray を返します。|
|[asin](../standard-library/valarray-functions.md#asin)|入力 valarray の要素を演算し、入力 valarray の要素のアークサインと等しい要素を持つ valarray を返します。|
|[atan](../standard-library/valarray-functions.md#atan)|入力 valarray の要素を演算し、入力 valarray の要素のアークタンジェントの主値と等しい要素を持つ valarray を返します。|
|[atan2](../standard-library/valarray-functions.md#atan2)|valarray の定数と要素の組み合わせによって指定されたデカルト成分のアークタンジェントと等しい要素を持つ valarray を返します。|
|[begin](../standard-library/valarray-functions.md#begin)||
|[cos](../standard-library/valarray-functions.md#cos)|入力 valarray の要素を演算し、入力 valarray の要素のコサインと等しい要素を持つ valarray を返します。|
|[cosh](../standard-library/valarray-functions.md#cosh)|入力 valarray の要素を演算し、入力 valarray の要素のハイパーボリック コサインと等しい要素を持つ valarray を返します。|
|[end](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|入力 valarray の要素を演算し、入力 valarray の要素の自然指数と等しい要素を持つ valarray を返します。|
|[log](../standard-library/valarray-functions.md#log)|入力 valarray の要素を演算し、入力 valarray の要素の自然対数と等しい要素を持つ valarray を返します。|
|[log10](../standard-library/valarray-functions.md#log10)|入力 valarray の要素を演算し、入力 valarray の要素の常用対数 (底が 10 の対数) と等しい要素を持つ valarray を返します。|
|[pow](../standard-library/valarray-functions.md#pow)|入力 valarray と定数の要素を演算し、入力 valarray の要素によって指定されている底と等しい要素を持つ valarray か、入力 valarray か定数の要素で指定された値だけ定数を指数乗したものと等しい要素を持つ valarray を返します。|
|[sin](../standard-library/valarray-functions.md#sin)|入力 valarray の要素を演算し、入力 valarray の要素のサインと等しい要素を持つ valarray を返します。|
|[sinh](../standard-library/valarray-functions.md#sinh)|入力 valarray の要素を演算し、入力 valarray の要素のハイパーボリック サインと等しい要素を持つ valarray を返します。|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|入力 valarray の要素を演算し、入力 valarray の要素の平方根と等しい要素を持つ valarray を返します。|
|[swap](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|入力 valarray の要素を演算し、入力 valarray の要素のタンジェントと等しい要素を持つ valarray を返します。|
|[tanh](../standard-library/valarray-functions.md#tanh)|入力 valarray の要素を演算し、入力 valarray の要素のハイパーボリック タンジェントと等しい要素を持つ valarray を返します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|サイズが等しい 2 つの valarray の対応する要素が等しくないか、あるいはある valarray のすべての要素が valarray の要素型の指定値と等しくないかをテストします。|
|[operator%](../standard-library/valarray-operators.md#op_mod)|サイズが等しい 2 つの valarray の対応する要素を除算した剰余か、valarray の要素型の指定値で valarray を除算した剰余、または valarray で指定値を除算した剰余を取得します。|
|[operator&](../standard-library/valarray-operators.md#op_amp)|サイズが等しい 2 つの valarray の対応する要素間、または valarray と要素型の指定値との間でビットごとの `AND` を計算した結果を取得します。|
|[operator&&](../standard-library/valarray-operators.md#op_amp_amp)|サイズが等しい 2 つの valarray の対応する要素間、または valarray と valarray の要素型の指定値との間で論理 `AND` を計算した結果を取得します。|
|[operator>](../standard-library/valarray-operators.md#op_gt)|ある valarray の要素がサイズが等しい valarray の要素より大きいか、またはある valarray のすべての要素が valarray の要素型の指定値より大きいか、もしくは指定値より小さいかをテストします。|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|ある valarray の要素がサイズが等しい valarray の要素以上であるか、またはある valarray のすべての要素が valarray の要素型の指定値以上であるか、もしくは指定値以下であるかをテストします。|
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|valarray の各要素のビットを、指定された位置数だけ右にシフトさせるか、2 番目の valarray で指定された要素ごとの量だけ右にシフトさせます。|
|[operator<](../standard-library/valarray-operators.md#op_lt)|ある valarray の要素がサイズが等しい valarray の要素未満であるか、またはある valarray のすべての要素が valarray の要素型の指定値より大きいか、もしくは指定値未満であるかをテストします。|
|[operator<=](../standard-library/valarray-operators.md#op_lt_eq)|ある valarray の要素がサイズが等しい valarray の要素以下であるか、またはある valarray のすべての要素が valarray の要素型の指定値以上であるか、もしくは指定値以下であるかをテストします。|
|[operator<<](../standard-library/valarray-operators.md#op_lt_lt)|valarray の各要素のビットを、指定された位置数だけ左にシフトさせるか、2 番目の valarray で指定された要素ごとの量だけ左にシフトさせます。|
|[operator*](../standard-library/valarray-operators.md#op_star)|サイズが等しい 2 つの valarray の対応する要素間の要素ごとの積、または valarray と valarray の要素型の指定値との間の積を取得します。|
|[operator+](../standard-library/valarray-operators.md#op_add)|サイズが等しい 2 つの valarray の対応する要素間の要素ごとの和、または valarray と valarray の要素型の指定値との間の和を取得します。|
|[operator-](../standard-library/valarray-operators.md#operator-)|サイズが等しい 2 つの valarray の対応する要素間の要素ごとの差、または valarray と valarray の要素型の指定値との間の差を取得します。|
|[operator/](../standard-library/valarray-operators.md#op_div)|サイズが等しい 2 つの valarray の対応する要素間の要素ごとの商、または valarray と valarray の要素型の指定値との間の商を取得します。|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|サイズが等しい 2 つの valarray の対応する要素が等しいか、あるいはある valarray のすべての要素が valarray の要素型の指定値と等しいかをテストします。|
|[operator^](../standard-library/valarray-operators.md#op_xor)|サイズが等しい 2 つの valarray の対応する要素間、または valarray と要素型の指定値との間でビットごとの排他的 `OR` を計算した結果を取得します。|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|サイズが等しい 2 つの valarray の対応する要素間、または valarray と要素型の指定値との間でビットごとの `OR` を計算した結果を取得します。|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|サイズが等しい 2 つの valarray の対応する要素間、または valarray と valarray の要素型の指定値との間で論理 `OR` を計算した結果を取得します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[gslice クラス](../standard-library/gslice-class.md)|valarray の多次元スライスを定義するのに使用する valarray のユーティリティ クラス。|
|[gslice_array クラス](../standard-library/gslice-array-class.md)|Valarray の一般的なスライスによって定義されたサブセット配列間の演算を提供することによって一般的なスライスオブジェクトをサポートする、内部の補助クラステンプレート。|
|[indirect_array クラス](../standard-library/indirect-array-class.md)|親 valarray のインデックスのサブセットを指定することによって定義されたサブセット配列間の演算を提供することによって、valarray のサブセットであるオブジェクトをサポートする、内部の補助クラステンプレート。|
|[mask_array クラス](../standard-library/mask-array-class.md)|サブセット配列間の演算を提供することにより、ブール式で指定された親 valarrays のサブセットであるオブジェクトをサポートする、内部の補助クラステンプレート。|
|[slice クラス](../standard-library/slice-class.md)|valarray のベクター的 1 次元サブセットを定義するのに使用する valarray のユーティリティ クラス。|
|[slice_array クラス](../standard-library/slice-array-class.md)|Valarray のスライスによって定義されたサブセット配列間の演算を提供することによってスライスオブジェクトをサポートする、内部の補助クラステンプレート。|
|[valarray クラス](../standard-library/valarray-class.md)|クラステンプレートは、配列として格納され、高速な数値演算を実行するために設計され、計算パフォーマンスに最適化された、`Type` 型の要素のシーケンスを制御するオブジェクトを記述します。|

### <a name="specializations"></a>特殊化

|||
|-|-|
|[valarray\<bool> クラス](../standard-library/valarray-bool-class.md)|クラステンプレート valarray \<**型**の特殊化されたバージョンは、 **bool**型の要素に > ます。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
