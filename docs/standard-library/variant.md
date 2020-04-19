---
title: '&lt;バリアント&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 7a812ccc3c8cb2a660c01ad2b17ea75b5d5c9542
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268444"
---
# <a name="ltvariantgt"></a>&lt;バリアント&gt;

バリアント オブジェクトを保持し、値を管理します。 場合は、バリアントは、値の型はバリアントに指定されたテンプレート引数の型のいずれかを指定する必要があります、値を保持します。 これらのテンプレート引数には、代替手段は呼び出されます。

## <a name="requirements"></a>必要条件

**ヘッダー:** \<バリアント型 >

**名前空間:** std

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|演算子の左側にあるバリエーション オブジェクトが右側にあるバリアント型のオブジェクトと等しいかどうかをテストします。|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|演算子の左側にあるバリエーション オブジェクトが右側にあるバリエーション オブジェクトと等しくないかどうかをテストします。|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|演算子の左側にあるバリエーション オブジェクトが右側にあるバリエーション オブジェクトより小さいかどうかをテストします。|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|右側にあるバリアント型のオブジェクトと等しいまたはそれよりも小さいがの場合は、バリアントは、演算子の左側にあるオブジェクトを調べます。|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|演算子の左側にあるバリエーション オブジェクトが右側にあるバリエーション オブジェクトより大きいかどうかをテストします。|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|演算子の左側にあるバリエーション オブジェクトが右側にあるバリエーション オブジェクト以上かどうかをテストします。|

### <a name="functions"></a>関数

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|オブジェクトの変化形を取得します。|
|[get_if](../standard-library/variant-functions.md#get_if)|存在する場合は、オブジェクトの変化形を取得します。|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|返す**true**バリアントが存在する場合。|
|[swap](../standard-library/variant-functions.md#swap)|スワップを**バリアント**します。|
|[参照してください。](../standard-library/variant-functions.md#visit)|次の移動**バリアント**します。|

### <a name="classes"></a>クラス

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|オブジェクトがバリアント オブジェクトの値に無効なアクセスをレポートするためにスローします。|
|[バリアント](../standard-library/variant.md)|か、オブジェクトは、その代替の型のいずれかまたは値がないの値を保持します。|

### <a name="structs"></a>構造体

|||
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|バリアント型の既定値を構築できる一種の代替型。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|バリアント型のオブジェクトを支援します。|
|[variant_size](../standard-library/variant-size-structure.md)|バリアント型のオブジェクトを支援します。|

### <a name="objects"></a>オブジェクト

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
