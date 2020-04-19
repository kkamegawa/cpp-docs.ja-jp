---
title: '&lt;optional&gt;'
ms.date: 08/06/2019
f1_keywords:
- <optional>
helpviewer_keywords:
- <optional>
ms.openlocfilehash: bce31811c98d351f3c561b3136d41f7ed23d13e0
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687258"
---
# <a name="ltoptionalgt"></a>&lt;optional&gt;

コンテナークラステンプレート `optional` といくつかのサポートテンプレートを定義します。

## <a name="requirements"></a>［要件］

**ヘッダー:** \<optional >

**名前空間:** std

## <a name="members"></a>メンバー

### <a name="operators"></a>演算子

|||
|-|-|
|[operator==](../standard-library/optional-operators.md#op_eq_eq)|オブジェクトが別のオブジェクトと等しいかどうかをテストします。|
|[operator!=](../standard-library/optional-operators.md#op_neq)|オブジェクトが別のオブジェクトと等しくないかどうかをテストします。|
|[operator<](../standard-library/optional-operators.md#op_lt)|左側のオブジェクトが右側のオブジェクトより小さいかどうかをテストします。|
|[operator<=](../standard-library/optional-operators.md#op_lt_eq)|左側のオブジェクトが右側のオブジェクト以下かどうかをテストします。|
|[operator>](../standard-library/optional-operators.md#op_gt)|左側のオブジェクトが右側のオブジェクトより大きいかどうかをテストします。|
|[operator>=](../standard-library/optional-operators.md#op_lt_eq)|左側のオブジェクトが右側のオブジェクト以上かどうかをテストします。|

> [!NOTE]
> @No__t_0optional > 演算子は、関係比較に加えて、 **nullopt**および `T` との比較もサポートしています。

### <a name="functions"></a>関数

|||
|-|-|
|[make_optional](../standard-library/optional-functions.md#make_optional)|オブジェクトを省略可能にします。|
|[swap](../standard-library/optional-functions.md#swap)|2つの `optional` オブジェクトの格納されている値を交換します。|

### <a name="classes-and-structs"></a>クラスと構造体

|||
|-|-|
|hash|含まれているオブジェクトのハッシュを返します。|
|[省略可能なクラス](../standard-library/optional-class.md)|値を保持できるか、または保持できないオブジェクトを表します。|
|[nullopt_t 構造体](../standard-library/nullopt-t-structure.md)|値を保持しないオブジェクトを記述します。|
|[bad_optional_access クラス](../standard-library/bad-optional-access-class.md)|存在しない値にアクセスしようとしたことを報告する例外としてスローされるオブジェクトを表します。|

### <a name="objects"></a>オブジェクト

|||
|-|-|
|[nullopt](../standard-library/optional-functions.md#nullopt)|比較のための `nullopt_t` のインスタンス。|

## <a name="see-also"></a>関連項目

[ヘッダー ファイル リファレンス](../standard-library/cpp-standard-library-header-files.md)
