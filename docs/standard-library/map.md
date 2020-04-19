---
title: '&lt;map&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 2e861d2250585fbcdf3e1ef63d92f18185fc7f1c
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687776"
---
# <a name="ltmapgt"></a>&lt;map&gt;

コンテナークラステンプレート map および multimap とそのサポートテンプレートを定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<map>

**名前空間:** std

> [!NOTE]
> @No__t_0map > ライブラリでは、`#include <initializer_list>` ステートメントも使用します。

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|map バージョン|multimap バージョン|説明|
|-----------------|----------------------|-----------------|
|[operator!= (map)](../standard-library/map-operators.md#op_neq)|[operator!= (multimap)](../standard-library/map-operators.md#op_neq)|演算子の左側の map または multimap オブジェクトが右側の map または multimap オブジェクトと等しくないかどうかをテストします。|
|[operator< (map)](../standard-library/map-operators.md#op_eq_eq)|[operator< (multimap)](../standard-library/map-operators.md#op_eq_eq)|演算子の左側の map または multimap オブジェクトが右側の map または multimap オブジェクトより小さいかどうかをテストします。|
|[operator<= (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|演算子の左側の map または multimap オブジェクトが右側の map または multimap オブジェクト以下かどうかをテストします。|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|演算子の左側の map または multimap オブジェクトが右側の map または multimap オブジェクトと等しいかどうかをテストします。|
|[operator> (map)](../standard-library/map-operators.md#op_gt)|[operator> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|演算子の左側の map または multimap オブジェクトが右側の map または multimap オブジェクトより大きいかどうかを調べます。|
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|演算子の左側の map または multimap オブジェクトが右側の map または multimap オブジェクト以上であるかどうかをテストします。|

### <a name="specialized-template-functions"></a>特殊テンプレート関数

|map バージョン|multimap バージョン|説明|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|2 個の map または multimaps の要素を交換します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[value_compare クラス](../standard-library/value-compare-class-map.md)|要素のキーの値を比較し要素のマップ内の相対順序を決定して、マップの要素を比較できる関数オブジェクトを提供します。|
|[map クラス](../standard-library/map-class.md)|各要素にデータを自動的に並べる一意キーを持つコレクションからデータを格納および取得するために使用します。|
|[multimap クラス](../standard-library/multimap-class.md)|各要素にデータを自動的に並べるキー (一意の値である必要はありません) を持つコレクションからデータを格納および取得するために使用します。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準ライブラリ内のスレッド セーフ](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準ライブラリ リファレンス](../standard-library/cpp-standard-library-reference.md)
