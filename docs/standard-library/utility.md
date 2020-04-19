---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: eaae94bcffcda6e113001dd7070bcc80e7c14d09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458078"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

C++ 標準ライブラリの型、関数、および演算子を定義し、オブジェクトのペアを作成し管理するのに役立てます。これらは 2 つのオブジェクトをあたかも 1 つのように扱う必要がある場合に役立ちます。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<utility>

**名前空間:** std

## <a name="remarks"></a>Remarks

ペアは、C++ 標準ライブラリで広く使用されます。 これはさまざまな関数の引数と戻り値として、また [map クラス](../standard-library/map-class.md)と [multimap クラス](../standard-library/multimap-class.md)などのコンテナーの要素型として必要です。 \<utility> ヘッダーは、キー/値ペア型の要素の管理を補助するために、\<map> により自動で追加されます。

> [!NOTE]
> ユーティリティ\<> ヘッダーは、ステートメント`#include <initializer_list>`を使用します。 また、組 > `class tuple`で\<定義されているを参照します。

## <a name="members"></a>メンバー

### <a name="classes"></a>クラス

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|プリミティブ数値変換の浮動小数点形式。|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|`pair` 要素の型をラップするクラスです。|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|`pair` 要素の数をラップするクラスです。|

### <a name="objects"></a>オブジェクト

|||
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)||
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)||
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)||
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)||

### <a name="functions"></a>関数

|||
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|型を返します。|
|[declval](../standard-library/utility-functions.md#declval)|省略形の式の評価。|
|[exchange](../standard-library/utility-functions.md#exchange)|オブジェクトに新しい値を割り当て、その古い値を返します。|
|[forward](../standard-library/utility-functions.md#forward)|引数の参照型 (`lvalue` または `rvalue` のどちらか) が完全転送によって隠されないよう保ちます。|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|`pair` オブジェクトから要素を取得する関数です。|
|[make_pair](../standard-library/utility-functions.md#make_pair)|`pair` 型のオブジェクトを作成するために使用されるテンプレート ヘルパー関数。コンポーネントの型は、パラメーターとして渡されるデータ型に基づいています。|
|[move](../standard-library/utility-functions.md#move)|`rvalue` 参照として引数で渡されたものを返します。|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|2 つの `pair` オブジェクトの要素を交換します。|
|[to_chars](../standard-library/utility-functions.md#to_chars)|値を文字列に変換します。|

### <a name="operators"></a>演算子

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|演算子の左辺のペア オブジェクトが右辺のペア オブジェクトと等しくないかどうかを調べます。|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|演算子の左辺のペア オブジェクトが右辺のペア オブジェクトと等しいかどうかを調べます。|
|[operator\<](../standard-library/utility-operators.md#op_lt)|演算子の左辺のペア オブジェクトが右辺のペア オブジェクトより小さいかどうかを調べます。|
|[operator\<=](../standard-library/utility-operators.md#op_gt_eq)|演算子の左辺のペア オブジェクトが右辺のペア オブジェクト以下かどうかを調べます。|
|[operator>](../standard-library/utility-operators.md#op_gt)|演算子の左辺のペア オブジェクトが右辺のペア オブジェクトより大きいかどうかを調べます。|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|演算子の左辺のペア オブジェクトが右辺のペア オブジェクト以上かどうかを調べます。|

### <a name="structs"></a>構造体

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|に`from_chars`使用される構造体。|
|[identity](../standard-library/identity-structure.md)|テンプレート パラメーターの型定義を指定する構造体。|
|[in_place_t](../standard-library/in-place-t-struct.md)|には、 `in_place_type_t`構造`in_place_index_t`体とも含まれます。|
|[integer_sequence](../standard-library/integer-sequence-class.md)|整数のシーケンスを表します。|
|[pair](../standard-library/pair-structure.md)|2 つのオブジェクトを 1 つのオブジェクトとして処理する機能を提供する型。|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|個別のコンストラクターと関数のオーバーロードを維持するために使用される型。|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|に`to_chars`使用される構造体。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)
